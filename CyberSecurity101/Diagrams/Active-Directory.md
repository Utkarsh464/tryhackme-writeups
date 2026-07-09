# Active Directory — Domain Controller, Users, Groups, OUs, GPOs, Trusts

```mermaid
graph TB
    subgraph Forest["AD Forest — company.local"]
        subgraph DomainA["Domain A: corp.company.local"]
            DC1["Domain Controller<br/>(DC1.corp.company.local)"]

            subgraph OUs["Organizational Units"]
                OU1["OU: Corporate Users"]
                OU2["OU: Servers"]
                OU3["OU: Workstations"]
                OU4["OU: Admins"]
            end

            subgraph Users["Users & Groups"]
                U1["User: jdoe<br/>(Domain User)"]
                U2["User: asmith<br/>(Domain User)"]
                G1["Group: Domain Admins"]
                G2["Group: Domain Users"]
                G3["Group: Enterprise Admins"]
            end

            subgraph GPOs["Group Policy Objects"]
                GPO1["GPO: Password Policy<br/>(complexity, length, expiry)"]
                GPO2["GPO: Software Restriction"]
                GPO3["GPO: Audit Policy"]
                GPO4["GPO: Windows Firewall Rules"]
            end

            subgraph Computers["Computer Objects"]
                C1["Workstation: WS-001<br/>(Windows 11)"]
                C2["Workstation: WS-002"]
                S1["Server: SQL-01"]
                S2["Server: WEB-01"]
            end
        end

        subgraph DomainB["Domain B: dev.company.local"]
            DC2["Domain Controller<br/>(DC2.dev.company.local)"]
            OU5["OU: Developers"]
            U3["User: bwhite<br/>(Developer)"]
        end
    end

    DC1 -->|Replication| DC2
    DomainA -->|Two-Way Trust| DomainB
    OU1 --> U1
    OU1 --> U2
    OU4 --> G1
    G1 --> U1
    GPO1 --> OU1
    GPO2 --> OU3
    GPO3 --> DC1
    C1 --> OU3
    S1 --> OU2
```

Active Directory (AD) is Microsoft's directory service for Windows domain networks, providing centralized authentication, authorization, and management. **Domain Controller (DC)**: The DC is a server running Active Directory Domain Services (AD DS) that authenticates users, stores directory data, and replicates changes to other DCs. Every AD domain requires at least one DC. **Organizational Units (OUs)**: OUs are containers within a domain that organize users, groups, and computers into a logical hierarchy. They are the smallest scope for applying Group Policy and delegating administrative control. **Users and Groups**: User objects represent people or service accounts. Security groups (Domain Admins, Domain Users, Enterprise Admins) simplify permission assignment. Domain Admins have full control over the domain, while Enterprise Admins extend that across the entire forest. **Group Policy Objects (GPOs)**: GPOs are collections of policy settings applied to OUs, sites, or domains. They enforce security baselines like password complexity, account lockout, software restrictions, and audit policies. GPOs are processed in a specific order: Local, Site, Domain, OU (LSDOU), with later policies overriding earlier ones. **Trust Relationships**: Trusts allow users in one domain to access resources in another. A two-way transitive trust is automatically created between domains in the same forest. External trusts, forest trusts, and shortcut trusts provide cross-forest or cross-domain access. AD relies on Kerberos for authentication, LDAP for directory queries, and DNS for service location.
