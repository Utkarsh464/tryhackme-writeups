# Commands: Linux Fundamentals Part 1

## Filesystem Navigation

| Command | Description | Example |
|---------|-------------|---------|
| `pwd` | Print working directory | `pwd` outputs `/home/user` |
| `ls` | List directory contents | `ls -la` lists all files with details |
| `cd` | Change directory | `cd /var/log` changes to /var/log |
| `tree` | Display directory tree | `tree /etc` shows directory structure |

## File Operations

| Command | Description | Example |
|---------|-------------|---------|
| `touch` | Create empty file or update timestamp | `touch file.txt` |
| `cat` | Display file contents | `cat /etc/passwd` |
| `less` | View file with pagination | `less longfile.log` |
| `more` | View file with simple pagination | `more output.txt` |
| `head` | Display first 10 lines | `head -n 20 file.txt` |
| `tail` | Display last 10 lines | `tail -f /var/log/syslog` |
| `cp` | Copy files or directories | `cp source.txt dest.txt` |
| `mv` | Move or rename files | `mv old.txt new.txt` |
| `rm` | Remove files | `rm file.txt` |
| `mkdir` | Create directory | `mkdir newdir` |
| `rmdir` | Remove empty directory | `rmdir emptydir` |
| `file` | Determine file type | `file document.pdf` |

## File Viewing Utilities

| Command | Description | Example |
|---------|-------------|---------|
| `echo` | Print text to output | `echo "Hello World"` |
| `nl` | Number lines of file | `nl file.txt` |
| `od` | Dump file in octal/hex | `od -c binaryfile` |

## Help Commands

| Command | Description | Example |
|---------|-------------|---------|
| `man` | Display manual page | `man ls` |
| `whatis` | Brief command description | `whatis cat` |
| `apropos` | Search manual page names | `apropos editor` |
| `help` | Shell built-in help | `help echo` |
