# Canon Dual-Backend Pipeline (Gray-Core CMA Prototype)

This repository contains an experimental pipeline for **hallucination-aware claim ingestion**
using a **multi-stage uncertainty routing architecture**.

The core idea is simple:

> Not all model outputs should be treated equally —
> ambiguous claims must remain ambiguous unless evidence accumulates.

---

## What this system does

The pipeline enforces **meaningful state separation** across claims:

- **PASS**: high-confidence, stable claims
- **GRAY**: ambiguous claims routed for verification
- **GHOST**: unstable / hallucination-prone claims rejected early

Key components:

1. **Pastor Gate**
A statistical filter separating clean vs polluted embeddings.

2. **CMA (Contextual Modulation Analysis)**
Measures claim stability under small semantic perturbations.

3. **Gray Core**
Generates verification questions instead of forced answers.

4. **Human-Gated Knowledge Core**
Prevents automatic promotion to “supported” without review.

---

## Why this matters

Most hallucination mitigation strategies focus on:
- better prompting
- post-hoc filtering
- larger models

This system instead asks:

> *Should this claim even be answered yet?*

The result is a pipeline that **refuses premature certainty by design**.

---

## Current status

- ✅ Dual backend tested (Gemini free tier + fallback embedding)
- ✅ End-to-end execution confirmed
- ✅ Meaningful state differentiation observed
- ❌ No external ground-truth evaluation yet
- ❌ No human review UI (by design, out of scope)

This is a **prototype for validation**, not a production system.

---

## Disclaimer

This repository is shared to document **a perspective and experimental result**,
not to claim a finalized solution.


Initial commit: gray-core CMA pipeline with dual-backend execution

- Implemented multi-stage claim routing (PASS / GRAY / GHOST)
- Confirmed end-to-end execution on Gemini free tier
- Observed meaningful state separation without human promotion
- Prototype focused on uncertainty containment, not answer generation


Further validation, cost-aware deployment, and scaling analysis remain open.
