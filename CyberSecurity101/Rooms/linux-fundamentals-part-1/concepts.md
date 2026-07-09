# Concepts: Linux Fundamentals Part 1

## 1. Linux Operating System
An open-source, Unix-like operating system kernel created by Linus Torvalds in 1991. Linux powers the majority of servers, cloud infrastructure, embedded devices, Android smartphones, and supercomputers. In cybersecurity, Linux is the foundation for penetration testing distributions (Kali Linux, Parrot OS), security tools, and enterprise server environments.

## 2. Linux Distribution (Distro)
A complete operating system built on the Linux kernel, packaged with software, package managers, and configuration tools. Examples include Ubuntu (user-friendly), Debian (stable), CentOS (enterprise), Kali Linux (penetration testing), and Red Hat Enterprise Linux (commercial). Different distributions serve different purposes.

## 3. Terminal
A text-based interface for interacting with the operating system. The terminal accepts commands from the user, executes them, and displays output. It is the primary interface for system administration, development, and security work on Linux systems.

## 4. Shell
A command-line interpreter that processes user commands and communicates with the operating system. Bash (Bourne Again SHell) is the default shell on most Linux distributions. The shell provides scripting capabilities, command history, tab completion, and environment management.

## 5. Linux Filesystem Hierarchy
The standard directory structure in Linux, starting from root (/). Key directories include /bin (essential commands), /boot (boot files), /dev (device files), /etc (configuration files), /home (user home directories), /lib (libraries), /media (removable media), /mnt (temporary mounts), /opt (optional software), /proc (process information), /root (root user home), /sbin (system binaries), /tmp (temporary files), /usr (user programs), and /var (variable data).

## 6. Absolute vs. Relative Paths
Absolute paths specify the full location from the root directory (e.g., /home/user/Documents/file.txt). Relative paths specify the location relative to the current working directory (e.g., Documents/file.txt or ../other/file.txt). Understanding the difference is essential for navigation.

## 7. File Types in Linux
Everything in Linux is a file, including regular files (-), directories (d), symbolic links (l), device files (b, c), sockets (s), and named pipes (p). The file command determines the actual type of any file.

## 8. Command Syntax
Linux commands follow a general syntax: command [options] [arguments]. Options modify command behavior and typically start with a single dash (-) for short options or double dash (--) for long options. Arguments are the targets the command operates on.

## 9. Manual Pages (man)
Built-in documentation for Linux commands accessed with the man command. Manual pages contain detailed information including synopsis, description, options, examples, and related commands. Sections cover user commands (1), system calls (2), library functions (3), and more.
