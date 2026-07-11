# Logs Fundamentals - Commands

## Windows Event Log Commands

| Command | Description |
|---------|-------------|
| `wevtutil el` | List all available event logs |
| `wevtutil gl Security` | Get configuration information for Security log |
| `wevtutil qe Security /c:10 /rd:true /f:text` | Query last 10 Security events, most recent first |
| `wevtutil qe Security /q:"*[System[EventID=4625]]" /c:50 /f:text` | Query last 50 failed logon events |
| `wevtutil qe Security /q:"*[System[EventID=4624]]" /c:50 /f:text` | Query last 50 successful logons |
| `wevtutil qe Security /q:"*[System[EventID=4688]]" /c:50 /f:text` | Query last 50 process creations |
| `wevtutil cl Security` | Clear Security event log (requires admin) |
| `Get-WinEvent -LogName Security -MaxEvents 10` | PowerShell: get last 10 Security events |
| `Get-WinEvent -FilterHashtable @{LogName='Security';ID=4625} -MaxEvents 50` | PowerShell: get last 50 failed logons |

## Linux Log Navigation Commands

| Command | Description |
|---------|-------------|
| `ls /var/log/` | List available log files |
| `tail -f /var/log/syslog` | Monitor syslog in real-time |
| `tail -n 100 /var/log/syslog` | View last 100 syslog lines |
| `head -n 20 /var/log/syslog` | View first 20 syslog lines |
| `cat /var/log/auth.log` | View authentication log |
| `less /var/log/kern.log` | Browse kernel log with pagination |
| `zcat /var/log/auth.log.gz \| tail` | View compressed (rotated) log |
| `journalctl` | View the full systemd journal |
| `journalctl -xe` | View journal with explanations |
| `journalctl -u ssh.service` | View journal entries for SSH service |
| `journalctl --since "2024-01-01" --until "2024-01-02"` | View journal for a specific time range |
| `dmesg` | View kernel ring buffer messages |
| `dmesg -w` | Monitor kernel messages in real-time |

## Log Analysis with grep

| Command | Description |
|---------|-------------|
| `grep "Failed password" /var/log/auth.log` | Find SSH authentication failures |
| `grep "Accepted password" /var/log/auth.log` | Find successful SSH logins |
| `grep "Invalid user" /var/log/auth.log` | Find SSH attempts on non-existent users |
| `grep "sudo" /var/log/auth.log` | Find sudo command executions |
| `grep "404" /var/log/apache2/access.log` | Find HTTP 404 errors |
| `grep -E "500|502|503" /var/log/apache2/access.log` | Find server errors |
| `grep "union\|select\|drop\|insert" /var/log/apache2/access.log -i` | SQL injection keywords in web logs |
| `grep "<script\|alert(" /var/log/apache2/access.log -i` | XSS attempts in web logs |

## Log Analysis with awk

| Command | Description |
|---------|-------------|
| `awk '{print $1}' /var/log/apache2/access.log \| sort \| uniq -c \| sort -rn` | Count requests per IP |
| `awk '{print $9}' /var/log/apache2/access.log \| sort \| uniq -c \| sort -rn` | Count HTTP status codes |
| `awk '$1 ~ /^10\./ {print}' /var/log/apache2/access.log` | Filter logs from a specific IP range |
| `awk '{print $4,$5,$1}' /var/log/apache2/access.log` | Extract timestamp and IP |

## Log Analysis with jq (JSON logs)

| Command | Description |
|---------|-------------|
| `jq '.' /var/log/app.json` | Pretty-print JSON log |
| `jq 'select(.severity=="ERROR")' /var/log/app.json` | Filter JSON logs by severity |
| `jq 'group_by(.source) \| map({source: .[0].source, count: length})' /var/log/app.json` | Count log entries by source |
| `cat /var/log/app.log \| jq -s 'sort_by(.timestamp) \| .[]'` | Sort JSON logs by timestamp |
