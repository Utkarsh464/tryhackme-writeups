# Splunk SIEM

## Purpose
Splunk is a leading Security Information and Event Management (SIEM) platform that ingests, indexes, and analyzes machine-generated data from various sources including servers, network devices, endpoints, applications, and security appliances. It provides real-time visibility into an organization's security posture through log aggregation, correlation, alerting, dashboards, and threat hunting capabilities. Splunk is widely used by Security Operations Centers (SOC) for incident detection, investigation, and response.

## Installation (Splunk Free/Enterprise)
```bash
# Download Splunk Enterprise (14-day trial with full features)
wget -O splunk-9.2.0-<build>-Linux-x86_64.tgz https://www.splunk.com/en_us/download/splunk-enterprise.html

# Debian/Ubuntu
wget -O splunk.deb https://download.splunk.com/products/splunk/releases/9.2.0/linux/splunk-9.2.0-<build>-linux-2.6-amd64.deb
sudo dpkg -i splunk.deb

# RPM (Red Hat/CentOS)
sudo rpm -i splunk-9.2.0-<build>-linux-2.6-x86_64.rpm

# Universal Forwarder (for sending logs to Splunk)
wget -O splunkforwarder.deb https://download.splunk.com/products/universalforwarder/releases/9.2.0/linux/splunkforwarder-9.2.0-<build>-linux-2.6-amd64.deb

# Start Splunk
sudo /opt/splunk/bin/splunk start --accept-license

# Access web interface at http://localhost:8000
```

## Key Components
- **Splunk Enterprise** - Central indexer and search head with web UI
- **Universal Forwarder** - Lightweight agent for log collection
- **Heavy Forwarder** - Full Splunk instance with parsing and filtering
- **Indexers** - Store and index incoming data
- **Search Heads** - Query execution and visualization
- **Deployment Server** - Manage forwarder configurations centrally
- **License Manager** - Enforce daily indexing volume limits

## Searching and SPL (Search Processing Language)
SPL is Splunk's search language for querying indexed data:
```splunk
# Basic search
index=windows EventCode=4625

# Time range and statistics
index=firewall action=blocked | stats count by src_ip

# Threat hunting
index=* sourcetype=WinEventLog:Security EventCode=4688 | search "powershell.exe -enc"

# Correlation
index=web_access status=401 | join type=inner src_ip [search index=firewall action=blocked]

# Alert threshold
index=authentication EventCode=4625 | timechart count by src_ip | where count > 10
```

## Important SPL Commands
- `search` - retrieve events from indexes
- `stats` - compute statistics (`count, sum, avg, distinct_count, values, list`)
- `timechart` - time-based statistics for trend analysis
- `eval` - create calculated fields, perform calculations, string manipulation
- `rex` - extract fields using regular expressions
- `lookup` - enrich data with external lookup tables (CSV, KV store)
- `transaction` - group related events into a single transaction
- `where` - filter results based on conditions
- `dedup` - remove duplicate events
- `top/rare` - find most/least common values
- `table` - format results in table view
- `rename` - rename fields for display
- `convert` - convert between data types
- `sort` - sort results by field values
- `appendcols` - combine results from multiple searches side by side

## Typical Workflow
1. Deploy Universal Forwarders to servers and endpoints to collect logs
2. Configure data inputs for Windows Event Log, Syslog, firewall logs, web server logs, etc.
3. Create data onboarding and parsing configurations (props.conf, transforms.conf)
4. Monitor data volume in Splunk to ensure proper indexing
5. Build real-time correlation searches for known attack patterns
6. Create dashboards for SOC monitoring (failed logins, malware detections, anomalous traffic)
7. Set up alerts for critical events (multiple failures, known bad IPs, unusual process execution)
8. Use Splunk for proactive threat hunting (searching for suspicious patterns before alerts trigger)
9. Investigate incidents by pivoting through related events and sessions

## Advantages
- Extremely flexible data ingestion (any log format, unlimited sources)
- Powerful search language (SPL) for complex analytics
- Real-time alerting and correlation
- Rich visualization and dashboard capabilities
- Extensive app ecosystem (Splunkbase) for security-specific content
- Machine learning toolkit for anomaly detection
- Role-based access control for multi-tenant environments
- REST API for automation and integration

## Limitations
- Very expensive for enterprise deployments (licensing cost based on daily ingest volume)
- Complex to deploy and maintain at scale
- Search performance degrades without proper indexing strategies
- Learning curve for SPL is significant
- Resource-intensive (heavy RAM and CPU requirements for indexers)
- No built-in SOAR capabilities (requires Phantom, now Splunk SOAR)
- Free version limited to 500MB/day ingestion

## Industry Use
Splunk is the dominant SIEM platform used by enterprises, government agencies, MSSPs, and large SOCs. It is used for compliance reporting (PCI DSS, HIPAA, SOX), threat detection, incident investigation, and operational analytics. Splunk is also widely used as a general-purpose log management platform beyond security.

## Official Documentation
- Official Site: https://www.splunk.com
- Documentation: https://docs.splunk.com
- SPL Reference: https://docs.splunk.com/Documentation/Splunk/latest/SearchReference
- Security Essentials App: https://splunkbase.splunk.com/app/3435
- Free Training: https://www.splunk.com/en_us/training.html
