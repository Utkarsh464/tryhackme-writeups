# whoami

**Who Am I** — a simple command-line utility that prints the current user's username.

## Syntax

```
whoami [options]
```

## Purpose

Display the username associated with the current effective user ID. Often the first command run after gaining initial access during a CTF challenge or penetration test to determine which user context you are operating in. Also used in scripts to verify identity before performing privileged operations.

## Parameters

| Parameter | Description |
|-----------|-------------|
| `--help` | Display help and exit |
| `--version` | Output version information |

(There are essentially no practical options — it is the simplest command in the Unix toolbox.)

## Examples

```bash
# Show current user
whoami
# Output: lightyagami

# After sudo
sudo whoami
# Output: root

# In a script — act differently based on user
if [ "$(whoami)" != "root" ]; then
    echo "Please run as root"
    exit 1
fi

# Compare with who (which shows all logged-in users)
who

# Compare with id (which shows more detail)
id

# Common one-liner to verify user context after privilege escalation
whoami && id

# In CTF — first thing after getting a shell
whoami
# If output is "root", privilege escalation is complete
```

## Related Commands

| Command | Description |
|---------|-------------|
| `who` | Show who is logged in (users + terminals + login times) |
| `id` | Show user and group IDs (more detailed than whoami) |
| `logname` | Show the original login name (ignores su/sudo changes) |
| `users` | List usernames of all currently logged-in users |
| `w` | Show who is logged in and what they are doing |

## Common Mistakes

- Confusing `whoami` with `who am i` — `who am i` shows the user from the login session (original user), while `whoami` shows the effective user (may differ after `su` or `sudo`).
- Forgetting to run `whoami` after privilege escalation — many CTF players escalate but do not verify they are root.
- Assuming `whoami` output is the same as the user who started the process — `sudo command` changes the effective user.

## Real-World Usage

- **CTF basics:** The first command to run after gaining shell access to understand your privileges.
- **Privilege escalation verification:** Run `whoami` after a privilege escalation exploit to confirm you are now root.
- **Scripting:** Restrict script execution to specific users:
  ```bash
  if [ "$(whoami)" != "deploy" ]; then echo "Must be deploy user"; exit 1; fi
  ```
- **Debugging:** Determine why a process has certain permissions by checking the user context.
- **Post-exploitation:** Enumerate user context before running actions that vary by privilege level.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed (GNU coreutils) |
| Windows | Full | `whoami` available in CMD and PowerShell |
| macOS | Full | Pre-installed (BSD version) |

```bash
# Pre-installed on all systems
# (whoami is part of GNU coreutils on Linux)
```
