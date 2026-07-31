# Ubuntu Server Deployment

## Executive Summary

Ubuntu Server 24.04 LTS serves as the Linux infrastructure platform for the Enterprise SOC Lab. It hosts the organization's containerized services, including Docker Engine, Docker Compose, Portainer, and the Wazuh Security Information and Event Management (SIEM) platform.

The server was selected for its long-term support (LTS), stability, security, and widespread adoption in enterprise environments.

---

# Objectives

The Ubuntu Server deployment was designed to:

- Deploy a stable Linux server.
- Host enterprise containerized applications.
- Provide the Docker runtime environment.
- Deploy Portainer for container management.
- Host the Wazuh SIEM platform.
- Practice Linux system administration.
- Integrate Linux services with the Windows enterprise environment.

---

# Server Information

| Property         | Value                   |
| ---------------- | ----------------------- |
| Operating System | Ubuntu Server 24.04 LTS |
| Hostname         | loroinc-ub01            |
| Platform         | VMware Workstation Pro  |
| Primary Role     | Container Host          |
| Environment      | Enterprise SOC Lab      |

---

# System Responsibilities

The Ubuntu server provides the following services:

- Docker Engine
- Docker Compose
- Portainer
- Wazuh Manager
- Wazuh Dashboard
- Wazuh Indexer

These services support security monitoring, container management, and centralized log collection.

---

# Initial Configuration

After installation, the following configuration tasks were completed:

- Updated system packages.
- Configured hostname.
- Verified network connectivity.
- Configured static networking (if applicable).
- Created an administrative user.
- Enabled SSH administration.
- Installed required packages.

---

# Package Management

Ubuntu uses the APT package manager.

Common administrative commands include:

```bash
sudo apt update

sudo apt upgrade

sudo apt install

sudo apt remove

sudo apt autoremove
```

Keeping the system updated helps maintain security and stability.

---

# Network Configuration

The server communicates with:

- Windows Server 2022
- Windows 11 Enterprise
- Docker containers
- Wazuh agents

Connectivity was verified using standard networking tools before deploying enterprise applications.

---

# System Administration

Routine administration includes:

- Managing services
- Monitoring disk usage
- Reviewing system logs
- Updating packages
- Managing users and groups
- Verifying network connectivity

---

# Service Management

System services are managed using `systemctl`.

Examples:

```bash
sudo systemctl status docker

sudo systemctl start docker

sudo systemctl stop docker

sudo systemctl restart docker

sudo systemctl enable docker
```

---

# User Administration

Common commands:

```bash
whoami

id

sudo adduser

sudo usermod

groups

passwd
```

Administrative access is granted using the `sudo` mechanism.

---

# Storage Management

Useful commands:

```bash
df -h

lsblk

mount

du -sh

free -h
```

These commands assist with monitoring storage capacity and system resources.

---

# Networking Commands

Examples:

```bash
ip addr

ip route

hostname

hostnamectl

ping

curl

ss -tuln

netstat -tuln
```

These commands verify network connectivity and listening services.

---

# Security

Security best practices implemented include:

- Regular system updates.
- Least privilege administration.
- Secure SSH access.
- Firewall configuration (where applicable).
- Minimal package installation.
- Strong administrative credentials.

---

# Validation

The Ubuntu deployment was validated by confirming:

- Successful boot.
- Internet connectivity.
- Communication with Windows Server.
- Communication with Windows 11.
- Docker installed successfully.
- Docker Compose functioning.
- Portainer accessible.
- Wazuh services operational.

---

# Troubleshooting

## No Network Connectivity

Verify:

```bash
ip addr

ip route

ping 8.8.8.8
```

Check:

- VMware network adapter
- Gateway
- DNS configuration

---

## Package Installation Fails

Verify:

```bash
sudo apt update
```

Confirm:

- Internet access
- DNS resolution
- Ubuntu repositories

---

## Service Not Running

Check service status:

```bash
sudo systemctl status <service>
```

Review logs:

```bash
journalctl -xe
```

---

# Screenshots

Include:

- Ubuntu Login
- Terminal
- Hostname
- IP Configuration
- System Information
- Docker Installed
- Running Services
- Package Updates

---

# Lessons Learned

Ubuntu Server provides a reliable and lightweight platform for hosting enterprise infrastructure services. Deploying and administering a Linux server strengthened skills in package management, networking, service administration, and troubleshooting.

Hosting Docker, Portainer, and Wazuh on Ubuntu demonstrated how Linux serves as the foundation for many enterprise applications and cybersecurity platforms.

---

# Related Documentation

- 04-vmware-deployment.md
- 05-network-design.md
- 11-docker-portainer.md
- 12-wazuh-siem.md
- 13-troubleshooting.md