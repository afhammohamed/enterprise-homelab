# 🏠 Enterprise HomeLab

> A hands-on enterprise-style HomeLab built to develop practical skills in **IT infrastructure, Virtualization, Networking, Security, Linux, Monitoring, and Automation**.

---

## 👋 About This Project

This repository documents my personal **Enterprise HomeLab**, built as a practical environment for hands-on learning, experimentation, and development across IT infrastructure, virtualization, networking, operating systems, security, monitoring, and automation.

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

My goal is to build a small but realistic enterprise infrastructure where I can practice the responsibilities of a **System Administrator**.

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

Problems encountered during the project are intentionally documented because troubleshooting is an important part of real-world infrastructure administration.

---

# 🖥️ HomeLab Infrastructure

My lab currently uses:

| Hardware               | Purpose                               |
| ---------------------- | ------------------------------------- |
| Lenovo M720t           | Primary Proxmox virtualization server |
| Lenovo M910q           | Additional HomeLab node               |
| Lenovo M910q           | Additional HomeLab node               |
| Managed Switch         | Network connectivity                  |
| Additional HDD Storage | Backup and storage                    |

### Current Architecture

```text
                        Internet
                           │
                      ISP Router
                           │
                    Managed Switch
                           │
              ┌────────────┼────────────┐
              │            │            │
         Proxmox-01    Proxmox-02    Proxmox-03
              │
           pfSense
           Firewall
              │
          Lab Network
              │
       ┌──────┴───────┐
       │              │
Windows Server     Windows 11
     2025             Client
       │
       ├── Active Directory
       ├── DNS
       ├── DHCP
       ├── Group Policy
       ├── Microsoft LAPS
       ├── BitLocker
       ├── Windows Security
       ├── Sysmon
       ├── Event Forwarding
       └── Backup & Recovery
```

This architecture will continue to expand with Linux servers, containers, storage, monitoring, SIEM, automation, and other enterprise technologies.

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

* Windows Server deployment
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
* Windows Server Backup
* Remote administration

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

# 🚧 What I'm Working On Now

## 05 — Linux Administration 🐧

The next stage of the HomeLab focuses on developing practical Linux System Administration skills.

Planned areas include:

* Linux server deployment
* Ubuntu Server
* Debian
* Users and groups
* File permissions
* sudo
* Package management
* Linux networking
* SSH
* Storage and filesystems
* systemd and services
* Scheduled tasks
* Logging
* Firewall configuration
* Security hardening
* Samba
* Bash scripting
* Linux troubleshooting
* Active Directory integration

This Linux environment will eventually integrate with the existing Windows, pfSense, and Proxmox infrastructure.

---

# 🗺️ Future Roadmap

After Linux Administration, the HomeLab will continue expanding into:

| Stage | Project                    | Status      |
| ----- | -------------------------- | ----------- |
| 01    | Proxmox Virtualization     | ✅ Completed |
| 02    | pfSense Firewall           | ✅ Completed |
| 03    | Windows Server 2025        | ✅ Completed |
| 04    | Active Directory           | ✅ Completed |
| 05    | Linux Administration       | 🚧 Next     |
| 06    | Docker & Containers        | 🔜 Planned  |
| 07    | Storage & File Services    | 🔜 Planned  |
| 08    | Monitoring & Observability | 🔜 Planned  |
| 09    | Security & SIEM            | 🔜 Planned  |
| 10    | Automation & Scripting     | 🔜 Planned  |
| 11    | Backup & Disaster Recovery | 🔜 Planned  |
| 12    | Advanced Networking & VPN  | 🔜 Planned  |

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

**Virtualization**

* Proxmox VE
* Virtual machines
* Virtual networking
* Storage and backups

**Windows Administration**

* Windows Server 2025
* Windows 11
* Active Directory
* DNS
* DHCP
* Group Policy
* PowerShell

**Networking**

* pfSense
* Firewall policies
* NAT
* VPN
* WireGuard
* DNS
* Network troubleshooting

**Security**

* Microsoft LAPS
* BitLocker
* Windows Defender
* Windows Firewall
* Security auditing
* Sysmon
* Windows Event Forwarding

**Linux**

* Linux server administration
* Networking
* SSH
* Permissions
* Services
* Security
* Bash

**Future Skills**

* Docker
* SIEM
* Monitoring
* NAS and storage
* Infrastructure automation
* Disaster recovery
* High availability

---

# 📂 Repository Structure

```text
enterprise-homelab/
│
├── README.md
│
├── 01-proxmox/                    ✅
├── 02-pfsense/                    ✅
├── 03-windows-server-2025/        ✅
├── 04-active-directory/           ✅
│
├── 05-linux-administration/       🚧
├── 06-docker-containers/          🔜
├── 07-storage-file-services/      🔜
├── 08-monitoring-observability/   🔜
├── 09-security-siem/              🔜
├── 10-automation-scripting/       🔜
├── 11-backup-disaster-recovery/   🔜
└── 12-advanced-networking/        🔜
```

---

# 🔐 Security Notice

This repository documents a personal HomeLab created for educational and portfolio purposes.

Sensitive information is not intentionally published.

This includes:

* Passwords
* Private keys
* VPN keys
* Authentication tokens
* API keys
* BitLocker recovery keys
* Certificates
* Administrative credentials

Sensitive values shown in documentation are replaced with placeholders such as:

```text
Password   = <REDACTED>
PrivateKey = <REDACTED>
Token      = <REDACTED>
```

Remote access to the HomeLab is provided through secure VPN connectivity rather than intentionally exposing internal management interfaces directly to the Internet.

---

# 🚀 Project Status

> **🟢 Active — Continuously Developing**

### Completed

✅ Proxmox Virtualization
✅ pfSense Firewall
✅ Windows Server 2025
✅ Active Directory

### Current Focus

🚧 **Linux Administration**

### Coming Next

🐳 Docker & Containers
💾 Storage & File Services
📊 Monitoring & Observability
🛡️ Security & SIEM
⚙️ Automation & Scripting
♻️ Backup & Disaster Recovery
🌐 Advanced Networking

---

# 👤 Author

**Mohamed Afham**

Building and documenting hands-on enterprise infrastructure across:

**Windows • Linux • Active Directory • Proxmox • pfSense • Networking • Security • Monitoring • Automation**

This repository represents continuous hands-on learning, experimentation, troubleshooting, and infrastructure development.

---

> ### Build → Configure → Secure → Break → Troubleshoot → Recover → Automate → Document → Improve
