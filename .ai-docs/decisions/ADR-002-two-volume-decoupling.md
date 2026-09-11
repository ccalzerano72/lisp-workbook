---
id: adr-002-two-volume-decoupling
type: decision
scope: global
status: active
priority: high
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
  - volumes
  - organization
  - workbook
  - teoria
---

# ADR-002: Two-Volume Decoupled Architecture

## Decision
Split the instructional project into two distinct, physically separated volumes (`teoria/` for narrative concepts and `manuale/` for hands-on practice) linked by explicit bidirectional cross-references.

## Status
Active

## Context
A single monolithic book combining comprehensive conceptual explanation, quick reference tables, and 148 full exercises with solutions creates an unwieldy document where reading and interactive exercise-solving interfere with each other.

## Rationale
- Learners frequently keep a workbook or exercise list open next to their REPL/editor without needing to scroll past pages of theoretical discussion.
- The workbook is self-contained with its own Quick Reference, Cheat Sheet, and hints, while the theory volume provides the deeper narrative without cluttering the exercise workflow.
- Bidirectional linkage (workbook callout boxes in `teoria/` and reading hints in `manuale/`) ensures the two volumes reinforce each other.

## Alternatives
- *Single Monolithic Book:* Interleave theoretical sections with exercise sets at the end of each chapter. Rejected due to bulkiness, poor physical/digital ergonomics during coding sessions, and fragmented reference usability.
- *Independent Unlinked Projects:* Separate theory and exercises without explicit mutual references. Rejected because learners lose guidance on which exercises to attempt after specific conceptual topics.

## Consequences
- **Positive:** Maximum ergonomics for readers sitting at the REPL.
- **Positive:** Modular compilation and distinct formatting tailored to reading vs problem-solving.
- **Negative:** Requires rigorous synchronization of cross-volume chapter/exercise mappings whenever exercises are added, removed, or renumbered.
