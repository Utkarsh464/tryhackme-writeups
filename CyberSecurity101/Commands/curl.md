# curl

**Client URL** — a command-line tool for transferring data using URL syntax, supporting dozens of protocols.

## Syntax

```
curl [options] <URL>
```

## Purpose

Transfer data to or from a server using protocols like HTTP, HTTPS, FTP, SFTP, SCP, LDAP, and more. Essential for testing APIs, downloading files, debugging web servers, and crafting HTTP requests in penetration testing.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-X` / `--request` | HTTP method (GET, POST, PUT, DELETE) |
| `-d` / `--data` | Send data in POST request (form data) |
| `-H` / `--header` | Add an HTTP header |
| `-b` / `--cookie` | Send cookies |
| `-c` / `--cookie-jar` | Write cookies to a file |
| `-o` / `--output` | Write output to a file |
| `-O` | Save with remote file name |
| `-L` / `--location` | Follow redirects |
| `-k` / `--insecure` | Skip TLS certificate verification |
| `-i` / `--include` | Include HTTP response headers in output |
| `-s` / `--silent` | Silent mode (suppress progress/info) |
| `-v` / `--verbose` | Verbose output (full request/response details) |
| `-u` / `--user` | Username:password for basic auth |
| `--upload-file` | Upload a file |
| `--limit-rate` | Limit transfer speed |

## Examples

```bash
# Basic GET request
curl http://example.com

# View response headers only
curl -I http://example.com

# Download a file
curl -O https://example.com/file.zip

# Save with custom filename
curl -o output.txt http://example.com

# POST request with form data
curl -X POST -d "username=admin&password=pass" http://10.10.10.1/login.php

# POST with JSON data
curl -X POST -H "Content-Type: application/json" -d '{"user":"admin"}' http://10.10.10.1/api

# Send custom headers and cookies
curl -H "User-Agent: Mozilla/5.0" -b "session=abc123" http://10.10.10.1

# Follow redirects and show headers
curl -L -i http://example.com

# Upload a file via FTP
curl -T file.txt ftp://10.10.10.1/upload/ --user user:pass

# Silent + verbose for debugging
curl -sv http://example.com 2>&1

# Limit download speed
curl --limit-rate 100k -O http://example.com/largefile.iso
```

## Common Mistakes

- Forgetting `-L` to follow redirects — the response will be a 301/302 with no content.
- Using `-d` without `-X POST` — curl defaults to POST when `-d` is used, but explicit method is clearer.
- Not quoting JSON data — shell expansion corrupts the payload. Always use single quotes around JSON.
- Using `-k` in production — bypassing TLS verification defeats HTTPS security. Only for testing.
- Forgetting to URL-encode special characters in data — `&` and `=` inside values break parameters.

## Real-World Usage

- **API testing:** Craft requests to RESTful APIs, inspect responses, debug authentication flows.
- **Web pentesting:** Probe for vulnerabilities, test parameter injection, bypass access controls.
- **File transfers:** Automated uploads/downloads to and from FTP/HTTP servers.
- **Session handling:** Capture and replay cookies to test authenticated endpoints.
- **CTF challenges:** Many web-based CTF challenges require precise HTTP manipulation with curl.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed on most distros |
| Windows | Full | Bundled with Windows 10+, or download |
| macOS | Full | Pre-installed |

```bash
# Install on Linux
sudo apt install curl
```
