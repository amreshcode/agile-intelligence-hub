# 🤖 Agile Intelligence Hub

> **AI-powered assistant for Scrum Masters & Product Owners — combining Gen AI + RAG + MCP Server to automate user story creation, backlog grooming, and direct Azure DevOps / JIRA integration.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://python.org)
[![Azure OpenAI](https://img.shields.io/badge/Azure-OpenAI-0078D4?logo=microsoft-azure)](https://azure.microsoft.com/en-us/products/ai-services/openai-service)
[![Status](https://img.shields.io/badge/Status-In%20Development-orange)](https://github.com/amreshcode/agile-intelligence-hub)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-brightgreen.svg)](CONTRIBUTING.md)

---

## 🎯 What is Agile Intelligence Hub?

**Agile Intelligence Hub** is an open-source AI agent that helps any Scrum Master, Product Owner, or Project Manager work smarter — not harder.

Instead of spending hours writing user stories, acceptance criteria, and Definition of Done manually, you simply describe what you need in plain English — and the AI does the heavy lifting.

```
You type:   "Create a user story for user login with OAuth and Google SSO"

AI does:    ✅ Searches Agile best practices (RAG)
            ✅ Generates User Story + Acceptance Criteria + DoD (Gen AI)
            ✅ Pushes directly to your Azure DevOps or JIRA (MCP Server)

Result:     Story created in your board in under 10 seconds 🚀
```

---

## ✨ Key Features

| Feature | Description |
|---------|-------------|
| 🧠 **Gen AI Story Generator** | Natural language → properly formatted User Stories |
| 📚 **RAG Knowledge Base** | Answers grounded in Scrum Guide, Agile Manifesto, best practices |
| 🔗 **MCP Server Integration** | Direct push to Azure DevOps & JIRA — no copy-paste |
| ✅ **Acceptance Criteria Builder** | Auto-generates testable AC using Given/When/Then format |
| 📋 **Definition of Done Generator** | Consistent DoD tailored to your team's context |
| 📊 **Sprint Report Summarizer** | Convert raw sprint data into stakeholder-ready summaries |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     USER INPUT (Natural Language)            │
└──────────────────────────┬──────────────────────────────────┘
                           │
              ┌────────────▼────────────┐
              │      RAG ENGINE          │
              │  Azure AI Search         │
              │  Searches Agile docs,    │
              │  Scrum Guide, templates  │
              └────────────┬────────────┘
                           │ Relevant Context
              ┌────────────▼────────────┐
              │    GEN AI AGENT          │
              │  Azure OpenAI (GPT-4o)   │
              │  Generates User Story,   │
              │  AC, DoD, Sprint Reports │
              └────────────┬────────────┘
                           │ Structured Output
              ┌────────────▼────────────┐
              │    MCP SERVER            │
              │  Azure DevOps Connector  │
              │  JIRA Connector          │
              │  Auto-creates work items │
              └────────────┬────────────┘
                           │
              ┌────────────▼────────────┐
              │   STREAMLIT UI           │
              │  Simple web interface    │
              │  for non-technical users │
              └─────────────────────────┘
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **LLM** | Anthropic Claude Sonnet 4.6 |
| **RAG** | Azure AI Search + LangChain |
| **MCP Server** | Azure DevOps MCP + JIRA MCP |
| **Orchestration** | LangChain / AutoGen |
| **UI** | Streamlit |
| **Backend** | Python 3.11+ |
| **Hosting** | Azure App Service |
| **Version Control** | GitHub + GitHub Actions (CI/CD) |

---

## 📁 Project Structure

```
agile-intelligence-hub/
│
├── README.md                   ← You are here
├── ARCHITECTURE.md             ← Deep dive into design decisions
├── DECISIONS.md                ← Why each tool was chosen
├── CONTRIBUTING.md             ← How to contribute
├── LICENSE                     ← MIT License
│
├── docs/                       ← RAG Knowledge Base
│   ├── scrum-guide-2020.pdf
│   ├── agile-manifesto.pdf
│   ├── user-story-best-practices.pdf
│   └── definition-of-done-templates.pdf
│
├── src/
│   ├── rag/                    ← RAG Engine
│   │   ├── loader.py           ← Load & chunk documents
│   │   ├── embeddings.py       ← Create vector embeddings
│   │   └── retriever.py        ← Search relevant context
│   │
│   ├── agent/                  ← Gen AI Brain
│   │   ├── prompt_templates.py ← Story, AC, DoD prompts
│   │   └── generator.py        ← Calls Azure OpenAI
│   │
│   ├── mcp/                    ← MCP Server Integration
│   │   ├── ado_connector.py    ← Azure DevOps connector
│   │   └── jira_connector.py   ← JIRA connector
│   │
│   └── app.py                  ← Main Streamlit UI
│
├── tests/
│   ├── test_rag.py
│   ├── test_generator.py
│   └── test_mcp.py
│
├── .env.example                ← Template for API keys (never commit .env!)
├── requirements.txt            ← Python dependencies
└── setup.py                    ← Easy install script
```

---

## 🚀 Quick Start

### Prerequisites
- Python 3.11+
- Azure account (free tier works) → [Get one here](https://azure.microsoft.com/free)
- Azure OpenAI access
- Git

### 1. Clone the repo
```bash
git clone https://github.com/amreshcode/agile-intelligence-hub.git
cd agile-intelligence-hub
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Configure environment
```bash
cp .env.example .env
# Edit .env with your Azure OpenAI and ADO credentials
```

### 4. Run the app
```bash
streamlit run src/app.py
```

### 5. Open in browser
```
http://localhost:8501
```

---

## 💡 Example Outputs

### User Story Generated
```
Title: User Login with OAuth and Google SSO

As a registered user,
I want to log in using my Google account,
So that I can access the platform without remembering a separate password.

Acceptance Criteria:
  Given I am on the login page
  When I click "Sign in with Google"
  Then I should be redirected to Google OAuth
  And upon successful authentication, I should land on the dashboard

  Given my Google session has expired
  When I try to access a protected page
  Then I should be redirected to the login page

Definition of Done:
  ✅ Unit tests written and passing
  ✅ Integration test with Google OAuth completed
  ✅ Code reviewed and approved
  ✅ Security review passed
  ✅ Deployed to staging and verified
```

---

## 🗓️ Roadmap

- [x] Repo setup & architecture design
- [ ] RAG engine — document loading & search
- [ ] Gen AI layer — story & AC generation
- [ ] MCP Server — Azure DevOps integration
- [ ] MCP Server — JIRA integration
- [ ] Streamlit UI
- [ ] Azure deployment
- [ ] JIRA plugin
- [ ] Slack bot integration

---

## 🤝 Contributing

Contributions are welcome! This project is built to help the global Agile community.

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## 👤 Author

**Amresh Lenka**
Scrum Master | Product Owner | Agile Leader | AI Enthusiast

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?logo=linkedin)](https://linkedin.com/in/amreshlenka)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?logo=github)](https://github.com/amreshcode)

---

## 📄 License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.

---

> ⭐ If this project helps you, please give it a star — it helps others discover it!
