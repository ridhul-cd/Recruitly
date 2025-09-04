Recruitly/
│── README.md             # Project description
│── requirements.txt      # Python dependencies
│── docker-compose.yml    # For multi-service setup
│── .gitignore
│
├── backend/              # FastAPI / Flask backend
│   │── main.py           # Entry point (FastAPI app)
│   │── config.py         # Config/env variables
│   │── routers/          # API endpoints
│   │   │── resumes.py    # Resume upload & parsing APIs
│   │   │── jobs.py       # Job description APIs
│   │   │── ranking.py    # Candidate ranking APIs
│   │   │── agents.py     # Agent orchestration APIs
│   │── services/         # Business logic
│   │   │── parser.py     # Resume parsing logic
│   │   │── scorer.py     # Candidate scoring ML
│   │   │── genai.py      # Summaries, JD rewriting
│   │   │── agents.py     # Screening/Recruiter/Diversity agents
│   │── models/           # Pydantic models / DB schemas
│   │── database/         # DB setup (SQLAlchemy/ORM)
│   │── tests/            # Unit & integration tests
│
├── ml/                   # ML & NLP models
│   │── resume_parser.ipynb  # Initial experiments
│   │── scorer.ipynb         # Candidate scoring experiments
│   │── models/              # Saved ML models (BERT, classifiers)
│   │── preprocessing.py     # Data cleaning & preprocessing
│
├── genai/                # GenAI utilities
│   │── summarizer.py     # Resume & candidate summaries
│   │── jd_rewriter.py    # JD rewriting
│   │── question_gen.py   # Interview question generation
│
├── agents/               # Agentic AI
│   │── screening_agent.py
│   │── recruiter_agent.py
│   │── engagement_agent.py
│   │── diversity_agent.py
│   │── orchestrator.py   # Handles coordination
│
├── data/                 # Sample data
│   │── resumes/          # Sample resumes (PDF/DOCX)
│   │── jobs/             # Sample job descriptions
│   │── processed/        # Parsed/structured JSON
│
├── frontend/             # React / Angular frontend
│   │── src/
│   │   │── components/   # UI components
│   │   │── pages/        # Pages (Upload, Dashboard, Chatbot)
│   │   │── services/     # API calls
│   │── public/
│   │── package.json
│
├── docs/                 # Documentation
│   │── architecture.md   # Architecture diagrams
│   │── api.md            # API specs
│   │── roadmap.md        # Development roadmap
