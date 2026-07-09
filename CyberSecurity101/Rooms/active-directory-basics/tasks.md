# Tasks: Active Directory Basics

## Task 1: Introduction to Active Directory

**Purpose:** Understand what Active Directory is and why it is used.

**Skills:** Conceptual understanding of directory services.

**Theory:** Active Directory (AD) is Microsoft's directory service for Windows domain networks. It stores information about users, computers, groups, and other network resources and provides authentication and authorization services. AD enables centralized management of users and resources across an organization. It uses LDAP, Kerberos, and DNS as underlying protocols.

**Commands:** None

---

## Task 2: Domains and Domain Controllers

**Purpose:** Learn about Active Directory domains and domain controllers.

**Skills:** Domain architecture understanding.

**Theory:** A domain is an administrative boundary in AD. A domain controller (DC) is a server that authenticates users and stores the AD database. Domains have a DNS name (example.com) and a NetBIOS name (EXAMPLE). Multiple domain controllers provide redundancy. The Active Directory database is stored in NTDS.dit.

**Commands:** None

---

## Task 3: Organizational Units and Groups

**Purpose:** Manage AD objects using organizational units and security groups.

**Skills:** Object management, group strategy.

**Theory:** Organizational Units (OUs) are containers used to organize AD objects (users, computers, groups) for administrative purposes. OUs enable delegation of administration and Group Policy application. Security groups are used to assign permissions to resources. Groups have scope types: Domain Local, Global, and Universal.

**Commands:**
- dsa.msc - Active Directory Users and Computers
- net group - Manage groups
- net user - Manage users

---

## Task 4: Group Policy

**Purpose:** Understand Group Policy and its role in managing Windows systems.

**Skills:** Policy management, configuration enforcement.

**Theory:** Group Policy manages operating system settings, application configurations, and security settings for users and computers. Group Policy Objects (GPOs) are linked to domains, OUs, or sites. Settings include password policies, software installation, folder redirection, script execution, and security restrictions. gpupdate refreshes policy settings.

**Commands:**
- gpmc.msc - Group Policy Management Console
- gpupdate - Refresh Group Policy
- gpresult - Display applied policies

---

## Task 5: Authentication Protocols

**Purpose:** Understand Kerberos and NTLM authentication in Active Directory.

**Skills:** Authentication protocol awareness.

**Theory:** Kerberos is the default AD authentication protocol, using tickets for secure authentication. NTLM is a legacy challenge-response protocol. Kerberos uses a Key Distribution Center (KDC) on domain controllers. Understanding these protocols is essential for recognizing attacks like Kerberoasting, pass-the-hash, and golden ticket attacks.

**Commands:** None
