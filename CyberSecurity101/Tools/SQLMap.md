# SQLMap

## Purpose
SQLMap is an open-source penetration testing tool that automates the detection and exploitation of SQL injection vulnerabilities. Developed by Bernardo Damele and Miroslav Stampar, it can detect and exploit various SQL injection techniques including boolean-based blind, time-based blind, error-based, UNION query, stacked queries, and out-of-band injection. SQLMap supports multiple database backends including MySQL, Oracle, PostgreSQL, Microsoft SQL Server, and SQLite.

## Installation
```bash
# Kali Linux (pre-installed)
sudo apt install sqlmap

# Using pip (cross-platform)
pip install sqlmap

# Clone from GitHub (recommended for latest features)
git clone --depth 1 https://github.com/sqlmapproject/sqlmap.git sqlmap-dev
cd sqlmap-dev

# macOS
brew install sqlmap

# Usage (no installation needed if using git clone)
python sqlmap.py [options]
```

## Basic Usage
```bash
# Test a URL parameter for SQL injection
sqlmap -u "http://target.com/page.php?id=1"

# With cookie authentication
sqlmap -u "http://target.com/page.php?id=1" --cookie="PHPSESSID=abc123"

# POST request injection
sqlmap -u "http://target.com/login.php" --data="user=admin&pass=test"

# Specify database type
sqlmap -u "http://target.com/page.php?id=1" --dbms=mysql
```

## Important Options
- `-u <URL>` - target URL with injectable parameter
- `--data=<data>` - POST request body
- `-p <param>` - specify parameter to test (default: all)
- `--cookie=<cookie>` - HTTP cookie header
- `--level=<1-5>` - intensity of tests (1=light, 5=heavy with all payloads)
- `--risk=<1-3>` - risk of causing database modifications (1=safe, 3=high risk)
- `--dbms=<type>` - force database type to reduce test time
- `-a` / `--all` - retrieve everything accessible
- `--dbs` - enumerate database names
- `--tables` - enumerate tables in a database
- `--dump` - dump table contents (with `-D <db> -T <table>`)
- `--columns` - enumerate columns of a table
- `--os-shell` - attempt operating system shell access
- `--sql-shell` - interactive SQL prompt on target
- `--batch` - use default options without prompting
- `--threads=<num>` - number of concurrent HTTP requests
- `--proxy=<proxy>` - use HTTP/HTTPS/SOCKS proxy
- `--tamper=<script>` - apply tamper scripts to evade WAF/IDS
- `--technique=<B|E|U|S|T|Q>` - specify injection techniques (Boolean, Error, UNION, Stacked, Time, Query)
- `--no-cast` - turn off payload casting mechanism

## Tamper Scripts
Tamper scripts modify payloads to bypass WAF and input filters. Popular scripts include:
- `space2comment` - replaces spaces with comments
- `between` - replaces `>` with `NOT BETWEEN`
- `randomcase` - randomizes keyword case
- `charencode` - URL-encodes characters
- `modsecurityversioned` - bypasses ModSecurity with versioned comments

## Typical Workflow
1. Identify potentially vulnerable parameters during web application testing
2. Test with simple SQLMap command to confirm injection: `sqlmap -u "http://target.com/page.php?id=1" --batch`
3. If injection is confirmed, enumerate database: `sqlmap -u "http://target.com/page.php?id=1" --dbs`
4. Identify and extract target database: `sqlmap -u "http://target.com/page.php?id=1" -D target_db --tables`
5. Dump interesting tables: `sqlmap -u "http://target.com/page.php?id=1" -D target_db -T users --dump`
6. If possible, escalate to OS shell: `sqlmap -u "http://target.com/page.php?id=1" --os-shell`
7. Use WAF bypass techniques if blocked: `sqlmap -u "http://target.com/page.php?id=1" --tamper=between,randomcase`

## Advantages
- Fully automated SQL injection detection and exploitation
- Supports all major SQL injection techniques
- Extensive database backend compatibility
- Built-in WAF bypass mechanisms through tamper scripts
- Can achieve OS-level access via database RCE features (xp_cmdshell, INTO OUTFILE)
- Supports authentication bypass and session handling
- HTTP proxy and Tor integration for anonymity

## Limitations
- Noisy and easily detected by WAF and IDS/IPS
- Blind injection techniques are slow due to many requests
- Level/Risk 3+ tests can modify or delete database data
- May fail against custom parameter encoding or serialization
- Some tamper scripts are specific to older targets
- Cannot bypass WAF that blocks all SQL-like characters

## Industry Use
SQLMap is used by penetration testers for database security assessments, by web application auditors to validate SQL injection findings, by bug bounty hunters to confirm and exploit injection points, and by red teams for initial access via exposed web applications.

## Official Documentation
- Official Site: https://sqlmap.org
- GitHub: https://github.com/sqlmapproject/sqlmap
- User Manual: https://github.com/sqlmapproject/sqlmap/wiki
- Tamper Scripts: https://github.com/sqlmapproject/sqlmap/tree/master/tamper
- Usage: `python sqlmap.py -h` or `python sqlmap.py --pp`
