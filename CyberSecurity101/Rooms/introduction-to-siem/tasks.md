# Introduction to SIEM - Tasks

## Task 1: Introduction to SIEM
- Understand what SIEM is and its purpose
- Learn the difference between SIM and SEM
- Understand the evolution of SIEM technology
- Recognize the role of SIEM in SOC operations

## Task 2: SIEM Architecture
- Understand data collection and forwarding agents
- Learn about log parsing and normalization
- Explore the indexing and storage layer
- Understand the search and visualization layer
- Learn about alerting and correlation engines

## Task 3: Log Collection and Forwarding
- Configure Splunk Universal Forwarder on Linux
- Configure Splunk Universal Forwarder on Windows
- Understand syslog forwarding to SIEM
- Learn about Windows Event Collection (WEC)
- Verify log data is reaching the SIEM

## Task 4: Log Parsing and Normalization
- Understand why raw logs need parsing
- Learn about field extraction and key-value pairs
- Explore timestamp normalization
- Understand CIM (Common Information Model) in Splunk
- Create custom parsing rules for non-standard logs

## Task 5: SIEM Query Languages
- Learn Splunk SPL (Search Processing Language) basics
- Understand search terms, pipes, and commands
- Learn Kibana Query Language (KQL) syntax
- Practice filtering, transforming, and visualizing data
- Use time range and field-based filters

## Task 6: Splunk SPL Commands
- Use `search` to filter events by keywords and fields
- Use `stats` to calculate statistics (count, sum, avg)
- Use `top` and `rare` for frequency analysis
- Use `timechart` for time-based trending
- Use `table` and `fields` to control output columns
- Use `eval` for calculated fields
- Use `rex` for regex field extraction
- Use `lookup` for data enrichment
- Use `join` and `append` for combining data
- Use `transaction` for grouping related events
- Use `eventstats` and `streamstats` for contextual stats
- Use `geostats` for geographic visualization
- Use `sichart` for single-value visualizations
- Use `chart` for data aggregation and visualization
- Use `where` and `search` for filtering results
- Use `dedup` for removing duplicate events

## Task 7: Creating Dashboards
- Understand dashboard structure (panels, rows, inputs)
- Create time-based charts for attack trends
- Create tables for detailed event listings
- Add input controls (time pickers, dropdowns)
- Share dashboards with the SOC team

## Task 8: Correlation Rules and Alerting
- Understand what correlation rules do
- Create a rule for brute-force detection
- Create a rule for malware beaconing detection
- Configure alert actions (email, ticket creation)
- Tune rules to reduce false positives

## Task 9: SIEM Use Cases
- Detect brute-force attacks across multiple systems
- Identify impossible travel (impossible login sequences)
- Detect malware command and control communications
- Monitor for unauthorized privilege escalation
- Track data exfiltration via large outbound transfers

## Task 10: SIEM in Compliance and Operations
- Understand PCI DSS log retention requirements
- Understand HIPAA audit control requirements
- Generate compliance reports from SIEM data
- Use SIEM for operational troubleshooting (not just security)

## Task 11: Practical SIEM Exercise
- Configure log collection for a simulated environment
- Search for specific security events
- Create a dashboard monitoring key security metrics
- Configure an alert for a specific threat scenario
- Investigate and document findings using SIEM data
