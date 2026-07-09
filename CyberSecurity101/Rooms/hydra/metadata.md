# Hydra

## Room Information
- **URL**: https://tryhackme.com/room/hydra
- **Difficulty**: Easy
- **Subscription**: Free
- **Estimated Time**: ~1.5 hours

## Description

Hydra is a powerful, parallelized network login cracker that supports numerous protocols for brute-force attacks. Developed by van Hauser of the THC (The Hacker's Choice) group, Hydra is an essential tool in every penetration tester's arsenal. It can perform rapid password guessing against services including HTTP/HTTPS (GET and POST forms), FTP, SSH, Telnet, SMTP, POP3, IMAP, SMB, MySQL, PostgreSQL, LDAP, SNMP, VNC, and many more. This room teaches learners how to install Hydra, understand its command-line syntax, and apply it to real-world scenarios. The room covers the anatomy of a Hydra command: specifying the target service and host, choosing username and password sources (single values or wordlist files), setting the number of parallel tasks, and defining protocol-specific options. Learners practice brute-forcing HTTP POST login forms by crafting the correct form parameters and failure condition strings. The room also covers brute-forcing SSH and FTP services, which are common targets in internal network penetration tests. Wordlist selection is emphasized, with the rockyou.txt wordlist being the most commonly used for password cracking. The room also discusses the ethical and legal considerations of brute-force attacks, account lockout bypass techniques, and defensive strategies. Practical exercises include brute-forcing a simulated login portal, cracking an SSH user's password, and identifying valid credentials from Hydra's output.

## Objectives
- Install and configure Hydra for various protocols
- Perform brute-force attacks against HTTP, SSH, and FTP services
- Craft Hydra commands for POST-based login forms
- Analyze Hydra output to identify valid credentials
- Understand defensive measures against brute-force attacks

## Tools
- Hydra (THC-Hydra)
- rockyou.txt wordlist (or alternative wordlists)
- curl for manual form analysis
- Web browser for inspecting login forms

## Concepts
- Brute-force and dictionary attacks
- Parallelized password guessing
- HTTP form parameter analysis
- Service protocol authentication
- Account lockout and rate limiting
- Wordlist selection and management
