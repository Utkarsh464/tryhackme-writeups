# Nmap Cheat Sheet

## Scan Types
| Command | Description |
|---------|-------------|
| `-sS` | SYN stealth scan (default) |
| `-sT` | TCP connect scan |
| `-sU` | UDP scan |
| `-sA` | ACK scan (firewall mapping) |
| `-sW` | Window scan |
| `-sN` | TCP Null scan |
| `-sF` | FIN scan |
| `-sX` | Xmas scan |
| `-sV` | Version detection |
| `-O` | OS detection |
| `-A` | Aggressive (OS + version + scripts) |

## Scan Options
| Option | Description |
|--------|-------------|
| `-p 80` | Single port |
| `-p 80,443,8080` | Port list |
| `-p 1-1000` | Port range |
| `-p-` | All 65535 ports |
| `--top-ports 100` | Top 100 ports |
| `-T0` to `-T5` | Timing (0=paranoid, 5=insane) |
| `-n` | No DNS resolution |
| `-v` | Verbose |
| `-vv` | Very verbose |
| `-oA basename` | All output formats |
| `-oN file` | Normal output |
| `-oG file` | Grepable output |
| `-oX file` | XML output |

## NSE Scripts
| Script Category | Example |
|-----------------|---------|
| `-sC` or `--script=default` | Default scripts |
| `--script=vuln` | Vulnerability checks |
| `--script=exploit` | Exploit scripts |
| `--script=http-*` | HTTP scripts |
| `--script=smb-*` | SMB scripts |
| `--script=ssh-*` | SSH scripts |

## Host Discovery
| Command | Description |
|---------|-------------|
| `-sn 192.168.1.0/24` | Ping sweep |
| `-PR` | ARP scan (local network) |
| `-PE` | ICMP echo |
| `-PP` | ICMP timestamp |
| `-PM` | ICMP netmask |
| `-PO` | IP protocol ping |