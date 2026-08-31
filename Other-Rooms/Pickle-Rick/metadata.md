# Pickle Rick

## Room Information

- **URL**: https://tryhackme.com/room/picklerick
- **Difficulty**: Easy
- **Category**: Offensive — Web Exploitation / Command Injection
- **Target**: `10.48.131.21`
- **Platform**: TryHackMe AttackBox (web-based), completed from local Arch + web UI

## Description

Pickle Rick is a Rick and Morty–themed CTF on TryHackMe. The goal is to help Rick turn himself back into a human from a pickle by finding the **three secret ingredients** for his pickle-reverse potion. The challenge involves web enumeration, credentials hidden in page source and `robots.txt`, a login portal, and a command-panel web shell that escalates to root via an unrestricted `sudo` rule.

## Objectives

- Enumerate the target with Nmap to identify open ports and service versions
- Enumerate web directories with a directory-brute-force tool (bustit)
- Recover the username from an HTML comment and the password from `robots.txt`
- Log in to the web portal (`login.php`) and reach the command panel (`portal.php`)
- Use the built-in command execution to enumerate the filesystem with `sudo -l`
- Find the first ingredient (`mr. meeseek hair`)
- Exploit the `sudo` NOPASSWD rule to read `/home/rick` and `/root` files
- Find the second ingredient (`1 jerry tear`) and third ingredient (`fleeb juice`)

## Tools Used

- Nmap
- bustit (my own async directory brute-forcer — [dir-brute](https://github.com/Utkarsh464/dir-brute))
- curl
- Web browser (login portal + command panel)

## Concepts

- Web service enumeration
- Directory brute-forcing
- Credential leakage via HTML comments and `robots.txt`
- Web login portal authentication
- Command execution via a web shell / command panel
- `sudo -l` privilege review and NOPASSWD privilege escalation
