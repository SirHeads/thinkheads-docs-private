---
Project: AI-Driven Website
Type: Specifications
Date: 2025-07-17
Spec-ID: SPEC-DB
---

# ThinkHeads.ai Database Specifications

## Overview
This document details the technical specifications for the database of the thinkheads.ai website, corresponding to **SPEC-DB** from **4.1.2 Specifications_Overview.md**. The database stores chat session data and RAG embeddings, supporting requirement FR04 (session management). It is designed for solo development within a 20-hour/week schedule, hosted in LXC container `dockProd2` on Proxmox (16 GB RAM, NVMe storage) and mirrored on Linode, using PostgreSQL.

## Technical Specifications
- **Technology**: PostgreSQL.
- **Hosting**: `dockProd2` on Proxmox, mirrored on Linode for production.
- **Features**:
  - Stores chat session data with 24-hour expiry (FR04).
  - Stores RAG embeddings for markdown documents, used by Ollama for context-aware chat responses (FR01).
- **Schema**:
  - Sessions table: `session_id` (VARCHAR), `user_id` (VARCHAR), `chat_history` (JSONB), `created_at` (TIMESTAMP), `expires_at` (TIMESTAMP).
  - RAG embeddings table: `document_id` (SERIAL), `document_path` (VARCHAR), `embedding` (VECTOR), `created_at` (TIMESTAMP).
- **Security**: Encrypted connections via SSL, restricted access to FastAPI and Ollama.

## Implementation Details
- **Development**: Design schema in VS Code, apply via `psql` on Proxmox.
- **Testing**: Validate data storage and RAG queries in `dockTest1` (Proxmox).
- **Deployment**: Deploy PostgreSQL in `dockProd2`, mirror to Linode via replication.
- **RAG Integration**: Store in `/docs/project_details/ai_driven_website/specifications/`, sync to Linode, embed in PostgreSQL for RAG queries.