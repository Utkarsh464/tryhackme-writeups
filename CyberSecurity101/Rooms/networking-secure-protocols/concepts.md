# Networking Secure Protocols — Concepts

## TLS (Transport Layer Security)
A cryptographic protocol that provides encryption, authentication, and integrity for data in transit. Replaces the older SSL standard. Used extensively by HTTPS.

## HTTPS (HTTP Secure)
HTTP traffic encrypted over TLS. Prevents eavesdropping, tampering, and impersonation. Identified by the padlock icon in browsers and the https:// URL scheme.

## SSH (Secure Shell)
A protocol for secure remote administration and file transfer. Uses public-key cryptography for authentication and encrypts all traffic. Operates on TCP port 22.

## SFTP (SSH File Transfer Protocol)
A secure file transfer protocol that runs over SSH. Unlike FTPS, it does not require a separate control channel.

## IPsec (Internet Protocol Security)
A suite of protocols for securing IP communications. Can operate in transport mode (payload only) or tunnel mode (entire packet). Uses AH for integrity and ESP for encryption.

## DNSSEC (DNS Security Extensions)
Adds cryptographic authentication to DNS responses, preventing cache poisoning and spoofing. Uses a chain of trust from the root zone down to individual domains.
