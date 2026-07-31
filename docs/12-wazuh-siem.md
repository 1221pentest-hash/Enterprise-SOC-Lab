# Wazuh SIEM Deployment

## Executive Summary

The Enterprise SOC Lab uses the Wazuh Security Information and Event Management (SIEM) platform to provide centralized log collection, security monitoring, endpoint visibility, and threat detection.

Wazuh was deployed on Ubuntu Server using Docker Compose and monitors Windows Server 2022 and Windows 11 Enterprise through installed Wazuh agents. This deployment simulates a Security Operations Center (SOC) capable of collecting, analyzing, and visualizing security events in real time.

The implementation demonstrates enterprise security monitoring practices, including endpoint monitoring, authentication auditing, user account monitoring, and threat hunting.

---

# Objectives

The Wazuh deployment was designed to:

- Centralize security monitoring.
- Collect Windows Security Events.
- Monitor endpoint activity.
- Detect authentication events.
- Detect account changes.
- Support threat hunting.
- Provide dashboards for security analysis.
- Simulate enterprise SOC operations.

---

# Environment

| Component            | Value                                      |
| -------------------- | ------------------------------------------ |
| SIEM Platform        | Wazuh                                      |
| Deployment Method    | Docker Compose                             |
| Operating System     | Ubuntu Server 24.04 LTS                    |
| Management Interface | Wazuh Dashboard                            |
| Database             | Wazuh Indexer                              |
| Endpoint Agents      | Windows Server 2022, Windows 11 Enterprise |

---

# Wazuh Architecture

```
                  Windows Server
                   LOROINC-DC01
                         │
                  Wazuh Agent
                         │
                         ▼
                 Wazuh Manager
                         │
            ┌────────────┴────────────┐
            │                         │
            ▼                         ▼
      Wazuh Indexer          Wazuh Dashboard
            │
            ▼
      Security Events
            │
            ▼
      Threat Hunting
```

The same architecture applies to the Windows 11 workstation, which forwards events to the Wazuh Manager for analysis.

---

# Components

## Wazuh Manager

Responsibilities:

- Receive agent data.
- Analyze security events.
- Apply detection rules.
- Generate security alerts.
- Coordinate agent communication.

---

## Wazuh Dashboard

Provides:

- Security dashboards.
- Agent monitoring.
- Threat Hunting.
- Alert visualization.
- Search capabilities.
- Administrative interface.

---

## Wazuh Indexer

Responsible for:

- Event storage.
- Search indexing.
- Fast querying.
- Dashboard data retrieval.

---

## Wazuh Agents

Installed on:

| Endpoint     | Purpose                      |
| ------------ | ---------------------------- |
| LOROINC-DC01 | Domain Controller Monitoring |
| WIN11-LORO   | Workstation Monitoring       |

Agents collect:

- Windows Security Events
- System Logs
- Authentication Events
- User Activity
- Process Information
- System Status

---

# Deployment Process

The deployment followed these phases:

1. Install Docker Engine.
2. Install Docker Compose.
3. Deploy Wazuh containers.
4. Verify container health.
5. Access the Wazuh Dashboard.
6. Install Wazuh agents.
7. Register agents with the manager.
8. Verify agent connectivity.
9. Generate test security events.
10. Confirm event visibility in the dashboard.

---

# Security Monitoring

The following activities were monitored:

- Successful logons
- Failed logons
- User account creation
- User account modifications
- Group membership changes
- Account lockouts
- Password policy events
- Service activity

These events provide visibility into administrative and user actions across the environment.

---

# Threat Hunting

Threat Hunting was used to:

- Search Windows Security Events.
- Review authentication activity.
- Investigate administrative changes.
- Identify suspicious behavior.
- Validate security monitoring functionality.

The Threat Hunting interface allows analysts to filter events by:

- Host
- Event ID
- Username
- Rule level
- Time
- Event source

---

# Validation

The deployment was validated by confirming:

- Wazuh Manager running.
- Wazuh Dashboard accessible.
- Wazuh Indexer healthy.
- Windows Server agent active.
- Windows 11 agent active.
- Events received from both endpoints.
- Authentication events visible.
- Administrative events searchable.
- Threat Hunting operational.

---

# Event Validation

The following Windows events were successfully collected:

| Event | Description                    |
| ----- | ------------------------------ |
| 4624  | Successful Logon               |
| 4625  | Failed Logon                   |
| 4720  | User Account Created           |
| 4722  | User Account Enabled           |
| 4725  | User Account Disabled          |
| 4726  | User Account Deleted           |
| 4732  | User Added to Group            |
| 4740  | Account Locked Out             |
| 4756  | Member Added to Security Group |

These events confirmed end-to-end communication between monitored endpoints and the SIEM platform.

---

# Useful Commands

## Docker

```bash
docker ps

docker compose ps

docker compose logs

docker restart
```

---

## Wazuh Agent (Windows)

```powershell
Get-Service WazuhSvc

Start-Service WazuhSvc

Restart-Service WazuhSvc
```

---

## Ubuntu

```bash
systemctl status docker

docker ps

hostname

ip addr
```

---

# Troubleshooting

## Agent Offline

Verify:

- Agent service running.
- Network connectivity.
- Correct manager address.
- Firewall configuration.

---

## Dashboard Unavailable

Check:

- Docker containers.
- Port mappings.
- Browser connectivity.
- Resource utilization.

---

## No Events Received

Verify:

- Agent registration.
- Wazuh Manager status.
- Docker containers.
- Windows Event Log service.
- Network communication.

---

## Authentication Events Missing

Generate a test event by:

- Logging into Windows.
- Creating a test user.
- Modifying group membership.

Confirm the event appears in the Threat Hunting dashboard.

---

# Screenshots

Include:

- Wazuh Dashboard
- Wazuh Manager Status
- Active Agents
- Windows Server Agent
- Windows 11 Agent
- Threat Hunting Dashboard
- Authentication Events
- User Creation Event
- Group Membership Event
- Live Security Events

---

# Lessons Learned

Deploying Wazuh provided practical experience with enterprise Security Information and Event Management (SIEM) technologies. The platform successfully centralized security event collection from Windows endpoints, enabling real-time monitoring, log analysis, and threat hunting.

Integrating Wazuh with Active Directory demonstrated how authentication, account management, and administrative activity can be monitored within a Security Operations Center. This deployment reflects the foundational capabilities used by SOC analysts to detect, investigate, and respond to security events in enterprise environments.

---

# Related Documentation

- 07-windows-server.md
- 08-active-directory.md
- 10-ubuntu-server.md
- 11-docker-portainer.md
- 13-troubleshooting.md
- 16-command-reference.md