# Commands: Windows PowerShell

## Core Cmdlets

| Cmdlet | Alias | Description | Example |
|--------|-------|-------------|---------|
| `Get-Command` | `gcm` | List available commands | `Get-Command -Verb Get` |
| `Get-Help` | `help` | Display cmdlet help | `Get-Help Get-Process -Detailed` |
| `Get-Verb` | - | List approved verbs | `Get-Verb` |
| `Get-Member` | `gm` | Examine object members | `Get-Process \| Get-Member` |
| `Get-Date` | - | Get current date/time | `Get-Date` |
| `Get-Location` | `gl` | Display current path | `Get-Location` |

## Filesystem and Registry Providers

| Cmdlet | Alias | Description | Example |
|--------|-------|-------------|---------|
| `Get-ChildItem` | `ls`, `dir` | List items in location | `Get-ChildItem C:\Windows` |
| `Set-Location` | `cd`, `sl` | Change directory | `Set-Location C:\Users` |
| `Get-Content` | `cat`, `gc`, `type` | Read file content | `Get-Content C:\log.txt` |
| `Set-Content` | `sc` | Write file content | `Set-Content file.txt "Hello"` |
| `Add-Content` | `ac` | Append to file | `Add-Content log.txt "New entry"` |
| `Remove-Item` | `del`, `rm`, `ri` | Delete files | `Remove-Item C:\temp\*.tmp` |
| `New-Item` | `ni` | Create file or directory | `New-Item -ItemType Directory C:\New` |
| `Copy-Item` | `cp`, `copy`, `ci` | Copy items | `Copy-Item C:\src\* C:\dst\` |
| `Move-Item` | `mv`, `move`, `mi` | Move items | `Move-Item C:\src\file.txt C:\dst\` |
| `Rename-Item` | `ren`, `rni` | Rename item | `Rename-Item old.txt new.txt` |
| `Set-Location HKLM:\` | `cd HKLM:\` | Navigate registry | `Set-Location HKLM:\Software` |

## Process and Service Management

| Cmdlet | Alias | Description | Example |
|--------|-------|-------------|---------|
| `Get-Process` | `ps`, `gps` | List processes | `Get-Process -Name chrome` |
| `Stop-Process` | `kill`, `spps` | Terminate process | `Stop-Process -Name notepad -Force` |
| `Start-Process` | `saps` | Start a process | `Start-Process notepad` |
| `Get-Service` | `gsv` | List services | `Get-Service \| Where-Object Status -eq Running` |
| `Start-Service` | `sasv` | Start a service | `Start-Service Spooler` |
| `Stop-Service` | `spsv` | Stop a service | `Stop-Service Spooler` |
| `Restart-Service` | - | Restart a service | `Restart-Service Spooler` |
| `Set-Service` | - | Configure service | `Set-Service Spooler -StartupType Automatic` |
| `Get-EventLog` | - | Get event log entries | `Get-EventLog -LogName System -Newest 50` |

## Object Manipulation

| Cmdlet | Alias | Description | Example |
|--------|-------|-------------|---------|
| `Select-Object` | `select` | Select properties | `Get-Process \| Select-Object Name, CPU` |
| `Where-Object` | `where`, `?` | Filter objects | `Get-Service \| Where-Object {$_.Status -eq "Running"}` |
| `Sort-Object` | `sort` | Sort objects | `Get-Process \| Sort-Object CPU -Descending` |
| `Group-Object` | `group` | Group objects | `Get-Process \| Group-Object Company` |
| `Measure-Object` | `measure` | Calculate statistics | `Get-Process \| Measure-Object WorkingSet -Average` |
| `ForEach-Object` | `foreach`, `%` | Process each object | `1..10 \| ForEach-Object { $_ * 2 }` |

## Formatting and Output

| Cmdlet | Alias | Description | Example |
|--------|-------|-------------|---------|
| `Format-Table` | `ft` | Table format output | `Get-Process \| Format-Table -AutoSize` |
| `Format-List` | `fl` | List format output | `Get-Process \| Format-List *` |
| `Format-Wide` | `fw` | Wide format output | `Get-Command \| Format-Wide -Column 4` |
| `Out-File` | - | Send output to file | `Get-Process \| Out-File processes.txt` |
| `Export-Csv` | - | Export to CSV | `Get-Process \| Export-Csv processes.csv` |
| `ConvertTo-Json` | - | Convert to JSON | `Get-Process \| ConvertTo-Json` |
| `ConvertFrom-Json` | - | Convert from JSON | `$json \| ConvertFrom-Json` |

## Remoting and Execution

| Cmdlet | Alias | Description | Example |
|--------|-------|-------------|---------|
| `Invoke-Command` | `icm` | Run commands remotely | `Invoke-Command -ComputerName SRV01 -ScriptBlock { Get-Process }` |
| `Enter-PSSession` | `etsn` | Start interactive remote session | `Enter-PSSession -ComputerName SRV01` |
| `Exit-PSSession` | `exsn` | End remote session | `Exit-PSSession` |
| `Get-ExecutionPolicy` | - | View execution policy | `Get-ExecutionPolicy` |
| `Set-ExecutionPolicy` | - | Set execution policy | `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser` |
