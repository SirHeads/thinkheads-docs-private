---
Project: AI-Driven Website
Type: Specifications
Date: 2025-07-17
Spec-ID: SPEC-AUTO
---

# ThinkHeads.ai Automation and Monitoring Specifications

## Overview
This document details the technical specifications for automation and monitoring of the thinkheads.ai website, corresponding to **SPEC-AUTO** from **4.1.2 Specifications_Overview.md**. It supports requirement NFR05 (maintainability) by automating content deployment and monitoring system health. It is designed for solo development within a 20-hour/week schedule, using n8n and RustDesk on Proxmox.

## Technical Specifications
- **n8n**:
  - **Hosting**: LXC container `dockProd2` on Proxmox (8 GB RAM).
  - **Workflows**:
    - Content deployment: Git pull, rebuild Hugo site, reload Nginx (hourly).
    - Monitoring: Check Linode uptime, Proxmox resource usage, email alerts for issues.
    - RAG updates: Parse markdown, generate embeddings, store in PostgreSQL (daily).
  - **Configuration**: Workflows in `/n8n/workflows/` on Proxmox, triggered via cron.
- **RustDesk**:
  - Remote access to Proxmox and Linode, with secure key exchange.
- **Features**:
  - Automated deployment of markdown updates (NFR05).
  - Real-time monitoring and alerts for downtime or resource issues (NFR05).

## Implementation Details
- **Development**: Configure n8n workflows in VS Code, push to Proxmox Git.
- **Testing**: Test workflows and RustDesk locally on Proxmox.
- **Deployment**: Deploy n8n in `dockProd2`, RustDesk on Proxmox and Linode.
- **RAG Integration**: Store in `/docs/project_details/ai_driven_website/specifications/`, sync to Linode, embed in PostgreSQL for RAG queries.