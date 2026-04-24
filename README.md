<div align="center">

<img src="./media/fairlend-logo.png" alt="FairLend Logo" height="80" />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<img src="./media/deloitte-logo.png" alt="Deloitte Logo" height="80" />

<br/><br/>

# FairLend — AI Fair Lending Validation Workbench

### GenAI-powered, human-in-the-loop platform for detecting, quantifying, and mitigating bias in education loan AI systems

<br/>

[![Built With](https://img.shields.io/badge/Built%20With-FastAPI%20%7C%20Next.js%2014%20%7C%20Google%20Gemini-1d6f42?style=for-the-badge&logo=python&logoColor=white)](https://github.com/aayusharmaaa/Fairlend)
[![Collaboration](https://img.shields.io/badge/In%20Collaboration%20With-Deloitte-86BC25?style=for-the-badge)](https://github.com/aayusharmaaa/Fairlend)
[![Domain](https://img.shields.io/badge/Domain-Responsible%20AI%20%7C%20FinTech-0ea5e9?style=for-the-badge)](https://github.com/aayusharmaaa/Fairlend)

</div>

---

## Product Demo

<div align="center">

[![Watch Demo](./media/dashboard-overview.png)](https://drive.google.com/file/d/1WEtUOMbM7xz_MNx5zw3YgwkWfablmjH-/preview)

**[▶ Click to Watch Full Demo Video](https://drive.google.com/file/d/1WEtUOMbM7xz_MNx5zw3YgwkWfablmjH-/preview)**

</div>

---

## Overview

**FairLend** was built as part of a GenAI Capstone initiative in collaboration with **Deloitte**, addressing a critical gap in how financial institutions test and validate AI-driven loan decision systems.

Indian banks process over **700,000 education loan applications annually**. As lending increasingly shifts to AI-assisted decisioning, unchecked models carry significant risks — from regulatory non-compliance with RBI fair lending guidelines to systematic discrimination against underrepresented applicants.

FairLend is a full-stack validation and audit workbench that gives compliance teams, risk analysts, and model governance officers a structured, automated pipeline to test AI models for bias **before** they reach production.

The platform replaces what previously took compliance teams **2–3 weeks of manual spreadsheet auditing** with an end-to-end agentic workflow completing in **under 10 minutes** — across **3,100+ synthetic applicant profiles** and **5 bias dimensions**.

---

## Key Metrics

<div align="center">

| Metric | Result |
|---|---|
| Synthetic profiles evaluated per run | **3,100+** |
| Bias dimensions covered | **5** |
| Audit time vs. manual baseline | **10 min vs. 2 weeks** |
| Detected Urban vs. Rural approval gap | **12.5%** |
| Detected interest rate penalty (low-income) | **+1.56%** |
| Fairness score improvement post-mitigation | **65 → 85+ / 100** |
| Approval parity target | **≥ 0.95** |
| Interest rate disparity target | **< 0.5%** |
| Edge case coverage target | **≥ 95%** |

</div>

---

## How It Works

<div align="center">

![Workflow](./media/workflow-cycle.png)

</div>

The platform runs a **Continuous Proactive Validation** loop across five stages:

**1. Generate** — GenAI (Google Gemini) creates 3,100+ realistic synthetic student loan profiles covering rural/urban geography, diverse income bands (₹8L–₹50L), CIBIL scores (300–900), gender, education, and edge cases (first-time borrowers, self-employed, widows, border regions).

**2. Score** — Profiles are evaluated through two parallel scoring modes: a *fair model* (merit-based: academic performance, creditworthiness, repayment capacity) and a *biased simulation* (mimicking unconscious geographic, income, and demographic discrimination patterns).

**3. Detect** — The Fairness Metrics Engine quantifies bias across five dimensions: Geographic (Urban vs. Rural, Tier-1 vs. Tier-2/3), Income, Gender & Co-applicant, Credit Score Logic, and Edge Case Robustness. Critical and high-severity findings are surfaced to analysts.

**4. Validate** — Human domain experts (compliance officers, risk analysts) review flagged findings through a structured Human-in-the-Loop interface. They annotate each finding with severity ratings, root-cause analysis, and mitigation guidance.

**5. Mitigate** — An agentic mitigation loop reads expert feedback, refines scoring logic and prompt weights, re-evaluates all profiles, and generates a before/after comparison report — iterating until fairness targets are met.

---

## Platform Snapshots

### Live Dashboard — Bias KPIs & Heatmap

<div align="center">

![Dashboard Overview](./media/dashboard-overview.png)

</div>

The real-time dashboard gives analysts a complete picture: **Approval Parity**, **Interest Gap**, **Collateral Gap**, and a composite **Fairness Score**, alongside a dimension-level bias heatmap and ranked top findings with severity indicators.

---

### Synthetic Profile Generation — Coverage Across India

<div align="center">

![Profile Diversity](./media/profile-diversity.png)

</div>

Each test run generates synthetic applicant profiles spanning the full demographic landscape of Indian education loan applicants — geographic spread across urban Tier-1 and rural Tier-2/3 cities, income bands from ₹8L to ₹50L, CIBIL scores 300–900, diverse educational backgrounds, and edge cases such as first-time borrowers, self-employed parents, and widow co-applicants. This ensures the fairness audit covers the real-world diversity of applicants the model will encounter.

---

### Mitigation in Action — Before vs. After

<div align="center">

![Mitigation Results](./media/mitigation-results.png)

</div>

After detecting a **12% Urban vs. Rural approval gap** (Parity Ratio 0.85), the agentic mitigation loop runs iterative scoring adjustments guided by human expert feedback. After one mitigation cycle (8 iterations), the approval gap closes to **2%** — pushing the Parity Ratio from **0.85 to 0.97**, well within the ≥0.95 fairness target.

---

## System Architecture

<div align="center">

![System Architecture](./media/system-architecture-diagram.png)

</div>

The platform is built on a **cloud-native, modular architecture** designed for enterprise integration and horizontal scaling.

| Layer | Technology | Role |
|---|---|---|
| Frontend | Next.js 14, TypeScript, Tailwind CSS | Analyst dashboard, feedback UI, mitigation views |
| API Layer | FastAPI (Python 3.11), WebSocket | REST endpoints, real-time updates, auth |
| GenAI | Google Gemini (via LangChain) | Profile generation, mitigation orchestration |
| Scoring | Scikit-Learn, custom rule engine | Fair & biased model simulation |
| Data | PostgreSQL / SQLite, Redis | Profiles, runs, metrics, feedback storage & caching |
| Async | Celery | Background processing for large profile batches |
| Infra | Docker, Docker Compose | Container-based deployment |

Full component breakdown → [SYSTEM_ARCHITECTURE.md](./SYSTEM_ARCHITECTURE.md)

---

## Business Impact

| Challenge | FairLend Solution |
|---|---|
| Manual audits take 2–3 weeks | Fully automated audit in < 10 minutes |
| Coverage limited to 50–100 test cases | Scales to 3,100+ profiles per run |
| Bias found post-deployment | Pre-deployment validation workflow |
| No structured expert feedback trail | Structured HITL annotation with full traceability |
| Hard to prove fairness improvement | Quantified before/after metric comparison |

---

## Fairness Targets

| Dimension | Metric | Target |
|---|---|---|
| Geographic | Approval Rate Parity | ≥ 0.95 |
| Income | Interest Rate Disparity | < 0.5% |
| Gender | Collateral Requirement Gap | < 10% |
| Edge Cases | Profile Coverage | ≥ 95% |
| Overall | Composite Fairness Score | ≥ 85 / 100 |

---

## Tech Stack

<div align="center">

![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=flat-square&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-0.104-009688?style=flat-square&logo=fastapi&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-14-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5.3-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.3-38B2AC?style=flat-square&logo=tailwindcss&logoColor=white)
![Google Gemini](https://img.shields.io/badge/Google%20Gemini-GenAI-4285F4?style=flat-square&logo=google&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-336791?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-5.0-DC382D?style=flat-square&logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?style=flat-square&logo=docker&logoColor=white)

</div>

---

## Technical Deep Dive

### API Design

The backend exposes a versioned REST API (`/api/v1`) organized into six functional domains, with a WebSocket channel for real-time metric streaming to the frontend dashboard.

| Endpoint Group | Purpose |
|---|---|
| `/auth` | JWT-based employee login, token validation, session management |
| `/profiles` | Synthetic profile generation, upload (CSV/ZIP), and listing |
| `/scoring` | Trigger fair or biased scoring runs against loaded profiles |
| `/metrics` | Retrieve computed fairness metrics, parity ratios, and disparity indicators |
| `/feedback` | Submit, list, and manage human expert annotations and severity ratings |
| `/mitigation` | Launch mitigation cycles, retrieve before/after comparison reports |
| `ws://…/ws/metrics` | WebSocket stream for live fairness score and KPI updates |

---

### End-to-End Data Flow

```
Browser (Next.js 14)
  │
  ├─ REST calls ──► FastAPI Router
  │                    │
  │         ┌──────────┼──────────┐
  │         ▼          ▼          ▼
  │   Profile Svc  Scoring Svc  Metrics Svc
  │         │          │          │
  │         └────► SQLite / PostgreSQL (ORM via SQLAlchemy)
  │                    │
  │         ┌──────────┘
  │         ▼
  │   Celery Worker (async batch scoring)
  │         │
  │         ▼
  │   GenAI Service ──► Google Gemini API
  │         │           (profile generation, mitigation prompts)
  │         ▼
  │   Redis (task queue + response cache)
  │
  └─ WebSocket ──► Real-time KPI push to dashboard
```

---

### Key Engineering Decisions

| Decision | Rationale |
|---|---|
| **FastAPI over Django/Flask** | Native async support; automatic OpenAPI docs; Pydantic validation built-in — essential for a data-heavy validation API |
| **SQLite for demo, PostgreSQL for prod** | Zero-dependency local setup for showcasing; same SQLAlchemy ORM layer switches to PostgreSQL via a single env variable |
| **Celery + Redis for async scoring** | Scoring 3,100+ profiles blocks for seconds; offloading to Celery workers keeps the API responsive and allows horizontal scale-out |
| **WebSocket for live metrics** | Polling would miss intermediate scoring updates; WebSocket lets the dashboard show live fairness score changes during a mitigation run |
| **LangChain for GenAI orchestration** | Abstracts provider switching (OpenAI ↔ Gemini); structured output parsing and retry logic built-in; prompt chain management for multi-step mitigation |
| **Next.js App Router + TanStack Query** | Server components for fast initial load; TanStack Query handles cache invalidation for metric refreshes without manual state management |
| **Synthetic-only data** | Eliminates PII risk entirely; allows open sharing of test results and audit artifacts without data governance constraints |

---

### Scalability

- **Horizontal API scaling** — FastAPI is stateless; multiple instances sit behind a load balancer sharing the same PostgreSQL and Redis layer
- **Worker scale-out** — Celery workers are independently scalable; adding workers reduces large-batch scoring time linearly
- **Caching** — Redis caches computed fairness metrics; repeated dashboard loads hit cache, not the database
- **Containerised** — Docker Compose for local; Kubernetes-ready for production with minimal manifest changes

---

### Security

| Control | Implementation |
|---|---|
| Authentication | JWT (HS256) with expiring tokens; `python-jose` for signing and verification |
| Password storage | bcrypt hashing; no plaintext credentials stored anywhere |
| Input validation | All request bodies validated via Pydantic schemas before reaching service layer — prevents injection and malformed payloads |
| CORS | Strict allowlist of frontend origins; wildcard disabled in production config |
| Secrets management | All API keys and DB credentials via environment variables; never hardcoded or committed |
| PII protection | Entirely synthetic applicant data; no real customer records processed or stored |

---

## Repository Scope

This is a **public product showcase**. It intentionally includes product description, architecture, demo media, and metrics — and intentionally excludes all source code, proprietary algorithms, scoring logic, internal prompts, and deployment configurations.

---

## Contact

For collaboration inquiries, live demos, or case study discussions:

- **LinkedIn:** [linkedin.com/in/aayusharmaaa](https://linkedin.com/in/aayusharmaaa)
- **GitHub:** [github.com/aayusharmaaa](https://github.com/aayusharmaaa)
