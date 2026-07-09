# Commands: Active Directory Basics

## MMC Console Commands (Run Dialog)

| Command | Description |
|---------|-------------|
| `dsa.msc` | Active Directory Users and Computers (ADUC) |
| `gpmc.msc` | Group Policy Management Console |
| `dssite.msc` | Active Directory Sites and Services |
| `dsdom.msc` | Active Directory Domains and Trusts |
| `adsiedit.msc` | ADSI Edit (advanced AD editor) |
| `domain.msc` | Active Directory Module for Windows PowerShell |
| `netdom.msc` | Domain Management snap-in |

## Command Prompt (Net Commands)

| Command | Description | Example |
|---------|-------------|---------|
| `net user /domain` | List domain users | `net user /domain` |
| `net user username /domain` | View domain user details | `net user bob /domain` |
| `net group /domain` | List domain groups | `net group /domain` |
| `net group "Domain Admins" /domain` | View group members | `net group "Domain Admins" /domain` |
| `net accounts /domain` | View domain password policy | `net accounts /domain` |

## PowerShell Cmdlets (Active Directory Module)

| Cmdlet | Description | Example |
|--------|-------------|---------|
| `Get-ADUser` | Get AD user objects | `Get-ADUser -Identity bob` |
| `Get-ADGroup` | Get AD group objects | `Get-ADGroup -Identity "Domain Admins"` |
| `Get-ADComputer` | Get AD computer objects | `Get-ADComputer -Filter *` |
| `Get-ADOrganizationalUnit` | Get AD OUs | `Get-ADOrganizationalUnit -Filter *` |
| `New-ADUser` | Create new AD user | `New-ADUser -Name "Bob Smith" -SamAccountName bob` |
| `Add-ADGroupMember` | Add user to group | `Add-ADGroupMember "Domain Admins" bob` |
| `Get-ADDomain` | Get domain information | `Get-ADDomain` |
| `Get-ADGroupMember` | List group members | `Get-ADGroupMember "Domain Admins"` |

## Group Policy Commands

| Command | Description | Example |
|---------|-------------|---------|
| `gpupdate /target:computer` | Refresh computer policy | `gpupdate /target:computer` |
| `gpupdate /target:user` | Refresh user policy | `gpupdate /target:user` |
| `gpresult /h report.html` | Generate policy report | `gpresult /h policy.html` |
| `gpresult /r` | Display RSoP summary | `gpresult /r` |
