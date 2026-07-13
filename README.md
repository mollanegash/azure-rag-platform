
# Azure RAG Platform — AI-Powered Knowledge Assistant

**Live Demo:** Coming soon — see `/docs/screenshots` for preview  
**Stack:** TypeScript, Node.js, Fastify, React, Azure OpenAI, Azure AI Search, Bicep, Azure Container Apps  
**Status:** Production-style MVP deployed using Infrastructure-as-Code

## Overview

Azure RAG Platform is an AI-powered knowledge assistant that enables organizations to securely search, analyze, and interact with private business documents using Retrieval-Augmented Generation (RAG).

The platform combines Azure OpenAI, Azure AI Search, vector embeddings, secure authentication, and cloud-native microservices architecture to deliver accurate, citation-backed responses from enterprise data.

This project demonstrates modern AI application engineering, including:

- Full-stack cloud-native development
- RAG pipeline architecture
- Secure enterprise document processing
- Microservices design
- Infrastructure-as-Code deployment
- AI-enabled knowledge management workflows


## Why this project matters

Organizations have large amounts of internal knowledge stored across documents, policies, and technical resources. This platform demonstrates how AI can transform those documents into a secure, searchable knowledge system.

This repository serves as:

1. **Portfolio project** — End-to-end Azure AI engineering with frontend, backend, AI services, and infrastructure automation.
2. **Startup MVP foundation** — Designed as a scalable foundation for enterprise knowledge management and consulting workflows.


## Current Capabilities

### AI-Powered RAG Pipeline
- Azure OpenAI integration for grounded responses
- Azure AI Search for document retrieval
- Vector embedding-based semantic search
- Citation-backed answers from indexed content


### Secure Enterprise Architecture
- JWT authentication
- Azure AD integration
- Role-based access design
- Managed Identity support
- Key Vault integration
- Audit logging foundations


### Microservices Architecture

Services are separated by responsibility:

- `webapp` — React frontend application and authentication flow
- `search` — Fastify API handling chat requests and RAG orchestration
- `indexer` — Document processing and embedding pipeline
- `chat-component` — Reusable AI chat interface library


### Infrastructure Automation

Cloud resources are provisioned using:

- Azure Developer CLI (`azd`)
- Bicep Infrastructure-as-Code
- Azure Container Apps
- Azure Static Web Apps
- Docker containerization


# Technology Stack

| Layer | Technology |
|---|---|
| Frontend | React 18, Vite, TypeScript |
| Backend | Node.js 18, Fastify, TypeScript |
| AI Platform | Azure OpenAI GPT-4, Azure AI Search, Vector Embeddings |
| Authentication | Azure AD, JWT, Managed Identity |
| Infrastructure | Bicep, Azure Developer CLI, Docker |
| Deployment | Azure Container Apps, Azure Static Web Apps |
| Security | Key Vault, Role-Based Access, Secure API Design |


# Architecture Overview

Request flow:

```

User
↓
React Static Web App
↓
Container Apps API
↓
Fastify RAG Service
↓
Azure AI Search
↓
Azure OpenAI
↓
Grounded Response with Citations

```

The service separation enables independent scaling, clear ownership boundaries, and future SaaS evolution.


# Project Structure

```

azure-rag-platform/

├── packages/
│   ├── webapp              # React frontend + authentication flow
│   ├── search              # Fastify API + RAG orchestration
│   ├── indexer             # Document processing + embedding pipeline
│   └── chat-component      # Reusable AI chat component
│
├── infra/                  # Bicep templates and Azure resources
├── scripts/                # Automation scripts
├── tests/                  # Application tests
└── azure.yaml              # Azure Developer CLI deployment configuration

````


# Getting Started

## Prerequisites

- Node.js 18+
- npm 9+
- Azure subscription with Azure OpenAI access
- Azure Developer CLI (`azd`)


## Local Deployment

```bash
npm install

azd auth login

azd up
````

The deployment process provisions:

* Azure OpenAI
* Azure AI Search
* Azure Container Apps
* Supporting Azure infrastructure

After deployment:

```
http://localhost:5173
```

# Roadmap

## Phase 1 — Completed ✅

* RAG chat with citations
* Document upload and indexing
* Azure AD authentication
* Bicep infrastructure deployment

## Phase 2 — In Progress

* Multi-tenant data isolation
* Usage analytics dashboard
* Enhanced administration controls

## Phase 3 — Future

* Custom workflow builder
* Enterprise integrations
* Advanced analytics platform

# Engineering Highlights

This project demonstrates:

### Azure AI Engineering

* End-to-end RAG architecture
* Document ingestion pipelines
* Embeddings and semantic search
* LLM integration patterns

### Cloud-Native Engineering

* Infrastructure-as-Code
* Containerized deployment
* Microservices architecture
* Automated provisioning

### Security Engineering

* Identity-based authentication
* Managed Identity
* Secure secret management
* Enterprise access control patterns

### Product Engineering

* Built as a complete MVP
* Designed with scalability in mind
* Focused on real enterprise knowledge-management problems

# Deployment

Azure deployment:

```bash
azd up
```

Local development:

```bash
npm run dev
```

# Security

Security practices include:

* No secrets committed to source control
* Managed Identity authentication
* Key Vault-based secret management
* Secure API communication
* Audit logging foundations

For vulnerability reporting, see:

`SECURITY.md`

# Acknowledgment

This project was inspired by Microsoft's Azure RAG reference implementation:

`Azure-Samples/azure-search-openai-javascript`

The original concept was significantly extended with custom architecture, security improvements, microservice separation, and enterprise-focused features.

```

