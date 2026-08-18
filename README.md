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
| Lenovo M910q Mini PC | Additional HomeLab node |
| Lenovo M910q Mini PC | Additional HomeLab node |
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
```

A detailed graphical network architecture diagram will be added as the project develops.

---

## 📚 Project Documentation

Detailed implementation documentation is organized into separate sections.

Completed sections are linked below, with additional documentation being added as the HomeLab develops.

1. [Proxmox Virtualization](01-proxmox/README.md) ✅
2. pfSense Firewall
3. Windows Server 2025
4. Active Directory
5. DNS
6. DHCP
7. Group Policy
8. Microsoft LAPS
9. BitLocker
10. Sysmon
11. Windows Event Forwarding
12. Backup & Recovery
13. WireGuard VPN
14. Firewall & Networking Labs

Each section will contain configuration details, screenshots, troubleshooting notes, testing procedures, and lessons learned.

---

## 🎯 Project Goals

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

## 🔧 Hands-On Learning Approach

This HomeLab is focused on practical implementation rather than theory alone.

My general learning process is:

```text
Plan
  |
  v
Deploy
  |
  v
Configure
  |
  v
Test
  |
  v
Troubleshoot
  |
  v
Document
  |
  v
Improve
```

Configuration problems and troubleshooting scenarios encountered during the project are documented because diagnosing and resolving infrastructure issues is an important part of real-world system administration.

---

## 🔐 Security & Remote Access

Security is an important part of the HomeLab design.

The environment includes technologies and practices such as:

- pfSense firewall policies
- Windows Firewall
- Microsoft LAPS
- BitLocker
- Windows Defender
- Group Policy security controls
- Security auditing
- Sysmon
- Windows Event Forwarding
- WireGuard VPN
- Secure remote HomeLab access

Management interfaces are not intentionally exposed directly to the public Internet.

Remote access to internal HomeLab resources is performed through a secure VPN connection.

---

## 💾 Backup & Recovery

Backup and recovery are included as core parts of the project.

The environment includes practical experience with:

- Proxmox backup storage
- Dedicated backup disks
- Windows Server Backup
- WBAdmin
- Backup verification
- Recovery testing
- Active Directory recovery exercises

The objective is not only to deploy infrastructure but also to understand how services and systems can be recovered following failures or accidental changes.

---

## 🔍 Monitoring & Logging

The HomeLab includes centralized monitoring and security logging exercises.

Technologies currently being tested include:

- Windows Event Forwarding (WEF)
- Windows Event Collector (WEC)
- Sysmon
- Windows Security Auditing
- Centralized event collection

Windows client security events can be forwarded to the Windows Server environment for centralized investigation and monitoring.

---

## 🚧 Project Status

🟢 **Active — Continuously Developing**

This repository will be updated as new technologies, configurations, security controls, automation scripts, and infrastructure services are added to the HomeLab.

### Current Focus

- Proxmox virtualization documentation
- pfSense networking and firewall documentation
- Windows Server 2025 administration
- Active Directory
- Group Policy
- Security monitoring
- Backup and recovery

### Future Development

Planned future areas include:

- Proxmox clustering
- VLAN segmentation
- Linux server administration
- Docker
- Infrastructure monitoring
- Centralized logging
- PowerShell automation
- Infrastructure automation
- NAS / storage services
- Additional backup solutions
- High-availability concepts

---

## ⚠️ Security Notice

All configurations and screenshots published in this repository are reviewed and sanitized before publication.

Sensitive information is not intentionally published, including:

- Passwords
- Private keys
- WireGuard private keys
- Authentication tokens
- API keys
- Recovery keys
- Private certificates
- Administrative credentials

Any configuration examples containing sensitive values will use placeholders such as:

```text
Password   = <REDACTED>
PrivateKey = <REDACTED>
Token      = <REDACTED>
```

---

## 📸 Screenshots & Documentation

Screenshots are included throughout the individual project sections to demonstrate configuration and testing.

Screenshots are reviewed before publication to avoid exposing sensitive information.

Detailed documentation can be accessed through the **Project Documentation** section above.

---

## 🧠 Skills Demonstrated

This HomeLab project demonstrates practical experience across several areas of IT infrastructure:

**Virtualization**
- Proxmox VE
- Virtual machines
- Virtual networking
- Storage management

**Windows Infrastructure**
- Windows Server 2025
- Active Directory
- DNS
- DHCP
- Group Policy
- Certificate Services

**Security**
- Microsoft LAPS
- BitLocker
- Windows Defender
- Windows Firewall
- Security auditing

**Networking**
- pfSense
- NAT
- Firewall policies
- DNS
- VPN
- WireGuard
- Remote access

**Monitoring**
- Sysmon
- Windows Event Forwarding
- Windows Event Collector
- Windows Event Logs

**Backup & Recovery**
- Proxmox backups
- Windows Server Backup
- WBAdmin
- Recovery testing

**Troubleshooting**
- Network connectivity
- DNS resolution
- Domain connectivity
- Group Policy
- Certificate services
- Event forwarding
- VPN connectivity
- Virtual machine configuration

---

## 👤 Author

**Mohamed Afham**

**IT Support Engineer | Aspiring System Administrator**

Focused on Windows Server, Active Directory, Microsoft technologies, virtualization, networking, infrastructure security, troubleshooting, and automation.

This HomeLab is maintained as a personal learning environment and technical portfolio to demonstrate hands-on infrastructure administration experience.
