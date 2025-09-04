# Recruitly – System Architecture

## Overview
Recruitly is an AI-driven recruitment assistant that integrates **Machine Learning**, **Generative AI**, and **Agentic AI** to automate hiring workflows.

---

## High-Level Architecture

```
[Frontend (React/Angular)] 
        |
        v
[Backend API (FastAPI)]
   ├── Resume Parsing (ML)
   ├── Candidate Scoring (ML)
   ├── GenAI Services
   │      ├── Resume Summarizer
   │      ├── JD Rewriter
   │      └── Interview Q Generator
   ├── Agentic AI Orchestrator
   │      ├── Screening Agent
   │      ├── Recruiter Assistant Agent
   │      ├── Candidate Engagement Agent
   │      └── Diversity Agent
   └── Database (PostgreSQL / MongoDB)
        └── Candidate Profiles, Job Data, Results
```

---

## Components

1. **Frontend (Recruiter Dashboard)**
   - Upload resumes, view ranked candidates
   - AI-generated summaries, interview questions
   - Recruiter chatbot

2. **Backend (FastAPI)**
   - API layer exposing ML, GenAI, and Agent agents
   - Authentication & authorization

3. **ML Models**
   - Resume parsing with NLP (spaCy, BERT)
   - Candidate-job matching using embeddings

4. **Generative AI**
   - Summarizes resumes
   - Rewrites job descriptions
   - Generates interview questions

5. **Agentic AI**
   - Multi-agent system coordinating tasks
   - Screening, recruiter Q&A, candidate engagement, diversity bias detection

6. **Database**
   - Stores resumes, parsed profiles, rankings, recruiter interactions

---

## Deployment
- **Containerized with Docker**
- **Orchestration with Docker Compose or Kubernetes**
- **CI/CD** for automated builds and deployments

## Architecture Diagram

                ┌─────────────────────────┐
                │  Recruiter Frontend UI  │  ← React / Angular
                └───────────┬─────────────┘
                            │
                ┌───────────▼─────────────┐
                │   Backend API Layer     │  ← FastAPI / Flask (.NET optional)
                └───────────┬─────────────┘
                            │
        ┌───────────────────┼────────────────────┐
        │                   │                    │
┌───────▼───────┐   ┌───────▼─────────┐  ┌───────▼─────────┐
│  ML Services  │   │  GenAI Services │  │ Agent Orches-   │
│ (scikit/TF)   │   │ (GPT / LLaMA)   │  │ tration Layer   │
│ - Resume NLP  │   │ - Summaries     │  │ (LangChain/     │
│ - Candidate   │   │ - JD Rewriting  │  │  CrewAI/AutoGen)│
│   Scoring     │   │ - Q&A, Questions│  │ Agents:         │
│ - Fraud detect│   └───────▲─────────┘  │ - Screening     │
└───────▲───────┘           │            │ - Recruiter Asst│
        │                   │            │ - Candidate Eng │
        │                   │            │ - Diversity     │
        │                   │            └─────────────────┘
        │                   │
┌───────▼───────────────────▼──────────────────────────────┐
│                   Database Layer                         │
│ - PostgreSQL (structured candidate & JD data)            │
│ - Elasticsearch / Weaviate (semantic resume search)      │
│ - (Optional) Neo4j (candidate-skill-job relationship KG) │
└──────────────────────────────────────────────────────────┘

## Tech Stack

1. Frontend
   - Framework: React.js (with TailwindCSS)
   - Features: Recruiter dashboard, candidate ranking UI, chatbot
   - Alternative: Angular (if preferred)

2. Backend (API Layer)
   - Framework: FastAPI (Python)
   - Packages: pydantic, uvicorn, sqlalchemy
   - Purpose: REST APIs, data validation, DB operations

3. Machine Learning & NLP
   - Libraries: spaCy (NER, resume parsing), scikit-learn (scoring), Hugging Face Transformers (BERT, Sentence-BERT)
   - ML Serving: joblib / ONNX Runtime

4. Generative AI
   - LLM APIs: OpenAI / Azure OpenAI for summarization, JD rewriting, interview question generation
   - Alternative: Hugging Face models (open-source)

5. Agentic AI
   - Framework: LangChain / LlamaIndex
   - Purpose: Multi-agent orchestration (screening, recruiter assistant, engagement, diversity)

6. Database
   - PostgreSQL (structured job & candidate data)
   - MongoDB (for parsed resume JSONs, embeddings)

7. Infrastructure & DevOps
   - Docker & Docker Compose (containerization)
   - GitHub Actions / GitLab CI (CI/CD)
   - Cloud: AWS / GCP / Azure
   - Monitoring: Prometheus + Grafana

8. Extras
   - Authentication: JWT / OAuth2
   - Logging: Python logging + ELK stack (optional)
   - Testing: pytest (backend), Jest (frontend)


