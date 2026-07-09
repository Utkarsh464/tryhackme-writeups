# Windows Command Prompt Cheat Sheet

## Navigation & Directory
| Command | Description |
|---------|-------------|
| `dir /a` | Show all files incl. hidden |
| `dir /s pattern` | Recursive search |
| `dir /b` | Bare format (names only) |
| `dir /o:-s` | Sort by size descending |
| `cd /d D:\path` | Change drive & directory |
| `pushd path` | Push directory to stack |
| `popd` | Pop directory from stack |
| `tree /f` | Show file tree |

## File Operations
| Command | Description |
|---------|-------------|
| `copy src dst` | Copy file |
| `xcopy /E /I /H src dst` | Copy dirs with subdirs |
| `robocopy src dst /MIR` | Mirror directory |
| `move src dst` | Move/rename |
| `del /f /q file` | Force quiet delete |
| `rmdir /s /q dir` | Remove dir tree |
| `ren old new` | Rename |
| `type file` | Display file content |
| `more file` | Page through file |
| `fc file1 file2` | Compare files |
| `comp file1 file2` | Compare byte-byte |
| `attrib +h/-h +r/-r +s/-s file` | Set attributes |

## Disk & System
| Command | Description |
|---------|-------------|
| `systeminfo` | System configuration |
| `systeminfo \| find "Boot Time"` | Get uptime |
| `ver` | OS version |
| `wmic os get Caption,OSArchitecture` | OS info |
| `wmic cpu get Name,NumberOfCores` | CPU info |
| `wmic memorychip get Capacity,Speed` | RAM info |
| `diskpart` | Disk partition tool |
| `chkdsk /f C:` | Check disk for errors |
| `fsutil volume diskfree C:` | Free space |
| `vol C:` | Volume label/serial |

## Networking
| Command | Description |
|---------|-------------|
| `ipconfig /all` | Full network config |
| `ipconfig /displaydns` | DNS cache |
| `ipconfig /flushdns` | Clear DNS cache |
| `ipconfig /release && ipconfig /renew` | Renew DHCP |
| `ping -t target` | Continuous ping |
| `ping -n 10 target` | Ping 10 times |
| `tracert target` | Trace route |
| `pathping target` | Route with latency stats |
| `nslookup domain` | DNS lookup |
| `netstat -ano` | All connections with PIDs |
| `netstat -anb` | With binary names (admin) |
| `netstat -r` | Routing table |
| `route print` | Routing table |
| `arp -a` | ARP cache |
| `getmac /v` | MAC addresses |
| `telnet host port` | Test TCP connection |
| `net view` | Network shares |

## Processes & Services
| Command | Description |
|---------|-------------|
| `tasklist /v` | Verbose process list |
| `tasklist /svc` | Services per process |
| `tasklist /fi "status eq running"` | Filter |
| `taskkill /PID 1234 /F` | Force kill PID |
| `taskkill /IM notepad.exe /F` | Kill by name |
| `sc query` | List services |
| `sc queryex state=all` | All services |
| `sc start/stop service` | Service control |
| `net start` | Running services |
| `net stop/start service` | Start/stop service |
| `schtasks /query /fo LIST /v` | Scheduled tasks |
| `schtasks /create /tn task /tr prog /sc daily` | Create task |

## User & Management
| Command | Description |
|---------|-------------|
| `whoami` | Current user |
| `whoami /priv` | User privileges |
| `whoami /groups` | Group membership |
| `net user` | List users |
| `net user username /domain` | Domain user info |
| `net localgroup` | List local groups |
| `net localgroup groupname` | Group members |
| `net localgroup groupname user /add` | Add user to group |
| `net accounts` | Password policy |

## File & Text Processing
| Command | Description |
|---------|-------------|
| `find "text" file` | Search string in file |
| `find /i "text" file` | Case-insensitive |
| `findstr /s /i "regex" *.txt` | Regex search |
| `findstr /r "^[0-9]" file` | Lines start with digit |
| `sort file` | Sort lines |
| `sort /+n file` | Sort by column |
| `more file` | Page output |
| `echo %VAR%` | Print variable |
| `set` | Show environment variables |
| `set VAR=value` | Set variable |
| `%USERPROFILE%` | Home directory |
| `%TEMP%` | Temp directory |
| `%PATH%` | Executable search path |

## Batch Scripting
```batch
@echo off
setlocal enabledelayedexpansion
set /p input=Enter: 
if "%input%"=="yes" (echo ok) else (echo no)
for %%f in (*.txt) do echo %%f
for /f "tokens=1 delims=," %%a in (file.csv) do echo %%a
```
