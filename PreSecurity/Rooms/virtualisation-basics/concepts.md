# Concepts: Virtualisation Basics

## 1. Hypervisor
A hypervisor (or virtual machine monitor) is software that creates and manages virtual machines by abstracting the host's physical hardware resources into isolated virtual resources. It manages VM lifecycle, allocates hardware resources, and enforces isolation between VMs on the same host.

## 2. Type 1 (Bare-Metal) Hypervisor
Runs directly on the host hardware without an underlying operating system. It owns and manages hardware resources directly, offering greater performance, security, and scalability. Examples: VMware ESXi, Microsoft Hyper-V, KVM. Used in enterprise data centres and cloud providers.

## 3. Type 2 (Hosted) Hypervisor
Runs as a software application on top of a conventional OS. The host OS manages hardware, and the hypervisor translates guest OS calls to host system calls. Slower than Type 1 due to this extra layer. Used for personal labs, development, and testing. Examples: VirtualBox, VMware Workstation.

## 4. Virtual Machine Components
VMs consist of virtualised CPU (vCPU cores/threads mapped to physical), virtual RAM allocated from host memory, virtual disks stored as image files (VMDK, VHD, QCOW2), and virtual NICs connected to virtual switches. These components are defined in the VM configuration and managed by the hypervisor.

## 5. Resource Oversubscription
Allocating more total virtual resources to VMs than physically available on the host. For example, assigning 4 vCPUs each to 4 VMs on a 4-core 8-thread host. The hypervisor time-slices physical resources across VMs. Oversubscription increases utilisation but requires careful monitoring to avoid performance degradation.

## 6. VM Snapshots
A snapshot preserves a VM's state (disk contents and optionally memory) at a specific point in time. Snapshots enable quick rollback after software installation, configuration changes, or security testing. However, large snapshot chains degrade write performance and should not be used as long-term backups.

## 7. Isolation and Security
Each VM operates in its own isolated environment with separate memory, storage, and process space. A breach of isolation (VM escape) allows a guest to access the hypervisor or other VMs — one of the most critical virtualisation security threats. Proper hypervisor patching and configuration mitigates this risk.

## 8. Virtual Networking
VMs connect to virtual networks through virtual switches (vSwitch). Common modes include bridged (VM appears as a separate device on the physical network), NAT (shared host IP), and host-only (isolated between VMs and host). Each provides different connectivity and security properties.