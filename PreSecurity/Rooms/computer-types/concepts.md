# Concepts: Computer Types

## 1. Desktop Modularity
Desktops use standardised form factors (ATX, microATX, Mini-ITX) and sockets (LGA, PGA) that allow swapping CPUs, GPUs, RAM, and storage independently. This modularity enables customisation and incremental upgrades but results in a larger physical footprint than all-in-one or mobile designs.

## 2. Server Rack Form Factors
Servers are mounted in standard 19-inch racks with height measured in rack units (1U = 1.75 inches). Dense configurations (1U, 2U) maximise compute per rack space. Blade servers further increase density by sharing chassis-level power, cooling, and networking across multiple server modules.

## 3. ECC Memory
Error-Correcting Code memory detects and corrects single-bit memory errors automatically. It is critical in servers and workstations where undetected memory corruption could lead to data loss, financial errors, or inaccurate scientific results. Consumer hardware typically uses non-ECC memory.

## 4. IPMI and Out-of-Band Management
The Intelligent Platform Management Interface enables administrators to monitor and control servers even when the OS is offline — via remote console, power cycling, and sensor monitoring (temperature, fan speed, voltage). It runs on a dedicated BMC (Baseboard Management Controller) with its own network connection.

## 5. SoC (System on a Chip)
An SoC integrates CPU, GPU, memory controller, I/O, and often RAM onto a single chip. Common in smartphones (Snapdragon, Apple A-series) and embedded systems (Raspberry Pi BCM2711), SoCs offer high power efficiency and compact footprints essential in portable and embedded applications.

## 6. Microcontroller Architecture
Microcontrollers combine a processor core, RAM, flash storage, and I/O peripherals on a single chip. They lack the resources to run a full OS and instead execute bare-metal firmware or real-time operating systems (RTOS). They are ideal for simple, low-power, dedicated tasks in embedded systems.

## 7. HPC and Supercomputing
Supercomputers comprise thousands of nodes connected by high-speed interconnects (InfiniBand, Omni-Path) to solve massively parallel problems. They rely on MPI (Message Passing Interface) for inter-node communication and specialised job schedulers (SLURM, PBS) to allocate resources across the cluster.