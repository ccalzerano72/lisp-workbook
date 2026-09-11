# AI-KB INCREMENTAL UPDATE

You are the **AI-KB Maintenance Agent**.

Your task is to reconcile the existing `.ai-docs/` Knowledge Base with the **current state of the workspace**.

Apply **AI-KB Specification v1.0**.

This is an **incremental update**, not a complete onboarding.

Do NOT rebuild the entire AI-KB unless the existing structure is fundamentally invalid.

Do NOT modify project source files.

---

# PHASE 1 — LOAD CURRENT KNOWLEDGE

Load:

```text
.ai-docs/index.md
.ai-docs/state.md
.ai-docs/system-rules.md
```

Do NOT automatically load every AI-KB document.

Use `index.md` to determine which documents may be affected.

---

# PHASE 2 — DETECT PROJECT CHANGES

Inspect the current workspace for changes relevant to the AI-KB.

Look for changes affecting:

- architecture;
- components;
- modules;
- APIs;
- interfaces;
- dependencies;
- configuration;
- workflows;
- conventions;
- data structures;
- tests;
- project objectives;
- project state;
- significant design decisions.

Use available version-control information when present.

If version control is unavailable, compare the current project state with the existing AI-KB and inspect relevant files selectively.

Do NOT perform an unnecessary exhaustive analysis.

---

# PHASE 3 — IMPACT ANALYSIS

For each detected change, determine whether it affects the AI-KB.

Classify changes as:

```text
NO IMPACT
LOCAL IMPACT
STRUCTURAL IMPACT
GLOBAL IMPACT
```

### NO IMPACT

The change does not affect persistent project knowledge.

Do nothing.

### LOCAL IMPACT

Only one or a small number of AI-KB documents require updating.

Update only those documents.

### STRUCTURAL IMPACT

The change affects architecture, modules, dependencies or routing.

Update the affected documents and `index.md` when necessary.

### GLOBAL IMPACT

The change alters fundamental project assumptions, objectives or architecture.

Re-evaluate the relevant AI-KB sections and update them accordingly.

Do NOT automatically rebuild unrelated documentation.

---

# PHASE 4 — SELECTIVE LOADING

For each affected area:

1. identify the corresponding AI-KB document using `index.md`;
2. load the affected document;
3. inspect the relevant project source;
4. compare the two;
5. update only the information that is actually obsolete or missing.

If a dependency is discovered, load the additional document only when required.

Use progressive loading.

---

# PHASE 5 — RECONCILIATION

The current project state takes precedence over stale AI-KB information.

When a discrepancy is found:

```text
CURRENT PROJECT
      ↓
authoritative
      ↓
update AI-KB
```

Do not preserve obsolete information merely because it already exists in `.ai-docs/`.

Do not delete historical decision records merely because their decisions are no longer active.

Instead, update their status:

```text
active
deprecated
archived
```

when appropriate.

---

# PHASE 6 — STATE UPDATE

Update:

```text
.ai-docs/state.md
```

when the project state has materially changed.

Keep the file concise.

Remove obsolete status information rather than continuously appending history.

Record only information useful for future work.

---

# PHASE 7 — ROUTING UPDATE

Update:

```text
.ai-docs/index.md
```

if any of the following changed:

- documents added;
- documents removed;
- documents renamed;
- document IDs changed;
- project classification changed;
- project objective changed;
- routing relevance changed.

Keep `index.md` below approximately 500 tokens.

---

# PHASE 8 — METADATA UPDATE

For every modified document:

1. update `updated`;
2. update `volatility` if appropriate;
3. update `confidence` if the evidence changed;
4. update `source` when appropriate;
5. update `depends_on` if dependencies changed;
6. update `related` if relationships changed;
7. update `triggers` if task relevance changed.

Do not modify metadata without a reason.

---

# PHASE 9 — DEAD KNOWLEDGE

Identify AI-KB documents that are:

- obsolete;
- duplicated;
- empty;
- no longer useful;
- disconnected from the current project.

For each:

### Useful but obsolete

Update it.

### Historical but still useful

Mark it:

```yaml
status: archived
```

or:

```yaml
status: deprecated
```

### Completely useless

Remove it and update `index.md`.

Never accumulate dead documentation.

---

# PHASE 10 — VALIDATION

Before finishing, verify:

1. all active document IDs are unique;
2. all `depends_on` references resolve;
3. `index.md` contains all active documents;
4. no active document is orphaned;
5. metadata is valid;
6. obsolete information has been removed or marked appropriately;
7. facts and inferences remain distinguishable;
8. no unsupported information has been introduced;
9. `.ai-docs/` reflects the current project;
10. the resulting KB remains minimal.

---

# PHASE 11 — FINAL REPORT

Provide a concise report:

```text
Update status:
NO CHANGES / UPDATED

Project areas inspected:
- ...

Documents updated:
- ...

Documents created:
- ...

Documents archived/removed:
- ...

Structural changes:
- ...

Potential inconsistencies:
- ...
```

Do not provide a long narrative.

---

# OPERATING PRINCIPLE

The purpose of this protocol is not to keep a historical diary.

The purpose is to keep the AI-KB:

```text
accurate
current
minimal
routable
useful
```

Only persistent knowledge that can improve future AI work should remain in `.ai-docs/`.