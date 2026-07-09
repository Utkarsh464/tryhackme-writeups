# Commands: Client-Server Basics

## Web Servers

| Command | Description |
|---------|-------------|
| `curl http://example.com` | Send HTTP request and show response |
| `curl -I https://example.com` | Fetch HTTP response headers only |
| `telnet example.com 80` | Open raw TCP connection to web server |
| `sudo systemctl status apache2` | Check Apache web server status |
| `nginx -t` | Test Nginx configuration syntax |

## File Servers

| Command | Description |
|---------|-------------|
| `smbclient -L //server` | List SMB shares on a server |
| `mount -t nfs server:/share /mnt` | Mount an NFS share |
| `showmount -e server` | List NFS exports on a server |

## Database Servers

| Command | Description |
|---------|-------------|
| `mysql -u root -p` | Connect to MySQL interactive client |
| `psql -U user -d db` | Connect to PostgreSQL database |
| `mssql -S server -U sa` | Connect to Microsoft SQL Server |

## Mail Servers

| Command | Description |
|---------|-------------|
| `telnet mail.server.com 25` | Raw SMTP interaction |
| `openssl s_client -connect smtp:465` | SMTPS connection test |
| `openssl s_client -connect imap:993` | IMAPS connection test |

## General Network

| Command | Description |
|---------|-------------|
| `netstat -tulpn` | Show listening TCP/UDP ports |
| `sudo ufw status` | Check firewall rules (UFW) |
| `ss -tuln` | Alternative netstat for socket statistics |