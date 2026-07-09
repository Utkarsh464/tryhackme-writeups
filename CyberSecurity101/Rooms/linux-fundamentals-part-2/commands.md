# Commands: Linux Fundamentals Part 2

## User and Group Management

| Command | Description | Example |
|---------|-------------|---------|
| `useradd` | Create a new user | `useradd -m -s /bin/bash bob` |
| `usermod` | Modify user account | `usermod -aG sudo bob` |
| `userdel` | Delete user account | `userdel -r bob` |
| `passwd` | Change user password | `passwd bob` |
| `groupadd` | Create a new group | `groupadd developers` |
| `groupdel` | Delete a group | `groupdel developers` |
| `groups` | Show user group membership | `groups bob` |
| `id` | Display user and group IDs | `id bob` |
| `who` | Show logged-in users | `who` |
| `last` | Show last logins | `last -10` |

## File Permissions

| Command | Description | Example |
|---------|-------------|---------|
| `chmod` | Change file permissions | `chmod 755 script.sh` |
| `chown` | Change file owner and group | `chown bob:bob file.txt` |
| `chgrp` | Change group ownership | `chgrp developers data.txt` |
| `umask` | Set default permission mask | `umask 022` |
| `ls -l` | List with permissions | `ls -l` |

## Process Management

| Command | Description | Example |
|---------|-------------|---------|
| `ps` | Report process status | `ps aux` |
| `top` | Display live processes | `top` |
| `htop` | Interactive process viewer | `htop` |
| `kill` | Send signal to process | `kill -9 1234` |
| `killall` | Kill processes by name | `killall firefox` |
| `pkill` | Kill processes by pattern | `pkill -u bob` |
| `nice` | Run with modified priority | `nice -n 10 command` |
| `renice` | Change running process priority | `renice 5 1234` |
| `bg` | Resume job in background | `bg %1` |
| `fg` | Resume job in foreground | `fg %1` |
| `jobs` | List active jobs | `jobs` |
| `&` | Run command in background | `command &` |

## Service Management

| Command | Description | Example |
|---------|-------------|---------|
| `systemctl start` | Start a service | `systemctl start nginx` |
| `systemctl stop` | Stop a service | `systemctl stop nginx` |
| `systemctl restart` | Restart a service | `systemctl restart ssh` |
| `systemctl enable` | Enable service at boot | `systemctl enable docker` |
| `systemctl disable` | Disable service at boot | `systemctl disable apache2` |
| `systemctl status` | Check service status | `systemctl status ssh` |
| `journalctl` | Query system logs | `journalctl -u ssh` |

## Text Editors

| Command | Description | Example |
|---------|-------------|---------|
| `nano` | Simple terminal text editor | `nano file.txt` |
| `vim` | Advanced modal text editor | `vim file.txt` |
