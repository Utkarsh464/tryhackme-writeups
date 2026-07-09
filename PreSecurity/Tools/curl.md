# curl

## Purpose
Command-line tool for transferring data with URLs. Supports HTTP/HTTPS, FTP, LDAP, and many other protocols. Essential for API testing, file downloads, and web reconnaissance.

## Installation
```bash
sudo apt install curl          # Debian/Ubuntu
# Pre-installed on most systems
```

## Basic Usage
```bash
curl https://example.com                        # GET request
curl -X POST -d "user=admin&pass=test" http://example.com/login
curl -H "Authorization: Bearer TOKEN" http://api.example.com/users
curl -L -o file.zip http://example.com/file.zip
```

## Important Commands
- `-X METHOD` — HTTP method (GET, POST, PUT, DELETE)
- `-d "data"` — Send POST data (automatic Content-Type)
- `-H "Header: value"` — Custom header
- `-L` — Follow redirects
- `-o FILE` — Write output to file
- `-O` — Save with remote filename
- `-k` — Allow insecure SSL
- `-v` — Verbose (full request/response)
- `-s` — Silent mode (no progress bars)
- `-S` — Show errors in silent mode
- `-b COOKIE` — Send cookies
- `-c FILE` — Save cookies to file
- `-x proxy` — Use proxy
- `-A "User-Agent"` — Custom User-Agent

## Typical Workflow
1. `curl -v http://target.com` — Map initial response
2. `curl -L http://target.com` — Follow redirects
3. `curl -X POST -d "user=admin" -H "X-Forwarded-For: 127.0.0.1" http://target.com/login`
4. `curl -b "session=abc123" http://target.com/dashboard`
5. Download: `curl -L -O https://example.com/tool.sh`

## Official Documentation
https://curl.se/docs/