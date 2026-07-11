# SOC Fundamentals - Commands

## No direct command-line commands are introduced in SOC Fundamentals.

This room focuses on SOC concepts, processes, and tool classifications rather than specific command-line utilities. The following table lists common SOC-relevant commands that are used with SIEM and log analysis tools:

## Log Analysis Commands (Reference)

| Command | Description |
|---------|-------------|
| `grep "Failed password" /var/log/auth.log` | Search for SSH authentication failures |
| `grep "Accepted password" /var/log/auth.log` | Search for successful SSH logins |
| `tail -f /var/log/syslog` | Monitor system logs in real-time |
| `journalctl -xe` | View systemd journal with explanations |
| `cat /var/log/apache2/access.log \| awk '{print $1}' \| sort \| uniq -c \| sort -rn` | List unique IP addresses from web logs by frequency |
| `last -10` | Show last 10 logins |
| `w` | Show currently logged-in users |
| `ps aux --sort=-%cpu` | List processes sorted by CPU usage |
| `netstat -tulpn` | Show listening ports and associated processes |
| `ss -tulpn` | Modern alternative to netstat for socket statistics |

## SIEM Query Examples (Reference)

| Query Type | Description |
|-------------|-------------|
| `index=main sourcetype=linux_secure "Failed password"` | Splunk query for SSH failures |
| `source="/var/log/auth.log" and "Accepted publickey"` | Kibana/ELK query for SSH key auth |
| `EventID=4625` | Windows Security log: failed logon |
| `EventID=4624` | Windows Security log: successful logon |
| `EventID=4688` | Windows Security log: process creation |
| `EventID=7045` | System log: service installed |

## SOC Metrics Formulas (Reference)

| Metric | Formula | Description |
|--------|---------|-------------|
| MTTD | Total detection time / Number of incidents | Mean Time to Detect |
| MTTR | Total response time / Number of incidents | Mean Time to Respond |
| TTR | Alert close time - Alert creation time | Time to Resolve |
| FP Rate | False positives / Total alerts | False Positive Rate |
| Escalation Rate | Escalated alerts / Total alerts | Percentage of alerts escalated |
