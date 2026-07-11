# Security Principles — Commands

This room is primarily conceptual and does not introduce specific command-line tools. However, the following commands and utilities are referenced for security auditing and compliance verification:

| Command | Description |
|---------|-------------|
| `openssl dgst -sha256 file.txt` | Compute SHA256 hash to verify file integrity |
| `sha256sum file.txt` | Compute and verify SHA256 checksums |
| `gpg --verify file.sig` | Verify a GPG digital signature |
| `getfacl file.txt` | View file access control lists on Linux |
| `setfacl -m u:user:rwx file.txt` | Modify file ACLs on Linux |
| `icacls file.txt` | View file permissions on Windows |
| `tail -f /var/log/auth.log` | Monitor authentication logs on Linux |
| `Get-EventLog -LogName Security` | View security event logs on Windows (PowerShell) |
| `nmap -p 22,80,443 target.com` | Port scanning to verify firewall controls |
| `openssl s_client -connect example.com:443` | Test TLS certificate validity |
| `openssl enc -aes-256-cbc -salt -in plain.txt -out encrypted.enc` | Encrypt a file using AES-256-CBC for confidentiality |
| `openssl enc -d -aes-256-cbc -in encrypted.enc -out decrypted.txt` | Decrypt an AES-256-CBC encrypted file |
| `gpg --symmetric --cipher-algo AES256 secrets.txt` | Encrypt a file symmetrically with GPG |
| `gpg --decrypt secrets.txt.gpg` | Decrypt a GPG-encrypted file |
| `ssh-keygen -t ed25519 -a 100` | Generate an Ed25519 SSH key pair for authentication |
| `ssh-copy-id user@server` | Install a public SSH key for passwordless authentication |

## Additional Context
The commands listed above support the implementation of security principles covered in this room. For example, hashing commands (`sha256sum`, `openssl dgst`) enforce integrity by allowing verification that files have not been tampered with. Encryption commands (`openssl enc`, `gpg`) enforce confidentiality by protecting data at rest and in transit. Access control commands (`getfacl`, `setfacl`, `icacls`) enforce least privilege by granting only the minimum necessary permissions. Log monitoring commands (`tail -f /var/log/auth.log`, `Get-EventLog`) support accountability and accounting by tracking who accessed what and when. These commands are commonly used by system administrators and security professionals to operationalize security principles in real-world environments.
