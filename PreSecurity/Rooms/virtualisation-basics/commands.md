# Commands: Virtualisation Basics

## KVM/libvirt Management

| Command | Description |
|---------|-------------|
| `virsh list --all` | List all VMs (running and stopped) |
| `virsh nodeinfo` | Show hypervisor node information |
| `virsh dominfo vm-name` | Detailed info about a specific VM |
| `virsh snapshot-create-as vm-name snap1` | Create a VM snapshot |
| `virsh snapshot-list vm-name` | List snapshots for a VM |
| `virsh start vm-name` | Start a stopped VM |
| `virsh shutdown vm-name` | Gracefully shut down a VM |
| `systemctl status libvirtd` | Check KVM/libvirt daemon status |
| `kvm-ok` | Check if the CPU supports hardware virtualisation |

## VirtualBox Management

| Command | Description |
|---------|-------------|
| `VBoxManage list vms` | List all registered VirtualBox VMs |
| `VBoxManage list runningvms` | List running VMs |
| `VBoxManage startvm "VM1" --type headless` | Start VM headless (no GUI) |
| `VBoxManage snapshot "VM1" take "snap1"` | Create a snapshot |
| `VBoxManage snapshot "VM1" restore "snap1"` | Restore a snapshot |
| `VBoxManage controlvm "VM1" poweroff` | Power off a VM |

## General

| Command | Description |
|---------|-------------|
| `virt-manager` | GUI Virtual Machine Manager for libvirt |
| `ls /dev/kvm` | Verify KVM kernel module is loaded |
| `cat /proc/cpuinfo | grep -E "vmx|svm"` | Check CPU virtualization features |