# Linux Commands Cheat Sheet

## Navigation
| Command | Description |
|---------|-------------|
| `pwd` | Print working directory |
| `ls -la` | List all files with details |
| `ls -lh` | Human-readable sizes |
| `cd ~` | Go to home directory |
| `cd -` | Go to previous directory |
| `tree -L 2` | Show directory tree 2 levels deep |

## File Operations
| Command | Description |
|---------|-------------|
| `cp -r src dst` | Copy recursively |
| `mv src dst` | Move/rename |
| `rm -rf dir` | Remove forcefully recursively |
| `mkdir -p a/b/c` | Create parent dirs |
| `touch file` | Create empty file / update timestamp |
| `ln -s target link` | Create symlink |
| `find / -name "*.conf"` | Find files by name |
| `find / -size +100M` | Find files > 100MB |
| `rsync -avz src/ dst/` | Sync directories |

## Permissions
| Command | Description |
|---------|-------------|
| `chmod 755 file` | rwxr-xr-x |
| `chmod u+x file` | Add execute for user |
| `chown user:group file` | Change owner/group |
| `umask 022` | Set default permissions |
| `getfacl file` | View ACLs |
| `setfacl -m u:user:rwx file` | Set ACL |

## Processes
| Command | Description |
|---------|-------------|
| `ps aux` | All processes |
| `ps -ef` | Full listing |
| `top -o %MEM` | Sort by memory |
| `htop` | Interactive process viewer |
| `kill -9 PID` | Force kill |
| `pkill -f pattern` | Kill by name pattern |
| `nice -n 19 cmd` | Run with low priority |
| `renice -n -5 PID` | Change priority |
| `nohup cmd &` | Run immune to hup |
| `systemctl start/stop/status service` | Systemd control |

## Networking
| Command | Description |
|---------|-------------|
| `ip a` | Show interfaces |
| `ip r` | Show routing |
| `ss -tulnp` | Listening sockets |
| `ss -tunap` | Active connections |
| `nc -lvnp 4444` | Listen on port |
| `curl -I http://example.com` | Fetch headers |
| `curl -X POST -d "data" URL` | POST request |
| `wget -r url` | Recursive download |
| `tcpdump -i eth0 port 80` | Capture traffic |

## Package Management (APT)
| Command | Description |
|---------|-------------|
| `apt update && apt upgrade -y` | Full upgrade |
| `apt install pkg` | Install package |
| `apt remove pkg` | Remove package |
| `apt purge pkg` | Remove with configs |
| `dpkg -i pkg.deb` | Install .deb |
| `dpkg -l | grep pkg` | List installed |

## Text Processing
| Command | Description |
|---------|-------------|
| `grep -rn "pattern" .` | Recursive search |
| `grep -v pattern` | Invert match |
| `grep -E "regex"` | Extended regex |
| `sed -i 's/old/new/g' file` | Replace in-place |
| `awk '{print $2}' file` | Print column 2 |
| `awk -F: '{print $1}'` | Custom delimiter |
| `sort -t: -k3 -n` | Sort by column numerically |
| `uniq -c` | Count unique lines |
| `wc -l file` | Line count |
| `cut -d: -f1,3 file` | Cut columns |
| `xargs -n1 cmd` | Pass args to cmd |
| `tee file` | Write and display output |
| `diff file1 file2` | Compare files |
