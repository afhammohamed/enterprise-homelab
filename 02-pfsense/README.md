# 🔥 pfSense Firewall & Network Security

## 📌 Overview

pfSense is deployed as a virtual firewall within the Proxmox VE environment and provides firewalling, routing, network segmentation, VPN connectivity, DNS services, and security controls for the Enterprise HomeLab.

The purpose of this stage was to gain practical experience with enterprise networking concepts including:

- Firewall rule configuration
- Network segmentation
- NAT
- DNS
- DHCP
- Network aliases
- Scheduled firewall rules
- Dynamic DNS
- WireGuard VPN
- Remote access
- Traffic filtering
- Firewall troubleshooting

pfSense acts as an important security and networking component between the HomeLab infrastructure and other networks.

---

## 🏗️ pfSense Deployment

pfSense was deployed as a virtual machine on the Proxmox VE hypervisor.

The firewall VM is hosted on:

```text
Proxmox Node: pve01
VM ID: 100
VM Name: pfSense
Platform: Proxmox VE
Role: Firewall / Router / VPN Gateway
```

Virtualizing pfSense provides a flexible environment for testing firewall configurations, networking technologies, VPN connectivity, and security policies without requiring dedicated firewall hardware.

---

## 🌐 Network Architecture

The HomeLab network follows the general architecture below:

```text
                    Internet
                       |
                       |
                  ISP Router
                       |
                       |
                 Proxmox Host
                       |
                 +-----+-----+
                 |           |
               vmbr0       vmbr1
                 |           |
             WAN Side     Lab Network
                             |
                          pfSense
                             |
                      10.10.10.0/24
                             |
             +---------------+---------------+
             |                               |
      Windows Server 2025             Windows 11 Client
          SRV-DC01                       WIN-11-01
```

The design allows pfSense to control traffic entering and leaving the internal HomeLab network.

---

## 🔌 Proxmox Network Bridges

Multiple Linux bridges are used within Proxmox to provide connectivity for the pfSense virtual machine.

The configuration includes:

```text
vmbr0
Purpose: External / upstream network connectivity

vmbr1
Purpose: pfSense LAN / internal HomeLab network
```

The pfSense VM connects the external network to the isolated HomeLab network.

This architecture provides a practical environment for experimenting with routing, firewall policies, network isolation, and VPN access.

---

## 🖧 pfSense LAN

The internal pfSense LAN gateway is configured as:

```text
10.10.10.1
```

The internal lab network uses:

```text
10.10.10.0/24
```

pfSense provides routing and security controls for systems located on this network.

---

## 🛡️ Firewall Rules

Multiple firewall rule exercises were performed to understand how pfSense processes network traffic.

Testing included:

- Allowing outbound network traffic
- Blocking specific outbound traffic
- ICMP filtering
- TCP connectivity testing
- Destination-based filtering
- Rule ordering
- Alias-based rules
- Scheduled firewall rules

These exercises helped demonstrate how firewall policies can control communication between network devices.

---

## 🚫 ICMP Blocking Test

A firewall rule was created to block ICMP traffic to an external destination.

Testing was performed using:

```powershell
ping 8.8.8.8
```

Initially, the traffic continued to pass because of firewall rule ordering.

The issue was identified by reviewing the pfSense firewall rule list.

After moving the blocking rule above the broader allow rule, the traffic was successfully blocked.

The test then returned timeout responses.

### Lesson Learned

pfSense processes firewall rules from top to bottom.

A more specific blocking rule must therefore be positioned correctly relative to broader allow rules.

This exercise provided practical experience troubleshooting firewall policy behavior.

---

## 🌍 Website Filtering Lab

A firewall exercise was performed to understand destination-based website filtering.

The objective was to test how access to specific external services could be controlled while restricting other destinations.

Testing included:

- Creating firewall aliases
- Configuring destination rules
- Testing TCP connectivity
- Troubleshooting alias behavior
- Reviewing DNS dependencies
- Reviewing firewall rule order

PowerShell was used to verify TCP connectivity during testing.

Example:

```powershell
Test-NetConnection example.com -Port 443
```

This exercise demonstrated that modern website filtering can be more complex than simply allowing a single IP address because large web services often use multiple IP addresses, CDNs, and dynamically changing infrastructure.

---

## 🗂️ Network Aliases

pfSense aliases were configured to simplify firewall administration.

Aliases allow multiple:

- IP addresses
- Networks
- Hosts
- Ports

to be represented by a single reusable object.

Instead of repeatedly entering individual destinations into firewall rules, aliases can be referenced directly.

This makes firewall policies easier to manage and closer to enterprise firewall administration practices.

---

## ⏰ Scheduled Firewall Rules

Scheduled firewall rules were tested to understand time-based network access control.

A schedule can be associated with firewall rules so that a policy is active only during specific periods.

Potential enterprise use cases include:

- Restricting internet access after working hours
- Allowing services only during maintenance windows
- Temporary administrative access
- Scheduled security policies

This exercise provided experience with policy-based access control beyond basic static firewall rules.

---

## 🔀 NAT & Port Forwarding

Network Address Translation concepts were explored within pfSense.

The lab covered the purpose and configuration concepts of:

- Outbound NAT
- Port forwarding
- WAN-to-LAN traffic
- Internal service publishing
- Firewall rules associated with NAT

Port forwarding was evaluated as a method of providing external access to internal services.

However, VPN-based remote access was preferred for administrative access because directly exposing management interfaces to the Internet creates additional security risk.

---

## 🌎 Dynamic DNS

Dynamic DNS was configured to provide a consistent hostname for remote connectivity.

A No-IP DDNS hostname was configured and integrated with the HomeLab environment.

Dynamic DNS solves the problem of changing residential public IP addresses by automatically associating a hostname with the current external IP address.

General flow:

```text
Remote Device
     |
     |
   Internet
     |
     |
DDNS Hostname
     |
     |
Public IP
     |
     |
ISP Router
     |
     |
HomeLab
```

This provides a consistent connection point even when the ISP public IP address changes.

---

## 🔐 WireGuard VPN

WireGuard VPN was configured to provide secure remote access to the HomeLab.

The VPN allows authorized devices to connect to internal infrastructure without directly exposing management interfaces to the public Internet.

WireGuard was configured on pfSense and client configurations were created for remote devices.

Clients tested included:

- Laptop
- iPhone

Remote VPN connectivity was successfully verified.

---

## 📱 Mobile VPN Access

WireGuard was also configured on an iPhone.

After establishing the VPN tunnel, internal HomeLab resources could be accessed remotely.

This demonstrated secure remote infrastructure management from a mobile device.

The general connection path is:

```text
iPhone / Laptop
      |
      |
   Internet
      |
      |
 WireGuard VPN
      |
      |
    pfSense
      |
      |
 HomeLab Network
      |
 +----+-------------------+
 |                        |
Proxmox             Internal Servers
```

---

## 🖥️ Remote Proxmox Access

After establishing the WireGuard tunnel, the Proxmox management interface could be accessed remotely.

This provided secure administrative access to the virtualization infrastructure without exposing the Proxmox web interface directly to the Internet.

The environment was tested using both IP-based and DNS-based access.

---

## 🌐 Internal DNS

Internal DNS records were configured so that HomeLab infrastructure could be accessed using hostnames instead of remembering IP addresses.

Examples include:

```text
pfSense hostname → pfSense LAN IP

Proxmox hostname → Proxmox management IP
```

An internal `.arpa` namespace was also used for HomeLab name resolution.

This provides a more realistic enterprise-style infrastructure environment where services are accessed through DNS names rather than only IP addresses.

---

## 🔎 DNS Troubleshooting

During VPN testing, internal resources were initially reachable using IP addresses but some resources were not accessible using their DNS names.

Troubleshooting included checking:

- DNS server configuration
- Internal DNS records
- WireGuard client DNS settings
- Hostname resolution
- pfSense DNS configuration
- Network routing

After correcting the DNS configuration, internal infrastructure could be accessed using DNS names through the VPN connection.

This provided practical troubleshooting experience across multiple networking layers.

---

## 🧪 Connectivity Testing

Several tools were used throughout the firewall and networking labs.

### ICMP Testing

```powershell
ping 8.8.8.8
```

Used to verify basic network connectivity and firewall ICMP rules.

### TCP Testing

```powershell
Test-NetConnection <hostname> -Port 443
```

Used to verify TCP connectivity and troubleshoot firewall policies.

### DNS Testing

```powershell
nslookup <hostname>
```

Used to verify DNS resolution.

### Route Testing

```powershell
tracert <destination>
```

Used when troubleshooting network paths.

These tools helped identify whether problems were related to routing, firewall rules, DNS, or application connectivity.

---

## 🧯 Troubleshooting Experience

Several real-world networking problems were encountered and resolved during the pfSense implementation.

### Firewall Rule Ordering

**Problem:**

A blocking rule was configured, but traffic continued to pass.

**Cause:**

A broader allow rule was positioned above the blocking rule.

**Solution:**

The rules were reordered so that the specific block rule was evaluated first.

---

### Website Alias Filtering

**Problem:**

After implementing restrictive firewall policies, intended websites were also inaccessible.

**Investigation:**

The firewall alias configuration, DNS resolution, destination addresses, and rule ordering were reviewed.

**Lesson Learned:**

Modern websites may rely on multiple addresses, CDNs, APIs, and external services, making simple IP-based website filtering unreliable.

---

### Remote DNS Resolution

**Problem:**

Internal services could be accessed through their IP addresses over WireGuard, but DNS names initially failed.

**Solution:**

Internal DNS and VPN DNS settings were reviewed and corrected.

After the changes, internal DNS names successfully resolved through the VPN.

---

### WAN Address Configuration

During the configuration process, an address conflict was encountered while modifying the WAN network configuration.

The WAN configuration and upstream router addressing were reviewed and corrected.

This provided additional practical experience troubleshooting IP addressing conflicts between virtual firewall infrastructure and the physical network.

---

## 🔒 Security Design

The HomeLab follows several important security principles.

### VPN Instead of Direct Management Exposure

Administrative services should not be directly exposed to the Internet whenever avoidable.

Remote management is therefore performed through WireGuard VPN.

### Firewall Policy Control

Traffic is controlled using pfSense firewall policies rather than allowing unrestricted communication.

### Network Segmentation

Separate virtual network bridges allow the firewall to sit between network segments.

### Internal DNS

Internal infrastructure hostnames are resolved only within the HomeLab/VPN environment.

### Sensitive Information Protection

Public documentation does not include:

- Private VPN keys
- Passwords
- Public IP addresses
- Authentication credentials
- Recovery information
- Sensitive certificates

---

## 📸 Screenshots

Screenshots documenting the pfSense implementation will be stored in:

```text
02-pfsense/images/
```

Planned screenshots include:

1. pfSense Dashboard
2. pfSense Interface Configuration
3. WAN/LAN Configuration
4. Firewall Rules
5. Firewall Aliases
6. NAT Configuration
7. WireGuard Configuration
8. Dynamic DNS
9. DNS Resolver
10. VPN Connectivity Testing

All screenshots will be reviewed and sanitized before being published.

---

## 🧠 Skills Demonstrated

This stage demonstrates practical experience with:

- pfSense administration
- Virtual firewall deployment
- Network routing
- Firewall policy management
- Rule ordering
- ICMP filtering
- TCP connectivity testing
- Network aliases
- Scheduled firewall policies
- NAT
- Port forwarding concepts
- Dynamic DNS
- WireGuard VPN
- Secure remote access
- Internal DNS
- Network segmentation
- DNS troubleshooting
- VPN troubleshooting
- Network connectivity testing
- Security-focused infrastructure design

---

## 🎯 Key Learning Outcomes

The pfSense stage provided hands-on experience designing and troubleshooting a virtual enterprise-style network.

Key lessons included:

- Firewall rules are evaluated in order.
- Broad allow rules can override intended blocking behavior when positioned incorrectly.
- DNS is critical for both internal infrastructure and VPN connectivity.
- Modern websites cannot always be reliably controlled using simple destination IP rules.
- VPN access is preferable to directly exposing administrative interfaces.
- Network segmentation improves infrastructure security and manageability.
- Testing tools such as Ping, Test-NetConnection, and NSLookup are essential for troubleshooting.
- Firewall, routing, DNS, NAT, and VPN configurations must work together for successful remote connectivity.

---

## 🚀 Future Improvements

Future pfSense improvements may include:

- VLAN segmentation
- Dedicated management VLAN
- Server VLAN
- Client VLAN
- IoT VLAN
- Inter-VLAN firewall policies
- IDS/IPS implementation
- Advanced firewall logging
- Centralized syslog
- Additional VPN security controls
- High availability testing
- Traffic monitoring
- Network performance monitoring

These additions will further develop the HomeLab toward a more complete enterprise-style network architecture.

---

## ✅ Status

**pfSense Firewall Lab: Operational**

Current functionality includes:

- Firewall routing
- Internal HomeLab connectivity
- Firewall rule testing
- Network aliases
- Dynamic DNS
- WireGuard VPN
- Remote laptop connectivity
- Remote mobile connectivity
- Internal DNS resolution
- Secure remote infrastructure access

The pfSense environment will continue to be expanded as additional networking and security technologies are introduced.
