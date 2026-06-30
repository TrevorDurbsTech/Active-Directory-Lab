# Active Directory Home Lab – trevortech.local

## Overview

This project is a hands-on Active Directory home lab built using Oracle VirtualBox. The goal was to simulate a small enterprise environment by deploying a Windows Server 2022 Domain Controller and connecting a Windows 11 client machine to a centralized domain.

This lab demonstrates core Windows Server administration skills including Active Directory setup, DNS, DHCP, and domain-joined client management.

---

## Project Goals

* Build a working Active Directory environment from scratch
* Configure Windows Server 2022 as a Domain Controller
* Deploy DNS and DHCP services
* Create and manage domain users and Organizational Units (OUs)
* Join a Windows 11 client to the domain
* Simulate a basic enterprise network environment

---

## Lab Architecture

```
                +----------------------+
                |   DC01 (Server 2022) |
                |  192.168.108.10      |
                |  AD DS / DNS / DHCP  |
                +----------+-----------+
                           |
            -------------------------------
                           |
                +----------------------+
                |   CLIENT01 (Win11)   |
                |  192.168.108.101     |
                |  Domain Joined       |
                +----------------------+
```

---

## Environment

| Component    | Configuration                            |
| ------------ | ---------------------------------------- |
| Hypervisor   | Oracle VirtualBox                        |
| Domain Name  | trevortech.local                         |
| Server OS    | Windows Server 2022 (Desktop Experience) |
| Client OS    | Windows 11 Pro                           |
| Network Type | Host-Only Adapter                        |
| Subnet       | 192.168.108.0/24                         |

---

## Key Components

### 🖧 Domain Controller (DC01)

* Windows Server 2022
* Active Directory Domain Services (AD DS)
* DNS Server
* DHCP Server
* Static IP: `192.168.108.10`

### Client Machine (CLIENT01)

* Windows 11 Pro
* DHCP-assigned IP: `192.168.108.101`
* DNS pointed to DC01
* Joined to domain `trevortech.local`

---

## What Was Built

### 1. Domain Controller Setup

* Installed Windows Server 2022
* Configured static IP addressing
* Installed AD DS, DNS, and DHCP roles
* Promoted server to Domain Controller
* Created domain: `trevortech.local`

---

### 2. Active Directory Configuration

* Created Organizational Units (OUs):
  
  * IT
  * Created test domain user (`luffytech`)

---

### 3. Client Deployment (CLIENT01)

* Installed Windows 11 Pro on VirtualBox
* Bypassed hardware requirements (TPM/Secure Boot checks)
* Bypassed OOBE internet requirement
* Configured DHCP networking from DC01
* Joined domain successfully
* Logged in using domain credentials

---

## Key Skills Demonstrated

* Windows Server administration
* Active Directory domain configuration
* DNS and DHCP troubleshooting
* Windows 11 client setup in enterprise environment
* Network configuration in isolated lab environments
* Domain join and authentication process

---

## How the Lab Works

1. DC01 provides:

   * Active Directory authentication
   * DNS name resolution
   * DHCP IP address assignment

2. CLIENT01:

   * Receives IP configuration via DHCP
   * Uses DC01 for DNS resolution
   * Authenticates against Active Directory
   * Logs in using domain credentials

---

## 📸 Screenshots

*(Add your screenshots here)*

* VirtualBox VM configuration
* `ipconfig /all` output from CLIENT01
* Active Directory Users and Computers
* Domain join confirmation screen
* Successful domain login

---

## Lessons Learned

This project reinforced how tightly integrated Active Directory, DNS, and DHCP are in a real Windows domain environment. Even when the network is technically working, small misconfigurations in DNS can prevent domain joins entirely.

Building the lab from scratch also helped me better understand how enterprise environments are structured.
---

## Future Improvements

* Add Group Policy Objects (GPOs)
* Create user login scripts
* Add file sharing and permissions lab
* Deploy additional client machines
* Implement Windows Server hardening practices

---

## Author

**Trevor Durbin**

---

