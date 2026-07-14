# Commands Used — Network Reconnaissance

## Passive Reconnaissance

### WHOIS
```bash
whois example.com
```

### DNS Lookups
```bash
# Basic lookup
nslookup example.com

# Query specific record types with dig
dig example.com A
dig example.com MX
dig example.com NS
dig example.com TXT
dig example.com ANY

# Reverse DNS
dig -x 1.2.3.4
```

### DNS Automated Enumeration
```bash
# Subdomain brute-force with dnsrecon
dnsrecon -d example.com -t brt -D /usr/share/wordlists/subdomains.txt
```

## Active Reconnaissance

### HTTP Probing
```bash
# Basic request
curl http://example.com

# View response headers
curl -I http://example.com

# Follow redirects
curl -L http://example.com
```

### Host Discovery
```bash
# ICMP ping
ping -c 4 example.com

# Traceroute (Linux)
traceroute example.com

# Traceroute (Windows)
tracert example.com
```

### Raw Socket Probing with Netcat
```bash
# Banner grab on port 80
nc -nv 10.10.10.10 80

# Port scan (single port)
nc -zv 10.10.10.10 22

# Port scan (range)
nc -zv 10.10.10.10 1-1000

# Listen for reverse shell
nc -lvnp 4444
```
