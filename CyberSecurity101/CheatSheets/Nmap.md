# Nmap Cheat Sheet

## Scan Types
| Command | Description |
|---------|-------------|
| `nmap -sT target` | TCP Connect scan (default, no root) |
| `nmap -sS target` | SYN half-open scan (requires root) |
| `nmap -sU target` | UDP scan (slow) |
| `nmap -sA target` | ACK scan (firewall mapping) |
| `nmap -sW target` | Window scan |
| `nmap -sM target` | Maimon scan |
| `nmap -sN target` | TCP Null scan |
| `nmap -sF target` | FIN scan |
| `nmap -sX target` | Xmas scan |
| `nmap -sV target` | Version detection |
| `nmap -O target` | OS detection |

## Port Specification
| Command | Description |
|---------|-------------|
| `-p 80` | Single port |
| `-p 80,443,8080` | Multiple ports |
| `-p 1-1000` | Range |
| `-p-` | All ports (1-65535) |
| `--top-ports 100` | Top 100 common ports |
| `-p http,https` | Service name |
| `-p T:80,U:53` | TCP and UDP ports |

## Output Formats
| Command | Description |
|---------|-------------|
| `-oN output.nmap` | Normal output |
| `-oX output.xml` | XML output |
| `-oG output.gnmap` | Grepable output |
| `-oA basename` | All formats |
| `-oS output.txt` | Script kiddie format |
| `--stylesheet` | Custom XSL stylesheet |

## Timing Templates
| Template | Name | Speed |
|----------|------|-------|
| `-T0` | Paranoid | Very slow, evades IDS |
| `-T1` | Sneaky | Slow, evades IDS |
| `-T2` | Polite | Slows to < 1 Mbps |
| `-T3` | Normal | Default |
| `-T4` | Aggressive | Fast, assumes good network |
| `-T5` | Insane | Very fast, may miss ports |

## Performance Options
| Command | Description |
|---------|-------------|
| `--min-hostgroup 256` | Min parallel hosts |
| `--max-hostgroup 512` | Max parallel hosts |
| `--min-parallelism 64` | Min probes parallel |
| `--max-parallelism 256` | Max probes parallel |
| `--min-rtt-timeout 100ms` | Min RTT |
| `--max-rtt-timeout 1000ms` | Max RTT |
| `--host-timeout 30m` | Abort after timeout |
| `--scan-delay 1s` | Delay between probes |

## Host Discovery
| Command | Description |
|---------|-------------|
| `-sL` | List targets (no scan) |
| `-sn` | Ping sweep only |
| `-Pn` | Skip host discovery |
| `-PS22,80` | TCP SYN ping |
| `-PA80` | TCP ACK ping |
| `-PU53` | UDP ping |
| `-PE` | ICMP echo ping |
| `-PP` | ICMP timestamp ping |
| `-PM` | ICMP netmask ping |
| `-PO` | IP protocol ping |
| `--disable-arp-ping` | Disable ARP |

## NSE Scripts
| Command | Description |
|---------|-------------|
| `-sC` | Default safe scripts |
| `--script=vuln` | Vulnerability checks |
| `--script=http-headers` | HTTP headers |
| `--script=http-enum` | Web enumeration |
| `--script=smb-enum-shares` | SMB shares |
| `--script=dns-brute` | DNS subdomain brute |
| `--script=ssh-brute` | SSH brute force |
| `--script=mysql-enum` | MySQL enumeration |
| `--script-args` | Script arguments |
| `--script-updatedb` | Update NSE database |

## Common Examples
```bash
# Quick service scan
nmap -sV -sC -T4 -p- -oA quick 192.168.1.1

# Full port + version + OS
nmap -sS -sV -O -p- -T4 192.168.1.1-254

# Firewall detection
nmap -sA -T4 192.168.1.1

# UDP scan
nmap -sU --top-ports 20 target

# Web server enumeration
nmap -p 80,443 --script=http-* target

# Network sweep
nmap -sn 192.168.1.0/24

# Subnet scan with all outputs
nmap -sV -p- -T4 -oA subnet_scan 10.10.10.0/24

# Specific ports + NSE
nmap -p 3306 --script=mysql-* target

# Evasion
nmap -f -D RND:10 --data-length 200 -g 53 target
```

## Evasion Options
| Command | Description |
|---------|-------------|
| `-f` | Fragment packets |
| `-D RND:10` | Decoy scans |
| `--data-length 200` | Pad packets |
| `-g 53` | Source port spoof |
| `--ttl 128` | Custom TTL |
| `--spoof-mac 0` | Random MAC |
| `--proxies http://proxy:8080` | Proxy |

## Target Specification
| Format | Example |
|--------|---------|
| Single IP | `192.168.1.1` |
| Range | `192.168.1.1-100` |
| CIDR | `192.168.1.0/24` |
| File | `-iL targets.txt` |
| Random | `-iR 100` |
| Exclude | `--exclude 192.168.1.1` |
