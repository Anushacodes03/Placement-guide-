# 🧩 Castellum Labs Internship — Answers & Hands-On Command Guide

> *Companion to the Interview Prep Guide — this one has the actual answers, explanations, and exact commands you can run to practice.*

---

## 📚 1. Core Security Concepts — Answers

**CIA Triad**
- **Confidentiality** — only authorized people can access data (e.g., encryption, access controls)
- **Integrity** — data isn't tampered with (e.g., hashing, checksums)
- **Availability** — systems stay up and accessible (e.g., DDoS protection, redundancy)

**Authentication vs Authorization**
- Authentication = *"Who are you?"* (login, verifying identity)
- Authorization = *"What are you allowed to do?"* (permissions, access control)
- Example: logging in with a password = authentication; only admins being able to delete users = authorization

**Symmetric vs Asymmetric Encryption**
- Symmetric: same key encrypts and decrypts (fast, used for bulk data) → **AES**
- Asymmetric: public key encrypts, private key decrypts (slower, used for key exchange/signing) → **RSA, ECC**
- TLS uses asymmetric encryption to securely exchange a symmetric session key, then switches to symmetric for the actual data transfer (best of both worlds)

**Hashing vs Encryption vs Encoding**
- **Hashing** — one-way, fixed-length output, used for integrity/passwords (SHA-256, bcrypt). Cannot be reversed.
- **Encryption** — two-way, reversible with a key, used for confidentiality (AES, RSA)
- **Encoding** — reversible transformation for compatibility, NOT security (Base64). Never use encoding to "protect" data.

**False Positive vs False Negative**
- False Positive = tool flags something as a threat, but it's actually safe (wastes analyst time)
- False Negative = tool misses an actual threat (dangerous — this is the worse of the two in security)

---

## 🌐 2. OWASP Top 10 (2021) — Cheat Sheet with Fixes

| # | Vulnerability | One-Line Explanation | Fix |
|---|---|---|---|
| A01 | Broken Access Control | Users can access data/functions they shouldn't | Enforce server-side authorization checks on every request |
| A02 | Cryptographic Failures | Sensitive data exposed due to weak/missing encryption | Use strong, up-to-date algorithms (AES-256, TLS 1.3); never roll your own crypto |
| A03 | Injection | Untrusted input executed as code (SQL, OS commands) | Use parameterized queries / prepared statements, input validation |
| A04 | Insecure Design | Security flaws baked into architecture, not just code | Threat modeling early in design phase |
| A05 | Security Misconfiguration | Default creds, verbose errors, open cloud buckets | Harden configs, disable unused features, automate config checks |
| A06 | Vulnerable & Outdated Components | Using libraries with known CVEs | Regular dependency scanning (SCA tools), patch management |
| A07 | Identification & Auth Failures | Weak session/password handling | MFA, strong session management, rate-limit login attempts |
| A08 | Software & Data Integrity Failures | Trusting unverified code/updates (e.g., CI/CD pipeline attacks) | Verify signatures, use trusted repositories |
| A09 | Security Logging & Monitoring Failures | Attacks go undetected due to poor logging | Centralized logging (SIEM), alerting on anomalies |
| A10 | Server-Side Request Forgery (SSRF) | Server tricked into making requests to internal/unintended resources | Whitelist allowed destinations, disable unused URL schemas |

**SQLi vs Blind SQLi**
- SQLi: attacker sees direct output/error from the injected query
- Blind SQLi: no visible output — attacker infers data via true/false responses (boolean-based) or response time (time-based)

**Stored vs Reflected vs DOM XSS**
- Stored: malicious script saved on server (e.g., in a comment), served to every visitor
- Reflected: script comes back in the immediate response (e.g., via URL parameter), not saved
- DOM-based: vulnerability exists purely in client-side JavaScript, never touches the server

---

## 🖧 3. Networking — Answers & Commands to Run

**TCP 3-Way Handshake:** `SYN → SYN-ACK → ACK`

**Common Ports (memorize these):**
```
21   FTP
22   SSH
23   Telnet
25   SMTP
53   DNS
80   HTTP
443  HTTPS
3306 MySQL
3389 RDP
```

**Firewall vs IDS vs IPS**
- Firewall — blocks/allows traffic based on rules (ports, IPs)
- IDS (Intrusion Detection System) — detects and alerts on suspicious traffic, doesn't block
- IPS (Intrusion Prevention System) — detects AND actively blocks malicious traffic

### 🔧 Commands to Practice (Network Recon)

```bash
# Basic host discovery on a subnet
nmap -sn 192.168.1.0/24

# Full TCP SYN scan with service/version detection
nmap -sS -sV -sC -A target_ip

# Scan all 65535 ports
nmap -p- target_ip

# Aggressive scan with OS detection
nmap -A -T4 target_ip

# UDP scan (slower, often skipped but important)
nmap -sU --top-ports 20 target_ip
```

> ⚠️ **Only run these against machines you own or have explicit permission to test** — e.g., your own home lab, TryHackMe/HackTheBox targets, or DVWA/Juice Shop set up locally.

---

## 🕵️ 4. SOC / SIEM / Threat Intel — Answers

**What a SOC Analyst does day-to-day:**
1. Monitor SIEM dashboards for alerts
2. Triage alerts (is this a real threat or noise?)
3. Investigate using logs, network data, endpoint data
4. Escalate confirmed incidents per playbook
5. Document findings and update detection rules

**MITRE ATT&CK Framework:** A knowledge base of real-world attacker tactics and techniques (e.g., Initial Access → Execution → Persistence → Privilege Escalation → Exfiltration). Analysts use it to map detected activity to known attacker behavior patterns.

**Cyber Kill Chain (Lockheed Martin model):**
```
Reconnaissance → Weaponization → Delivery → Exploitation
→ Installation → Command & Control → Actions on Objectives
```

---

## 🛠️ 5. DevSecOps — Answers

**SAST vs DAST vs SCA**
- **SAST** (Static Application Security Testing) — scans source code without running it (finds issues early, in the IDE/CI)
- **DAST** (Dynamic Application Security Testing) — tests a running application from the outside (like a black-box pentest)
- **SCA** (Software Composition Analysis) — scans third-party libraries/dependencies for known CVEs

**Shift-Left Security:** Moving security checks earlier in the development lifecycle (design/code stage) instead of only testing right before release — cheaper and faster to fix issues early.

---

## 🧪 6. Practical Lab Setup — What to Actually Run

### Step 1 — Set up a local vulnerable app (safe practice target)
```bash
# Using Docker (recommended — fastest way to get DVWA running)
docker pull vulnerables/web-dvwa
docker run --rm -it -p 80:80 vulnerables/web-dvwa
# Then visit http://localhost in your browser
```

Or for OWASP Juice Shop:
```bash
docker pull bkimminich/juice-shop
docker run --rm -p 3000:3000 bkimminich/juice-shop
# Visit http://localhost:3000
```

### Step 2 — Install Burp Suite Community Edition
- Download from PortSwigger's official site
- Configure your browser to proxy through `127.0.0.1:8080`
- Practice: intercept a login request in DVWA, send it to **Repeater**, modify the username field, and observe the response

### Step 3 — Try a basic SQL Injection (on DVWA, Low security level only)
In the DVWA "SQL Injection" module, try entering into the input field:
```
1' OR '1'='1
```
This is a classic authentication bypass style payload — understand *why* it works (it manipulates the query logic), not just that it works.

### Step 4 — Try a basic Reflected XSS (on DVWA, Low security level only)
```html
<script>alert('XSS')</script>
```
Enter this into an input field that reflects back to the page — if an alert box pops up, the input isn't being sanitized.

### Step 5 — Practice basic Python automation
A simple starter script (extend this — interviewers love to see initiative):
```python
import socket

def scan_port(host, port):
    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    sock.settimeout(0.5)
    result = sock.connect_ex((host, port))
    sock.close()
    return result == 0

target = "127.0.0.1"
common_ports = [21, 22, 23, 25, 53, 80, 443, 3306, 3389]

for port in common_ports:
    if scan_port(target, port):
        print(f"Port {port} is OPEN")
```
Run it with:
```bash
python3 port_scanner.py
```

### Step 6 — Practice Linux fundamentals
```bash
ls -la              # list files with permissions
chmod 644 file.txt   # change file permissions
netstat -tulnp       # show listening ports and processes
curl -I https://example.com   # check HTTP response headers
grep -r "password" /var/www/  # search for a string recursively
```

---

## 🎯 7. Sample Answers to Behavioral Questions

**"Why cybersecurity, and why Castellum Labs?"**
> A strong answer connects a genuine personal interest (a project, CTF, or "aha" moment) to Castellum's specific model — e.g., "I'm drawn to their continuous-security / MSSP approach rather than one-off audits, because it means security work is ongoing and outcome-driven, which matches how I like to work."

**"How do you stay updated with security trends?"**
> Name specific sources: The Hacker News, PortSwigger Research blog, NVD/CVE feeds, r/netsec, specific security researchers on X/Twitter, TryHackMe/HTB for hands-on practice.

**"Tell me about a time you learned something technical quickly."**
> Use a specific story with a beginning-middle-end structure: the problem, what you did to learn it, the outcome. Concrete > generic.

---

## ✅ 8. Final Pre-Interview Run-Through Checklist

- [ ] Can explain all 10 OWASP categories with a fix for each — out loud, without notes
- [ ] Ran `nmap -sV -sC` against a local target and can explain the output
- [ ] Successfully intercepted a request in Burp Suite and used Repeater
- [ ] Completed a basic SQLi and XSS exercise on DVWA/Juice Shop and can explain *why* each works
- [ ] Ran and understood the Python port scanner script above
- [ ] Comfortable navigating Linux CLI (permissions, netstat, grep, curl)
- [ ] Can explain the Cyber Kill Chain and MITRE ATT&CK at a high level
- [ ] Has 2–3 specific personal project/CTF stories ready to reference

---


