# Module 09: Offensive Security Tooling

## Overview

Offensive Security Tooling is a practical, hands-on module that equips learners with the essential tools used by penetration testers, ethical hackers, and red team professionals. While understanding vulnerabilities is important, knowing how to use the tools that automate discovery, exploitation, and post-exploitation is equally critical. This module covers four of the most widely used offensive security tools: Hydra for password brute-forcing, Gobuster for directory and DNS enumeration, Shells Overview for understanding reverse shells and bind shells, and SQLMap for automated SQL injection detection and exploitation.

The module begins with Hydra, a powerful network login cracker that supports numerous protocols including HTTP, HTTPS, FTP, SSH, SMB, MySQL, and many more. Hydra is the standard tool for performing brute-force attacks against authentication services during penetration tests. Learners explore how to use Hydra with username and password lists, how to customize attack parameters, and how to interpret results to identify valid credentials. The room also covers defensive insights, such as implementing account lockout policies and rate limiting to mitigate brute-force attacks.

Gobuster: The Basics introduces a tool specialized for directory and subdomain enumeration. During the reconnaissance phase of a penetration test, finding hidden directories and subdomains is crucial for expanding the attack surface. Gobuster uses wordlist-based brute-force attacks to discover URLs and DNS names that are not linked from the main application. The room covers directory/file enumeration mode, DNS subdomain enumeration mode, and vhost enumeration. Learners practice targeting practice websites to uncover hidden resources.

Shells Overview provides essential knowledge about reverse shells, bind shells, and web shells. After exploiting a vulnerability, an attacker needs a way to interact with the compromised system. This room explains the differences between reverse and bind shells, how to generate payloads using tools like msfvenom, how to set up listeners with netcat, and how to upgrade basic shells to fully interactive TTY sessions. The room also covers web shells for environments where traditional reverse shells are blocked.

The module concludes with SQLMap: The Basics, which introduces the automated SQL injection detection and exploitation tool. While manual SQL injection requires significant expertise, SQLMap automates the process of detecting vulnerable parameters, fingerprinting databases, enumerating tables and columns, and extracting data. The room covers basic usage, optimization techniques, bypassing WAF protections, and post-exploitation features.

By the end of this module, learners will have hands-on experience with the core offensive security tools used in professional penetration testing engagements and capture-the-flag competitions.

## Rooms

1. **Hydra** (Free, ~1.5 hours)
2. **Gobuster: The Basics** (Premium, ~1 hour)
3. **Shells Overview** (Premium, ~1 hour)
4. **SQLMap: The Basics** (Premium, ~1 hour)

## Prerequisites

- Familiarity with Linux command line and terminal usage
- Understanding of network protocols (Module 05)
- Basic knowledge of web application concepts (Module 08)

## Learning Objectives

- Perform password brute-force attacks with Hydra
- Enumerate directories, subdomains, and vhosts with Gobuster
- Generate and deploy reverse shells, bind shells, and web shells
- Automate SQL injection detection and exploitation with SQLMap
- Understand when and how to use each offensive tool ethically
