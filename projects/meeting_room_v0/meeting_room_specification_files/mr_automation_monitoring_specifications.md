---
Project: Meeting Room
Type: Specifications
Date: 2025-07-17
Spec-ID: SPEC-MR-AUTO
---

# Meeting Room V0 Automation and Monitoring Specifications

## Overview
This document details the technical specifications for automation and monitoring of the Meeting Room V0, corresponding to **SPEC-MR-AUTO** from **4.3.2 Meeting_Room_Specifications_Overview.md**. It supports requirement NFR05 (maintainability) by automating content updates, action item exports, and system monitoring. It is designed for solo development within a 20-hour/week schedule, using n8n and RustDesk on Proxmox (LXC container `dockProd2`, 8 GB RAM).

## Technical Specifications
- **Technology**: n8n for automation, RustDesk for remote management.
- **Hosting**: LXC container `dockProd2` on Proxmox.
- **Configuration**:
  - **n8n Workflows**:
    - Content Updates: Git pull for markdown updates, rebuild Hugo site, reload Nginx (hourly).
    - Action Item Exports: Export action items from PostgreSQL to markdown, sync to Git (daily).
    - Monitoring: Check Linode uptime, Proxmox resource usage, alert via email for issues (hourly).
    - RAG Updates: Parse markdown and meeting notes, generate embeddings via Ollama, store in PostgreSQL (daily).
  - Workflows stored in `/n8n/workflows/` on Proxmox, triggered via cron.
  - RustDesk: Configured for remote access to Proxmox and Linode, with secure key exchange.
- **Features**:
  - Automate deployment of frontend updates and action item exports (NFR05).
  - Monitor system health (e.g., API latency, database uptime) with email alerts (NFR05).
- **Performance**: Automation tasks complete in <10s, monitoring alerts within 1 minute of issues.

## Implementation Details
- **Development**: Configure n8n workflows in VS Code, push to Proxmox Git.
- **Testing**: Test workflows and RustDesk connectivity in `dockTest1` (Proxmox).
- **Deployment**: Deploy n8n in `dockProd2`, RustDesk on Proxmox and Linode.
- **Dependencies**: Requires frontend (SPEC-MR-FRONT), backend (SPEC-MR-BACK), and database (SPEC-MR-DB) for full functionality.
- **RAG Integration**: Store in `/docs/projects/meeting_room_specifications/`, sync to Linode, embed in PostgreSQL for RAG queries.