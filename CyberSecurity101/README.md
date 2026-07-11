# TryHackMe — Cyber Security 101

> **A complete walkthrough & reference handbook for the TryHackMe Cyber Security 101 learning path.**  
> Covers foundational to intermediate cybersecurity concepts through hands-on rooms, real-world scenarios, and practical tool mastery.

[![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)](#)
[![Modules Completed](https://img.shields.io/badge/Modules%20Completed-11%2F14-brightgreen)](#)
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
| **Modules 1–11** | `COMPLETED` — Core foundations: Linux, Windows, Web, Networks, Cryptography, Exploitation, Web Hacking, Tooling, Defensive Security, Security Solutions |
| **Modules 12–14** | `PENDING` — Defensive Security Tooling, Cyber Career, OWASP Top 10 (2025) |

Each module contains a series of interactive rooms (virtual machines, challenges, guided exercises) that reinforce the topic through hands-on application. This handbook documents every room with step-by-step solutions, explanations, key takeaways, and optional deep-dives.

---

## Quick Navigation

| Module | Topic | Status |
|--------|-------|--------|
| 01 | Start Your Cyber Security Journey | ✅ Completed |
| 02 | Linux Fundamentals | ✅ Completed |
| 03 | Windows and AD Fundamentals | ✅ Completed |
| 04 | Command Line | ✅ Completed |
| 05 | Networking | ✅ Completed |
| 06 | Cryptography | ✅ Completed |
| 07 | Exploitation Basics | ✅ Completed |
| 08 | Web Hacking | ✅ Completed |
| 09 | Offensive Security Tooling | ✅ Completed |
| 10 | Defensive Security | ✅ Completed |
| 11 | Security Solutions | ✅ Completed |
| 12 | Defensive Security Tooling | ⏳ Pending |
| 13 | Build Your Cyber Security Career | ⏳ Pending |
| 14 | OWASP Top 10 (2025) | ⏳ Pending |

---

## Skills Covered

### Completed (Modules 1–11)

- **Cyber Security Foundations** — CIA triad, risk management, security frameworks, threat actors
- **Linux System Administration** — Command-line navigation, file permissions, process management, bash scripting, service configuration
- **Windows & Active Directory** — User/group management, AD basics, Group Policy, registry, event viewer, PowerShell
- **Command Line** — Windows CMD, PowerShell, Linux shells, shell scripting
- **Networking** — TCP/IP, OSI model, protocols, Wireshark, tcpdump, Nmap
- **Cryptography** — Symmetric & asymmetric encryption, hashing, PKI, John the Ripper
- **Exploitation Basics** — Metasploit, Meterpreter, vulnerability exploitation
- **Web Hacking** — Web apps, JavaScript, SQL, Burp Suite basics
- **Offensive Security Tooling** — Hydra, Gobuster, shells, SQLMap
- **Defensive Security** — SOC fundamentals, digital forensics, incident response, log analysis
- **Security Solutions** — SIEM, firewalls, IDS/IPS, vulnerability scanners

### Pending (Modules 12–14)

- **Defensive Security Tooling** — CyberChef, CAPA, REMnux, FlareVM
- **Build Your Cyber Security Career** — Security principles, career paths, team impact
- **OWASP Top 10 (2025)** — IAAA failures, application design flaws, insecure data handling

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

### Defensive Security & SIEM
`Splunk`, `ELK Stack`, `IBM QRadar`, `Microsoft Sentinel`, `Wazuh`, `Snort`, `Suricata`, `Nessus`, `OpenVAS`, `Qualys`, `iptables`, `nftables`, `pfSense`, `Windows Firewall`

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

### Module 03 — Windows and AD Fundamentals
Windows OS internals and Active Directory from a security perspective.
- **Rooms:** Windows Fundamentals 1–3, Active Directory Basics
- **Key Outcomes:** Navigate Windows GUI/CLI, understand AD concepts, work with PowerShell

### Module 04 — Command Line
Master the command-line interfaces used by security professionals.
- **Rooms:** Windows Command Line, Windows PowerShell, Linux Shells
- **Key Outcomes:** Navigate and administer systems via CMD, PowerShell, and bash

### Module 05 — Networking
Understand network protocols, attacks, and defenses.
- **Rooms:** Networking Concepts, Networking Essentials, Networking Core Protocols, Networking Secure Protocols, Wireshark: The Basics, Tcpdump: The Basics, Nmap: The Basics
- **Key Outcomes:** Perform port scans, analyze traffic, understand protocol-level attacks

### Module 06 — Cryptography
Understand encryption, hashing, and cryptographic attacks.
- **Rooms:** Cryptography Basics, Public Key Cryptography Basics, Hashing Basics, John the Ripper: The Basics
- **Key Outcomes:** Differentiate symmetric vs asymmetric encryption, crack hashes, understand PKI

### Module 07 — Exploitation Basics
Learn to exploit vulnerabilities using industry-standard tools.
- **Rooms:** Moniker Link (CVE-2024-21413), Metasploit: Introduction, Metasploit: Exploitation, Metasploit: Meterpreter, Blue
- **Key Outcomes:** Use Metasploit for scanning, exploitation, pivoting, and post-exploitation

### Module 08 — Web Hacking
Understand web application security and common vulnerabilities.
- **Rooms:** Web Application Basics, JavaScript Essentials, SQL Fundamentals, Burp Suite: The Basics, OWASP Top 10 - 2021
- **Key Outcomes:** Identify web vulnerabilities, use Burp Suite for intercepting and testing

### Module 09 — Offensive Security Tooling
Master essential offensive security tools.
- **Rooms:** Hydra, Gobuster: The Basics, Shells Overview, SQLMap: The Basics
- **Key Outcomes:** Brute-force credentials, enumerate directories, generate shells, automate SQLi

### Module 10 — Defensive Security
Learn SOC operations, forensics, incident response, and log analysis.
- **Rooms:** Defensive Security Intro, SOC Fundamentals, Digital Forensics Fundamentals, Incident Response Fundamentals, Logs Fundamentals
- **Key Outcomes:** Understand blue team roles, analyze logs, respond to incidents

### Module 11 — Security Solutions
Explore fundamental defensive security solutions.
- **Rooms:** Introduction to SIEM, Firewall Fundamentals, IDS Fundamentals, Vulnerability Scanner Overview
- **Key Outcomes:** Understand SIEM architecture, configure firewalls, deploy IDS/IPS, manage vulnerabilities

### Modules 12–14
Covering Defensive Security Tooling, Cyber Career, and OWASP Top 10 (2025). See `SUMMARY.md` for full details.

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
