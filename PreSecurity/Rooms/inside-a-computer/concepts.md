# Concepts: Inside a Computer

## 1. CPU Architecture
The CPU is the brain of the computer, executing program instructions. It contains multiple cores for parallel processing, operates at a clock speed measured in GHz, and uses cache memory (L1 fastest/smallest, L2, L3 larger/slower) to reduce latency accessing frequently used data.

## 2. Instruction Set Architectures (ISA)
x86 (Intel/AMD) is a Complex Instruction Set Computer (CISC) architecture dominant in desktops and servers. ARM is a Reduced Instruction Set Computer (RISC) architecture dominant in mobile devices due to its power efficiency. The ISA determines software compatibility and performance characteristics.

## 3. Volatile vs Non-Volatile Memory
RAM is volatile — it loses data when power is removed. This makes it suitable for active workloads but requires saving to persistent storage. Non-volatile storage (SSD, HDD) retains data across reboots. Understanding this distinction is critical for data recovery and forensics.

## 4. Virtual Memory and Swapping
When physical RAM is exhausted, the operating system uses a swap file (Linux) or pagefile (Windows) on disk as overflow memory. The kernel manages paging — moving data pages between RAM and disk. Excessive swapping (thrashing) severely degrades performance.

## 5. SSD vs HDD Performance
HDDs rely on spinning magnetic platters and read/write heads (latency ~5–10 ms). SSDs use NAND flash with no moving parts (latency ~0.1 ms). NVMe SSDs connect over PCIe for throughput of several GB/s, while SATA SSDs are limited to ~550 MB/s by the SATA interface.

## 6. PCIe Lanes
Peripheral Component Interconnect Express (PCIe) provides a point-to-point serial connection between devices and the CPU/chipset. Lanes (x1, x4, x8, x16) determine bandwidth. GPUs use x16 slots, NVMe drives use x4. Limited lane count on CPUs/chipsets constrains expandability.

## 7. GPU Parallel Processing
GPUs contain thousands of small cores optimised for parallel floating-point computations, unlike CPUs which have fewer but more powerful cores. NVIDIA's CUDA and AMD's ROCm enable general-purpose GPU computing for machine learning, scientific simulation, and rendering.

## 8. Motherboard Chipset
The chipset manages communication between the CPU, memory, storage, and peripherals. Modern platforms split into a Platform Controller Hub (PCH) which handles I/O, while the CPU directly handles memory and PCIe. The chipset determines available ports, expansion, and overclocking support.