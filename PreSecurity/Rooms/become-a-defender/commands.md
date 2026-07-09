# Commands: Become a Defender

## File Analysis

| Command | Description |
|---------|-------------|
| `sha256sum file.exe` | Compute SHA-256 hash of suspicious file |
| `md5sum file.exe` | Compute MD5 hash for threat intelligence lookup |
| `file suspicious.bin` | Determine file type |
| `strings suspicious.exe` | Extract printable strings from binary |
| `hexdump -C file.bin` | Full hex dump of file |

## Network Analysis

| Command | Description |
|---------|-------------|
| `tcpdump -i eth0 port 80` | Capture HTTP traffic |
| `tcpdump -r capture.pcap` | Read a packet capture file |
| `ss -tuln` | List listening ports and services |
| `lsof -i :80` | Show processes using port 80 |

## Log Analysis

| Command | Description |
|---------|-------------|
| `journalctl -u sshd` | View SSH daemon logs |
| `tail -f /var/log/syslog` | Monitor system log in real time |
| `grep "Failed password" /var/log/auth.log` | Find failed SSH login attempts |

## System Monitoring

| Command | Description |
|---------|-------------|
| `top` | View running processes |
| `ps aux` | List all processes |
| `netstat -ano` | Show network connections and PIDs |
| `lsof` | List open files and processes |
