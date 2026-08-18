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

```
A detailed network architecture diagram will be added as the project develops.
---

### 📚 Project Documentation

Detailed implementation documentation will be organized into separate sections:

- Proxmox Virtualization
- pfSense Firewall
- Windows Server 2025
- Active Directory
- DNS
- DHCP
- Group Policy
- Microsoft LAPS
- BitLocker
- Sysmon
- Windows Event Forwarding
- Backup & Recovery
- WireGuard VPN
- Firewall & Networking Labs

Each section will contain configuration steps, screenshots, troubleshooting notes, testing procedures, and lessons learned.

---

### 🎯 Project Goals

The main goals of this HomeLab are to:

- Develop practical System Administrator skills
- Build and manage Windows enterprise infrastructure
- Improve networking and firewall knowledge
- Practice Active Directory administration
- Implement enterprise security policies
- Learn infrastructure monitoring and logging
- Practice backup and disaster recovery
- Develop PowerShell automation skills
- Troubleshoot realistic infrastructure problems
- Document technical projects professionally using GitHub

---

### 🚧 Project Status

🟢 Active — Continuously Developing

This repository will be updated as new technologies, configurations, security controls, automation scripts, and infrastructure services are added to the HomeLab.

---
### ⚠️ Security Notice

All configurations and screenshots published in this repository are sanitized before publication.

Passwords, private keys, certificates, authentication tokens, recovery keys, and other sensitive information are not included.

---
### 👤 Author

Mohamed Afham

IT Support Engineer | Aspiring System Administrator

Focused on Windows Server, Active Directory, Microsoft technologies, virtualization, networking, infrastructure security, and automation.
     +-- Event Collection
