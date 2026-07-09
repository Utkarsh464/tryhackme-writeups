# Commands: Operating Systems Introduction

## Kernel and System Info

| Command | Description |
|---------|-------------|
| `uname -a` | Show all kernel/system information |
| `cat /proc/version` | Show kernel version string |
| `lsmod` | List loaded kernel modules |
| `modinfo <module>` | Show information about a kernel module |

## Process Management

| Command | Description |
|---------|-------------|
| `ps -eo pid,comm,%cpu,%mem,pri` | Detailed process list with priority |
| `top` | Real-time process monitoring |
| `htop` | Interactive process viewer (enhanced top) |
| `nice -n 10 ./program` | Run a program with adjusted priority |
| `kill -9 <pid>` | Force kill a process |

## Memory

| Command | Description |
|---------|-------------|
| `free -h` | Show RAM and swap usage |
| `cat /proc/meminfo` | Detailed memory statistics |
| `vmstat 1` | Virtual memory statistics every second |

## File System

| Command | Description |
|---------|-------------|
| `lsblk -f` | List block devices with file system info |
| `df -hT` | Show mounted file system types and usage |
| `stat /etc/passwd` | Display inode metadata for a file |
| `mount | column -t` | Show all mounted file systems |

## Shell

| Command | Description |
|---------|-------------|
| `echo $SHELL` | Show the current shell path |
| `cat /etc/shells` | List available shells on the system |
| `echo $0` | Show the name of the current shell |