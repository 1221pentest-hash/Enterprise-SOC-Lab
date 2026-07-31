# DNS and DHCP Infrastructure

## Executive Summary

The Enterprise SOC Lab relies on Domain Name System (DNS) and Dynamic Host Configuration Protocol (DHCP) services hosted on Windows Server 2022. These services provide automatic network configuration, reliable name resolution, and seamless integration with Active Directory Domain Services (AD DS).

DNS and DHCP are fundamental to enterprise Windows environments. Proper configuration ensures that domain-joined systems can locate domain controllers, authenticate users, apply Group Policy, and communicate across the network without manual configuration.

---

# Objectives

The DNS and DHCP deployment was designed to:

- Provide centralized name resolution.
- Automatically assign IP addresses.
- Support Active Directory authentication.
- Simplify workstation deployment.
- Eliminate manual network configuration.
- Improve network reliability.
- Support enterprise scalability.

---

# Infrastructure Overview

| Service | Server | Purpose |
|----------|--------|---------|
| DNS | LOROINC-DC01 | Name Resolution |
| DHCP | LOROINC-DC01 | IP Address Assignment |
| Domain | LOROINC.LOCAL | Active Directory |

---

# DNS Architecture

DNS is integrated with Active Directory and provides name resolution for all domain-joined systems.

Example domain:

```
LOROINC.LOCAL
```

Primary responsibilities include:

- Hostname resolution
- Domain Controller discovery
- Service (SRV) records
- Active Directory integration
- Internal resource access

---

# DNS Zone Structure

```
LOROINC.LOCAL
│
├── LOROINC-DC01
├── WIN11-LORO
├── loroinc-ub01
```

The DNS server automatically resolves hostnames to IP addresses within the enterprise network.

---

# DNS Benefits

Using internal DNS provides:

- Centralized management
- Faster hostname resolution
- Active Directory support
- Reduced administrative effort
- Improved reliability

---

# DHCP Architecture

The DHCP Server role automatically distributes network configuration to client systems.

Assigned settings include:

- IPv4 Address
- Subnet Mask
- Default Gateway
- Preferred DNS Server
- Lease Duration

This eliminates the need to manually configure client devices.

---

# DHCP Scope Example

| Setting | Value |
|----------|-------|
| Scope Name | LOROINC-LAN |
| Start Address | 192.168.50.100 |
| End Address | 192.168.50.200 |
| Subnet Mask | 255.255.255.0 |
| Gateway | 192.168.50.2 |
| DNS Server | 192.168.50.10 |

---

# Client Configuration Process

When a Windows client starts:

1. Requests an IP address.
2. Receives an available address from DHCP.
3. Receives DNS server information.
4. Locates the Domain Controller.
5. Authenticates to Active Directory.
6. Applies Group Policy.
7. Accesses enterprise resources.

This process occurs automatically without user intervention.

---

# Administrative Tools

The following tools were used:

- DNS Manager
- DHCP Manager
- Server Manager
- Windows PowerShell
- Command Prompt

---

# Useful Commands

### Windows

```powershell
ipconfig /all

ipconfig /release

ipconfig /renew

ipconfig /flushdns

nslookup

Resolve-DnsName

Get-DnsServerZone

Get-DhcpServerv4Scope
```

### Linux

```bash
hostname

ip addr

ip route

cat /etc/resolv.conf

ping

host

nslookup
```

---

# Validation

DNS validation included:

- Successful hostname resolution
- Domain controller discovery
- Domain login
- Internal name resolution

DHCP validation included:

- Automatic IP assignment
- Correct subnet mask
- Correct gateway
- Correct DNS server
- Successful lease renewal

---

# Troubleshooting

## DNS Resolution Failure

Verify:

- DNS Server service is running.
- Client DNS settings point to the Domain Controller.
- DNS zone exists.
- Network connectivity.

Useful commands:

```powershell
nslookup

Resolve-DnsName

ipconfig /flushdns
```

---

## DHCP Not Assigning Addresses

Verify:

- DHCP service is running.
- Scope is activated.
- Address pool has available leases.
- Server is authorized.
- Client renews its lease.

Useful commands:

```powershell
ipconfig /release

ipconfig /renew
```

---

## Client Cannot Locate Domain Controller

Possible causes:

- Incorrect DNS configuration
- Firewall restrictions
- Network connectivity
- Domain Controller unavailable

---

# Screenshots

Include:

- DNS Manager
- Forward Lookup Zone
- DHCP Console
- DHCP Scope
- IP Configuration
- Successful nslookup
- Successful ping
- Successful domain authentication

---

# Lessons Learned

DNS and DHCP are critical services in every Windows enterprise environment. Active Directory depends heavily on DNS for authentication and service discovery, while DHCP simplifies network administration by automatically configuring client devices.

Implementing both services in the Enterprise SOC Lab provided practical experience with enterprise networking fundamentals and reinforced the importance of infrastructure services in supporting identity management and secure communication.

---

# Related Documentation

- 05-network-design.md
- 07-windows-server.md
- 08-active-directory.md
- 10-ubuntu-server.md
- 12-wazuh-siem.md