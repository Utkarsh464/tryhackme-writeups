# Commands: Windows Fundamentals Part 2

## MMC Console Commands (Run Dialog - Win+R)

| Command | Description |
|---------|-------------|
| `lusrmgr.msc` | Local Users and Groups Manager |
| `secpol.msc` | Local Security Policy Editor |
| `regedit` | Registry Editor |
| `regedt32` | Registry Editor (alternative) |
| `gpedit.msc` | Group Policy Editor (Professional/Enterprise) |
| `control` | Control Panel |
| `ncpa.cpl` | Network Connections |
| `sysdm.cpl` | System Properties |
| `ms-settings:` | Settings app (Windows 10/11) |

## Command Prompt (Networking)

| Command | Description | Example |
|---------|-------------|---------|
| `ipconfig` | Display IP configuration | `ipconfig /all` |
| `ipconfig /release` | Release DHCP lease | `ipconfig /release` |
| `ipconfig /renew` | Renew DHCP lease | `ipconfig /renew` |
| `ipconfig /flushdns` | Clear DNS cache | `ipconfig /flushdns` |
| `ping` | Test network connectivity | `ping 8.8.8.8` |
| `mstsc` | Remote Desktop Connection | `mstsc /v:192.168.1.100` |
| `net share` | Manage shared folders | `net share` |
| `net use` | Connect to network shares | `net use Z: \\server\share` |
| `net view` | View network resources | `net view` |

## User Management (Command Prompt)

| Command | Description | Example |
|---------|-------------|---------|
| `net user` | List or manage users | `net user username` |
| `net user username * /add` | Create new user | `net user bob * /add` |
| `net user username /delete` | Delete user | `net user bob /delete` |
| `net localgroup` | List or manage groups | `net localgroup Administrators` |

## Group Policy Commands

| Command | Description | Example |
|---------|-------------|---------|
| `gpupdate` | Refresh Group Policy | `gpupdate /force` |
| `gpresult` | Display Resultant Set of Policy | `gpresult /r` |
