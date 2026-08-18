# 🏠 Enterprise HomeLab

> A hands-on enterprise-style IT infrastructure lab built to develop and demonstrate practical skills in system administration, virtualization, networking, security, monitoring, automation, and disaster recovery.

---

## 📌 Project Overview

This HomeLab is designed to simulate a small enterprise IT environment where I can deploy, configure, secure, monitor, troubleshoot, automate, and maintain real-world infrastructure technologies.

The environment is built around **Proxmox VE** and currently includes:

* pfSense Firewall
* Windows Server 2025
* Windows 11 Enterprise client
* Active Directory Domain Services
* DNS
* DHCP
* Group Policy
* Microsoft LAPS
* BitLocker
* Windows Defender
* Windows Firewall
* Sysmon
* Windows Event Forwarding
* Windows Server Backup
* WireGuard VPN
* Enterprise security policies
* Centralized administration and monitoring

The project will continue expanding into:

* Linux administration
* Docker and containerization
* Storage and file services
* Infrastructure monitoring
* SIEM and security monitoring
* PowerShell and Linux automation
* Advanced networking
* High availability
* Backup and disaster recovery

Rather than only studying these technologies theoretically, this HomeLab provides a practical environment where I can implement, test, break, troubleshoot, recover, and document infrastructure in a way that reflects real-world System Administrator responsibilities.

---

# 🖥️ Lab Infrastructure

## Physical Hardware

| Device                 | Role                                  |
| ---------------------- | ------------------------------------- |
| Lenovo M720t Tower     | Primary Proxmox virtualization host   |
| Lenovo M910q Mini PC   | Additional HomeLab node               |
| Lenovo M910q Mini PC   | Additional HomeLab node               |
| Managed Network Switch | Lab network connectivity              |
| Additional HDD Storage | Backups, storage, and future services |

The environment is designed to grow into a multi-node infrastructure lab supporting virtualization, networking, Windows and Linux administration, monitoring, storage, security, and automation.

---

# 🛠️ Technologies & Skills

## 🖥️ Virtualization

* Proxmox VE
* Virtual Machines
* Virtual networking
* Linux bridges
* VM storage
* Backup storage
* Virtual hardware configuration
* VirtIO drivers
* VM troubleshooting
* Multi-node infrastructure

## 🪟 Windows Infrastructure

* Windows Server 2025
* Windows 11
* Active Directory Domain Services
* DNS
* DHCP
* Group Policy
* Certificate Services
* Microsoft LAPS
* BitLocker
* Windows Defender
* Windows Firewall
* Windows Server Backup
* Remote Desktop
* PowerShell administration

## 🌐 Networking

* pfSense Firewall
* WAN/LAN configuration
* Firewall rules
* NAT
* Network aliases
* DNS
* DHCP
* Dynamic DNS
* Internal DNS
* Network troubleshooting
* WireGuard VPN
* Secure remote access

## 🔐 Security

* Microsoft LAPS
* BitLocker
* Windows Defender
* Windows Firewall
* Group Policy security controls
* Security auditing
* Sysmon
* Windows Event Forwarding
* Windows Event Collector
* Account security
* Privileged administration
* Enterprise security policies

## 🐧 Linux — Planned

* Linux server administration
* Ubuntu Server
* Debian
* User and group management
* Linux permissions
* SSH
* Networking
* Storage and filesystems
* Package management
* systemd
* Scheduled tasks
* Logging
* Firewall administration
* Security hardening
* Samba
* Linux/Active Directory integration
* Shell scripting

## 📦 Containers — Planned

* Docker
* Docker Compose
* Container networking
* Persistent storage
* Container security
* Application deployment
* Service management

## 📊 Monitoring — Planned / In Development

* Sysmon
* Windows Event Forwarding
* Windows Event Collector
* Infrastructure monitoring
* Centralized logging
* Performance monitoring
* Alerting
* SIEM integration

## ⚙️ Automation — Planned

* PowerShell
* Bash
* Active Directory automation
* User provisioning
* Server administration automation
* Scheduled administration tasks
* Infrastructure automation

---

# 🏗️ Current Lab Architecture

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
     +----+-------------------------+
     |                              |
Windows Server 2025            Windows 11 Client
     |
     +-- Active Directory
     +-- DNS
     +-- DHCP
     +-- Group Policy
     +-- Certificate Services
     +-- Microsoft LAPS
     +-- BitLocker Management
     +-- Windows Security Policies
     +-- Sysmon
     +-- Windows Event Collection
     +-- Backup & Recovery
```

The architecture will continue evolving as Linux servers, containers, storage services, monitoring platforms, security tools, and additional infrastructure components are introduced.

---

# 📚 Project Documentation

Detailed implementation documentation is organized by **major infrastructure technology and administration domain**.

Individual technologies such as DNS, DHCP, Group Policy, LAPS, BitLocker, Sysmon, Windows Event Forwarding, and Windows Server Backup are documented within their relevant major infrastructure sections instead of being treated as separate top-level projects.

This keeps the repository scalable as the HomeLab expands into Windows, Linux, networking, containers, security, storage, monitoring, automation, and high availability.

## Current & Planned Modules

### 01 — Proxmox Virtualization ✅

Hands-on virtualization infrastructure including:

* Proxmox VE installation
* Host configuration
* Storage configuration
* Network bridges
* VM creation
* Virtual hardware
* Backup storage
* VM management
* Troubleshooting

📁 [`01-proxmox`](./01-proxmox/)

---

### 02 — pfSense Firewall ✅

Enterprise-style firewall and network administration including:

* pfSense deployment
* WAN/LAN configuration
* Firewall rules
* NAT
* Network aliases
* DNS configuration
* Dynamic DNS
* WireGuard VPN
* Remote HomeLab access
* Firewall troubleshooting

📁 [`02-pfsense`](./02-pfsense/)

---

### 03 — Windows Server 2025 ✅

Windows Server infrastructure deployment and administration.

Topics include:

* Windows Server 2025 installation
* Server configuration
* Static networking
* Server roles and features
* DNS
* DHCP
* Group Policy
* Certificate Services
* Microsoft LAPS
* BitLocker
* Windows Defender
* Windows Firewall
* Sysmon
* Windows Event Forwarding
* Windows Event Collector
* Remote Desktop
* Windows Server Backup
* WBAdmin
* Security policies
* Server troubleshooting

📁 [`03-windows-server-2025`](./03-windows-server-2025/)

---

### 04 — Active Directory ✅

Dedicated Active Directory administration lab.

Topics include:

* Active Directory Domain Services
* Domain Controller configuration
* Organizational Unit design
* User administration
* Group administration
* AGDLP
* Administrative accounts
* Delegation of Control
* Password policies
* Fine-Grained Password Policies
* Active Directory Sites and Services
* FSMO roles
* AD health validation
* DNS validation
* Active Directory Recycle Bin
* Group Managed Service Accounts
* PowerShell administration
* Active Directory troubleshooting

Future expansion will include:

* Additional Domain Controllers
* Active Directory replication
* Domain Controller failure testing
* AD backup and recovery
* Advanced delegation
* AD security hardening

📁 [`04-active-directory`](./04-active-directory/)

---

### 05 — Linux Administration 🔜

The next major HomeLab learning track will introduce Linux system administration.

Planned topics:

* Linux installation
* Ubuntu Server
* Debian
* Linux filesystem
* Users and groups
* File ownership
* Linux permissions
* sudo administration
* Package management
* Linux networking
* Static IP configuration
* DNS configuration
* SSH
* Storage and filesystems
* Mounting disks
* systemd
* Services
* Process management
* Cron jobs
* Logging
* Linux firewall
* Security hardening
* Samba
* Linux troubleshooting
* Bash scripting
* Linux integration with Active Directory

📁 `05-linux-administration/` — Planned

---

### 06 — Docker & Containers 🔜

Planned container administration lab covering:

* Docker installation
* Images
* Containers
* Volumes
* Networks
* Docker Compose
* Persistent storage
* Container security
* Application deployment
* Container troubleshooting
* Multi-container services

📁 `06-docker-containers/` — Planned

---

### 07 — Storage & File Services 🔜

Planned enterprise storage exercises including:

* File servers
* SMB
* Samba
* NTFS permissions
* Share permissions
* AGDLP access control
* Storage management
* NAS
* Network shares
* Disk management
* Quotas
* Storage monitoring
* Media storage

📁 `07-storage-file-services/` — Planned

---

### 08 — Monitoring & Observability 🔜

Planned infrastructure monitoring environment.

Topics may include:

* Server monitoring
* Network monitoring
* CPU monitoring
* Memory monitoring
* Disk monitoring
* Service availability
* Centralized logging
* Dashboards
* Alerting
* Windows Event monitoring
* Linux logging
* Infrastructure health monitoring

📁 `08-monitoring-observability/` — Planned

---

### 09 — Security & SIEM 🔜

Dedicated infrastructure security and security-monitoring lab.

Planned topics:

* Security event collection
* Sysmon
* Windows Security Events
* Linux security logs
* Centralized logging
* SIEM
* Security dashboards
* Detection rules
* Authentication monitoring
* Failed login detection
* Privileged account monitoring
* Firewall log analysis
* Security incident investigation
* Kali Linux security lab

📁 `09-security-siem/` — Planned

---

### 10 — Automation & Scripting 🔜

Infrastructure administration automation.

Planned topics:

* PowerShell
* Bash
* Active Directory automation
* Bulk user creation
* Group management
* System information collection
* Automated health checks
* Backup automation
* Scheduled scripts
* Server administration
* Linux automation
* Infrastructure automation

📁 `10-automation-scripting/` — Planned

---

### 11 — Backup & Disaster Recovery 🔜

A dedicated advanced disaster-recovery module building on the backup exercises already performed in Proxmox and Windows Server.

Planned topics:

* Proxmox backups
* Windows Server Backup
* WBAdmin
* VM recovery
* File recovery
* Active Directory recovery
* Backup verification
* Restore testing
* Disaster recovery procedures
* Recovery Point Objective concepts
* Recovery Time Objective concepts
* Failure simulations
* Recovery documentation

📁 `11-backup-disaster-recovery/` — Planned

---

### 12 — Advanced Networking & VPN 🔜

Advanced networking exercises building on the existing pfSense and WireGuard infrastructure.

Planned topics:

* VLANs
* Network segmentation
* Inter-VLAN routing
* Firewall segmentation
* Advanced NAT
* DNS architecture
* DHCP architecture
* VPN administration
* WireGuard
* Remote administration
* Network troubleshooting
* Traffic analysis
* Secure management networks

📁 `12-advanced-networking/` — Planned

---

### Future Expansion

As the HomeLab grows, additional projects may include:

* Proxmox clustering
* High availability
* Additional Domain Controllers
* Linux clustering
* Reverse proxy services
* Configuration management
* Infrastructure as Code
* Cloud integration
* Hybrid identity
* Microsoft Azure
* Advanced monitoring
* Advanced security testing

---

# 🎯 Project Goals

The main goals of this HomeLab are to:

* Develop practical System Administrator skills
* Build and manage Windows enterprise infrastructure
* Develop Linux administration skills
* Improve networking and firewall knowledge
* Practice Active Directory administration
* Implement enterprise security controls
* Understand virtualization infrastructure
* Learn container technologies
* Build centralized monitoring and logging
* Practice backup and disaster recovery
* Develop PowerShell and Bash automation skills
* Troubleshoot realistic infrastructure problems
* Understand infrastructure dependencies
* Document technical projects professionally using GitHub
* Build a technical portfolio demonstrating practical IT infrastructure experience

---

# 🔧 Hands-On Learning Approach

This HomeLab focuses on practical implementation rather than theory alone.

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
Secure
  |
  v
Test
  |
  v
Troubleshoot
  |
  v
Recover
  |
  v
Document
  |
  v
Improve
```

Configuration problems and troubleshooting scenarios encountered during the project are documented because diagnosing and resolving infrastructure issues is an essential part of real-world system administration.

Successful configuration alone is not the objective.

The goal is to understand:

* How the technology works
* Why it is configured
* How to validate it
* What happens when it fails
* How to troubleshoot it
* How to secure it
* How to recover it
* How it interacts with other infrastructure services

---

# 🔐 Security & Remote Access

Security is an important part of the HomeLab architecture.

Current technologies and practices include:

* pfSense firewall policies
* Windows Firewall
* Microsoft LAPS
* BitLocker
* Windows Defender
* Group Policy security controls
* Active Directory security
* Administrative account separation
* Security auditing
* Sysmon
* Windows Event Forwarding
* WireGuard VPN
* Secure remote HomeLab access

Management interfaces are not intentionally exposed directly to the public Internet.

Remote access to internal HomeLab resources is performed through secure VPN connectivity.

Security controls will continue to evolve as additional Linux, SIEM, monitoring, segmentation, and security technologies are introduced.

---

# 💾 Backup & Recovery

Backup and recovery are treated as core infrastructure responsibilities rather than optional features.

Current experience includes:

* Proxmox backup storage
* Dedicated backup disks
* Windows Server Backup
* WBAdmin
* Backup verification
* Recovery testing
* Active Directory recovery exercises

Future development will expand into:

* Automated backups
* Additional backup destinations
* VM disaster recovery
* Linux backups
* Configuration backups
* Recovery procedures
* Failure simulations
* Recovery testing

The objective is not only to deploy infrastructure but also to understand how services and systems can be restored following hardware failure, configuration errors, accidental deletion, or other incidents.

---

# 🔍 Monitoring & Logging

The HomeLab includes centralized monitoring and security logging exercises.

Current technologies include:

* Windows Event Forwarding
* Windows Event Collector
* Sysmon
* Windows Security Auditing
* Centralized Windows event collection

Windows client security events can be forwarded to the Windows Server environment for centralized investigation and monitoring.

Future monitoring development will introduce infrastructure-wide monitoring covering:

```text
Proxmox
   |
Windows Servers
   |
Windows Clients
   |
Linux Servers
   |
Docker Containers
   |
pfSense
   |
Network Infrastructure
   |
Centralized Monitoring / Logging
```

---

# 🚧 Project Status

**🟢 Active — Continuously Developing**

This repository is an ongoing technical learning project.

New technologies, configurations, security controls, automation scripts, troubleshooting scenarios, and infrastructure services will be added as the HomeLab develops.

## Completed Major Modules

* ✅ Proxmox Virtualization
* ✅ pfSense Firewall
* ✅ Windows Server 2025
* ✅ Active Directory

## Current Focus

* 🐧 Linux Administration

## Planned Development

* ⏳ Docker & Containers
* ⏳ Storage & File Services
* ⏳ Monitoring & Observability
* ⏳ Security & SIEM
* ⏳ Automation & Scripting
* ⏳ Backup & Disaster Recovery
* ⏳ Advanced Networking & VPN
* ⏳ Proxmox clustering
* ⏳ VLAN segmentation
* ⏳ High availability
* ⏳ Additional Domain Controllers
* ⏳ Cloud and hybrid infrastructure

---

# 📸 Screenshots & Documentation

Screenshots are included throughout individual project modules to demonstrate:

* Installation
* Configuration
* Validation
* Testing
* Troubleshooting
* Successful results

Screenshots are reviewed before publication to prevent accidental exposure of sensitive information.

Detailed implementation documentation can be accessed through the **Project Documentation** section above.

---

# ⚠️ Security Notice

This repository documents a personal HomeLab environment for educational and portfolio purposes.

All configurations and screenshots published in this repository are reviewed and sanitized before publication.

Sensitive information is not intentionally published, including:

* Passwords
* Private keys
* WireGuard private keys
* Authentication tokens
* API keys
* BitLocker recovery keys
* Private certificates
* Administrative credentials
* Sensitive network information

Configuration examples containing sensitive values use placeholders such as:

```text
Password   = <REDACTED>
PrivateKey = <REDACTED>
Token      = <REDACTED>
RecoveryKey = <REDACTED>
```

---

# 🧠 Skills Demonstrated

This HomeLab demonstrates practical experience across multiple IT infrastructure disciplines.

## Virtualization

* Proxmox VE
* Virtual machines
* Virtual networking
* Storage management
* VM backup and recovery
* Virtual infrastructure troubleshooting

## Windows Infrastructure

* Windows Server 2025
* Windows 11
* Active Directory
* DNS
* DHCP
* Group Policy
* Certificate Services
* Microsoft LAPS
* BitLocker
* Remote administration

## Networking

* pfSense
* Firewall policies
* NAT
* DNS
* DHCP
* VPN
* WireGuard
* Remote access
* Network troubleshooting

## Security

* Microsoft LAPS
* BitLocker
* Windows Defender
* Windows Firewall
* Security auditing
* Privileged administration
* Group Policy security
* Endpoint security controls

## Monitoring & Logging

* Sysmon
* Windows Event Forwarding
* Windows Event Collector
* Windows Event Logs
* Security event collection

## Backup & Recovery

* Proxmox backups
* Windows Server Backup
* WBAdmin
* Backup verification
* Recovery testing
* Active Directory recovery

## Active Directory Administration

* AD DS
* Organizational Units
* Users and groups
* AGDLP
* Delegation
* Administrative accounts
* Password policies
* Fine-Grained Password Policies
* FSMO roles
* Sites and Services
* Active Directory Recycle Bin
* gMSA
* AD troubleshooting

## Troubleshooting

* Network connectivity
* DNS resolution
* Domain connectivity
* Group Policy
* Certificate Services
* Event forwarding
* VPN connectivity
* Virtual machines
* Authentication
* Windows Server services

## Linux & Automation

These areas will expand as the next phases of the HomeLab are completed.

Planned skills include:

* Linux server administration
* Bash
* PowerShell automation
* Docker
* Linux networking
* Linux security
* Infrastructure automation

---

# 🗂️ Repository Structure

```text
enterprise-homelab/
│
├── README.md
│
├── 01-proxmox/
│
├── 02-pfsense/
│
├── 03-windows-server-2025/
│
├── 04-active-directory/
│
├── 05-linux-administration/          # Next
│
├── 06-docker-containers/             # Planned
│
├── 07-storage-file-services/         # Planned
│
├── 08-monitoring-observability/      # Planned
│
├── 09-security-siem/                 # Planned
│
├── 10-automation-scripting/          # Planned
│
├── 11-backup-disaster-recovery/      # Planned
│
└── 12-advanced-networking/            # Planned
```

The repository structure may evolve as the HomeLab grows and additional enterprise technologies are introduced.

---

# 👤 Author

**Mohamed Afham**

**IT Support Engineer | Aspiring System Administrator**

Focused on:

* Windows Server
* Active Directory
* Linux
* Virtualization
* Networking
* Infrastructure security
* Monitoring
* Troubleshooting
* Automation
* Backup and disaster recovery

This HomeLab is maintained as a personal learning environment and technical portfolio to demonstrate hands-on infrastructure administration experience.

---

> **Enterprise HomeLab — Build. Secure. Test. Troubleshoot. Automate. Document. Improve.**
