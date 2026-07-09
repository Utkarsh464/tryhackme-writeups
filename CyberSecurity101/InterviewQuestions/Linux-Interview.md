# Linux Interview Questions & Answers

## 1. Explain Linux file permissions in detail.

**Answer:** Linux uses a permission system with three levels: Owner (u), Group (g), and Others (o). Each level has read (r=4), write (w=2), and execute (x=1) permissions. Permissions are represented as a 10-character string (e.g., `-rwxr-xr--`) or a 3-digit octal number (e.g., 754). The first character indicates file type (`-` for file, `d` for directory, `l` for symlink). Chmod changes permissions, chown changes owner, chgrp changes group. Special permissions include SUID (4xxx - runs as owner), SGID (2xxx - runs as group), and sticky bit (1xxx - only owner can delete). ACLs provide finer-grained control beyond standard permissions.

## 2. How do you manage processes in Linux?

**Answer:** Every process has a PID. `ps` lists processes (`ps aux` for all users), `top`/`htop` provides real-time monitoring, `kill [PID]` terminates processes, `kill -9 [PID]` force kills. `bg`/`fg` manage background/foreground jobs, `jobs` lists them. `nohup` runs processes immune to hangups. `systemctl` manages systemd services (`start`, `stop`, `enable`, `status`). Process states include Running (R), Sleeping (S), Zombie (Z), Stopped (T). `nice`/`renice` adjust process priority (-20 to 19). `strace` traces system calls, `lsof` lists open files per process.

## 3. Explain the Linux file system hierarchy.

**Answer:** The FHS (Filesystem Hierarchy Standard) defines the structure: `/` is root. `/bin` and `/sbin` contain essential binaries (now often symlinks to `/usr/bin`). `/etc` stores configuration files. `/home` contains user directories. `/var` has variable data like logs (`/var/log`), spools (`/var/spool`). `/tmp` is temporary storage (cleared on reboot). `/dev` contains device files. `/proc` is a virtual filesystem with kernel/process info. `/sys` exposes kernel objects. `/usr` contains user utilities and applications. `/opt` is for optional third-party software. `/mnt` and `/media` are mount points.

## 4. How does piping and redirection work in bash?

**Answer:** Redirection operators: `>` redirects stdout to file (overwrites), `>>` appends, `2>` redirects stderr, `&>` redirects both stdout and stderr, `<` reads from file as stdin. `|` pipes stdout of left command to stdin of right command. Examples: `ls -l | grep ".txt"`, `command > output.log 2>&1`, `cat < input.txt`. Here-strings (`<<<`) and here-documents (`<< EOF`) provide inline input. `tee` writes to both file and stdout simultaneously.

## 5. Explain common networking commands in Linux.

**Answer:** `ip` (replaces ifconfig) shows/manages network interfaces, addresses, routes. `ss` (replaces netstat) shows socket statistics. `ping` tests connectivity via ICMP. `traceroute`/`tracepath` shows the path packets take. `nslookup`/`dig` query DNS records. `curl`/`wget` transfer data via various protocols. `nc` (netcat) reads/writes network connections. `nmap` scans ports and discovers services. `tcpdump` captures and analyzes packets. `iptables`/`nftables` manage firewall rules. `ss -tuln` shows listening TCP/UDP ports.

## 6. What is the difference between a hard link and a symbolic link?

**Answer:** A hard link is a directory entry pointing directly to the inode of the original file. It shares the same inode number and data blocks. Hard links cannot span filesystems or link to directories (typically). Deleting the original file doesn't affect hard links. A symbolic link (symlink) is a special file that contains a path to the target file. It has its own inode. Symlinks can span filesystems and link to directories. If the target is deleted, the symlink becomes broken/dangling.

## 7. How do you schedule tasks in Linux?

**Answer:** `cron` is for recurring tasks. Edit with `crontab -e`. Format: minute hour day-of-month month day-of-week command. `@daily`, `@weekly`, `@reboot` are shorthand. Crontabs are stored in `/var/spool/cron/crontabs/`. System-wide cron jobs are in `/etc/crontab` and `/etc/cron.d/`. `anacron` runs missed jobs (for systems not running 24/7). `at` schedules one-time tasks (`at 10:00 PM`). `systemd.timers` provide an alternative to cron with more flexibility.

## 8. Explain environment variables and how to set them.

**Answer:** Environment variables affect process behavior. Key variables: `PATH` (executable search paths), `HOME` (user home directory), `SHELL` (default shell), `USER` (current username), `LANG` (locale). Set temporarily: `export VAR=value`. Set permanently: add to `~/.bashrc` (user), `~/.bash_profile` (login shell), or `/etc/environment` (system-wide). `echo $VAR` displays value. `env` lists all environment variables. `unset VAR` removes a variable.

## 9. What is the difference between `bash`, `sh`, `zsh`, and other shells?

**Answer:** `sh` (Bourne shell) is the original Unix shell. `bash` (Bourne Again SHell) extends `sh` with features like command history, tab completion, arrays, and arithmetic. `zsh` extends `bash` with advanced globbing, spelling correction, themes/plugins (Oh My Zsh), and better completion. `fish` focuses on user-friendliness with autosuggestions and web-based config. `dash` is a minimal POSIX-compliant shell (Debian default for `/bin/sh`). `ksh` (KornShell) combines Bourne and C shell features. Each shell can be set in `/etc/passwd` or with `chsh`.

## 10. How do you find files in Linux?

**Answer:** `find` searches the filesystem: `find /path -name "*.txt"` (by name), `find /path -type f -size +1M` (by size), `find /path -mtime -7` (modified in last 7 days). `locate` uses a pre-built database (`updatedb` updates it) for faster searches. `which` shows the path of a command. `whereis` finds binary, source, and man pages. `type` explains how a command would be interpreted. `grep -r "pattern" /path` searches file contents recursively.

## 11. Explain the boot process in Linux.

**Answer:** 1) BIOS/UEFI initializes hardware and loads the bootloader. 2) Bootloader (GRUB2) loads the kernel and initramfs into memory. 3) Kernel initializes hardware, mounts root filesystem, and starts init (PID 1). 4) init system (systemd) runs default target unit and starts services. 5) Getty spawns login prompts. Boot messages can be viewed with `dmesg` or `journalctl -b`. Runlevels: 0 (halt), 1 (single-user), 2-4 (multi-user), 5 (graphical), 6 (reboot).

## 12. How do you manage disk partitions and filesystems?

**Answer:** `fdisk`/`gdisk` create/manage MBR/GPT partition tables. `parted` handles both. `mkfs.ext4`, `mkfs.xfs`, `mkfs.btrfs` create filesystems. `mount` attaches filesystems, `umount` detaches. `/etc/fstab` defines persistent mount points. `df -h` shows disk usage, `du -sh *` shows directory sizes. `lsblk` lists block devices. `blkid` shows UUIDs and labels. LVM (Logical Volume Manager) provides flexible volume management with PV, VG, LV. `fsck` checks and repairs filesystem errors.

## 13. What is swap and how is it used?

**Answer:** Swap is disk space used as virtual memory when physical RAM is full. It can be a partition or a file. `swapon`/`swapoff` enable/disable swap. `swapon --show` displays active swap. `free -h` shows RAM and swap usage. The kernel's swappiness parameter (0-100, in `/proc/sys/vm/swappiness`) controls how aggressively swap is used (lower = less swapping). Swap allows overcommitment of memory and supports hibernation (suspend-to-disk). Performance tip: put swap on SSD for better speed.

## 14. Explain how user authentication works in Linux.

**Answer:** Traditional authentication uses `/etc/passwd` (usernames, UIDs, GIDs, home dirs, shells) and `/etc/shadow` (hashed passwords, expiration info). `/etc/group` defines groups. `useradd`/`usermod`/`userdel` manage users. `passwd` changes passwords. PAM (Pluggable Authentication Modules) provides modular authentication (e.g., password strength, LDAP, two-factor). `/etc/pam.d/` contains PAM configs. `su` switches user (requires target password), `sudo` executes as another user (configured in `/etc/sudoers` via `visudo`). SSH key auth uses `~/.ssh/authorized_keys`.

## 15. How do you debug network connectivity issues?

**Answer:** Systematic approach: 1) `ip a` check interface status. 2) `ping 127.0.0.1` verify local stack. 3) `ping gateway_ip` check LAN connectivity. 4) `ping 8.8.8.8` check external routing. 5) `nslookup example.com` verify DNS. 6) `curl -v http://example.com` test application layer. 7) `traceroute` identifies path issues. 8) `ss -tulpn` check if services are listening. 9) `tcpdump -i eth0` capture traffic. 10) Check `iptables -L` for firewall blocks.

## 16. What are Linux capabilities?

**Answer:** Capabilities break root privileges into granular units (CAP_NET_BIND_SERVICE, CAP_DAC_OVERRIDE, etc.) instead of full root access. Tools: `getcap`/`setcap` manage capabilities. Example: `setcap cap_net_bind_service=+ep /usr/bin/program` allows binding privileged ports without root. Used extensively in containers (Docker drops all capabilities by default, adds specific ones). `/proc/[PID]/task/[TID]/status` shows CapEff, CapInh, CapPrm, CapBnd. This reduces attack surface by limiting privilege escalation vectors.

## 17. Explain the purpose of `/etc/passwd` and `/etc/shadow`.

**Answer:** `/etc/passwd` (world-readable) contains: username:password_placeholder:UID:GID:comment:homedir:shell. The password field is typically `x`, indicating the actual hash is in `/etc/shadow`. `/etc/shadow` (root-readable only) contains: username:hashed_password:last_change:min_age:max_age:warn:inactive:expire. Hash format: `$type$salt$hash` where type 6=SHA-512, 5=SHA-256, 1=MD5, y=yescrypt. Shadowing prevents users from reading password hashes, mitigating offline brute-force attacks.

## 18. How do you create and manage services with systemd?

**Answer:** Systemd manages services via unit files in `/etc/systemd/system/` (custom) and `/lib/systemd/system/` (default). A service unit includes `[Unit]` (description, dependencies), `[Service]` (ExecStart, ExecStop, Restart policy, User), `[Install]` (WantedBy). Commands: `systemctl start/enable/stop/disable/restart/status [service]`. `journalctl -u [service]` views logs. `systemctl daemon-reload` reloads configs after changes. Targets replace runlevels: `systemctl isolate multi-user.target`.

## 19. What is a kernel module and how do you manage them?

**Answer:** Kernel modules are loadable drivers/extensions that add functionality to the kernel without rebooting. `lsmod` lists loaded modules. `modprobe` loads/unloads modules (handles dependencies automatically). `modinfo [module]` shows module details. `insmod`/`rmmod` load/unload manually. Module parameters can be set in `/etc/modprobe.d/` or passed via kernel command line. Blacklist modules with `blacklist` in modprobe config. Common modules: filesystem drivers, network drivers, hardware drivers.

## 20. Explain input/output redirection operators in detail with examples.

**Answer:** `cmd > file` - stdout to file (overwrite). `cmd >> file` - stdout to file (append). `cmd 2> file` - stderr to file. `cmd &> file` - both stdout and stderr. `cmd < file` - stdin from file. `cmd << EOF ... EOF` - here-document for multi-line input. `cmd <<< "string"` - here-string. `cmd1 | cmd2` - pipe stdout of cmd1 to cmd2. `cmd 2>&1` - redirect stderr to stdout. `cmd > /dev/null` - discard output. `exec fd<>file` - open file on specific FD. Examples: `find / -name "*.conf" 2>/dev/null`, `grep error < /var/log/syslog | tee errors.log`.

## 21. How would you harden a Linux server?

**Answer:** 1) Keep system updated (`apt update && apt upgrade`). 2) Disable root SSH login (`PermitRootLogin no`). 3) Use SSH key auth instead of passwords. 4) Remove unnecessary services (`systemctl disable`). 5) Configure firewall (`ufw` or `iptables`). 6) Implement fail2ban for brute-force protection. 7) Set proper file permissions and use umask. 8) Enable auditd for logging. 9) Use SELinux or AppArmor for MAC. 10) Regular log monitoring. 11) Disable unused user accounts. 12) Kernel hardening via sysctl (disable IP forwarding, ignore ICMP redirects).

## 22. Explain how the Linux kernel manages memory.

**Answer:** The kernel uses virtual memory with paging. Each process has a virtual address space (stack, heap, text, data segments) mapped to physical pages via page tables. The MMU handles translation. Pages can be in RAM or swapped. The OOM killer terminates processes when memory is exhausted. `/proc/meminfo` shows memory details. `free -h` shows usage. `top`/`htop` shows per-process memory. `vmstat` reports virtual memory statistics. HugePages improve TLB efficiency for large workloads. Page cache and buffer cache speed up disk I/O.

## 23. What are common log files in Linux and how to analyze them?

**Answer:** `/var/log/syslog` or `/var/log/messages` - general system logs. `/var/log/auth.log` - authentication attempts. `/var/log/kern.log` - kernel messages. `/var/log/dmesg` - kernel ring buffer. `/var/log/nginx/access.log` - web server access. `/var/log/faillog` - failed login attempts. `/var/log/boot.log` - boot messages. Tools: `tail -f` for real-time monitoring, `grep` to filter, `journalctl` for systemd logs, `logrotate` manages rotation. `auditd` provides detailed audit trails. `lnav` is an advanced log file navigator.

## 24. Explain the `strace` command and its use cases.

**Answer:** `strace` traces system calls and signals. Syntax: `strace [options] command`. Key options: `-p [PID]` attach to running process, `-e trace=open,read` filter syscalls, `-o file` write to file, `-c` count calls/time, `-f` follow child processes, `-t` add timestamps, `-T` show time spent in syscalls. Use cases: debugging "file not found" errors, identifying performance bottlenecks, reverse engineering, understanding program behavior. Example: `strace -e open,openat ls` shows which files are opened during `ls`.

## 25. How do you work with compressed archives in Linux?

**Answer:** `tar -czf archive.tar.gz dir/` - create gzipped tar. `tar -xzf archive.tar.gz` - extract. `tar -cjf archive.tar.bz2` - bzip2. `tar -cJf archive.tar.xz` - xz. `gzip`/`gunzip` - gzip compression. `bzip2`/`bunzip2` - bzip2. `zip`/`unzip` - ZIP archives. `7z` - 7-Zip with high compression. `zcat`/`zless`/`zgrep` - view/search compressed files without extracting. `tar --list -f archive.tar.gz` - list contents. Daily use: `tar czvf backup-$(date +%F).tar.gz /important/data`.
