# Architecture Decision Records (ADR)

This document captures key architectural decisions made while owning and operating a production AI system.

Each decision records context, constraints, and trade-offs to ensure clarity and long-term maintainability.

---

## ADR-001 — Preserve Existing Infrastructure and OAuth

- **Status:** Accepted
- **Context:** The system is already live with users and OAuth 2 (Google APIs) configured.
- **Decision:** Infrastructure and authentication providers remain unchanged.
- **Rationale:**
  - Avoids breaking production auth flows
  - Minimizes risk and downtime
  - Preserves existing trust boundaries
- **Consequences:**
  - Design must work within existing constraints
  - Scaling strategies must not rely on infra changes

---

## ADR-002 — Treat AI as a Probabilistic Dependency

- **Status:** Accepted
- **Context:** AI outputs vary and cannot be assumed correct.
- **Decision:** AI is never treated as a source of truth.
- **Rationale:**
  - Reduces downstream failure risk
  - Enables deterministic fallbacks
- **Consequences:**
  - Additional validation logic required
  - Slightly higher implementation effort, much higher reliability

---

## ADR-003 — Use n8n for Orchestration, Not Business Logic

- **Status:** Accepted
- **Context:** n8n is already used for workflow orchestration.
- **Decision:** Core business logic remains outside n8n where possible.
- **Rationale:**
  - Prevents workflow sprawl
  - Improves debuggability
  - Reduces coupling
- **Consequences:**
  - Clear boundaries between orchestration and logic
  - Better long-term maintainability

---

## ADR-004 — Prefer Incremental Scaling Over Rewrites

- **Status:** Accepted
- **Context:** System is live and cannot tolerate large-scale rewrites.
- **Decision:** Scale incrementally with reversible changes.
- **Rationale:**
  - Lower risk
  - Faster feedback loops
  - Preserves production stability
- **Consequences:**
  - Slower than greenfield redesigns
  - Significantly safer

---

## ADR-005 — Favor Observability Before Optimization

- **Status:** Accepted
- **Context:** Performance issues are often misdiagnosed.
- **Decision:** Add logging, tracing, and metrics before tuning.
- **Rationale:**
  - Prevents premature optimization
  - Enables accurate root-cause analysis
- **Consequences:**
  - Slight upfront effort
  - Long-term operational clarity

---

## ADR Governance

- ADRs are updated when constraints or assumptions change
- Superseded decisions are marked explicitly
- Decisions prioritize stability, clarity, and ownership

---

## Ownership Statement

These decisions reflect deliberate trade-offs made under full system ownership, with accountability for production outcomes.
