# Commands Used — Nmap

## Host Discovery

```bash
# ARP scan (local network)
nmap -PR -sn 10.10.10.0/24

# ICMP echo ping sweep
nmap -PE -sn 10.10.10.0/24

# TCP SYN ping to port 80
nmap -PS80 -sn 10.10.10.0/24

# TCP ACK ping to port 80
nmap -PA80 -sn 10.10.10.0/24

# UDP ping
nmap -PU53 -sn 10.10.10.0/24
```

## Basic Port Scans

```bash
# TCP SYN scan (stealth, requires root)
sudo nmap -sS 10.10.10.10

# TCP Connect scan (no root needed)
nmap -sT 10.10.10.10

# UDP scan (slow)
sudo nmap -sU 10.10.10.10

# NULL, FIN, Xmas scans
sudo nmap -sN 10.10.10.10
sudo nmap -sF 10.10.10.10
sudo nmap -sX 10.10.10.10

# Scan specific ports
nmap -p 22,80,443 10.10.10.10

# Scan top 100 ports
nmap --top-ports 100 10.10.10.10

# Scan all 65535 ports
nmap -p- 10.10.10.10
```

## Advanced Port Scans

```bash
# TCP ACK scan (firewall rule mapping)
sudo nmap -sA 10.10.10.10

# TCP Window scan
sudo nmap -sW 10.10.10.10

# TCP Maimon scan
sudo nmap -sM 10.10.10.10

# Idle/Zombie scan (using zombie host)
sudo nmap -sI zombie_ip 10.10.10.10

# Spoof source IP
sudo nmap -S spoofed_ip 10.10.10.10

# Decoy scan (appear as multiple sources)
sudo nmap -D decoy1,decoy2,ME 10.10.10.10
```

## Post Port Scans

```bash
# Service version detection
nmap -sV 10.10.10.10

# OS fingerprinting
sudo nmap -O 10.10.10.10

# Aggressive scan (OS + version + scripts + traceroute)
nmap -A 10.10.10.10

# Default NSE scripts
nmap -sC 10.10.10.10

# Vulnerability scripts
nmap --script=vuln 10.10.10.10

# Specific NSE script
nmap --script=http-title,ssl-enum-ciphers 10.10.10.10

# Output formats
nmap -oN scan.nmap 10.10.10.10
nmap -oX scan.xml 10.10.10.10
nmap -oG scan.gnmap 10.10.10.10
nmap -oA scan 10.10.10.10
```

## Common Protocol Commands

```bash
# FTP connection
ftp 10.10.10.10

# SMB enumeration
smbclient -L //10.10.10.10 -N
enum4linux 10.10.10.10

# Telnet connection
telnet 10.10.10.10 23

# SMTP user enumeration
nc -nv 10.10.10.10 25
VRFY root
EXPN admin
```
