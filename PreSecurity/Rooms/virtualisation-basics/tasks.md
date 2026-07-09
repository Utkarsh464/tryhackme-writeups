# Tasks: Virtualisation Basics

## Task 1: What is Virtualisation?
**Purpose:** Define virtualisation and its benefits for resource utilisation.

**Skills:** Understanding hardware abstraction, multi-tenancy, efficiency.

**Theory:** Virtualisation uses a hypervisor to abstract physical hardware (CPU, RAM, storage, networking) into virtual resources. Multiple VMs run isolated on one host, each with its own OS and applications. This improves hardware utilisation, enables server consolidation, and provides isolation between workloads.

**Commands:** `systemctl status libvirtd`, `kvm-ok`

---

## Task 2: Type 1 Hypervisors
**Purpose:** Understand bare-metal hypervisors running directly on hardware.

**Skills:** VMware ESXi, Hyper-V, KVM architecture.

**Theory:** Type 1 hypervisors run directly on physical hardware without a host OS. They offer near-native performance and enterprise features like live migration, high availability, and centralised management. VMware ESXi, Microsoft Hyper-V, and KVM (Linux) are the dominant Type 1 hypervisors.

**Commands:** `virsh list --all`, `virsh nodeinfo`

---

## Task 3: Type 2 Hypervisors
**Purpose:** Describe hosted hypervisors running on a conventional OS.

**Skills:** VirtualBox, VMware Workstation.

**Theory:** Type 2 hypervisors run as applications on top of a host OS. They are typically used for development, testing, and training environments. While they are easier to set up than Type 1, they introduce additional overhead because each VM access must go through both the hypervisor and the host OS.

**Commands:** `VBoxManage list vms`, `VBoxManage startvm "VM Name" --type headless`

---

## Task 4: VM Components and Resource Allocation
**Purpose:** Identify the components that comprise a virtual machine.

**Skills:** vCPU, vRAM, vDisk, virtual NIC, host vs guest resources.

**Theory:** Each VM includes virtual CPU cores (vCPU) mapped to physical cores or threads, virtual RAM (vRAM) allocated from host memory, a virtual disk (vDisk) stored as a file image, and one or more virtual NICs for network connectivity. The hypervisor allocates and translates these virtual resources to physical hardware transparently.

**Commands:** `virt-manager`, `virsh dominfo vm-name`

---

## Task 5: Snapshots and Isolation
**Purpose:** Learn how snapshots preserve VM state and isolation protects tenants.

**Skills:** Snapshotting for recovery, VM escape attacks, resource isolation.

**Theory:** Snapshots capture the entire state of a VM (disk, RAM) at a point in time, enabling rapid rollback after changes or incidents. Isolation ensures one VM cannot access another VM's memory or storage — a critical security property. VM escape attacks exploit hypervisor bugs to break this isolation.

**Commands:** `virsh snapshot-create-as vm-name snap1`, `VBoxManage snapshot "VM1" take "snap1"`

---