# Introduction to SIEM - Commands

## Splunk SPL (Search Processing Language)

| Command | Description |
|---------|-------------|
| `index=main sourcetype="linux_secure" "Failed password"` | Search for SSH failures in Linux auth logs |
| `index=main sourcetype="WinEventLog:Security" EventCode=4625` | Search for Windows failed logon events |
| `index=main sourcetype="WinEventLog:Security" EventCode=4624` | Search for successful Windows logon events |
| `index=main sourcetype="linux_secure" "Accepted password"` | Search for successful SSH logins |
| `index=main sourcetype="WinEventLog:Security" EventCode=4688` | Search for process creation events |
| `index=main sourcetype="WinEventLog:Security" EventCode=4720` | Search for user account creation |
| `index=main sourcetype="linux_secure" \| stats count by src_ip` | Count events by source IP |
| `index=main sourcetype="access_combined" \| top 10 src_ip` | Top 10 IP addresses from web logs |
| `index=main sourcetype="access_combined" status=404 \| stats count by src_ip` | Count 404 errors by IP |
| `index=main \| timechart count by sourcetype` | Event count over time by sourcetype |
| `index=main sourcetype="linux_secure" \| where like(Message,"%Failed%") \| table _time, src_ip, user` | Extract specific field values |
| `index=main sourcetype="linux_secure" "Failed password" \| rex "Failed password for (?<user>\S+)" \| stats count by user` | Extract username from event with regex |
| `index=main sourcetype="WinEventLog:Security" EventCode=4625 \| eval user = coalesce(TargetUserName, "unknown") \| stats count by user` | Use eval for field calculation |

## Splunk Forwarder Commands (Linux)

| Command | Description |
|---------|-------------|
| `./splunk add forward-server 192.168.1.100:9997` | Configure forwarder to send to indexer |
| `./splunk add monitor /var/log/` | Monitor a directory for new log files |
| `./splunk add monitor /var/log/auth.log -index main -sourcetype linux_secure` | Monitor auth.log with specific sourcetype |
| `./splunk list forward-server` | List configured forward servers |
| `./splunk status` | Check Splunk processes status |
| `./splunk restart` | Restart Splunk services |

## Elasticsearch / Kibana Query Commands

| Command | Description |
|---------|-------------|
| `GET /_search { "query": { "match": { "message": "Failed password" } } }` | Elasticsearch query for SSH failures |
| `source:"/var/log/auth.log" AND "Failed password"` | Kibana KQL query for SSH failures |
| `event.code:4625 AND winlog.provider_name:"Microsoft-Windows-Security-Auditing"` | Kibana KQL for failed logon |
| `GET /_cat/indices?v` | List all Elasticsearch indices |
| `GET /_cluster/health` | Check Elasticsearch cluster health |
