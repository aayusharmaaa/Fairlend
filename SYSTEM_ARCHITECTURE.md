<div align="center">
  <br/>
  <img src="./media/fairlend-logo.png" alt="FairLend" height="56" />
  &nbsp;&nbsp;&nbsp;
  <img src="./media/deloitte-logo.png" alt="Deloitte" height="56" />
  <br/><br/>

  # System Architecture — FairLend

  **Cloud-Native · Modular · Enterprise-Ready**

  <br/>
</div>

---

## Architecture Diagram

<div align="center">

![System Architecture](./media/system-architecture-diagram.png)

</div>

---

## Design Principles

FairLend is built around four core design principles:

- **Modularity** — Each service owns a single responsibility and can be developed, scaled, or replaced independently
- **Auditability** — Every profile, scoring run, bias finding, and expert annotation is persisted with full traceability across evaluation cycles
- **Scalability** — Async task processing (Celery) decouples compute-heavy operations from the UI; the architecture scales horizontally via Docker/Kubernetes
- **Security** — Synthetic data eliminates PII exposure; JWT-based authentication, Pydantic input validation, and CORS controls enforce access boundaries

---

## Component Breakdown

### Frontend — Next.js 14

The analyst-facing web application built with React, TypeScript, and Tailwind CSS.

| Page | Purpose |
|---|---|
| **Dashboard** | Real-time KPI cards, bias heatmap, and top findings panel |
| **Profiles** | Browse and filter generated synthetic applicant profiles |
| **Bias Analysis** | Detailed filterable findings table with severity indicators |
| **Feedback** | Structured HITL annotation form for domain expert review |
| **Mitigation** | Before/after metric comparison and run history |

- Communicates with the backend over **REST API** and **WebSocket** for live updates
- Role-based access control (Admin, Analyst, Manager)
- JWT tokens stored client-side; interceptors auto-refresh and redirect on expiry

---

### API Layer — FastAPI (Python 3.11)

High-performance async REST API with WebSocket support.

| Endpoint Group | Responsibility |
|---|---|
| `/auth` | Login, token issuance, and user identity |
| `/profiles` | Profile generation triggers and retrieval |
| `/scoring` | Fair and biased scoring run management |
| `/metrics` | Bias metric computation and retrieval |
| `/feedback` | Expert annotation submission and history |
| `/mitigation` | Mitigation loop execution and result storage |
| `/dashboard` | Aggregated KPI data for dashboard views |
| `ws/metrics` | WebSocket stream for real-time metric updates |

- Pydantic schemas enforce strict request/response validation
- SQLAlchemy ORM manages all database interactions
- Dependency injection pattern used throughout for testability

---

### GenAI Layer — Google Gemini via LangChain

The intelligence layer responsible for profile generation and agentic mitigation.

**Profile Generation**
- Prompted with diversity constraints: geography (Urban Tier-1 / Rural Tier-2/3), income bands (₹8L–₹50L), CIBIL scores (300–900), gender, education stream, and employment type
- Generates structured JSON profiles at scale with realistic Indian student loan demographics
- Edge case injection: first-time borrowers, self-employed, widowed applicants, border regions

**Agentic Mitigation Orchestrator**
- Reads structured expert feedback from the HITL review
- Identifies root causes and constructs targeted prompt refinements
- Re-runs scoring with updated logic
- Evaluates metric deltas and reports improvement
- Iterates until all fairness targets are satisfied or max iterations reached

---

### Scoring Engine — Scikit-Learn + Rule Engine

Dual-mode profile evaluation system.

| Mode | Logic |
|---|---|
| **Fair Scorer** | Merit-based: academic performance, repayment capacity, creditworthiness — no demographic weighting |
| **Bias Simulator** | Replicates real-world unconscious bias: geographic penalty (rural –15%), income band penalties, gender-linked collateral differentials, CIBIL threshold cliffs |

Outputs per profile: approval decision, interest rate, collateral requirement, and confidence score.

---

### Fairness Metrics Engine

Computes parity and disparity indicators across all 5 bias dimensions.

| Dimension | Metric | Target |
|---|---|---|
| Geographic | Approval Rate Parity (Urban vs. Rural) | ≥ 0.95 |
| Income | Interest Rate Disparity | < 0.5% |
| Gender | Collateral Requirement Gap | < 10% |
| Credit Logic | CIBIL threshold fairness | Consistent treatment |
| Edge Cases | Profile coverage rate | ≥ 95% |

Composite **Fairness Score** (0–100) aggregates all dimensions into a single governance metric.

---

### Data Layer — PostgreSQL / SQLite + Redis

| Store | Purpose |
|---|---|
| **PostgreSQL / SQLite** | Profiles, scoring runs, bias findings, feedback annotations, mitigation history |
| **Redis** | Session caching, Celery task broker, real-time metric state |

Full run-level traceability: every profile, scoring output, metric snapshot, and expert annotation is linked to a timestamped evaluation run.

---

### Async Processing — Celery

Long-running operations (profile generation batches, scoring runs, mitigation iterations) are offloaded to Celery workers, keeping the UI responsive during compute-heavy tasks. Progress is streamed back to the frontend via WebSocket.

---

### Infrastructure — Docker + Docker Compose

All services containerised for consistent, reproducible deployment.

| Container | Service |
|---|---|
| `backend` | FastAPI application |
| `frontend` | Next.js application |
| `db` | PostgreSQL database |
| `redis` | Redis cache & message broker |
| `worker` | Celery async task worker |

Designed for horizontal scaling via Kubernetes. Cloud-agnostic — deployable on AWS, GCP, or Azure.

---

## Security & Governance

| Control | Implementation |
|---|---|
| **Data Privacy** | 100% synthetic data — zero production PII in the validation pipeline |
| **Authentication** | JWT-based auth with role-based access (Admin / Analyst / Manager) |
| **Input Validation** | Pydantic schemas on all API endpoints prevent injection and malformed inputs |
| **CORS** | Strict origin allowlist configured at the API layer |
| **Audit Trail** | All expert annotations, scoring runs, and mitigation actions persisted with timestamps |
| **Secrets Management** | API keys and credentials managed via environment variables, never hardcoded |

---

<div align="center">

← Back to [README](./README.md)

</div>
