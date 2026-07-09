# Commands: Operating System Security

## User Management — Windows

| Command | Description |
|---------|-------------|
| `net user /add username password` | Create a local user |
| `net user username /active:no` | Disable a user account |
| `net localgroup Administrators username /add` | Add user to administrators |

## User Management — Linux

| Command | Description |
|---------|-------------|
| `useradd -m username` | Create a new user with home directory |
| `usermod -aG sudo username` | Add user to sudo group |
| `passwd username` | Change user password |
| `chage -M 90 username` | Set password maximum age to 90 days |

## Password Policy

| Command | Description |
|---------|-------------|
| `secpol.msc` | Open Local Security Policy editor (Windows) |
| `net accounts /minpwlen:12` | Set minimum password length (Windows) |
| `net accounts /lockoutthreshold:5` | Set lockout after 5 bad attempts (Windows) |
| `pam-auth-update` | Configure PAM authentication modules (Linux) |
| `chage -l username` | View password expiry details (Linux) |

## Patch Management

| Command | Description |
|---------|-------------|
| `sudo apt update && sudo apt upgrade` | Update Debian/Ubuntu system |
| `sudo yum update` | Update RHEL/CentOS system |

## Logging

| Command | Description |
|---------|-------------|
| `sudo journalctl -xe` | View systemd journal with explanations |
| `auditctl -w /etc/passwd -p wa -k passwd-changes` | Audit changes to passwd (Linux) |
| `wevtutil qe Security /c:20 /rd:true` | Query last 20 security events (Windows) |
| `Get-EventLog Security -Newest 10 -EntryType FailureAudit` | Recent failed logins (PowerShell) |

## Firewall

| Command | Description |
|---------|-------------|
| `sudo iptables -L -v` | List iptables rules with packet counts |
| `sudo ufw enable` | Enable UFW |
| `sudo ufw allow 22/tcp` | Allow SSH via UFW |
| `netsh advfirewall set allprofiles state on` | Enable Windows firewall |
| `netsh advfirewall firewall add rule name="Allow SSH" dir=in action=allow protocol=TCP localport=22` | Create a Windows firewall rule |