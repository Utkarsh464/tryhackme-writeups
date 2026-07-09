# Nikto

## Purpose
Web server scanner that checks for outdated software, dangerous files, misconfigurations, and common vulnerabilities.

## Installation
```bash
sudo apt install nikto         # Debian/Ubuntu/Kali
git clone https://github.com/sullo/nikto.git
```

## Basic Usage
```bash
nikto -h http://target.com                           # Basic scan
nikto -h https://target.com -ssl                     # HTTPS scan
nikto -h target.com -p 8080                          # Non-default port
nikto -h target.com -output scan.html -Format html   # Save report
```

## Important Commands
- `-h HOST` — Target host
- `-p PORT` — Port (default 80)
- `-ssl` — Force SSL mode
- `-output FILE` — Save report
- `-Format FORMAT` — Report format (html, txt, csv, xml)
- `-Tuning N` — Scan tuning (1=interesting file, 2=misconfig, 3=info, etc.)
- `-id user:pass` — Basic HTTP auth
- `-evasion TECH` — IDS evasion (encode URI, etc.)
- `-list-plugins` — List available plugins
- `-Plugins +method` — Enable specific plugins

## Typical Workflow
1. `nikto -h http://target.com -ssl` for HTTPS
2. Review output for critical findings (admin panels, outdated software, info disclosures)
3. Save results: `nikto -h target.com -o report.html -Format html`
4. Tune scans: `-Tuning 1 2 3 4` to focus on file/disclosure/misconfig issues

## Official Documentation
https://github.com/sullo/nikto