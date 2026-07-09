# Linux

## Definition
Linux is a family of open-source Unix-like operating systems built around the Linux kernel. The kernel manages hardware resources, process scheduling, memory management, and device drivers. Distributions (distros) like Ubuntu, Debian, Fedora, and CentOS package the kernel with system utilities, libraries, and applications into a complete OS.

## Why It Matters
Linux powers the vast majority of servers, cloud infrastructure, embedded systems, and supercomputers. In cybersecurity, Linux is the primary platform for penetration testing (Kali Linux), security research, and defensive tooling. Understanding Linux is non-negotiable for any cybersecurity professional — most security tools, log analysis, and forensic investigations rely on Linux knowledge.

## Where It Appears in the Path
Linux is introduced early in the Cyber Security 101 path as a foundational skill. It appears in modules covering command-line basics, file permissions, process management, and scripting. Tools like `grep`, `awk`, `sed`, `find`, and `netstat` are used throughout later topics including networking, forensics, and exploitation.

## Prerequisites
- Basic computer literacy (files, directories, programs)
- No prior Linux experience required — the path assumes beginners

## Real-World Usage
- **Server Administration**: 96% of web servers run Linux. Administrators manage users, services, firewalls (iptables/nftables), and containers (Docker/LXC).
- **Penetration Testing**: Distributions like Kali and Parrot OS bundle hundreds of security tools (Nmap, Metasploit, Burp Suite, Wireshark).
- **Incident Response**: Analysts use Linux to examine disk images, parse logs, and run memory forensics tools like Volatility.
- **DevSecOps**: CI/CD pipelines, infrastructure-as-code (Terraform, Ansible), and container orchestration (Kubernetes) all run on Linux.

## Common Interview Questions
1. **Explain the Linux boot process.** BIOS/UEFI → Boot loader (GRUB) → Kernel initializes → init/systemd starts services → getty/login.
2. **What are the differences between hard links and symbolic links?** Hard links share the same inode (same data on disk); symbolic links are pointers to file pathnames.
3. **How do you change file permissions in Linux?** `chmod` with octal (e.g., `chmod 755 file`) or symbolic notation (`chmod u+x file`). `chown` changes ownership.
4. **What is a zombie process and how do you handle it?** A child process that has terminated but its parent has not called `wait()`. Kill the parent or send SIGCHLD.
5. **Explain /etc/passwd and /etc/shadow formats.** /etc/passwd contains user accounts (7 colon-separated fields). /etc/shadow stores hashed passwords and aging info, readable only by root.
6. **How does Linux handle process management?** Each process has a PID, runs in user or kernel mode, scheduled via CFS (Completely Fair Scheduler). `ps`, `top`, `htop`, `kill` are management tools.

## File System Hierarchy
- `/` — Root directory
- `/bin`, `/sbin` — Essential binaries (often symlinks to /usr/bin)
- `/etc` — Configuration files
- `/var` — Variable data (logs, databases, spools)
- `/tmp` — Temporary files
- `/home` — User home directories
- `/root` — Root user's home
- `/proc` — Virtual filesystem for process and kernel info
- `/dev` — Device files
- `/usr` — User system resources (binaries, libraries, documentation)

## Key Commands
- `ls`, `cd`, `pwd`, `cp`, `mv`, `rm`, `mkdir`, `rmdir` — File operations
- `chmod`, `chown`, `chgrp` — Permission management
- `ps`, `top`, `kill`, `systemctl`, `service` — Process/service management
- `grep`, `find`, `locate`, `sort`, `awk`, `sed` — Text processing
- `ssh`, `scp`, `rsync` — Remote access and transfer
- `iptables`, `nftables`, `ufw` — Firewall management

## Permissions Model
Linux uses a 3-tier permission system: owner, group, and others. Permissions are read (r=4), write (w=2), and execute (x=1). The `ls -l` command displays permissions as strings like `-rwxr-xr--`. Special permissions include SUID (setuid), SGID (setgid), and the sticky bit.

## Further Reading
- [The Linux Documentation Project](https://tldp.org/)
- [Linux Journey](https://linuxjourney.com/)
- [Kali Linux Documentation](https://www.kali.org/docs/)
- OverTheWire Bandit Wargame (practical Linux practice)
- _The Linux Command Line_ by William Shotts (free online)
