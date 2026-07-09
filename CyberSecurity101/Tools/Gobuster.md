# Gobuster

## Purpose
Gobuster is a fast directory/file and DNS subdomain brute-forcing tool written in Go. It is used during the reconnaissance phase of penetration testing to discover hidden web directories, files, virtual hosts, and DNS subdomains. Gobuster's multi-threaded design makes it significantly faster than traditional tools like Dirb or Dirbuster, and the single-binary deployment eliminates dependency issues.

## Installation
```bash
# Kali Linux (pre-installed)
sudo apt install gobuster

# Using Go (from source)
go install github.com/OJ/gobuster/v3@latest

# Manual binary download
wget https://github.com/OJ/gobuster/releases/download/v3.6.0/gobuster_Linux_x86_64.tar.gz
tar -xzf gobuster_*.tar.gz
sudo mv gobuster /usr/local/bin/

# macOS using Homebrew
brew install gobuster

# Docker
docker run --rm -it -v $(pwd):/data ghcr.io/oj/gobuster
```

## Basic Usage
Gobuster uses a wordlist to brute-force common paths or subdomains:
```bash
# Directory/file brute-forcing (dir mode)
gobuster dir -u http://example.com -w /usr/share/wordlists/dirb/common.txt

# DNS subdomain brute-forcing (dns mode)
gobuster dns -d example.com -w /usr/share/wordlists/dns/subdomains-top1M-5000.txt

# Virtual host discovery (vhost mode)
gobuster vhost -u http://example.com -w /usr/share/wordlists/vhost.txt

# S3 bucket enumeration (s3 mode)
gobuster s3 -w bucket-names.txt
```

## Important Options
- `dir` mode - directory and file enumeration
- `dns` mode - DNS subdomain discovery
- `vhost` mode - virtual host brute-forcing
- `s3` mode - AWS S3 bucket enumeration
- `-u, --url` - target URL (dir/vhost modes)
- `-d, --domain` - target domain (dns mode)
- `-w, --wordlist` - path to wordlist file
- `-x, --extensions` - file extensions to append (e.g., `-x php,html,txt`)
- `-t, --threads` - number of concurrent threads (default 10)
- `-k, --no-tls-validation` - skip TLS certificate verification
- `-o, --output` - write results to file
- `-s, --status-codes` - positive status codes (e.g., `-s 200,204,301,302,307`)
- `-b, --exclude-status-codes` - negative status codes to exclude
- `-c, --cookies` - cookies to include in requests
- `-H, --headers` - custom HTTP headers
- `-U, --username` / `-P, --password` - HTTP basic authentication
- `-r, --follow-redirect` - follow redirects
- `-n, --no-status` - don't display status codes in output

## Typical Workflow
1. Identify the target web application from Nmap scan results
2. Choose an appropriate wordlist (e.g., `dirb/common.txt` for quick scan, `directory-list-2.3-medium.txt` for thorough scan)
3. Run Gobuster in dir mode with file extensions relevant to the target technology stack: `gobuster dir -u http://target.com -w wordlist.txt -x php,asp,html,txt -t 50`
4. Review discovered paths and test each for interesting content
5. If the target uses virtual hosting, run vhost mode against known domains
6. For subdomain enumeration, run dns mode with appropriate wordlist
7. Correlate findings with results from other enumeration tools

## Advantages
- Extremely fast due to Go's concurrency model and multi-threading
- Single binary with no runtime dependencies
- Cross-platform (Linux, Windows, macOS)
- Supports multiple modes (dir, dns, vhost, s3) in one tool
- HTTP/HTTPS proxy support (useful with Burp Suite)
- Extensible with custom wordlists and patterns
- Regular expressions in output for automated processing

## Limitations
- Wordlist-dependent: miss paths not in the chosen wordlist
- No recursive scanning (must be done manually or with scripts)
- No built-in content length filtering (use grep to post-process)
- DNS mode is limited by the DNS resolver reliability
- No authentication mechanism support beyond basic auth
- Cannot parse JavaScript for endpoint discovery

## Industry Use
Gobuster is used by penetration testers for initial web application enumeration, bug bounty hunters for discovering hidden endpoints, security researchers for mapping attack surfaces, and red teamers during external reconnaissance. It has largely replaced older tools like Dirbuster and Dirb due to its speed and flexibility.

## Official Documentation
- GitHub: https://github.com/OJ/gobuster
- Releases: https://github.com/OJ/gobuster/releases
- Wiki: https://github.com/OJ/gobuster/wiki
- Wordlists (Kali): `/usr/share/wordlists/`
- SecLists: https://github.com/danielmiessler/SecLists
