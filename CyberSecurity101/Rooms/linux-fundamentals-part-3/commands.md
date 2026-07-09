# Commands: Linux Fundamentals Part 3

## Shell Scripting

| Command | Description | Example |
|---------|-------------|---------|
| `#!/bin/bash` | Shebang line | First line of script |
| `chmod +x` | Make file executable | `chmod +x script.sh` |
| `read` | Read user input | `read -p "Name: " name` |
| `export` | Set environment variable | `export PATH=$PATH:/new/path` |

## Conditional and Loop Constructs

| Construct | Description | Example |
|-----------|-------------|---------|
| `if [ condition ]` | If-then-else | `if [ -f file ]` |
| `case $var in` | Pattern matching | `case $1 in start)` |
| `for var in list` | Iterate over list | `for i in {1..5}` |
| `while [ condition ]` | Loop while true | `while [ $count -lt 10 ]` |
| `until [ condition ]` | Loop until true | `until ping -c1 host` |
| `test` | Evaluate expression | `test -d /home` |
| `[[ expression ]]` | Extended conditional | `[[ $var == "yes" ]]` |

## Networking Commands

| Command | Description | Example |
|---------|-------------|---------|
| `ip` | Show/manage routing and devices | `ip addr show` |
| `ifconfig` | Configure network interfaces | `ifconfig eth0 up` |
| `ping` | Test network connectivity | `ping -c 4 8.8.8.8` |
| `ss` | Socket statistics | `ss -tuln` |
| `netstat` | Network statistics | `netstat -ano` |
| `ssh` | Secure Shell client | `ssh user@host` |
| `scp` | Secure copy over SSH | `scp file.txt user@host:/tmp/` |
| `rsync` | Remote file synchronization | `rsync -av /src/ /dst/` |
| `curl` | Transfer data from/to URLs | `curl -O https://example.com/file` |
| `wget` | Download files from web | `wget https://example.com/file` |

## Package Management

| Command | Description | Example |
|---------|-------------|---------|
| `apt update` | Update package index | `sudo apt update` |
| `apt install` | Install a package | `sudo apt install nginx` |
| `apt upgrade` | Upgrade all packages | `sudo apt upgrade` |
| `apt remove` | Remove a package | `sudo apt remove nginx` |
| `apt search` | Search packages | `apt search webserver` |
| `dpkg -i` | Install .deb package | `sudo dpkg -i package.deb` |
| `dpkg -l` | List installed packages | `dpkg -l \| grep nginx` |
| `yum install` | Install a package (RHEL) | `sudo yum install httpd` |
| `yum update` | Update packages (RHEL) | `sudo yum update` |

## Task Scheduling

| Command | Description | Example |
|---------|-------------|---------|
| `crontab -e` | Edit crontab file | `crontab -e` |
| `crontab -l` | List crontab entries | `crontab -l` |
| `crontab -r` | Remove crontab | `crontab -r` |
| `at` | Schedule one-time task | `at now + 1 hour` |
