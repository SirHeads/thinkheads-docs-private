---
Project: ThinkHeads.ai
Type: Repository Overview
Date: 2025-07-17
---

# ThinkHeads.ai Documentation Repository

## Overview
The `thinkheads-docs-private` repository serves as the central documentation hub for thinkheads.ai, a solo project to master artificial intelligence, machine learning, and deep learning (AI/ML/DL), build a professional portfolio, and secure a career in the AI industry. This repository organizes high-level strategies and project-specific details for thinkheads.ai, a platform showcasing AI-driven sub-products (AI-driven website, Learning Assistant, Meeting Room, Online Card Game, User Profiles). The documents are designed for public sharing on thinkheads.ai to demonstrate technical expertise to potential employers and the tech community, while also supporting Retrieval-Augmented Generation (RAG) for strategic planning via the Meeting Room sub-product. The repository leverages a tech stack including Proxmox (AMD 7700, 96 GB DDR5, dual RTX 5060 Ti GPUs, NVMe storage), Linode (4 GB RAM, 2 CPU cores, 80 GB storage), Cloudflare, Nginx, PostgreSQL, Python/FastAPI, Linux, RustDesk, n8n, Ollama, and Hugo.

## Purpose
This repository:
- Centralizes planning and specification documents for thinkheads.ai.
- Supports AI/ML/DL learning through structured project development.
- Builds a public portfolio to showcase skills to employers via X and LinkedIn.
- Enables RAG integration for the Meeting Room sub-product, using markdown documents stored in PostgreSQL for context-aware planning.
- Reflects a 20-hour/week solo development effort, with automation (n8n) and remote management (RustDesk) to maximize efficiency.

## Repository Structure
The repository is organized into high-level strategy documents and project-specific details, stored in the following folders:

- **Root Directory**:
  - **README.md**: This file, providing an overview of the repository.
  - **document_structure.md**: Outlines the organization and purpose of all documents.

- **corporate_strategy/**:
  - **company_overview.md**: Defines the mission, vision, core values, goals, and target audience for thinkheads.ai.
  - **business_model.md**: Describes the non-commercial model focused on skill development and portfolio building.
  - **technology_stack.md**: Details the hardware (Proxmox, Linode) and software (Cloudflare, Nginx, etc.) used across projects.
  - **project_ideas.md**: Outlines the vision for all sub-products, aligning with learning and employment goals.
  - **feature_backlog.md**: Lists and prioritizes features for all sub-products.
  - **project_selection_criteria.md**: Defines criteria for prioritizing sub-products based on learning, portfolio, and feasibility.
  - **project_roadmap.md**: Provides a timeline and milestones for sub-product development (July 2025 - July 2026).

- **projects/**:
  - **thinkheads_v0_requirements.md**: Specifies functional and non-functional requirements for the AI-driven website.
  - **thinkheads_v0_specifications_overview.md**: Summarizes specifications for the AI-driven website, with identifiers for detailed specs.
  - **thinkheads_specification_files/**:
    - **frontend_specifications.md**: Specifications for the static site (Hugo, Nginx) hosting portfolio and blog content.
    - **backend_specifications.md**: Specifications for API endpoints and LLM-powered chat navigation (FastAPI, Ollama).
    - **database_specifications.md**: Specifications for PostgreSQL storage of session data and RAG embeddings.
    - **security_specifications.md**: Specifications for securing the website with Cloudflare and Nginx.
    - **automation_monitoring_specifications.md**: Specifications for automating deployment and monitoring with n8n and RustDesk.

## Usage
- **Portfolio Sharing**: Documents are synced to Linode and published on thinkheads.ai to showcase work to employers and the tech community.
- **RAG Integration**: Markdown files are stored in PostgreSQL embeddings for the Meeting Room sub-product’s RAG pipeline, enabling context-aware planning.
- **Development Planning**: Use the roadmap and specifications to guide implementation, starting with the AI-driven website MVP by October 2025.
- **Maintenance**: Update documents via Git on Proxmox, automate syncing and deployment with n8n, and monitor with RustDesk.

## Getting Started
1. **Clone Repository**: Clone `thinkheads-docs-private` to your Proxmox server (`/git/thinkheads-docs-private`).
2. **Sync to Linode**: Use rsync to sync documents to Linode for public access on thinkheads.ai.
3. **RAG Setup**: Parse markdown files with a Python script, generate embeddings via Ollama, and store in PostgreSQL for Meeting Room queries.
4. **Development**: Begin with the AI-driven website (frontend: Hugo/Nginx, backend: FastAPI/Ollama), following specifications in `projects/thinkheads_specification_files/`.

## Success Metrics
- **Documentation**: Complete and maintain all listed documents, with regular updates to reflect project progress.
- **Learning**: Master AI/ML/DL skills (e.g., LLM integration, RAG, full-stack development) through documented projects by February 2026.
- **Portfolio**: Achieve 10+ employer views on thinkheads.ai via X/LinkedIn by November 2025.
- **Engagement**: Attract 100+ unique visitors to thinkheads.ai by February 2026.

## Contact
For inquiries or collaboration interest, reach out via X or LinkedIn, linked from thinkheads.ai.