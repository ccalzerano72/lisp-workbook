---
id: editorial-and-typography
type: standard
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
  - adr-001-functional-first-progression
triggers:
  - standards
  - editorial
  - typography
  - boxes
  - rules
  - latex
---

# Editorial & Typographical Standards

## 1. Pedagogical Foundation
- **Target Audience:** University computer science students with prior experience in imperative programming (C, Java, Python).
- **Core Editorial Stance:** *"Funzionale prima, tutto il resto dopo"* (Teach functional thinking first; then Common Lisp unlocks multi-paradigm powers).
- **Paradigm Progression:**
  - Cap. 1–4: Pure functional style (recursion, accumulators, higher-order functions, closures). `setf` is acknowledged but not used as a pattern.
  - Cap. 5: Mutability introduced out of concrete technical necessity (hash tables, mutable arrays).
  - Cap. 6+: Multi-paradigm style applied deliberately and pragmatically.
- **Tone:** Technical, rigorous, neither condescending nor assuming existing Lisp expertise. Emphasize *why* idioms exist, contrasting with imperative paradigms where helpful.

## 2. Typographic & Writing Rules
- **Conciseness:** Maximum 5 consecutive lines of prose without a visual break (listing, box, list, or separator).
- **Concrete Code:** Every construct must feature at least one practical example with commented REPL output.
- **Strict Prohibition of Narrative Em-Dashes (`---`):**
  - **NEVER** use `---` as an em-dash, parenthetical pause, or clause separator in prose (a common hallmark of unedited AI text).
  - Use commas, colons, or parentheses instead.
  - Title formats: `Nome: descrizione` (NOT `Nome --- descrizione`).
  - Table cells: `& --- &` is the **only** permitted use of triple hyphens (indicating null/empty values).
- **Listing Accents (LaTeX `listings`):**
  - Inside `\begin{lstlisting}`: use ASCII apostrophe forms (`e'`, `puo'`, `perche'`, `piu'`) to prevent font-encoding errors.
  - In normal LaTeX text: use standard Italian UTF-8 accented characters (`è`, `può`, `perché`, `più`).
  - Ensure `columns=fullflexible, keepspaces=true` remains set for copy-paste safety.
- **Unicode & Symbols:** Use LaTeX macros (`\unaStella`, `\dueStelle`, etc.) rather than raw Unicode symbols or emojis.

## 3. Box Environments & Visual Systems

### Teoria (`teoria/`)
| Environment | Color | Purpose |
|---|---|---|
| `concetto` | Blue | Central concept or language construct |
| `esempio` | Green | Code snippet with commented output |
| `attenzione` | Orange | Common traps, pitfalls, C/Java false friends |
| `intuizione` | Teal | Crucial mental shifts / conceptual leaps |
| `confronto` | Warm Brown | Direct comparison with imperative languages |
| `nota` | Gray italic | Secondary details or language standards context |
| `workbook` | Purple | Callouts to corresponding workbook exercises |

*Visual Hierarchy within boxes:* `\keyline{label}{text}`, `\detail{text}`, `\boxsep`. Outside boxes: `\argomento{...}`, `\seprule`.

### Workbook (`manuale/`)
| Box Environment | Badge | Border Color | Track / Meaning | Count |
|---|---|---|---|---|
| `essbox` | ◆ (`\minimo`) | Solid Blue | Minimo (core concepts) | 25 |
| `stdbox` | ■ (`\standard`) | Solid Green | Standard (deepening) | 54 |
| `colbox` | ○ (`\collateral`) | Dashed Gray | Collaterale (consolidation) | 69 |

*Difficulty Scale:* `\unaStella` (★) to `\cinqueStelle` (★★★★★).

## 4. Cross-Volume Synchronization Checklist
Before finalizing changes:
1. **Example Consistency:** If an example in the workbook is updated, check whether it appears in `teoria/`.
2. **Exercise Callouts:** When adding or moving an exercise, update all `workbook` boxes in `teoria/`.
3. **Numbering Integrity:** Maintain strict synchronization between `manuale/main.tex`, `02_esercizi.tex`, `03_suggerimenti.tex`, and `04_soluzioni.tex`.
4. **Path Totals:** Keep declared path counts (25 ◆, 54 ■, 69 ○ = 148 total) synchronized.
5. **Verified Outputs:** Ensure workbook problem prompts and `04_soluzioni.tex` outputs match verified Allegro CL / SBCL execution.
