# Commands: Windows Fundamentals Part 3

## MMC Console Commands (Run Dialog)

| Command | Description |
|---------|-------------|
| `wf.msc` | Windows Firewall with Advanced Security |
| `eventvwr.msc` | Event Viewer |
| `mmc` | Microsoft Management Console (empty) |
| `compmgmt.msc` | Computer Management |
| `devmgmt.msc` | Device Manager |
| `diskmgmt.msc` | Disk Management |
| `services.msc` | Services Manager |
| `perfmon.msc` | Performance Monitor |

## PowerShell Cmdlets

| Cmdlet | Description | Example |
|--------|-------------|---------|
| `Get-MpPreference` | View Windows Defender settings | `Get-MpPreference` |
| `Set-MpPreference` | Configure Windows Defender | `Set-MpPreference -DisableRealtimeMonitoring $false` |
| `Start-MpScan` | Start antivirus scan | `Start-MpScan -ScanType QuickScan` |
| `Update-MpSignature` | Update virus definitions | `Update-MpSignature` |
| `Get-NetFirewallRule` | View firewall rules | `Get-NetFirewallRule \| Where-Object Enabled` |
| `New-NetFirewallRule` | Create firewall rule | `New-NetFirewallRule -DisplayName "Block 80" -Direction Inbound -LocalPort 80 -Action Block` |
| `Get-Process` | List running processes | `Get-Process \| Sort-Object CPU -Descending` |
| `Get-Service` | List services | `Get-Service \| Where-Object Status Running` |
| `Get-WinEvent` | Query event logs | `Get-WinEvent -LogName Security -MaxEvents 50` |

## BitLocker Commands

| Command | Description | Example |
|---------|-------------|---------|
| `manage-bde -status` | Check BitLocker status | `manage-bde -status C:` |
| `manage-bde -on` | Enable BitLocker | `manage-bde -on C:` |
| `manage-bde -off` | Disable BitLocker | `manage-bde -off C:` |
| `manage-bde -protectors` | View protection methods | `manage-bde -protectors -get C:` |
| `repair-bde` | Access partially decrypted drive | `repair-bde C: D: -rp 48-char-key` |

## Windows Update

| Command | Description | Example |
|---------|-------------|---------|
| `wuauclt /detectnow` | Force update detection | `wuauclt /detectnow` |
| `usoclient StartScan` | Start update scan (Win10) | `usoclient StartScan` |
| `usoclient StartDownload` | Start update download | `usoclient StartDownload` |
| `usoclient StartInstall` | Start update install | `usoclient StartInstall` |

## Netsh Commands

| Command | Description | Example |
|---------|-------------|---------|
| `netsh advfirewall show allprofiles` | Show firewall state | `netsh advfirewall show allprofiles` |
| `netsh advfirewall set allprofiles state on` | Enable firewall | `netsh advfirewall set allprofiles state on` |
| `netsh advfirewall export` | Export firewall policy | `netsh advfirewall export "C:\backup.wfw"` |
