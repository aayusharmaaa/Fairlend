<div align="center">
  <br/>
  <img src="./media/fairlend-logo.png" alt="FairLend" height="72" />
  &nbsp;&nbsp;&nbsp;&nbsp;
  <img src="./media/deloitte-logo.png" alt="Deloitte" height="72" />
  <br/><br/>

  # FairLend — AI Fair Lending Validation Workbench

  **GenAI-powered · Human-in-the-Loop · Pre-deployment Bias Validation for Education Loan AI**

  <br/>

  ![Python](https://img.shields.io/badge/Python_3.11-3776AB?style=flat-square&logo=python&logoColor=white)
  ![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
  ![Next.js](https://img.shields.io/badge/Next.js_14-000000?style=flat-square&logo=nextdotjs&logoColor=white)
  ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
  ![Gemini](https://img.shields.io/badge/Google_Gemini-4285F4?style=flat-square&logo=google&logoColor=white)
  ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

  <br/>

  ![Deloitte Collab](https://img.shields.io/badge/Built_in_collaboration_with-Deloitte-86BC25?style=flat-square)
  ![Domain](https://img.shields.io/badge/Domain-Responsible_AI_%7C_FinTech-1d6f42?style=flat-square)
  ![Type](https://img.shields.io/badge/Type-GenAI_Capstone_Project-0ea5e9?style=flat-square)

  <br/><br/>

</div>

---

## Demo

<div align="center">

  [![Watch Demo](./media/dashboard-overview.png)](https://github.com/aayusharmaaa/Fairlend/releases/download/v1.0-demo/fairlend.mp4)

  ### [▶&nbsp;&nbsp;Watch Product Demo](https://github.com/aayusharmaaa/Fairlend/releases/download/v1.0-demo/fairlend.mp4)

</div>

---

## The Problem

Indian banks process over **700,000 education loan applications annually**. As credit decisioning shifts to AI, "black-box" models introduce systemic risks that are difficult to detect until after deployment:

- **Regulatory exposure** — Non-compliance with RBI fair lending guidelines
- **Reputational damage** — Bias discovered post-launch destroys trust
- **Operational bottleneck** — Manually auditing 50 test cases takes 2–3 weeks. Testing 3,000+ edge cases is practically impossible

> There is no streamlined workflow for compliance teams to rapidly test, detect, and fix bias in AI lending models **before** deployment.

---

## The Solution

**FairLend** is a full-stack, GenAI-powered validation and audit workbench built in collaboration with **Deloitte**. It gives compliance officers, risk analysts, and model governance teams an end-to-end pipeline to test AI models for bias at scale — **before they reach production**.

The platform replaces weeks of manual spreadsheet audits with an agentic, human-in-the-loop workflow that completes in **under 10 minutes**, across **3,100+ synthetic applicant profiles** and **5 bias dimensions**.

---

## Impact at a Glance

<div align="center">

| | |
|:---:|:---:|
| **3,100+** synthetic profiles per audit run | **5** bias dimensions detected |
| **10 minutes** vs. 2–3 week manual baseline | **12.5%** urban–rural approval gap detected |
| **+1.56%** interest rate penalty on low-income applicants | **65 → 85+** fairness score after mitigation |

</div>

---

## How It Works

<div align="center">

![Validation Loop](./media/workflow-cycle.png)

</div>

FairLend runs a **Continuous Proactive Validation** loop across five stages:

| Stage | What Happens |
|---|---|
| **1. Generate** | Google Gemini creates 3,100+ realistic synthetic student profiles — rural/urban, diverse income bands (₹8L–₹50L), CIBIL scores (300–900), gender, education backgrounds, and edge cases (first-time borrowers, self-employed, widowed applicants, border regions) |
| **2. Score** | Profiles run through two parallel models — a *fair scorer* (merit-based: academic record, creditworthiness, repayment capacity) and a *bias simulator* (replicating unconscious geographic, income, and demographic discrimination) |
| **3. Detect** | The Fairness Metrics Engine quantifies disparity across 5 dimensions: Geographic, Income, Gender & Co-applicant, Credit Logic, and Edge Case Robustness. Critical findings are ranked and surfaced to analysts |
| **4. Validate** | Human experts review flagged findings via a structured HITL interface — annotating severity, root cause, and mitigation guidance for governance traceability |
| **5. Mitigate** | An agentic loop reads expert feedback, refines scoring weights and logic, re-evaluates all profiles, and generates quantified before/after comparison reports — iterating until fairness targets are met |

---

## Dashboard

<div align="center">

![Dashboard](./media/dashboard-overview.png)

</div>

The real-time analyst dashboard provides:

- **Approval Parity** — ratio of approval rates across demographic groups
- **Interest Rate Gap** — disparity in rates across income and geography
- **Collateral Requirement Gap** — differential collateral demands across groups
- **Composite Fairness Score** — single 0–100 governance metric
- **Bias Heatmap** — severity distribution across all 5 dimensions
- **Top Findings Panel** — ranked critical issues with group-level breakdowns

---

## Fairness Targets

<div align="center">

| Dimension | Metric | Target | Status |
|:---:|:---:|:---:|:---:|
| Geographic | Approval Rate Parity | ≥ 0.95 | Validated post-mitigation |
| Income | Interest Rate Disparity | < 0.5% | Validated post-mitigation |
| Gender | Collateral Requirement Gap | < 10% | Validated post-mitigation |
| Edge Cases | Profile Coverage | ≥ 95% | Achieved |
| Overall | Composite Fairness Score | ≥ 85 / 100 | 65 → **87** post-mitigation |

</div>

---

## System Architecture

<div align="center">

![Architecture](./media/system-architecture-diagram.png)

</div>

<div align="center">

| Layer | Technology | Role |
|:---|:---|:---|
| **Frontend** | Next.js 14, TypeScript, Tailwind CSS, Recharts | Analyst dashboard, feedback UI, before/after comparison |
| **API** | FastAPI (Python 3.11), WebSocket | REST endpoints, real-time streaming, JWT auth |
| **GenAI** | Google Gemini via LangChain | Profile generation & agentic mitigation orchestration |
| **Scoring** | Scikit-Learn + custom rule engine | Fair and biased model simulation |
| **Data** | PostgreSQL / SQLite, Redis | Profile storage, metrics, feedback, run traceability |
| **Async** | Celery | Background batch processing for large profile sets |
| **Infra** | Docker, Docker Compose | Containerised, cloud-ready deployment |

</div>

Full component breakdown → [SYSTEM_ARCHITECTURE.md](./SYSTEM_ARCHITECTURE.md)

---

## Business Impact

<div align="center">

| Without FairLend | With FairLend |
|:---|:---|
| Manual audits: 2–3 weeks per cycle | Automated audit: < 10 minutes end-to-end |
| Test coverage: 50–100 hand-picked cases | Coverage: 3,100+ diverse synthetic profiles |
| Bias discovered after production rollout | Bias caught and fixed before deployment |
| No audit trail for regulatory review | Structured HITL annotation with full traceability |
| Hard to quantify improvement | Quantified before/after fairness metric comparison |
| Teams blocked on compliance bottlenecks | Compliance officers unblocked via agentic automation |

</div>

---

## Tech Stack

<div align="center">

![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-0.104-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-14-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5.3-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.3-38B2AC?style=for-the-badge&logo=tailwindcss&logoColor=white)

![Google Gemini](https://img.shields.io/badge/Google_Gemini-GenAI-4285F4?style=for-the-badge&logo=google&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-Orchestration-1C3C3C?style=for-the-badge)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-5.0-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?style=for-the-badge&logo=docker&logoColor=white)

</div>

---

## Scope of This Repository

This is a **public product showcase**. It contains the product vision, architecture, demo media, and impact metrics.

Source code, proprietary algorithms, scoring logic, internal GenAI prompts, and deployment configurations are excluded from this repository.

---

## Contact

<div align="center">

Built by **Aayush Sharma** · GenAI Capstone · In collaboration with Deloitte

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Aayush_Sharma-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aayusharmaaa)
[![GitHub](https://img.shields.io/badge/GitHub-aayusharmaaa-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/aayusharmaaa)

</div>
