# PowerShell Cheat Sheet

## Core Cmdlets
| Command | Description |
|---------|-------------|
| `Get-Command` | List all cmdlets |
| `Get-Command *process*` | Search cmdlets |
| `Get-Help cmdlet -Examples` | Show examples |
| `Get-Help cmdlet -Online` | Online docs |
| `Update-Help` | Update help files |
| `Get-Module -ListAvailable` | Installed modules |
| `Import-Module ModuleName` | Import module |

## Aliases
| Alias | Cmdlet |
|-------|--------|
| `ls`, `dir` | `Get-ChildItem` |
| `cd`, `sl` | `Set-Location` |
| `cat`, `type` | `Get-Content` |
| `rm`, `del` | `Remove-Item` |
| `cp`, `copy` | `Copy-Item` |
| `mv`, `move` | `Move-Item` |
| `echo` | `Write-Output` |
| `ps` | `Get-Process` |
| `kill` | `Stop-Process` |
| `sleep` | `Start-Sleep` |
| `sort` | `Sort-Object` |
| `where` | `Where-Object` |
| `select` | `Select-Object` |
| `fl` | `Format-List` |
| `ft` | `Format-Table` |
| `gwmi` | `Get-WmiObject` |
| `curl` | `Invoke-WebRequest` |
| `ni` | `New-Item` |

## File Operations
```powershell
Get-ChildItem -Recurse -Filter *.txt
Get-Content file.txt -Tail 50
Get-Content file.txt -Wait              # Follow like tail -f
Set-Content file.txt -Value "text"
Add-Content file.txt -Value "append"
New-Item -Path dir -ItemType Directory -Force
Remove-Item -Recurse -Force dir
Copy-Item src dst -Recurse
Move-Item src dst
Test-Path file                          # $true/$false
Get-Item file | Select-Object Length,LastWriteTime
```

## Pipeline & Filtering
```powershell
Get-Process | Where-Object {$_.CPU -gt 10}
Get-Process | Sort-Object -Property VM -Descending
Get-Process | Select-Object -First 5 Name,CPU
Get-Process | Format-Table -AutoSize
Get-Service | Where-Object Status -eq "Running"
Get-EventLog -LogName System -Newest 10
Get-ChildItem | Where-Object {$_.Length -gt 1MB}
```

## System & Networking
```powershell
Get-Process -Name "explorer" | Stop-Process
Get-Service -Name "wuauserv" | Start-Service
Get-WmiObject Win32_OperatingSystem
Get-WmiObject Win32_ComputerSystem
Get-WmiObject Win32_NetworkAdapterConfiguration | Where-Object IPEnabled
Get-NetIPAddress                          # IP config
Get-NetTCPConnection | Where-Object State -eq "Listen"
Test-NetConnection host -Port 80
Test-NetConnection host -TraceRoute
Resolve-DnsName domain                    # nslookup
Get-DnsClientCache
Clear-DnsClientCache
Get-NetFirewallRule | Where-Object Enabled -eq "True"
```

## Active Directory (RSAT Tools)
```powershell
# Requires Import-Module ActiveDirectory
Get-ADUser -Filter * -Properties *
Get-ADUser -Identity username -Properties EmailAddress,Department
Get-ADGroup -Identity "Domain Admins" | Get-ADGroupMember
Get-ADComputer -Filter * | Select-Object Name
Get-ADDomain
Set-ADUser username -Department "IT"
New-ADUser -Name "User" -SamAccountName user -Enabled $true
Search-ADAccount -AccountDisabled | Format-Table Name
```

## Execution Policy & Remoting
```powershell
Get-ExecutionPolicy
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
Enter-PSSession -ComputerName target
Invoke-Command -ComputerName target -ScriptBlock { Get-Process }
New-PSSession -ComputerName target
```

## Text & Data Processing
```powershell
Select-String -Path *.txt -Pattern "error"
Select-String -Path C:\Logs\* -Pattern "FAILED"
Get-Content file.csv | ConvertFrom-Csv
Get-Content file.json | ConvertFrom-Json
ConvertTo-Json -InputObject $data
Export-Csv -Path out.csv -NoTypeInformation
Import-Csv -Path data.csv
```

## Variables & Objects
```powershell
$var = "value"                         # Variable
$list = @("a","b","c")                 # Array
$hash = @{key="value"}                 # Hashtable
$obj = [PSCustomObject]@{Name="x";ID=1}
$list | ForEach-Object { $_ }
foreach ($item in $list) { $item }
1..10 | ForEach-Object { $_ * 2 }
```

## One-Liners
```powershell
Get-ChildItem -Recurse -ErrorAction SilentlyContinue
Get-Process | Export-Csv processes.csv -NoTypeInformation
Invoke-WebRequest -Uri http://example.com -OutFile out.html
Get-ChildItem -Recurse *.log | Get-Content -Tail 100
```
