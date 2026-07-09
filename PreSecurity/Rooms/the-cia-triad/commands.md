# Commands: The CIA Triad

## Integrity Verification

| Command | Description |
|---------|-------------|
| `sha256sum file.txt` | Generate SHA-256 hash of a file |
| `md5sum file.txt` | Generate MD5 hash of a file |
| `sha256sum -c checksum.txt` | Verify file integrity against checksum file |
| `cksum file.txt` | Generate CRC checksum and byte count |

## File Permissions (Access Control)

| Command | Description |
|---------|-------------|
| `chmod 600 file` | Set file to read/write for owner only |
| `chown user:group file` | Change file owner and group |
| `ls -la` | View file permissions |
| `umask 077` | Set default permissions for new files |
