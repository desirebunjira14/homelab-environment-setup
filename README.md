# homelab-environment-setup
VirtualBox installation, VM creation (DC01 + CLIENT 1)
# 🖥️ Homelab Phase 1 – Virtualization & Environment Setup

**Role alignment:** IT Support Specialist | Junior Sysadmin | Datacenter Technician | Helpdesk

**Objective:** Build a foundational virtualized Windows environment to learn hardware resource management, OS installation, and networking basics.

---

## 📦 What I Built

| VM Name       | OS                | vCPU | RAM  | Storage | Network Adapters        |
|---------------|-------------------|------|------|---------|-------------------------|
| DC01          | Windows Server 2022 | 2    | 4GB  | 2TB (thin) | NAT + Internal Network |
| CLIENT1       | Windows 10/11      | 2    | 2GB  | 128GB   | NAT only (initially)    |

- **Virtualization platform:** Oracle VirtualBox (free)
- **Host machine:** 16GB RAM, 4-core CPU, 250GB free storage

---

 ## 🎯 Skills Learned & Applied
 
 ### 1. Virtualization & Hypervisor Management:

- Created and configured VMs using VirtualBox.
- Managed vCPUs, RAM, and storage allocation.
- Set up virtual networking (NAT and Internal networks)

 ### 2. Operating System Deployment 

- Performed clean installations of Windows Server 2022 and Windows 11 from ISO files.

 ### 3. Hardware Resource Planning

- Allocated system resources (RAM, CPU, storage) based on workload requirements to optimize performance and troubleshoot bottlenecks


---

## ⚠️ Key Challenges & Workarounds

### 1. VirtualBox Guest Additions failing on Windows Server 2022
- Challenge: Screen resolution stuck at 800x600; no copy-paste or shared folders.
- Workaround: Boot into **Safe Mode** → Install Guest Additions with "Direct3D support disabled". Reboot normally → Run again in normal mode for remaining drivers.

### 2. Windows 11 VM was unusably slow
- Challenge: CLIENT1 took 10+ minutes to boot, constant freezing
- Workaround:  
  - Increase RAM from 1GB to 2GB in VM settings  
  - Close all host applications to free memory  
  - Consider reducing to 1.5GB if host struggles

### 3. Windows 11 CLIENT1 couldn’t see the domain controller
- Challenge: CLIENT1 only had NAT → no communication with DC01 on Internal Network.
- Workaround:  
  - Added a **second network adapter** to CLIENT1 → `Internal Network` (same name as DC01’s internal).  
  - This allows domain join later without exposing lab to host network.

---
