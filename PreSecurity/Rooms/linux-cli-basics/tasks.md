# Tasks: Linux CLI Basics

## Task 1: Linux Filesystem Layout
**Purpose:** Learn the standard FHS directory structure.

**Skills:** Navigating directories, understanding purpose of each system directory.

**Theory:** The Linux Filesystem Hierarchy Standard defines key directories: `/bin` and `/sbin` (essential user/system binaries), `/etc` (configuration files), `/home` (user home directories), `/var` (variable data like logs), `/tmp` (temporary files), `/dev` (device files), and `/proc` (process and kernel info as virtual files). Understanding this layout is essential for finding files, configuring services, and system administration.

**Commands:** `ls /`, `cd /etc`, `pwd`, `tree -d /`

---

## Task 2: File Manipulation Commands
**Purpose:** Master basic file creation, copying, moving, and deletion.

**Skills:** Creating, copying, moving, renaming, and deleting files.

**Theory:** Core file commands include `touch` (create empty file or update timestamp), `cp` (copy files/directories with `-r` for recursive), `mv` (move or rename), `rm` (delete, use `-rf` with extreme caution), and `mkdir` (create directories with `-p` for parent creation). Understanding these basics is essential before learning about permissions and text processing.

**Commands:** `touch file.txt`, `cp source dest`, `mv old new`, `rm file.txt`, `mkdir -p a/b/c`

---

## Task 3: Linux Permission Model
**Purpose:** Understand rwx permissions, octal notation, and ownership.

**Skills:** chmod, chown, permission classes (owner, group, others).

**Theory:** Linux uses a 3x3 permission matrix: read (4), write (2), execute (1) for user, group, and others. `rwxr-xr--` means owner can read/write/execute, group can read/execute, others can read only. `chmod 755 file` sets owner=rwx, group=rx, others=rx. `chown user:group file` changes ownership. Permissions control access to files and directories — a fundamental security mechanism.

**Commands:** `chmod 755 script.sh`, `chown user:group file.txt`, `ls -la`, `umask`

---

## Task 4: Process Management
**Purpose:** Monitor and control running processes.

**Skills:** Listing processes, understanding process hierarchy, killing processes.

**Theory:** `ps aux` shows all processes with user, PID, CPU%, memory%. `top` provides real-time interactive monitoring. `htop` is an enhanced version. The `kill` command sends signals — `kill -9` forces termination; `kill -15` requests graceful shutdown. Understanding processes helps diagnose performance issues and terminate compromised processes.

**Commands:** `ps aux`, `top`, `htop`, `kill -9 1234`

---

## Task 5: Text Processing
**Purpose:** Master commands for searching, filtering, and transforming text.

**Skills:** grep, sed, awk, find.

**Theory:** `grep -r "pattern" /dir` recursively searches file contents. `sed` performs stream editing (substitution, deletion). `awk` is excellent for column-based output. `find /path -name "*.log"` locates files. These commands are essential for log analysis, configuration inspection, and data extraction during forensics and CTF challenges.

**Commands:** `grep -ri "error" /var/log/`, `sed 's/old/new/g' file`, `awk '{print $2}'`, `find / -name "*.conf"`

---