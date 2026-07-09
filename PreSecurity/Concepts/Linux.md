# Linux

## Definition
Linux is a Unix-like, open-source operating system kernel created by Linus Torvalds. The OS comprises the **kernel** (manages hardware, processes, memory, drivers), **shell** (command interpreter — bash, zsh), **filesystem** (hierarchical, unified directory tree starting at `/`), and **utilities** (coreutils, system tools). Distributions (Ubuntu, Debian, CentOS, Kali) package the kernel with software.

## Why It Matters
Linux powers most servers, cloud infrastructure, and security tools. Nearly all penetration testing distributions are Linux-based. Proficiency in Linux command line is essential for log analysis, scripting, privilege escalation, and managing security tools.

## Where It Appears in the Path
- Linux Fundamentals
- Security Operations

## Prerequisites
- Basic computer literacy

## Key Points
- Filesystem Hierarchy Standard (FHS): `/bin`, `/etc`, `/var`, `/tmp`, `/home`
- Everything is a file (including devices, sockets, pipes)
- Root user (UID 0) has unrestricted access
- Package managers: `apt` (Debian), `yum`/`dnf` (RHEL), `pacman` (Arch)

## Common Interview Questions
1. What is the Linux kernel?
**Answer:** The core component managing hardware, processes, memory, and system calls.
2. How do you check running processes?
**Answer:** `ps aux` or `top` / `htop`.
3. What is the difference between hard and symbolic links?
**Answer:** Hard links share the same inode; symbolic links are pointers to paths.

## Further Reading
- Linux Documentation Project (tldp.org)
- "The Linux Command Line" (Shotts)
- man pages