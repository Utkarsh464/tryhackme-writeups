# ps

**Process Status** — a command-line utility that displays information about currently running processes.

## Syntax

```
ps [options]
```

## Purpose

View active processes, their PIDs, resource usage, and state. Essential for monitoring system health, identifying malicious or misbehaving processes, and managing running services.

## Common Options (BSD / UNIX / GNU Styles)

| Option | Description |
|--------|-------------|
| `ps -e` | All processes (equivalent to `-A`) |
| `ps -f` | Full-format listing |
| `ps -l` | Long format |
| `ps -u <user>` | Processes for a specific user |
| `ps -p <PID>` | Specific PID(s) |
| `ps aux` | All processes (BSD style: user, detailed) |
| `ps -ef` | All processes with full format (System V style) |
| `ps axjf` | Show process tree |
| `ps -eo <format>` | Custom output format |
| `--sort=<field>` | Sort by field (e.g., `-%mem`, `%cpu`) |

## Common Columns

| Column | Meaning |
|--------|---------|
| `PID` | Process ID |
| `PPID` | Parent Process ID |
| `USER` | Owner of the process |
| `%CPU` | CPU usage percentage |
| `%MEM` | Memory usage percentage |
| `VSZ` | Virtual memory size |
| `RSS` | Resident Set Size (physical memory) |
| `TTY` | Controlling terminal |
| `STAT` | Process state (R=running, S=sleeping, Z=zombie, T=stopped) |
| `TIME` | Total CPU time used |
| `CMD` | Command that started the process |

## Examples

```bash
# List all running processes
ps -e

# Detailed view of all processes (BSD style)
ps aux

# Full-format listing (System V style)
ps -ef

# Find a specific process
ps aux | grep "nginx"

# Show process tree
ps axjf

# Processes for a specific user
ps -u www-data

# Custom output format
ps -eo pid,ppid,user,%mem,%cpu,cmd --sort=-%mem

# Show top 5 memory-consuming processes
ps -eo pid,user,%mem,cmd --sort=-%mem | head -6

# Show parent-child relationships
ps -eo pid,ppid,user,cmd

# Watch changing process list
watch -n 1 'ps aux --sort=-%cpu | head -20'
```

## Common Mistakes

- Searching for processes by `grep` without excluding the grep process itself:
  `ps aux | grep "apache"` also matches the grep command. Use `ps aux | grep "[a]pache"` to avoid this.
- Using `ps` without options — shows only processes in the current terminal, which is usually nearly empty.
- Confusing BSD (`ps aux`) and System V (`ps -ef`) syntax — both work but have different columns.
- Not realizing that `ps` is a snapshot — it does not update live. Use `top` or `htop` for real-time monitoring.
- Killing a PID without checking PPID — the parent process may restart it immediately.

## Real-World Usage

- **Incident response:** Identify suspicious processes running on a compromised system.
- **Performance troubleshooting:** Find processes consuming excessive CPU or memory.
- **CTF challenges:** Locate running reverse shells, backdoors, or flag-generating processes.
- **System administration:** Check if a service is running before attempting to restart it.
- **Scripting:** Capture PID for later use (e.g., `PID=$(pgrep nginx)`).

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed (procps-ng) |
| Windows | Limited | `tasklist` or `Get-Process` in PowerShell |
| macOS | Full | Pre-installed (BSD ps) |

```bash
# ps is pre-installed on all Linux/macOS systems
```
