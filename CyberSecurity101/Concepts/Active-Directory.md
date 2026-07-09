# Active Directory

## Definition
Active Directory (AD) is Microsoft's directory service for Windows domain networks. It provides centralized authentication, authorization, and management for users, computers, groups, and other resources in an enterprise network. AD uses a hierarchical database (the directory) based on LDAP (Lightweight Directory Access Protocol), Kerberos for authentication, and DNS for service discovery.

## Why It Matters
Active Directory is the backbone of most enterprise IT environments. Over 90% of Fortune 1000 companies use AD. In cybersecurity, AD is the crown jewel — compromising a domain controller means controlling the entire network. Understanding AD is essential for penetration testers (attack paths, Kerberos attacks, privilege escalation), incident responders (identifying compromised accounts, lateral movement), and defenders (hardening, monitoring, Group Policy management).

## Where It Appears in the Path
Active Directory is covered in the Windows enterprise security module. It assumes prior knowledge of Windows OS, networking, DNS, and LDAP. AD is a prerequisite for understanding enterprise attack techniques like Kerberoasting, AS-REP roasting, DCSync, pass-the-ticket, and Golden/Silver ticket attacks.

## Prerequisites
- Windows OS fundamentals
- Networking (DNS, ports, authentication)
- LDAP basics helpful

## Core Components

### Domain
The basic administrative unit in AD. A domain is a logical group of objects (users, computers, groups) that share a common directory database, security policies, and trust relationships. Each domain has a unique DNS name (e.g., `corp.tryhackme.com`).

### Domain Controller (DC)
A Windows server that hosts the AD database (NTDS.dit), authenticates users, and responds to LDAP queries. Critical infrastructure — compromise of a DC means compromise of the entire domain. Multiple DCs provide redundancy with multi-master replication.

### Organizational Units (OUs)
Containers within a domain used to organize objects and delegate administration. OUs are hierarchical — an OU can contain child OUs. Group Policy Objects (GPOs) can be linked to OUs to apply settings to users/computers in that OU.

### Trees and Forests
- **Tree**: One or more domains sharing a contiguous DNS namespace (e.g., `uk.corp.com` and `us.corp.com` under `corp.com`).
- **Forest**: Collection of trees sharing a common schema, configuration, and Global Catalog. The forest is the security boundary in AD.

### Trust Relationships
Allow users in one domain to access resources in another domain. Trusts can be one-way or two-way, transitive or non-transitive. Forest trusts connect AD forests.

### Global Catalog
A subset of all objects in a forest, stored on Global Catalog servers. Enables searching across domains without requiring referrals.

### FSMO Roles
Flexible Single Master Operation roles — five special roles that must be held by specific DCs:
- Schema Master (forest-wide)
- Domain Naming Master (forest-wide)
- PDC Emulator (domain-wide — time sync, password changes)
- RID Master (domain-wide — allocates RID pools)
- Infrastructure Master (domain-wide — references objects in other domains)

## Group Policy Objects (GPOs)
GPOs are collections of policy settings applied to users and computers in AD. Linked to sites, domains, or OUs. Settings include security policies, software installation, scripts, desktop configurations. GPOs process in order: Local → Site → Domain → OU (inherited, with Block Inheritance and Enforce options).

## Active Directory Attacks

### Kerberoasting
Request a service ticket (TGS) for a service account, extract the encrypted hash, crack offline. Targets accounts with Service Principal Names (SPNs).

### AS-REP Roasting
Find accounts without Kerberos pre-authentication required, request an AS-REP with encrypted hash, crack offline.

### Golden Ticket
Forge a Kerberos Ticket-Granting Ticket (TGT) using the compromised KRBTGT account hash. Grants domain admin privileges indefinitely.

### Silver Ticket
Forge a service ticket (TGS) to access a specific service. More limited than a golden ticket but harder to detect.

### DCSync
Mimic a domain controller to request account credentials (password hashes) from another DC via MS-DRSR protocol. Requires DA privileges.

### Pass-the-Hash / Pass-the-Ticket
Use extracted password hashes or Kerberos tickets to authenticate without knowing the plaintext password.

### SMB Relay
Relay captured NTLM authentication to other machines in the domain.

## Common Interview Questions
1. **What is Active Directory and what are its main components?** Directory service by Microsoft. Components: domains, domain controllers, OUs, trees, forests, GPOs, trusts, global catalog.
2. **What is the difference between a domain and a forest?** A domain is an administrative unit. A forest is a collection of domains with shared schema and configuration. Forest is the security boundary.
3. **How does Kerberos authentication work in AD?** AS-REQ → AS-REP (TGT) → TGS-REQ → TGS-REP (service ticket) → AP-REQ → AP-REP. Uses tickets and session keys.
4. **What is a Kerberoasting attack?** Request TGS tickets for service accounts, extract TGS-REP hashes (encrypted with service account NTLM hash), crack offline.
5. **What is the difference between a Golden Ticket and a Silver Ticket?** Golden = forged TGT (KRBTGT hash), full domain access. Silver = forged TGS (service account hash), limited to one service.
6. **How do you harden Active Directory?** Enable Advanced Audit Policy, restrict privileged groups, implement LAPS for local admin passwords, enforce smart card/MFA, use Protected Users group, disable RC4 and DES, monitor for golden ticket indicators.

## Further Reading
- [Microsoft Active Directory Documentation](https://learn.microsoft.com/en-us/windows-server/identity/)
- _Active Directory Security_ by Sean Metcalf (ADSecurity.org)
- [Windows Security Log Events (ADSecurity)](https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/)
- BloodHound tool for attack path analysis
- Hack The Box / TryHackMe AD labs
