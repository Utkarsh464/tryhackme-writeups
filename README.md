# TryHackMe Write-ups

Structured technical documentation from my TryHackMe learning progress. Each room I complete gets a writeup covering the methodology, commands, concepts, and tools I used — organized by learning path and module for reference and review.

| Path                  | Status                           |
| --------------------- | -------------------------------- |
| Pre-Security          | Completed                        |
| Cyber Security 101    | Completed (14/14 modules)        |
| Jr Penetration Tester | In progress (27% — 4/15 modules) |

---

## Table of Contents

- [Learning Paths](#learning-paths)
  - [Pre-Security](#pre-security)
  - [Cyber Security 101](#cyber-security-101)
  - [Jr Penetration Tester](#jr-penetration-tester)
- [Standalone Rooms](#standalone-rooms)
- [Skills and Tools](#skills-and-tools)
- [Repository Structure](#repository-structure)
- [Related Repositories](#related-repositories)
- [License](#license)
- [TryHackMe Profile](#tryhackme-profile)

---

## Learning Paths

---

## Pre-Security

SEC0 Professional Certification earned. Foundational knowledge across networking, operating systems, web technologies, and security operations.

[PreSecurity/](./PreSecurity/README.md) — 7 modules, 31 rooms with room-level writeups, concept deep-dives, command references, tool guides, cheat sheets, diagrams, and interview questions.

1. [Introduction to Cyber Security](./PreSecurity/Modules/Module-01-Introduction-to-Cyber-Security/rooms.md) — Offense and defense fundamentals, career pathways
2. [Network Fundamentals](./PreSecurity/Modules/Module-02-Network-Fundamentals/rooms.md) — OSI/TCP-IP, protocols, ports, subnetting
3. [How The Web Works](./PreSecurity/Modules/Module-03-How-The-Web-Works/rooms.md) — DNS, HTTP, request lifecycle
4. [Computer Fundamentals](./PreSecurity/Modules/Module-04-Computer-Fundamentals/rooms.md) — CPU, RAM, storage, cloud computing
5. [Operating Systems Basics](./PreSecurity/Modules/Module-05-Operating-Systems-Basics/rooms.md) — Windows and Linux internals, CLI, permissions
6. [Software Basics](./PreSecurity/Modules/Module-06-Software-Basics/rooms.md) — Binary, Python, JavaScript, SQL
7. [Attacks and Defenses](./PreSecurity/Modules/Module-07-Attacks-and-Defenses/rooms.md) — Cyber Kill Chain, MITRE ATT&CK, incident response

---

## Cyber Security 101

Expanded foundations with hands-on tooling — 14 modules covering operating systems, networking, cryptography, exploitation, web security, defensive operations, and career preparation.

[CyberSecurity101/](./CyberSecurity101/README.md) — 14 modules, 54 rooms with the same structured format plus tool guides and architecture diagrams.

---

## Jr Penetration Tester

27% complete (4/15 modules). Next module: Introduction to Web Hacking.

[jr-penetration-tester/](./jr-penetration-tester/README.md)

1. [Pentesting Foundations](./jr-penetration-tester/01-pentesting-foundations/README.md) — Red and blue team roles, ethical hacking foundations
2. [Network Reconnaissance](./jr-penetration-tester/02-network-reconnaissance/README.md) — Passive and active recon, OSINT, DNS enumeration
3. [Nmap](./jr-penetration-tester/03-nmap/README.md) — Host discovery, port scanning, service detection, NSE scripting
4. [Web App Fundamentals](./jr-penetration-tester/04-web-app-fundamentals/README.md) — OWASP Top 10, HTTP methods, directory brute-forcing, Burp Suite basics

---

## Standalone Rooms

| Room             | Category     | Writeup                                                 |
| ---------------- | ------------ | ------------------------------------------------------- |
| Cache Me Outside | OSINT        | [writeup.md](./Other-Rooms/Cache-Me-Outside/writeup.md) |
| Cowboy Hacker    | Exploitation | [writeup.md](./Other-Rooms/Cowboy-Hacker/writeup.md)    |
| Pickle Rick      | Web Exploit  | [writeup.md](./Other-Rooms/Pickle-Rick/writeup.md)      |

---

## Skills and Tools

**Foundations:** Networking (OSI, TCP/IP, DNS, HTTP), operating systems (Linux, Windows), programming (Python, JavaScript, SQL), cryptography, web technologies, security operations (CIA triad, Cyber Kill Chain, MITRE ATT&CK, incident response)

**Offensive:** Nmap, Metasploit, Burp Suite, Hydra, Gobuster, SQLMap, John the Ripper, Nikto, netcat, enumeration techniques, exploitation methodology

**Defensive:** SIEM fundamentals, Wireshark, tcpdump, digital forensics, IDS/IPS, vulnerability scanning, log analysis, malware analysis tooling (REMnux, FlareVM, CAPA)

---

## Repository Structure

```
tryhackme-writeups/
├── PreSecurity/            7 modules, 31 rooms, completed
├── CyberSecurity101/       14 modules, 54 rooms, completed
├── jr-penetration-tester/  4/15 modules, in progress
└── Other-Rooms/            Standalone writeups
```

Each path directory includes: room-level writeups (metadata, tasks, commands, concepts, tools), concept references, command guides, tool documentation, cheat sheets, diagrams, interview questions, and revision summaries.

---

## Related Repositories

This repo holds TryHackMe room notes. For web-security lab writeups see [portswigger-academy](https://github.com/Utkarsh464/portswigger-academy), for machine exploitation see [labs](https://github.com/Utkarsh464/labs), and for condensed reference notes see [Notes-cyber-security](https://github.com/Utkarsh464/Notes-cyber-security).

- [labs](https://github.com/Utkarsh464/labs) — Metasploitable 2 penetration testing labs
- [portswigger-academy](https://github.com/Utkarsh464/portswigger-academy) — Web security lab writeups
- [chat-server](https://github.com/Utkarsh464/chat-server) — Multi-threaded TCP chat server in Python
- [Notes-cyber-security](https://github.com/Utkarsh464/Notes-cyber-security) — Structured study notes

---

## License

MIT — see [LICENSE](./LICENSE).

---

## TryHackMe Profile

> TryHackMe profile: [utkarsshh](https://tryhackme.com/p/utkarsshh)
> Last updated: August 2026
