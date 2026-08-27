# 🏠 Enterprise HomeLab

> A hands-on enterprise-style HomeLab built to develop practical skills in IT infrastructure, virtualization, networking, security, Linux, monitoring, and automation.

---

## 👋 About This Project

This repository documents my personal Enterprise HomeLab, built for hands-on learning, experimentation, troubleshooting, and infrastructure development.

Rather than simply installing technologies, I use the environment to deploy services, apply security controls, test configurations, troubleshoot failures, perform recovery exercises, automate administrative tasks, and document what I learn.

The goal is not simply to install different technologies.

I use this environment to:

* Deploy infrastructure
* Configure enterprise services
* Apply security controls
* Test configurations
* Troubleshoot problems
* Simulate failures
* Recover systems
* Automate administrative tasks
* Document everything I learn

The HomeLab is continuously expanding as I develop my skills across **Windows, Linux, networking, virtualization, security, monitoring, storage, and automation**.

---

# 🎯 My Goal

My goal is to build a small but realistic enterprise-style infrastructure where I can develop practical skills across systems, networking, security, virtualization, automation, and infrastructure operations.

The learning process follows:

```text
Plan
  ↓
Deploy
  ↓
Configure
  ↓
Secure
  ↓
Test
  ↓
Troubleshoot
  ↓
Recover
  ↓
Document
  ↓
Improve
```

Troubleshooting and recovery are intentionally documented because diagnosing failures is a key part of infrastructure administration.

---

# 🖥️ HomeLab Infrastructure

My lab currently uses:

| Hardware               | Purpose                               |
| ---------------------- | ------------------------------------- |
| Lenovo M720t           | Primary Proxmox virtualization server |
| Lenovo M910q x 2       | Available for multi-node / cluster expansion               |
| Managed Switch         | Network connectivity                  |
| Additional HDD Storage | Backup and storage                    |

## 🏗️ Current Architecture

The diagram below represents the current architecture of my Enterprise HomeLab, including Proxmox VE, pfSense, Windows Server 2025, Active Directory services, WireGuard VPN, DDNS, security controls, monitoring, and backup components.

![Enterprise HomeLab Current Architecture](docs/architecture/updated_enterprise-homelab-current-architecture.png)

---

# 📚 Project Documentation

The repository is organized by **major infrastructure technologies**.

Detailed installation steps, configuration, commands, screenshots, testing, troubleshooting, and lessons learned are stored inside each project folder.

---

## 01 — Proxmox Virtualization ✅

Built the virtualization platform used to host the HomeLab infrastructure.

Covered:

* Proxmox VE installation
* Virtual machines
* Virtual networking
* Linux bridges
* Storage
* Backup storage
* VM management
* Troubleshooting

➡️ **[View Proxmox Documentation](./01-proxmox/)**

---

## 02 — pfSense Firewall ✅

Deployed pfSense to provide firewalling, networking, and secure remote access for the HomeLab.

Covered:

* WAN/LAN configuration
* Firewall rules
* NAT
* Network aliases
* DNS
* Dynamic DNS
* WireGuard VPN
* Secure remote access
* Firewall troubleshooting

➡️ **[View pfSense Documentation](./02-pfsense/)**

---

## 03 — Windows Server 2025 ✅

Deployed Windows Server 2025 and configured the main Windows infrastructure services used throughout the lab.

Covered:

- Windows Server 2025 deployment
- DNS and DHCP
- Group Policy
- Active Directory Certificate Services
- Microsoft LAPS
- BitLocker and Windows security policies
- Sysmon and Windows Event Forwarding
- Windows Server Backup
- Remote administration
- Troubleshooting and recovery

➡️ **[View Windows Server 2025 Documentation](./03-windows-server-2025/)**

---

## 04 — Active Directory ✅

Built an enterprise-style Active Directory environment for centralized identity and access management.

Covered:

* Active Directory Domain Services
* Organizational Units
* Users and groups
* AGDLP
* Administrative accounts
* Delegation
* Password policies
* Fine-Grained Password Policies
* Active Directory Sites & Services
* FSMO roles
* AD health validation
* Active Directory Recycle Bin
* gMSA
* PowerShell administration
* Troubleshooting

➡️ **[View Active Directory Documentation](./04-active-directory/)**

---

## 🐧 05 — Linux Administration ✅

Deployed an Ubuntu Linux system and integrated it into the existing Windows-based HomeLab infrastructure.

### Implemented

- Linux networking and internal DNS
- Users, groups and filesystem permissions
- sudo and least-privilege administration
- APT package management
- systemd service management
- SSH remote administration
- Ed25519 key-based authentication
- SSH security hardening
- LVM storage administration
- Linux logging with journalctl
- Bash scripting and cron automation
- UFW host firewall
- Samba / SMB file sharing
- Windows-to-Linux interoperability
- Active Directory domain integration
- SSSD and Kerberos authentication
- AD group-based Linux login
- AD-controlled sudo authorization

**Key outcome:** Linux authentication and administrative access can be centrally controlled through Active Directory security groups.

➡️ [View Linux Administration Documentation](05-Linux%20Administration/README.md)

---

# 🚧 What I'm Working On Now

## 06 — Monitoring & Observability

The next stage will introduce centralized infrastructure monitoring.

The objective is to move from simply administering systems to being able to proactively identify performance issues, service failures and infrastructure problems.

### Planned Monitoring

- Proxmox host and VM health
- Windows Server monitoring
- Linux server monitoring
- pfSense monitoring
- CPU, memory, disk and network utilization
- Service availability
- Active Directory service health
- Dashboards
- Warning and critical thresholds
- Alerting
- Failure simulation
- Monitoring-based troubleshooting

This will create the monitoring foundation for later Docker, storage and security projects..

---

# 🗺️ Future Roadmap

| Stage | Project | Status |
|---|---|---|
| 01 | Proxmox Virtualization | ✅ Completed |
| 02 | pfSense Firewall & Networking | ✅ Completed |
| 03 | Windows Server 2025 | ✅ Completed |
| 04 | Active Directory | ✅ Completed |
| 05 | Linux Administration | ✅ Completed |
| **06** | **Monitoring & Observability** | 🔜 **In Progress** |
| 07 | Docker & Containers | 📋 Planned |
| 08 | Storage & File Services | 📋 Planned |
| 09 | Security & SIEM | 📋 Planned |
| 10 | Automation & Scripting | 📋 Planned |
| 11 | Backup & Disaster Recovery | 📋 Planned |
| 12 | Advanced Networking | 📋 Planned |

The roadmap may evolve as new technologies and infrastructure requirements are introduced.

---

# 🔮 Where This Lab Is Going

The long-term goal is to connect the individual projects into a more complete enterprise-style environment.

For example:

```text
                    Proxmox Infrastructure
                            │
             ┌──────────────┼──────────────┐
             │              │              │
          Windows          Linux        Containers
             │              │              │
      Active Directory      │            Docker
             │              │              │
             └──────────────┼──────────────┘
                            │
                     pfSense Network
                            │
             ┌──────────────┼──────────────┐
             │              │              │
          Storage       Monitoring       Security
             │              │              │
            NAS          Dashboards       SIEM
                            │
                         Logging
                            │
                        Automation
```

The objective is to understand how different infrastructure technologies work **together**, rather than learning each technology in isolation.

---

# 🛠️ Skills Being Developed

This project provides hands-on experience with:

| Area | Technologies |
|---|---|
| **Virtualization** | Proxmox VE • VMs • Linux Bridges |
| **Windows Infrastructure** | Windows Server 2025 • Windows 11 • AD DS • DNS • DHCP • GPO |
| **Linux** | Ubuntu • SSH • systemd • LVM • UFW • Samba • Bash |
| **Networking** | pfSense • NAT • DNS • DDNS • WireGuard |
| **Security** | LAPS • BitLocker • Defender • Windows Firewall • SSH Hardening |
| **Identity** | Active Directory • SSSD • Kerberos • AD Groups |
| **Monitoring** | Sysmon • Windows Event Forwarding |
| **Automation** | PowerShell • Bash • Cron |

---

# 📂 Repository Structure

```text
enterprise-homelab/
│
├── README.md
│
├── 01-proxmox/
├── 02-pfsense/
├── 03-windows-server-2025/
├── 04-active-directory/
├── 05-Linux Administration/
│
└── docs/
    └── architecture/
        └── enterprise-homelab-current-architecture.png
```
Future project folders will be added as each new stage begins.
---

# 🔐 Security Notice

This repository is intended for educational and portfolio purposes.

Sensitive information such as passwords, private keys, VPN credentials, recovery keys, certificates, tokens and administrative credentials is excluded or replaced with placeholders.

Internal addresses and hostnames shown in the documentation belong only to the isolated HomeLab environment.

---

# 👤 Author

**Mohamed Afham**

This repository documents my ongoing hands-on infrastructure learning and HomeLab development.

---

> ### Build → Configure → Secure → Break → Troubleshoot → Recover → Automate → Document → Improve
