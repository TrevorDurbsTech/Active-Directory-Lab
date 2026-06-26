# Windows Server Installation

## Objective

The objective of this phase was to build the foundation of the Active Directory lab by deploying a Windows Server 2022 virtual machine. This server will function as the primary Domain Controller (DC01) and will provide Active Directory Domain Services (AD DS), DNS, and DHCP for the lab environment.

---

## Environment

| Component               | Configuration                                                |
| ----------------------- | ------------------------------------------------------------ |
| Host Operating System   | Windows 11                                                   |
| Virtualization Platform | Oracle VirtualBox                                            |
| Guest Operating System  | Windows Server 2022 Standard Evaluation (Desktop Experience) |
| VM Name                 | DC01                                                         |
| Memory                  | 4 GB                                                         |
| Processors              | 2 vCPUs                                                      |
| Storage                 | 60 GB Dynamically Allocated VDI                              |

---

## Installation Process

1. Downloaded the Windows Server 2022 Evaluation ISO from Microsoft.
2. Created a new virtual machine named **DC01** in Oracle VirtualBox.
3. Configured the virtual machine with:

   * 4 GB RAM
   * 3 virtual processors
   * 60 GB dynamically allocated virtual disk
4. Installed **Windows Server 2022 Standard Evaluation (Desktop Experience)**.
5. Created the local Administrator password.
6. Logged into Windows Server and verified the installation.

---

## Initial Configuration

After installation, the following configuration tasks were completed:

* Renamed the server to **DC01**
* Configured a static IP address
* Verified network connectivity
* Installed all available Windows Updates
* Installed the Active Directory Domain Services (AD DS) role
* Promoted the server to the first Domain Controller for the **trevortech.local** domain

---

## Networking

The virtual machine uses two network adapters.

### LAN Adapter

* Type: Bridged Adapter
* Purpose: Management access from the home network and remote administration.
* IP Address: 192.168.50.50

### LAB Adapter

* Type: Host-Only Adapter
* Purpose: Private network for domain clients and Active Directory services.
* IP Address: 192.168.56.10

This design isolates the lab environment from the home network while still allowing administrative access to the server.

---

## Validation

The following checks were completed after installation:

* Successfully logged into Windows Server.
* Verified static IP configuration using `ipconfig`.
* Confirmed connectivity to the home router.
* Confirmed internet connectivity.
* Verified Active Directory installation.
* Verified successful domain controller promotion.

---

## Lessons Learned

A dual-network design provides a safer and more realistic enterprise environment than placing all lab systems directly on the home network. Using a dedicated Host-Only network allows services such as DHCP to be deployed without affecting other devices while the Bridged adapter provides convenient management access.

