# Concepts: The CIA Triad

## 1. Confidentiality
The principle that information should be accessible only to authorised parties. Breached by data leaks, eavesdropping, or theft. Controls include encryption, access controls, and data classification.

## 2. Encryption
A core confidentiality control that transforms data into unreadable form without the correct key. Applied to data at rest (stored files) and data in transit (network traffic).

## 3. Access Control
Mechanisms that restrict resource access to authorised users. Includes discretionary (DAC), mandatory (MAC), and role-based (RBAC) access control models.

## 4. Least Privilege
The security principle that users and systems should have only the minimum permissions needed to perform their functions. Reduces the attack surface and limits damage from compromise.

## 5. Integrity
The principle that data is accurate, consistent, and protected from unauthorised modification. Breached by tampering, corruption, or man-in-the-middle attacks. Controls include hashing and checksums.

## 6. Hashing
A one-way cryptographic function that produces a fixed-size digest from input data. Used to verify integrity by comparing hash values before and after transmission or storage.

## 7. Availability
The principle that systems and data are accessible when needed. Breached by denial-of-service attacks, hardware failures, or natural disasters. Controls include redundancy, backups, and failover.

## 8. Defence in Depth
A layered security strategy that applies multiple independent controls to protect each CIA principle. If one control fails, others continue to provide protection.
