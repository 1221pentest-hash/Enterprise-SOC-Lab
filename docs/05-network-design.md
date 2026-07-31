# Enterprise Network Design

## Executive Summary

The Enterprise SOC Lab network was designed to simulate a small business infrastructure while remaining isolated from the physical home network. VMware Workstation NAT networking was selected to provide secure Internet access while allowing communication between all virtual machines.

The network supports Windows Server 2022, Windows 11 Enterprise, Ubuntu Server, OPNsense Firewall, Docker, Portainer, and Wazuh SIEM.

---

# Network Objectives

The network was designed to accomplish the following goals:

- Provide Internet access to all virtual machines.
- Simulate an enterprise LAN.
- Support Active Directory.
- Support DNS and DHCP.
- Allow communication between Windows and Linux systems.
- Support Docker containers.
- Allow Wazuh agent communication.
- Maintain network isolation from the physical network.

---

# Network Topology

```
                    Internet
                        │
                        │
               VMware NAT (VMnet8)
                        │
                        ▼
               Enterprise Virtual LAN
                        │
        ┌───────────────┼────────────────┐
        │               │                │
        ▼               ▼                ▼
   OPNsense       Windows Server     Ubuntu Server
    Firewall        LOROINC-DC01      Docker Host
        │               │                │
        └───────────────┼────────────────┘
                        │
                        ▼
                Windows 11 Client
                  WIN11-LORO
```

---

# IP Addressing

| Device         | IP Address     | Purpose                |
| -------------- | -------------- | ---------------------- |
| VMware Gateway | 192.168.50.2   | NAT Gateway            |
| Windows Server | 192.168.50.10  | Domain Controller      |
| Windows 11     | 192.168.50.100 | Enterprise Workstation |
| Ubuntu Server  | 192.168.50.102 | Docker & Wazuh         |
| OPNsense       | 192.168.50.x   | Firewall               |

---

# DNS Design

DNS services are hosted on Windows Server 2022.

Responsibilities include:

- Domain name resolution
- Active Directory integration
- Client name resolution
- Service location records

Example:

```
loroinc.local
```

---

# DHCP Design

DHCP services are also hosted on Windows Server.

Responsibilities include:

- Automatic IP address assignment
- Gateway configuration
- DNS server assignment
- Lease management

---

# Routing

Traffic flows through VMware NAT before reaching the Internet.

Internal communication remains within the virtual network.

Example communication path:

```
Windows 11
      │
      ▼
Windows Server
      │
      ▼
Ubuntu Server
      │
      ▼
Docker
      │
      ▼
Wazuh Manager
```

---

# Connectivity Validation

The network was validated using the following commands.

Windows

```powershell
ipconfig /all

ping

nslookup

tracert

Test-NetConnection
```

Ubuntu

```bash
ip addr

hostname

ip route

ping

curl
```

---

# Network Services

| Service          | Server         |
| ---------------- | -------------- |
| Active Directory | Windows Server |
| DNS              | Windows Server |
| DHCP             | Windows Server |
| Docker           | Ubuntu         |
| Portainer        | Ubuntu         |
| Wazuh Manager    | Ubuntu         |
| Wazuh Dashboard  | Ubuntu         |
| Wazuh Indexer    | Ubuntu         |

---

# Validation Results

The network deployment was considered successful after verifying:

- Internet access from every virtual machine.
- Communication between Windows Server and Windows 11.
- Communication between Windows Server and Ubuntu.
- DNS name resolution.
- DHCP address assignment.
- Successful Wazuh agent communication.
- Successful Docker communication.

---

# Screenshots

Include the following screenshots:

- VMware Network Editor
- ipconfig /all
- ip addr
- Successful ping tests
- Docker networking
- Wazuh Dashboard
- Active agents

---

# Lessons Learned

A properly designed network is the foundation of every enterprise environment.

Before deploying enterprise services such as Active Directory, Docker, Portainer, or Wazuh, reliable network communication, DNS resolution, and Internet connectivity must be verified.

Network validation simplified later deployment and troubleshooting by ensuring every component could communicate successfully.

---

# Related Documentation

- 04-vmware-deployment.md
- 06-opnsense-firewall.md
- 07-windows-server.md
- 12-wazuh-siem.md