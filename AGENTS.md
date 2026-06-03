# AGENTS.md — Puelche: Crea y Valida Grant Application

## Project

**Puelche** is an agent-based AI system that supports the evaluation of bids in Chilean public procurement (licitaciones). It assists evaluation committees by automating document analysis, compliance checking, and evidence structuring — while keeping all decisions under human authority.

The current task is drafting the profile form for **CORFO's Crea y Valida (Fase I, 2026-1)**, a grant focused on **bringing validated technologies to market**. It emphasizes commercial readiness, market entry strategy, and product-market fit — not basic scientific research.

## Knowledge Base

All reference material is in `KB/`:

- `KB/FONDEF/Formulacion.md` — Full prior formulation for a FONDEF grant. Use this as the authoritative source of technical detail, problem framing, and solution architecture. **Do not copy it verbatim** — it was written for a research-oriented grant with different evaluation criteria.
- `KB/FONDEF/` — Supporting documents (TRL analysis, cost spreadsheets, presentation) from that prior formulation.
- `KB/Bases tecnicas Crea y Valida.pdf` — The technical rules of the Crea y Valida contest.
- `KB/Corfo Innova - Crea y Valida Form.pdf` — The actual form being filled out.

## Key Differences: FONDEF vs. Crea y Valida

| Dimension | FONDEF (prior) | Crea y Valida (this) |
|---|---|---|
| Focus | Scientific R&D | Lab-to-market transition |
| Emphasis | Research rigor, publications | Product validation, commercial traction |
| Language | Academic | Entrepreneurial, market-oriented |
| Deliverables | Research outputs | Prototypes, pilots, market entry |
| Audience | Research evaluators | Innovation/commercialization evaluators |

## Working Conventions

- The form to fill is `corfo_crea_y_valida_perfil_de_proyecto.md`.
- Answers should be in **Spanish**, concise, and respect character limits. When a question specifies a maximum character count, count the answer before writing it and ensure it does not exceed that limit — trim content if needed rather than going over.
- Reuse facts, numbers, and technical descriptions from the FONDEF formulation, but reframe them toward commercial value and market validation.
- TRL declared: **3**. Narrative should support this and show a credible path to TRL 5–6.
