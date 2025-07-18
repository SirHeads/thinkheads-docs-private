---
Project: Online Card Game
Type: Specifications
Date: 2025-07-17
Spec-ID: SPEC-CG-FRONT
---

# Online Card Game V0 Frontend Specifications

## Overview
This document details the technical specifications for the frontend of the Online Card Game V0, corresponding to **SPEC-CG-FRONT** from **4.4.2 Online_Card_Game_Specifications_Overview.md**. The frontend provides a web interface for multiplayer gameplay and AI-driven challenges, integrated with the AI-driven website, supporting requirements FR01 (multiplayer gameplay), FR02 (AI-driven challenges), FR03 (game state persistence), and NFR04 (performance). It is designed for solo development within a 20-hour/week schedule, hosted on Linode (4 GB RAM, 2 CPU cores, 80 GB storage) using Hugo and Nginx, with Cloudflare for performance.

## Technical Specifications
- **Technology**: Hugo (static site generator), Nginx (web server), JavaScript/WebSocket for dynamic interactions.
- **Hosting**: Linode, integrated with AI-driven website at `/var/www/thinkheads.ai/game`.
- **Configuration**:
  - Hugo site in `/var/www/thinkheads.ai/game`, generated from markdown in Git repository.
  - Nginx configuration (extends AI-driven website’s `/etc/nginx/sites-available/thinkheads.ai`):
    ```nginx
    location /game/ {
        root /var/www/thinkheads.ai;
        index index.html;
        try_files $uri $uri/ /game/index.html;
    }
    location /ws/game/ {
        proxy_pass http://localhost:8000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;
    }
    location /api/game/ {
        proxy_pass http://localhost:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
    ```
  - Cloudflare caching enabled for static content.
- **Features**:
  - Web interface for joining multiplayer games (2-4 players), playing cards, and engaging with AI-driven challenges (FR01, FR02).
  - Real-time updates via WebSocket (`/ws/game/{game_id}`) for game actions (FR01).
  - Game state restoration from PostgreSQL (FR03).
  - Responsive design with Tailwind CSS for mobile/desktop (NFR04).
- **Performance**: Page load time <2s for 95% of requests, game action updates <1s, achieved via Hugo’s static rendering and Cloudflare caching (NFR04).

## Implementation Details
- **Development**: Create Hugo templates and JavaScript in VS Code, push to Git on Proxmox, sync to Linode via rsync.
- **Testing**: Validate interface rendering, WebSocket connectivity, and API interactions locally on Proxmox (`dockTest1`) and on Linode.
- **Deployment**: Run `hugo --minify` on Linode to generate site, served by Nginx.
- **Dependencies**: Requires AI-driven website (Nginx, Cloudflare) for hosting, backend (SPEC-CG-BACK) for API/WebSocket connectivity.
- **RAG Integration**: Store in `/docs/projects/online_card_game_specifications/`, sync to Linode, embed in PostgreSQL for RAG queries.