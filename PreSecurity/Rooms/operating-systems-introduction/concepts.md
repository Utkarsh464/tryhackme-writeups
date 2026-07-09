# Concepts: Operating Systems Introduction

## 1. Operating System
Software that manages computer hardware and provides common services for application programs. It handles process execution, memory allocation, file storage, device communication, and user interaction. The OS is the critical layer between physical hardware and software applications.

## 2. Monolithic Kernel
All OS subsystems (scheduling, file system, networking, device drivers) run in kernel space with full hardware access. This provides high performance via direct function calls but means a bug in any subsystem can crash the entire system. Linux uses a monolithic kernel (with modular loadable drivers).

## 3. Microkernel
Only the most essential functions (inter-process communication, basic scheduling, memory management) run in kernel space. File systems, drivers, and networking run as user-space processes. This improves stability (a driver crash doesn't crash the system) but adds performance overhead from IPC. Minix is a classic example.

## 4. Hybrid Kernel
Combines monolithic and microkernel approaches. The kernel runs as a single binary but includes a minimal microkernel core with additional modular services running in kernel space. Windows NT kernel uses this approach, balancing performance with modularity and stability.

## 5. Process Scheduler
The kernel component that determines which process runs on the CPU and for how long. Scheduling algorithms include round-robin (fair time slices), priority-based (higher priority runs first), and multi-level feedback queue (dynamic priority adjustment). The scheduler directly impacts system responsiveness and throughput.

## 6. Virtual Memory
The OS gives each process a virtual address space independent of physical RAM, translating addresses via page tables. This enables processes to use more memory than physically available (via swapping), isolates processes from each other, and simplifies memory allocation for applications.

## 7. File System Journaling
A journal records pending file system operations before they are executed. After a crash or power failure, the journal is replayed to complete or roll back incomplete operations, avoiding the need for lengthy file system checks. Supported by ext3, ext4, NTFS, and most modern file systems.

## 8. Shell and User Interface
The shell is a command-line interpreter that executes user commands, runs scripts, and controls processes. Popular shells include Bash (Linux), Zsh, and PowerShell (Windows). The graphical UI (GUI) provides visual interaction through windows, menus, and pointers. Both interfaces can be targets for attacks if not properly secured.