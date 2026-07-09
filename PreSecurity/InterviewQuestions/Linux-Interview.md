# Linux Interview Questions

## 1. Explain the Linux filesystem hierarchy.
**Answer:** The Linux filesystem follows the FHS (Filesystem Hierarchy Standard). Key directories: `/` (root, top of the tree), `/bin` and `/sbin` (essential binaries and system administration commands), `/etc` (system configuration files), `/home` (user home directories), `/var` (variable data like logs, spools, caches), `/tmp` (temporary files), `/dev` (device files representing hardware), `/proc` (virtual filesystem for process and kernel information), `/usr` (user system resources, installed software), and `/opt` (optional third-party software).

## 2. Explain the Linux permission model (rwx and octal).
**Answer:** Linux permissions are divided into three groups: Owner (u), Group (g), and Others (o). Each group has read (r=4), write (w=2), and execute (x=1) permissions. Octal notation represents permissions as a three-digit number: e.g., 755 = Owner (7=rwx), Group (5=r-x), Others (5=r-x). `chmod 755 file` sets these permissions. Directories need execute permission to be accessible. Additional bits include SUID (4xxx), SGID (2xxx), and Sticky (1xxx) bits.

## 3. What do chmod and chown do?
**Answer:** `chmod` (change mode) modifies file or directory permissions. Usage: `chmod u+x script.sh` (add execute for owner), `chmod 644 file.txt` (set octal permissions). `chown` (change owner) changes file ownership: `chown user:group file.txt` changes both owner and group. Both require appropriate privileges (typically root or file owner) and are fundamental for Linux security and access control.

## 4. How do you manage processes in Linux?
**Answer:** Key process management commands: `ps` (snapshot of current processes), `top`/`htop` (real-time process monitoring), `kill` (terminate by PID), `killall` (terminate by name), `nice`/`renice` (adjust process priority), `bg`/`fg` (background/foreground jobs), `jobs` (list background jobs), `nohup` (run immune to hangups), `systemctl` (manage systemd services), and `&` (run in background). The `/proc` filesystem exposes process details via numbered directories.

## 5. Explain grep, sed, and awk.
**Answer:** `grep` searches text using patterns/regex: `grep "error" /var/log/syslog`. `sed` (stream editor) transforms text: `sed 's/old/new/g' file.txt` (replace all occurrences). `awk` is a powerful text-processing language for field-based manipulation: `awk '{print $1, $3}' file.txt` (print first and third columns). These tools are essential for log analysis, data extraction, and automation in shell scripting.

## 6. Explain pipes and redirects in Linux.
**Answer:** Pipes (`|`) send the output of one command as input to another: `ps aux | grep nginx`. Redirects send output to files: `>` (overwrite), `>>` (append), `<` (input from file). File descriptors: 0 (stdin), 1 (stdout), 2 (stderr). Common patterns: `command > file 2>&1` (redirect both stdout and stderr to file), `command &> file` (same, bash shorthand). `/dev/null` discards output.

## 7. How does SSH key-based authentication work?
**Answer:** SSH key authentication uses a cryptographic key pair. The public key is placed on the server in `~/.ssh/authorized_keys`, while the private key remains on the client. During authentication, the server generates a challenge encrypted with the public key; the client proves possession of the private key by decrypting it. This is more secure than password auth (resists brute-force, no password transmission) and supports passphrase-protected keys and ssh-agent for convenience.

## 8. What are cron jobs and how do you manage them?
**Answer:** Cron jobs schedule commands to run automatically at specified times. The cron table (crontab) uses five time fields: minute (0-59), hour (0-23), day of month (1-31), month (1-12), day of week (0-7). Example: `0 3 * * * /script/backup.sh` runs daily at 3 AM. Commands: `crontab -e` (edit), `crontab -l` (list), `crontab -r` (remove). System-wide jobs are in `/etc/crontab` and `/etc/cron.d/`.

## 9. Explain environment variables in Linux.
**Answer:** Environment variables store system-wide or session-wide values that affect process behavior. Key variables: `PATH` (command search directories), `HOME` (user home directory), `USER` (current username), `SHELL` (default shell), `LANG` (locale settings). Set with `export VAR=value` or in config files (`~/.bashrc`, `~/.profile`, `/etc/environment`). View with `env` or `printenv`. They are inherited by child processes.

## 10. How does package management work in Linux?
**Answer:** Linux distributions use package managers to install, update, and remove software. Debian/Ubuntu use `apt` (APT) with `.deb` packages: `apt update && apt install nginx`. Red Hat/Fedora use `dnf` with `.rpm` packages: `dnf install httpd`. Arch uses `pacman`. Package managers resolve dependencies automatically, manage repositories, and handle configuration files during upgrades. Snap and Flatpak provide sandboxed cross-distribution packages.
