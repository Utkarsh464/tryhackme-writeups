# FTP

## Definition
FTP (File Transfer Protocol) is a standard network protocol used to transfer files between a client and a server on a computer network. Operating on TCP, it typically uses ports 20 (data) and 21 (control). FTP has been a foundational file transfer mechanism since the early Internet, though it is increasingly replaced by more secure alternatives.

## Why It Matters
FTP is still widely deployed in legacy systems, embedded devices, and network equipment. Understanding FTP is important for security professionals because: (1) FTP transmits credentials and data in plaintext (no encryption), making it a significant security risk; (2) FTP servers are common targets for anonymous access abuse and data theft; (3) analyzing FTP traffic reveals file transfer patterns in forensic investigations; and (4) understanding FTP limitations motivates the adoption of secure alternatives like SFTP and FTPS.

## Where It Appears in the Path
FTP is covered in the networking module alongside other application-layer protocols. It provides context for understanding secure file transfer protocols (SFTP, FTPS) and is a common target in penetration testing labs for anonymous access and credential brute-forcing.

## Prerequisites
- TCP/IP fundamentals (ports, connections)
- Client-server architecture basics

## FTP Architecture
FTP uses two separate TCP connections:
- **Control Connection (Port 21)**: For commands and responses. Persistent throughout the session.
- **Data Connection (Port 20, default)**: For actual file data. Opened per transfer.

## Active vs Passive Mode

### Active Mode
1. Client opens a random port (N > 1023) and sends `PORT N` to the server.
2. Server connects FROM port 20 TO client port N.
3. Problem: Client firewalls often block incoming connections on high ports.

### Passive Mode
1. Client sends `PASV` command.
2. Server opens a random port (P > 1023) and sends it to the client.
3. Client connects FROM random port TO server port P.
4. Solves the firewall issue — client initiates both connections.

Passive mode is standard today. Firewalls must allow outbound connections to high ports.

## FTP Commands
- `USER`, `PASS`: Authentication
- `PWD`, `CWD`: Directory navigation
- `LIST`, `NLST`: List files
- `RETR filename`: Download file
- `STOR filename`: Upload file
- `DELE filename`: Delete file
- `MKD`, `RMD`: Create/remove directory
- `RENAME`: Rename file
- `ABOR`: Abort transfer

## FTP Response Codes
- 110 Restart marker reply
- 120 Service ready in n minutes
- 125 Data connection already open
- 150 File status okay
- 200 Command okay
- 220 Service ready
- 221 Service closing control connection
- 226 Closing data connection
- 230 User logged in
- 331 User name okay, need password
- 425 Can't open data connection
- 426 Connection closed
- 450 File unavailable
- 500 Syntax error, command unrecognized
- 530 Not logged in
- 550 Requested action not taken (file unavailable)

## FTP vs SFTP vs FTPS

| Protocol | Encryption | Port(s) | Based On |
|----------|-----------|---------|----------|
| **FTP** | None (plaintext) | 21 (control), 20 (data) | FTP protocol |
| **FTPS (FTP over SSL/TLS)** | TLS/SSL | 990 (implicit) or 21 (explicit AUTH TLS) | FTP protocol |
| **SFTP (SSH File Transfer Protocol)** | SSH encryption | 22 | SSH protocol (not FTP!) |

SFTP is often preferred because it uses a single port (22), encrypts both authentication and data, and benefits from SSH key management. FTPS retains the complexity of separate control/data connections but adds encryption.

## Security Concerns
- **Plaintext credentials**: Username and password are sent as cleartext in USER/PASS commands.
- **Data in cleartext**: File contents are transmitted unencrypted.
- **Anonymous access**: Unsecured FTP servers allow anyone to log in with username `anonymous` and any email as password.
- **Bounce attack**: FTP can be tricked to send data to a third-party IP (used for port scanning).
- **Weak authentication**: No support for modern authentication mechanisms (MFA, key-based).

## Common Interview Questions
1. **What is the difference between FTP active and passive mode?** Active: server connects to client for data. Passive: client connects to server for data. Passive is firewall-friendly.
2. **What is the difference between FTP and SFTP?** FTP is unencrypted, uses ports 20/21, separate control/data connections. SFTP is encrypted via SSH, uses single port 22, is a completely different protocol.
3. **Why is FTP considered insecure?** Credentials and data are transmitted in plaintext. No encryption. Vulnerable to sniffing, MITM, credential theft.
4. **What is anonymous FTP access?** FTP that allows login with username "anonymous" and no proper password. Used for public file sharing but often a security risk if misconfigured.
5. **How do you secure an FTP server?** (1) Don't use FTP — use SFTP/FTPS. (2) Disable anonymous access. (3) Restrict by IP (firewall). (4) Chroot users to their home directories. (5) Use strong passwords. (6) Enable logging and monitoring. (7) Implement file integrity monitoring.
6. **What is the default port for FTP control connection?** 21 (TCP).

## Further Reading
- [RFC 959 — File Transfer Protocol](https://tools.ietf.org/html/rfc959)
- [RFC 4217 — Securing FTP with TLS (FTPS)](https://tools.ietf.org/html/rfc4217)
- [OWASP FTP Best Practices](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/02-Configuration_and_Deployment_Management_Testing/09-Test_File_Permissions)
- `man ftp`, `man vsftpd`
- VSFTPD (Very Secure FTP Daemon) documentation
