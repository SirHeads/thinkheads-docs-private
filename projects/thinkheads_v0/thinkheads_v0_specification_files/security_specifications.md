---
Project: AI-Driven Website
Type: Specifications
Date: 2025-07-17
Spec-ID: SPEC-SEC
---

# ThinkHeads.ai Security Specifications

## Overview
This document details the technical specifications for the security of the thinkheads.ai website, corresponding to **SPEC-SEC** from **4.1.2 Specifications_Overview.md**. It ensures high availability and data protection, supporting requirements NFR01 (high availability) and NFR02 (security). It is designed for solo development within a 20-hour/week schedule, using Cloudflare, Nginx, PostgreSQL, and RustDesk on Proxmox and Linode.

## Technical Specifications
- **Cloudflare**:
  - DNS: A record for `thinkheads.ai` pointing to Linode IP.
  - SSL/TLS: Free certificate for HTTPS, auto-renewed.
  - Tunnel: Secure connection for FastAPI endpoints, configured via Cloudflare Zero Trust.
- **Nginx**: HTTPS enforced, OWASP Top 10 protections (e.g., header sanitization, rate limiting).
- **PostgreSQL**: Encrypted connections, restricted user permissions.
- **Proxmox**: Hardened SSH, LXC isolation, RustDesk with password-protected access.
- **Features**:
  - 99% uptime via Cloudflare and Nginx (NFR01).
  - Secure API access and data protection (NFR02).

## Implementation Details
- **Development**: Configure Cloudflare and Nginx on Linode, SSH/RustDesk on Proxmox.
- **Testing**: Validate HTTPS, Tunnel, and OWASP protections on Linode.
- **Deployment**: Apply configurations via Cloudflare dashboard, Nginx, and Proxmox.
- **RAG Integration**: Store in `/docs/project_details/ai_driven_website/specifications/`, sync to Linode, embed in PostgreSQL for RAG queries.