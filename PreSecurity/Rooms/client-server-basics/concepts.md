# Concepts: Client-Server Basics

## 1. Client-Server Model
A distributed application architecture where clients initiate connections and send requests to a centralised server, which processes them and returns responses. The server provides shared resources such as files, databases, or compute power. Advantages include centralised administration, security, and resource pooling.

## 2. Request-Response Pattern
Communication follows a strict pattern: the client sends a request (usually structured, e.g. an HTTP request), the server processes it, and sends back a response. This pattern is fundamental to HTTP, DNS, SMTP, and most application-layer protocols.

## 3. Web Servers (Apache vs Nginx)
Apache uses a process/thread-based architecture and supports per-directory configuration via `.htaccess`. Nginx uses an asynchronous, event-driven architecture that handles thousands of simultaneous connections with minimal resource overhead. Each has different performance characteristics and security considerations.

## 4. File Server Protocols (SMB vs NFS)
SMB (Server Message Block) is the native Windows file sharing protocol, also supported by Linux via Samba. NFS (Network File System) is native to Unix/Linux systems. Both require authentication and permission management to control access. SMB has historically been a vector for worm propagation (EternalBlue).

## 5. Database Servers
Database servers (MySQL, PostgreSQL, MSSQL) manage structured data and handle client SQL queries. They use authentication, user privileges, and query parsing. SQL injection is among the most critical web vulnerabilities, exploiting improper input sanitisation in database queries.

## 6. Mail Server Protocols (SMTP, IMAP, POP3)
SMTP handles outgoing message transmission and relay. IMAP keeps mail on the server for multi-device access. POP3 downloads messages to the client. Unsecured SMTP servers can be abused as open relays for spam. Encryption (STARTTLS) is critical for all three protocols.

## 7. Peer-to-Peer vs Client-Server
In P2P, every node acts as both client and server, distributing load and removing central points of failure. However, P2P lacks centralised access control, making it harder to enforce security policies. Client-server centralises management but creates high-value attack targets.

## 8. Security Implications of Client-Server
Servers are high-value targets exposed to the network. Attack vectors include DDoS, SQL injection, path traversal, authentication bypass, and service-specific exploits. Defence strategies include firewalls, intrusion detection, input validation, least privilege, and encryption.