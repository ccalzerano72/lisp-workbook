---
id: index
type: index
scope: global
status: active
priority: critical
updated: 2026-09-11
volatility: medium
confidence: high
source:
  - repository
---

# Common Lisp Educational Book Series — Knowledge Base Index

## Project Identity
- **Name:** Common Lisp Book (Fondamenti & Workbook)
- **Author:** Carmelo Calzerano
- **Type:** HYBRID / OTHER (EDITORIAL / WRITING + STUDY / EDUCATIONAL)
- **Objective:** Two-volume educational manual (narrative textbook + hands-on workbook with 148 graded exercises) for university students with an imperative background (C, Java, Python) learning ANSI Common Lisp.

## Current Status
- **Phase:** Revision & Refinement (First Edition, Sept 2026).
- Both volumes written and compiled to PDF (`teoria/` 9 chapters + 2 appendices; `manuale/` 148 exercises, hints, solutions, cheatsheet, quick reference).
- Review round 2 completed (`REVISIONE_COMPLETA_002.md`); cataloged action items pending.

## Document Routing Map

| ID | Path | Description | Task / Domain |
|---|---|---|---|
| `system-rules` | `system-rules.md` | Operating rules & protocol for AI agents | Startup, context loading, routing |
| `state` | `state.md` | Current implementation state, backlogs, known issues | Project monitoring, task selection |
| `volume-structure` | `architecture/volume-structure.md` | Structure and inter-volume coupling of Teoria & Workbook | Structural edits, chapter/exercise mapping |
| `editorial-and-typography` | `standards/editorial-and-typography.md` | Pedagogical philosophy, typographic constraints, box styles | Content authoring, formatting, review |
| `adr-001-functional-first-progression` | `decisions/ADR-001-functional-first-progression.md` | Rationale for functional-first pedagogical progression | Pedagogy, lesson planning, tone |
| `adr-002-two-volume-decoupling` | `decisions/ADR-002-two-volume-decoupling.md` | Rationale for decoupling Theory and Workbook | Structure, cross-volume referencing |
| `adr-003-tiered-exercise-tracks` | `decisions/ADR-003-tiered-exercise-tracks.md` | Rationale for three-tier exercise tracks (Min/Std/Cmpl) | Exercise design, tagging, solutions |
