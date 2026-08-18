# 🪟 Windows Server 2025

## 📌 Overview

Windows Server 2025 is used as the primary Windows server platform within my Enterprise HomeLab.

The server was deployed as a virtual machine on Proxmox VE and provides centralized Windows infrastructure services including identity, authentication, DNS, Group Policy, security management, monitoring, and backup/recovery functionality.

The Windows Server virtual machine is named:

**SRV-DC01**

The server was later promoted to a Domain Controller and now forms the core of the Windows Active Directory environment.

---

## 🏗️ Server Architecture

Windows Server 2025 is hosted as a virtual machine on the Proxmox VE virtualization platform.

The general infrastructure design is:

```text
Internet
   │
ISP Router
   │
pfSense Firewall
   │
HomeLab Network
   │
Proxmox VE
   │
   └── SRV-DC01
       │
       ├── Windows Server 2025
       ├── Active Directory Domain Services
       ├── DNS Server
       ├── DHCP Server
       ├── Group Policy
       ├── Active Directory Certificate Services
       ├── Microsoft LAPS
       ├── Windows Event Forwarding
       └── Enterprise Security Policies
```

This architecture provides a realistic environment for practicing Windows Server administration while integrating virtualization, networking, security, monitoring, and remote-access technologies.

---

## 💻 Virtual Machine Configuration

Windows Server 2025 was deployed as a dedicated virtual machine within Proxmox VE.

### VM Details

| Setting | Configuration |
|---|---|
| VM Name | SRV-DC01 |
| Operating System | Windows Server 2025 |
| Hypervisor | Proxmox VE |
| Firmware | OVMF (UEFI) |
| Machine Type | q35 |
| CPU | 4 vCPU |
| Memory | 8 GB |
| Primary Disk | 80 GB |
| Backup Disk | 50 GB |
| Network Adapter | VirtIO |
| Virtualization Platform | KVM/QEMU |

VirtIO drivers were installed to provide optimized virtual storage and network performance.

The additional 50 GB virtual disk is used for Windows Server backup and recovery testing.

---

## 🌐 Network Configuration

SRV-DC01 is connected to the internal HomeLab network through the Proxmox virtual networking infrastructure.

The server uses a static network configuration because it provides critical infrastructure services including Active Directory and DNS.

The general network path is:

```text
SRV-DC01
    │
VirtIO Network Adapter
    │
Proxmox Linux Bridge
    │
pfSense
    │
HomeLab Network
```

This design allows pfSense to provide routing, firewalling, VPN connectivity, and network security while Windows Server provides centralized Windows infrastructure services.

---

## 🧩 Server Roles & Features

Windows Server 2025 was configured with several infrastructure roles and management components as the HomeLab developed.

Key technologies implemented include:

- Active Directory Domain Services (AD DS)
- DNS Server
- DHCP Server
- Group Policy Management
- Active Directory Certificate Services
- Microsoft LAPS
- Windows Server Backup
- Windows Event Forwarding
- Windows security and auditing policies

Some technologies are documented separately within this repository to provide more detailed configuration, testing, and troubleshooting information.

---

## 👥 Active Directory Domain Services

Active Directory Domain Services was installed on SRV-DC01.

The server was subsequently promoted to a Domain Controller, creating centralized identity and authentication services for the HomeLab.

Active Directory is used to manage:

- Domain users
- Administrative accounts
- Domain-joined computers
- Organizational Units
- Security groups
- Group memberships
- Authentication
- Authorization
- Enterprise security policies

A Windows 11 client was successfully joined to the domain and is managed through the Windows Server Active Directory environment.

Detailed Active Directory configuration is documented separately in the dedicated Active Directory section.

---

## 🌐 DNS Server

DNS was installed alongside Active Directory Domain Services.

The DNS service provides internal name resolution for domain-joined systems and infrastructure resources.

DNS integration allows HomeLab systems to locate internal services using hostnames instead of relying exclusively on IP addresses.

pfSense DNS Resolver configuration is also integrated with the Windows DNS infrastructure to provide name resolution across different parts of the HomeLab environment.

---

## 📡 DHCP Server

The DHCP Server role was installed during the Windows Server implementation.

DHCP responsibilities were tested between Windows Server and pfSense to understand how enterprise DHCP services interact with firewall-based DHCP services.

During configuration and testing, care was taken to avoid operating multiple conflicting DHCP services on the same network.

This provided practical experience with:

- DHCP installation
- DHCP authorization
- DHCP scopes
- IP address allocation
- Default gateway configuration
- DNS server assignment
- Scope activation and deactivation
- DHCP troubleshooting

---

## 🖥️ Remote Administration

Remote Desktop was enabled on Windows Server to allow SRV-DC01 to be administered remotely from authorized management systems.

Remote administration is performed through the protected HomeLab network.

Remote access to the infrastructure can also be established through the WireGuard VPN configured on pfSense.

The general remote administration path is:

```text
Remote Device
     │
WireGuard VPN
     │
   pfSense
     │
HomeLab Network
     │
  SRV-DC01
```

This allows remote server administration without exposing Windows Remote Desktop directly to the public Internet.

---

## 🔐 Group Policy

Group Policy is used to centrally configure and enforce Windows settings across the domain environment.

Enterprise-style Group Policy Objects were created and tested for areas including:

- Windows Firewall
- Password and account policies
- Windows Defender
- BitLocker
- Audit policies
- Remote Desktop
- User Account Control
- SMB security
- Network security
- Windows Event Forwarding
- Endpoint security settings

Group Policy configuration is documented in greater detail in its dedicated project section.

---

## 🔑 Microsoft LAPS

Microsoft Local Administrator Password Solution (LAPS) was configured within the Active Directory environment.

LAPS provides centralized management of local administrator credentials for domain-joined Windows computers.

The implementation included testing of Windows LAPS Active Directory attributes and policy application.

This provides practical experience with securing local administrator accounts in an enterprise-style Windows environment.

---

## 🔒 BitLocker

BitLocker policies were configured and tested through Group Policy.

The Windows 11 domain client was used to validate BitLocker configuration and encryption behavior.

This provided practical experience with:

- Operating system drive encryption
- TPM integration
- Group Policy configuration
- Recovery information
- Encryption status verification
- Enterprise endpoint security

---

## 🛡️ Windows Firewall & Security Policies

Enterprise-style Windows Firewall policies were configured through Group Policy.

Additional Windows security controls were also implemented and tested.

These include:

- Windows Firewall policies
- Windows Defender configuration
- Password policies
- Account lockout policies
- Audit policies
- UAC configuration
- SMB hardening
- Network security settings
- TLS security settings
- Remote access restrictions
- Remote Assistance restrictions
- Windows Event Logging

These configurations help simulate centralized security management commonly used within enterprise Windows environments.

---

## 📜 Active Directory Certificate Services

Active Directory Certificate Services was implemented within the HomeLab to gain practical experience with enterprise certificate infrastructure.

During implementation, certificate authority communication and certificate trust issues were encountered and troubleshooted.

This provided experience with:

- Certificate Authority services
- Enterprise certificate infrastructure
- Certificate trust
- Certificate troubleshooting
- Windows domain integration

---

## 📊 Sysmon Monitoring

Sysmon was deployed to provide enhanced endpoint activity logging within the Windows environment.

Sysmon provides additional visibility into system activity beyond standard Windows event logs.

The implementation was used to generate and monitor security-relevant events within the HomeLab.

This provides practical experience with endpoint monitoring and security telemetry.

---

## 📡 Windows Event Forwarding

Windows Event Forwarding was implemented to centralize selected Windows events from domain-joined systems.

The general logging architecture is:

```text
Windows 11 Client
       │
     Sysmon
       │
Windows Event Log
       │
Windows Event Forwarding
       │
    SRV-DC01
       │
 Forwarded Events
```

A Windows Event Collector subscription was configured on the server.

During initial testing, the **Forwarded Events** log did not receive events correctly.

The configuration was investigated, recreated, and tested until the subscription became operational and events were successfully forwarded.

This provided practical troubleshooting experience with centralized Windows event collection.

---

## 💾 Backup & Recovery

A dedicated 50 GB virtual disk was attached to SRV-DC01 for Windows Server backup and recovery testing.

Windows Server Backup and the `wbadmin` command-line utility were used to perform and verify backup operations.

The implementation included:

- Dedicated backup storage
- Windows Server Backup
- `wbadmin`
- Backup verification
- Recovery testing
- Restore procedures

The backup disk is kept separate from the primary Windows Server operating system disk.

This allows backup and recovery procedures to be tested without using the primary system volume as the backup destination.

---

## ♻️ Active Directory Recycle Bin

Active Directory Recycle Bin functionality was implemented and tested within the HomeLab environment.

This provides the ability to recover accidentally deleted Active Directory objects while preserving important object attributes.

Testing the Active Directory Recycle Bin provided practical experience with directory recovery and administrative troubleshooting.

---

## 🧪 Testing & Validation

The Windows Server environment was tested throughout the implementation process.

Testing included:

- Server network connectivity
- DNS resolution
- Domain authentication
- Windows 11 domain joining
- Group Policy processing
- Remote Desktop connectivity
- Microsoft LAPS functionality
- BitLocker policy application
- Windows Firewall policies
- Sysmon logging
- Windows Event Forwarding
- Certificate Services
- DHCP configuration
- Server backup
- Recovery procedures
- Active Directory object recovery

Testing was performed after major configuration changes to confirm that services were operating correctly.

---

## 🔧 Troubleshooting Experience

Several realistic troubleshooting scenarios were encountered while building the Windows Server environment.

Examples included:

- Domain connectivity problems
- DNS resolution issues
- Certificate Authority communication errors
- Group Policy troubleshooting
- Windows Event Forwarding configuration problems
- Remote Desktop connectivity issues
- DHCP configuration conflicts
- LAPS configuration validation
- Backup and recovery testing
- Service startup and dependency issues

Troubleshooting these issues provided practical experience beyond simply installing and configuring Windows Server roles.

---

## 🔗 Integration with pfSense

Windows Server operates behind the pfSense firewall within the HomeLab network.

pfSense provides:

- Network routing
- Firewall protection
- NAT
- WireGuard VPN
- Dynamic DNS
- DNS forwarding and overrides
- Remote-access connectivity

Windows Server provides:

- Active Directory
- DNS
- Group Policy
- Identity management
- Certificate services
- Windows security policies
- Centralized event collection

Together, these systems create a more realistic enterprise-style infrastructure environment.

---

## 🔗 Integration with Windows 11

A Windows 11 virtual machine was deployed within Proxmox and joined to the Active Directory domain.

The Windows 11 client is used to test:

- Domain authentication
- Group Policy
- Microsoft LAPS
- BitLocker
- Windows Firewall
- Sysmon
- Windows Event Forwarding
- DNS
- Remote administration
- Enterprise security policies

This provides a client/server environment for testing centralized Windows administration.

---

## 📸 Screenshots

Screenshots will be added to demonstrate the Windows Server 2025 configuration while ensuring that sensitive information is removed before publication.

Recommended screenshots include:

- Windows Server Manager Dashboard
- Local Server configuration
- Installed Roles and Features
- Active Directory Domain Services
- DNS Manager
- DHCP Manager
- Group Policy Management
- Windows Event Viewer
- Windows Event Forwarding
- Microsoft LAPS
- Windows Server Backup
- Active Directory Recycle Bin
- Proxmox SRV-DC01 VM configuration

> **Security Notice:** IP addresses, usernames, domain information, passwords, certificates, recovery keys, authentication information, and other sensitive infrastructure details should be sanitized where appropriate before screenshots are published.

---

## 🧠 Skills Demonstrated

This stage demonstrates practical experience with:

- Windows Server 2025 administration
- Windows Server deployment
- Proxmox virtualization
- Active Directory Domain Services
- DNS
- DHCP
- Group Policy
- Microsoft LAPS
- BitLocker
- Windows Firewall
- Active Directory Certificate Services
- Sysmon
- Windows Event Forwarding
- Windows Server Backup
- Active Directory recovery
- Remote administration
- Enterprise security configuration
- Infrastructure troubleshooting
- Windows client/server integration
- pfSense integration
- Backup and disaster recovery

---

## 🎯 Key Learning Outcomes

Through this stage of the HomeLab, I gained practical experience deploying and administering a Windows Server environment rather than only studying Windows Server technologies theoretically.

The environment allowed me to practice how multiple enterprise technologies work together, including virtualization, networking, identity management, DNS, Group Policy, endpoint security, centralized logging, remote access, backup, and disaster recovery.

It also provided hands-on troubleshooting experience with real configuration problems and helped develop a structured approach to diagnosing infrastructure issues.

---

## ➡️ Next Stage

The next stage documents:

**Active Directory Domain Services (AD DS)**

The Active Directory section will cover:

- Domain Controller configuration
- Domain structure
- Organizational Units
- Users
- Groups
- Computers
- Administrative accounts
- Domain security
- Active Directory Recycle Bin
- Testing and troubleshooting

---
