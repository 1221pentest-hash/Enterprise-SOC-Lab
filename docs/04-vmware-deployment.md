# VMware Workstation Deployment

## Executive Summary

The Enterprise SOC Lab is hosted entirely within VMware Workstation Pro and simulates a small enterprise network. The environment was designed to provide hands-on experience with enterprise system administration, networking, cybersecurity, and Security Operations Center (SOC) technologies without requiring physical hardware.

The virtual infrastructure consists of Windows Server 2022, Windows 11 Enterprise, Ubuntu Server 24.04 LTS, and OPNsense Firewall. These systems communicate over an isolated virtual network while maintaining Internet access through VMware NAT networking.

---

# Objectives

The VMware environment was designed to achieve the following objectives:

- Build an enterprise-grade home lab.
- Practice Windows Server administration.
- Deploy Active Directory Domain Services.
- Configure DNS and DHCP.
- Deploy Linux services.
- Host Docker containers.
- Deploy Wazuh SIEM.
- Monitor Windows endpoints.
- Simulate enterprise security operations.

---

# Host System

| Component             | Specification          |
| --------------------- | ---------------------- |
| Hypervisor            | VMware Workstation Pro |
| Host Operating System | Windows 11 Pro         |
| Network Mode          | NAT                    |
| Virtual Network       | VMnet8                 |
| Internet Access       | VMware NAT             |

---

# Virtual Machines

## OPNsense Firewall

Purpose

Acts as the enterprise firewall separating the internal network from the Internet.

Responsibilities

- Firewall
- Routing
- NAT
- Security Policies

---

## Windows Server 2022

Purpose

Acts as the Enterprise Domain Controller.

Installed Roles

- Active Directory Domain Services
- DNS Server
- DHCP Server

Responsibilities

- Authentication
- User Management
- Group Policy
- DNS Resolution
- DHCP Address Assignment

Hostname

LOROINC-DC01

---

## Windows 11 Enterprise

Purpose

Enterprise workstation joined to the Active Directory domain.

Responsibilities

- Domain Authentication
- Endpoint Monitoring
- Security Event Generation
- Policy Validation

Hostname

WIN11-LORO

---

## Ubuntu Server 24.04 LTS

Purpose

Linux server hosting enterprise security services.

Installed Software

- Docker Engine
- Docker Compose
- Portainer
- Wazuh Manager
- Wazuh Dashboard
- Wazuh Indexer

Hostname

loroinc-ub01

---

# Virtual Hardware

Each virtual machine was configured with resources appropriate for a home lab while maintaining acceptable performance.

Example configuration

| VM             |  CPU | Memory |
| -------------- | ---: | -----: |
| OPNsense       |    2 |   2 GB |
| Windows Server |    2 |   4 GB |
| Windows 11     |    2 |   4 GB |
| Ubuntu         |    2 |   6 GB |

---

# Network Configuration

The lab uses VMware NAT networking.

Advantages

- Internet connectivity
- Private enterprise network
- Isolation from the physical LAN
- Simple deployment

Example network

Gateway

192.168.50.2

Windows Server

192.168.50.10

Ubuntu Server

192.168.50.102

Windows 11

192.168.50.100

---

# Deployment Process

The VMware deployment followed these phases:

1. Install VMware Workstation Pro.
2. Configure Virtual Network Editor.
3. Create VMnet8 NAT network.
4. Create all virtual machines.
5. Install operating systems.
6. Configure networking.
7. Verify Internet connectivity.
8. Verify communication between virtual machines.

---

# Validation

The deployment was validated by confirming:

- All virtual machines boot successfully.
- All systems communicate over the enterprise network.
- Internet connectivity is available.
- DNS resolution functions correctly.
- Remote administration works.
- Docker services start automatically.
- Wazuh services initialize successfully.

---

# Screenshots

Include the following screenshots:

- VMware Overview
- Virtual Network Editor
- Virtual Machine Settings
- Running Virtual Machines

---

# Lessons Learned

Building the VMware environment provided practical experience with enterprise virtualization, resource allocation, virtual networking, and infrastructure planning. A stable virtual platform formed the foundation for the remainder of the Enterprise SOC Lab, including Active Directory, Docker, Portainer, and Wazuh SIEM deployment.

---

# Related Documents

- 05-network-design.md
- 06-opnsense-firewall.md
- 07-windows-server.md
- 10-ubuntu-server.md