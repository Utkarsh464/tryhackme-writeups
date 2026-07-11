# Logs Fundamentals - Tasks

## Task 1: Introduction to Logging
- Understand what logs are and why they are important
- Learn about the different types of logs (system, application, security, network)
- Understand log levels (DEBUG, INFO, WARNING, ERROR, CRITICAL)
- Learn about log rotation and retention policies

## Task 2: Windows Event Logs
- Understand the Windows Event Log system structure
- Explore the three main Windows logs: Application, System, Security
- Learn common Security Event IDs and their meanings
- Use Windows Event Viewer to browse and filter logs
- Use wevtutil command-line tool to query logs

## Task 3: Windows Security Logs - Authentication Events
- Identify successful logon events (Event ID 4624)
- Identify failed logon events (Event ID 4625)
- Understand logon types (interactive, network, batch, service)
- Identify account lockout events (Event ID 4740)
- Recognize brute-force attacks in authentication logs

## Task 4: Windows Security Logs - Account and Process Events
- Identify user account creation (Event ID 4720)
- Identify user added to privileged group (Event ID 4732/4728/4756)
- Identify process creation events (Event ID 4688)
- Identify service installation events (Event ID 7045)
- Identify privilege escalation patterns

## Task 5: Linux System Logs
- Navigate the /var/log directory structure
- Understand syslog, auth.log, kern.log, and dmesg
- Read and interpret authentication log entries
- Understand systemd journal and journalctl
- Configure rsyslog for log management

## Task 6: Linux Authentication Logs
- Identify successful SSH logins in auth.log
- Identify failed SSH login attempts
- Recognize brute-force attack patterns
- Identify sudo command execution events
- Track user account changes

## Task 7: Web Server Logs
- Understand Common Log Format (CLF) for Apache/Nginx
- Identify HTTP status codes in access logs
- Recognize common web attacks in logs (SQLi, XSS, path traversal)
- Analyze error logs for application issues
- Extract interesting patterns from web traffic

## Task 8: Log Analysis with Command-Line Tools
- Use grep to search for patterns in log files
- Use awk to extract and format specific fields
- Use sed to transform and filter log data
- Use cut and sort for basic log processing
- Use tail and head to view specific log segments
- Use jq to parse JSON-structured logs

## Task 9: Log Collection and Centralization
- Understand the importance of centralized logging
- Configure Syslog for Linux log forwarding
- Understand Windows Event Forwarding (WEF)
- Learn about log shipping to SIEM platforms
- Understand log format normalization

## Task 10: Log Security
- Understand log integrity protection (WORM storage, hashing, signing)
- Prevent log tampering and deletion by attackers
- Protect log data confidentiality
- Configure appropriate log retention periods
- Understand compliance requirements for log retention

## Task 11: Practical Log Analysis
- Review a set of log files from a simulated attack
- Identify Indicators of Compromise in the logs
- Reconstruct the attack timeline
- Determine the scope of the compromise
- Document findings with supporting log evidence
