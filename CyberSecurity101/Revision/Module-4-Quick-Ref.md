# Module 4: Command Line - Quick Reference

## Shell Fundamentals
- **Bash** - Bourne Again SHell (default on most Linux)
- **Zsh** - Extended bash with themes/plugins (Oh My Zsh)
- **Fish** - User-friendly shell with autosuggestions
- **Command Types**: Built-in (shell internal), External (binary in PATH), Alias, Function
- **Command structure**: `command [options] [arguments]`
- **Short options**: `-v`, `-h` (single dash, single letter)
- **Long options**: `--verbose`, `--help` (double dash, word)
- **Combine short options**: `-la` = `-l -a`

## Essential Commands by Category

### File Operations
- **Create**: `touch file`, `mkdir -p path/to/dir`, `echo "text" > file`
- **Read**: `cat file`, `less file`, `more file`, `head -n 20`, `tail -f file` (follow)
- **Copy/Move/Delete**: `cp -r source dest`, `mv source dest`, `rm -rf dir`, `rm file`
- **Links**: `ln -s target linkname` (symlink), `ln target linkname` (hard link)

### Permissions & Ownership
- `chmod 755 file` - Numeric permissions
- `chmod u+x file` - Symbolic (add execute for user)
- `chown user:group file` - Change owner/group
- `umask 022` - Default permissions mask (result = 777 - mask for files)

### Process Management
- `ps aux` - All processes (BSD style)
- `ps -ef` - All processes (Unix style)
- `top` / `htop` - Interactive process viewer
- `kill -9 PID` - Force kill (SIGKILL)
- `kill -15 PID` - Graceful termination (SIGTERM)
- `pkill process_name` - Kill by name
- `pgrep -a process` - Find PID by name
- `nice -n 10 command` - Run with lower priority
- `renice 10 PID` - Change priority of running process

### Network Commands
- **Interface**: `ip a` (addresses), `ip link` (interfaces), `ip route` (routing)
- **Connection**: `ss -tuln` (listening ports), `ss -tup` (active connections)
- **Testing**: `ping host`, `traceroute host`, `mtr host`
- **DNS**: `nslookup domain`, `dig domain ANY`, `dig -x IP` (reverse)
- **Download**: `curl -O URL`, `wget URL`, `curl -v URL` (verbose)
- **Connectivity**: `nc -zv host port` (port check), `nc -lvnp port` (listener)

### Text Processing (Power User)
- **grep**: `grep -r "pattern" /path/` (recursive), `grep -i` (case-insensitive), `grep -v` (invert match), `grep -c` (count), `grep -E` (extended regex)
- **sed**: `sed 's/old/new/g' file` (replace globally), `sed -i` (in-place), `sed '/pattern/d'` (delete lines)
- **awk**: `awk '{print $1,$3}' file` (columns), `awk -F: '{print $1}' /etc/passwd` (custom delimiter), `awk '/pattern/{print $2}'` (conditional)
- **cut**: `cut -d: -f1,3 file` (delimiter + fields)
- **sort**: `sort -n` (numeric), `sort -r` (reverse), `sort -u` (unique), `sort -k2` (by column)
- **tr**: `tr '[:lower:]' '[:upper:]'` (case conversion), `tr -d ' '` (delete chars)
- **uniq**: Requires sorted input, `-c` (count), `-d` (duplicates only)
- **xargs**: `find . -name "*.log" | xargs rm` (pass input as arguments)

### Regex Patterns
- `^` - Start of line
- `$` - End of line
- `.` - Any single character
- `*` - Zero or more of preceding
- `+` - One or more of preceding
- `?` - Zero or one of preceding
- `[abc]` - Character class
- `[^abc]` - Negated character class
- `(pattern)` - Grouping
- `\d` / `\w` / `\s` - Digit / word char / whitespace

### Scripting Basics
- **Shebang**: `#!/bin/bash` at top of script
- **Variables**: `NAME="value"`, no spaces around `=`, use `$NAME` to reference
- **Quoting**: `"$VAR"` (variable expansion), `'$VAR'` (literal), backticks for command substitution (use `$()` instead)
- **Conditionals**: `if [ "$VAR" = "value" ]; then ...; fi`
- **Comparisons**: `-eq` (equal), `-ne` (not equal), `-lt` (less than), `-gt` (greater than), `= ` (string), `-z` (empty), `-n` (not empty)
- **File tests**: `-f file` (exists/is file), `-d dir` (directory), `-x file` (executable), `-r file` (readable)
- **Loops**: `for i in {1..10}; do ...; done`, `while read line; do ...; done < file`
- **Functions**: `myfunc() { ... }`, call with `myfunc arg1`
- **Exit codes**: 0 = success, non-zero = error, `$?` captures last exit code

### Environment & Config
- **.bashrc**: Executed for interactive non-login shells (user config)
- **.bash_profile** / **.profile**: Executed for login shells
- **.bash_logout**: Executed when shell exits
- **/etc/profile**: System-wide profile
- **/etc/bash.bashrc**: System-wide bashrc
- **Source**: `source ~/.bashrc` or `. ~/.bashrc` to reload

### Job Control
- `command &` - Run in background
- `Ctrl+Z` - Suspend foreground process
- `bg` - Resume suspended job in background
- `fg` - Bring job to foreground
- `jobs` - List background jobs
- `disown %n` - Remove job from shell's job table

### SSH
- `ssh user@host` - Basic connection
- `ssh -p 2222 user@host` - Custom port
- `ssh-keygen -t ed25519` - Generate key pair
- `ssh-copy-id user@host` - Copy public key to server
- `ssh -L 8080:localhost:80 user@host` - Local port forwarding
- `ssh -R 8080:localhost:80 user@host` - Remote port forwarding
- `ssh -D 9050 user@host` - SOCKS proxy (dynamic forwarding)
- `scp file user@host:/path/` - Secure copy
- `sftp user@host` - Secure FTP

### Permissions (Extended)
- **SUID (4xxx)**: Runs with owner's permissions (`chmod u+s file`, appears as `s` in owner x)
- **SGID (2xxx)**: Runs with group's permissions (`chmod g+s file`, appears as `s` in group x)
- **Sticky (1xxx)**: Only owner can delete (`chmod +t dir`, appears as `t` in other x)
- **ACLs**: `getfacl file`, `setfacl -m u:user:rwx file` (granular permissions)
- **Find SUID files**: `find / -perm -4000 2>/dev/null`
- **Capabilities**: `getcap -r / 2>/dev/null`, `setcap cap_net_bind_service=+ep /usr/bin/app`

### System Information
- `uname -a` - Kernel info
- `lsb_release -a` - Distribution info
- `cat /etc/os-release` - OS details
- `lscpu` - CPU info
- `lsblk` - Block devices
- `free -h` - Memory usage
- `df -h` - Disk usage
- `du -sh *` - Directory sizes
- `dmesg` - Kernel messages
- `uptime` - System uptime
- `hostnamectl` - Hostname info
