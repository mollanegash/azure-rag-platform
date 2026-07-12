# Betsi Eco Hub

AI-powered digital platform for secure data processing, intelligent document search, and modern IT consulting workflows.

Built as a startup-style MVP using Azure OpenAI, Azure AI Search, React, and Node.js, this project demonstrates how AI can help businesses turn documents, knowledge, and operational data into useful insights.

## Why this project matters

Betsi Eco Hub is designed around a simple but valuable idea: help businesses work smarter by combining secure data processing, AI-assisted search, and modern digital services in one experience.

This repository is being shaped as both:

- a portfolio project that showcases full-stack and AI development skills
- a prototype for a real client-facing platform that could grow into a startup product

## What this app does

The current application provides an AI-driven chat experience over business content, allowing users to ask questions and receive grounded answers from indexed documents.

### Core capabilities

- AI-powered chat over uploaded or indexed business content
- Retrieval-augmented search using Azure AI Search
- Modern web interface for interactive conversations
- Backend services for indexing and retrieval
- Architecture that can evolve into a secure client portal or knowledge assistant

## Product direction for Betsi Eco Hub

The long-term vision is to turn this into a practical platform for businesses that need:

- secure document processing
- AI-assisted knowledge access
- cybersecurity assessments
- consulting and operations support tools
- data-driven decision support

### MVP ideas

The next version of this product could include:

- user authentication and client dashboards
- secure document upload and indexing
- project/request tracking
- AI chat for company documents and policies
- admin tools for managing content and users
- feedback and analytics features

## Tech stack

- Frontend: React, Vite, TypeScript
- Backend services: Node.js, Fastify
- AI and search: Azure OpenAI, Azure AI Search
- Deployment: Azure Container Apps, Azure Static Web Apps
- Infrastructure: Bicep and Azure Developer CLI

## Project structure

- packages/webapp — frontend user experience
- packages/search — search and retrieval backend
- packages/indexer — document indexing service
- packages/chat-component — reusable chat UI component
- infra — Azure infrastructure as code

## Getting started

### Prerequisites

- Node.js 18+
- npm 9+
- Azure account with access to Azure OpenAI and Azure AI Search
- Docker (optional, for local container workflows)

### Install dependencies

```bash
npm install
```

### Run locally

```bash
npm start
```

Then open the local web app at:

```text
http://localhost:5173
```

> The app may require Azure environment configuration for the full experience to work end to end.

## Architecture overview

The platform is organized around three main services:

1. Web app — user-facing interface
2. Search service — handles retrieval and chat orchestration
3. Indexer service — processes and prepares content for search

This separation makes it easier to grow the project into a real product with additional features and business logic.

## Roadmap

### Phase 1 — Prototype

- working AI chat experience
- document-backed search
- polished startup-style UI

### Phase 2 — MVP

- authentication
- secure file upload
- client dashboard
- saved conversations and history

### Phase 3 — Business-ready platform

- multi-client support
- admin controls
- analytics and reporting
- custom workflows for consulting and operations

## Why this is a strong portfolio project

This repository shows:

- full-stack application design
- AI integration with Azure services
- backend/frontend separation
- cloud deployment readiness
- startup-style product thinking

## Contact

For questions, collaboration, or startup discussions, connect with the project owner through GitHub.

The `azd up` command comes from the [Azure Developer CLI](https://learn.microsoft.com/azure/developer/azure-developer-cli/overview), and takes care of both provisioning the Azure resources and deploying code to the selected Azure hosts.

The `azd up` command uses the `azure.yaml` file combined with the infrastructure-as-code `.bicep` files in the `infra/` folder. The `azure.yaml` file for this project declares several "hooks" for the prepackage step and postprovision steps. The `up` command first runs the `prepackage` hook which installs Node dependencies and builds the React.JS-based JavaScript files. It then packages all the code (both frontend and backend services) into a zip file which it will deploy later.

Next, it provisions the resources based on `main.bicep` and `main.parameters.json`. At that point, since there is no default value for the OpenAI resource location, it asks you to pick a location from a short list of available regions. Then it will send requests to Azure to provision all the required resources. With everything provisioned, it runs the `postprovision` hook to process the local data and add it to an Azure AI Search index.

Finally, it looks at `azure.yaml` to determine the Azure host (Container Apps and Static Web Apps, in this case) and uploads the zip to Azure App Service. The `azd up` command is now complete, but it may take a few minutes for the app to be fully available and working after the initial deploy.

Related commands are `azd provision` for just provisioning (if infra files change) and `azd deploy` for just deploying updated app code.

</details>

### Troubleshooting

Here are the most common failure scenarios and solutions:

1. The subscription (`AZURE_SUBSCRIPTION_ID`) doesn't have access to the Azure OpenAI service. Please ensure `AZURE_SUBSCRIPTION_ID` matches the ID specified in the [OpenAI access request process](https://aka.ms/oai/access).

1. You're attempting to create resources in regions not enabled for Azure OpenAI (e.g. East US 2 instead of East US), or where the model you're trying to use isn't enabled. See [this matrix of model availability](https://aka.ms/oai/models).

1. You've exceeded a quota, most often number of resources per region. See [this article on quotas and limits](https://aka.ms/oai/quotas).

1. You're getting "same resource name not allowed" conflicts. That's likely because you've run the sample multiple times and deleted the resources you've been creating each time, but are forgetting to purge them. Azure keeps resources for 48 hours unless you purge from soft delete. See [this article on purging resources](https://learn.microsoft.com/azure/ai-services/recover-purge-resources?tabs=azure-portal#purge-a-deleted-resource).

1. After running `azd up` and visiting the website, you see a '404 Not Found' in the browser. Wait 10 minutes and try again, as it might be still starting up. Then try running `azd deploy` and wait again. If you still encounter errors with the deployed app, consult these [tips for debugging App Service app deployments](http://blog.pamelafox.org/2023/06/tips-for-debugging-flask-deployments-to.html) and file an issue if the error logs don't help you resolve the issue.

1. You're getting an error `401 Principal does not have access to API/Operation` while running the project locally or trying to deploy. That's likely because your environment variables include `AZURE_TENANT_ID`, `AZURE_CLIENT_ID` and `AZURE_CLIENT_SECRET`. You should either grant permissions to the related _Service Principal_ or remove these variables from your environment to ensure normal access. For more details, please refer to [Azure identity SDK](https://github.com/Azure/azure-sdk-for-js/blob/main/sdk/identity/identity/README.md#defaultazurecredential).

### Note

> Note: The documents used in this demo contain information generated using a language model (Azure OpenAI Service). The information contained in these documents is only for demonstration purposes and does not reflect the opinions or beliefs of Microsoft. Microsoft makes no representations or warranties of any kind, express or implied, about the completeness, accuracy, reliability, suitability or availability with respect to the information contained in this document. All rights reserved to Microsoft.
