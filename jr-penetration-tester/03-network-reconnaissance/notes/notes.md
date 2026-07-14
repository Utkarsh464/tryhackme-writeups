# Network Reconnaissance — Study Notes

## Passive Reconnaissance

### WHOIS Lookups
- Query domain registration details
- Registrar, registrant, creation/expiry dates, name servers, contacts
- `whois example.com`

### DNS Enumeration
- `dig` — Detailed DNS queries (A, AAAA, MX, NS, TXT, SOA, CNAME)
- `nslookup` — Simpler DNS lookup tool
- `dnsrecon` — Automated DNS enumeration

### Certificate Transparency
- crt.sh — Search SSL/TLS certificate logs
- Reveals subdomains from issued certificates
- Example: `https://crt.sh/?q=%25.example.com`

### Other Passive Techniques
- Search engines (Google dorking: `site:example.com`)
- Social media OSINT
- Shodan (internet-connected devices)
- Wayback Machine (historical website snapshots)

## Active Reconnaissance

### Web Server Probing
- `curl` — HTTP requests, header inspection
- `wget` — File downloads, mirroring
- Browser dev tools — Network tab, source view

### Network Probing
- `ping` — ICMP echo to check if host is alive
- `traceroute` / `tracert` — Map network path to target
- `nc` (netcat) — Raw TCP/UDP connections, port probing, banner grabbing

### Considerations
- Active recon generates traffic and can be detected (IDS, firewall logs)
- Always operate within authorised scope (ROE)
- Combine passive and active for complete picture
