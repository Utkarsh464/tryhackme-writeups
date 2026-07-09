# Tasks: Operating Systems Introduction

## Task 1: What is an OS and Kernel Types
**Purpose:** Define the operating system and compare kernel architectures.

**Skills:** Distinguishing monolithic, microkernel, and hybrid kernels.

**Theory:** The OS is software that manages hardware and provides services to applications. The kernel is its core. Monolithic kernels (Linux) run all subsystems in kernel space for performance. Microkernels (Minix) run minimal code in kernel space, placing drivers and services in user space for stability. Hybrid kernels (Windows NT) combine elements of both.

**Commands:** `uname -a`, `cat /proc/version`

---

## Task 2: Process Scheduling
**Purpose:** Understand how the OS schedules processes for CPU time.

**Skills:** Round-robin, priority-based, multi-level feedback queue.

**Theory:** The scheduler determines which process runs next. Round-robin assigns fixed time slices in a circular order. Priority scheduling runs higher-priority processes first. Multi-level feedback queue uses multiple queues with different priorities and adjusts process priority dynamically based on behaviour (CPU-bound vs I/O-bound).

**Commands:** `ps -eo pid,comm,%cpu,%mem,pri`, `top`, `nice -n 10 ./program`

---

## Task 3: Memory Management
**Purpose:** Learn how the OS manages virtual memory, paging, and segmentation.

**Skills:** Virtual address translation, page faults, swap.

**Theory:** The memory manager gives each process its own virtual address space, mapped to physical memory via page tables. Paging divides memory into fixed-size pages. Segmentation uses variable-sized segments. When RAM fills, pages are swapped to disk. The memory manager handles protection by preventing processes from accessing each other's address space.

**Commands:** `free -h`, `cat /proc/meminfo`, `vmstat 1`

---

## Task 4: File Systems
**Purpose:** Compare file system types and the journaling mechanism.

**Skills:** ext4 vs NTFS, journaling, inodes, MFT.

**Theory:** A file system controls how data is stored and retrieved. ext4 (Linux) uses inodes to store metadata, supporting journaling to prevent corruption after crashes. NTFS (Windows) uses the Master File Table (MFT), supports permissions (ACLs), alternate data streams, compression, and encryption. Journaling records pending changes to a log for crash recovery.

**Commands:** `lsblk -f`, `df -hT`, `stat /etc/passwd`

---

## Task 5: Device Drivers and Shell/UI
**Purpose:** Explain how the OS communicates with hardware and interfaces with users.

**Skills:** Kernel modules, shell interpreters, graphical UIs.

**Theory:** Device drivers are kernel modules that enable the OS to control hardware. They can be compiled into the kernel or loaded as modules. The shell interprets user commands. The UI can be CLI-only (servers) or GUI-based. Each has different security properties and attack surfaces.

**Commands:** `lsmod`, `modinfo <module>`, `echo $SHELL`

---