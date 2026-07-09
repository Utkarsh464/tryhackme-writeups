# Tasks: The CIA Triad

## Task 1: Confidentiality
**Purpose:** Understand how to protect data from unauthorised access.

**Skills:** Encryption, access control, least privilege.

**Theory:** Confidentiality ensures only authorised parties can access information. Controls include encryption (at rest and in transit), access control lists, the principle of least privilege, and data classification schemes.

**Commands:** None

---

## Task 2: Integrity
**Purpose:** Ensure data is accurate and unaltered.

**Skills:** Hashing, checksums, audit logs.

**Theory:** Integrity guarantees that data has not been modified by unauthorised parties. Hashing algorithms (SHA-256) verify file integrity, checksums detect transmission errors, version control tracks changes, and audit logs record modifications.

**Commands:** `sha256sum file.txt`

---

## Task 3: Availability
**Purpose:** Ensure systems and data are accessible when needed.

**Skills:** Redundancy, backups, failover.

**Theory:** Availability ensures authorised users can access resources when required. Controls include redundant hardware, regular backups, failover clusters, load balancers, and DDoS protection measures.

**Commands:** None

---

## Task 4: Real-World Examples
**Purpose:** Apply the CIA Triad to practical scenarios.

**Skills:** Security analysis.

**Theory:** A healthcare database requires high confidentiality (patient privacy) and integrity (accurate records). An e-commerce site prioritises availability (uptime) while maintaining confidentiality (payment data) and integrity (order accuracy).

**Commands:** None

---

## Task 5: Trade-offs
**Purpose:** Understand that CIA principles can conflict.

**Skills:** Balancing security requirements.

**Theory:** Increasing confidentiality (e.g., complex authentication) can reduce availability (slower access). Strong integrity checks can impact performance. Security design requires balancing these principles based on the specific context and risk tolerance.

**Commands:** None

---
