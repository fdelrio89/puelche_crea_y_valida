# AGENTS.md — Puelche: Crea y Valida Grant Application

## Project

**Puelche** is an agent-based AI system that supports the evaluation of bids in Chilean public procurement (licitaciones). It assists evaluation committees by automating document analysis, compliance checking, and evidence structuring — while keeping all decisions under human authority.

The current task is drafting the **Fase II application form** for **CORFO's Crea y Valida (2026-1)**, a grant focused on **bringing validated technologies to market**. It emphasizes commercial readiness, market entry strategy, and product-market fit — not basic scientific research. Fase I (the project profile) is already submitted; its form and evaluator feedback live in `Phase 1/`.

## Knowledge Base

Shared reference material is in `KB/`; phase-specific material lives under `Phase 1/` and `Phase 2/`:

- `KB/FONDEF/Formulacion.md` — Full prior formulation for a FONDEF grant. Use this as the authoritative source of technical detail, problem framing, and solution architecture. **Do not copy it verbatim** — it was written for a research-oriented grant with different evaluation criteria.
- `KB/FONDEF/` — Supporting documents (TRL analysis, cost spreadsheets, presentation) from that prior formulation.
- `KB/Bases tecnicas Crea y Valida.pdf` — The technical rules of the Crea y Valida contest.
- `Phase 2/Corfo Innova - Crea y Valida Form.pdf` — The Fase II form being filled out (`Phase 1/` holds the Fase I form).
- `Phase 1/phase_1_feedback.md` — CORFO evaluation committee's feedback on the Phase 1 project profile, with observations, recommendations, and priority actions for Phase 2. Address these points when refining the proposal.

## Key Differences: FONDEF vs. Crea y Valida

| Dimension | FONDEF (prior) | Crea y Valida (this) |
|---|---|---|
| Focus | Scientific R&D | Lab-to-market transition |
| Emphasis | Research rigor, publications | Product validation, commercial traction |
| Language | Academic | Entrepreneurial, market-oriented |
| Deliverables | Research outputs | Prototypes, pilots, market entry |
| Audience | Research evaluators | Innovation/commercialization evaluators |

## Working Conventions

- The form to fill is `Phase 2/fase_2_corfo_crea_y_valida_postulacion.md`. The submitted Fase I profile (`Phase 1/fase_1_corfo_crea_y_valida_perfil_de_proyecto.md`) is the main source to reuse and reframe from.
- Answers should be in **Spanish**, concise, and respect character limits. When a question specifies a maximum character count, count the answer before writing it and ensure it does not exceed that limit — trim content if needed rather than going over.
- Reuse facts, numbers, and technical descriptions from the FONDEF formulation, but reframe them toward commercial value and market validation.
- TRL declared: **3**. Narrative should support this and show a credible path to TRL 5–6.
