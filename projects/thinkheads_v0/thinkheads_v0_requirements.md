---
Project: AI-Driven Website
Type: Requirements
Date: 2025-07-17
---

# ThinkHeads.ai Website Requirements

## Overview
The AI-driven website serves as the central hub for thinkheads.ai, showcasing all sub-products (Learning Assistant, Meeting Room, Online Card Game, User Profiles) and portfolio content. It features a chat-based navigation interface powered by an LLM (Ollama) to guide users through features and documentation. This document outlines functional and non-functional requirements to ensure the website supports AI/ML/DL learning, portfolio development, and employability. Requirements are designed for solo development within a 20-hour/week schedule, using Proxmox (AMD 7700, 96 GB DDR5, dual RTX 5060 Ti GPUs, NVMe storage) and Linode (4 GB RAM, 2 CPU cores, 80 GB storage) with the tech stack (Cloudflare, Nginx, PostgreSQL, Python/FastAPI, Linux, Ollama, Hugo).

## Functional Requirements
The website must provide the following capabilities to meet user and portfolio needs:

| ID  | Requirement Description                              | Priority | Acceptance Criteria                                      |
|-----|-----------------------------------------------------|----------|---------------------------------------------------------|
| FR01 | **Chat-Based Navigation**: Provide an LLM-powered chat interface to guide users to sub-products and portfolio content. | High     | - Users can input text queries via a web interface.<br>- LLM (Ollama) responds with links to sub-products or documentation.<br>- Response time <2 seconds for 95% of queries.<br>- Supports at least 10 concurrent users. |
| FR02 | **Portfolio Hosting**: Host static content (project documentation, blog posts) using Hugo. | High     | - Markdown documents rendered as HTML pages.<br>- Accessible via thinkheads.ai with clear navigation.<br>- Supports 100+ unique visitors/day without performance degradation. |
| FR03 | **Sub-Product Integration**: Provide entry points to sub-products (e.g., links or API calls to Learning Assistant, Meeting Room). | High     | - Each sub-product accessible via chat or static links.<br>- Seamless redirects to sub-product interfaces (e.g., FastAPI endpoints).<br>- No broken links or errors. |
| FR04 | **User Session Management**: Store chat session data for personalized responses. | Medium   | - Session data stored in PostgreSQL (e.g., user ID, chat history).<br>- Sessions persist for 24 hours.<br>- Secure data handling with encryption. |
| FR05 | **Blog Section**: Host AI/ML/DL learning insights and project updates. | Medium   | - Blog posts rendered from markdown via Hugo.<br>- Supports at least 10 posts with tags and search functionality.<br>- Accessible to all visitors. |

## Non-Functional Requirements
The website must meet the following performance, security, and scalability standards:

| ID  | Requirement Description                              | Priority | Acceptance Criteria                                      |
|-----|-----------------------------------------------------|----------|---------------------------------------------------------|
| NFR01 | **High Availability**: Ensure website uptime and reliability. | High     | - 99% uptime (measured monthly) via Cloudflare and Nginx.<br>- Downtime <10 minutes/month for maintenance. |
| NFR02 | **Security**: Protect website and user data.         | High     | - HTTPS via Cloudflare SSL/TLS.<br>- Cloudflare Tunnel for secure API access.<br>- No vulnerabilities (e.g., SQL injection, XSS) in OWASP Top 10. |
| NFR03 | **Scalability**: Handle expected traffic and growth. | High     | - Supports 100+ unique visitors/day on Linode (4 GB RAM).<br>- Static content cached via Cloudflare.<br>- API endpoints (FastAPI) handle 10 concurrent requests. |
| NFR04 | **Performance**: Ensure fast load times and responsiveness. | High     | - Page load time <2 seconds for static content.<br>- Chat response time <2 seconds for LLM queries.<br>- Responsive design for mobile and desktop. |
| NFR05 | **Maintainability**: Enable easy updates and monitoring. | Medium   | - Markdown updates via Git push, auto-deployed via n8n.<br>- Monitoring via RustDesk and n8n alerts for downtime or errors.<br>- Documentation for all components. |

## Technical Constraints
- **Hardware**:
  - **Proxmox**: Hosts LLM (Ollama) in LXC container (`dockProd1`, 1 RTX 5060 Ti GPU) for chat functionality. Limited GPU availability requires scheduling with other sub-products (e.g., User Profiles).
  - **Linode**: Hosts static site (Hugo, Nginx) and FastAPI endpoints. 4 GB RAM limits complex backend services; prioritize static content and lightweight APIs.
- **Software**:
  - Hugo for static site generation, served via Nginx on Linode.
  - FastAPI for API endpoints (chat, sub-product integration), hosted on Linode or Proxmox.
  - PostgreSQL for session data and RAG embeddings, hosted on `dockProd2` (Proxmox) and mirrored on Linode.
  - Ollama for LLM, running on Proxmox with RAG pipeline using markdown documents.
  - Cloudflare for DNS, security, and caching; Cloudflare Tunnel for secure access.
  - n8n for automation (e.g., content deployment, monitoring), hosted on Proxmox.
  - RustDesk for remote management of Proxmox and Linode.
- **Time**: 20 hours/week, with ~90 hours allocated for website MVP (FR01-FR03, NFR01-NFR04) by October 2025, per **3.2 Project_Roadmap.md**.
- **Solo Operation**: Automation (n8n) and AI tools (Ollama) maximize productivity. No external human collaborators.

## User Flows
- **Portfolio Visitor (Employer/Tech Community)**:
  1. Access thinkheads.ai via browser.
  2. Interact with chat interface (FR01) to explore sub-products or documentation.
  3. Browse static portfolio content (FR02) or blog posts (FR05).
  4. Click links to sub-products (FR03) for demos (e.g., Learning Assistant).
- **Self (Developer)**:
  1. Update markdown content via Git on Proxmox.
  2. Monitor performance via RustDesk and n8n alerts (NFR05).
  3. Test chat functionality and RAG responses locally (Proxmox) before deployment.
- **RAG Integration**:
  - Markdown requirements and documentation feed into Ollama (via PostgreSQL embeddings) for context-aware chat responses (FR01) and Meeting Room planning.

## RAG Integration
- **Usage**: This document feeds into the Meeting Room sub-product’s RAG pipeline (Ollama, PostgreSQL) to guide development and validate requirements.
- **Structure**: Consistent headers, tables, and metadata ensure parseability. Requirement IDs and acceptance criteria provide context for LLM-driven planning.
- **Storage**: Store in Git repository on Proxmox, sync to Linode for public access on thinkheads.ai, embed in PostgreSQL for RAG queries.

## Success Metrics
- **Feature Completion**: Deliver high-priority requirements (FR01-FR03, NFR01-NFR04) by October 2025, per **3.2 Project_Roadmap.md**.
- **Learning Outcomes**: Master LLM integration (Ollama, RAG) and full-stack development (FastAPI, Hugo, Nginx) through website development.
- **Portfolio Impact**: Deploy website MVP on thinkheads.ai, achieving 10+ employer views via X/LinkedIn by November 2025.
- **Performance**: Achieve 99% uptime, <2s page load time, and <2s chat response time for 95% of requests.
- **Engagement**: Attract 100+ unique visitors to thinkheads.ai by February 2026.
  