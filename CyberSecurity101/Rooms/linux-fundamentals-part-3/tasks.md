# Tasks: Linux Fundamentals Part 3

## Task 1: Shell Scripting Basics

**Purpose:** Write and execute simple Bash scripts.

**Skills:** Script writing, automation.

**Theory:** Shell scripts are text files containing commands that are executed sequentially. Scripts begin with a shebang line (#!/bin/bash) and are made executable with chmod +x. Variables store data, command substitution ($()) captures command output, and arithmetic expansion ($(())) performs calculations.

**Commands:**
- chmod +x - Make script executable
- ./script.sh - Execute script
- echo - Print to output
- read - Read user input

---

## Task 2: Conditional Statements and Loops

**Purpose:** Add logic and iteration to Bash scripts.

**Skills:** Programming constructs in shell scripts.

**Theory:** Conditionals (if, elif, else, case) allow scripts to make decisions based on conditions. Loops (for, while, until) repeat actions multiple times. Test conditions use operators like -eq, -ne, -lt, -gt, -f, -d, and -z. Proper syntax with spaces and semicolons is critical.

**Commands:**
- if - Conditional execution
- for - Loop over items
- while - Loop while condition true
- case - Multi-way branch
- test or [ ] - Evaluate condition

---

## Task 3: Networking Commands

**Purpose:** Configure networks and test connectivity from the command line.

**Skills:** Network configuration, connectivity testing.

**Theory:** Linux provides powerful networking tools. ip and ifconfig manage network interfaces. ping tests reachability. ss and netstat display socket statistics and active connections. ssh enables secure remote access. Understanding these tools is essential for troubleshooting and security assessment.

**Commands:**
- ip - Show/manipulate routing and devices
- ifconfig - Configure network interfaces
- ping - Test network connectivity
- ss - Socket statistics
- netstat - Network statistics
- ssh - Secure Shell client
- scp - Secure copy over SSH
- rsync - Remote file sync

---

## Task 4: Package Management

**Purpose:** Install, update, and remove software packages.

**Skills:** Software management, system maintenance.

**Theory:** Linux distributions use package managers to handle software installation. Debian-based systems use apt (Advanced Package Tool). RHEL-based systems use yum or dnf. dpkg is the low-level tool for .deb packages. Packages have dependencies that are resolved automatically.

**Commands:**
- apt update - Update package index
- apt install - Install package
- apt upgrade - Upgrade all packages
- apt remove - Remove package
- dpkg -i - Install .deb package
- yum install - Install package (RHEL)
- yum update - Update packages (RHEL)

---

## Task 5: Task Scheduling with Cron

**Purpose:** Automate recurring tasks using cron.

**Skills:** Task automation, scheduling.

**Theory:** cron is a time-based job scheduler in Unix-like systems. crontab files define schedules using five fields: minute, hour, day of month, month, day of week. Users edit their crontab with crontab -e. System-wide cron jobs are in /etc/crontab and /etc/cron.d/.

**Commands:**
- crontab -e - Edit user's crontab
- crontab -l - List user's crontab
- crontab -r - Remove user's crontab
