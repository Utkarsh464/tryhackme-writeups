# Gobuster: The Basics - Commands

## Directory Enumeration (dir mode)

| Command | Description |
|---------|-------------|
| `gobuster dir -u http://10.10.10.10 -w /usr/share/wordlists/dirb/common.txt` | Basic directory brute-force |
| `gobuster dir -u http://10.10.10.10 -w wordlist.txt -x php,txt,html` | Append file extensions |
| `gobuster dir -u http://10.10.10.10 -w wordlist.txt -s 200,301,403` | Show only specific status codes |
| `gobuster dir -u http://10.10.10.10 -w wordlist.txt --exclude-status 404` | Exclude 404 responses |
| `gobuster dir -u http://10.10.10.10 -w wordlist.txt -t 64` | Use 64 concurrent threads |
| `gobuster dir -u http://10.10.10.10 -w wordlist.txt -c "session=abc123"` | Send a cookie with requests |
| `gobuster dir -u http://10.10.10.10 -w wordlist.txt -H "Authorization: Bearer token"` | Add custom header |
| `gobuster dir -u http://10.10.10.10 -w wordlist.txt -a "Mozilla/5.0"` | Set custom User-Agent |
| `gobuster dir -u http://10.10.10.10 -w wordlist.txt -n` | Do not follow redirects |
| `gobuster dir -u http://10.10.10.10 -w wordlist.txt -r` | Follow redirects |
| `gobuster dir -u http://10.10.10.10 -w wordlist.txt -o results.txt` | Save output to file |
| `gobuster dir -u http://10.10.10.10 -w wordlist.txt -q` | Quiet mode (hide banner and progress) |
| `gobuster dir -u http://10.10.10.10 -w wordlist.txt -k` | Skip TLS certificate validation |

## DNS Subdomain Enumeration (dns mode)

| Command | Description |
|---------|-------------|
| `gobuster dns -d example.com -w subdomains.txt` | Basic subdomain enumeration |
| `gobuster dns -d example.com -w subdomains.txt -i` | Show IP addresses of resolved subdomains |
| `gobuster dns -d example.com -w subdomains.txt -r 8.8.8.8` | Use Google DNS as resolver |
| `gobuster dns -d example.com -w subdomains.txt --wildcard` | Detect and handle wildcard DNS |
| `gobuster dns -d example.com -w subdomains.txt -t 32` | Use 32 concurrent threads |
| `gobuster dns -d example.com -w subdomains.txt -o subdomains.txt` | Save results to file |

## Virtual Host Enumeration (vhost mode)

| Command | Description |
|---------|-------------|
| `gobuster vhost -u http://10.10.10.10 -w vhosts.txt` | Basic vhost enumeration |
| `gobuster vhost -u http://10.10.10.10 -w vhosts.txt --append-domain` | Append target domain to each word |
| `gobuster vhost -u http://10.10.10.10 -w vhosts.txt -t 32` | Use 32 concurrent threads |
| `gobuster vhost -u http://10.10.10.10 -w vhosts.txt -o vhosts.txt` | Save results to file |
| `gobuster vhost -u http://10.10.10.10 -w vhosts.txt -k` | Skip TLS certificate validation |

## Common Gobuster Flags

| Flag | Description |
|------|-------------|
| `-t` | Number of concurrent threads (default 10) |
| `-w` | Path to wordlist file |
| `-o` | Output file for results |
| `-q` | Quiet mode |
| `-k` | Skip SSL/TLS certificate verification |
| `-U` | Username for basic authentication |
| `-P` | Password for basic authentication |
| `-z` | No progress updates |
| `--delay` | Time between threads (milliseconds) |
| `--timeout` | HTTP request timeout (seconds) |
