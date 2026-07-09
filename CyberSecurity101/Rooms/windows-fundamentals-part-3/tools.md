# Tools: Windows Fundamentals Part 3

## Security Tools

| Tool | Command | Purpose |
|------|---------|---------|
| Windows Security Center | System tray shield icon | Centralized security management interface |
| Windows Defender Antivirus | Part of Security Center | Real-time malware protection and scanning |
| Windows Firewall with Advanced Security | `wf.msc` | Advanced inbound/outbound traffic filtering with IPsec |
| BitLocker Drive Encryption | `manage-bde` | Full disk encryption to protect data at rest |
| Event Viewer | `eventvwr.msc` | System, security, and application log viewer |

## Management Tools

| Tool | Command | Purpose |
|------|---------|---------|
| Microsoft Management Console | `mmc` | Framework for hosting administrative snap-ins |
| Computer Management | `compmgmt.msc` | Consolidated system management |
| Device Manager | `devmgmt.msc` | View and configure hardware devices |
| Disk Management | `diskmgmt.msc` | Manage disk partitions and volumes |
| Services Manager | `services.msc` | Start, stop, and configure Windows services |
| Performance Monitor | `perfmon.msc` | System performance data collection and analysis |

## Diagnostic and Update Tools

| Tool | Command | Purpose |
|------|---------|---------|
| System File Checker | `sfc /scannow` | Verify and repair protected system files |
| Deployment Imaging Servicing | `DISM` | Repair Windows system image |
| Windows Update | Settings > Update & Security | Download and install system updates |
| PowerShell | `powershell.exe` | Advanced command-line shell for administration |

## PowerShell Security Cmdlets

| Cmdlet | Purpose |
|--------|---------|
| `Get-MpPreference` | View Windows Defender configuration |
| `Set-MpPreference` | Modify Windows Defender settings |
| `Start-MpScan` | Initiate antivirus scans |
| `Update-MpSignature` | Update antivirus definitions |
| `Get-NetFirewallRule` | List Windows Firewall rules |
| `New-NetFirewallRule` | Create new firewall rules |
| `Get-WinEvent` | Query Windows event logs |
| `Get-Service` | List and manage Windows services |

## Netsh Firewall Commands

| Command | Purpose |
|---------|---------|
| `netsh advfirewall show allprofiles` | Display firewall status for all profiles |
| `netsh advfirewall set allprofiles state on` | Enable firewall for all profiles |
| `netsh advfirewall export` | Export firewall configuration to file |
| `netsh advfirewall import` | Import firewall configuration from file |
