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
```
sudo pacman -S qemu-full virt-manager virt-viewer dnsmasq vde2 bridge-utils openbsd-netcat libguestfs swtpm
```

## enable libvirtd
```
sudo systemctl enable --now libvirtd
```

## Verify libvirtd Status

```
systemctl status libvirtd
```
<img width="753" height="471" alt="3" src="https://github.com/user-attachments/assets/3188fe09-3a14-4998-a852-12507cdb25ac" />

---

# Network Configuration

## Verify Default Virtual Network

```
sudo virsh net-list --all
```
<img width="229" height="69" alt="1" src="https://github.com/user-attachments/assets/03d9e5ca-d6e2-43cd-903f-14ef257ffe04" />


The default NAT network was used for communication between the host and virtual machine.

---

# Virtual Disk Setup

## Create qcow2 Disk

```
qemu-img create -f qcow2 /var/lib/libvirt/images/winserver2019.qcow2 60G
```
<img width="859" height="184" alt="5" src="https://github.com/user-attachments/assets/7895bc97-ae38-439d-9114-0cf7fc588759" />

---

# Cockpit Web Management

## Install Cockpit

```
sudo pacman -S cockpit cockpit-machines
```

---

## Enable Cockpit

```
sudo systemctl enable --now cockpit.socket
```

---

## Access Cockpit

Cockpit was accessed remotely through a web browser:

```
https://192.168.0.128:9090
```
<img width="879" height="692" alt="6" src="https://github.com/user-attachments/assets/58fe371d-b4f6-435b-b078-45b097992c8e" />

---


# VM Deployment

The virtual machine was configured with:
- 4GB RAM
- 2 vCPUs
- 60GB qcow2 disk
- Default NAT networking
- Windows Server 2019 installation ISO
  
<img width="1462" height="818" alt="8" src="https://github.com/user-attachments/assets/cc3b73ab-e5e6-4bce-8d7d-56193d9542a1" />

# Windows Server Installation

Installed:
- Windows Server 2019 Standard Evaluation (Desktop Experience)

The server was configured using:
- Static IP addressing
- DNS
- Active Directory Domain Services
<img width="1462" height="818" alt="8" src="https://github.com/user-attachments/assets/0045ff49-84e6-43f8-bcbd-939f4e5d36b2" />
<img width="1462" height="818" alt="12" src="https://github.com/user-attachments/assets/a4049939-6891-4430-b1c3-1e0ea0b6cefb" />
<img width="1462" height="818" alt="Screenshot 2026-05-12 at 8 29 18 PM" src="https://github.com/user-attachments/assets/5cda9780-9803-4871-bc41-a6ce0d064a5c" />
<img width="1462" height="818" alt="Screenshot 2026-05-12 at 8 29 34 PM" src="https://github.com/user-attachments/assets/156ed1fd-d998-4e77-9163-7618c3a286df" />
<img width="1462" height="818" alt="Screenshot 2026-05-12 at 8 35 15 PM" src="https://github.com/user-attachments/assets/68f8d653-dcdd-44ec-8921-e8ba0796e7db" />

<img width="1462" height="818" alt="Screenshot 2026-05-12 at 8 36 49 PM" src="https://github.com/user-attachments/assets/100bc9f9-3215-49e7-92aa-cc4d66bafa1a" />

---

# Static IP Configuration

| Setting | Value |
|---|---|
| IP Address | 192.168.122.10 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 192.168.122.1 |
| Preferred DNS | 127.0.0.1 |

---

# Active Directory Setup

Installed role:
- Active Directory Domain Services (AD DS)

The server was promoted into a Domain Controller using:

```text
lab.local
```

NetBIOS name:
```text
LAB
```

---

# User Management

Created test domain users through:
- Active Directory Users and Computers

Example accounts:
-Aki Bright

# Screenshots

Screenshots will be added later for:
- libvirtd service status
- active virtual network
- qcow2 disk creation
- Cockpit dashboard
- VM creation
- Windows Server installation
- static IP configuration
- Active Directory installation
- domain controller login
- created domain users

---

# Lessons Learned

- Learned how KVM/libvirt virtualization works
- Learned how virtual NAT networking functions
- Understood the importance of static IP addressing for domain controllers
- Learned how Active Directory relies on DNS
- Practiced Windows Server administration
- Improved troubleshooting skills through resolving virtualization and networking issues
- Learned the basics of identity and access management

---

# Future Improvements

- Add Windows 10/11 client VM
- Join client machine to the domain
- Configure Group Policies (GPOs)
- Add shared network folders
- Implement DHCP services
- Practice remote administration
- Add monitoring tools
- Integrate backup solutions

---

# Architecture Diagram

Architecture diagram will be added later.

Example structure:

```text
MacBook
   │
Browser / SSH
   │
Arch Linux Host
   ├── Cockpit
   ├── KVM/libvirt
   └── Windows Server 2019 VM
          ├── Active Directory
          └── DNS
```
