# Tasks: Linux Fundamentals Part 2

## Task 1: User and Group Management

**Purpose:** Learn to create, modify, and delete Linux users and groups.

**Skills:** User administration, group management.

**Theory:** Linux is a multi-user system. Each user has a unique username and user ID (UID). Users are organized into groups with shared permissions. Root is the superuser with unlimited privileges. Regular users can perform tasks with elevated privileges using sudo. User information is stored in /etc/passwd, passwords in /etc/shadow.

**Commands:**
- useradd - Create new user
- usermod - Modify user account
- userdel - Delete user account
- passwd - Change user password
- groupadd - Create new group
- groups - Show user group membership

---

## Task 2: File Permissions

**Purpose:** Understand and modify Linux file permissions and ownership.

**Skills:** Permission management, security hardening.

**Theory:** Every file has read (r), write (w), and execute (x) permissions for three categories: owner, group, and others. Permissions can be set symbolically (chmod u+x file) or numerically (chmod 755 file). The chown command changes file ownership. Understanding permissions is critical for security.

**Commands:**
- chmod - Change file mode bits
- chown - Change file owner and group
- chgrp - Change group ownership
- ls -l - List with permissions
- umask - Set default permissions

---

## Task 3: Process Management

**Purpose:** Monitor and control running processes.

**Skills:** Process monitoring, resource management.

**Theory:** A process is a running instance of a program. Each process has a unique process ID (PID). Processes can be viewed with ps and top. Signals (SIGTERM, SIGKILL) are sent with kill to terminate processes. Background and foreground job control is managed with &, bg, and fg.

**Commands:**
- ps - Report process status
- top - Display Linux processes
- kill - Send signal to process
- killall - Kill processes by name
- bg - Resume job in background
- fg - Resume job in foreground
- jobs - List active jobs

---

## Task 4: Service Management with systemd

**Purpose:** Manage system services using systemd.

**Skills:** Service administration, system control.

**Theory:** systemd is the init system and service manager for most modern Linux distributions. Services (daemons) run in the background and can be started, stopped, enabled, disabled, and monitored using systemctl. System logs are viewed with journalctl.

**Commands:**
- systemctl start - Start a service
- systemctl stop - Stop a service
- systemctl enable - Enable service at boot
- systemctl disable - Disable service at boot
- systemctl status - Check service status
- journalctl - Query system log

---

## Task 5: Text Editors

**Purpose:** Edit configuration files using terminal-based text editors.

**Skills:** File editing, configuration management.

**Theory:** Linux configuration files are plain text. nano is a beginner-friendly editor with on-screen shortcuts. vim is a powerful modal editor with a steep learning curve but high efficiency. Both are essential for editing files directly on servers without a GUI.

**Commands:**
- nano - Simple text editor
- vim - Advanced text editor
