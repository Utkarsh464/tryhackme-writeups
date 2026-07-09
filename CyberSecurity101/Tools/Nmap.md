# Nmap (Network Mapper)

## Purpose
Nmap (Network Mapper) is a free and open-source utility for network discovery and security auditing. It is used to discover hosts and services on a computer network, identify operating systems, detect open ports, enumerate service versions, and perform advanced network reconnaissance. Created by Gordon Lyon (Fyodor), Nmap is an essential tool for network inventory, security assessments, and penetration testing.

## Installation
Nmap is pre-installed on Kali Linux. To install on other systems:
```bash
# Debian/Ubuntu
sudo apt update && sudo apt install nmap

# Red Hat/CentOS/Fedora
sudo yum install nmap

# macOS
brew install nmap

# Windows
Download installer from https://nmap.org/download.html

# Build from source
wget https://nmap.org/dist/nmap-7.94.tar.bz2
bzip2 -cd nmap-*.tar.bz2 | tar xvf -
cd nmap-* && ./configure && make && sudo make install
```

## Basic Usage
Nmap is run from the command line with targets and options:
```bash
# Quick scan of top 1000 ports
nmap 192.168.1.1

# Service version detection
nmap -sV 192.168.1.1

# OS detection
nmap -O 192.168.1.1

# Full port range scan
nmap -p- 192.168.1.1

# Aggressive scan with all features
nmap -A 192.168.1.1
```

## Important Commands
- `-sS` - TCP SYN stealth scan (default, requires root)
- `-sT` - TCP connect scan (no root required)
- `-sU` - UDP port scan
- `-sV` - service/version detection
- `-O` - OS detection
- `-A` - aggressive scan (OS, version, script, traceroute)
- `-p <ports>` - specify port range (e.g., `-p 22,80,443` or `-p-` for all)
- `-Pn` - skip host discovery (assume host is up)
- `-T<0-5>` - timing template (0=paranoid, 3=normal, 5=insane)
- `-oN/-oX/-oG/-oA` - output to normal/XML/grepable/all formats
- `-sC` - run default NSE scripts
- `--script=<script>` - run specific NSE script
- `-sn` - ping sweep only (no port scan)
- `-v` - increase verbosity
- `--reason` - show why ports are in a given state

## Typical Workflow
1. Identify live hosts: `nmap -sn 10.10.10.0/24`
2. Perform detailed scan on discovered hosts: `nmap -sC -sV -O -p- 10.10.10.10`
3. Run vulnerability scripts: `nmap --script vuln 10.10.10.10`
4. Enumerate specific services: `nmap --script smb-enum-shares -p 445 10.10.10.10`
5. Save results: `nmap -sC -sV -oA target_scan 10.10.10.10`
6. Parse XML output with tools like Ndiff for comparison across scans

## Advantages
- Extremely fast and efficient scanning engine
- Highly customizable with hundreds of options and NSE scripts
- Cross-platform (Linux, Windows, macOS)
- Active community maintaining NSE script database
- Scriptable output formats for integration with other tools
- Can bypass basic firewalls with fragmentation and decoy options

## Limitations
- SYN scans require root privileges
- Stealth scanning is increasingly detectable by modern IDS/IPS
- OS detection can be inaccurate against hardened systems
- UDP scans are slow and unreliable
- Rate limiting can cause false negatives
- Some advanced evasion techniques require deep network knowledge

## Industry Use
Nmap is a standard tool for network inventory, vulnerability assessment, penetration testing, and security auditing. It is used by system administrators to discover unauthorized services, by security teams during incident response to map network segments, and by penetration testers as the first step in the reconnaissance phase.

## Official Documentation
- Official Site: https://nmap.org
- Documentation: https://nmap.org/docs.html
- Book: https://nmap.org/book/
- NSE Scripts: https://nmap.org/nsedoc/
- GitHub: https://github.com/nmap/nmap
