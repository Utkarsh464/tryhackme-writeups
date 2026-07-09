# Networking Secure Protocols — Tasks

## Task 1: HTTPS and TLS
- **Purpose:** Understand how TLS encrypts HTTP traffic and authenticates servers.
- **Skills:** TLS handshake comprehension, certificate inspection.
- **Commands:** None.
- **Theory:** HTTPS uses TLS to encrypt HTTP traffic. The TLS handshake involves the client and server negotiating a cipher suite, exchanging certificates, and generating session keys. Certificate Authorities (CAs) sign certificates to validate server identity. Without valid certificates, users are warned of potential man-in-the-middle attacks.

## Task 2: SSH and SFTP
- **Purpose:** Learn how SSH provides encrypted remote access and how SFTP enables secure file transfer.
- **Skills:** SSH authentication method identification, port knowledge.
- **Commands:** None.
- **Theory:** SSH uses public-key cryptography for authentication and establishes an encrypted tunnel for all traffic. SFTP (SSH File Transfer Protocol) runs over SSH and provides secure file operations. Both operate on TCP port 22 by default.

## Task 3: IPsec
- **Purpose:** Understand how IPsec secures IP communications at the network layer.
- **Skills:** Mode differentiation (transport vs. tunnel), protocol understanding (AH vs. ESP).
- **Commands:** None.
- **Theory:** IPsec operates in two modes: transport mode encrypts only the payload, while tunnel mode encrypts the entire IP packet. It uses two protocols: Authentication Header (AH) for integrity and Encapsulating Security Payload (ESP) for both encryption and integrity.

## Task 4: DNSSEC
- **Purpose:** Learn how DNSSEC protects the DNS infrastructure from spoofing and cache poisoning.
- **Skills:** DNSSEC record identification, trust chain understanding.
- **Commands:** None.
- **Theory:** DNSSEC adds cryptographic signatures to DNS records, allowing resolvers to verify authenticity. It uses a chain of trust starting from the root zone, with each parent zone signing the keys of child zones. Record types introduced include RRSIG, DNSKEY, DS, and NSEC.
