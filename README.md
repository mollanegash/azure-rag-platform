# Betsi Eco Hub — AI-Powered Knowledge Platform

**Live Demo:** Coming soon — see `/docs/screenshots` for preview  
**Stack:** TypeScript, Node.js, Fastify, Azure OpenAI, Azure AI Search, Bicep, Azure Container Apps, React  
**Status:** Production-ready MVP deployed via Infrastructure-as-Code

> Forked from Azure-Samples/azure-search-openai-javascript and extensively customized with enterprise features, security hardening, and multi-tenant architecture.

## Why this project matters

Betsi Eco Hub helps organizations turn internal documents into secure, AI-searchable knowledge. It demonstrates how retrieval-augmented generation can deliver accurate, cited answers from company data.

This repository serves as:
1. **Portfolio project** — Full-stack Azure AI engineering with IaC and microservices
2. **Startup MVP** — Foundation for a client-facing platform for knowledge management and consulting workflows

## What this app does today

Production-ready AI chat experience over private business content. Users ask natural-language questions and get grounded answers with citations from indexed documents.

### Current Features
- **RAG Pipeline** — Azure OpenAI + Azure AI Search with citation-backed responses
- **JWT Authentication + Azure AD Integration** — Role-based access and SSO support
- **Secure Document Upload** — Content indexing pipeline with metadata support
- **Microservices Architecture** — Separated `search`, `indexer`, and `webapp` services
- **Infrastructure-as-Code** — One-command Azure provisioning via Bicep + `azd up`
- **Client Dashboard** — Saved conversations, document management, usage analytics
- **Admin Controls** — Content curation, user management, audit logging hooks

## Tech stack

| **Layer** | **Technology** |
| --- | --- |
| **Frontend** | React 18, Vite, TypeScript |
| **Backend** | Node.js 18, Fastify, TypeScript |
| **AI/RAG** | Azure OpenAI GPT-4, Azure AI Search, Vector Embeddings |
| **Infrastructure** | Bicep, Azure Developer CLI, Docker |
| **Deployment** | Azure Container Apps, Azure Static Web Apps |
| **Security** | Azure AD, Managed Identity, Key Vault |

## Project structure
betsi-eco-hub/
├── packages/webapp # React frontend + auth flow
├── packages/search # Fastify API: chat, RAG orchestration
├── packages/indexer # Document processing + embedding pipeline
├── packages/chat-component # Reusable chat UI library
├── infra/ # Bicep templates: OpenAI, Search, Container Apps
└── azure.yaml # azd hooks: build, provision, deploy

javascript

## Getting started

### Prerequisites
- Node.js 18+ and npm 9+
- Azure subscription with Azure OpenAI access
- Azure Developer CLI `azd` installed

### Run locally
```bash
npm install
azd auth login
azd up
Then open: http://localhost:5173

azd up provisions Azure OpenAI, AI Search, and Container Apps, then deploys all services. First run takes 5-8 minutes.

Architecture overview
Request flow: User → Static Web App → Container Apps API → Azure AI Search retrieves docs → Azure OpenAI generates grounded answer → Response with citations

The microservices separation enables independent scaling and clear service boundaries for future SaaS evolution.

Roadmap
Phase 1 — Shipped ✅
RAG chat with citations
Document upload + indexing
Azure AD authentication
Bicep IaC deployment
Phase 2 — In Progress
Multi-client data isolation
Usage analytics dashboard
Enhanced admin controls
Phase 3 — Scale
Custom workflow builder for business teams
Advanced analytics and reporting
Integration APIs for enterprise tools
Why this is a strong portfolio project
This repo demonstrates:

Azure AI Engineering — End-to-end RAG: indexing, embeddings, vector search, grounded generation
Cloud-Native IaC — Zero-click deploys with Bicep and Azure Developer CLI
Security Practices — Managed Identity, Key Vault, SECURITY.md, audit logging
Microservices Design — Production service separation and API design
Product Thinking — Built as MVP with clear roadmap and real user problems
Deployment
Azure: azd up — provisions + deploys everything
Local dev: npm run dev — uses Azure services via environment variables

For detailed Azure setup, see /infra/README.md.

Troubleshooting
Issue

Fix

401 Principal does not have access

Run azd auth login or remove AZURE_CLIENT_ID from .env

404 after azd up

Wait 10 min for Container Apps cold start, then azd deploy

Region not enabled for OpenAI

Pick East US or Sweden Central during azd up prompts

Quota exceeded

Delete old resource groups: az group delete --name <rg-name>

Security
See SECURITY.md for vulnerability reporting. Key practices:

No secrets in code — all via Managed Identity + Key Vault
Audit logging hooks in API calls
Azure AD integration for enterprise authentication
Contact
Built by Molla Negash — Backend Engineer specializing in Azure AI + Cloud Architecture
GitHub: 
Open to: Full-time roles, consulting, collaboration
