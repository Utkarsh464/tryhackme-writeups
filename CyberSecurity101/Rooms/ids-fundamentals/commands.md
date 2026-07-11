# IDS Fundamentals - Commands

## Snort Commands

| Command | Description |
|---------|-------------|
| `snort -T -c /etc/snort/snort.conf` | Test Snort configuration for errors |
| `snort -A console -c /etc/snort/snort.conf -i eth0` | Run Snort with console alert output |
| `snort -A fast -c /etc/snort/snort.conf -l /var/log/snort` | Run with fast alert mode to log directory |
| `snort -A full -c /etc/snort/snort.conf -l /var/log/snort` | Run with full alert mode |
| `snort -q -c /etc/snort/snort.conf -i eth0` | Run in quiet mode (only alerts) |
| `snort -c /etc/snort/snort.conf -r capture.pcap` | Analyze a pcap file offline |
| `snort -v -i eth0` | Run in sniffer mode (verbose) |
| `snort -vd -i eth0` | Sniffer mode with packet payload (hex/ASCII) |
| `snort -X -i eth0` | Sniffer mode with link-layer headers |
| `snort --dump-dynamic-rules` | Dump dynamically loaded rules |

## Suricata Commands

| Command | Description |
|---------|-------------|
| `suricata -T -c /etc/suricata/suricata.yaml` | Test Suricata configuration |
| `suricata -c /etc/suricata/suricata.yaml -i eth0` | Run Suricata on interface |
| `suricata -c /etc/suricata/suricata.yaml -r capture.pcap` | Analyze pcap with Suricata |
| `suricata -c /etc/suricata/suricata.yaml -i eth0 -l /var/log/suricata/` | Run with custom log directory |
| `suricata --list-app-layer-protos` | List supported application layer protocols |
| `suricata --build-info` | Show Suricata build information |
| `suricata --dump-config` | Dump current configuration |
| `suricata --list-keywords=all` | List all rule keywords |
| `suricata-sync` | Update Suricata rules (if configured) |
| `suricata-update` | Update Suricata rulesets (newer method) |

## Snort/Suricata Rule Examples

| Rule | Description |
|------|-------------|
| `alert tcp $EXTERNAL_NET any -> $HOME_NET 80 (msg:"SQL Injection"; content:"union"; nocase; sid:1000001; rev:1;)` | Basic SQL injection detection (simplified) |
| `alert tcp $HOME_NET any -> $EXTERNAL_NET 443 (msg:"Malware Beacon"; content:"|00 00 00|"; offset:0; depth:3; flow:established; sid:1000002; rev:1;)` | Simple beacon detection pattern |
| `alert tcp $EXTERNAL_NET any -> $HOME_NET 22 (msg:"SSH Brute Force"; flow:to_server,established; threshold:type both, track by_src, count 10, seconds 60; sid:1000003; rev:1;)` | SSH brute-force detection with threshold |
| `alert ip $EXTERNAL_NET any -> $HOME_NET any (msg:"Known Malicious IP"; reference:url, threatintel.example.com; sid:1000004; rev:1;)` | Alert on known malicious IP |
| `drop tcp $EXTERNAL_NET any -> $HOME_NET 445 (msg:"EternalBlue Exploit"; content:"|00 00 00 31 ff 53 4d 42|"; sid:1000005; rev:1;)` | IPS drop rule for SMB exploit |

## Log Analysis Commands

| Command | Description |
|---------|-------------|
| `tail -f /var/log/snort/alert` | Monitor Snort alerts in real-time |
| `cat /var/log/suricata/fast.log \| head -50` | View last 50 Suricata fast alerts |
| `cat /var/log/suricata/eve.json \| jq '. \| select(.alert.severity==1)'` | View critical severity alerts from Suricata JSON log |
| `cat /var/log/suricata/eve.json \| jq -c 'select(.event_type=="alert") \| {timestamp: .timestamp, signature: .alert.signature, src_ip: .src_ip, dest_ip: .dest_ip}'` | Extract alert fields from Suricata JSON |
| `grep "Classification:" /var/log/snort/alert \| sort \| uniq -c \| sort -rn` | Count alerts by classification |
| `awk '{print $4}' /var/log/suricata/fast.log \| sort \| uniq -c \| sort -rn` | Count top alert sources from fast.log |
