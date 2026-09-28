cat > README.md <<'EOF'
# Remote Linux Server & Docker Infrastructure Lab

## Overview

A hands-on infrastructure project focused on building, securing, and remotely administering a Fedora Linux server running Docker-based workloads.

## Objectives

- Configure a Linux server for reliable remote administration
- Implement secure SSH-based administration
- Configure and manage Docker Engine
- Build and manage containerized workloads with Docker Compose
- Document infrastructure configuration and operational procedures
- Apply basic security hardening and least-exposure principles
- Validate remote administration from a separate client system

## Architecture

The project uses a Fedora Linux machine as the infrastructure server and a separate client system for remote administration.

```text
Administrator Client
        |
        | SSH
        v
 Fedora Linux Server
        |
        +-- Docker Engine
                |
                +-- Project Containers
