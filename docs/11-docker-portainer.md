# Docker and Portainer Deployment

## Executive Summary

Docker was deployed on Ubuntu Server 24.04 LTS to provide a modern, containerized platform for enterprise applications within the Enterprise SOC Lab. Docker enables applications to run in isolated containers, simplifying deployment, maintenance, and scalability.

Portainer was deployed as a web-based management interface to simplify container administration, allowing Docker resources to be monitored and managed through a graphical interface.

Together, Docker and Portainer provide the foundation for hosting the Wazuh SIEM platform and demonstrate current enterprise container management practices.

---

# Objectives

The Docker platform was implemented to:

- Deploy containerized enterprise applications.
- Simplify software deployment.
- Isolate services.
- Improve resource utilization.
- Centralize container management.
- Support Wazuh SIEM.
- Gain practical DevOps experience.

---

# Environment

| Component | Value |
|----------|-------|
| Operating System | Ubuntu Server 24.04 LTS |
| Container Runtime | Docker Engine |
| Orchestration | Docker Compose |
| Management Platform | Portainer CE |
| Primary Workload | Wazuh SIEM |

---

# Docker Architecture

```
Ubuntu Server
│
├── Docker Engine
│
├── Docker Compose
│
├── Portainer
│
└── Wazuh Stack
    ├── Wazuh Manager
    ├── Wazuh Dashboard
    └── Wazuh Indexer
```

Docker provides isolation between services while allowing them to communicate over dedicated Docker networks.

---

# Docker Installation

The deployment process included:

1. Update Ubuntu packages.
2. Install Docker Engine.
3. Enable Docker service.
4. Verify installation.
5. Install Docker Compose.
6. Configure Docker to start automatically.

---

# Docker Compose

Docker Compose was used to deploy multi-container applications from a single configuration file.

Advantages include:

- Infrastructure as Code
- Simplified deployments
- Consistent environments
- Easier maintenance
- Service dependency management

---

# Portainer Deployment

Portainer provides a web-based interface for managing Docker.

Features include:

- Container management
- Image management
- Volume management
- Network management
- Stack deployment
- Resource monitoring
- Log viewing

---

# Docker Components

The environment includes:

| Component | Purpose |
|-----------|---------|
| Docker Engine | Container runtime |
| Docker Compose | Multi-container deployment |
| Portainer | Web management interface |
| Docker Networks | Container communication |
| Docker Volumes | Persistent storage |

---

# Container Management

Typical administrative tasks include:

- Starting containers
- Stopping containers
- Restarting containers
- Viewing logs
- Inspecting containers
- Updating images
- Deploying stacks

---

# Common Docker Commands

```bash
docker version

docker info

docker ps

docker ps -a

docker images

docker volume ls

docker network ls

docker logs

docker exec -it

docker inspect

docker restart

docker stop

docker start

docker rm
```

---

# Docker Compose Commands

```bash
docker compose up -d

docker compose down

docker compose ps

docker compose logs

docker compose pull

docker compose restart
```

---

# Portainer Administration

Portainer was used to:

- Monitor container health.
- Deploy Docker stacks.
- Review container logs.
- Restart services.
- Manage persistent volumes.
- Inspect Docker networks.

Administrative access is restricted to authorized users.

---

# Validation

The Docker platform was validated by confirming:

- Docker Engine running.
- Docker Compose operational.
- Portainer accessible.
- Wazuh containers deployed.
- Containers automatically restarted after reboot.
- Docker networking functioning.
- Persistent volumes retained application data.

---

# Troubleshooting

## Docker Service Not Running

Verify:

```bash
sudo systemctl status docker
```

Restart the service if required:

```bash
sudo systemctl restart docker
```

---

## Container Failed to Start

Check logs:

```bash
docker logs <container-name>
```

Inspect configuration:

```bash
docker inspect <container-name>
```

---

## Docker Compose Errors

Validate the compose configuration:

```bash
docker compose config
```

Restart the deployment:

```bash
docker compose down

docker compose up -d
```

---

## Portainer Login Issues

Possible causes:

- Forgotten administrator password.
- Portainer container stopped.
- Browser cache.
- Incorrect mapped port.

Verify:

```bash
docker ps

docker logs portainer
```

---

# Screenshots

Include the following screenshots:

- Docker Version
- Docker Running Containers
- Docker Images
- Docker Networks
- Docker Volumes
- Docker Compose Deployment
- Portainer Dashboard
- Portainer Container View
- Portainer Stack
- Portainer Volumes

---

# Lessons Learned

Deploying Docker and Portainer demonstrated the advantages of containerized infrastructure in enterprise environments. Containers simplify application deployment, reduce configuration inconsistencies, and improve resource efficiency.

Using Docker Compose and Portainer provided practical experience with Infrastructure as Code, container lifecycle management, and modern DevOps administration. These technologies also formed the foundation for the Wazuh SIEM deployment documented in the next section.

---

# Related Documentation

- 10-ubuntu-server.md
- 12-wazuh-siem.md
- 13-troubleshooting.md
- 16-command-reference.md