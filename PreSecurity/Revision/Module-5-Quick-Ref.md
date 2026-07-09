# Module 5: Operating Systems Basics — Quick Reference

## Key Concepts
- **Linux Filesystem**: / (root), /bin, /etc, /home, /var, /tmp, /dev, /proc, /usr
- **Linux Permissions**: rwx (read=4, write=2, execute=1) for Owner/Group/Others
- **Windows Filesystem**: C:\, Users, Program Files, Windows, System32
- **Windows Permissions**: NTFS with ACLs, SIDs, inheritance
- **Process Management**: Linux (ps, top, kill, systemctl), Windows (Task Manager, tasklist, taskkill)
- **UAC (User Account Control)**: Windows security feature — prompts for admin approval
- **Linux Services**: Managed by systemd — systemctl start/stop/enable/disable
- **Windows Services**: Managed by Services.msc or sc command
- **SSH**: Secure shell for remote Linux access (port 22)
- **RDP**: Remote Desktop Protocol for Windows (port 3389)

## Important Linux Commands
| Command | Purpose |
|---------|---------|
| `ls -la` | List files with details |
| `cd dir` | Change directory |
| `pwd` | Print working directory |
| `chmod 755 file` | Set file permissions |
| `chown user:group file` | Change owner/group |
| `ps aux` | List all processes |
| `grep pattern file` | Search text |
| `ssh user@host` | SSH to remote server |
| `scp file user@host:/path` | Copy files over SSH |
| `sudo command` | Run as superuser |
| `apt install pkg` | Install package (Debian) |

## Important Windows Commands
| Command | Purpose |
|---------|---------|
| `ipconfig` | Show IP configuration |
| `whoami` | Current user |
| `net user` | List users |
| `net localgroup` | List groups |
| `tasklist` | Running processes |
| `systeminfo` | System configuration |
| `regedit` | Registry editor |
| `msconfig` | System configuration |

## Key Terms
- **Kernel**: Core of the OS, manages hardware and resources
- **Shell**: Command interpreter (bash, zsh, PowerShell, cmd)
- **SID**: Security Identifier (Windows unique user/group ID)
- **ACL**: Access Control List — defines permissions
- **Run Level / Target**: System state (Linux runlevels, systemd targets)
- **SUID/GUID**: Special Linux permission bits for elevated execution
