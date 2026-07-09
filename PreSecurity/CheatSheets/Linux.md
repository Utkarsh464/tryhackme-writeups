# Linux Cheat Sheet

## File Operations
| Command | Description |
|---------|-------------|
| `ls -la` | List files (detailed, all) |
| `cp -r src dst` | Copy recursively |
| `mv src dst` | Move/rename |
| `rm -rf dir` | Delete recursively (force) |
| `mkdir -p a/b/c` | Create directories (parents) |
| `touch file` | Create empty file / update timestamp |
| `cat file` | Display file |
| `less file` | Paginated file view |
| `head -n 5 file` | First 5 lines |
| `tail -n 5 file` | Last 5 lines |
| `tail -f file` | Follow file (live updates) |

## Permissions
| Command | Effect |
|---------|--------|
| `chmod 755 file` | rwxr-xr-x |
| `chmod 644 file` | rw-r--r-- |
| `chmod 600 file` | rw------- |
| `chmod +x file` | Add execute |
| `chown user:group file` | Change owner/group |
| `umask 022` | Set default permissions |

## Process Management
| Command | Description |
|---------|-------------|
| `ps aux` | All processes |
| `ps -ef` | Full process list |
| `top` | Interactive process monitor |
| `htop` | Enhanced interactive monitor |
| `kill PID` | Terminate process |
| `kill -9 PID` | Force kill |
| `pkill name` | Kill by name |
| `jobs` | Background jobs |
| `fg %1` | Bring job 1 to foreground |
| `&` suffix | Run in background |

## Text Processing
| Command | Description |
|---------|-------------|
| `grep pattern file` | Search for pattern |
| `grep -rni pattern dir/` | Recursive, case-insensitive, line numbers |
| `sort file` | Sort lines |
| `uniq` | Remove duplicates (requires sort) |
| `wc -l` | Count lines |
| `cut -d: -f1 file` | Split by delimiter, get field |
| `awk '{print $1}'` | Print first column |
| `sed 's/old/new/g'` | Replace text |