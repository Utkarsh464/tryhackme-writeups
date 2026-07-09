# SQL Injection

## Definition
SQL Injection (SQLi) is a code injection technique where an attacker inserts malicious SQL statements into application queries through unsanitized input. Types include **In-Band** (same channel to retrieve and display data — UNION SQLi, Error-based), **Blind** (Boolean-based, Time-based), and **Out-of-Band** (using DNS/HTTP exfiltration).

## Why It Matters
SQLi is consistently in the OWASP Top 10. It can bypass authentication, extract entire databases, and even execute OS commands (via `xp_cmdshell` on MSSQL or `INTO OUTFILE` on MySQL). It is one of the oldest but most impactful web vulnerabilities.

## Where It Appears in the Path
- Web Hacking Fundamentals

## Prerequisites
- SQL syntax basics, HTTP fundamentals

## Key Points
- Classic: `' OR 1=1 --` bypasses login
- UNION SQLi: concatenate results from other tables
- Blind SQLi: ask true/false questions (`1=1` vs `1=2`)
- Time-based: `IF(condition, WAIT, 0)` to infer data
- Prevention: prepared statements / parameterized queries, least privilege

## Common Interview Questions
1. What is the difference between SQLi and NoSQL injection?
**Answer:** SQLi targets relational databases with SQL syntax; NoSQL injection targets document stores with JSON query syntax.
2. How do you prevent SQL injection?
**Answer:** Use parameterized queries; never concatenate user input into SQL strings.
3. What does `UNION SELECT` do in SQLi?
**Answer:** Appends results from the attacker's query to the original query results.

## Further Reading
- OWASP SQL Injection Prevention Cheat Sheet
- PortSwigger SQLi Cheat Sheet