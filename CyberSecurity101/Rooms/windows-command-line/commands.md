# Commands: Windows Command Line

## Filesystem Navigation

| Command | Description | Example |
|---------|-------------|---------|
| `dir` | List directory contents | `dir C:\Windows` |
| `dir /w` | Wide format listing | `dir /w` |
| `dir /s` | List with subdirectories | `dir /s *.txt` |
| `dir /a` | List including hidden/system files | `dir /a` |
| `cd` | Change directory or display path | `cd C:\Users\bob` |
| `cd ..` | Move up one directory | `cd ..` |
| `cd \` | Go to root of current drive | `cd \` |
| `tree` | Display directory tree | `tree C:\Windows` |

## File Management

| Command | Description | Example |
|---------|-------------|---------|
| `md` or `mkdir` | Create directory | `md C:\NewFolder` |
| `rd` or `rmdir` | Remove directory | `rd C:\OldFolder` |
| `rmdir /s` | Remove directory tree | `rmdir /s C:\Folder` |
| `copy` | Copy files | `copy file.txt C:\Backup\` |
| `move` | Move or rename files | `move file.txt C:\NewLocation\` |
| `del` | Delete files | `del *.tmp` |
| `ren` | Rename files | `ren old.txt new.txt` |
| `type` | Display file contents | `type readme.txt` |
| `more` | Display file with paging | `more longfile.txt` |
| `find` | Search for string in files | `find "error" log.txt` |
| `findstr` | Advanced string search | `findstr /si "password" *.txt` |
| `xcopy` | Copy with directory support | `xcopy /s /e C:\Src C:\Dst` |
| `robocopy` | Robust file copy | `robocopy /mir C:\Src C:\Dst` |

## Networking

| Command | Description | Example |
|---------|-------------|---------|
| `ipconfig` | Display IP configuration | `ipconfig /all` |
| `ping` | Test connectivity | `ping -n 4 google.com` |
| `tracert` | Trace route to host | `tracert google.com` |
| `pathping` | Trace with latency stats | `pathping google.com` |
| `nslookup` | Query DNS | `nslookup example.com` |
| `netstat` | Display network stats | `netstat -ano` |
| `netstat -b` | Show process for connections | `netstat -b` |
| `route print` | Display routing table | `route print` |
| `arp -a` | Display ARP cache | `arp -a` |
| `getmac` | Display MAC addresses | `getmac` |

## System Administration

| Command | Description | Example |
|---------|-------------|---------|
| `systeminfo` | System configuration details | `systeminfo \| find "OS Name"` |
| `tasklist` | List running processes | `tasklist /v` |
| `taskkill` | Terminate a process | `taskkill /PID 1234 /F` |
| `taskkill /IM` | Kill by image name | `taskkill /IM notepad.exe /F` |
| `schtasks` | Schedule tasks | `schtasks /create /tn "Task" /tr "cmd" /sc daily` |
| `schtasks /query` | List scheduled tasks | `schtasks /query /v` |
| `net start` | Start a service | `net start Spooler` |
| `net stop` | Stop a service | `net stop Spooler` |
| `shutdown` | Shutdown or restart | `shutdown /r /t 0` |
| `sfc /scannow` | System File Checker | `sfc /scannow` |
| `chkdsk` | Check disk for errors | `chkdsk C: /f` |
| `diskpart` | Disk partition manager | `diskpart` |
| `driverquery` | List installed drivers | `driverquery /v` |
