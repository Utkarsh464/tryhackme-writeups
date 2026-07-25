# Important Concepts — Nmap

## Nmap Concepts

| Concept | Description |
|---------|-------------|
| Host Discovery | Finding live hosts on a network |
| Port Scanning | Determining which ports are open/closed/filtered |
| Service Detection | Identifying running services and their versions |
| OS Fingerprinting | Determining target operating system |
| NSE | Nmap Scripting Engine — automated enumeration and vuln detection |
| NSE Categories | default, vuln, exploit, discovery, safe, auth, brute |
| TCP SYN Scan | Half-open stealth scan (requires root) |
| TCP Connect Scan | Full handshake, logged by apps (no root needed) |
| UDP Scan | Slow, unreliable, send empty UDP packets |
| NULL/FIN/Xmas | Stealth scans using unusual flag combinations |
| Idle/Zombie Scan | Completely blind scan through zombie host |
| Decoy Scan | Appears as multiple source IPs |

## Protocol Concepts

| Concept | Description |
|---------|-------------|
| Plaintext Protocols | Credentials transmitted without encryption (Telnet, FTP, HTTP) |
| Anonymous Access | FTP/SMB allowing guest or anonymous login |
| SMB Null Session | Unauthenticated access to Windows shares |
| SMTP VRFY/EXPN | User enumeration via mail server commands |
| Open Relay | SMTP server forwarding mail from anyone (spam risk) |

## Scan Types Summary

| Scan Type | Flag | Best For |
|-----------|------|----------|
| SYN | `-sS` | Stealth, speed (default with root) |
| Connect | `-sT` | No root, compatibility |
| UDP | `-sU` | UDP services (slow) |
| NULL | `-sN` | Firewall evasion (stateless) |
| FIN | `-sF` | Firewall evasion |
| Xmas | `-sX` | Firewall evasion |
| ACK | `-sA` | Firewall rule mapping |
| Window | `-sW` | Firewall rule mapping (with port state) |
| Maimon | `-sM` | BSD-specific behaviour |
| Idle | `-sI` | Maximum stealth (zombie host) |
