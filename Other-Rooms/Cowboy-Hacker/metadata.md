# Cowboy Hacker

## Room Information

- **URL**: https://tryhackme.com/room/cowboyhacker
- **Difficulty**: Easy
- **Category**: Offensive — Basic Exploitation
- **Target**: `10.49.172.169`
- **Platform**: TryHackMe AttackBox (web-based — no local OpenVPN session)

## Description

Cowboy Hacker is an easy exploitation room that chains together anonymous FTP access, a leaked password wordlist, an SSH brute-force, and a GTFOBins-based privilege escalation. The final goal is to capture both the `user.txt` and `root.txt` flags.

## Objectives

- Enumerate the target with Nmap to identify open ports and service versions
- Access the FTP server anonymously and retrieve the task list (`task.txt`) and password wordlist (`locks.txt`)
- Brute-force the SSH password for the discovered user using the leaked wordlist
- Obtain the `user.txt` flag
- Escalate privileges to root by abusing the sudo-granted `/bin/tar` binary (GTFOBins)
- Obtain the `root.txt` flag

## Tools Used

- Nmap
- FTP client (local terminal, then THM AttackBox)
- Hydra (SSH brute-force)
- SSH client
- GTFOBins — `tar --checkpoint-action=exec` command execution

## Concepts

- Anonymous FTP enumeration
- Leaked credential wordlists
- SSH brute-force with Hydra
- `sudo -l` privilege review
- Sudo misconfiguration exploitation (binary runnable as root)
- GTFOBins `tar` checkpoint command injection
