---
id: adr-003-tiered-exercise-tracks
type: decision
scope: global
status: active
priority: medium
updated: 2026-09-11
volatility: low
confidence: high
source:
  - repository
  - documentation
depends_on:
  - index
related:
  - volume-structure
  - editorial-and-typography
triggers:
  - decision
  - adr
  - tracks
  - exercises
  - minimo
  - standard
  - completo
---

# ADR-003: Three-Tier Exercise Pathways

## Decision
Structure the 148 workbook exercises into three nested pathways using distinct visual badges and border styles:
1. **Percorso Minimo (25 exercises):** Essential key concepts (`essbox`, solid blue border, ◆).
2. **Percorso Standard (79 exercises):** Comprehensive coverage recommended for typical university coursework (Minimo + `stdbox`, solid green border, ■).
3. **Percorso Completo (148 exercises):** Full collection for mastery, including edge cases and projects (Standard + `colbox`, dashed gray border, ○).

## Status
Active

## Context
Students and instructors have varying time constraints. A uniform list of 148 exercises is overwhelming for a short course or quick study, but reducing the total count limits depth for motivated students seeking mastery.

## Rationale
- Explicit pathways allow students with limited time to cover all foundational concepts without gaps.
- Visual badges in the exercise box header provide immediate recognition of priority while working through the text.
- Difficulty stars (★ to ★★★★★) provide an orthogonal difficulty indicator independent of syllabus priority.

## Alternatives
- *Flat Exercise List:* Number exercises 1 to 148 without priority distinction. Rejected because learners cannot easily prioritize when constrained by time.
- *Difficulty-Only Classification:* Rely solely on star ratings. Rejected because an essential foundational concept might be easy (★) or medium (★★), whereas an optional edge-case drill could also be easy (★).

## Consequences
- **Positive:** Clear, flexible study options for different student profiles and course durations.
- **Positive:** Immediate visual guidance in printed or PDF format.
- **Negative:** Requires strict accounting of exercise counts (25 ◆, 54 ■, 69 ○ = 148 total) across introductory tables, chapter summaries, and cross-volume references.
