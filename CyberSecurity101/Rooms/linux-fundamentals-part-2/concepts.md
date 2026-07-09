# Concepts: Linux Fundamentals Part 2

## 1. Multi-User System
Linux is designed to support multiple users simultaneously. Each user has a unique username, user ID (UID), home directory, and login shell. Users can be working on the same system at the same time without interfering with each other, with file permissions controlling access.

## 2. Root User (Superuser)
The administrative superuser with UID 0 who has unrestricted access to all system resources. Root can read, write, and execute any file, change any configuration, and perform any system operation. Due to its power, regular use of root is discouraged in favor of sudo for privilege escalation.

## 3. Sudo
A program that allows permitted users to execute commands as the superuser (or another user) while providing an audit trail. Sudo is configured in /etc/sudoers and typically grants specific users or groups the ability to run specific commands with elevated privileges.

## 4. File Permissions
Linux file permissions control who can read, write, and execute files and directories. Permissions are divided into three categories: owner (u), group (g), and others (o). Each category has read (r=4), write (w=2), and execute (x=1) permissions, often represented as octal numbers (e.g., 755) or symbolic strings (e.g., rwxr-xr-x).

## 5. SetUID, SetGID, and Sticky Bit
Special permission bits that modify file and directory behavior. SetUID (s on owner) runs a file with the owner's privileges. SetGID (s on group) runs with the group's privileges or ensures new files in a directory inherit the group. Sticky Bit (t on others) restricts file deletion in shared directories to file owners only.

## 6. Process
A running instance of a program with a unique process ID (PID). Processes have a parent process (PPID), a user owner, and resource usage statistics. Processes can run in the foreground (interactive) or background (detached from terminal).

## 7. Signals
Software interrupts sent to processes to notify them of events or request actions. Common signals include SIGTERM (15) for graceful termination, SIGKILL (9) for forceful termination, SIGINT (2) for interrupt (Ctrl+C), and SIGHUP (1) for hangup or reload configuration.

## 8. Daemon
A background process that runs continuously, performing system services. Daemons typically start at boot and operate independently of user sessions. Examples include sshd (SSH server), httpd (web server), and systemd-journald (logging).

## 9. systemd
The init system and service manager used by most modern Linux distributions. systemd replaces the older SysV init system and provides parallel service startup, dependency management, socket activation, and comprehensive logging with journald.

## 10. JournalD
systemd's logging system that collects and stores log data from the kernel, system services, and applications. Journalctl queries the journal with filtering by service, time range, priority, and other criteria.
