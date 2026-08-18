# 🏠 Enterprise HomeLab

> A hands-on enterprise-style IT infrastructure lab built to develop and demonstrate practical skills in system administration, virtualization, networking, security, monitoring, and disaster recovery.

## 📌 Project Overview

This HomeLab is designed to simulate a small enterprise IT environment where I can deploy, configure, secure, monitor, troubleshoot, and maintain real-world infrastructure technologies.

The environment is built primarily on **Proxmox VE** and includes **pfSense**, **Windows Server 2025**, **Windows 11**, **Active Directory Domain Services**, **DNS**, **DHCP**, **Group Policy**, **WireGuard VPN**, security monitoring, and backup/recovery solutions.

Rather than only studying these technologies theoretically, this project allows me to gain hands-on experience implementing and troubleshooting them in a working environment.

---

## 🖥️ Lab Infrastructure

### Physical Hardware

| Device | Role |
|---|---|
| Lenovo M720t Tower | Primary Proxmox virtualization host |
| Lenovo M910q Mini PC | Proxmox Node 2 |
| Lenovo M910q Mini PC | Proxmox Node 3 |
| Managed Network Switch | Lab network connectivity |
| Additional HDD Storage | Backups and storage |

---

## 🛠️ Technologies & Skills

### Virtualization
- Proxmox VE
- Virtual Machines
- Virtual networking
- VM storage and backups

### Windows Server
- Windows Server 2025
- Active Directory Domain Services (AD DS)
- DNS
- DHCP
- Group Policy
- Certificate Services
- Windows Server Backup

### Security
- Microsoft LAPS
- BitLocker
- Windows Defender
- Windows Firewall
- Sysmon
- Windows Event Forwarding (WEF)
- Security auditing

### Networking
- pfSense Firewall
- Firewall rules
- NAT
- Network aliases
- Dynamic DNS
- Internal DNS
- WireGuard VPN
- Secure remote access

### Client Management
- Windows 11
- Active Directory domain join
- Group Policy deployment
- Remote Desktop
- Centralized security policies

---

## 🏗️ Current Lab Architecture

```text
                         Internet
                            |
                       ISP Router
                            |
                      Managed Switch
                            |
          +-----------------+-----------------+
          |                 |                 |
      Proxmox-01        Proxmox-02        Proxmox-03
          |
       pfSense
       Firewall
          |
       Lab Network
          |
     +----+---------------------+
     |                          |
Windows Server 2025        Windows 11 Client
     |
     +-- Active Directory
     +-- DNS
     +-- DHCP
     +-- Group Policy
     +-- Certificate Services
     +-- LAPS
     +-- Event Collection
