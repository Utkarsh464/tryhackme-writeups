# Concepts: Windows CLI Basics

## 1. Command Prompt (CMD)
The legacy Windows command-line interpreter. CMD executes batch commands and scripts (.bat/.cmd). It outputs text (not objects), making parsing harder. Despite being superseded by PowerShell for many tasks, CMD remains useful for quick operations and environments where PowerShell is restricted.

## 2. ipconfig and Network Diagnostics
`ipconfig /all` shows IP, subnet mask, gateway, DNS servers, and DHCP info. `ping` tests reachability via ICMP. `tracert` maps the routing path. `netstat -anb` identifies listening services and active connections — essential for identifying backdoors.

## 3. systeminfo
Displays OS name, version, build, install date, manufacturer, CPU, RAM, hotfixes, and network config. Invaluable during reconnaissance to assess the patch level and hardware of a Windows target.

## 4. WMIC
WMIC provides a CLI to WMI. It can list users, processes, installed software, services, and disks. `wmic /node:target process list brief` queries remote systems. WMIC is deprecated in newer Windows versions, replaced by PowerShell WMI cmdlets.

## 5. PowerShell Cmdlets
PowerShell uses verb-noun naming (Get-Process, Set-Service). Cmdlets return .NET objects with typed properties. `Get-Command` lists available cmdlets — discovery is built into the shell itself.

## 6. PowerShell Pipeline
The pipeline (`|`) passes objects between cmdlets. This allows filtering with `Where-Object`, property selection with `Select-Object`, sorting with `Sort-Object`, and exporting with `Export-CSV`. This is the most powerful PowerShell feature.

## 7. Select-Object and Where-Object
`Where-Object` filters by condition: `Where-Object {$_.Status -eq 'Running'}`. `Select-Object` picks properties or limits objects: `Select-Object -First 10 Name, CPU`. These two cmdlets are the backbone of PowerShell queries.

## 8. Exporting and Formatting Output
PowerShell supports Export-CSV, ConvertTo-JSON, ConvertTo-HTML, and Export-CliXML. Formatting cmdlets (Format-Table, Format-List) control console display. Out-GridView presents interactive tables for analysis.