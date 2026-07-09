# Tasks: Windows Fundamentals Part 2

## Task 1: User Account Control (UAC)

**Purpose:** Understand how UAC protects Windows from unauthorized changes.

**Skills:** Security configuration awareness.

**Theory:** User Account Control (UAC) prompts for administrator approval or credentials before allowing system changes. This prevents malware from making unauthorized modifications. UAC has four notification levels from Always Notify to Never Notify. Standard users are prompted for admin credentials, while admins are prompted for consent.

**Commands:** None

---

## Task 2: Local Users and Groups

**Purpose:** Manage local user accounts and groups on a Windows system.

**Skills:** User administration.

**Theory:** The Local Users and Groups Manager (lusrmgr.msc) allows creation and management of local users and groups. Built-in accounts include Administrator and Guest. Groups like Administrators, Users, Guests, and Remote Desktop Users control permissions. User accounts can be password-protected and disabled.

**Commands:**
- lusrmgr.msc - Local Users and Groups Manager
- net user - Manage users from command line
- net localgroup - Manage groups from command line

---

## Task 3: Windows Security Policies

**Purpose:** Configure security policies using Local Security Policy.

**Skills:** Policy configuration, security hardening.

**Theory:** Local Security Policy (secpol.msc) configures account policies (password requirements, lockout thresholds), audit policies (logging successful/failed events), user rights assignments (who can log on locally, shut down), and security options. These policies enforce security baselines on local machines.

**Commands:**
- secpol.msc - Local Security Policy
- gpupdate - Refresh Group Policy settings
- gpresult - Display Resultant Set of Policy

---

## Task 4: Windows Registry

**Purpose:** Understand the structure and purpose of the Windows Registry.

**Skills:** Registry navigation, configuration management.

**Theory:** The Registry is a hierarchical database storing OS and application settings. It has five root keys: HKEY_CLASSES_ROOT, HKEY_CURRENT_USER, HKEY_LOCAL_MACHINE, HKEY_USERS, and HKEY_CURRENT_CONFIG. Incorrect modifications can break the system, so caution is essential. Registry Editor (regedit) is used for navigation and editing.

**Commands:**
- regedit - Registry Editor
- reg - Registry console tool

---

## Task 5: Networking and Remote Access

**Purpose:** Configure Windows networking and use Remote Desktop.

**Skills:** Network configuration, remote administration.

**Theory:** Windows networking includes TCP/IP configuration, network discovery, file and printer sharing, and Remote Desktop Protocol (RDP). Network settings are configured through the Network and Sharing Center or Settings app. RDP allows remote graphical access to Windows systems and is commonly used for administration.

**Commands:**
- ipconfig - IP configuration
- ping - Test connectivity
- net share - Manage shared folders
- mstsc - Remote Desktop Connection
