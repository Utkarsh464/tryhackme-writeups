# Tools: Windows Fundamentals Part 2

## MMC Console Snap-ins

| Tool | Command | Purpose |
|------|---------|---------|
| Local Users and Groups Manager | `lusrmgr.msc` | Create and manage local user accounts and groups |
| Local Security Policy | `secpol.msc` | Configure account policies, audit policies, and user rights |
| Registry Editor | `regedit.exe` | View and modify the Windows Registry |
| Group Policy Editor | `gpedit.msc` | Manage local group policy settings (Pro/Enterprise) |
| Computer Management | `compmgmt.msc` | Consolidated management console for multiple tools |

## Networking Tools

| Tool | Command | Purpose |
|------|---------|---------|
| IP Configuration | `ipconfig` | Display and manage IP address configuration |
| Ping | `ping` | Test network connectivity to remote hosts |
| Remote Desktop Connection | `mstsc.exe` | Connect to remote Windows machines via RDP |
| Network Connections | `ncpa.cpl` | View and configure network adapters |
| System Properties | `sysdm.cpl` | View computer name, domain membership, and remote settings |

## Command-Line Tools

| Tool | Purpose |
|------|---------|
| `net user` | Manage user accounts from command line |
| `net localgroup` | Manage local groups from command line |
| `net share` | View and manage shared folders |
| `net use` | Connect to network shared resources |
| `gpupdate` | Refresh Group Policy settings immediately |
| `gpresult` | Display applied Group Policy settings |

## Group Policy Tools

| Tool | Purpose |
|------|---------|
| Local Group Policy Editor | Configure computer and user policies locally |
| Resultant Set of Policy (RSoP) | View combined policy effects |
| Group Policy Modeling | Simulate policy application (domain environment) |

## Security Policy Categories

| Policy Category | Configuration Examples |
|-----------------|----------------------|
| Account Policies | Password complexity, length, age, lockout threshold |
| Audit Policies | Log success/failure for logon, object access, privilege use |
| User Rights Assignment | Who can log on locally, shut down, access from network |
| Security Options | UAC behavior, drive encryption requirements, admin status |
