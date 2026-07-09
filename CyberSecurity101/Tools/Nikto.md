# Nikto

## Purpose
Nikto is an open-source web server scanner that performs comprehensive tests against web servers for dangerous files, outdated server software, misconfigurations, and common vulnerabilities. Developed by Chris Sullo and maintained by the open-source community, Nikto scans for over 6,700 potentially dangerous files and programs, 1,200+ outdated server versions, and 270+ server-specific issues. It is a standard tool in the web server security assessment toolkit, complementing directory brute-forcers like Gobuster.

## Installation
```bash
# Kali Linux (pre-installed)
nikto -h

# Debian/Ubuntu
sudo apt update && sudo apt install nikto

# Clone from GitHub (recommended for latest updates)
git clone https://github.com/sullo/nikto
cd nikto/program

# Perl dependencies (if needed)
cpan -i Net::SSLeay
cpan -i IO::Socket::SSL

# Docker
docker pull sullo/nikto
docker run --rm sullo/nikto -h http://targetsite.com

# macOS
brew install nikto
```

## Basic Usage
```bash
# Basic scan
nikto -h http://targetsite.com

# Scan with SSL
nikto -h https://targetsite.com -ssl

# Scan on specific port
nikto -h http://targetsite.com -p 8080

# Verbose output
nikto -h http://targetsite.com -v

# Save output to file
nikto -h http://targetsite.com -o report.html -Format html
```

## Important Options
- `-h <host>` - target host (URL, IP, or hostname)
- `-p <port>` - TCP port to scan (default 80)
- `-ssl` - force SSL/TLS mode
- `-vhost <name>` - virtual host header for Name-Based Virtual Host scanning
- `-Format <format>` - output format: `csv`, `htm`, `html`, `json`, `msf+`, `nbe`, `sql`, `txt`, `xml`
- `-o <file>` - output file name
- `-output <dir>` - output directory (for multiple files)
- `-c <config>` - configuration file
- `-C <id>` - Cookie value
- `-d` - display debugging output
- `-D <level>` - display debugging level (1-3)
- `-e` - error handling (suppress specific error types)
- `-F <format>` - output format (same as -Format)
- `-id <user>:<pass>` - HTTP authentication credentials
- `-list-plugins` - list all available scan plugins
- `-mutate <type>` - mutation technique (1=file list, 2=username, etc.)
- `-mutate-options <opts>` - mutation options
- `-Plugins <plugins>` - run specific plugins
- `-evasion <type>` - IDS evasion technique (1-8 for different encodings)
- `-Tune <tune>` - tune scan for specific tests (e.g., `-Tune 1` for interesting files, `-Tune 5` for injection)
- `-timeout <secs>` - request timeout in seconds
- `-useragent <ua>` - custom User-Agent header
- `-update` - update the database from CIRT.net

## Scan Categories (Tuning Options)
- `1` - Interesting File / Seen in logs
- `2` - Misconfiguration / Default File
- `3` - Information Disclosure
- `4` - Injection (XSS/Script/HTML)
- `5` - Remote File Retrieval - Inside Web Root
- `6` - Denial of Service
- `7` - Remote File Retrieval - Server Wide
- `8` - Command Execution / Remote Shell
- `9` - SQL Injection
- `0` - File Upload
- `a` - Authentication Bypass
- `b` - Software Identification
- `c` - CGI Scanning
- `x` - Reverse Tuning Options (skip tests)

## Typical Workflow
1. After discovering a web server via Nmap, identify open ports (80, 443, 8080, 8443, etc.)
2. Run basic Nikto scan against each web service: `nikto -h http://target.com`
3. Review the output for critical findings: outdated software, known vulnerabilities, dangerous files
4. For HTTPS servers, use SSL scan: `nikto -h https://target.com -ssl`
5. Run targeted scans with specific tuning options (e.g., focus on information disclosure)
6. Verify findings manually using curl or a browser
7. Cross-reference Nikto findings with Nmap NSE scripts and other enumeration results
8. Document vulnerable software versions for exploitation phase

## Advantages
- Comprehensive database of 6,700+ checks for dangerous files and programs
- Fast scanning with minimal configuration required
- Supports SSL/TLS scanning with certificate validation
- Multiple output formats for reporting and automation
- IDS evasion techniques (encoding, delay, custom User-Agent)
- Plugin architecture for extending functionality
- Regular database updates via the `-update` flag
- Proxy support for integration with Burp Suite or ZAP

## Limitations
- No authentication support beyond basic HTTP auth (cannot scan behind login pages)
- High false positive rate (findings require manual verification)
- No JavaScript parsing or crawling capabilities
- Cannot detect vulnerabilities in custom web applications (only generic checks)
- Scan can be aggressive and trigger WAF/IDS alerts
- Terminal output is not color-coded and can be hard to read
- No built-in prioritization or severity scoring

## Industry Use
Nikto is used by penetration testers during web application reconnaissance, by security auditors for initial web server assessment, by system administrators verifying server configurations, and by CTF participants for web challenge enumeration.

## Official Documentation
- GitHub: https://github.com/sullo/nikto
- Documentation: https://github.com/sullo/nikto/wiki
- Plugin Help: http://cirt.net/nikto2-docs/
- Kali Docs: https://www.kali.org/tools/nikto/
- Updates: `nikto -update`
