# Module 2: Linux Fundamentals - Quick Reference

## File System Hierarchy
- **/** - Root directory
- **/bin** - Essential user binaries (now often symlink to /usr/bin)
- **/sbin** - System binaries
- **/etc** - Configuration files
- **/home** - User home directories
- **/var** - Variable data (logs in /var/log, spools)
- **/tmp** - Temporary files (cleared on reboot)
- **/dev** - Device files
- **/proc** - Virtual process/kernel information
- **/usr** - User utilities and applications
- **/opt** - Third-party software
- **/boot** - Boot loader files and kernel
- **/mnt** / **/media** - Mount points

## Permission System
- **3 levels**: Owner (u), Group (g), Others (o)
- **3 permissions per level**: Read (r=4), Write (w=2), Execute (x=1)
- **Format**: `-rwxr-xr--` (file type + owner + group + other)
- **Octal**: `chmod 755 file` = rwxr-xr-x
- **Special**: SUID=4xxx, SGID=2xxx, Sticky=1xxx
- **Commands**: `chmod` (change mode), `chown` (change owner), `chgrp` (change group), `umask` (default permissions)

## Essential Commands
- **Navigation**: `pwd`, `ls -la`, `cd`, `tree`
- **File ops**: `cp`, `mv`, `rm -rf`, `mkdir -p`, `touch`, `cat`, `less`, `more`, `head`, `tail -f`
- **Finding**: `find /path -name "*.txt"`, `locate`, `which`, `whereis`, `type`
- **Viewing**: `file` (file type), `stat` (detailed info), `du -sh` (size), `df -h` (disk free)
- **Processes**: `ps aux`, `top`/`htop`, `kill [PID]`, `kill -9 [PID]`, `bg`, `fg`, `jobs`, `nohup`
- **Networking**: `ip a/route/link`, `ss -tuln`, `ping`, `traceroute`, `dig`, `curl`, `wget`, `nc -zv`
- **Users**: `whoami`, `id`, `who`, `w`, `users`, `useradd`, `usermod`, `passwd`, `su`, `sudo -l`

## Redirection & Piping
- `>` redirect stdout (overwrite), `>>` append stdout
- `2>` redirect stderr, `&>` redirect both
- `<` read stdin from file
- `|` pipe stdout to next command
- `tee` write to both file and stdout
- `cmd 2>&1` merge stderr into stdout
- `cmd > /dev/null` discard output

## Text Processing
- **grep** - Search text: `grep -r "pattern" /path`, `grep -i` (case-insensitive), `grep -v` (invert)
- **sed** - Stream editor: `sed 's/old/new/g' file`
- **awk** - Pattern scanning: `awk '{print $1}' file`
- **cut** - Column extraction: `cut -d: -f1 /etc/passwd`
- **sort** - Sort lines: `sort -n` (numeric), `sort -u` (unique)
- **wc** - Word count: `wc -l` (lines), `wc -w` (words)
- **uniq** - Filter repeated lines (requires sorted input)
- **xargs** - Build/execute command from stdin

## Package Management
- **Debian/Ubuntu (APT)**: `apt update`, `apt upgrade`, `apt install pkg`, `apt remove pkg`, `apt search term`
- **Red Hat (YUM/DNF)**: `yum install`, `yum update`, `dnf install`
- **Arch (Pacman)**: `pacman -Syu`, `pacman -S pkg`
- **Snap**: `snap install pkg`
- **Flatpak**: `flatpak install pkg`
- **dpkg/rpm**: Low-level package tools

## Service Management (systemd)
- **Commands**: `systemctl start/stop/enable/disable/restart/status service`
- **View logs**: `journalctl -u service`
- **Reload config**: `systemctl daemon-reload`
- **Targets**: `multi-user.target` (no GUI), `graphical.target` (with GUI)
- **Unit files**: `/etc/systemd/system/` (custom), `/lib/systemd/system/` (default)

## Shell Basics
- **Environment variables**: `export VAR=value`, `echo $VAR`, `env`, `unset VAR`
- **PATH**: `export PATH=$PATH:/new/dir`, persist in ~/.bashrc
- **Aliases**: `alias ll='ls -la'` (persist in ~/.bashrc)
- **History**: `history`, `!n` (rerun command #n), `Ctrl+R` (reverse search)
- **Wildcards**: `*` (any chars), `?` (one char), `[abc]` (character class)
- **Command substitution**: `$(command)` or `` `command` ``
- **Variable substitution**: `${var:-default}`, `${var:?error}`

## File Archiving & Compression
- **tar**: `tar czf archive.tar.gz dir/` (create gzip), `tar xzf archive.tar.gz` (extract)
- **gzip/gunzip**: Compress single files
- **bzip2/bunzip2**: Better compression than gzip
- **xz**: Highest compression ratio
- **zip/unzip**: Universal archive format
- **zcat/zgrep/zless**: Work with compressed files without extracting

## Users & Groups
- `/etc/passwd` - User accounts (world-readable)
- `/etc/shadow` - Password hashes (root-only)
- `/etc/group` - Group definitions
- `/etc/sudoers` - Sudo privileges (edit with `visudo`)
- **GID/UID**: Regular users start at 1000 (UID_MIN in /etc/login.defs)
- **Commands**: `useradd -m user`, `passwd user`, `usermod -aG group user`, `userdel -r user`
