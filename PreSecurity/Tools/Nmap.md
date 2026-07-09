# Nmap

## Purpose
Network scanner for host discovery, port scanning, service/version detection, OS fingerprinting, and script-based vulnerability scanning.

## Installation
```bash
sudo apt install nmap          # Debian/Ubuntu
sudo yum install nmap          # RHEL/CentOS
sudo pacman -S nmap            # Arch
```

## Basic Usage
```bash
nmap -sV 192.168.1.1                    # Version detection
nmap -p- target.com                   # Scan all 65535 ports
nmap -sC target.com                   # Default scripts
nmap -sS -O target.com                # SYN stealth + OS detection
nmap -A target.com                    # Aggressive (all features)
```

## Important Commands
- `nmap -sn 192.168.1.0/24` - Ping sweep subnet
- `nmap -sU target.com` - UDP scan
- `nmap --script vuln target.com` - Vulnerability scripts
- `nmap -p 80,443 --script=http-* target.com` - HTTP-specific scripts
- `nmap -sV --version-intensity 9 target.com` - Aggressive version detection
- `nmap -T4 -A -v target.com` - Fast aggressive scan with verbosity

## Typical Workflow
1. Host discovery: `nmap -sn subnet/24` to find live hosts
2. Port scan: `nmap -p- target` for all ports or `nmap -top-ports 1000 target`
3. Service/version detection: `nmap -sV -p ports target`
4. Script scan: `nmap -sC target` or targeted `--script`
5. OS detection: `nmap -O target`

## Official Documentation
https://nmap.org/docs.html