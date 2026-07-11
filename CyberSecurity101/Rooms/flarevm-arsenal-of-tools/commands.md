# FlareVM: Arsenal of Tools — Commands

FlareVM is primarily a GUI-based environment, but the following PowerShell and command-line utilities are commonly used:

| Command | Description |
|---------|-------------|
| `Set-ExecutionPolicy Unrestricted -Force` | Bypass PowerShell execution policy for scripts |
| `Get-Process` | List running processes (PowerShell) |
| `Get-Service` | List Windows services (PowerShell) |
| `netstat -ano` | Display active network connections and listening ports |
| `tasklist` | List running processes (CMD) |
| `taskkill /PID <pid> /F` | Force-kill a process by PID |
| `reg export HKLM\Software\Microsoft\Windows\CurrentVersion\Run run.reg` | Export registry keys to a file |
| `reg query HKLM\Software\Microsoft\Windows\CurrentVersion\Run` | Query registry Run keys |
| `certutil -hashfile sample.exe MD5` | Compute MD5 hash of a file |
| `certutil -hashfile sample.exe SHA256` | Compute SHA256 hash of a file |
| `fls -r -m C: image.dd > body.txt` | List files from a disk image (Sleuth Kit) |
| `iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/mandiant/flare-vm/main/install.ps1'))` | Install FlareVM via PowerShell |

Additional GUI tools launched from FlareVM shortcuts or command line:

| Command | Tool |
|---------|------|
| `x64dbg` | x64dbg debugger |
| `procmon` | Process Monitor |
| `procexp` | Process Explorer |
| `HxD` | HxD hex editor |
| `die` | Detect It Easy |
| `pe-bear` | PE-bear PE analysis tool |
| `regshot` | RegShot registry comparison tool |
| `dnSpy` | dnSpy .NET debugger |
