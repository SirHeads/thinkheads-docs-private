---
Project: User Profiles
Type: Requirements
Date: 2025-07-17
---

# User Profiles V0 Requirements

## Overview
The User Profiles V0 is an AI-driven user management system for thinkheads.ai, enabling personalized profiles with AI/ML learning progress tracking and portfolio integration. Integrated with the AI-driven website, it uses Ollama for personalization and PostgreSQL for data storage. This document outlines functional and non-functional requirements to support skill development and portfolio enhancement, designed for solo development within a 20-hour/week schedule, using Proxmox (Ollama, PostgreSQL) and Linode (APIs), per **3.2 Project_Roadmap.md**.

## Functional Requirements
| ID  | Requirement Description                              | Priority | Acceptance Criteria                                      |
|-----|-----------------------------------------------------|----------|---------------------------------------------------------|
| FR01 | **Profile Creation**: Allow users to create and manage profiles with authentication. | High     | - Users create profiles via web interface with email/password.<br>- Supports OAuth (e.g., GitHub).<br>- Profiles stored in PostgreSQL.<br>- Creation completes in <5s. |
| FR02 | **Learning Progress Tracking**: Track and display AI/ML learning progress. | High     | - Tracks completed resources and exercises (via Learning Assistant integration).<br>- Displays progress metrics (e.g., 10+ completed tasks).<br>- Updates reflected in <5s. |
| FR03 | **Portfolio Integration**: Allow users to showcase projects and export profiles. | Medium   | - Users upload project details (markdown), stored in PostgreSQL.<br>- Exportable as markdown for portfolio.<br>- Supports 10+ projects per user.<br>- Export completes in <5s. |

## Non-Functional Requirements
| ID  | Requirement Description                              | Priority | Acceptance Criteria                                      |
|-----|-----------------------------------------------------|----------|---------------------------------------------------------|
| NFR01 | **High Availability**: Ensure system uptime and reliability. | High     | - 99% uptime via Cloudflare and Nginx.<br>- Downtime <10 minutes/month for maintenance. |
| NFR02 | **Security**: Protect user data and interactions.    | High     | - HTTPS via Cloudflare SSL/TLS.<br>- Encrypted PostgreSQL connections.<br>- Secure OAuth and password hashing.<br>- No OWASP Top 10 vulnerabilities. |
| NFR03 | **Scalability**: Handle expected usage.              | Medium   | - Supports 100 concurrent users on Linode (4 GB RAM).<br>- API handles 10+ requests/second.<br>- Cloudflare caching for static content. |
| NFR04 | **Performance**: Ensure fast response times.         | High     | - LLM responses <2s for 95% of queries.<br>- Profile updates <5s.<br>- Responsive web interface for mobile/desktop. |
| NFR05 | **Maintainability**: Enable easy updates and monitoring. | Medium   | - Markdown updates via Git, auto-deployed by n8n.<br>- Monitoring via n8n and RustDesk.<br>- Documentation for all components. |

## Technical Constraints
- **Hardware**:
  - Proxmox: Hosts Ollama (`dockProd1`, 1 RTX 5060 Ti GPU) and PostgreSQL (`dockProd2`, 16 GB RAM).
  - Linode: Hosts FastAPI endpoints, limited by 4 GB RAM; offload LLM tasks to Proxmox.
- **Software**: Ollama, PostgreSQL, FastAPI, n8n, Cloudflare, integrated with AI-driven website (Hugo, Nginx).
- **Time**: ~160 hours for MVP (FR01-FR02, NFR01-NFR04) by August 2026, per **3.2 Project_Roadmap.md**.
- **Solo Operation**: Use n8n for automation, RustDesk for remote management.

## User Flows
- **User (Self)**:
  1. Access User Profiles via thinkheads.ai.
  2. Create/manage profile (FR01), track learning progress (FR02), or export portfolio (FR03).
  3. Share profile link on X/LinkedIn for employer visibility.
- **Employer/Community**:
  1. View public user profiles on thinkheads.ai.
  2. Explore learning progress and portfolio to assess technical skills.
- **RAG Integration**: Profile data and markdown documents feed into Ollama for personalization.

## RAG Integration
- **Usage**: Feeds into Meeting Room’s RAG pipeline for planning and personalization.
- **Structure**: Consistent headers, tables, and metadata for parseability.
- **Storage**: Store in `/docs/projects/`, sync to Linode, embed in PostgreSQL for RAG queries.

## Success Metrics
- **Feature Completion**: Deploy MVP (FR01-FR02, NFR01-NFR04) by August 2026.
- **Learning**: Master user authentication, database management, and personalization by September 2026.
- **Portfolio**: Achieve 10+ employer views via X/LinkedIn by September 2026.
- **Performance**: <2s LLM response time, 99% uptime.
- **Engagement**: Contribute to 100+ unique visitors to thinkheads.ai by September 2026.