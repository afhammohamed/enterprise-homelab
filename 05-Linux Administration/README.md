## 05 — Linux Administration 🐧

This stage of the Enterprise HomeLab focuses on practical Linux System Administration using **Ubuntu Server** integrated with the existing **Proxmox, pfSense, Windows Server 2025 Active Directory, DNS, and Windows 11 environment**.

The objective was not only to deploy a Linux VM, but to configure and administer it using techniques commonly used in enterprise IT environments.

### Lab Environment

| Component | Configuration |
|---|---|
| Linux Server | Ubuntu Server 26.04 LTS |
| Hostname | `LINUX-SRV01` |
| IP Address | `10.10.10.20` |
| Hypervisor | Proxmox VE |
| Firewall / Gateway | pfSense |
| Domain Controller | `SRV-DC01` |
| Domain Controller IP | `10.10.10.10` |
| Active Directory Domain | `afhamhomelab.local` |
| Windows Client | `WIN11-CL01` |
| Authentication | Local + Active Directory / SSSD |
| Remote Administration | OpenSSH |
| File Sharing | Samba / SMB |
| Host Firewall | UFW |

---

### 05.1 — Ubuntu Server Deployment

Deployed **Ubuntu Server 26.04 LTS** as a virtual machine inside Proxmox.

The VM was connected to the internal HomeLab network protected by pfSense.

Storage was configured using **LVM (Logical Volume Manager)** to provide flexible Linux storage management.

Initial verification:

```bash
hostname
hostname -f
ip addr
ip route
```

Configured hostname:

```text
linux-srv01
```

Configured server IP:

```text
10.10.10.20
```

---

### 05.2 — Linux Networking

Configured the Ubuntu server to communicate with the existing HomeLab infrastructure.

Network interface:

```text
ens18
```

The server uses the Windows Server DNS service:

```text
DNS Server: 10.10.10.10
Search Domain: afhamhomelab.local
```

DNS resolution was verified using:

```bash
resolvectl status ens18
```

```bash
resolvectl query SRV-DC01.afhamhomelab.local
```

Successful resolution:

```text
SRV-DC01.afhamhomelab.local
→ 10.10.10.10
```

The Linux server DNS record was also verified:

```bash
resolvectl query linux-srv01.afhamhomelab.local
```

Result:

```text
linux-srv01.afhamhomelab.local
→ 10.10.10.20
```

This allows the Linux server to participate correctly in the internal DNS infrastructure.

---

### 05.3 — Linux Filesystem Administration

Practiced navigation and administration of the Linux filesystem.

Commands used:

```bash
pwd
ls
ls -l
ls -la
cd
mkdir
touch
cp
mv
rm
```

Example:

```bash
pwd
```

Output:

```text
/home/mafham
```

Root filesystem inspection:

```bash
ls /
```

Important Linux directories studied include:

```text
/etc     → System configuration
/home    → User home directories
/var     → Logs and variable application data
/usr     → Applications and utilities
/tmp     → Temporary files
/srv     → Server/service data
/root    → Root administrator home
/boot    → Boot files and kernel
```

---

### 05.4 — Linux Users and Groups

Created and managed Linux users and groups.

Commands practiced:

```bash
whoami
users
id
useradd
usermod
userdel
groupadd
groups
```

Example test account:

```text
testuser
```

Verification:

```bash
id testuser
```

Example result:

```text
uid=1001(testuser)
gid=1001(testuser)
groups=1001(testuser),100(users)
```

This demonstrated how Linux uses:

```text
UID → User Identifier
GID → Group Identifier
```

for filesystem ownership and access control.

---

### 05.5 — Linux File Permissions

Practiced Linux ownership and permission management.

Commands used:

```bash
chmod
chown
chgrp
ls -l
```

Linux permissions were studied using:

```text
r = Read    = 4
w = Write   = 2
x = Execute = 1
```

For example:

```text
770 = rwxrwx---
754 = rwxr-xr--
644 = rw-r--r--
```

Example:

```bash
chmod 644 ~/server-config.txt
```

Access was then tested using another Linux user.

This demonstrated that Linux security depends on:

```text
Owner permissions
Group permissions
Other permissions
Directory traversal permissions
```

---

### 05.6 — sudo Administration

Practiced privilege elevation using:

```bash
sudo
```

Instead of routinely logging in as `root`, administrative commands are executed using the administrator's own account.

Examples:

```bash
sudo apt update
sudo systemctl restart ssh
sudo journalctl
```

This provides better accountability and follows the principle of least privilege.

---

### 05.7 — Linux Package Management

Used Ubuntu's **APT package manager** to maintain the server.

Commands used:

```bash
sudo apt update
sudo apt upgrade
apt list --upgradable
sudo apt install <package>
sudo apt remove <package>
```

This is used by Linux administrators to:

- Install software
- Apply security patches
- Update packages
- Remove software
- Maintain server security

---

### 05.8 — systemd and Service Management

Practiced Linux service administration using `systemctl`.

Examples:

```bash
systemctl status ssh
systemctl is-active ssh
systemctl is-enabled ssh
sudo systemctl start ssh
sudo systemctl stop ssh
sudo systemctl restart ssh
sudo systemctl enable ssh
```

An important distinction was tested:

```text
active  → Service is currently running
enabled → Service is configured to start automatically
```

This is commonly used when troubleshooting Linux services.

---

### 05.9 — Linux Network Troubleshooting

Used Linux networking tools to inspect connectivity and listening services.

Commands included:

```bash
ip addr
ip route
ping
resolvectl
ss
```

Listening ports were inspected using:

```bash
sudo ss -tulpn
```

SSH was confirmed listening on:

```text
0.0.0.0:22
[::]:22
```

This demonstrates an important troubleshooting workflow:

```text
Service
   ↓
Listening Port
   ↓
Host Firewall
   ↓
Network Firewall
   ↓
Routing
   ↓
Client
```

---

### 05.10 — SSH Remote Administration

Installed and configured **OpenSSH Server** for secure remote Linux administration.

SSH service verification:

```bash
systemctl is-active ssh
```

Remote access from Windows:

```powershell
ssh mafham@10.10.10.20
```

SSH allows Linux servers to be administered securely without requiring console access.

---

### 05.11 — SSH Key Authentication

Configured **Ed25519 SSH key authentication** between the Windows administrator workstation and Ubuntu Server.

The Windows client successfully authenticated using:

```text
id_ed25519
```

Remote login:

```powershell
ssh mafham@10.10.10.20
```

SSH keys provide stronger authentication than relying only on passwords and are widely used for enterprise Linux administration and automation.

---

### 05.12 — SSH Security Hardening

Created a dedicated SSH hardening configuration:

```text
/etc/ssh/sshd_config.d/99-homelab-hardening.conf
```

Configuration:

```text
PubkeyAuthentication yes
PasswordAuthentication no
PermitRootLogin no
```

This configuration:

- Enables SSH public-key authentication
- Disables SSH password authentication
- Prevents direct root SSH login

The effective configuration was verified and key-based authentication was successfully tested.

---

### 05.13 — Linux Storage and LVM

Investigated Linux storage using:

```bash
lsblk
df -h
sudo pvs
sudo vgs
sudo lvs
```

Disk layout:

```text
sda                     32 GB
├── sda1                 1 MB
├── sda2                 2 GB  /boot
└── sda3                30 GB
     └── ubuntu-vg
          └── ubuntu-lv 15 GB /
```

LVM structure:

```text
Physical Volume
      ↓
Volume Group
      ↓
Logical Volume
      ↓
Filesystem
```

Approximately **15 GB remained free inside the Volume Group**, allowing future expansion of the logical volume.

---

### 05.14 — Linux Logging

Practiced system log investigation using `journalctl`.

Example:

```bash
sudo journalctl
```

Service-specific logs:

```bash
sudo journalctl -u ssh
```

Cron logs:

```bash
sudo journalctl -u cron -n 20
```

Linux logs are essential for:

- Troubleshooting
- Security investigations
- Service monitoring
- Root-cause analysis
- Auditing

---

### 05.15 — Bash Scripting

Created a basic Linux server health-check script.

The script was used to collect server information such as system health and resource status.

Example execution:

```bash
/home/mafham/server-health.sh
```

This introduced practical Bash scripting for Linux administration and automation.

---

### 05.16 — Scheduled Tasks with Cron

Configured Linux scheduled tasks using:

```bash
crontab -e
```

Server health monitoring was scheduled every five minutes:

```cron
*/5 * * * * /home/mafham/server-health.sh >> /var/log/homelab/server-health.log 2>&1
```

Cron execution was verified using:

```bash
sudo journalctl -u cron -n 20
```

Cron is commonly used for:

- Backup jobs
- Maintenance scripts
- Log processing
- Health checks
- Automated reports
- Cleanup operations

---

### 05.17 — UFW Host Firewall

Configured Ubuntu's host firewall using **UFW**.

Firewall status:

```bash
sudo ufw status
```

Required services were permitted, including:

```text
OpenSSH
Samba
```

Example:

```bash
sudo ufw allow Samba
```

This adds another security layer in addition to the pfSense network firewall.

The HomeLab therefore uses defense in depth:

```text
pfSense
   ↓
Network Firewall
   ↓
Ubuntu UFW
   ↓
Application / Service
```

---

### 05.18 — Samba File Server

Installed and configured **Samba** to provide Windows-compatible SMB file sharing.

Created:

```text
/srv/samba/ITShare
```

Directory configuration:

```bash
sudo mkdir -p /srv/samba/ITShare
sudo chown root:itadmins /srv/samba/ITShare
sudo chmod 2770 /srv/samba/ITShare
```

The `2` in:

```text
2770
```

enables **setgid**, causing new files to inherit the shared `itadmins` group.

This is useful for departmental shared directories.

---

### 05.19 — Samba Authentication

Created a Samba account associated with the existing Linux user:

```bash
sudo smbpasswd -a mafham
```

Enabled the account:

```bash
sudo smbpasswd -e mafham
```

Verified:

```bash
sudo pdbedit -L
```

This demonstrated the difference between:

```text
Linux local account
        ↓
Samba authentication database
        ↓
SMB access
```

---

### 05.20 — Enterprise-Style SMB Share

Configured:

```text
/etc/samba/smb.conf
```

with:

```ini
[ITShare]
   comment = IT Department Shared Folder
   path = /srv/samba/ITShare
   browseable = yes
   read only = no
   guest ok = no
   valid users = @itadmins
   force group = itadmins
   create mask = 0660
   directory mask = 2770
```

Before restarting Samba, the configuration was validated:

```bash
sudo testparm
```

Successful result:

```text
Loaded services file OK.
```

Then Samba was restarted:

```bash
sudo systemctl restart smbd
```

---

### 05.21 — Windows-to-Linux SMB Testing

The Samba share was tested from the Windows 11 domain client.

Windows path:

```text
\\10.10.10.20\ITShare
```

Authentication was performed using the Samba account.

A file was created from Windows:

```text
Created-From-Windows.txt
```

Linux verification:

```bash
ls -l /srv/samba/ITShare
```

```bash
cat /srv/samba/ITShare/Created-From-Windows.txt
```

This successfully demonstrated:

```text
WIN11-CL01
     ↓
SMB / TCP 445
     ↓
Ubuntu UFW
     ↓
Samba
     ↓
Linux Filesystem
     ↓
ITShare
```

---

### 05.22 — Active Directory DNS Discovery

Before joining Linux to Active Directory, AD DNS service records were verified.

LDAP discovery:

```bash
resolvectl service _ldap._tcp.dc._msdcs.afhamhomelab.local
```

Result:

```text
SRV-DC01.afhamhomelab.local
10.10.10.10
Port 389
```

Kerberos discovery:

```bash
resolvectl service _kerberos._tcp.afhamhomelab.local
```

Result:

```text
SRV-DC01.afhamhomelab.local
10.10.10.10
Port 88
```

These DNS SRV records allow Linux to discover Active Directory services.

---

### 05.23 — Linux Time Synchronization

Verified system time using:

```bash
timedatectl
```

The timezone was changed to:

```bash
sudo timedatectl set-timezone Europe/Malta
```

Final status:

```text
Time zone: Europe/Malta
System clock synchronized: yes
NTP service: active
```

Accurate time is particularly important because **Kerberos authentication is time-sensitive**.

---

### 05.24 — Active Directory Integration Packages

Installed the required Linux/AD integration components:

```bash
sudo apt install realmd sssd sssd-tools libnss-sss libpam-sss adcli samba-common-bin oddjob oddjob-mkhomedir packagekit krb5-user -y
```

Key components:

```text
realmd
   → AD discovery and domain joining

SSSD
   → AD identity and authentication integration

Kerberos
   → Secure ticket-based authentication

adcli
   → Active Directory domain operations
```

---

### 05.25 — Active Directory Domain Discovery

Before joining the domain:

```bash
realm discover afhamhomelab.local
```

The Linux server successfully discovered:

```text
realm-name: AFHAMHOMELAB.LOCAL
domain-name: afhamhomelab.local
server-software: active-directory
client-software: sssd
```

This confirmed that DNS and AD discovery were functioning correctly.

---

### 05.26 — Join Ubuntu to Windows Active Directory

Joined `LINUX-SRV01` to the Windows Server 2025 domain:

```bash
sudo realm join afhamhomelab.local -U Administrator
```

Verified:

```bash
realm list
```

Result included:

```text
configured: kerberos-member
server-software: active-directory
client-software: sssd
```

SSSD verification:

```bash
systemctl is-active sssd
```

Result:

```text
active
```

The `LINUX-SRV01` computer object appeared successfully inside **Active Directory Users and Computers**.

It was moved into:

```text
Afham-Computers
└── Servers
    └── LINUX-SRV01
```

---

### 05.27 — Active Directory User Resolution

Tested whether Linux could retrieve an Active Directory user:

```bash
id 'mafham@afhamhomelab.local'
```

Linux successfully retrieved the domain identity and AD group memberships including:

```text
Domain Users
GG-IT-Users
DL-IT-Share-Modify
```

This confirmed:

```text
LINUX-SRV01
      ↓
SSSD
      ↓
Active Directory
      ↓
Users + Groups
```

---

### 05.28 — Active Directory Login to Linux

Enabled automatic home-directory creation:

```bash
sudo pam-auth-update --enable mkhomedir
```

Restarted SSSD:

```bash
sudo systemctl restart sssd
```

Then tested an actual AD login:

```bash
su - 'mafham@afhamhomelab.local'
```

Authentication succeeded.

Verification:

```bash
whoami
hostname
pwd
id
```

Home directory was automatically created:

```text
/home/mafham@afhamhomelab.local
```

Linux was therefore successfully authenticating an Active Directory user.

---

### 05.29 — AD Group-Based Linux Access

Created a dedicated Active Directory Global Security Group:

```text
GG-Linux-Admins
```

The authorized administrator account was added to this group.

Linux group synchronization was refreshed:

```bash
sudo sss_cache -E
sudo systemctl restart sssd
```

Verification:

```bash
id 'mafham@afhamhomelab.local'
```

Linux successfully detected:

```text
gg-linux-admins@afhamhomelab.local
```

---

### 05.30 — Restrict Linux Login Using Active Directory Groups

Instead of allowing every domain user to access the Linux server, domain login was restricted.

Default realm access was denied:

```bash
sudo realm deny --all
```

Then only the Linux administrator AD group was permitted:

```bash
sudo realm permit -g 'GG-Linux-Admins@afhamhomelab.local'
```

This implements:

```text
Active Directory
       │
       ├── Normal Domain User
       │        └── Linux Login DENIED
       │
       └── GG-Linux-Admins
                └── Linux Login ALLOWED
```

A positive and negative authentication test was performed.

Authorized user:

```text
mafham@afhamhomelab.local
→ Login successful
```

Unauthorized domain user:

```text
fhaneefa@afhamhomelab.local
→ Permission denied
```

This demonstrates **least privilege and group-based access control**.

---

### 05.31 — Active Directory Controlled sudo

Linux login access and administrative privilege were intentionally treated as separate permissions.

First the AD group was verified:

```bash
getent group 'GG-Linux-Admins@afhamhomelab.local'
```

Then a dedicated sudoers configuration was created:

```bash
sudo visudo -f /etc/sudoers.d/ad-linux-admins
```

Configuration:

```text
%gg-linux-admins@afhamhomelab.local ALL=(ALL:ALL) ALL
```

The `%` indicates that the rule applies to a **group**.

Configuration validation:

```bash
sudo visudo -c
```

The sudo configuration parsed successfully.

AD administrator privilege was then tested:

```bash
su - 'mafham@afhamhomelab.local'
```

```bash
sudo -l
```

```bash
sudo whoami
```

Result:

```text
root
```

This successfully demonstrated:

```text
Active Directory User
        ↓
GG-Linux-Admins
        ↓
Linux Login Permission
        ↓
sudo Authorization
        ↓
Root-Level Administration
```

Administrators therefore use their **individual Active Directory identity** rather than sharing the Linux root password.

---

## Linux Security Architecture

The completed Linux security model is:

```text
                    Windows Server 2025
                         SRV-DC01
                    Active Directory
                    afhamhomelab.local
                           │
                  Kerberos / LDAP / DNS
                           │
                           ▼
                     LINUX-SRV01
                           │
                ┌──────────┼──────────┐
                │          │          │
               SSSD       UFW       Samba
                │                     │
        AD Authentication          ITShare
                │                     │
        GG-Linux-Admins         SMB / TCP 445
                │                     │
         Login Permission          WIN11-CL01
                │
               sudo
                │
               root
```

---

## Enterprise Skills Practiced

This Linux stage provided hands-on experience with:

- Ubuntu Server deployment
- Linux CLI administration
- Linux filesystem structure
- Users and groups
- UID/GID concepts
- File ownership
- Linux permissions
- `chmod`, `chown`, and `chgrp`
- Special permissions / setgid
- sudo administration
- APT package management
- systemd service management
- Linux networking
- DNS troubleshooting
- Listening-port analysis
- SSH administration
- SSH key authentication
- SSH security hardening
- UFW firewall configuration
- LVM storage administration
- Linux logging with `journalctl`
- Bash scripting
- Cron scheduled tasks
- Samba / SMB file sharing
- Windows-to-Linux file sharing
- Active Directory DNS discovery
- Kerberos
- SSSD
- realmd
- Active Directory domain joining
- AD user authentication on Linux
- AD group resolution
- Group-based server access
- Least-privilege administration
- AD-controlled sudo
- Linux troubleshooting

---

## Troubleshooting Methodology Practiced

Throughout the Linux stage I followed a structured troubleshooting approach:

```text
Identify the problem
        ↓
Check configuration
        ↓
Check service status
        ↓
Check listening ports
        ↓
Check DNS / network connectivity
        ↓
Check firewall
        ↓
Check authentication / permissions
        ↓
Review logs
        ↓
Test from client
```

This approach was used across SSH, DNS, Samba, SSSD, Active Directory and Linux permissions troubleshooting.

---

## Current Status

| Linux Administration Area | Status |
|---|---|
| Linux Server Deployment | ✅ Completed |
| Ubuntu Server | ✅ Completed |
| Users & Groups | ✅ Completed |
| File Permissions | ✅ Completed |
| sudo | ✅ Completed |
| Package Management | ✅ Completed |
| Linux Networking | ✅ Completed |
| SSH | ✅ Completed |
| SSH Key Authentication | ✅ Completed |
| SSH Hardening | ✅ Completed |
| Storage & LVM | ✅ Completed |
| systemd / Services | ✅ Completed |
| Scheduled Tasks | ✅ Completed |
| Logging | ✅ Completed |
| UFW Firewall | ✅ Completed |
| Security Hardening | ✅ Completed |
| Samba | ✅ Completed |
| Bash Scripting | ✅ Completed |
| Linux Troubleshooting | ✅ Completed |
| Active Directory Integration | ✅ Completed |
| AD Group-Based Access | ✅ Completed |
| AD-Controlled sudo | ✅ Completed |
| Debian | ⏳ Planned |

---

### Key Outcome

The Linux server is no longer an isolated VM.

`LINUX-SRV01` is now integrated into the wider Enterprise HomeLab with:

**Proxmox virtualization → pfSense networking/security → Windows Server DNS → Active Directory → Kerberos/SSSD authentication → AD security groups → Linux authorization → Samba → Windows clients.**

This stage provided practical experience administering a Linux server in a mixed **Windows + Linux enterprise-style environment**.
