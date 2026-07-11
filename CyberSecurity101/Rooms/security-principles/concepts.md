# Security Principles — Concepts

## CIA Triad
The three core objectives of information security. Confidentiality ensures data is accessible only to authorized individuals, typically enforced through encryption and access controls. Integrity guarantees data has not been tampered with, maintained through hashing and digital signatures. Availability ensures systems and data are accessible when needed, supported by redundancy, backup, and disaster recovery planning.

## Authentication, Authorization, and Accounting (AAA)
A framework for controlling access to resources. Authentication verifies a user's identity through factors such as passwords (something you know), tokens (something you have), and biometrics (something you are). Authorization determines what an authenticated user is permitted to do, often managed through role-based access control (RBAC). Accounting tracks user activities for auditing and billing purposes.

## Defense in Depth
A security strategy that deploys multiple layers of defense so that if one layer is breached, subsequent layers still provide protection. Layers include physical security, network security (firewalls, IDS/IPS), endpoint security (antivirus, EDR), application security (input validation, WAF), data security (encryption, DLP), and administrative controls (policies, training).

## Least Privilege
The principle that users, processes, and systems should be granted only the minimum permissions necessary to perform their functions. Applying least privilege reduces the attack surface and limits the damage from compromised accounts. Implementation includes using regular user accounts instead of admin accounts, applying file permissions strictly, and using just-in-time privilege elevation.

## Risk Management
The process of identifying, assessing, and prioritizing risks followed by coordinated application of resources to minimize their impact. Key components include asset identification, threat assessment, vulnerability analysis, risk evaluation (likelihood x impact), control selection, and continuous monitoring. Common frameworks include NIST RMF and ISO 31000.

## Security Frameworks
Structured approaches to building and managing security programs. The NIST Cybersecurity Framework organizes security into five functions: Identify, Protect, Detect, Respond, Recover. ISO 27001 provides requirements for an Information Security Management System (ISMS). These frameworks help organizations establish, implement, and improve security practices.
