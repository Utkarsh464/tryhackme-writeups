# Commands: Windows Basics

## File System and Permissions (CMD)

| Command | Description |
|---------|-------------|
| `icacls C:\path` | View file/folder NTFS permissions (ACLs) |
| `icacls C:\path /grant User:F` | Grant Full Control to a user |
| `icacls C:\path /inheritance:r` | Disable permission inheritance |
| `dir /r` | Show files and their Alternate Data Streams |
| `cipher /e C:\path` | Encrypt a folder with EFS |

## User Management (CMD)

| Command | Description |
|---------|-------------|
| `net user username /add` | Create a local user account |
| `net user username *` | Set password for a user |
| `net localgroup Administrators` | Show Administrators group members |
| `whoami` | Show current user and privileges |

## Processes and Services (CMD)

| Command | Description |
|---------|-------------|
| `tasklist /v` | List processes with verbose details |
| `tasklist /svc` | Show services hosted in each process |
| `net start "Service Name"` | Start a service |
| `net stop "Service Name"` | Stop a service |
| `sc query` | Query all service statuses |
| `sc config ServiceName start= disabled` | Set service to disabled |

## Event Logs (CMD)

| Command | Description |
|---------|-------------|
| `wevtutil qe Security /c:10 /rd:true` | Query last 10 security events |
| `wevtutil el` | List all event log names |

## Registry (CMD)

| Command | Description |
|---------|-------------|
| `reg query HKLM\SOFTWARE\...\Run` | Query Registry Run keys (persistence) |
| `reg add HKLM\...\Run /v App /t REG_SZ /d "c:\app.exe"` | Add a Registry entry |
| `reg export HKCR\somekey backup.reg` | Export a Registry key for backup |

## PowerShell

| Command | Description |
|---------|-------------|
| `Get-Process` | List running processes (PowerShell) |
| `Get-Service` | List all services (PowerShell) |
| `Get-EventLog Security -Newest 10` | Show last 10 security events |
| `Get-WmiObject -Class Win32_ComputerSystem` | Get system information |