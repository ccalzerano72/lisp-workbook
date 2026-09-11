---
id: adr-001-functional-first-progression
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
  - editorial-and-typography
  - volume-structure
triggers:
  - decision
  - adr
  - functional
  - pedagogy
---

# ADR-001: Functional-First Pedagogical Progression

## Decision
Teach Common Lisp by enforcing a strictly functional programming style in initial chapters (Cap. 1–4: recursion, accumulators, higher-order functions, closures), delaying stateful mutation and imperative constructs (`setf`, arrays, hash tables, loops) until they become technically necessary in Cap. 5+.

## Status
Active

## Context
The target readership consists of university students fluent in imperative languages (C, Java, Python). When students with this background encounter Lisp, they instinctively attempt to reproduce familiar loops and mutable variables (`for`, `x = x + 1`), reducing Lisp to "C with parentheses" and bypassing the core paradigm shift.

## Rationale
Enforcing functional purity early breaks imperative habits and forces the acquisition of recursive and expression-based mental models. Once functional idioms are internalized, Common Lisp's multi-paradigm capabilities (`setf`, `loop`, OOP) can be introduced as deliberate engineering choices rather than default fallback habits.

## Alternatives
- *Immediate Multi-Paradigm Introduction:* Introduce `setf`, `loop`, and mutable structures alongside functions in early chapters. Rejected because imperative habits dominate and inhibit functional thinking.
- *Strict Pure Functional Framing (Haskell-style):* Present mutation as an error or antipattern. Rejected because Common Lisp is inherently multi-paradigm and professional Lisp code leverages mutation where appropriate.

## Consequences
- **Positive:** Students develop authentic fluency in recursive problem decomposition and higher-order abstractions.
- **Positive:** Clear progression from purity to pragmatic engineering.
- **Negative:** Early chapters require strict avoidance of `setf` in solutions even when an imperative solution might be shorter.
