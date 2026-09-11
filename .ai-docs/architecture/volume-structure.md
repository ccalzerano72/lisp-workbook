---
id: volume-structure
type: architecture
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
  - state
  - editorial-and-typography
  - adr-002-two-volume-decoupling
triggers:
  - architecture
  - volumes
  - chapters
  - exercises
  - structure
---

# Architecture: Two-Volume Book Structure

The project is architected as two tightly coupled, complementary volumes. They must never be treated as independent projects.

```
BOOK/
├── manuale/   ← Common Lisp — Workbook (practice & exercises)
└── teoria/    ← Common Lisp — Fondamenti (narrative theory & concepts)
```

## 1. Theory Volume (`teoria/`)
- **Title:** *Common Lisp: Fondamenti — Dal modello mentale alla programmazione professionale*
- **Role:** Narrative guide focused on "how to think in Lisp" and "why" constructs work the way they do.
- **Root File:** `teoria/main.tex` (inputs `preamble.tex` and `parts/*.tex`).
- **Chapter Breakdown:**
  - **Part I: Le basi del linguaggio**
    - Cap. 1: `01_modello_mentale.tex` (S-expressions, evaluation, symbols, REPL)
    - Cap. 2: `02_funzioni_dati.tex` (Functions, predicates, numbers, characters, equality)
    - Cap. 3: `03_liste_ricorsione.tex` (Cons cells, lists, recursive thinking, accumulator pattern)
    - Cap. 4: `04_higher_order.tex` (Higher-order functions, mapcar/remove-if, lambdas, closures)
    - Cap. 5: `05_strutture_dati.tex` (Alist, plist, hash tables, arrays, vectors, defstruct/CLOS)
    - Cap. 6: `06_macro.tex` (Evaluation vs expansion, backquote/unquote, defmacro, macro hygiene)
  - **Part II: Algoritmi e dati dall'esterno**
    - Cap. 7: `07_backtracking.tex` (Search trees, pruning, N-Queens, graph traversal)
    - Cap. 8: `08_stringhe_io.tex` (Streams, format, pathnames, parsing, CSV/S-expr files)
  - **Part III: Stile e professione**
    - Cap. 9: `09_stile.tex` (Idiomatic code, packages, ASDF, error handling, performance basics)
  - **Appendices**
    - `appendice_stack.tex` (Call stack & recursion mechanics)
    - `appendice_adt.tex` (Abstract Data Types)

## 2. Practical Volume (`manuale/`)
- **Title:** *Common Lisp — Workbook con 148 esercizi graduali*
- **Role:** Self-contained hands-on workbook. Provides immediate practice without lengthy exposition.
- **Root File:** `manuale/main.tex` (inputs `preamble.tex` and `parts/*.tex`).
- **Component Breakdown:**
  - `00a_introduzione.tex`: Purpose, target, study pathways.
  - `00_cheatsheet.tex`: 2-page compact quick-lookup tables.
  - `00b_ambiente.tex`: Allegro CL setup, REPL commands, debugger, trace.
  - `01_reference.tex`: Quick reference by domain with short examples.
  - `02_esercizi.tex`: 148 exercises divided into 10 numbered sections.
  - `03_suggerimenti.tex`: ~60 hints for exercises rated ★★★ or higher.
  - `04_soluzioni.tex`: Complete commented solutions for all 148 exercises.

## 3. Chapter-to-Exercise Alignment

| Teoria Chapter | Topic | Workbook Exercise Range | Essential Exercises (◆) |
|---|---|---|---|
| Cap. 1 | Modello mentale | Es. 1–11 | 1, 6 |
| Cap. 2 | Funzioni e dati | Es. 1–21 (espande a 12–21) | 4, 8, 12, 16 |
| Cap. 3 | Liste e ricorsione | Es. 22–68 | 22, 26, 32, 41, 50, 60 |
| Cap. 4 | Higher-order e closure | Es. 69–92 | 69, 74, 80, 85 |
| Cap. 5 | Strutture dati | Es. 93–120 | 93, 101, 108, 114 |
| Cap. 6 | Macro | Es. 121–123 | 121 |
| Cap. 7 | Backtracking e algoritmi | Es. 124–133 | 124, 128 |
| Cap. 8 | Stringhe, I/O e parsing | Es. 134–144 | 134, 138, 141 |
| Cap. 9 | Stile e professione | Es. 145–148 (Progetti) | 145 |

## 4. Build Toolchain
- Standard LaTeX engine: `pdflatex` (two passes required for hyperref and table of contents stability).
- Key packages: `tcolorbox`, `listings`, `hyperref`, `booktabs`, `needspace`.
