# Incident Response Fundamentals - Commands

## Triage and Investigation Commands

| Command | Description |
|---------|-------------|
| `who` | Show currently logged-in users |
| `last` | Show recent login history |
| `lastb` | Show failed login attempts |
| `w` | Show who is logged in and what they are doing |
| `ps aux --sort=-%cpu` | List processes sorted by CPU usage |
| `ps aux --sort=-%mem` | List processes sorted by memory usage |
| `netstat -tulpn` | Show listening ports and connections |
| `ss -tulpn` | Modern alternative to netstat |
| `lsof -i` | List open network files and connections |
| `lsof -p PID` | List files opened by a specific process |

## System Information Gathering

| Command | Description |
|---------|-------------|
| `uname -a` | Show all system information |
| `hostname` | Show system hostname |
| `uptime` | Show system uptime |
| `free -h` | Show memory usage in human-readable format |
| `df -h` | Show disk usage |
| `mount -l` | Show mounted file systems |
| `cat /etc/passwd` | List local user accounts |
| `cat /etc/shadow` | List password hashes (root only) |
| `getent group` | List system groups |
| `ip addr` | Show IP addresses and network interfaces |
| `ip route` | Show routing table |

## Log Analysis Commands

| Command | Description |
|---------|-------------|
| `journalctl -xe` | View systemd journal with explanations |
| `journalctl -u ssh.service --since "1 hour ago"` | View SSH service logs for last hour |
| `grep "Failed password" /var/log/auth.log` | Search SSH failure logins |
| `grep "Accepted" /var/log/auth.log` | Search successful logins |
| `tail -n 100 /var/log/syslog` | View last 100 syslog entries |
| `cat /var/log/apache2/access.log \| cut -d' ' -f1 \| sort \| uniq -c \| sort -nr \| head -10` | Top 10 IPs from Apache access log |

## Windows Incident Response Commands

| Command | Description |
|---------|-------------|
| `wevtutil qe Security /c:50 /rd:true /f:text \| findstr /i "4625"` | View last 50 failed logon events |
| `wevtutil qe Security /c:50 /rd:true /f:text \| findstr /i "4624"` | View last 50 successful logon events |
| `wevtutil qe System /c:50 /rd:true /f:text \| findstr /i "7045"` | View last 50 service installations |
| `netstat -anob` | Show connections with owning process (admin) |
| `tasklist /v` | Show detailed process list |
| `wmic process list full` | Show full process information |
| `schtasks /query /fo LIST /v` | List all scheduled tasks |
| `net user username` | Show user account details |

## Containment Commands

| Command | Description |
|---------|-------------|
| `kill -9 PID` | Force terminate a process (Linux) |
| `taskkill /F /PID 1234` | Force terminate a process (Windows) |
| `iptables -A INPUT -s 10.10.10.10 -j DROP` | Block an IP address using iptables |
| `ufw deny from 10.10.10.10` | Block an IP address using UFW |
| `passwd -l username` | Lock a user account (Linux) |
| `net user username /active:no` | Disable a user account (Windows) |
| `ip link set eth0 down` | Bring network interface down (disconnect host) |
