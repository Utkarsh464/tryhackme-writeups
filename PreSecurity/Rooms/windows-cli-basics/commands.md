# Commands: Windows CLI Basics

## CMD — Filesystem

| Command | Description |
|---------|-------------|
| `dir /s` | List files recursively |
| `dir /a` | List files including hidden/system |
| `cd /d D:\` | Change to a different drive |
| `copy source dest` | Copy file to destination |
| `move source dest` | Move/rename a file |
| `del file` | Delete a file |
| `mkdir path` | Create a directory |
| `rmdir /s path` | Remove a directory and contents |
| `attrib +h file` | Set hidden attribute on a file |
| `type file.txt` | Display contents of text file |

## CMD — Network

| Command | Description |
|---------|-------------|
| `ipconfig /all` | Show full network configuration |
| `netstat -an` | Show all active connections and listening ports |
| `netstat -anb` | Show connections with process name (admin) |
| `ping -n 4 8.8.8.8` | Send 4 ICMP echo requests |
| `tracert target` | Trace route to destination |
| `nslookup domain.com` | Query DNS for domain |
| `route print` | Display the IP routing table |

## CMD — System and Process

| Command | Description |
|---------|-------------|
| `systeminfo` | Display system configuration |
| `tasklist /v` | List processes with verbose info |
| `taskkill /PID 1234 /F` | Force kill a process |
| `wmic useraccount list brief` | List user accounts |
| `wmic process list brief` | List running processes |
| `wmic product get name,version` | List installed software |
| `driverquery` | List installed device drivers |

## PowerShell — Basics

| Command | Description |
|---------|-------------|
| `Get-Command` | List all available cmdlets |
| `Get-Command *process*` | Find cmdlets related to processes |
| `Get-Help Get-Process -Examples` | Show usage examples for a cmdlet |
| `Get-Process` | List all running processes |
| `Get-Service` | List all services and their status |

## PowerShell — Pipeline and Filtering

| Command | Description |
|---------|-------------|
| `Get-Process | Where-Object {$_.CPU -gt 10}` | Filter processes by CPU usage |
| `Get-Service | Where-Object {$_.Status -eq "Running"}` | Filter to running services |
| `Get-Process | Select-Object Name, CPU, WorkingSet` | Select specific properties |
| `Get-Process | Sort-Object CPU -Descending | Select-Object -First 5` | Top 5 CPU-consuming processes |
| `Get-Process | Export-CSV processes.csv` | Export process list to CSV |
| `Get-Service | ConvertTo-HTML > services.html` | Export services list to HTML |