# Tools: Windows PowerShell

## Primary Tool

| Tool | Location | Purpose |
|------|----------|---------|
| Windows PowerShell | C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe | Object-oriented shell and scripting environment |
| PowerShell Core (pwsh.exe) | Cross-platform | Modern, cross-platform PowerShell version 7+ |

## Core Cmdlets by Category

### Discovery and Help
| Cmdlet | Purpose |
|--------|---------|
| `Get-Command` | Discover all available cmdlets, functions, and aliases |
| `Get-Help` | Display detailed help for cmdlets and concepts |
| `Get-Verb` | List approved PowerShell verbs |
| `Get-Member` | Examine properties and methods of objects |
| `Get-PSDrive` | List available PowerShell drives (providers) |
| `Get-PSProvider` | List available PowerShell providers |

### Filesystem and Provider Navigation
| Cmdlet | Purpose |
|--------|---------|
| `Get-ChildItem` | List items in a location (like dir/ls) |
| `Set-Location` | Change to a different location (like cd) |
| `Get-Location` | Display current location (like pwd) |
| `Get-Content` | Read content from a file |
| `Set-Content` | Write content to a file |
| `Add-Content` | Append content to a file |
| `New-Item` | Create files, directories, or registry keys |
| `Remove-Item` | Delete files, directories, or registry keys |
| `Copy-Item` | Copy items from one location to another |
| `Move-Item` | Move items to a new location |
| `Rename-Item` | Rename an item |

### Process and Service Management
| Cmdlet | Purpose |
|--------|---------|
| `Get-Process` | Retrieve running processes |
| `Stop-Process` | Terminate a running process |
| `Start-Process` | Launch a new process |
| `Get-Service` | Retrieve Windows services |
| `Start-Service` | Start a stopped service |
| `Stop-Service` | Stop a running service |
| `Restart-Service` | Stop and restart a service |
| `Set-Service` | Modify service properties |

### Object Manipulation
| Cmdlet | Purpose |
|--------|---------|
| `Select-Object` | Select specific properties of objects |
| `Where-Object` | Filter objects based on conditions |
| `Sort-Object` | Sort objects by property values |
| `Group-Object` | Group objects by property values |
| `Measure-Object` | Calculate statistical properties |
| `ForEach-Object` | Perform operations on each item in a collection |

### Output and Formatting
| Cmdlet | Purpose |
|--------|---------|
| `Format-Table` | Format output as a table |
| `Format-List` | Format output as a property list |
| `Format-Wide` | Format output as a wide list |
| `Out-File` | Send output to a text file |
| `Export-Csv` | Export objects to comma-separated values |
| `ConvertTo-Json` | Convert objects to JSON format |
| `ConvertFrom-Json` | Convert JSON to PowerShell objects |
| `ConvertTo-Html` | Convert objects to HTML |

### Remoting
| Cmdlet | Purpose |
|--------|---------|
| `Invoke-Command` | Run commands on local or remote systems |
| `Enter-PSSession` | Start an interactive remote PowerShell session |
| `Exit-PSSession` | End an interactive remote session |
| `New-PSSession` | Create a persistent remote session |
| `Remove-PSSession` | Close and remove remote sessions |
| `Test-WSMan` | Test WinRM connectivity to a remote host |

### Security and Execution
| Cmdlet | Purpose |
|--------|---------|
| `Get-ExecutionPolicy` | Display current script execution policy |
| `Set-ExecutionPolicy` | Change script execution policy |
| `Get-AuthenticodeSignature` | Retrieve digital signature from a file |
| `Set-AuthenticodeSignature` | Add digital signature to a script |

## Related Technologies

| Technology | Purpose |
|------------|---------|
| PowerShell ISE | Integrated scripting environment (legacy) |
| Visual Studio Code | Modern editor with PowerShell extension |
| PowerShell Gallery | Online repository for PowerShell modules |
| Windows Remote Management (WinRM) | Remoting protocol underlying PowerShell remoting |
