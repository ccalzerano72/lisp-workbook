---
id: state
type: state
scope: global
status: active
priority: high
updated: 2026-09-11
volatility: high
confidence: high
source:
  - repository
  - documentation
depends_on:
  - index
triggers:
  - status
  - progress
  - backlog
  - issues
---

# Current Project State

## Implemented
- **Workbook (`manuale/`)**: Complete draft compiled to `workbook.pdf`.
  - 148 exercises across 10 chapters.
  - 3 differentiated tracks: Minimo (25 ◆ `essbox`), Standard (79 ◆+■ `stdbox`), Completo (148 ◆+■+○ `colbox`).
  - Sections: Cheat sheet (`00_cheatsheet.tex`), Quick Reference (`01_reference.tex`), Allegro CL Guide (`00b_ambiente.tex`), Hints (`03_suggerimenti.tex`), Commented solutions (`04_soluzioni.tex`).
- **Teoria (`teoria/`)**: Complete draft compiled to `teoria.pdf` / `main.pdf`.
  - Part I (Basi): Cap. 1–6 (Modello mentale, Funzioni e dati, Liste e ricorsione, Higher-order, Strutture dati, Macro).
  - Part II (Algoritmi e dati esterni): Cap. 7 (Backtracking), Cap. 8 (Stringhe, I/O e parsing).
  - Part III (Stile): Cap. 9 (Stile e professione).
  - Appendici: Appendice Stack, Appendice ADT.
- **Steering & Reviews**:
  - Editorial steering rules (`.kiro/steering/progetto-lisp.md`).
  - Comprehensive reviews Round 1 & Round 2 (`REVISIONE_COMPLETA_001.md`, `REVISIONE_COMPLETA_002.md`).

## In Progress
- Systematic refinement addressing findings from `REVISIONE_COMPLETA_002.md`.

## Planned
- **Priority 1 (High)**:
  - Synchronize inter-volume references (align workbook box references in `teoria/` with exercise numbering in `manuale/`).
  - Resolve discrepancies between exercise requirements and solution code.
- **Priority 2 (Medium)**:
  - Address identified conceptual omissions (`char-digit-p` in Cap. 2; `define-condition` in Cap. 6; expand `defstruct`/CLOS in Cap. 5).
  - Add missing hints for remaining ★★★ exercises in `manuale/parts/03_suggerimenti.tex`.
- **Priority 3 (Low / Polish)**:
  - Typographic check: remove any lingering narrative em-dashes (`---`).
  - Verify ASCII-only compliance for Italian accented characters inside `lstlisting` blocks.

## Blocked
- None.

## Known Issues
- Minor discrepancies between Cap. 1/2 workbook callouts in `teoria` and actual exercise indices in `manuale`.
- Few ★★★ exercises lack corresponding entries in `03_suggerimenti.tex`.
- Localized minor typos documented in `REVISIONE_COMPLETA_002.md`.

## Recent Structural Changes
- Part II and Part III of `teoria/` (Chapters 7, 8, 9) and Appendices written, integrated, and verified in build.
- Review 002 generated, evaluating both volumes with quantitative ratings and cataloging priority fixes.
- AI Knowledge Base initialized under `.ai-docs/` per AI-KB Specification v1.0.
