# Gobuster

## Purpose
Directory/file enumeration and DNS subdomain discovery using brute-force wordlists.

## Installation
```bash
sudo apt install gobuster      # Debian/Ubuntu/Kali
go install github.com/OJ/gobuster/v3@latest  # Go install
```

## Basic Usage
```bash
gobuster dir -u http://target.com -w /usr/share/wordlists/dirb/common.txt
gobuster dns -d target.com -w /usr/share/wordlists/dns/subdomains.txt
gobuster vhost -u http://target.com -w subdomains.txt
```

## Important Commands
- `dir` mode — Directory/file enumeration
- `dns` mode — Subdomain discovery
- `vhost` mode — Virtual host brute-forcing
- `-x php,txt,html` — File extensions to append
- `-t N` — Threads (default 10)
- `-s` — Status codes to include (default 200,204,301,302,307,401,403)
- `-b` — Bad status codes to exclude
- `-k` — Skip TLS verification
- `-o FILE` — Output to file
- `-c` — Cookie for authenticated sessions
- `-H` — Custom headers
- `--wildcard` — Detect wildcard DNS responses (DNS mode)

## Typical Workflow
1. `gobuster dir -u http://target -w medium-list.txt`
2. Check discovered paths in browser
3. Extend: `gobuster dir -u http://target -w common.txt -x php,html,txt,zip`
4. Subdomain: `gobuster dns -d target.com -w subdomains.txt -t 50`

## Official Documentation
https://github.com/OJ/gobuster