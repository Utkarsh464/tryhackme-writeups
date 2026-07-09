# adduser / useradd

**User Add** — command-line utilities for creating new user accounts on Linux. `adduser` is the interactive, user-friendly Perl wrapper; `useradd` is the low-level binary.

## Syntax

```
adduser <username>           # Interactive (Debian/Ubuntu style)
useradd [options] <username> # Low-level
```

## Purpose

Create user accounts on a Linux system — setting up home directories, default shell, group memberships, and password policies. Essential for system administration and CTF privilege escalation scenarios.

## Common Parameters (useradd)

| Parameter | Description |
|-----------|-------------|
| `-m` / `--create-home` | Create home directory |
| `-d <dir>` | Home directory path |
| `-s <shell>` | Login shell (e.g., `/bin/bash`) |
| `-g <group>` | Primary group |
| `-G <group1,group2>` | Supplementary groups |
| `-u <uid>` | Custom UID |
| `-c <comment>` | Full name or comment (GECOS field) |
| `-e <date>` | Account expiration date |
| `-f <days>` | Days after password expires before account is disabled |
| `-r` | Create system account |
| `-M` | Do not create home directory |

## Common Parameters (adduser — Debian/Ubuntu)

| Parameter | Description |
|-----------|-------------|
| `--home <dir>` | Home directory |
| `--shell <shell>` | Login shell |
| `--uid <id>` | Custom UID |
| `--gid <id>` | Primary group ID |
| `--ingroup <group>` | Add to specific group |
| `--disabled-password` | Create without password |
| `--no-create-home` | Skip home directory creation |
| `--system` | Create system account |

## Examples

```bash
# Basic interactive user creation (Debian/Ubuntu)
sudo adduser alice

# Minimal user creation with useradd
sudo useradd -m -s /bin/bash bob

# Useradd with full options
sudo useradd -m -d /home/charlie -s /bin/bash -G sudo,www-data -c "Charlie Admin" charlie

# Create user without password (useful for service accounts)
sudo adduser --disabled-password --gecos "" svc_account

# Create user and set password in one line
sudo useradd -m -s /bin/bash dave && echo "dave:Password123" | sudo chpasswd

# Create system account (no login, no home)
sudo useradd -r -s /usr/sbin/nologin my_service

# Set password for an existing user
sudo passwd alice

# Create user with expired password (must change on first login)
sudo useradd -m -s /bin/bash eve
sudo passwd -e eve

# Create user with specific UID
sudo useradd -u 1500 -m -s /bin/bash frank

# Remove a user
sudo userdel -r alice  # -r removes home directory and mail spool
```

## adduser vs useradd

| Feature | adduser | useradd |
|---------|---------|---------|
| Interface | Interactive, prompts for password/GECOS | Command-line only |
| Defaults | Creates home, sets shell, prompts for password | Does nothing unless flags specified |
| Distribution | Debian/Ubuntu default | Available everywhere |
| Complexity | Simple, great for beginners | Full control for scripting |

## Post-Creation Steps

```bash
# Set/change password
sudo passwd username

# Lock a user account
sudo usermod -L username

# Unlock a user account
sudo usermod -U username

# Add user to sudo group
sudo usermod -aG sudo username

# View user information
id username
finger username  # if finger is installed

# Check /etc/passwd entry
grep "^username:" /etc/passwd
```

## Common Mistakes

- Forgetting `-m` with `useradd` — no home directory is created, which can break applications expecting one.
- Not setting a password — the account is created but cannot log in.
- Not adding the user to `sudo` (or `wheel`) group — cannot execute privileged commands.
- Using `adduser` without `sudo` on many systems — the wrapper prompts for root but not always.
- Creating users with `useradd` and assuming it is interactive — it is silent and creates accounts with no password, no home.

## Real-World Usage

- **CTF privilege escalation:** Create a new user with sudo privileges or add yourself to groups.
- **System administration:** Onboard new team members with appropriate access.
- **Service accounts:** Create non-login users for running services (nginx, mysql, etc.).
- **Container management:** Create application users inside Docker containers.
- **Lab environments:** Quickly set up multiple users for testing.

## Compatibility

| OS | Command | Notes |
|----|---------|-------|
| Linux | `adduser` / `useradd` | Both available |
| Windows | N/A | `net user` or `New-LocalUser` in PowerShell |
| macOS | `dscl` or System Preferences | Different approach (directory services) |

```bash
# Pre-installed on all Linux distributions
```
