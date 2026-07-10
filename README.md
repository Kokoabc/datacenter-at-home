<a name="top"></a>
# datacenter-at-home
# Enterprise-Grade Home Lab: Virtualization & Security Architecture
**Status:** Phase 1: Hardware Procurement & Network Design


## Project Overview
This project involves the transformation of legacy consumer hardware into a robust, enterprise-grade virtualization host. The goal is to create a secure, segmented environment to master **Systems Engineering**, **Network Security**, and **GRC** (Governance, Risk, and Compliance) frameworks.

### Objective
To simulate a corporate network environment using a Type-1 Hypervisor to host a multi-VLAN architecture, allowing for hands-on practice in firewall orchestration, identity management (Active Directory), and traffic analysis.   

---
## Table of Contents
* [Project Overview](#project-overview)
* [Technical Stack](#technical-stack)
* [Hardware Inventory](#hardware-inventory-the-brain)
* [Logical Network Topology](#logical-network-topology)
* [Roadmap and Milestone Tracking](#roadmap-and-milestone-tracking)
* [Troubleshooting Log](#troubleshooting-log)
* [About the Author](#about-the-author)

##  Technical Stack

### **Hypervisor & Core Services**
* **Hypervisor:** Proxmox VE 9.1.1 (Deployed)
* **Operating Systems:** Ubuntu 24.04 LTS (Active), Windows 10/11, Kali Linux (Planned)
* **Identity Management:** Windows Server 2022 Active Directory (Planned)
* **Networking:** OPNsense Firewall/Router (Planned)

---

### **Hardware Inventory**

| Component | Specification | Purpose |
| :--- | :--- | :--- |
| **Host Motherboard** | MSI Z97 Guard-Pro (MS-7917) | Durable foundation with PCIe expandability |
| **CPU** | Intel® Core™ i5-4690K | Quad-core processing for multi-VM workloads |
| **Memory** | 32GB DDR3 1600MHz | High-density RAM for concurrent VM execution |
| **Storage** | Hitachi & Fujitsu HDD Array | Redundant storage for VM images and backups |

---


#### **Phase 2: The Memory Overhaul**  
### Build Gallery

#### **Physical Assembly**
* **RAM Upgrade:** Successfully populated all 4 DIMM slots for a total of 32GB DDR3.
  ![32GB ram upgrade](https://github.com/user-attachments/assets/16d8a4f5-0ffd-4d5c-831a-db5f434af1a1)




* **The "Before":** Original 8GB configuration, insufficient for multi-VM workloads.
![Old 8GB ram](https://github.com/user-attachments/assets/fbc75878-2ac7-45f8-8d11-2c3b5e5ee487)




* **NIC Installation:** Installed a genuine Intel i350-T2 Server NIC.
* ![NIC card-Intel i350-T2](https://github.com/user-attachments/assets/0e53888a-bd9b-438a-84b8-73527e5be879)



> **Technical Note:** I specifically chose the Intel i350-T2 because it uses the **`igb` driver**. This provides better stability and hardware offloading for virtualization compared to standard consumer chips.
>


* **Mainboard Setup:** Preparing the MSI Z97 Guard-Pro for the first Proxmox VE boot.
* ![1st Proxmox VE boot](https://github.com/user-attachments/assets/e10e5c5a-5bce-435e-ac2f-9b6926b411de)




#### **Software Verification**
* **Ubuntu VM:** First successful boot with manual network bridging confirmed.
* ![Welcome to Ubuntu](https://github.com/user-attachments/assets/a22820ca-e408-415b-8516-50b128be3bee)

![Ubuntu Success Screenshot](Welcome-to-Ubuntu.png)
---



### **Logical Network Topology**

<img width="434" height="335" alt="Kokolab Network Diagram" src="https://github.com/user-attachments/assets/81e97235-8ae4-4135-b679-a0f332463765" />


---

### **Roadmap & Milestone Tracking**

* [x] **Phase 1:** Project Scope & Requirements Gathering
* [x] **Phase 2:** Hardware Selection & RAM Upgrades (32GB)
* [x] **Phase 3:** Physical Assembly & Proxmox VE Installation
* [x] **Phase 4:** First VM Deployment (Ubuntu 24.04)
* [ ] **Phase 5:** OPNsense Deployment & Network Hardening
* [ ] **Phase 6:** Active Directory Domain Controller Setup

---

### **Troubleshooting Log**

**1: Proxmox hypervisor network interface recovery**
Problem: The Proxmox VE node was completely inaccessible via the web GUI. Despite physical cabling, the active network interfaces reported a state of DOWN with NO-CARRIER because the default virtual bridge (vmbr0) was incorrectly bound to the inactive, onboard motherboard NIC.

Solution: Manually forced the Intel i350-T2 network interfaces into an administrative UP state via the CLI (ip link set nic2 up). Then, modified the network configuration file (/etc/network/interfaces) to re-bind the vmbr0 bridge ports to the active Intel interface, adding auto stanzas to ensure they initialize automatically on boot.

Result: Restored full network connectivity to the hypervisor host. Locked the static management IP to 192.168.1.100/24, allowing the physical monitor and keyboard to be decommissioned so the server could run in its intended headless state.

**2: Ubuntu VM initial installation network error**
Problem: During the initial setup of the Ubuntu virtual machine, the installer threw a "Connection Failed" error during the network configuration phase, failing to fetch an IP address automatically.

Solution: Bypassed the automated DHCP setup during the installation wizard and manually assigned a static IPv4 gateway inside the VM configuration, utilizing Windows internet connection sharing (ICS) from the management laptop to bridge the gap.

Result: Successfully bypassed the provisioning error, established a stable local network link, and completed the base Ubuntu operating system installation.
---

**Lessons Learned**
* **Verify Logic First:** Always verify the logical interface name mapping (`ip link`) before assuming a hardware failure.
* **Bridge Requirements:** Linux bridges (`vmbr0`) require at least one active physical port (`bridge-ports`) to allow external traffic to reach the hypervisor.

---


[⬆ Back to Top](#top)
## About the Author
**Mopelola Opeifa**
*Security+ Certified | GRC & Systems Engineering Enthusiast*

This lab is a live representation of my technical journey and commitment to mastering secure infrastructure. By documenting the procurement, architecture, and troubleshooting phases, I aim to provide full transparency into my technical problem-solving process.

🔗 **Connect with me:**
* **Certification:** https://www.credly.com/badges/4b46121e-5f1f-4d7f-8e76-55f369d38e29/public_url
* **LinkedIn:** www.linkedin.com/in/mopelola-opeifa-3751a0344


---
