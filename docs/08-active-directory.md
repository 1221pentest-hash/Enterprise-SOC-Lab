# Active Directory Infrastructure

## Executive Summary

Active Directory Domain Services (AD DS) is the identity and access management platform for the Enterprise SOC Lab. It provides centralized authentication, authorization, directory services, and policy management for all Windows systems within the **LOROINC.LOCAL** domain.

The Active Directory deployment simulates a production enterprise environment by organizing users, computers, organizational units (OUs), and security groups according to business functions.

---

# Objectives

The Active Directory deployment was designed to:

- Centralize user authentication.
- Manage computer accounts.
- Organize business departments.
- Implement Group Policy.
- Apply enterprise security practices.
- Simplify user administration.
- Generate authentication events for SIEM monitoring.

---

# Domain Information

| Property | Value |
|----------|-------|
| Domain Name | LOROINC.LOCAL |
| NetBIOS Name | LOROINC |
| Domain Controller | LOROINC-DC01 |
| Operating System | Windows Server 2022 |

---

# Active Directory Architecture

```
LOROINC.LOCAL
│
├── _LOROINC
│   ├── IT
│   ├── HR
│   ├── Finance
│   ├── Management
│   ├── Computers
│   └── Service Accounts
```

This organizational structure reflects a typical small-to-medium enterprise and simplifies administration through delegated management and policy application.

---

# Organizational Units (OUs)

The following Organizational Units were created:

| OU | Purpose |
|----|---------|
| IT | IT staff accounts |
| HR | Human Resources |
| Finance | Finance department |
| Management | Management accounts |
| Computers | Domain-joined computers |
| Service Accounts | Application and service accounts |

Benefits of using OUs include:

- Logical organization
- Easier administration
- Targeted Group Policy
- Delegation of control
- Improved scalability

---

# Security Groups

Security groups were created to simplify permission management.

| Group | Purpose |
|--------|---------|
| GRP-IT-Admins | IT Administrators |
| GRP-HR-Staff | HR Users |
| GRP-Finance-Staff | Finance Users |
| GRP-All-Employees | Standard Domain Users |

Using security groups follows Microsoft's recommended practice of assigning permissions to groups instead of individual users.

---

# User Management

The Active Directory environment includes user accounts representing different departments.

User account administration includes:

- User creation
- Password management
- Account locking and unlocking
- Group membership
- User property management

These administrative activities generate Windows Security Events that are collected by Wazuh.

---

# Computer Accounts

Domain-joined systems include:

| Computer | Purpose |
|-----------|---------|
| LOROINC-DC01 | Domain Controller |
| WIN11-LORO | Enterprise Workstation |

Joining computers to the domain enables:

- Centralized authentication
- Group Policy processing
- Security monitoring
- Resource access
- Simplified administration

---

# Group Policy

Group Policy Objects (GPOs) were configured to enforce security standards.

Examples include:

- Password complexity
- Minimum password length
- Account lockout policy
- Screen lock timeout
- Login banner
- Security configuration

Policies are applied centrally and automatically to domain-joined systems.

---

# Password Policy

The default domain password policy includes:

- Minimum password length
- Password complexity enabled
- Password history
- Maximum password age
- Account lockout threshold

These settings help reduce the risk of unauthorized access.

---

# Administrative Tools

The following tools were used:

- Server Manager
- Active Directory Users and Computers
- Active Directory Administrative Center
- Group Policy Management
- Event Viewer
- Windows PowerShell

---

# PowerShell Administration

Example commands used during administration:

```powershell
Get-ADDomain

Get-ADUser

Get-ADComputer

Get-ADGroup

New-ADUser

Enable-ADAccount

Disable-ADAccount

Unlock-ADAccount

Add-ADGroupMember

Remove-ADGroupMember

Get-ADOrganizationalUnit

gpupdate /force

gpresult /r
```

---

# Validation

The Active Directory deployment was validated by confirming:

- Domain Controller operational.
- Users successfully created.
- Organizational Units created.
- Security Groups created.
- Computers joined to the domain.
- Group Policy applied successfully.
- Authentication functioning correctly.
- Administrative tools operational.

---

# Security Monitoring

Active Directory activities are monitored by Wazuh.

Examples of monitored events include:

- Successful logons
- Failed logons
- User account creation
- User account modification
- Group membership changes
- Account lockouts
- Password changes

These events provide visibility into authentication and administrative activity.

---

# Troubleshooting

## Client Cannot Join Domain

Verify:

- DNS configuration
- Time synchronization
- Network connectivity
- Domain Controller availability

---

## User Cannot Log In

Verify:

- User account enabled
- Password correctness
- Group membership
- Domain connectivity

---

## Group Policy Not Updating

Run:

```powershell
gpupdate /force

gpresult /r
```

Review the applied policies and Event Viewer logs for errors.

---

# Screenshots

Include the following screenshots:

- Active Directory Users and Computers
- Organizational Units
- User Accounts
- Security Groups
- Group Policy Management
- Default Domain Policy
- PowerShell administration
- Successful domain join

---

# Lessons Learned

Active Directory is the foundation of most Windows enterprise environments. Deploying and administering a domain provided hands-on experience with centralized identity management, authentication, authorization, and policy enforcement.

By implementing Organizational Units, Security Groups, and Group Policy Objects, the lab demonstrates industry-standard administrative practices while generating realistic security events for monitoring with Wazuh SIEM.

---

# Related Documentation

- 07-windows-server.md
- 09-dns-dhcp.md
- 12-wazuh-siem.md
- 13-troubleshooting.md