# TryHackMe Write-ups

Structured documentation, walkthroughs, and study notes from my TryHackMe learning journey. Covers network fundamentals, operating systems, web security, penetration testing methodology, and hands-on tool usage across multiple learning paths.

## Current Progress

| Path | Status |
|------|--------|
| Pre-Security | ✅ Completed |
| Cyber Security 101 | ✅ Completed (14/14 modules) |
| Jr Penetration Tester | 🟡 In Progress (4/15 modules — 27% complete) |

---

## Pre-Security

**SEC0 Professional Certification:** Unlocked

Foundational knowledge covering computer hardware, networking, web technologies, operating systems, programming basics, and real-world attacks and defenses.

👉 **[PreSecurity/](./PreSecurity/README.md)** — Full documentation with modules, rooms, concepts, commands, tools, cheatsheets, diagrams, interview questions, and revision notes.

### Modules Covered

1. [Introduction to Cyber Security](./PreSecurity/Modules/Module-01-Introduction-to-Cyber-Security/rooms.md) — Offensive vs defensive security, career pathways
2. [Network Fundamentals](./PreSecurity/Modules/Module-02-Network-Fundamentals/rooms.md) — OSI/TCP-IP models, protocols, ports, subnetting
3. [How The Web Works](./PreSecurity/Modules/Module-03-How-The-Web-Works/rooms.md) — DNS, HTTP, HTML, full request lifecycle
4. [Computer Fundamentals](./PreSecurity/Modules/Module-04-Computer-Fundamentals/rooms.md) — CPU, RAM, storage, cloud computing
5. [Operating Systems Basics](./PreSecurity/Modules/Module-05-Operating-Systems-Basics/rooms.md) — Windows & Linux, kernels, processes, file systems
6. [Software Basics](./PreSecurity/Modules/Module-06-Software-Basics/rooms.md) — Binary, Python, JavaScript, SQL
7. [Attacks and Defenses](./PreSecurity/Modules/Module-07-Attacks-and-Defenses/rooms.md) — Cyber Kill Chain, MITRE ATT&CK, incident response

---

## Cyber Security 101

A 14-module path covering operating systems, networking, web security, exploitation, forensics, and defensive techniques.

👉 **[CyberSecurity101/](./CyberSecurity101/README.md)**

### Modules Covered

1. [Start Your Cyber Security Journey](./CyberSecurity101/Modules/Module-01-Start-Your-Cybersecurity-Journey/rooms.md) — Offensive vs defensive security, search skills
2. [Linux Fundamentals](./CyberSecurity101/Modules/Module-02-Linux-Fundamentals/rooms.md) — Linux command line, file permissions, process management, bash scripting
3. [Windows and AD Fundamentals](./CyberSecurity101/Modules/Module-03-Windows-and-AD-Fundamentals/rooms.md) — Windows OS, Active Directory, Group Policy, PowerShell
4. [Command Line](./CyberSecurity101/Modules/Module-04-Command-Line/rooms.md) — Windows CMD, PowerShell, Linux shells, shell scripting
5. [Networking](./CyberSecurity101/Modules/Module-05-Networking/rooms.md) — TCP/IP, protocols, Wireshark, tcpdump, Nmap
6. [Cryptography](./CyberSecurity101/Modules/Module-06-Cryptography/rooms.md) — Symmetric/asymmetric encryption, hashing, PKI, John the Ripper
7. [Exploitation Basics](./CyberSecurity101/Modules/Module-07-Exploitation-Basics/rooms.md) — Metasploit, Meterpreter, CVE exploitation
8. [Web Hacking](./CyberSecurity101/Modules/Module-08-Web-Hacking/rooms.md) — Web apps, JavaScript, SQL, Burp Suite, OWASP Top 10 2021
9. [Offensive Security Tooling](./CyberSecurity101/Modules/Module-09-Offensive-Security-Tooling/rooms.md) — Hydra, Gobuster, shells, SQLMap
10. [Defensive Security](./CyberSecurity101/Modules/Module-10-Defensive-Security/rooms.md) — SOC fundamentals, digital forensics, incident response, log analysis
11. [Security Solutions](./CyberSecurity101/Modules/Module-11-Security-Solutions/rooms.md) — SIEM, firewalls, IDS/IPS, vulnerability scanners
12. [Defensive Security Tooling](./CyberSecurity101/Modules/Module-12-Defensive-Security-Tooling/rooms.md) — CyberChef, CAPA, REMnux, FlareVM
13. [Build Your Cyber Security Career](./CyberSecurity101/Modules/Module-13-Cyber-Career-Path/rooms.md) — Security principles, career paths, training impact
14. [Final Assessment: OWASP Top 10 2025](./CyberSecurity101/Modules/Module-14-Final-Assessment/rooms.md) — OWASP Top 10 2025 hands-on capstone

---

## Jr Penetration Tester

🟡 **In Progress** — 27% complete (4/15 modules). Next module: Introduction to Web Hacking.

Penetration testing methodology, network reconnaissance, and Nmap scanning — building toward full-spectrum offensive security skills.

👉 **[jr-penetration-tester/](./jr-penetration-tester/README.md)**

### Modules Covered

1. [Start Your Cyber Security Journey](./jr-penetration-tester/01-start-your-cyber-security-journey/README.md) — Red vs blue team, ethical hacking foundations, career pathways ✅
2. [Penetration Testing Foundations](./jr-penetration-tester/02-penetration-testing-foundations/README.md) — Pentest methodology, ROE, CIA triad, STRIDE, incident response ✅
3. [Network Reconnaissance](./jr-penetration-tester/03-network-reconnaissance/README.md) — Passive and active recon, OSINT, DNS enumeration, WHOIS ✅
4. [Nmap](./jr-penetration-tester/04-nmap/README.md) — Host discovery, port scanning, service detection, NSE, protocol security ✅

---

## Other Standalone Rooms

| Room | Category | Status |
|------|----------|--------|
| [Cache Me Outside](./Other-Rooms/Cache-Me-Outside/writeup.md) | OSINT | ✅ Completed |

OSINT investigation tracking a retired hacker's digital footprint across Komoot, GitHub, Threads, and email — covering public profile correlation, Git commit metadata leaks, active OSINT via auto-replies, image geolocation, and transit route reconstruction.

---

## Repository Structure

```
tryhackme-writeups/
├── README.md                   <-- You are here
├── PreSecurity/                <-- Pre-Security path (7 modules, completed)
├── CyberSecurity101/           <-- Cyber Security 101 path (14 modules, completed)
├── jr-penetration-tester/      <-- Jr Penetration Tester path (27% completed)
└── Other-Rooms/                <-- Standalone room writeups
```

Each path directory follows a consistent structure:
```
Path/
├── README.md           Path overview and navigation
├── SUMMARY.md          Module and room index with completion status
├── ROADMAP.md          Learning progression and career guidance
└── module-name/
    ├── README.md       Module overview
    ├── notes/          Detailed study notes
    ├── commands.md     Commands and tools used
    ├── concepts.md     Important concepts
    ├── references.md   References and further reading
    └── screenshots/    Lab screenshots
```

## Skills & Tools

### Completed Paths
- **Foundations** — CIA triad, network fundamentals (OSI, TCP/IP, DNS, HTTP), computer hardware, OS administration (Linux & Windows), programming basics (Python, JavaScript, SQL)
- **Cyber Security 101** — Linux/Windows/AD administration, cryptography, exploitation (Metasploit), web hacking (Burp Suite, OWASP Top 10), defensive security (SIEM, forensics, IR), malware analysis tooling

### In Progress
- **Jr Penetration Tester** — Pentesting methodology, network recon, Nmap scanning, protocol security

### Tools Covered
`nmap` `burpsuite` `wireshark` `metasploit` `gobuster` `hydra` `sqlmap` `john` `hashcat` `nikto` `tcpdump` `curl` `dig` `nslookup` `whois` `dnsrecon` `netcat` `socat` `smbclient` `enum4linux` `ldapsearch` `python` `powershell` `bash`

---

## Related Repositories

| Repo | Description | Status |
|------|-------------|--------|
| [Metasploit Labs](https://github.com/Utkarsh464/metasploit-labs) | Hands-on penetration testing labs using Metasploit, Nmap, and intentionally vulnerable machines (Metasploitable 2). Covers enumeration, exploitation, troubleshooting, and post-exploitation validation. | ✅ Active |

---

## Contribution

This is a personal study repository documenting my learning progress. If you spot an error or have a suggestion, feel free to open an issue or pull request.

---

## License

This project is licensed under the MIT License — see the LICENSE file for details.

---

> **Profile:** [utkarsshh](https://tryhackme.com/p/utkarsshh) | **GitHub:** [Utkarsh464](https://github.com/Utkarsh464)
> **Maintained by @lightyagami** — *Last updated: July 2026*
