# TryHackMe Pre-Security Path — Complete Walkthrough

**Path:** Pre-Security  
**Difficulty:** Beginner  
**Time:** ~10–15 hours  
**Certificate:** Included

## What is Pre-Security?

The Pre-Security path teaches how technology works from the ground up. No prior experience needed — it covers computer systems, networking, how the web works, and basic cyber attacks & defences. It's the starting point for anyone entering cybersecurity.

---

## Module 1: Cyber Security Introduction

### Careers in Cyber

An overview of cybersecurity roles and how to get started.

| Role | Description |
|------|-------------|
| Security Analyst | Monitor, detect, respond to threats |
| Penetration Tester | Authorized attacker, find vulnerabilities |
| SOC Analyst | SIEM monitoring, alert triage, IR |
| Security Engineer | Build and maintain security infrastructure |
| Forensic Analyst | Investigate incidents, recover evidence |
| Malware Analyst | Reverse engineer malicious software |
| GRC Analyst | Governance, risk, compliance |
| CISO | Executive security leadership |

**Key takeaway:** Hands-on skills, CTFs, and home labs matter more than certs for entry-level roles.

---

## Module 2: Network Fundamentals

### What is Networking?

Core networking concepts:

- **OSI Model:** 7 layers — Physical → Application
- **TCP/IP Model:** 4 layers — Network Interface → Application
- **IPv4 vs IPv6:** Addressing, subnetting basics
- **Protocols:** TCP (reliable), UDP (fast), ICMP (ping), ARP
- **Common Ports:** 22 (SSH), 80 (HTTP), 443 (HTTPS), 21 (FTP)
- **Network Types:** LAN, WAN, MAN, PAN

**Commands:**
```bash
ip a                # View network interfaces
ping 8.8.8.8        # Test connectivity
netstat -tuln       # List listening ports
```

---

## Module 3: How The Web Works

### How Websites Work

- HTML structure: tags, attributes, forms, comments
- JavaScript: client-side logic, DOM interaction
- DevTools: inspect elements, network tab, console
- HTML injection via unsanitized form inputs

### DNS in Detail

- DNS hierarchy: Root → TLD → Authoritative
- Record types: A, AAAA, CNAME, MX, TXT, NS
- Resolution flow: recursive resolver → root → TLD → authoritative

**Commands:**
```bash
nslookup example.com
nslookup -type=MX example.com
dig example.com ANY
dig +trace example.com
```

### HTTP in Detail

- Methods: GET, POST, PUT, DELETE, PATCH
- Status codes: 1xx (info), 2xx (success), 3xx (redirect), 4xx (client error), 5xx (server error)
- Headers: Content-Type, Authorization, Cookie, User-Agent
- HTTPS: TLS/SSL encryption

**Commands:**
```bash
curl -v http://example.com
curl -X POST -d "user=test" http://example.com/login
curl -A "Mozilla/5.0" http://example.com
curl -b "session=abc" http://example.com/dashboard
```

### Putting it all together

Full request flow:
1. User types URL in browser
2. DNS lookup resolves domain to IP
3. TCP handshake (SYN, SYN-ACK, ACK)
4. HTTP request sent to server
5. Server processes request (backend logic)
6. HTTP response returned with status code and content
7. Browser renders HTML/CSS/JS

---

## Module 4: Linux Fundamentals

### Linux Fundamentals Part 1

Essential Linux commands:

| Command | Purpose |
|---------|---------|
| `pwd` | Print working directory |
| `ls` | List files/directories |
| `cd` | Change directory |
| `cat` | View file contents |
| `touch` | Create empty file |
| `mkdir` | Create directory |
| `cp`, `mv`, `rm` | Copy, move, delete |
| `chmod`, `chown` | Change permissions/ownership |
| `find`, `grep` | Search files and content |
| `sudo` | Execute as superuser |

---

## Module 5: Windows Fundamentals

### Windows Fundamentals 1

- **Desktop:** Taskbar, Start Menu, File Explorer, System Tray
- **NTFS:** Permissions, Alternate Data Streams (ADS), encryption
- **UAC:** User Account Control — prevents unauthorized admin changes
- **Task Manager:** Processes, performance, startup apps, services
- **Control Panel:** User accounts, firewall, device manager, system settings

---

## Module 6: Web Security Fundamentals

### Search Skills

Advanced searching techniques:

- **Google dorks:** `site:`, `filetype:`, `intitle:`, `inurl:`
- **Shodan:** Search internet-connected devices
- **CVE databases:** Search known vulnerabilities
- **GitHub search:** Find repos, leaked credentials, code

### OWASP Top 10 2025: IAAA Failures

Three categories:

**A01 — Broken Access Control:**
- IDOR: Manipulating object references (e.g., `/user/123` → `/user/124`)
- Path traversal: `../../../etc/passwd`
- Missing function-level access controls

**A07 — Identification & Authentication Failures:**
- Weak passwords, credential stuffing
- No MFA/2FA
- Session fixation / hijacking
- Plaintext credentials in logs or URLs

**A09 — Security Logging & Monitoring Failures:**
- Insufficient logging of auth events
- No brute force alerts
- Missing audit trails

---

## Module 7: Operating System Basics

### Operating Systems: Introduction

- **OS Types:** Windows, Linux, macOS, Android, iOS, RTOS
- **Kernel:** Manages hardware, memory, processes
- **Process Scheduling:** CPU time allocation, context switching
- **Memory Management:** Virtual memory, paging, segmentation
- **File Systems:** NTFS (Windows), ext4 (Linux), APFS (macOS), FAT32

### Inside a Computer System

| Component | Function |
|-----------|----------|
| CPU | Executes instructions, cores, cache |
| RAM | Volatile memory for active processes |
| Storage | HDD (mechanical) / SSD (flash) |
| Motherboard | Connects all components |
| GPU | Graphics rendering, parallel compute |
| PSU | Power supply |

### Computer Types

- **Desktop:** Modular, high performance
- **Laptop:** Portable all-in-one
- **Server:** Always-on, headless, high throughput
- **Embedded:** Dedicated function (IoT, routers)
- **Microcontroller:** Single-chip (Arduino, ESP32)
- **Smartphone:** Mobile + cellular
- **Mainframe:** Enterprise-scale
- **Supercomputer:** Extreme scientific computing

---

## Module 8: Offensive & Defensive Security

### Offensive Security Intro

First hack — command injection on a ping form:

```
127.0.0.1 && cat flag.txt
```

The unsanitized input was passed directly to the system shell, allowing command chaining.

**Lesson:** Always validate and sanitize user input before passing it to system commands.

### Defensive Security Intro

Protecting FakeBank from an active attack:
1. Analysed network traffic for suspicious connections
2. Checked firewall logs
3. Identified malware indicators (processes, registry)
4. Isolated affected systems
5. Documented and recommended controls

**Key difference:** Offensive = find & exploit. Defensive = detect & protect.

---

## Final Thoughts

The Pre-Security path is the perfect starting point. It takes you from zero knowledge to understanding the fundamentals of how computers, networks, and the web operate — and how to attack and defend them. Every concept is hands-on with an interactive terminal.

**Next steps:** Complete the SOC Level 1 path or Jr Penetration Tester path to build on these foundations.

---

*Room completion date: June 2026*  
*TryHackMe profile: https://tryhackme.com/p/utkarshsolanki776*
