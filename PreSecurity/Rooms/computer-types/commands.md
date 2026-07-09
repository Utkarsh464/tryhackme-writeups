# Commands: Computer Types

## Hardware Information

| Command | Description |
|---------|-------------|
| `sudo dmidecode -t system` | Show system manufacturer and form factor |
| `lspci -w` | List PCI devices with config space details |
| `ipmitool sensor list` | View IPMI sensor readings (temp, voltage, fan) |
| `dmidecode -t memory` | Show installed memory modules and ECC status |
| `lscpu | grep "Core(socket)"` | Count cores per socket in the system |
| `cat /proc/cpuinfo` | Full CPU information per logical core |
| `pinout` | Raspberry Pi GPIO pinout diagram |
| `nvidia-smi -q` | Detailed GPU query including memory and ECC |