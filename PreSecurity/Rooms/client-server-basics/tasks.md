# Tasks: Client-Server Basics

## Task 1: The Client-Server Model
**Purpose:** Define the client-server architecture and how it enables distributed computing.

**Skills:** Identifying the roles of client and server in network communication.

**Theory:** In the client-server model, clients initiate requests and servers respond with data or services. Communication follows a request-response pattern over a network. A single server can serve many clients simultaneously, centralising resources and enabling scalable, manageable service delivery.

**Commands:** `curl http://example.com`, `telnet example.com 80`

---

## Task 2: Web Servers
**Purpose:** Understand how web servers deliver web content to browsers.

**Skills:** Configuring Apache or Nginx, analysing HTTP headers.

**Theory:** Web servers handle HTTP/HTTPS requests from browsers and serve HTML pages, images, and API responses. Apache uses `.htaccess` directories and mod_* modules; Nginx uses an event-driven architecture for high concurrency. Both require careful security configuration to prevent common web attacks.

**Commands:** `sudo systemctl status apache2`, `curl -I https://example.com`, `nginx -t`

---

## Task 3: File and Database Servers
**Purpose:** Examine file sharing and database server roles.

**Skills:** SMB/NFS for file access, SQL for data management.

**Theory:** File servers use SMB (Windows file sharing) or NFS (Unix) to provide centralised storage access. Database servers like MySQL and PostgreSQL store structured data and process SQL queries. Both types must enforce access controls and authentication to protect sensitive resources.

**Commands:** `smbclient -L //server`, `mysql -u root -p`, `psql -U user -d db`

---

## Task 4: Mail Servers
**Purpose:** Understand how email delivery works via SMTP and mailbox access via IMAP/POP3.

**Skills:** SMTP relay, IMAP vs POP3 differences.

**Theory:** Mail servers use SMTP to send and relay messages between domains. Recipients retrieve messages via IMAP (keeps messages on server, syncs across devices) or POP3 (downloads and typically deletes). SMTP servers must be hardened against open relay abuse and spoofing.

**Commands:** `telnet mail.server.com 25`, `openssl s_client -connect server:993`

---

## Task 5: Peer-to-Peer and Security Implications
**Purpose:** Contrast client-server with peer-to-peer and explore attack surfaces.

**Skills:** P2P architecture, server-side vs client-side attacks.

**Theory:** In P2P, every node is both client and server, distributing the load but complicating security. Client-server centralises control, making servers high-value targets — DDoS, SQL injection, XSS, and authentication bypass are common attack vectors. Securing both ends requires defence in depth.

**Commands:** `netstat -tulpn`, `sudo ufw status`

---