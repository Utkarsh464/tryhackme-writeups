# Defensive Security Intro - Commands

## No specific commands are introduced in this introductory room.

Defensive Security Intro is a conceptual room that does not involve command-line tools. The concepts covered are foundational knowledge that will be applied in later rooms and modules where specific tools and commands are introduced.

## Related Commands (from other modules)

For reference, here are commands commonly used in defensive security that will be covered in later rooms:

| Command | Room | Description |
|---------|------|-------------|
| `tail -f /var/log/syslog` | Logs Fundamentals | Monitor system logs in real-time |
| `grep "Failed password" /var/log/auth.log` | Logs Fundamentals | Search for SSH failures in auth logs |
| `tcpdump -i eth0 port 80` | Networking | Capture HTTP traffic for analysis |
| `wevtutil qe Security /c:10 /rd:true /f:text` | Logs Fundamentals | Query Windows Security event log |
| `stat -c "%Y %n" *` | Logs Fundamentals | Check file modification timestamps |
