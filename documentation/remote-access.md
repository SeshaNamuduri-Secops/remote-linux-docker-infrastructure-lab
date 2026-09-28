# Remote Access

## Overview

Tailscale was configured to provide private connectivity between the administrator Mac and the Fedora infrastructure server.

The setup allows the administrator to securely access the Fedora server from different networks without exposing SSH or the Docker API directly to the public Internet.

## Architecture

```text
Mac Administrator
       |
       | Tailscale
       |
       v
Fedora Infrastructure Server
       |
       +-- SSH
       +-- Docker Engine
       +-- Docker Compose
       +-- Nginx
       +-- PostgreSQL
Configuration
Tailscale was installed and enabled on the Fedora server.
The Fedora server was authenticated to the project administrator's Tailscale network.
Tailscale was also installed on the Mac administrator workstation and authenticated to the same network.
Remote SSH Validation
SSH connectivity was tested from the Mac to the Fedora server using the Fedora Tailscale address.
Example:
ssh <fedora-user>@<tailscale-ip>

After connecting, the server identity was validated using:
hostname

Expected result:
fedora

Security Considerations
- SSH was not exposed through router port forwarding.
- The Docker API was not exposed on TCP port 2375.
- Docker continues to use the local Unix socket.
- Tailscale provides the private connectivity layer between administrator and server.
- Credentials, authentication tokens and private keys are not stored in the repository.
- Tailscale account information and device-specific addresses should not be published unnecessarily.
Remote Administration Model
Administrator Mac
        |
        | Encrypted Tailscale Connectivity
        |
        v
Fedora Server
        |
        +-- SSH Administration
        |
        +-- Docker Administration
        |
        +-- Docker Compose
        |
        +-- Application Services

The Fedora server must remain powered on, connected to the Internet and connected to the Tailscale network for remote administration.
