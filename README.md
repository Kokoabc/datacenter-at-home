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

![Installing the RAM](32GB-ram-upgrade.jpg)



* **The "Before":** Original 8GB configuration, insufficient for multi-VM workloads.
![Old 8GB ram](https://github.com/user-attachments/assets/fbc75878-2ac7-45f8-8d11-2c3b5e5ee487)

![Old 8GB RAM](Old-8GB-ram.jpg)   



* **NIC Installation:** Installed a genuine Intel i350-T2 Server NIC.
* ![NIC card-Intel i350-T2](https://github.com/user-attachments/assets/0e53888a-bd9b-438a-84b8-73527e5be879)

![Intel i350-T2 NIC Installation](NIC-card-Intel-i350-T2.jpg)

> **Technical Note:** I specifically chose the Intel i350-T2 because it uses the **`igb` driver**. This provides better stability and hardware offloading for virtualization compared to standard consumer chips.
>


* **Mainboard Setup:** Preparing the MSI Z97 Guard-Pro for the first Proxmox VE boot.
* ![1st Proxmox VE boot](https://github.com/user-attachments/assets/e10e5c5a-5bce-435e-ac2f-9b6926b411de)

![MSI Motherboard Setup](1st-Proxmox-VE-boot.jpg)



#### **Software Verification**
* **Ubuntu VM:** First successful boot with manual network bridging confirmed.
* ![Welcome to Ubuntu](https://github.com/user-attachments/assets/a22820ca-e408-415b-8516-50b128be3bee)

![Ubuntu Success Screenshot](Welcome-to-Ubuntu.png)
---



### **Logical Network Topology**

* **WAN Zone:** Raw ISP feed entering the laptop via Wi-Fi and bridged to the Lab PC.
* **Management:** Proxmox GUI & SSH access via static IP `192.168.1.100`.
* **VLAN 20 (Sandbox):** Primary Ubuntu VM with manual network configuration.

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

**Challenge:** Ubuntu VM initial installation "Connection Failed" error during network setup.

**Solution:** Bypassed DHCP during installation; configured Windows Internet Connection Sharing (ICS) on the laptop and assigned a manual IPv4 gateway inside the VM.

**Hardware Insight:** Verified the **Intel i350-T2** was correctly identified by the Proxmox kernel using the `igb` driver, ensuring the physical link was stable even when the software configuration required manual intervention.

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
