<a name="top"></a>
# datacenter-at-home
# Enterprise-Grade Home Lab: Virtualization & Security Architecture
**Status:** Phase 1: Hardware Procurement & Network Design (In-Progress)

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

## Technical Stack
* **Hypervisor:** Proxmox VE
* **Firewall/Router:** OPNsense
* **Switching:** TP-Link TL-SG108E (L2 Managed)
* **Identity Management:** Windows Server 2022 (Active Directory)
* **Operating Systems:** Ubuntu Server, Windows 10/11 Enterprise, Kali Linux

---

## Hardware Inventory (The "Brain")
| Component | Specification | Purpose |
| :--- | :--- | :--- |
| **Host Motherboard** | MSI Z97 Guard-Pro (MS-7917) | Durable foundation with PCIe expandability. |
| **CPU** | Intel® Core™ i5-4690K | Quad-core processing for multi-VM workloads. |
| **Memory** | 32GB DDR3 1600MHz (Upgraded) | High-density RAM for concurrent VM execution. |
| **Network Card** | Intel i350-T2 Server NIC | Dual-port 1Gbps with SR-IOV & Hardware Offloading. |
| **Switch** | TP-Link TL-SG108E | 8-Port Managed Switch for 802.1Q VLAN tagging. |

---

## Logical Network Topology
*Planned architecture for the upcoming implementation:*

1.  **WAN Zone:** Raw ISP feed entering the **Intel i350 Port 1**.
2.  **Edge Security:** **OPNsense VM** acting as the primary gateway/firewall.
3.  **LAN Zone:** Protected traffic exiting **Intel i350 Port 2** to the **Managed Switch**.
4.  **VLAN Segmentation:**
    * **VLAN 10 (Management):** Proxmox GUI & Switch Interface access.
    * **VLAN 20 (Lab):** Windows Server, Active Directory, and Sandbox Workstations.
    * **VLAN 30 (Security):** IDS/IPS monitoring and Kali Linux tools.

---

## Roadmap & Milestone Tracking
- [x] **Project Scope & Requirements Gathering**
- [x] **Hardware Selection & Compatibility Audit** (MSI Z97 + Intel i350)
- [ ] **Physical Assembly & RAM Burn-in Testing** (Waiting for parts)
- [ ] **Proxmox VE Installation & Network Bridge Configuration**
- [ ] **OPNsense Deployment & Firewall Rule Hardening**
- [ ] **Active Directory Domain Controller Setup**

---

## Troubleshooting Log (Current Phase)
* **Challenge:** Determining NIC compatibility for FreeBSD-based OPNsense.
* **Solution:** Sourced a genuine Intel i350-T2 chipset due to its superior driver support (igb) and hardware offloading capabilities compared to consumer Realtek chips.

* ---
[⬆ Back to Top](#top)
## About the Author
**Mopelola Opeifa**
*Security+ Certified | GRC & Systems Engineering Enthusiast*

This lab is a live representation of my technical journey and commitment to mastering secure infrastructure. By documenting the procurement, architecture, and troubleshooting phases, I aim to provide full transparency into my technical problem-solving process.

🔗 **Connect with me:**
* www.linkedin.com/in/mopelola-opeifa-3751a0344
* https://www.credly.com/badges/4b46121e-5f1f-4d7f-8e76-55f369d38e29/public_url

---
