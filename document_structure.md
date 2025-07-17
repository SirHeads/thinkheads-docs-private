# ThinkHeads.ai Document Structure

## 1. Corporate Strategy
- **1.1 Company_Overview.md**
  - Purpose: Defines the mission, vision, and objectives of thinkheads.ai as a company.
  - Content:
    - Mission statement (e.g., "Empowering AI-driven learning and creativity through innovative web solutions").
    - Vision for thinkheads.ai (e.g., becoming a showcase for AI/ML skills to secure employment).
    - Core values (e.g., innovation, self-reliance, open-source ethos).
    - High-level goals (e.g., build portfolio, learn AI/ML/DL, secure AI job).
    - Target audience (e.g., potential employers, personal network, tech community).

- **1.2 Business_Model.md**
  - Purpose: Outlines how thinkheads.ai operates as a "company" for learning and portfolio-building.
  - Content:
    - Revenue model (e.g., currently non-commercial, focused on employability).
    - Key activities (e.g., AI project development, public portfolio hosting).
    - Resource allocation (Proxmox local server, Linode cloud server).
    - Partnerships (e.g., leveraging open-source tools, potential employer outreach).
    - Success metrics (e.g., completed projects, job applications, portfolio engagement).

- **1.3 Technology_Stack.md**
  - Purpose: Documents the tech stack for transparency and RAG ingestion.
  - Content:
    - List of tools: Cloudflare, Nginx, PostgreSQL, Python, APIs, Linux, Proxmox, RustDesk, n8n, Ollama.
    - Role of each tool (e.g., Cloudflare for DNS/security, Ollama for LLMs).
    - Hardware: Proxmox server (AMD 7700, 96 GB DDR5, dual RTX 5060 Ti GPUs, NVMe storage), Linode server (4 GB RAM, 2 CPU cores, 80 GB storage).
    - Integration plan (e.g., Nginx for web serving, n8n for automation).

## 2. Product Ideas
- **2.1 Product_Vision.md**
  - Purpose: High-level overview of all sub-products and their alignment with company goals.
  - Content:
    - List of sub-products: AI-driven website, Learning Assistant, Meeting Room, Online Card Game, User Profiles.
    - Value proposition for each (e.g., Learning Assistant enhances AI/ML education).
    - Alignment with employment goals (e.g., showcases AI/ML, full-stack skills).
    - User personas (e.g., you, friends, employers, tech enthusiasts).

- **2.2 Feature_Backlog.md**
  - Purpose: Centralized list of features across all sub-products for prioritization.
  - Content:
    - Table of features: ID, Sub-Product, Feature Description, Priority, Status.
    - Example entries:
      - AI-driven website: Initial chat interface (High, In Progress).
      - Learning Assistant: Note-taking system (High, Planned).
      - Meeting Room: RAG-powered LLM for strategy (Medium, Planned).
      - Online Card Game: Multiplayer functionality (Low, Planned).
      - User Profiles: AI-generated avatars (Medium, Planned).
    - Prioritization criteria (e.g., learning value, employability impact).

## 3. Project Planning
- **3.1 Project_Selection_Criteria.md**
  - Purpose: Defines how projects are chosen to balance learning, portfolio impact, and feasibility.
  - Content:
    - Selection criteria: Skill development (AI/ML/DL), portfolio visibility, technical feasibility, time commitment (20 hours/week).
    - Scoring system (e.g., 1-5 scale for impact, complexity, relevance).
    - Current project priorities (e.g., Learning Assistant first for AI/ML focus).
    - Constraints: Solo development, local/cloud resources, no additional human help.

- **3.2 Project_Roadmap.md**
  - Purpose: Timeline and milestones for all projects.
  - Content:
    - Phases (e.g., Phase 1: Infrastructure setup, Phase 2: Core features, Phase 3: Public deployment).
    - Timeline (e.g., 4-6 months for job-ready portfolio).
    - Milestones per sub-product (e.g., Learning Assistant MVP in 2 months).
    - Dependencies (e.g., infrastructure setup before feature development).

## 4. Project Details
### 4.1 AI-Driven Website
- **4.1.1 Website_Requirements.md**
  - Purpose: Functional and non-functional requirements for the main thinkheads.ai site.
  - Content:
    - Functional: Chat-based navigation, integration with sub-products, responsive design.
    - Non-functional: High availability (Cloudflare, Nginx), secure (Cloudflare Tunnel), scalable.
    - Tech stack: Hugo (static site), FastAPI (backend), Nginx, Cloudflare.
    - User flow: Initial chat to guide users to sub-products.

- **4.1.2 Website_Specifications.md**
  - Purpose: Detailed technical specs for implementation and RAG.
  - Content:
    - Architecture: Static site on Linode, API endpoints via FastAPI on Proxmox.
    - Chat system: Ollama LLM with RAG, hosted in LXC container (dockProd1, 1 RTX 5060 Ti).
    - Database: PostgreSQL for user sessions, hosted in LXC (dockProd2).
    - Automation: n8n workflows for updates, monitoring via RustDesk.

### 4.2 Learning Assistant
- **4.2.1 Learning_Assistant_Requirements.md**
  - Purpose: Requirements for the AI-powered learning tool.
  - Content:
    - Functional: Note-taking, reinforcement learning exercises, progress tracking.
    - Non-functional: Low latency, offline capability (local Proxmox), exportable notes.
    - Integration: Ollama for LLM, PostgreSQL for data storage.
    - User flow: Input topics, receive curated resources, save notes.

- **4.2.2 Learning_Assistant_Specifications.md**
  - Purpose: Technical details for building the assistant.
  - Content:
    - LLM: Fine-tuned Ollama model for education (RAG with markdown notes).
    - Hosting: LXC container (dockProd1) with GPU passthrough.
    - APIs: FastAPI for note-taking, retrieval from PostgreSQL.
    - Workflow: n8n for scheduling learning sessions, syncing notes.

### 4.3 Meeting Room
- **4.3.1 Meeting_Room_Requirements.md**
  - Purpose: Requirements for the strategy and planning LLM tool.
  - Content:
    - Functional: RAG-powered LLM for product strategy, release planning, feature refinement.
    - Non-functional: Secure access (RustDesk), real-time interaction, exportable plans.
    - Integration: Open Web UI, PostgreSQL for RAG data.
    - User flow: Input project details, receive strategic recommendations.

- **4.3.2 Meeting_Room_Specifications.md**
  - Purpose: Technical specs for the meeting room tool.
  - Content:
    - LLM: Ollama with RAG (markdown project docs as context).
    - Hosting: LXC container (dockProd2, 2 RTX 5060 Ti GPUs, dynamic GPU release).
    - APIs: FastAPI for strategy outputs, PostgreSQL for storing plans.
    - Automation: n8n for scheduling planning sessions, RustDesk for remote access.

### 4.4 Online Card Game
- **4.4.1 Card_Game_Requirements.md**
  - Purpose: Requirements for the multiplayer card game.
  - Content:
    - Functional: Multiplayer support, real-time gameplay, customizable decks.
    - Non-functional: Scalable (Linode), low latency, secure user authentication.
    - Integration: PostgreSQL for game state, Nginx for serving.
    - User flow: Join game, play with friends, save progress.

- **4.4.2 Card_Game_Specifications.md**
  - Purpose: Technical details for the card game.
  - Content:
    - Backend: FastAPI for game logic, hosted on Linode.
    - Frontend: Hugo-based UI, served via Nginx.
    - Database: PostgreSQL for user accounts, game states.
    - Networking: WebSocket for real-time gameplay, Cloudflare for security.

### 4.5 User Profiles
- **4.5.1 User_Profiles_Requirements.md**
  - Purpose: Requirements for the profile and avatar generation feature.
  - Content:
    - Functional: Webcam photo upload, AI-generated avatars, user profile pages.
    - Non-functional: Secure storage (Cloudflare Tunnel), fast image processing.
    - Integration: Imagen (or equivalent AI image model), PostgreSQL for profiles.
    - User flow: Upload photo, generate avatars overnight, view profile.

- **4.5.2 User_Profiles_Specifications.md**
  - Purpose: Technical specs for profile and avatar system.
  - Content:
    - Image processing: Imagen model on Proxmox (dockProd2, GPU-intensive).
    - Hosting: FastAPI for API, LXC container for processing.
    - Database: PostgreSQL for user data, avatar metadata.
    - Automation: n8n for scheduling overnight processing, RustDesk for monitoring.

## 5. Infrastructure and Operations
- **5.1 Infrastructure_Setup.md**
  - Purpose: Details the setup of Proxmox and Linode environments.
  - Content:
    - Proxmox: LXC containers (dockProd1, dockProd2, dockTest1), GPU passthrough, VM for ML desktop.
    - Linode: Debian server, Docker for production/test, Nginx, Cloudflare Tunnel.
    - Networking: Shared network via Proxmox, SSH access, RustDesk for remote management.
    - Storage: NVMe on Proxmox, 80 GB on Linode, backup strategy (rsync).

- **5.2 Automation_Workflows.md**
  - Purpose: Documents n8n workflows for automation.
  - Content:
    - Workflows: Backup (rsync), monitoring (resource usage), deployment (Docker updates).
    - Triggers: Scheduled (e.g., nightly backups), event-based (e.g., new user profile).
    - Integration: n8n with PostgreSQL, FastAPI, Ollama.

- **5.3 Security_Plan.md**
  - Purpose: Outlines security measures for local and cloud setups.
  - Content:
    - Cloudflare: DNS, DDoS protection, Tunnel for secure access.
    - Nginx: Reverse proxy, SSL/TLS configuration.
    - Proxmox: SSH hardening, LXC isolation, RustDesk secure access.
    - Data: Encryption for PostgreSQL, secure API keys for FastAPI.

## 6. Learning and Development Plan
- **6.1 AI_ML_Learning_Plan.md**
  - Purpose: Personal learning roadmap for AI/ML/DL to support projects and job readiness.
  - Content:
    - Topics: AI/ML basics, deep learning (e.g., neural networks), RAG, fine-tuning LLMs.
    - Resources: Online courses, books, hands-on projects (e.g., Iris Flower Classification).
    - Schedule: 20 hours/week, milestones (e.g., first ML model in 1 month).
    - Integration: Learning Assistant to track progress, reinforce concepts.

- **6.2 Portfolio_Strategy.md**
  - Purpose: Plan to showcase work on thinkheads.ai for employers.
  - Content:
    - Content: Project demos, code repositories, blog posts on AI/ML learnings.
    - Hosting: Hugo site on Linode, AI demos on Proxmox (e.g., Open Web UI).
    - Promotion: Share on X, LinkedIn, job applications.
    - Metrics: Employer engagement, job interview invitations.

## 7. RAG Data Preparation
- **7.1 RAG_Data_Guidelines.md**
  - Purpose: Guidelines for structuring markdown for RAG compatibility.
  - Content:
    - Formatting: Consistent headers (H1-H3), bullet points, tables for structured data.
    - Metadata: Include document type (e.g., requirements, specs), project, date.
    - Content rules: Clear, concise, avoid ambiguity, use examples for clarity.
    - Storage: PostgreSQL for RAG embeddings, file system for markdown originals.

- **7.2 RAG_Integration_Plan.md**
  - Purpose: Plan for feeding documents into LLMs via RAG.
  - Content:
    - Pipeline: Markdown parsing, embedding generation (Ollama), storage in PostgreSQL.
    - Query system: FastAPI endpoint for RAG queries, integrated with Open Web UI.
    - Testing: Validate RAG outputs for accuracy (e.g., strategy suggestions).
    - Maintenance: Update embeddings with new documents, n8n for automation.