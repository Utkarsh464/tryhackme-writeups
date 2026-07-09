# Windows CMD Cheat Sheet

## CMD Commands
| Command | Description |
|---------|-------------|
| `dir` | List directory |
| `cd /d D:\path` | Change drive and directory |
| `mkdir folder` | Create directory |
| `rmdir /s folder` | Remove directory tree |
| `del file` | Delete file |
| `copy src dst` | Copy file |
| `move src dst` | Move/rename |
| `type file` | Display file content |
| `findstr pattern file` | Search (like grep) |
| `ipconfig /all` | Network configuration |
| `netstat -an` | Connections and ports |
| `tasklist` | Running processes |
| `taskkill /PID N /F` | Force kill process |
| `ping -n 4 host` | Ping |
| `tracert host` | Trace route |
| `nslookup domain` | DNS lookup |
| `systeminfo` | System information |
| `whoami` | Current user |
| `net user` | List users |
| `net localgroup` | List local groups |
| `reg query key` | Read registry |

## PowerShell Commands
| Command | Description |
|---------|-------------|
| `Get-ChildItem` | `ls` equivalent |
| `Get-Content file` | `cat` equivalent |
| `Get-Process` | `ps` equivalent |
| `Stop-Process -Name name` | Kill process |
| `Get-Service` | List services |
| `Select-String -Path file -Pattern "text"` | Grep equivalent |
| `Invoke-WebRequest -Uri url` | `curl` equivalent |
| `Get-WmiObject Win32_ComputerSystem` | System info |
| `Get-EventLog -LogName Security` | Security logs |
| `Get-LocalUser` | List local users |
| `New-Item item -ItemType Directory` | mkdir |
| `Set-ExecutionPolicy RemoteSigned` | Enable script execution |