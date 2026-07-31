# OPNsense Firewall Deployment

## Executive Summary

The Enterprise SOC Lab uses OPNsense as the perimeter firewall to simulate a secure enterprise network. OPNsense provides routing, firewall protection, network address translation (NAT), and traffic control between the virtual enterprise environment and the Internet.

Deploying a dedicated firewall adds realism to the lab by introducing a security layer commonly found in production environments.

---

# Objectives

The firewall was deployed to accomplish the following objectives:

- Secure the enterprise network.
- Control inbound and outbound traffic.
- Provide network address translation (NAT).
- Route traffic between internal systems and the Internet.
- Simulate an enterprise security appliance.
- Gain experience with enterprise firewall administration.

---

# Environment

| Component       | Value                         |
| --------------- | ----------------------------- |
| Firewall        | OPNsense                      |
| Platform        | VMware Workstation Pro        |
| Deployment Type | Virtual Appliance             |
| Network         | VMware NAT                    |
| Purpose         | Enterprise Perimeter Security |

---

# Network Placement

```
                     Internet
                         │
                         │
                  VMware NAT Network
                         │
                         ▼
                 +-----------------+
                 |    OPNsense     |
                 |    Firewall     |
                 +-----------------+
                         │
      ┌──────────────────┼──────────────────┐
      │                  │                  │
      ▼                  ▼                  ▼
Windows Server      Windows 11       Ubuntu Server
LOROINC-DC01        WIN11-LORO       Docker Host
```

---

# Firewall Responsibilities

The firewall is responsible for:

- Routing traffic
- Network isolation
- Traffic inspection
- NAT
- Internet connectivity
- Secure communication

---

# Interfaces

## WAN Interface

Purpose

Provides Internet connectivity through VMware NAT.

Responsibilities

- External communication
- Internet access
- Software updates

---

## LAN Interface

Purpose

Connects all enterprise systems.

Connected Systems

- Windows Server
- Windows 11
- Ubuntu Server
- Docker Services
- Wazuh Platform

---

# Network Address Translation (NAT)

NAT allows internal systems to access external resources without exposing private IP addresses.

Benefits include:

- Internal address protection
- Simplified Internet connectivity
- Enterprise-style network design
- Isolation from the physical LAN

---

# Firewall Rules

The firewall was configured to allow legitimate communication required by the lab.

Examples include:

- Windows Update
- Active Directory communication
- DNS
- DHCP
- Docker downloads
- Wazuh agent communication
- Administrative access

Traffic not required for lab functionality should remain blocked by default.

---

# Security Features

The firewall contributes to the security posture by providing:

- Stateful packet inspection
- Network segmentation
- Traffic filtering
- Logging
- Secure routing

---

# Deployment Process

The deployment followed these stages:

1. Deploy OPNsense virtual machine.
2. Assign virtual network adapters.
3. Configure WAN interface.
4. Configure LAN interface.
5. Verify Internet connectivity.
6. Configure firewall rules.
7. Validate internal communication.
8. Test routing.

---

# Validation

The firewall deployment was validated by confirming:

- WAN connectivity
- LAN connectivity
- Internet access
- DNS resolution
- Windows Update functionality
- Docker image downloads
- Wazuh communication
- Communication between all virtual machines

---

# Troubleshooting

## No Internet Access

Possible causes:

- Incorrect VMware adapter
- NAT service stopped
- Incorrect gateway
- Firewall rule blocking traffic

---

## Cannot Reach Another Virtual Machine

Verify:

- IP configuration
- Network adapter
- VMware Virtual Network Editor
- Firewall rules
- DNS configuration

---

## DNS Resolution Failure

Verify:

- Windows Server DNS service
- DNS server settings
- Network connectivity
- Domain configuration

---

# Screenshots

Include the following screenshots:

- OPNsense Dashboard
- Interface Configuration
- Firewall Rules
- NAT Configuration
- Status Overview
- Network Interfaces

---

# Lessons Learned

Deploying OPNsense demonstrated how enterprise environments use dedicated security appliances to protect internal infrastructure. Even within a virtual lab, proper firewall design improves security, network organization, and troubleshooting while providing practical experience with enterprise networking concepts.

---

# Related Documentation

- 04-vmware-deployment.md
- 05-network-design.md
- 07-windows-server.md
- 09-dns-dhcp.md
- 12-wazuh-siem.md