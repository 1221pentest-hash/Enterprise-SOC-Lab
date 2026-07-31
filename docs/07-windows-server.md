# Windows Server 2022 Deployment

## Executive Summary

Windows Server 2022 serves as the core infrastructure server for the Enterprise SOC Lab. It functions as the Domain Controller for the **LOROINC.LOCAL** Active Directory domain and hosts critical services including Active Directory Domain Services (AD DS), DNS, and DHCP.

This server provides centralized authentication, authorization, name resolution, and IP address management, forming the foundation of the enterprise environment.

---

# Objectives

The Windows Server deployment was designed to:

- Build an enterprise Active Directory domain.
- Centralize user authentication.
- Provide DNS services.
- Provide DHCP services.
- Apply Group Policy Objects (GPOs).
- Manage users, computers, and security groups.
- Generate security events for monitoring with Wazuh.

---

# Server Information

| Property         | Value                        |
| ---------------- | ---------------------------- |
| Operating System | Windows Server 2022 Standard |
| Hostname         | LOROINC-DC01                 |
| Domain           | LOROINC.LOCAL                |
| Primary Roles    | AD DS, DNS, DHCP             |
| Hypervisor       | VMware Workstation Pro       |

---

# Server Roles

The following Windows Server roles were installed.

## Active Directory Domain Services (AD DS)

Provides centralized identity management for:

- User accounts
- Computer accounts
- Organizational Units
- Security Groups
- Authentication
- Authorization

---

## DNS Server

The DNS Server role provides:

- Internal name resolution
- Active Directory integration
- Service location records (SRV)
- Forward and reverse lookup support

---

## DHCP Server

The DHCP role automatically assigns:

- IP addresses
- Default gateway
- DNS server
- Lease information

This eliminates the need for manual IP configuration on client systems.

---

# Active Directory Overview

The lab domain:

```
LOROINC.LOCAL
```

The domain contains:

- Organizational Units (OUs)
- User Accounts
- Computer Accounts
- Security Groups
- Group Policies

This structure simulates a production enterprise Active Directory environment.

---

# Server Configuration

The following configuration tasks were completed:

- Assigned a static IP address.
- Configured the server hostname.
- Installed Windows updates.
- Promoted the server to a Domain Controller.
- Created the Active Directory forest.
- Installed DNS.
- Installed DHCP.
- Authorized the DHCP server.
- Verified all services were operational.

---

# Enterprise Services

The Windows Server provides the following services to the environment.

| Service               | Purpose                |
| --------------------- | ---------------------- |
| Active Directory      | Authentication         |
| DNS                   | Name Resolution        |
| DHCP                  | IP Address Assignment  |
| Group Policy          | Security Configuration |
| File Sharing          | Resource Access        |
| Remote Administration | Server Management      |

---

# Administrative Tools

The following management consoles were used:

- Server Manager
- Active Directory Users and Computers
- Active Directory Administrative Center
- DNS Manager
- DHCP Manager
- Group Policy Management
- Event Viewer
- Windows PowerShell

---

# PowerShell Commands

Examples of commands used during deployment:

```powershell
Get-ADDomain

Get-ADDomainController

Get-ADUser

Get-ADComputer

Get-Service

Get-DnsServerZone

Get-DhcpServerv4Scope

gpupdate /force

gpresult /r

ipconfig /all
```

---

# Validation

The deployment was validated by confirming:

- Domain Controller operational.
- Active Directory services running.
- DNS resolving internal hostnames.
- DHCP assigning addresses.
- Windows 11 successfully joined the domain.
- Group Policy applied successfully.
- Administrative tools functioning correctly.

---

# Security Configuration

Security measures implemented include:

- Strong password policy.
- Account lockout policy.
- Security Groups.
- Organizational Units.
- Group Policy Objects.
- Restricted administrative privileges.

These controls reflect common enterprise security practices.

---

# Troubleshooting

## Domain Join Failure

Possible causes:

- Incorrect DNS server.
- Time synchronization issues.
- Firewall configuration.
- Network connectivity.

---

## DNS Problems

Verify:

- DNS service status.
- DNS zone configuration.
- Client DNS settings.

---

## DHCP Issues

Verify:

- DHCP service running.
- Scope activated.
- Available IP addresses.
- Client lease renewal.

---

## Group Policy Not Applying

Verify:

```powershell
gpupdate /force

gpresult /r
```

Review the applied policies and investigate any errors.

---

# Screenshots

Include the following screenshots:

- Server Manager
- Installed Roles
- Active Directory Users and Computers
- DNS Manager
- DHCP Console
- Group Policy Management
- Event Viewer
- Windows PowerShell
- Domain Properties

---

# Lessons Learned

Deploying Windows Server 2022 provided practical experience with enterprise identity management and infrastructure services. Understanding how Active Directory, DNS, DHCP, and Group Policy interact is fundamental for system administrators and IT support professionals.

The server became the central point of administration for the entire Enterprise SOC Lab, supporting authentication, policy enforcement, networking, and security monitoring.

---

# Related Documentation

- 04-vmware-deployment.md
- 05-network-design.md
- 08-active-directory.md
- 09-dns-dhcp.md
- 12-wazuh-siem.md