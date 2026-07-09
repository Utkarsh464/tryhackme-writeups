# SQLMap: The Basics

## Room Information
- **URL**: https://tryhackme.com/room/sqlmapthebasics
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

## Description

SQLMap: The Basics introduces SQLMap, the most popular open-source tool for automating SQL injection detection and exploitation. Developed by Bernardo Damele and Miroslav Stampar, SQLMap is a powerful, feature-rich tool that can detect and exploit SQL injection vulnerabilities with minimal manual intervention. This room covers the complete workflow: identifying potentially vulnerable parameters, using SQLMap to confirm SQL injection, fingerprinting the database management system (MySQL, PostgreSQL, Oracle, MSSQL, SQLite, etc.), enumerating database structure (databases, tables, columns), extracting sensitive data, and performing advanced exploitation. The room begins with basic usage, demonstrating how to pass a URL and potentially vulnerable parameters to SQLMap. Learners practice using the `-u` flag for target URLs, `--data` for POST parameters, and `--cookie` for authenticated sessions. The room covers optimization flags including `--level` and `--risk` for adjusting the thoroughness of tests, `--threads` for parallel processing, and `--batch` for non-interactive mode. Database fingerprinting is explained with flags like `--dbms` for specifying the database type and `--fingerprint` for detailed version detection. Data extraction techniques include `--tables` and `--columns` for schema enumeration, `--dump` for extracting data, and `--dump-all` for complete database extraction. The room also covers advanced features: reading and writing files on the database server (when the DBMS has sufficient privileges), spawning interactive SQL shells with `--sql-shell`, and executing OS commands with `--os-shell`. Bypassing Web Application Firewalls (WAFs) with tamper scripts is introduced, showing how SQLMap can modify payloads to evade detection rules. Practical exercises include exploiting a vulnerable web application to extract user credentials, reading files from the server, and executing commands through SQL injection.

## Objectives
- Use SQLMap to detect SQL injection vulnerabilities automatically
- Fingerprint database management systems and versions
- Enumerate database tables, columns, and data
- Extract sensitive data from vulnerable databases
- Read and write files on the database server
- Bypass WAF protections using tamper scripts

## Tools
- SQLMap
- Burp Suite (for capturing request data)
- Web browser for target interaction

## Concepts
- Automated SQL injection detection
- Database fingerprinting techniques
- Blind SQL injection detection (boolean-based, time-based)
- Union-based data extraction
- Out-of-band SQL injection
- WAF bypass and evasion techniques
- Database privilege escalation
