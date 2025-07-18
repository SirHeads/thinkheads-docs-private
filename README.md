---
Project: thinkheads.ai
Type: Repository Overview
Date: 2025-07-17
---

# thinkheads.ai Repository

## Company Overview
thinkheads.ai is a personal, non-commercial platform dedicated to exploring the transformative potential of Artificial Intelligence (AI), Machine Learning (ML), and Deep Learning (DL) through hands-on projects. Operated solo, it serves as a learning lab and portfolio showcase, demonstrating technical expertise in AI-driven applications to potential employers in the AI industry. Hosted on a Proxmox server and a Linode cloud instance, thinkheads.ai leverages cutting-edge tools to build innovative tools like Learning Assistant, Meeting Room, Online Card Game, and User Profiles, reflecting a passion for AI’s ability to revolutionize productivity and education.

## Business Model
- **Purpose**: Non-commercial, focused on skill development and portfolio building.
- **Approach**: Develop AI-driven sub-products to master AI/ML/DL techniques, share publicly via thinkheads.ai, and engage the tech community on X/LinkedIn.
- **Value Proposition**: Provide a showcase of practical AI applications, enhancing employability in the AI industry.
- **Key Document**: `/docs/strategic/1.2 Business_Model.md`

## Feature Backlog
- **Purpose**: Centralized list of planned features for thinkheads.ai sub-products.
- **Content**: Defines prioritized features (e.g., F01-F15) with descriptions, such as personalized learning resources (F01-F03), meeting agenda generation (F07-F09), multiplayer gameplay (F10-F12), and user profile management (F13-F15).
- **Key Document**: `/docs/strategic/2.2 Feature_Backlog.md`

## Project Ideas
- **Purpose**: Outlines potential sub-products to align with learning and portfolio goals.
- **Content**: Includes ideas for AI-driven tools like Learning Assistant (educational resource platform), Meeting Room (virtual meeting management), Online Card Game (gamified AI/ML learning), and User Profiles (personalized user management).
- **Key Document**: `/docs/strategic/2.1 Project_Ideas.md`

## Project Planning Criteria
- **Purpose**: Defines criteria for selecting and prioritizing sub-products.
- **Content**: Evaluates projects based on learning value, portfolio impact, technical complexity, and resource availability (e.g., scores: Learning Assistant 4.5, Meeting Room 4.2, Online Card Game 4.0, User Profiles 3.8).
- **Key Document**: `/docs/strategic/3.1 Project_Selection_Criteria.md`

## Project Roadmap
- **Purpose**: Provides a timeline for sub-product development.
- **Content**: Schedules MVP delivery: Learning Assistant (Dec 2025), Meeting Room (Mar 2026), Online Card Game (Jun 2026), User Profiles (Aug 2026), within a 20-hour/week schedule.
- **Key Document**: `/docs/strategic/3.2 Project_Roadmap.md`

## Technology Stack
- **Infrastructure**:
  - **Proxmox Server**: AMD 7700, 96 GB DDR5, dual RTX 5060 Ti GPUs, NVMe storage, hosting LXC containers (`dockProd1`, `dockProd2`, `dockTest1`) for compute-intensive tasks.
  - **Linode Server**: 4 GB RAM, 2 CPU cores, 80 GB storage, Debian OS, hosting lightweight APIs and website.
- **Software**:
  - **AI/ML**: Ollama (LLM with RAG), Python (AI/ML scripts, FastAPI).
  - **Database**: PostgreSQL for data storage and RAG embeddings.
  - **Web**: Hugo (static site generator), Nginx (web server), Cloudflare (SSL, caching).
  - **Automation**: n8n for workflows, RustDesk for remote management.
- **Key Document**: `/docs/strategic/1.3 Technology_Stack.md`

## Overview
Welcome to the `thinkheads-docs-private` repository, the backbone of thinkheads.ai. This repository captures the planning, requirements, and technical specifications for four sub-products: Learning Assistant, Meeting Room, Online Card Game, and User Profiles. Built solo, it leverages a modern tech stack to create AI-driven tools, serving as a learning lab and portfolio to showcase expertise to potential employers. The repository reflects my excitement for AI’s potential to transform learning and productivity, aiming to connect with the tech community via thinkheads.ai and X/LinkedIn.

## Objectives
- **Learn AI/ML/DL**: Develop proficiency in RAG, LLM fine-tuning, NLP, real-time APIs, and database management.
- **Build a Portfolio**: Create a professional showcase of AI-driven applications for employability.
- **Engage the Community**: Drive 100+ unique visitors to thinkheads.ai by September 2026.
- **Leverage AI**: Use AI tools (e.g., Ollama, RAG) to accelerate development and personalize experiences.

## Repository Structure
The repository is organized under `/docs/` to document project planning, requirements, and specifications, stored in markdown for readability and RAG ingestion.

- **/docs/strategic/**: Strategic documents for business model, feature backlog, project ideas, selection criteria, and roadmap.
- **/docs/projects/**: Sub-product documentation with subfolders:
  - **learning_assistant/**: AI-powered learning tool.
  - **meeting_room/**: AI-driven virtual meeting tool.
  - **online_card_game/**: AI-driven multiplayer card game.
  - **user_profiles/**: AI-driven user management system.
- **/docs/projects/<sub-product>_specifications/**: Detailed specifications for each sub-product’s components.
- **/n8n/workflows/**: Automation workflows for deployment and monitoring.
- **/scripts/**: Setup scripts (e.g., `proxmox_setup_zfs_datasets.sh`).

## File Types and Purpose
Each sub-product includes a consistent set of file types:

- **Business Case** (`*_business_case.md`):
  - **Purpose**: Justifies project development with cost-benefit analysis and risks.
  - **Content**: Outlines project idea, costs (time, resources), benefits (learning, portfolio), and success metrics.
  - **Location**: `/docs/projects/<sub-product>/` (e.g., `learning_assistant_v0_business_case.md`).
- **Requirements** (`*_requirements.md`):
  - **Purpose**: Defines functional and non-functional requirements.
  - **Content**: Lists user flows, technical constraints, and acceptance criteria for features.
  - **Location**: `/docs/projects/<sub-product>/` (e.g., `meeting_room_v0_requirements.md`).
- **Specifications Overview** (`*_specifications_overview.md`):
  - **Purpose**: Summarizes system architecture and assigns identifiers for detailed specs.
  - **Content**: Outlines backend, database, frontend, and automation components.
  - **Location**: `/docs/projects/<sub-product>/` (e.g., `online_card_game_v0_specifications_overview.md`).
- **Detailed Specifications** (`*_Specifications.md`):
  - **Purpose**: Provides technical blueprints for implementation.
  - **Content**: Includes code snippets, hosting details, and configurations (e.g., FastAPI, PostgreSQL, n8n).
  - **Location**: `/docs/projects/<sub-product>_specifications/` (e.g., `user_profiles_specifications/Backend_Specifications.md`).

## Sub-Products
- **Learning Assistant V0**:
  - AI-powered tool for personalized learning resources, note-taking, and AI/ML exercises.
  - Files: `/docs/projects/learning_assistant/` and `/docs/projects/learning_assistant_specifications/`.
  - Timeline: MVP by December 2025.
- **Meeting Room V0**:
  - AI-driven virtual meeting tool for agenda planning, action item tracking, and insights.
  - Files: `/docs/projects/meeting_room/` and `/docs/projects/meeting_room_specifications/`.
  - Timeline: MVP by March 2026.
- **Online Card Game V0**:
  - AI-driven multiplayer card game with educational AI/ML challenges.
  - Files: `/docs/projects/online_card_game/` and `/docs/projects/online_card_game_specifications/`.
  - Timeline: MVP by June 2026.
- **User Profiles V0**:
  - AI-driven user management system for personalized profiles and portfolio integration.
  - Files: `/docs/projects/user_profiles/` and `/docs/projects/user_profiles_specifications/`.
  - Timeline: MVP by August 2026.

## Technical Setup
- **Proxmox Server**: Hosts compute-intensive tasks (Ollama in `dockProd1`, PostgreSQL in `dockProd2`, testing in `dockTest1`) with LXC containers and ZFS datasets.
- **Linode Server**: Hosts APIs (FastAPI), game servers, and Hugo-generated website, served via Nginx.
- **Tech Stack**: Cloudflare (SSL, caching), Nginx, PostgreSQL, Python/FastAPI, n8n, Ollama, Hugo, RustDesk.
- **Syncing**: Documents synced to Linode via rsync (e.g., `rsync -avz /git/thinkheads-docs-private/docs/ user@linode:/var/www/thinkheads.ai/docs/`), with NFS/Samba for file sharing.
- **RAG Integration**: Markdown documents embedded in PostgreSQL for context-aware LLM queries.

## Getting Started
1. **Clone Repository**: `git clone /git/thinkheads-docs-private` on Proxmox.
2. **Explore Strategic Docs**: Review `/docs/strategic/` for business model and roadmap.
3. **Explore Projects**: Navigate to `/docs/projects/<sub-product>/` for planning documents.
4. **Review Specifications**: Check `/docs/projects/<sub-product>_specifications/` for implementation plans.
5. **Deploy Website**: Sync to Linode and run `hugo --minify` in `/var/www/thinkheads.ai`.
6. **Contribute**: Update markdown files, push to Git, and automate with n8n.

## Success Metrics
- **Learning**: Master 3+ AI/ML/DL skills per sub-product.
- **Portfolio**: Achieve 10+ employer views per sub-product via X/LinkedIn by September 2026.
- **Engagement**: Reach 100+ unique visitors to thinkheads.ai by September 2026.
- **Performance**: Ensure <2s response times for LLM/APIs, 99% uptime.

## Why This Matters
This repository reflects my passion for AI’s potential to transform learning and productivity. Each sub-product is a step toward mastering AI technologies and building a portfolio that stands out in the AI industry. By sharing this work on thinkheads.ai and X/LinkedIn, I aim to connect with the tech community and demonstrate my readiness for AI/ML roles.