# 🛡️ Castellum Labs Internship — Interview & Assessment Prep Guide

> *Your complete roadmap to preparing for the Castellum Labs cybersecurity internship — from company research to technical rounds to HR.*

---

## 📌 1. Company Snapshot (Know This Cold)

| Attribute | Detail |
|---|---|
| **Founded** | 2018, Hyderabad, India |
| **Parent entity** | Raaga Technologies Private Limited |
| **Founder** | Rajeev Shukla |
| **HQ** | Hyderabad, Telangana (registered office in Chandigarh) |
| **Team size** | ~50 employees |
| **Core areas** | Application Security (AppSec/DevSecOps), Managed Detection & Response (MDR/SOC), Cloud Security, Dark Web Monitoring & OSINT |
| **Flagship products** | **appFORT** (AppSec orchestration + CodeSafe IDE plugin), **threatNiXD** (threat detection/response), **watchOUT** (dark web & attack surface monitoring) |
| **Tech stack signals** | Python, OWASP frameworks, WordPress/WooCommerce (for their own site), cloud-native delivery model |
| **Positioning** | Aims to be an MSSP (Managed Security Services Provider) delivering *continuous* security rather than one-off audits |
| **Culture notes (from reviews)** | Strong mentorship & hands-on learning reported by many; some reviews flag inconsistent pay timelines and heavy workload during incidents — go in with realistic expectations and ask about stipend/payment terms during HR round |

**💡 Why this matters:** Interviewers often ask *"What do you know about us?"* — being able to speak fluently about their MSSP model, their three product lines, and their AppSec + SOC dual focus will set you apart from candidates who only skimmed the homepage.

---

## 🗂️ 2. The Interview Process (What to Expect)

Based on candidate reports, the process typically has **3 stages**:

```
Stage 1: Application Screening
        ↓
Stage 2: Technical Round 1 — THEORETICAL
        ↓
Stage 3: Technical Round 2 — PRACTICAL
   (Application Security + Network Pentesting)
        ↓
Stage 4: HR Round — Onboarding Discussion
```

- **Timeline:** Roughly ~1 week from application to first interview call.
- **Format:** Rounds are typically short and conversational rather than aggressive grilling — reported average difficulty is **2.3/5**, i.e., approachable if you have solid fundamentals.
- **Vibe:** Reviewers describe interviewers as generally kind, mixing theory and hands-on tasks rather than pure whiteboard grilling.

---

## 📚 3. Round 1 — Theoretical Round

This round tests **fundamentals**, not obscure trivia. Expect questions across these buckets:

### 🔐 A. Core Security Concepts
- CIA Triad (Confidentiality, Integrity, Availability) — explain with real examples
- Difference between **Authentication vs Authorization**
- Symmetric vs Asymmetric encryption (be ready to name algorithms: AES, RSA)
- Hashing vs Encryption vs Encoding — know the distinction cold
- What is a **false positive vs false negative** in security scanning?

### 🌐 B. Web Application Security (OWASP)
- **OWASP Top 10** — you must be able to name and briefly explain all 10 (2021 list), especially:
  - Broken Access Control
  - Injection (SQLi, Command Injection)
  - Cross-Site Scripting (XSS) — Stored vs Reflected vs DOM-based
  - Cross-Site Request Forgery (CSRF)
  - Security Misconfiguration
  - Insecure Deserialization
- Difference between **SQLi** and **Blind SQLi**
- What is **SSRF** and how is it exploited?
- Session management flaws (session fixation, session hijacking)
- How does **HTTPS/TLS handshake** work at a high level?

### 🖧 C. Networking & Infrastructure
- TCP vs UDP, and the 3-way handshake
- Common ports to memorize: 21 (FTP), 22 (SSH), 23 (Telnet), 25 (SMTP), 53 (DNS), 80/443 (HTTP/S), 3389 (RDP), 3306 (MySQL)
- What is a **firewall**, **IDS**, **IPS** — and how do they differ?
- DNS resolution process, and what **DNS spoofing/poisoning** is
- VPN basics and common protocols

### 🕵️ D. SOC / MDR & Threat Intel (since it's a core service line)
- What is a **SOC (Security Operations Center)** and what does an analyst do day-to-day?
- SIEM basics — what does a SIEM tool do? (Splunk, ELK, QRadar are common names to know)
- What is a **kill chain** / **MITRE ATT&CK framework** (even a basic overview helps a lot)
- Phishing detection and social engineering awareness — Castellum runs phishing simulation programs, so understanding this domain shows you've researched them

### 🛠️ E. DevSecOps (since appFORT/CodeSafe is their flagship)
- What is DevSecOps and how does it differ from traditional AppSec?
- SAST vs DAST vs SCA (Software Composition Analysis) — know the difference
- Where security fits in a CI/CD pipeline
- What is "shift-left security"?

---

## 🧪 4. Round 2 — Practical Round (AppSec + Network Pentesting)

This is hands-on. Be ready to **demonstrate**, not just describe.

### Application Security Practical Tasks (Likely)
- Identify a vulnerability in a sample vulnerable web app (think **DVWA**, **bWAPP**, **Juice Shop**, **PortSwigger Web Security Academy** labs)
- Walk through exploiting a simple **SQL Injection** or **XSS** payload
- Explain how you'd write a basic **secure code review** checklist
- Discuss common tools: **Burp Suite**, **OWASP ZAP**, **Nmap**, **Nikto**

### Network Pentesting Practical Tasks (Likely)
- Basic **Nmap** scanning — scan types (`-sS`, `-sV`, `-sC`, `-A`), what output tells you
- Identify open ports/services and suggest possible attack vectors
- Basic understanding of **privilege escalation** concepts (Linux/Windows)
- Explain a simple **enumeration → exploitation → post-exploitation** workflow (even conceptually, if no live exploitation is required)

### 🎯 Tools You Should Have Hands-On Familiarity With
| Category | Tools |
|---|---|
| Web Proxy/Scanner | Burp Suite (Community), OWASP ZAP |
| Network Scanning | Nmap, Wireshark |
| Vulnerable Practice Labs | DVWA, bWAPP, OWASP Juice Shop, TryHackMe, PortSwigger Academy |
| Recon/OSINT | theHarvester, Shodan, Google Dorking |
| Scripting | Python (basic automation scripts — they explicitly value this) |
| OS | Comfort with Linux CLI (Kali Linux basics) |

> **Tip:** If you've done *any* CTFs, TryHackMe rooms, or HackTheBox machines — bring specific examples. Interviewers love concrete stories over textbook answers.

---

## 💻 5. Skills to Sharpen Before the Interview (Priority Order)

1. **OWASP Top 10** — deep enough to explain root cause + fix for each
2. **Burp Suite fundamentals** — intercepting requests, repeater, intruder basics
3. **Nmap scanning syntax** and reading output
4. **Basic Python scripting** — even simple automation (e.g., a port scanner script) shows initiative
5. **Linux command line fluency** (file permissions, grep, basic networking commands like `netstat`, `curl`)
6. **One structured story** about a personal project, CTF, or lab exercise you can walk through end-to-end

---

## ❓ 6. Sample Questions You Might Be Asked

### Technical
- "Walk me through what happens when you type a URL into a browser and hit Enter."
- "How would you test a login page for vulnerabilities?"
- "What's the difference between a vulnerability scan and a penetration test?"
- "If you found a critical vulnerability in a client's production system, what would you do first?"
- "Explain a CVE you've read about recently."

### Behavioral / Fit
- "Why cybersecurity, and why Castellum Labs specifically?"
- "Tell me about a time you had to learn something technical very quickly."
- "How do you stay updated with the latest security trends?" (Good answer: mention specific sources — Twitter/X security researchers, r/netsec, The Hacker News, PortSwigger blog, CVE feeds)
- "Are you comfortable working in a fast-paced environment with tight deadlines?" (Reviews mention workload can spike during incidents — answer honestly but positively)

---

## 📝 7. Questions YOU Should Ask Them

Asking sharp questions signals genuine interest and maturity:

- "Which of your three products — appFORT, threatNiXD, or watchOUT — would I primarily be supporting as an intern?"
- "What does a typical week look like for an intern on the AppSec vs. SOC side?"
- "Is there a mentor or buddy system for interns?"
- "What's the possibility of a full-time offer at the end of the internship, and what does that evaluation look like?"
- "What's the stipend structure and is it paid on a fixed monthly cycle?" *(reasonable to ask given some reviews mention payment delays — frame it professionally)*

---

## 📄 8. Practical Prep Checklist (Do This Before the Interview)

- [ ] Re-read the OWASP Top 10 (2021) with real examples for each
- [ ] Set up **Burp Suite Community Edition** and practice intercepting a request
- [ ] Complete 2–3 rooms on **TryHackMe** (start with "Web Fundamentals" or "Nmap" path)
- [ ] Practice explaining **Nmap scan output** out loud
- [ ] Write and test one small **Python script** (e.g., a basic port scanner or log parser)
- [ ] Review your resume — be ready to explain *every single line*, especially any VAPT or project experience
- [ ] Prepare your "Why Castellum Labs?" answer using the company snapshot above
- [ ] Prepare 2–3 thoughtful questions to ask the interviewer
- [ ] Get comfortable narrating your thought process out loud while solving a problem — practical rounds often value *how you think* over getting the "right" answer instantly

---

## 🌟 9. Final Tips

- **Fundamentals over flash.** Reviews suggest they test core understanding, not trick questions — don't over-prepare exotic attack techniques at the expense of nailing the basics.
- **Think aloud.** In the practical round, narrate your reasoning — it shows problem-solving process, which matters more than a fast final answer.
- **Be honest about what you don't know**, but pivot to how you'd find out (e.g., "I haven't used that tool, but I'd start by checking its docs and testing it in a lab environment").
- **Bring genuine curiosity** about their MSSP model and continuous security approach — it's central to their identity and differentiator.

---

*Good luck! Prepare well, stay calm, and let your fundamentals do the talking.* 🎯
