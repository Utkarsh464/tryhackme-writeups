# Nmap: The Basics — Commands

| Command | Description |
|---------|-------------|
| `nmap -sn 192.168.1.0/24` | Ping sweep to discover live hosts |
| `nmap -sS 192.168.1.1` | TCP SYN scan (default, requires root) |
| `nmap -sT 192.168.1.1` | TCP Connect scan (no root required) |
| `nmap -sU 192.168.1.1` | UDP scan |
| `nmap -p 80,443 192.168.1.1` | Scan specific ports |
| `nmap -p- 192.168.1.1` | Scan all 65535 ports |
| `nmap -sV 192.168.1.1` | Service version detection |
| `nmap -O 192.168.1.1` | OS detection |
| `nmap -A 192.168.1.1` | Aggressive scan (OS, version, scripts, traceroute) |
| `nmap -sC 192.168.1.1` | Run default NSE scripts |
| `nmap --script=vuln 192.168.1.1` | Run vulnerability scanning scripts |
| `nmap -T4 192.168.1.1` | Set timing template (0-5, higher is faster) |
| `nmap -oN output.txt 192.168.1.1` | Save output in normal format |
| `nmap -oX output.xml 192.168.1.1` | Save output in XML format |
| `nmap -oA output 192.168.1.1` | Save output in all formats |
