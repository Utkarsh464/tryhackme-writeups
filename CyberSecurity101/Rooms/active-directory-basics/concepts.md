# Concepts: Active Directory Basics

## 1. Active Directory (AD)
Microsoft's directory service for Windows domain networks, providing centralized authentication, authorization, and management of network resources. AD stores information about users, computers, groups, printers, and other network objects in a hierarchical database. It is the foundation of identity management in most enterprise Windows environments.

## 2. Domain
An administrative boundary in Active Directory that defines a group of computers, users, and resources that share a common directory database and security policies. Domains have a DNS name (example.com) and a NetBIOS name (EXAMPLE). All domain members trust the domain controllers for authentication.

## 3. Domain Controller (DC)
A Windows Server that hosts Active Directory Domain Services and authenticates domain users and computers. Domain controllers store the Active Directory database (NTDS.dit). Multiple domain controllers provide redundancy and load balancing. Changes can be made on any DC and replicate to others.

## 4. Organizational Unit (OU)
A container object in Active Directory used to organize users, groups, computers, and other objects into a hierarchical structure. OUs enable delegation of administrative control and targeted application of Group Policy. OUs are the smallest scope for applying Group Policy.

## 5. Security Group
A collection of user accounts, computer accounts, or other groups that can be assigned permissions to resources. Security group scope types include Domain Local (permissions on local resources), Global (group accounts within a domain), and Universal (groups from any domain in the forest).

## 6. Group Policy Object (GPO)
A collection of policy settings that define how systems and users should behave in an Active Directory environment. GPOs are linked to domains, OUs, or sites and contain computer configuration settings (OS policies, security settings, software installation) and user configuration settings (desktop settings, folder redirection, scripts).

## 7. Kerberos Authentication
The default authentication protocol in Active Directory, providing secure authentication using tickets. Kerberos uses a Key Distribution Center (KDC) on domain controllers to issue Ticket Granting Tickets (TGTs) and Service Tickets. It provides mutual authentication and protects against eavesdropping and replay attacks.

## 8. NTLM Authentication
A legacy challenge-response authentication protocol used by Windows for backward compatibility. NTLM has security weaknesses compared to Kerberos, including vulnerability to pass-the-hash attacks and relay attacks. Its use is discouraged in modern environments.

## 9. Lightweight Directory Access Protocol (LDAP)
An open, vendor-neutral protocol for accessing and maintaining directory services. Active Directory supports LDAP for querying and modifying the directory database. LDAP is used by applications and tools to authenticate users and retrieve directory information.

## 10. Trust Relationship
A relationship between domains or forests that allows users in one domain to access resources in another domain. Trusts can be one-way or two-way, transitive or non-transitive. Trust relationships enable resource sharing across organizational boundaries while maintaining security.

## 11. NTDS.dit
The Active Directory database file stored on domain controllers at %SystemRoot%\NTDS\NTDS.dit. This file contains all Active Directory objects including users, groups, computers, and their attributes. Protecting this file is critical for AD security.

## 12. Common AD Attack Vectors
Active Directory is frequently targeted by attackers using techniques such as Kerberoasting (requesting service tickets for cracking), AS-REP roasting (finding users without pre-authentication), pass-the-hash (using NTLM hashes for authentication), DCSync (replicating credentials from DCs), and golden ticket attacks (forging Kerberos tickets).
