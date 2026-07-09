# Tools: Active Directory Basics

## Active Directory Management Tools

| Tool | Command | Purpose |
|------|---------|---------|
| Active Directory Users and Computers | `dsa.msc` | Primary tool for managing AD users, groups, computers, and OUs |
| Group Policy Management Console | `gpmc.msc` | Create, edit, and link Group Policy Objects |
| Active Directory Sites and Services | `dssite.msc` | Manage site topology and replication |
| Active Directory Domains and Trusts | `dsdom.msc` | Manage domain and forest trust relationships |
| ADSI Edit | `adsiedit.msc` | Low-level AD object editing and troubleshooting |
| Active Directory Module for PowerShell | `domain.msc` | PowerShell integration for AD management |

## Command-Line Tools

| Command | Purpose |
|---------|---------|
| `net user /domain` | List or manage domain user accounts |
| `net group /domain` | List or manage domain global groups |
| `net localgroup /domain` | List or manage domain local groups |
| `net accounts /domain` | View domain password and lockout policies |
| `net computer /domain` | Add or remove computers from domain |

## PowerShell Active Directory Cmdlets

| Cmdlet | Purpose |
|--------|---------|
| `Get-ADUser` | Retrieve one or more AD user accounts |
| `New-ADUser` | Create a new AD user account |
| `Set-ADUser` | Modify an existing AD user account |
| `Remove-ADUser` | Delete an AD user account |
| `Get-ADGroup` | Retrieve AD group objects |
| `New-ADGroup` | Create a new AD security or distribution group |
| `Add-ADGroupMember` | Add members to an AD group |
| `Remove-ADGroupMember` | Remove members from an AD group |
| `Get-ADComputer` | Retrieve AD computer objects |
| `Get-ADOrganizationalUnit` | Retrieve AD organizational units |
| `Get-ADDomain` | Retrieve domain information |
| `Get-ADGroupMember` | List members of an AD group |

## Group Policy Tools

| Tool/Command | Purpose |
|-------------|---------|
| Group Policy Management Console | Central console for all GPO operations |
| `gpupdate` | Force refresh of Group Policy settings |
| `gpupdate /force` | Force reapplication of all policies |
| `gpresult /r` | Display Resultant Set of Policy summary |
| `gpresult /h report.html` | Generate detailed HTML policy report |

## Related Protocols

| Protocol | Port | Purpose |
|----------|------|---------|
| LDAP | 389 | Directory access protocol (unencrypted) |
| LDAPS | 636 | Directory access protocol (encrypted) |
| Kerberos | 88 | Authentication protocol |
| DNS | 53 | Domain name resolution (critical for AD) |
| SMB | 445 | File sharing and RPC communication |
| Global Catalog | 3268 | Forest-wide directory search |
