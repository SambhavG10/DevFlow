# 🛠️ DevFlow – Multi-Agent AI Software Development System

DevFlow is an intelligent multi-agent software development platform that transforms high-level software requirements into working applications. It automates the complete software development lifecycle, including planning, architecture design, code generation, testing, debugging, and deployment through a collaborative network of AI agents.

Built using **LangGraph, Node.js, Docker, Redis, React**, and powered by **Google Gemini AI** with optional support for **local LLMs through Ollama**.

---

# ✨ Key Features

## 🧠 Multi-Agent Development Pipeline

* AI-driven software development workflow powered by LangGraph
* Specialized agents for project planning, architecture, coding, reviewing, debugging, and deployment
* Shared global state for seamless collaboration between agents
* Intelligent task orchestration using graph-based execution

---

## 💻 Automated Code Generation

* Converts high-level software requirements into production-ready code
* Generates frontend and backend project structures
* Supports iterative code refinement and improvements
* Maintains project context throughout execution

---

## 🐳 Docker Sandbox Execution

* Runs generated applications inside isolated Docker containers
* Automated environment setup for frontend, backend, and database services
* Health checks for generated applications
* Safe execution without affecting the host system

---

## 🔄 Intelligent Debugging

* Automatically detects runtime and build errors
* Self-debugging workflow using dedicated debugging agents
* Retries failed execution steps before requesting human intervention
* Improves generated code through iterative validation

---

## 💾 Persistent Workflow State

* Redis-based checkpointing for every execution stage
* Resume execution from the last successful checkpoint
* Prevents data loss during long-running workflows
* Supports interruption and continuation of complex tasks

---

## 📡 Real-Time Monitoring

* Live execution logs using WebSockets
* Real-time workflow visualization
* Dynamic pipeline status updates
* Generated file previews during execution

---

## 🤖 Flexible AI Model Support

* Google Gemini AI integration
* Local LLM support using Ollama
* Easy switching between cloud and local models
* Reduced dependency on external APIs

---

## 💰 Token & Cost Management

* Tracks token consumption during execution
* Estimates API usage costs
* Prevents excessive AI usage with configurable budget limits
* Improves resource utilization

---

# 🛠️ Technology Stack

### Core Framework

* Node.js
* LangGraph
* LangChain

### Frontend

* React
* Zustand
* Tailwind CSS
* WebSockets

### Backend

* Node.js
* Express.js

### AI Models

* Google Gemini AI
* Ollama

### Infrastructure

* Docker
* Docker Compose
* Redis

---

## 🗺️ System Design

```
                 START ➔ [pmAgent] ➔ [architectAgent] ➔ [blueprintValidator]
                              │                │
                        (vague spec)     (invalid design)
                              ▼                ▼
                         [humanInput]     [architectStep]
                              │
                              ▼
                       [plannerAgent] ➔ [setupSandbox] ➔ [sandboxHealthCheck]
                                                               │
                                                               ▼
  ┌─────────────────────────── [selectNextTask] ◄──────────────┘
  ▼                                   │
[contextBuilder]               (all tasks done)
  │                                   ▼
[coderAgent]                 [phaseVerification]
  │                                   │
[updateRegistry]                      ▼
  │                         [deploymentVerifier]
  │                                   │
[reviewerAgent]                       ▼
  │                                   ▼
[executorAgent] ➔ [snapshot] ➔ [presentToUser] ➔ END
  │ (fails)
  ▼
[debuggerAgent] ➔ [humanEscalation] (if stuck)
```

---

# 🚀 Getting Started

## Prerequisites

* Node.js (v18 or above)
* Docker Desktop
* Redis
* Ollama (Optional)
* Google Gemini API Key (Optional)

---

## Clone Repository

```bash
git clone https://github.com/sanjay-dtu/DevFlow.git

cd DevFlow

npm install

cd dashboard

npm install

cd ..
```

---

## Environment Variables

Create a `.env` file in the project root.

```env
# AI Provider
LLM_PROVIDER=ollama

# Google Gemini
GEMINI_API_KEY=
GEMINI_MODEL=gemini-2.5-flash

# Ollama
OLLAMA_HOST=http://localhost:11434
OLLAMA_MODEL=qwen2.5-coder

# Redis
REDIS_URL=redis://localhost:6379

# Server
SERVER_PORT=3000

# Frontend
FRONTEND_URL=http://localhost:5173

# Token Budget
TOKEN_BUDGET=2.0
```

---

## Run Locally

```bash
npm run dev
```

Frontend

```text
http://localhost:5173
```

Backend

```text
http://localhost:3000
```

---

# ☁️ Deployment

The project can be deployed using Docker-based infrastructure or cloud platforms that support Node.js services. The modular architecture allows the backend, dashboard, Redis instance, and Docker execution environment to be configured independently for production deployments.

---

# 🚧 Challenges Faced

Developing **DevFlow** involved solving several engineering challenges related to AI orchestration, workflow management, and automated software development.

### 🧠 Designing a Multi-Agent Workflow

One of the biggest challenges was coordinating multiple AI agents that perform different responsibilities such as planning, architecture design, coding, reviewing, debugging, and deployment. A graph-based workflow was implemented using LangGraph to ensure each agent executed in the correct sequence while sharing contextual information.

---

### 🔄 Maintaining Agent Context

Each AI agent depends on the outputs generated by previous agents. Preserving context across multiple execution stages without losing information required a centralized shared state and structured message passing between agents.

---

### 💾 Reliable State Persistence

Long-running workflows can be interrupted unexpectedly due to crashes or manual intervention. Redis checkpointing was integrated to persist workflow states after every major execution step, allowing the system to resume from the latest checkpoint instead of restarting the entire pipeline.

---

### 🐳 Secure Code Execution

Executing AI-generated code directly on the host system presents security and stability concerns. Docker-based isolated sandboxes were introduced to safely build, execute, and validate generated applications while protecting the development environment.

---

### 🤖 Supporting Multiple LLM Providers

Integrating both Google Gemini AI and local Ollama models required designing a flexible abstraction layer capable of switching between providers without affecting the overall workflow or agent logic.

---

### 📡 Real-Time Execution Monitoring

Displaying workflow progress, generated files, and execution logs in real time required efficient WebSocket communication between the backend and dashboard while keeping the interface responsive during long-running tasks.

---

### 💰 Managing AI Costs

Large software generation tasks can consume significant AI tokens. A token budgeting mechanism was implemented to estimate API usage, monitor consumption, and prevent unnecessary execution costs during lengthy workflows.

---

### 📈 Building a Scalable Architecture

As additional agents and workflow stages were introduced, maintaining a modular architecture became increasingly important. The system was designed with reusable agents, configurable workflows, and independent execution modules to simplify future enhancements.

---

# 🔮 Future Roadmap

* Autonomous Pull Request Generation
* GitHub Repository Integration
* Kubernetes-based Sandbox Deployment
* Multi-language Code Generation
* AI-generated System Architecture Diagrams
* Automated CI/CD Pipeline Creation
* Multi-Repository Project Support
* Collaborative Human-in-the-Loop Development
* Performance Benchmarking Dashboard
* Plugin Architecture for Custom AI Agents

---
