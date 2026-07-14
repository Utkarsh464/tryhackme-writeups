# Nmap — Study Notes

## Nmap Live Host Discovery

### Techniques
- **ARP Scan** (`-PR`) — Local networks only, most reliable
- **ICMP Echo** (`-PE`) — Standard ping sweep
- **ICMP Timestamp** (`-PP`) — Alternative when echo is blocked
- **ICMP Address Mask** (`-PM`) — Another ICMP alternative
- **TCP SYN Ping** (`-PS`) — SYN to specified port, waits for RST/SYN-ACK
- **TCP ACK Ping** (`-PA`) — ACK to specified port, expects RST
- **UDP Ping** (`-PU`) — UDP to specified port, expects ICMP unreachable

### Target Specification
- Single IP: `10.10.10.10`
- Range: `10.10.10.1-50`
- CIDR: `10.10.10.0/24`
- List: `-iL targets.txt`
- Exclude: `--exclude 10.10.10.10`

## Nmap Basic Port Scans

### Scan Types
| Scan | Flag | Description |
|------|------|-------------|
| TCP SYN Scan (Stealth) | `-sS` | Half-open, sends SYN, reads SYN-ACK/RST |
| TCP Connect Scan | `-sT` | Full TCP handshake, no root needed |
| UDP Scan | `-sU` | Slow, sends empty UDP packets |
| TCP Null Scan | `-sN` | No flags set, expects RST if closed |
| TCP FIN Scan | `-sF` | FIN flag set, expects RST if closed |
| TCP Xmas Scan | `-sX` | FIN+PSH+URG flags set, expects RST if closed |

### Port Specification
- All ports: `-p-`
- Specific ports: `-p 22,80,443`
- Range: `-p 1-1000`
- Top ports: `--top-ports 100`

### State Interpretation
| State | Meaning |
|-------|---------|
| Open | Port accepting connections |
| Closed | Port accessible but no service listening |
| Filtered | Firewall blocking probe |
| Unfiltered | Port accessible but state unknown (ACK scan) |

## Nmap Advanced Port Scans

### TCP ACK Scan (`-sA`)
- Maps firewall rules (not open/closed)
- Filtered = no response (RST not received)
- Unfiltered = RST received

### TCP Window Scan (`-sW`)
- Like ACK scan but examines RST window field
- Open ports may have non-zero window size

### TCP Maimon Scan (`-sM`)
- FIN/ACK probe, expects RST
- BSD systems respond differently

### Idle/Zombie Scan (`-sI`)
- Spoofs source IP through a zombie host
- Uses IPID sequence analysis to infer port state
- Stealthiest scan — impossible to trace back

### Spoofed Source IP (`-S`)
- Requires understanding of response routing
- Won't receive responses unless on-path

## Nmap Post Port Scans

### Service Version Detection
```bash
# Version detection on found ports
nmap -sV 10.10.10.10

# More aggressive version detection
nmap -sV --version-intensity 9 10.10.10.10
```

### OS Fingerprinting
```bash
# OS detection (requires open and closed ports)
nmap -O 10.10.10.10

# Aggressive (OS + version + scripts + traceroute)
nmap -A 10.10.10.10
```

### Nmap Scripting Engine (NSE)
```bash
# Run default scripts
nmap -sC 10.10.10.10

# Run specific script category
nmap --script=vuln 10.10.10.10

# Run individual script
nmap --script=http-title 10.10.10.10

# Run scripts with arguments
nmap --script=ftp-anon --script-args=ftp-anon.maxlist=5 10.10.10.10
```

### Output Formats
```bash
# Normal output
nmap -oN scan.txt 10.10.10.10

# XML (grepable with xsltproc)
nmap -oX scan.xml 10.10.10.10

# Grepable
nmap -oG scan.gnmap 10.10.10.10

# All formats
nmap -oA scan 10.10.10.10
```

## Protocols and Servers

### Common Protocol Vulnerabilities
| Protocol | Port | Common Issues |
|----------|------|---------------|
| Telnet | 23 | Plaintext credentials, no encryption |
| HTTP | 80 | Plaintext traffic, XSS, SQLi |
| FTP | 21 | Anonymous access, plaintext auth |
| SMB | 445 | EternalBlue (MS17-010), anonymous shares |
| SMTP | 25 | Open relay, user enumeration (VRFY, EXPN) |
| POP3 | 110 | Plaintext credentials |
| IMAP | 143 | Plaintext credentials |

### Protocol-Specific Attacks
- **FTP:** Anonymous login (`anonymous:anonymous`), binary mode for downloads
- **SMB:** Null sessions, enum4linux enumeration, PsExec
- **Telnet:** Clear-text credential capture via tcpdump/Wireshark
- **SMTP:** VRFY/EXPN user enumeration, open relay testing

## Net Sec Challenge

Capstone applying all learned skills:
- Nmap host discovery and port scanning
- Service version detection and OS fingerprinting
- NSE script usage
- Protocol-specific exploitation
- Multi-stage flag capture across services
