# General Security Interview Questions

## 1. What is the CIA triad?
**Answer:** The CIA triad is the foundational model in information security consisting of Confidentiality (ensuring data is accessible only to authorized parties), Integrity (ensuring data is accurate and unmodified), and Availability (ensuring systems and data are accessible when needed). Every security control aims to protect one or more of these principles.

## 2. What is defense in depth?
**Answer:** Defense in depth is a security strategy that layers multiple independent controls across different parts of a system so that if one control fails, others still provide protection. Examples include combining firewalls, intrusion detection, endpoint protection, access controls, and encryption so no single point of failure compromises the entire system.

## 3. Explain risk management in cybersecurity.
**Answer:** Risk management is the process of identifying, assessing, and prioritizing risks, then applying resources to minimize their impact. The four strategies are: Risk Avoidance (eliminating the activity), Risk Mitigation (reducing likelihood/impact), Risk Transfer (insurance or outsourcing), and Risk Acceptance (acknowledging and monitoring). Frameworks like NIST RMF guide this process.

## 4. What is the difference between a threat, a vulnerability, and a risk?
**Answer:** A threat is a potential danger or attacker that could cause harm (e.g., a hacker). A vulnerability is a weakness that can be exploited (e.g., unpatched software). A risk is the potential for loss when a threat exploits a vulnerability, often expressed as Risk = Threat × Vulnerability × Impact.

## 5. What are the different types of security controls?
**Answer:** Security controls are categorized as: Administrative (policies, training, background checks), Technical (firewalls, encryption, access control lists, IDS/IPS), and Physical (locks, guards, biometrics, CCTV). They can also be classified by function: Preventive (stops incidents), Detective (identifies incidents), Corrective (remedies incidents), and Deterrent (discourages attackers).

## 6. What is the principle of least privilege?
**Answer:** The principle of least privilege means users and processes should be granted only the minimum permissions necessary to perform their job functions. This limits the potential damage from accidents, errors, or compromise. Implementation includes role-based access control (RBAC), regular permission audits, and just-in-time privilege elevation.

## 7. Walk me through the incident response process.
**Answer:** The incident response process follows six phases: Preparation (tools, playbooks, training), Detection & Analysis (identifying and verifying the incident), Containment (short-term and long-term to stop spread), Eradication (removing the threat), Recovery (restoring systems to normal operation), and Lessons Learned (documenting findings and improving processes). Frameworks like NIST SP 800-61 and SANS PICERL guide this process.

## 8. What is the difference between authentication and authorization?
**Answer:** Authentication verifies who a user is (e.g., password, biometric, MFA) — answering "Are you who you say you are?" Authorization determines what an authenticated user is allowed to do (e.g., read, write, delete) — answering "What are you allowed to access?" Authentication always precedes authorization.

## 9. Describe the NIST Cybersecurity Framework.
**Answer:** The NIST Cybersecurity Framework (CSF) consists of five core functions: Identify (understand assets and risks), Protect (implement safeguards), Detect (monitor for incidents), Respond (take action on incidents), and Recover (restore capabilities). It provides a risk-based approach for organizations to improve their cybersecurity posture using implementation tiers and profiles.

## 10. What is ISO 27001?
**Answer:** ISO 27001 is an international standard for Information Security Management Systems (ISMS). It specifies requirements for establishing, implementing, maintaining, and continually improving an ISMS. Organizations certify against this standard to demonstrate they follow best practices for managing information security risks, including risk assessment, security controls (Annex A), and continuous improvement.

## 11. What is the difference between red team and blue team?
**Answer:** The red team simulates real-world attackers by attempting to breach defenses (offensive security). The blue team defends against attacks by monitoring, detecting, and responding to incidents (defensive security). A purple team integrates both by having red and blue teams work together to share insights and improve overall security posture.

## 12. What is the Zero Trust model?
**Answer:** Zero Trust is a security model based on "never trust, always verify." It assumes no user, device, or network is inherently trustworthy, even if inside the corporate perimeter. Key principles include: continuous authentication, micro-segmentation, least-privilege access, and assuming breach. It replaces the traditional castle-and-moat model.

## 13. What is a SIEM and how does it work?
**Answer:** A Security Information and Event Management (SIEM) system aggregates log data from across an organization's infrastructure (servers, firewalls, endpoints, applications) into a centralized platform. It normalizes, correlates, and analyzes the data in real-time to detect suspicious activity, generate alerts, and support forensic investigations. Examples include Splunk, ELK Stack, and Microsoft Sentinel.

## 14. What is the difference between hashing and encryption?
**Answer:** Hashing is a one-way function that produces a fixed-size output (digest) from input data; it cannot be reversed. It is used for password storage, data integrity checks, and digital signatures. Encryption is a two-way function that transforms data using a key; encrypted data can be decrypted back to its original form. Encryption provides confidentiality; hashing provides integrity verification.

## 15. Explain the Cyber Kill Chain.
**Answer:** The Cyber Kill Chain, developed by Lockheed Martin, describes the stages of a cyber attack: Reconnaissance (gathering intel on the target), Weaponization (creating malicious payload), Delivery (sending the payload, e.g., phishing email), Exploitation (triggering the vulnerability), Installation (installing malware), Command & Control (C2 — establishing remote control), and Actions on Objectives (data exfiltration, ransomware, etc.). Understanding these stages helps defenders detect and interrupt attacks at each phase.
