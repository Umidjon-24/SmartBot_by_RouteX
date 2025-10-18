## SmartBot – AI Recruitment Assistant (HackNU 2025)

SmartBot is an intelligent widget for automated candidate screening and clarification.  
It analyzes resumes against job requirements, identifies mismatches, and dynamically asks clarifying questions through an interactive chatbot embedded on the employer’s website.  

This project was built for **HackNU 2025**.

---

## Overview

The system automates the early stage of recruitment:
1. Candidate submits an application through the website widget.  
2. SmartBot parses the resume and compares it with the vacancy requirements.  
3. If inconsistencies or missing info are found, SmartBot asks clarifying questions in real time.  
4. Answers are stored, the candidate’s relevance score is updated, and the employer sees detailed results in the dashboard.

**Core Goals:**
- Automate recruiter’s manual screening
- Improve candidate experience via chat interaction
- Provide employers with transparent, data-driven candidate scoring

---

## System Architecture

| Component | Description |
|------------|-------------|
| **Frontend Widget (React)** | Embeddable chatbot on the employer’s career page |
| **Backend (FastAPI)** | API, resume analysis, LLM integration, scoring logic |
| **Database (PostgreSQL)** | Jobs, candidates, dialogs, and scoring data |
| **Cache (Redis)** | Real-time session state and WebSocket communication |
| **LLM Service** | Generates clarifying questions and human-readable explanations |
| **Employer Dashboard (React)** | Interface for viewing candidates, scores, and chat history |

---

## Features

- **Resume & Vacancy Comparison** (city, experience, languages, salary, format)
- **AI-driven Clarification Dialog**
- **Transparent Relevance Scoring**
- **Employer Dashboard** for sorting, filtering, and reviewing candidates
- **JWT Authentication** for employer access
- **Multi-language Support (i18n-ready)**

---

## Tech Stack

**Backend**
- Python 3.11+
- FastAPI
- PostgreSQL
- Redis
- SQLAlchemy / Alembic
- OpenAI / Anthropic API (for LLM tasks)

**Frontend**
- React + TypeScript
- TailwindCSS
- shadcn/ui components
- WebSocket (real-time chat)
- Vite build system

---

## Core Logic Flow

```text
1. Candidate applies → Widget sends data to /api/application
2. Backend parses resume → extracts fields (city, experience, skills, etc.)
3. Compare with vacancy → detect mismatches or low-confidence fields
4. For each mismatch → LLM generates clarifying question
5. Candidate answers → score recalculated
6. Employer dashboard displays candidate list + relevance + reasons
