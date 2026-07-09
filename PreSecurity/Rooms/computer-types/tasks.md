# Tasks: Computer Types

## Task 1: Desktops and Laptops
**Purpose:** Compare personal computing form factors and their trade-offs.

**Skills:** Understanding modularity, portability, and integrated vs discrete components.

**Theory:** Desktops are modular and upgradeable — CPU, RAM, GPU, and storage can be replaced individually. Laptops prioritise portability and power efficiency, often soldering RAM and CPU (BGA) and using integrated peripherals. These design choices affect repairability, upgradeability, and lifespan.

**Commands:** `sudo dmidecode -t system`, `lspci -v`

---

## Task 2: Servers
**Purpose:** Understand server-specific hardware for reliability and remote management.

**Skills:** Rack form factors, ECC memory, redundant power, IPMI/BMC.

**Theory:** Servers are designed for continuous operation in data centres. They use ECC (Error-Correcting Code) RAM to detect and fix memory errors, redundant power supplies to survive PSU failure, and IPMI (Intelligent Platform Management Interface) or BMC for out-of-band remote management independent of the OS.

**Commands:** `ipmitool sensor list`, `dmidecode -t memory`

---

## Task 3: Workstations
**Purpose:** Identify workstation-class hardware for professional workloads.

**Skills:** High-core-count CPUs, professional GPUs, certification.

**Theory:** Workstations bridge consumer and server hardware. They use high-core-count CPUs (Threadripper, Xeon, EPYC), professional GPUs (NVIDIA RTX A-series, AMD Radeon Pro) with ISV certification for CAD/DCC software, and ECC memory for data integrity during long compute jobs.

**Commands:** `nvidia-smi -q`, `lscpu | grep "Core(s) per socket"`

---

## Task 4: Embedded Systems and Microcontrollers
**Purpose:** Explore embedded computing platforms and constrained devices.

**Skills:** Single-board computers, microcontrollers, GPIO, real-time requirements.

**Theory:** Embedded systems like the Raspberry Pi run full operating systems (Linux) with GPIO for hardware interfacing. Microcontrollers (Arduino, ESP32) run bare-metal or RTOS code on a single chip with minimal RAM and flash. They are used in IoT, automation, and sensor networks where cost and power are constrained.

**Commands:** `cat /proc/cpuinfo`, `pinout`

---

## Task 5: Mainframes and Supercomputers
**Purpose:** Understand enterprise-scale and high-performance computing.

**Skills:** Mainframe reliability, HPC clustering, InfiniBand interconnects.

**Theory:** Mainframes (IBM Z series) process massive transaction volumes with redundant components, hot-swap capable hardware, and nearly 100% uptime. Supercomputers aggregate thousands of nodes via high-speed interconnects like InfiniBand to perform parallel computation for simulation, weather modelling, and research.

**Commands:** (none — these are specialised environments)

---