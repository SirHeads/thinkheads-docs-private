---
Project: Learning Assistant
Type: Specifications
Date: 2025-07-17
Spec-ID: SPEC-LA-FRONT
---

# Learning Assistant V0 Frontend Specifications

## Overview
This document details the technical specifications for the frontend of the Learning Assistant V0, corresponding to **SPEC-LA-FRONT** from **4.2.2 Learning_Assistant_Specifications_Overview.md**. The frontend provides a web interface for querying resources, saving notes, and accessing exercises, integrated with the AI-driven website, supporting requirements FR01 (resource suggestions), FR02 (note-taking), FR03 (exercises), and NFR04 (performance). It is designed for solo development within a 20-hour/week schedule, hosted on Linode (4 GB RAM, 2 CPU cores, 80 GB storage) using Hugo and Nginx, with Cloudflare for performance.

## Technical Specifications
- **Technology**: Hugo (static site generator), Nginx (web server), JavaScript for dynamic interactions.
- **Hosting**: Linode, integrated with AI-driven website at `/var/www/thinkheads.ai/learning`.
- **Configuration**:
  - Hugo site in `/var/www/thinkheads.ai/learning`, generated from markdown in Git repository.
  - Nginx configuration (extends AI-driven website’s `/etc/nginx/sites-available/thinkheads.ai`):
    ```nginx
    location /learning/ {
        root /var/www/thinkheads.ai;
        index index.html;
        try_files $uri $uri/ /learning/index.html;
    }
    location /api/learning/ {
        proxy_pass http://localhost:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
    ```
  - Cloudflare caching enabled for static content.
- **Features**:
  - Web interface for querying AI/ML resources (FR01), saving/exporting notes (FR02), and accessing exercises (FR03).
  - Responsive design with Tailwind CSS for mobile/desktop (NFR04).
  - JavaScript for dynamic form submissions to FastAPI endpoints (`/api/learning/resources`, `/api/learning/exercises`).
- **Performance**: Page load time <2s for 95% of requests, achieved via Hugo’s static rendering and Cloudflare caching (NFR04).

## Implementation Details
- **Development**: Create Hugo templates in VS Code, push to Git on Proxmox, sync to Linode via rsync.
- **Testing**: Validate interface rendering and API interactions locally on Proxmox (`dockTest1`) and on Linode.
- **Deployment**: Run `hugo --minify` on Linode to generate site, served by Nginx.
- **Dependencies**: Requires AI-driven website (Nginx, Cloudflare) for hosting, backend (SPEC-LA-BACK) for API connectivity.
- **RAG Integration**: Store in `/docs/projects/learning_assistant_specifications/`, sync to Linode, embed in PostgreSQL for RAG queries.