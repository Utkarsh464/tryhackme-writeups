# TryHackMe — Cyber Security 101

> **A complete walkthrough & reference handbook for the TryHackMe Cyber Security 101 learning path.**  
> Covers foundational to intermediate cybersecurity concepts through hands-on rooms, real-world scenarios, and practical tool mastery.

[![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)](#)
[![Modules Completed](https://img.shields.io/badge/Modules%20Completed-9%2F14-brightgreen)](#)
[![Difficulty](https://img.shields.io/badge/Difficulty-Foundation%20to%20Intermediate-blue)](#)
[![Platform](https://img.shields.io/badge/Platform-TryHackMe-red)](#)
[![License](https://img.shields.io/badge/License-MIT-lightgrey)](#)

---

## Table of Contents

- [Learning Path Overview](#learning-path-overview)
- [Quick Navigation](#quick-navigation)
- [Skills Covered](#skills-covered)
- [Tools Mastered](#tools-mastered)
- [How to Use This Handbook](#how-to-use-this-handbook)
- [Module Breakdown](#module-breakdown)
- [Next Steps & Career Paths](#next-steps--career-paths)
- [Resources & References](#resources--references)

---

## Learning Path Overview

The **Cyber Security 101** path on TryHackMe is an entry-to-intermediate level curriculum designed to take a complete beginner and turn them into a capable junior security analyst or penetration tester. The path comprises **14 modules** spanning operating systems, networking, web security, exploitation, forensics, and defensive techniques.

| Status | Detail |
|--------|--------|
| **Modules 1–9** | `COMPLETED` — Core foundations: Linux, Windows, Web, Networks, Python, Privilege Escalation, Metasploit, Burp Suite |
| **Modules 10–14** | `PENDING` — Advanced topics: Active Directory, Cryptography, Malware Analysis, Wireshark, Final Assessment |

Each module contains a series of interactive rooms (virtual machines, challenges, guided exercises) that reinforce the topic through hands-on application. This handbook documents every room with step-by-step solutions, explanations, key takeaways, and optional deep-dives.

---

## Quick Navigation

| Module | Topic | Status |
|--------|-------|--------|
| 01 | Introduction to Cyber Security | ✅ Completed |
| 02 | Linux Fundamentals | ✅ Completed |
| 03 | Web Hacking Fundamentals | ✅ Completed |
| 04 | Network Security | ✅ Completed |
| 05 | Windows Fundamentals | ✅ Completed |
| 06 | Python Basics | ✅ Completed |
| 07 | Privilege Escalation | ✅ Completed |
| 08 | Metasploit Framework | ✅ Completed |
| 09 | Burp Suite | ✅ Completed |
| 10 | Active Directory | ⏳ Pending |
| 11 | Cryptography | ⏳ Pending |
| 12 | Malware Analysis | ⏳ Pending |
| 13 | Wireshark & Traffic Analysis | ⏳ Pending |
| 14 | Final Assessment / Capstone | ⏳ Pending |

---

## Skills Covered

### Completed (Modules 1–9)

- **Cyber Security Foundations** — CIA triad, risk management, security frameworks, threat actors
- **Linux System Administration** — Command-line navigation, file permissions, process management, bash scripting, service configuration
- **Web Application Security** — OWASP Top 10, SQL injection, XSS, CSRF, file inclusion, SSRF, authentication bypasses
- **Network Security & Analysis** — TCP/IP stack, OSI model, subnetting, DNS, HTTP/S, firewalls, IDS/IPS, port scanning
- **Windows Internals** — Active Directory basics, user/group management, Group Policy, registry, event viewer, PowerShell
- **Python for Security** — Scripting, automation, socket programming, HTTP requests, parsing, basic exploitation scripts
- **Privilege Escalation** — Linux kernel exploits, SUID misconfigurations, cron jobs, PATH hijacking, Windows token manipulation, UAC bypass, service exploits
- **Metasploit Framework** — Module structure, staging vs stageless payloads, meterpreter, post-exploitation, pivoting, database integration
- **Burp Suite** — Proxy interception, repeater, intruder, scanner, sequencer, decoder, comparer, extensions (Turbo Intruder, Autorize)

### Pending (Modules 10–14)

- **Active Directory Attacking & Defending** — Kerberos, NTLM, delegation, AS-REP roasting, Kerberoasting, ACL abuse, DCSync
- **Cryptography** — Symmetric vs asymmetric encryption, hashing, PKI, TLS/SSL, digital signatures, cryptanalysis basics
- **Malware Analysis** — Static & dynamic analysis, sandboxing, reverse engineering basics, YARA rules, memory forensics
- **Network Traffic Analysis** — Wireshark filters, protocol dissection, PCAP analysis, traffic forensics, exfiltration detection
- **Capstone Assessment** — Multi-technique scenario combining all previous modules

---

## Tools Mastered

### CLI & System Tools
`bash`, `grep`, `awk`, `sed`, `find`, `chmod`, `chown`, `ps`, `netstat`, `ss`, `systemctl`, `journalctl`, `crontab`, `pwsh`, `cmd`, `regedit`, `mmc`

### Network & Reconnaissance
`nmap`, `netcat`, `socat`, `tcpdump`, `dig`, `nslookup`, `whois`, `curl`, `wget`, `smbclient`, `enum4linux`, `ldapsearch`

### Web Testing & Exploitation
`Burp Suite` (Community & Professional), `sqlmap`, `nikto`, `gobuster`, `ffuf`, `dirb`, `wpscan`, `hydra`, `john`, `hashcat`

### Exploitation Frameworks
`Metasploit` (`msfconsole`, `msfvenom`), `Impacket` (psexec, secretsdump, wmiexec), `BloodHound`, `CrackMapExec`

### Privilege Escalation
`LinPEAS`, `WinPEAS`, `pspy`, `GTFOBins`, `PowerUp`, `Sherlock`, `Seatbelt`, `SharpUp`

### Development & Scripting
`Python 3` (socket, requests, scapy, pwntools, paramiko), `PowerShell`, `bash`

### Forensic & Analysis
`Wireshark`, `strings`, `exiftool`, `binwalk`, `steghide`, `volatility`, `Autopsy`, `YARA`

---

## How to Use This Handbook

```
TryHackMe-CyberSecurity101/
├── README.md           <-- You are here
├── SUMMARY.md          <-- Full room-by-room index with completion status
├── ROADMAP.md          <-- Learning progression & career guidance
├── Module-01-Intro/
│   ├── README.md       <-- Module overview, key concepts
│   └── rooms/          <-- Individual room writeups
├── Module-02-Linux/
│   └── ...
└── Module-14-Capstone/
    └── ...
```

**For learners:** Start from Module 01 and work forward. Each room writeup contains the challenge description, methodology, flags/questions with answers, and explanations.

**For revisers:** Use `SUMMARY.md` to jump directly to any room. Use `ROADMAP.md` to understand how each module fits your career goals.

**For instructors:** Use these materials as a curriculum guide or lab companion. Each module documents expected time, difficulty, and learning objectives.

> **Tip:** Flags and answers are marked with `>!spoiler tags!<` so you can attempt rooms first before peeking.

---

## Module Breakdown

### Module 01 — Introduction to Cyber Security
First steps into the field. Covers security fundamentals, career paths, and the TryHackMe platform itself.
- **Rooms:** Intro to Offensive Security, Intro to Defensive Security, Careers in Cyber
- **Key Outcomes:** Understand red vs blue team roles, CIA triad, basic threat modeling

### Module 02 — Linux Fundamentals
Become comfortable with the Linux command line — the backbone of most security tools.
- **Rooms:** Linux Fundamentals Part 1–3, Linux Challenges
- **Key Outcomes:** Navigate filesystem, manage processes, configure permissions, write bash scripts

### Module 03 — Web Hacking Fundamentals
Learn how web applications work and how they break.
- **Rooms:** Walking an Application, Content Discovery, Subdomain Enumeration, OWASP Top 10 (several), Authentication Bypass, IDOR, File Inclusion, SSRF, XSS, SQL Injection
- **Key Outcomes:** Exploit OWASP Top 10 vulnerabilities, automate recon with ffuf/gobuster

### Module 04 — Network Security
Understand network protocols, attacks, and defenses.
- **Rooms:** Intro to LAN, HTTP in Detail, DNS in Detail, Nmap (LIVE), Network Services, Network Security Protocols, Attacking ICS/SCADA
- **Key Outcomes:** Perform port scans, enumerate services, understand protocol-level attacks

### Module 05 — Windows Fundamentals
Windows OS internals from a security perspective.
- **Rooms:** Windows Fundamentals 1–3, Active Directory Basics
- **Key Outcomes:** Navigate Windows GUI/CLI, understand AD concepts, work with PowerShell

### Module 06 — Python Basics
Python for automating security tasks and writing custom tools.
- **Rooms:** Python Basics, Python for Pentesters, PicoCTF Prep (Python)
- **Key Outcomes:** Write scripts to parse logs, scan ports, connect sockets, interact with APIs

### Module 07 — Privilege Escalation
Escalate from low-privileged to root/administrator on both Linux and Windows.
- **Rooms:** Linux PrivEsc, Windows PrivEsc Arena, Common Linux Privesc, Common Windows Privesc
- **Key Outcomes:** Enumerate misconfigurations, exploit SUID/token/service vulnerabilities

### Module 08 — Metasploit Framework
Industry-standard exploitation framework.
- **Rooms:** Metasploit Introduction, Meterpreter, Post-Exploitation, Msfvenom
- **Key Outcomes:** Use msfconsole for scanning, exploitation, pivoting, and post-exploitation

### Module 09 — Burp Suite
The web penetration tester's Swiss Army knife.
- **Rooms:** Burp Suite Basics, Repeater, Intruder, Extensions, Scanner
- **Key Outcomes:** Intercept and modify HTTP traffic, automate attacks, scan for vulnerabilities

### Modules 10–14
Covering Active Directory attacks, cryptography, malware analysis, Wireshark, and the final capstone. See `SUMMARY.md` for full details.

---

## Next Steps & Career Paths

After completing Cyber Security 101 (Modules 1–14), recommended next paths on TryHackMe:

| Path | Focus Area | Best For |
|------|-----------|----------|
| **Jr Penetration Tester** | Web & network exploitation, report writing | Aspiring pentesters |
| **SOC Level 1** | Blue team, SIEM, incident response, log analysis | Aspiring SOC analysts |
| **Offensive Pentesting** | Advanced exploitation, AD, buffer overflows | Experienced pentesters |
| **Red Team** | C2 frameworks, evasion, TTPs | Advanced red teamers |
| **Cyber Defense** | Forensics, malware analysis, threat hunting | Defenders & DFIR |

See `ROADMAP.md` for a detailed career-oriented breakdown.

---

## Resources & References

- [TryHackMe Cyber Security 101](https://tryhackme.com/path/outline/cybersecurity101)
- [OWASP Top 10 – 2021](https://owasp.org/Top10/)
- [GTFOBins](https://gtfobins.github.io/) — Linux privilege escalation
- [LOLBAS](https://lolbas-project.github.io/) — Windows living-off-the-land
- [HackTricks](https://book.hacktricks.xyz/) — Penetration testing guides
- [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings) — Payload cheatsheets

---

> **Maintained by [@lightyagami]** — This is a living document. Contributions, corrections, and improvements are welcome.  
> *Last updated: July 2026*
