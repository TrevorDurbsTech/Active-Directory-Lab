# Windows Server Installation

## Objective

The objective of this phase was to build the foundation of the Active Directory lab by deploying a Windows Server 2022 virtual machine. This server functions as the primary Domain Controller (DC01) and provides Active Directory Domain Services (AD DS), DNS, and DHCP for the lab environment.

---

## Environment

| Component | Configuration |
| ----------------------- | ------------------------------------------------------------ |
| Host Operating System | Windows 11 |
| Virtualization Platform | Oracle VirtualBox |
| Guest Operating System | Windows Server 2022 Standard Evaluation (Desktop Experience) |
| VM Name | DC01 |
| Memory | 4 GB |
| Processors | 3 vCPUs |
| Storage | 60 GB Dynamically Allocated VDI |

---

## Virtual Machine Configuration

The Windows Server virtual machine was created in Oracle VirtualBox and configured with resources suitable for running a small enterprise Active Directory environment. The configuration balances performance with efficient use of the host system's resources while leaving room to add additional virtual machines later in the project.

![VirtualBox VM Settings](../screenshots/vm-settings.png)

**Figure 1.** Oracle VirtualBox configuration for the DC01 virtual machine.

---

## Installation Process

1. Downloaded the Windows Server 2022 Evaluation ISO from Microsoft.
2. Created a new virtual machine named **DC01** in Oracle VirtualBox.
3. Configured the virtual machine with:
   - 4 GB RAM
   - 3 virtual processors
   - 60 GB dynamically allocated virtual disk
4. Installed **Windows Server 2022 Standard Evaluation (Desktop Experience)**.
5. Created the local Administrator password.
6. Logged into Windows Server and verified the installation.

---

## Initial Configuration

After installation, the following configuration tasks were completed:

- Renamed the server to **DC01**
- Configured a static IP address
- Verified network connectivity
- Installed all available Windows Updates
- Installed the Active Directory Domain Services (AD DS) role
- Promoted the server to the first Domain Controller for the **trevortech.local** domain

---

## Networking

The virtual machine uses two network adapters.

### LAN Adapter

- **Type:** Bridged Adapter
- **Purpose:** Provides management access from the home network and internet connectivity.
- **IP Address:** 192.168.50.50

### LAB Adapter

- **Type:** Host-Only Adapter
- **Purpose:** Provides an isolated network for domain clients and Active Directory services.
- **IP Address:** 192.168.56.10

Using separate network adapters isolates the lab environment from the home network while still allowing administrative access to the domain controller.

---

## Validation

The following checks were completed after installation:

- Successfully logged into Windows Server.
- Verified static IP configuration using `ipconfig`.
- Confirmed connectivity to the home router.
- Confirmed internet connectivity.
- Verified Active Directory installation.
- Verified successful promotion of the server to a Domain Controller.
- Confirmed both the Bridged and Host-Only network adapters were configured correctly.

---

## Lessons Learned

Creating a dual-network architecture early in the project provides a safer and more realistic lab environment. The Bridged Adapter allows remote management and internet connectivity, while the Host-Only Adapter creates an isolated network where services such as DHCP, DNS, and Active Directory can be tested without affecting devices on the home network.
