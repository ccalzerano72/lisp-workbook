---
id: system-rules
type: standard
scope: global
status: active
priority: critical
updated: 2026-09-11
volatility: low
confidence: high
source:
  - repository
  - documentation
depends_on:
  - index
triggers:
  - rules
  - startup
  - protocol
  - agent
---

# AI Operating Rules — AI-KB Specification v1.0

This workspace uses the AI Knowledge Base (AI-KB) protocol. All AI agents working in this repository must strictly abide by these operating rules.

## 1. Startup & Initial Session Entry
- At session startup, load **ONLY** `.ai-docs/index.md`.
- Do **NOT** automatically scan or bulk-read the workspace or `.ai-docs/`.

## 2. Task Classification & Document Routing
- For every user task, classify:
  - **Domain:** (e.g., editorial authoring, exercise design, LaTeX styling, bug fixing, cross-volume synchronization).
  - **Target Volume/Component:** (`teoria/`, `manuale/`, or shared).
- Use `.ai-docs/index.md` to classify candidate documents:
  - **REQUIRED:** Documents indispensable for the task.
  - **CANDIDATE:** Documents that might be needed depending on depth.
  - **IRRELEVANT:** Documents unrelated to the task (must stay unloaded).

## 3. Minimal Loading & Progressive Expansion
- Start with the smallest useful context (typically 1–2 documents, e.g., `state.md` or `standards/editorial-and-typography.md`).
- Follow dependencies (`depends_on`) incrementally only when additional context is genuinely required.
- Isolate context: keep unrelated knowledge strictly unloaded.

## 4. Source-of-Truth Hierarchy & Precedence
When information conflicts, resolve according to this hierarchy:
1. Current explicit user instruction
2. Actual current project/workspace state (source files, compiled output)
3. Primary project documentation (`.kiro/steering/progetto-lisp.md`, review files)
4. AI-KB (`.ai-docs/`)
5. AI inference

- Current workspace reality always overrides stale AI-KB documentation.
- When a conflict is discovered, treat the workspace as authoritative and update the AI-KB.

## 5. Epistemic Rigor: Fact vs Inference vs Unknown
- **FACT:** Directly verifiable from source files, LaTeX code, or explicit user directives.
- **INFERENCE:** Derived logically from facts, but not explicitly stated. Must be flagged as inference.
- **UNKNOWN:** Missing information. Must **NEVER** be fabricated or assumed without evidence.

## 6. Maintenance & Synchronization
- Update `.ai-docs/` whenever structural changes occur (e.g., adding/renaming chapters, changing exercise counts or tiers, altering typographic standards, resolving review items).
- Follow `update.md` for incremental updates.
- Keep `state.md` up to date with task progress and known issues.
- Never let dead, duplicate, or obsolete documentation accumulate.
