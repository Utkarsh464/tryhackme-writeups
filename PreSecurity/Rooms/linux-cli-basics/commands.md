# Commands: Linux CLI Basics

## Filesystem Navigation

| Command | Description |
|---------|-------------|
| `ls -la` | List all files with permissions and details |
| `cd /path` | Change directory |
| `pwd` | Print working directory |
| `tree -d` | Show directory tree structure |

## File Operations

| Command | Description |
|---------|-------------|
| `touch file` | Create empty file or update timestamp |
| `cp -r source dest` | Copy file or directory (recursive) |
| `mv source dest` | Move or rename a file/directory |
| `rm -i file` | Delete a file (prompt before removal) |
| `rm -rf dir` | Force delete directory (dangerous!) |
| `mkdir -p a/b/c` | Create directories (parents too) |
| `ln -s target link` | Create a symbolic link |

## Permissions

| Command | Description |
|---------|-------------|
| `chmod 755 file` | Set rwxr-xr-x permissions |
| `chmod u+x file` | Add execute for the owner |
| `chown user:group file` | Change owner and group |
| `umask` | Show or set default permission mask |
| `ls -la` | View detailed permission strings |

## Process Management

| Command | Description |
|---------|-------------|
| `ps aux` | Show all processes with full details |
| `top` | Real-time interactive process monitor |
| `htop` | Enhanced interactive process monitor |
| `kill -9 PID` | Force kill a process |
| `kill -15 PID` | Graceful process termination |
| `nice -n 5 ./program` | Run with adjusted priority |

## Text Processing

| Command | Description |
|---------|-------------|
| `grep -ri "pattern" /dir` | Case-insensitive recursive search |
| `sed 's/old/new/g' file` | Global substitution in file |
| `awk '{print $1, $3}' file` | Print specific columns |
| `find / -name "*.conf"` | Find files by name |
| `find / -size +1G` | Find files larger than 1 GB |
| `wc -l file` | Count lines in a file |