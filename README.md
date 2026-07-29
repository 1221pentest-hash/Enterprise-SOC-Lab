# 🔒 Enterprise-SOC-Lab — Security Operations Environment

> A self-built, fully functional Security Operations Center (SOC) environment designed to simulate real-world threat detection, incident response, and network security monitoring.

---

## 📌 Project Overview

This home lab replicates a small enterprise security environment. The goal is to practice hands-on blue team skills — log analysis, SIEM alerting, firewall management, and Active Directory administration — while also running controlled offensive scenarios to validate detection coverage.

**Status:** 🟡 In progress — actively expanding

---

## 🏗️ Lab Architecture

```
┌─────────────────────────────────────────────────────────┐
│                     VMware Workstation                  │
│                                                         │
│  ┌──────────────┐    ┌──────────────┐                  │
│  │  OPNsense    │    │ Windows      │                  │
│  │  Firewall /  │◄──►│ Server 2022  │                  │
│  │  Router      │    │ (AD, DNS,    │                  │
│  │              │    │  DHCP, GPO)  │                  │
│  └──────┬───────┘    └──────────────┘                  │
│         │                                               │
│  ┌──────▼───────┐    ┌──────────────┐                  │
│  │  Ubuntu      │    │  Windows 11  │                  │
│  │  (Wazuh      │◄──►│  Endpoint    │                  │
│  │   SIEM)      │    │  (monitored) │                  │
│  └──────────────┘    └──────────────┘                  │
│                                                         │
│  ┌──────────────┐                                       │
│  │  Parrot OS   │  ← Offensive / attack simulation      │
│  │  (Red Team)  │                                       │
│  └──────────────┘                                       │
└─────────────────────────────────────────────────────────┘
```

---

## 🧰 Tech Stack

| Component | Technology | Role |
|---|---|---|
| Hypervisor | VMware Workstation | Host all VMs |
| Firewall / Router | OPNsense | Network segmentation, traffic inspection, firewall rules |
| SIEM | Wazuh (Ubuntu) | Log ingestion, alerting, dashboards |
| Domain Controller | Windows Server 2022 | Active Directory, DNS, DHCP, GPO |
| Endpoint | Windows 11 | Monitored workstation (Wazuh agent) |
| Attack Platform | Parrot OS | Offensive testing, attack simulation |

---

## ✅ What's Been Built

### 🔥 Firewall & Network (OPNsense)
- Configured firewall rules to segment lab into isolated network zones
- Set up inter-VLAN routing and traffic inspection rules
- Enabled logging of blocked/allowed traffic for SIEM ingestion
- Configured DNS and DHCP services for the lab network

### 🏢 Active Directory (Windows Server 2022)
- Deployed a full AD DS environment from scratch
- Created Organizational Units (OUs), users, and security groups
- Configured Group Policy Objects (GPOs) for endpoint hardening
- Integrated endpoints as domain-joined machines

### 📊 SIEM & Monitoring (Wazuh on Ubuntu)
- Deployed Wazuh manager and installed agents on Windows and Linux endpoints
- Configured log ingestion from Windows Event Logs, Sysmon, and OPNsense
- Built custom detection rules to identify suspicious activity
- Analyzed security dashboards for anomalies and alert patterns

### ⚔️ Attack Simulation (Parrot OS)
- Conducted controlled attack scenarios against lab endpoints
- Used Nmap for host discovery and port scanning
- Used Wireshark to capture and analyze network traffic
- Validated Wazuh detection rules against simulated attacks
- Documented detection gaps and tuned alerting thresholds

---

## 📋 Skills Demonstrated

`Network Security` `SIEM` `Threat Detection` `Incident Response` `Firewall Configuration`
`Active Directory` `GPO` `Log Analysis` `Linux Administration` `Windows Server`
`Virtualization` `Blue Team` `Offensive Security (basic)` `Security Monitoring`

---

## 🗺️ Roadmap — What's Coming Next

- [ ] Add Sysmon on Windows endpoints for enhanced log detail
- [ ] Configure Wazuh vulnerability detection module
- [ ] Integrate Nessus for scheduled vulnerability scans
- [ ] Add pfSense IDS/IPS (Suricata) rules
- [ ] Build automated incident response playbook with n8n
- [ ] Document full incident investigation walkthroughs
- [ ] Add a second domain for trust relationship testing

---

## 📁 Repository Structure

```
soc-home-lab/
├── README.md
├── architecture/
│   └── lab-diagram.png
├── configs/
│   ├── opnsense-firewall-rules.md
│   ├── wazuh-custom-rules.xml
│   └── ad-gpo-settings.md
├── playbooks/
│   └── incident-response-template.md
└── walkthroughs/
    └── attack-simulation-01.md
```

---

## 👤 About

**Israel Loyo** — Aspiring Cybersecurity Analyst | IT Support Technician
📍 Montréal, QC | Open to remote & hybrid opportunities
🎓 Cybersecurity Analyst Diploma — Willis College
📜 CCNA — In Progress

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/YOUR-PROFILE-HERE)

---

> *"The best way to learn security is to build the environment, break it, and fix it."*
