# Tasks: Inside a Computer

## Task 1: The CPU
**Purpose:** Learn the central processing unit's architecture and role.

**Skills:** Identifying CPU components and performance metrics.

**Theory:** The CPU executes instructions through a fetch-decode-execute cycle. Cores are individual processing units; more cores allow parallel execution. Clock speed measures cycles per second (GHz). Cache memory (L1, L2, L3) provides high-speed data access close to the core. x86 and ARM are the dominant instruction set architectures.

**Commands:** `lscpu`, `cat /proc/cpuinfo`, `wmic cpu get name`

---

## Task 2: RAM and Memory
**Purpose:** Understand volatile memory types and their characteristics.

**Skills:** Differentiating RAM generations and virtual memory concepts.

**Theory:** RAM (Random Access Memory) is volatile storage the CPU uses for active data. DDR generations (DDR3, DDR4, DDR5) differ in speed, bandwidth, and power efficiency. Virtual memory uses disk space (swap/pagefile) to extend apparent RAM capacity, enabling larger workloads than physical RAM alone allows.

**Commands:** `free -h`, `cat /proc/meminfo`, `wmic memorychip get capacity`

---

## Task 3: Storage Devices
**Purpose:** Compare storage technologies and their performance profiles.

**Skills:** Differentiating HDD, SATA SSD, NVMe SSD, and eMMC.

**Theory:** HDDs use spinning magnetic platters for low-cost bulk storage. SATA SSDs use flash memory over the SATA bus for faster access. NVMe SSDs connect directly over PCIe lanes, achieving significantly higher throughput. eMMC is embedded flash storage commonly found in low-cost laptops and single-board computers.

**Commands:** `lsblk`, `sudo fdisk -l`, `df -h`

---

## Task 4: The Motherboard and GPU
**Purpose:** Identify motherboard components and the GPU's role in parallel processing.

**Skills:** Understanding chipset, PCIe, and GPU architecture.

**Theory:** The motherboard interconnects all components via the chipset. PCIe lanes provide high-speed connections for expansion cards like GPUs and NVMe drives. The GPU performs parallel floating-point operations using thousands of cores, making it essential for rendering graphics and accelerating compute workloads via CUDA.

**Commands:** `lspci`, `nvidia-smi`, `sudo lshw`

---