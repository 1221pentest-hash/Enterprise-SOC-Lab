# Enterprise SOC Lab Troubleshooting Guide

## Executive Summary

Building an enterprise infrastructure requires systematic troubleshooting to identify and resolve issues affecting virtualization, networking, Windows Server, Linux, Docker, Active Directory, and security monitoring.

During the development of the Enterprise SOC Lab, multiple real-world issues were encountered and resolved. This document summarizes those scenarios, the diagnostic process, and the solutions implemented.

---

# Troubleshooting Methodology

The following troubleshooting process was used throughout the project:

1. Identify the problem.
2. Gather system information.
3. Review logs and error messages.
4. Verify network connectivity.
5. Validate service status.
6. Apply corrective actions.
7. Re-test functionality.
8. Document the resolution.

This structured approach reduces downtime and helps ensure consistent problem resolution.

---

# VMware Issues

## Virtual Machine Will Not Start

### Symptoms

- VM powers off immediately.
- Boot failures.
- VMware errors.

### Possible Causes

- Insufficient RAM
- Corrupted VM configuration
- Missing virtual disk
- VMware service failure

### Resolution

- Verify available host resources.
- Check VM configuration.
- Confirm virtual disk availability.
- Restart VMware Workstation.

---

## Network Adapter Missing

### Symptoms

- No network connectivity.
- VM receives no IP address.

### Resolution

- Verify VM network adapter settings.
- Open VMware Virtual Network Editor.
- Confirm VMnet8 is configured correctly.
- Restart VMware network services.

---

# Windows Server Issues

## Cannot Join Domain

### Possible Causes

- Incorrect DNS server
- Domain Controller unavailable
- Time synchronization
- Firewall restrictions

### Verification

```powershell
ipconfig /all

ping LOROINC-DC01

nslookup LOROINC.LOCAL
```

---

## Group Policy Not Updating

### Commands

```powershell
gpupdate /force

gpresult /r
```

Verify:

- Computer is domain joined.
- User has appropriate permissions.
- Domain Controller is reachable.

---

## DNS Resolution Failure

### Commands

```powershell
nslookup

Resolve-DnsName

ipconfig /flushdns
```

Verify:

- DNS service running.
- Correct DNS server configured.
- Active Directory healthy.

---

## DHCP Problems

### Commands

```powershell
ipconfig /release

ipconfig /renew

Get-DhcpServerv4Scope
```

Verify:

- DHCP service running.
- Scope active.
- Address pool available.

---

# Active Directory Issues

## User Cannot Log In

Verify:

- Account enabled.
- Correct password.
- Group membership.
- Domain connectivity.

---

## User Locked Out

Unlock account:

```powershell
Unlock-ADAccount username
```

Investigate:

- Failed authentication attempts.
- Password policy.
- Account lockout threshold.

---

# Ubuntu Server Issues

## No Internet Connectivity

Commands:

```bash
ip addr

ip route

ping 8.8.8.8
```

Verify:

- VMware adapter.
- Gateway.
- DNS configuration.

---

## Package Installation Failure

Commands:

```bash
sudo apt update

sudo apt upgrade
```

Verify:

- Internet connectivity.
- Repository availability.
- DNS resolution.

---

# Docker Issues

## Docker Service Not Running

Commands:

```bash
sudo systemctl status docker

sudo systemctl restart docker
```

---

## Container Fails to Start

Commands:

```bash
docker ps -a

docker logs <container>

docker inspect <container>
```

Verify:

- Configuration.
- Ports.
- Volumes.
- Images.

---

## Docker Compose Failure

Commands:

```bash
docker compose config

docker compose down

docker compose up -d
```

---

# Portainer Issues

## Unable to Access Web Interface

Verify:

- Docker running.
- Portainer container healthy.
- Port mapping correct.
- Browser cache cleared.

Commands:

```bash
docker ps

docker logs portainer
```

---

## Forgotten Administrator Password

Resolution:

- Stop Portainer container.
- Reset the administrator password using the official Portainer password reset utility.
- Restart the container.
- Sign in with the new credentials.

---

# Wazuh Issues

## Agent Offline

Verify:

Windows:

```powershell
Get-Service WazuhSvc
```

Restart:

```powershell
Restart-Service WazuhSvc
```

Verify:

- Manager address.
- Firewall.
- Network connectivity.

---

## Dashboard Not Loading

Verify:

```bash
docker ps
```

Confirm:

- Wazuh Dashboard
- Wazuh Manager
- Wazuh Indexer

All containers should be healthy and running.

---

## No Security Events

Verify:

- Agent connected.
- Windows Event Log service.
- Network communication.
- Wazuh Manager operational.

Generate a test event and confirm it appears in Threat Hunting.

---

# Network Troubleshooting

Useful commands:

Windows

```powershell
ipconfig /all

ping

tracert

nslookup

Test-NetConnection
```

Linux

```bash
ip addr

ip route

ping

curl

ss -tuln
```

---

# Validation Checklist

After resolving any issue, verify:

- Virtual machines operational.
- Network connectivity.
- Domain authentication.
- DNS resolution.
- DHCP leases.
- Docker healthy.
- Portainer accessible.
- Wazuh agents active.
- Security events visible.
- Threat Hunting operational.

---

# Lessons Learned

Effective troubleshooting requires a structured methodology rather than trial and error.

Throughout this project, issues involving virtualization, networking, Windows Server, Docker, and Wazuh reinforced the importance of validating one layer at a time. Verifying connectivity, service status, configuration, and logs before making changes significantly reduced troubleshooting time and improved system stability.

Documenting both the problem and its resolution creates a valuable knowledge base for future maintenance and serves as a reference for similar enterprise deployments.

---

# Related Documentation

- 04-vmware-deployment.md
- 07-windows-server.md
- 08-active-directory.md
- 11-docker-portainer.md
- 12-wazuh-siem.md
- 16-command-reference.md