# OWASP Top 10 - 2025 — Commands

| Command | Description |
|---------|-------------|
| `curl -v http://target.com/api/users` | Send an HTTP request and display verbose output including headers |
| `curl -X POST http://target.com/login -d "user=admin&pass=test"` | Send a POST request with form data |
| `curl -b "session=abc123" http://target.com/profile` | Send a request with a specific cookie |
| `sqlmap -u "http://target.com/page?id=1" --batch` | Automated SQL injection detection and exploitation |
| `sqlmap -u "http://target.com/login" --data="user=admin&pass=test" --level=2` | SQLMap with POST data and increased depth |
| `nc -lvnp 4444` | Start a netcat listener for reverse shells |
| `nc target.com 80` | Connect to a remote host on a specific port |
| `python3 -c 'import requests; print(requests.get("http://target.com").text)'` | Use Python Requests for HTTP interactions |
| `openssl s_client -connect target.com:443` | Examine TLS certificate and cipher details |
| `nmap -sV --script=http-enum target.com` | Enumerate web server and HTTP paths |
| `gobuster dir -u http://target.com -w /usr/share/wordlists/dirb/common.txt` | Directory and file brute forcing |
| `wget http://target.com/vulnerable.php --post-data="input=test"` | Download a page with POST data |
| `hashcat -m 0 -a 0 hashes.txt /usr/share/wordlists/rockyou.txt` | Crack MD5 hashes with Hashcat |
| `jwt_tool <token>` | Analyze and manipulate JSON Web Tokens |
| `python3 -m http.server 8080` | Start a simple HTTP server for exfiltration testing |
