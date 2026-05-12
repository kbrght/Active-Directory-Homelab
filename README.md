# Active-Directory-Homelab
Windows Server 2019 Active Directory homelab using KVM/libvirt and Cockpit on Arch Linux.


-----------------------------------------------------------------------------------
## Overview

This project is a Windows Server 2019 Active Directory homelab running on an Arch Linux host using KVM/libvirt virtualization and Cockpit web management.

The goal of this project is to practice:
- Virtualization
- Windows Server administration
- Active Directory Domain Services
- DNS configuration
- Static networking
- User management
- Infrastructure troubleshooting

---

#Environment

## Host Machine

| Component           | Details |
|---|---|
| Operating System    | Arch Linux |
| CPU                 | AMD A8-7300|
| RAM                 | 8GB |
| Virtualization      | KVM/libvirt |
| VM Management       | Cockpit |

---

## Guest Virtual Machine

| Component           | Details |
|---|---|
| Operating System    | Windows Server 2019 Standard Evaluation |
| Installation Type   | Desktop Experience |
| RAM                 | 4GB |
| CPU                 | 2 vCPUs |
| Disk                | 60GB qcow2 |
| Network             | Default NAT |

---

# Technologies Used

- KVM
- QEMU
- libvirt
- Cockpit
- Windows Server 2019
- Active Directory Domain Services
- DNS
- NAT Networking

---

#Project Goals

- Learn virtualization concepts
- Deploy and manage Windows Server virtual machines
- Configure Active Directory Domain Services
- Practice DNS and networking concepts
- Understand domain controller deployment
- Practice user and identity management
- Improve troubleshooting skills

---

# Virtualization Setup

## Verify Virtualization Support
``` 
egrep -c '(vmx|svm)' /proc/cpuinfo
```
## Install Virtualization Packages
