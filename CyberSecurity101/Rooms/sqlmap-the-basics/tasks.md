# SQLMap: The Basics - Tasks

## Task 1: Introduction to SQLMap
- Understand what SQLMap is and its capabilities
- Learn about the difference between manual and automated SQL injection
- Understand the ethical and legal requirements for using SQLMap

## Task 2: Installing SQLMap
- Install SQLMap using apt, git clone, or pip
- Verify installation with `sqlmap --version`
- Understand the basic command syntax and help system

## Task 3: Basic SQL Injection Detection
- Use `sqlmap -u "http://target.com/page?id=1"` to test a GET parameter
- Understand SQLMap's detection methodology
- Interpret SQLMap output to determine vulnerability status
- Learn about false positives and how to minimize them

## Task 4: POST Parameter Injection
- Capture a POST request using Burp Suite
- Save the request to a file for SQLMap input
- Use `sqlmap -r request.txt` to test POST parameters
- Use `sqlmap -u "http://target.com/login" --data="user=admin&pass=test"` for inline data

## Task 5: Request Customization
- Set cookies with the `--cookie` flag for authenticated testing
- Set custom headers with `--headers`
- Specify a custom User-Agent with `--user-agent`
- Use `--random-agent` for randomization
- Handle CSRF tokens and other dynamic parameters

## Task 6: Database Fingerprinting
- Use `--fingerprint` for detailed DBMS version detection
- Specify the database type with `--dbms` to speed up testing
- Understand how SQLMap identifies the backend database
- Learn about common DBMS differences (MySQL, MSSQL, Oracle, PostgreSQL)

## Task 7: Database and Table Enumeration
- List databases with `--dbs`
- List tables in a specific database with `-D database --tables`
- Count entries with `--count`
- Understand database naming conventions and interesting database names

## Task 8: Column and Data Extraction
- List columns with `-D database -T table --columns`
- Extract data with `-D database -T table --dump`
- Extract all data with `--dump-all`
- Limit results with `--start` and `--stop`
- Use `--where` for conditional extraction

## Task 9: Advanced Exploitation
- Read files with `--file-read /etc/passwd`
- Write files with `--file-write shell.php --file-dest /var/www/html/shell.php`
- Spawn an SQL shell with `--sql-shell`
- Spawn an OS shell with `--os-shell`
- Understand when these advanced features are available

## Task 10: Optimization and Evasion
- Use `--level 1-5` for increasing injection depth
- Use `--risk 1-3` for increasing risk tolerance
- Use `--threads 10` for parallel processing
- Use tamper scripts with `--tamper=space2comment` for WAF bypass
- List available tamper scripts with `--list-tampers`
- Use `--random-agent` and `--proxy` for anonymization

## Task 11: Working with Request Files
- Capture a full HTTP request with Burp Suite
- Save to a file and pass to SQLMap with `-r`
- Edit the request file for targeted testing
- Use `-p` to specify the exact parameter to test
- Combine request files with other flags

## Task 12: Practical Challenge
- Identify a vulnerable web application
- Use SQLMap to enumerate and extract data
- Practice advanced features (file read, shell access)
- Document findings responsibly
