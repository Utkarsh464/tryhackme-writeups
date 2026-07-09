# Shells Overview

## Room Information
- **URL**: https://tryhackme.com/room/shellsoverview
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

## Description

Shells Overview provides a comprehensive introduction to the three primary types of shells used in penetration testing: reverse shells, bind shells, and web shells. After successfully exploiting a vulnerability, gaining interactive access to the target system is essential for post-exploitation activities such as privilege escalation, lateral movement, data exfiltration, and persistence. This room demystifies how shells work at the network level and provides practical experience in generating, deploying, and managing shell access. Reverse shells involve the target system initiating a connection back to the attacker's machine, which is effective when the target is behind a firewall that blocks incoming connections. Bind shells involve the target opening a listening port that the attacker connects to, which is useful when the target can accept incoming connections. Web shells are script-based shells deployed on web servers, typically written in PHP, ASP, or JSP, that accept commands via HTTP parameters and execute them on the server. The room covers generating shell payloads using msfvenom (part of the Metasploit framework), setting up listeners with netcat and Metasploit's multi-handler, and upgrading limited shells to fully interactive TTY shells for proper command execution. Learners practice with various payload formats for different target architectures and operating systems (Linux x86/x64, Windows x86/x64, ARM). The room also covers shell stabilisation techniques including Python pty modules, socat, and the script command. Understanding shells is critical for any penetration tester, as shell access is the primary mechanism for executing commands on compromised systems during assessments.

## Objectives
- Understand the differences between reverse, bind, and web shells
- Generate shell payloads using msfvenom for various targets
- Set up netcat listeners to receive reverse shells
- Deploy and execute shells on target systems
- Upgrade basic shells to fully interactive TTY sessions
- Understand firewall and NAT considerations for shell connections

## Tools
- Netcat (nc)
- Metasploit Framework (msfvenom, msfconsole)
- Socat
- Web browser for web shell access

## Concepts
- TCP connection initiation and direction
- Firewall egress and ingress filtering
- Shell payload types and formats (staged vs stageless)
- TTY allocation and terminal emulation
- PTY spawning and shell stabilisation
- Web server code execution
