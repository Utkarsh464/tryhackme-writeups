# Tasks: Windows Command Line

## Task 1: Introduction to Command Prompt

**Purpose:** Access the Windows Command Prompt and understand its role.

**Skills:** Command-line access, basic operation.

**Theory:** Command Prompt (cmd.exe) is the traditional Windows command-line interpreter. It executes commands and displays output in a text window. It can be launched from the Start menu, Run dialog (cmd), or from File Explorer by typing cmd in the address bar. Administrative privileges may be required for certain commands.

**Commands:**
- cmd - Launch Command Prompt
- help - Display command help
- cls - Clear the screen
- exit - Close Command Prompt
- ver - Display Windows version

---

## Task 2: Filesystem Navigation

**Purpose:** Navigate the Windows filesystem using command-line commands.

**Skills:** Directory navigation, path understanding.

**Theory:** Windows uses drive letters with backslash paths. The current directory is displayed in the prompt. dir lists contents, cd changes directories, and tree shows the directory structure graphically. Absolute paths start with a drive letter (C:\Users), while relative paths are based on the current location.

**Commands:**
- dir - List directory contents
- cd - Change directory or display current path
- md or mkdir - Create directory
- rd or rmdir - Remove directory
- tree - Display directory tree structure

---

## Task 3: File Management

**Purpose:** Create, copy, move, rename, and delete files.

**Skills:** File operations.

**Theory:** File management commands are essential for organizing data. copy duplicates files, move relocates files, del deletes files, and ren renames files. The xcopy and robocopy commands provide advanced copying capabilities with additional options for directories, attributes, and error handling.

**Commands:**
- copy - Copy files
- move - Move or rename files
- del - Delete files
- ren - Rename files
- xcopy - Copy files and directories
- robocopy - Robust file copy
- type - Display file contents
- findstr - Search for strings in files

---

## Task 4: Networking Commands

**Purpose:** Diagnose and troubleshoot network connectivity.

**Skills:** Network troubleshooting.

**Theory:** Windows networking commands allow administrators to diagnose connectivity issues. ipconfig shows IP configuration, ping tests reachability, tracert traces the route to a destination, nslookup queries DNS, netstat displays active connections, and pathping combines ping and tracert for detailed analysis.

**Commands:**
- ipconfig - Display IP configuration
- ping - Test network connectivity
- tracert - Trace route to destination
- nslookup - Query DNS servers
- netstat - Display network statistics
- pathping - Trace route with latency analysis

---

## Task 5: System Administration

**Purpose:** Manage system settings, processes, and users from the command line.

**Skills:** System administration.

**Theory:** The command line provides system administration capabilities. systeminfo displays comprehensive system details. tasklist shows running processes, and taskkill terminates them. schtasks manages scheduled tasks. net commands manage users, services, and network resources.

**Commands:**
- systeminfo - System configuration information
- tasklist - List running processes
- taskkill - Terminate processes
- schtasks - Schedule tasks
- net user - Manage user accounts
- net localgroup - Manage local groups
- net start - Start a service
- net stop - Stop a service
