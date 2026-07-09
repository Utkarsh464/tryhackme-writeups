# Cyber Security 101 — Learning Roadmap & Career Progression

> **Your journey from security novice to job-ready professional.**  
> This roadmap maps the completed Modules 1–9 into the broader cybersecurity landscape, defines prerequisites, outlines skill progression, and charts career paths unlocked at each stage.

---

## Table of Contents

- [Where Modules 1–9 Fit in Cybersecurity](#where-modules-1-9-fit-in-cybersecurity)
- [Prerequisites Heatmap](#prerequisites-heatmap)
- [Skill Progression Map](#skill-progression-map)
- [Modules 10–14: The Bridge to Advanced Roles](#modules-10-14-the-bridge-to-advanced-roles)
- [Next Recommended Paths](#next-recommended-paths)
- [Career Paths Unlocked](#career-paths-unlocked)
- [Certifications Alignment](#certifications-alignment)
- [Personal Study Plan](#personal-study-plan)

---

## Where Modules 1–9 Fit in Cybersecurity

The Cyber Security 101 path is deliberately sequenced to build overlapping competencies. Below is how each completed module maps to real-world security domains:

```
                      ┌─────────────────────────────────────────┐
                      │         CYBERSECURITY LANDSCAPE          │
                      ├──────────────┬──────────────┬────────────┤
                      │  OFFENSIVE   │   DEFENSIVE   │   GOVERNANCE│
                      │  (Red Team)  │  (Blue Team)  │  (GRC)      │
├─────────────────────┼──────────────┼──────────────┼────────────┤
│ Mod 01: Intro       │  Foundation  │  Foundation  │  Foundation │
│ Mod 02: Linux       │  Essential   │  Essential   │  —          │
│ Mod 03: Web Hacking │  Core        │  Useful      │  —          │
│ Mod 04: Network     │  Core        │  Core        │  —          │
│ Mod 05: Windows     │  Essential   │  Essential   │  —          │
│ Mod 06: Python      │  Enabler     │  Enabler     │  —          │
│ Mod 07: PrivEsc     │  Core        │  Useful      │  —          │
│ Mod 08: Metasploit  │  Core        │  Useful      │  —          │
│ Mod 09: Burp Suite  │  Core        │  —           │  —          │
├─────────────────────┼──────────────┼──────────────┼────────────┤
│ Mod 10: AD          │  Advanced    │  Advanced    │  —          │
│ Mod 11: Crypto      │  Core        │  Core        │  Useful     │
│ Mod 12: Malware     │  Advanced    │  Core        │  —          │
│ Mod 13: Wireshark   │  Useful      │  Core        │  —          │
│ Mod 14: Capstone    │  Synthesis   │  Synthesis   │  Synthesis  │
└─────────────────────┴──────────────┴──────────────┴────────────┘
```

**Key Insight:** Modules 1–9 form the **common foundation** shared by all cybersecurity roles. Specialisation begins with Modules 10–14 and the subsequent learning paths.

---

## Prerequisites Heatmap

Below is the dependency graph showing what knowledge each module assumes:

```
Mod 01 (Intro)
  └─► Mod 02 (Linux) ──► Mod 04 (Network) ──► Mod 07 (PrivEsc)
                                    │                  │
                                    ├──► Mod 08 (MSF) ──┤
                                    │                  │
Mod 03 (Web) ──► Mod 09 (Burp)     │                  │
                                    │                  │
Mod 05 (Windows) ──► Mod 10 (AD) ──┘                  │
                                    │                  │
Mod 06 (Python) ◄───────────────────┴──────────────────┘
                                    │
Mod 11 (Crypto) ◄── Basic logic (no strict dependency)
                                    │
Mod 12 (Malware) ◄── Mod 02 + Mod 06 + Mod 11 (recommended)
                                    │
Mod 13 (Wireshark) ◄── Mod 04
                                    │
Mod 14 (Capstone) ◄── Everything above
```

**Recommended completion order:** Strictly sequential. Each module builds on concepts and tools introduced in prior modules. Jumping ahead will result in knowledge gaps.

---

## Skill Progression Map

### Phase 1 — Foundation (Modules 1–2)
| Skill | Level Achieved |
|-------|---------------|
| Operating system navigation | Proficient in Linux CLI |
| Security terminology & concepts | Understand CIA, risk, threat models |
| Tool installation & environment setup | Confident with apt, pip, git |

### Phase 2 — Core Technical (Modules 3–4)
| Skill | Level Achieved |
|-------|---------------|
| Web application architecture | Understand request/response cycle, DOM, APIs |
| Vulnerability identification | Can spot XSS, SQLi, IDOR, SSRF in source code |
| Network reconnaissance | Proficient with nmap, understand port states |
| Protocol analysis | Read HTTP headers, DNS records, TLS handshake |

### Phase 3 — Platform Depth (Modules 5–6)
| Skill | Level Achieved |
|-------|---------------|
| Windows system administration | Navigate GUI and CLI, manage users/services |
| Active Directory concepts | Understand domains, OUs, GPOs, authentication |
| Automation & scripting | Write Python scripts >50 lines for recon/exploitation |
| Log analysis | Parse syslog, Event Viewer, Apache logs |

### Phase 4 — Exploitation (Modules 7–9)
| Skill | Level Achieved |
|-------|---------------|
| Privilege escalation methodology | Systematic enumeration → exploitation on both OSes |
| Exploitation framework fluency | Use msfconsole without a GUI |
| Web proxy mastery | Chain Burp Suite with other tools, write extensions |
| Payload generation | Craft custom meterpreter/shellcode with msfvenom |

### Phase 5 — Specialisation (Modules 10–14 — Pending)
| Skill | Target Level |
|-------|-------------|
| Active Directory attacks | Kerberos abuse, ACL exploitation, forest trusts |
| Cryptography applied | Decrypt traffic, exploit weak schemes, PKI attacks |
| Malware reverse engineering | Static/dynamic analysis, memory forensics |
| Traffic forensics | Full PCAP analysis, exfiltration detection |
| Full-scope pentest execution | Chain techniques across domains, write reports |

---

## Modules 10–14: The Bridge to Advanced Roles

The pending modules are not just "more content" — they are the critical bridge between foundational knowledge and professional readiness.

```
Foundation (1-9) ──► Modules 10-14 ──► Specialised Path
     │                                        │
     │   Active Directory                    │
     ├───────────────────────────────────────► Jr Penetration Tester
     │   Cryptography                        │
     ├───────────────────────────────────────► SOC Level 1 / Cyber Defense
     │   Malware Analysis                    │
     ├───────────────────────────────────────► Malware & Forensics
     │   Wireshark / Traffic Analysis        │
     ├───────────────────────────────────────► SOC Level 1 / Threat Hunting
     │   Capstone (synthesis)                │
     └───────────────────────────────────────► Portfolio / Interview prep
```

**Why complete 10–14 before moving on?**
- They introduce enterprise-scale attacks (AD) which most real-world jobs require
- They cover the blue side (malware, Wireshark) balancing your red skills
- The capstone forces technique chaining under time pressure — exactly like real exams (e.g., PNPT, OSCP)

---

## Next Recommended Paths

Once the full Cyber Security 101 path is complete, these TryHackMe learning paths are the natural next step:

### 1. Jr Penetration Tester (Strongly Recommended after Mod 14)
- **Focus:** Web exploitation, network penetration testing, report writing
- **Key modules:** OWASP Top 10 revisited, buffer overflows, network exploitation, writeups
- **Prepares you for:** eJPT certification
- **Estimated time:** 40–60 hours
- **Leverages from 101:** Mod 03 (Web), Mod 04 (Network), Mod 07 (PrivEsc), Mod 08 (MSF), Mod 09 (Burp)

### 2. SOC Level 1
- **Focus:** Defensive security, SIEM (Splunk, ELK), incident response, threat intelligence
- **Key modules:** Network traffic analysis, endpoint monitoring, phishing analysis
- **Prepares you for:** BTL1 (Blue Team Level 1) certification
- **Estimated time:** 50–70 hours
- **Leverages from 101:** Mod 04 (Network), Mod 13 (Wireshark), Mod 12 (Malware)

### 3. Offensive Pentesting (Advanced)
- **Focus:** Buffer overflows (x86/x64), advanced AD attacks, anti-virus evasion
- **Key modules:** Buffer Overflow Prep, AD attacks revisited, shellcode development
- **Prepares you for:** OSCP (PWK/OSCP) certification
- **Estimated time:** 80–120 hours
- **Prerequisites:** Must complete Modules 10 (AD) and 11 (Crypto) first

### 4. Red Team
- **Focus:** C2 frameworks (Cobalt Strike, Mythic), evasion, operational security, TTP mapping
- **Key modules:** C2 infrastructure, phishing, bypassing defenses, threat emulation
- **Prepares you for:** CRTP, CRTO certifications
- **Estimated time:** 60–100 hours
- **Prerequisites:** Strong understanding of Mod 07 (PrivEsc), Mod 08 (MSF), Mod 10 (AD)

### 5. Cyber Defense
- **Focus:** Digital forensics, memory analysis, malware analysis, threat hunting
- **Key modules:** Forensics, memory forensics, YARA, threat intelligence platforms
- **Prepares you for:** GCFA, CHFI certifications
- **Estimated time:** 50–80 hours
- **Leverages from 101:** Mod 12 (Malware), Mod 13 (Wireshark)

---

## Career Paths Unlocked

Each completed phase of Cyber Security 101 qualifies you for progressively senior roles:

### With Modules 1–9 Completed

| Role | Entry Level? | Avg. Salary Range (USD) |
|------|-------------|------------------------|
| Security Administrator | Entry | $55k–$75k |
| IT Security Analyst | Entry | $60k–$80k |
| Network Security Technician | Entry | $50k–$70k |
| Junior Web Application Tester | Entry | $60k–$85k |
| SOC Analyst (Tier 1) | With additional SIEM training | $55k–$75k |

### With All Modules 1–14 Completed

| Role | Level | Avg. Salary Range (USD) |
|------|-------|------------------------|
| Penetration Tester (Junior) | Intermediate | $75k–$105k |
| SOC Analyst (Tier 2) | Intermediate | $70k–$95k |
| Incident Responder | Intermediate | $80k–$110k |
| Security Engineer (Junior) | Intermediate | $85k–$115k |
| Malware Analyst (Junior) | Intermediate | $90k–$120k |
| Red Team Operator (Junior) | Advanced Beginner | $95k–$130k |

### With 101 + Specialised Path Completed

| Role | Level | Avg. Salary Range (USD) |
|------|-------|------------------------|
| Senior Penetration Tester | Senior | $110k–$160k |
| SOC Lead / Threat Hunter | Senior | $100k–$145k |
| Security Architect | Senior | $130k–$180k |
| DFIR Consultant | Senior | $110k–$155k |
| Red Team Lead | Senior | $140k–$190k+ |

---

## Certifications Alignment

Cyber Security 101 directly maps to the knowledge domains of these industry certifications:

| Certification | Relevant Modules | 101 Coverage |
|--------------|-----------------|--------------|
| CompTIA Security+ | 1, 3, 4, 5, 11 | ~70% of SY0-701 domains |
| CompTIA Network+ | 4 | ~60% of N10-009 domains |
| eJPT (elearnSecurity) | 3, 4, 7, 8, 9 | ~80% of exam objectives |
| BTL1 (Blue Team Level 1) | 1, 4, 12, 13 | ~65% of exam objectives |
| PNPT (Practical Network Pen. Tester) | 3, 4, 7, 8, 9, 10 | ~75% of exam objectives |
| OSCP (Offensive Security) | 3, 7, 8, 9, 10, 14 | ~60% (buffer overflow is separate) |

---

## Personal Study Plan

After completing Modules 1–9, the suggested 90-day plan to finish Modules 10–14 and transition to a specialised path:

```
Weeks 1-3:   Module 10 — Active Directory (15 hrs)
             Supplement: HackTheBox AD labs, BloodHound practice

Weeks 4-5:   Module 11 — Cryptography (6 hrs)
             Supplement: Cryptopals challenges, Cryptography I on Coursera

Weeks 6-8:   Module 12 — Malware Analysis (12 hrs)
             Supplement: Practical Malware Analysis (book), FLARE VM

Weeks 9-10:  Module 13 — Wireshark & Traffic Analysis (8 hrs)
             Supplement: Wireshark CTF challenges, MalwareTrafficAnalysis.net

Weeks 11-12: Module 14 — Capstone (7 hrs)
             Followed by: Pick your specialisation path and start applying
```

> **Recommendation:** After Module 14, immediately attempt the **Jr Penetration Tester** path if offensive security is your goal, or **SOC Level 1** if defensive. Do not take a break — momentum is critical at this stage.

---

## Final Notes

The Cyber Security 101 path is one of the most well-structured beginner-to-intermediate programs available for free. Completing it demonstrates dedication, technical aptitude, and a broad understanding of the field. Treat it not as a checklist but as a **foundation** — every room completed is a tool in your belt.

> *"The difference between a script kiddie and a professional is understanding why something works, not just that it works."*

Use this roadmap to guide your next steps, track your progress, and stay focused on your end goal — whether that's a job in security, a certification, or simply the satisfaction of mastering the craft.

---

> **Maintained by @lightyagami** — Last updated: July 2026
