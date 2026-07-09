# Module 09: Offensive Security Tooling - Rooms

## Room 1: Hydra

- **URL**: https://tryhackme.com/room/hydra
- **Difficulty**: Easy
- **Subscription**: Free
- **Estimated Time**: ~1.5 hours

Hydra is one of the most popular password brute-forcing tools in the security industry. This room covers installing Hydra, understanding its command-line syntax, and using it to attack various network services. Learners practice brute-forcing HTTP login forms (POST-based and GET-based), SSH authentication, FTP logins, and other common protocols. The room emphasizes the importance of wordlists like rockyou.txt and demonstrates how to customize Hydra for specific attack scenarios. Practical exercises involve cracking real login forms and understanding the output to identify successful attacks. The room also discusses defensive measures such as account lockout policies, CAPTCHAs, and rate limiting.

## Room 2: Gobuster: The Basics

- **URL**: https://tryhackme.com/room/gobusterthebasics
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

Gobuster is a high-performance tool for brute-forcing directories, DNS subdomains, and virtual hosts. Written in Go, Gobuster is significantly faster than traditional tools like dirb or dirbuster. This room covers the three primary modes of operation: dir mode for discovering hidden files and directories, dns mode for enumerating subdomains, and vhost mode for identifying virtual hosts on web servers. Learners configure wordlists, set thread counts, handle HTTP status codes, and process results. The room emphasizes the reconnaissance phase of penetration testing, where finding hidden endpoints expands the attack surface.

## Room 3: Shells Overview

- **URL**: https://tryhackme.com/room/shellsoverview
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

Shells are the primary method for remote interaction with compromised systems. This room provides a comprehensive overview of reverse shells (where the target connects back to the attacker), bind shells (where the attacker connects to a listening service on the target), and web shells (script-based shells running on a web server). Learners explore various methods of shell generation using msfvenom, setting up netcat listeners, and upgrading limited shells to fully interactive TTY environments. The room covers common shell restrictions and techniques for bypassing them, including Python pty modules, socat, and script utilities.

## Room 4: SQLMap: The Basics

- **URL**: https://tryhackme.com/room/sqlmapthebasics
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

SQLMap is the leading open-source tool for automating SQL injection detection and exploitation. This room teaches learners how to identify SQL-injectable parameters, use SQLMap to fingerprint the database management system, enumerate database structures (tables, columns, data types), and extract sensitive data. The room covers optimization flags (--threads, --batch, --time-sec), request customization (cookies, headers, POST data), and advanced features like reading files from the database server, writing files, and spawning interactive shells. SQLMap's ability to bypass WAF protections through tamper scripts and randomization is also covered.
