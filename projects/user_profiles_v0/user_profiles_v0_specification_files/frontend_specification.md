---
Project: User Profiles
Type: Specifications
Date: 2025-07-17
Spec-ID: SPEC-UP-FRONT
---

# User Profiles V0 Frontend Specifications

## Overview
This document details the technical specifications for the frontend of the User Profiles V0, corresponding to **SPEC-UP-FRONT** from **4.5.2 User_Profiles_Specifications_Overview.md**. The frontend provides a web interface for profile creation, learning progress tracking, and portfolio display, integrated with the AI-driven website, supporting requirements FR01 (profile creation), FR02 (learning progress tracking), FR03 (portfolio integration), and NFR04 (performance). It is designed for solo development within a 20-hour/week schedule, hosted on Linode (4 GB RAM, 2 CPU cores, 80 GB storage) using Hugo and Nginx, with Cloudflare for performance.

## Technical Specifications
- **Technology**: Hugo (static site generator), Nginx (web server), JavaScript for dynamic interactions.
- **Hosting**: Linode, integrated with AI-driven website at `/var/www/thinkheads.ai/profiles`.
- **Configuration**:
  - Hugo site in `/var/www/thinkheads.ai/profiles`, generated from markdown in Git repository.
  - Nginx configuration (extends AI-driven website’s `/etc/nginx/sites-available/thinkheads.ai`):
    ```nginx
    location /profiles/ {
        root /var/www/thinkheads.ai;
        index index.html;
        try_files $uri $uri/ /profiles/index.html;
    }
    location /api/profiles/ {
        proxy_pass http://localhost:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
    ```
  - Cloudflare caching enabled for static content.
- **Features**:
  - Web interface for creating/managing profiles with email/password or OAuth (FR01).
  - Displays learning progress metrics (e.g., completed tasks) integrated with Learning Assistant (FR02).
  - Allows users to upload and display portfolio projects, exportable as markdown (FR03).
  - Responsive design with Tailwind CSS for mobile/desktop (NFR04).
- **Performance**: Page load time <2s for 95% of requests, achieved via Hugo’s static rendering and Cloudflare caching (NFR04).

## Implementation Details
- **Development**: Create Hugo templates and JavaScript in VS Code, push to Git on Proxmox, sync to Linode via rsync.
- **Testing**: Validate interface rendering and API interactions locally on Proxmox (`dockTest1`) and on Linode.
- **Deployment**: Run `hugo --minify` on Linode to generate site, served by Nginx.
- **Dependencies**: Requires AI-driven website (Nginx, Cloudflare) for hosting, backend (SPEC-UP-BACK) for API connectivity.
- **RAG Integration**: Store in `/docs/projects/user_profiles_specifications/`, sync to Linode, embed in PostgreSQL for RAG queries.