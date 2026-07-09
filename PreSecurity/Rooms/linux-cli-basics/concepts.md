# Concepts: Linux CLI Basics

## 1. Filesystem Hierarchy Standard (FHS)
The FHS defines the standard directory structure for Linux: `/bin` and `/sbin` for binaries, `/etc` for config, `/home` for user data, `/var` for variable data, `/tmp` for temporary files, `/dev` for device files, and `/proc` for virtual kernel/process files. This structure is consistent across FHS-compliant distributions.

## 2. File Permissions (rwx)
Each file has three permission triples: owner (u), group (g), and others (o). Each triple consists of read (r=4), write (w=2), and execute (x=1). `rw-r--r--` means owner can read/write, group and others can only read. Directories require execute to traverse.

## 3. chmod and chown
`chmod` changes file permissions symbolically (`u+x`) or numerically (`755`). Common modes: 755 (executable, writable by owner), 700 (private), 644 (readable by all, writable by owner). `chown user:group` changes file ownership.

## 4. The Root User (UID 0)
Root has unrestricted access, bypassing all permission checks. Commands run as root via `sudo` or `su` can read/write any file, kill any process, and change any configuration. Root should only be used when necessary.

## 5. Process Table and /proc
Each running process has an entry in `/proc/PID/` with environment, memory maps, file descriptors, and command-line arguments. `ps` reads this to present process listings. `/proc` is a virtual filesystem created by the kernel at runtime.

## 6. grep and Pattern Matching
`grep` searches files for lines matching a regular expression. Common flags: `-r` (recursive), `-i` (case-insensitive), `-l` (filenames only), `-n` (line numbers), `-v` (invert). grep is the most-used text processing command for log analysis and auditing.

## 7. sed and Stream Editing
`sed` performs non-interactive text transformations on input streams. Common uses: substitution (`s/pattern/replacement/g`), deletion (`/pattern/d`), printing specific lines (`-n '5,10p'`). It processes line by line without loading entire files into memory.

## 8. find and File Discovery
`find` searches the filesystem for files by name, type, size, time, and permissions. Examples: `find / -name "*.log"` (find log files), `find / -perm -4000` (SUID binaries), `find /home -size +1G` (large files). It is an essential audit and reconnaissance tool.