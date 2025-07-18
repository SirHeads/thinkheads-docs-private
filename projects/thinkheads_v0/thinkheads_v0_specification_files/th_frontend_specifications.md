---
Project: AI-Driven Website
Type: Specifications
Date: 2025-07-17
Spec-ID: SPEC-FRONT
---

# ThinkHeads.ai Frontend Specifications

## Overview
This document details the technical specifications for the frontend of the thinkheads.ai website, corresponding to **SPEC-FRONT** from **4.1.2 Specifications_Overview.md**. The frontend hosts static portfolio and blog content, supporting requirements FR02 (portfolio hosting), FR05 (blog section), and NFR04 (performance). It is designed for solo development within a 20-hour/week schedule, hosted on Linode (4 GB RAM, 2 CPU cores, 80 GB storage, Debian OS), using Hugo and Nginx, with Cloudflare for performance optimization.

## Technical Specifications
- **Technology**: Hugo (static site generator), Nginx (web server).
- **Hosting**: Linode, with site files in `/var/www/thinkheads.ai`.
- **Features**:
  - Render markdown documentation (e.g., `/docs/`) as HTML portfolio pages (FR02).
  - Blog section with tagged posts and search functionality using Hugo templates (FR05).
  - Responsive design with a CSS framework (e.g., Tailwind) for mobile/desktop (NFR04).
- **Configuration**:
  - Hugo site generated from markdown in Git repository, output to `/var/www/thinkheads.ai`.
  - Nginx serves static content, with Cloudflare caching to reduce load.
- **Performance**: Page load time <2s for 95% of requests, achieved via Hugo’s static rendering and Cloudflare caching (NFR04).

## Implementation Details
- **Development**: Edit markdown in VS Code, push to Git repository on Proxmox, sync to Linode via rsync.
- **Deployment**: Run `hugo --minify` on Linode to generate site, served by Nginx.
- **Testing**: Validate rendering and responsiveness locally on Proxmox (`dockTest1`) and on Linode.
- **RAG Integration**: Store in `/docs/project_details/ai_driven_website/specifications/`, sync to Linode, embed in PostgreSQL for RAG queries by Meeting Room LLM.