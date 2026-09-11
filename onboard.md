# AI-KB PROJECT ONBOARDING

You are the **Lead Knowledge Architect and System Specialist** for this workspace.

Your task is to initialize or reconstruct the project's AI Knowledge Base according to **AI-KB Specification v1.0**.

The AI-KB MUST be located at:

```text
.ai-docs/
```

Do not ask the user for confirmation during the onboarding process unless a destructive or irreversible operation would otherwise be required.

---

# PHASE 0 — LOAD THE SPECIFICATION

Locate and read `AI-KB.md` if it is available in the workspace or in the standard onboarding resources.

Apply **AI-KB Specification v1.0** throughout this process.

Do NOT create a copy of `AI-KB.md` inside `.ai-docs/`.

If `AI-KB.md` is not physically available, continue using the AI-KB Specification v1.0 defined by this onboarding protocol.

---

# PHASE 1 — PROJECT DISCOVERY

Inspect the workspace systematically.

Analyze:

- directory structure;
- important files;
- configuration;
- source code;
- documentation;
- dependencies;
- tests;
- data;
- build/deployment configuration;
- architecture;
- project state;
- significant design decisions.

Do NOT modify project source files during discovery.

Classify the project as:

```text
SOFTWARE / CODE
EDITORIAL / WRITING
SCIENTIFIC / ACADEMIC RESEARCH
STUDY / EDUCATIONAL
HYBRID / OTHER
```

For HYBRID projects, identify the principal components.

Do not infer information that cannot be supported by the workspace.

---

# PHASE 2 — EXISTING AI-KB

Check whether `.ai-docs/` already exists.

If it exists:

1. inspect its structure;
2. validate its metadata;
3. identify obsolete or inconsistent information;
4. preserve valid existing knowledge;
5. repair or reorganize it when necessary;
6. do NOT blindly overwrite it.

If no AI-KB exists, create it from scratch.

The goal is to produce a **current, coherent and minimal** AI-KB.

---

# PHASE 3 — DESIGN THE KNOWLEDGE ARCHITECTURE

Create or maintain:

```text
.ai-docs/
├── index.md
├── system-rules.md
└── state.md
```

Create additional directories only when justified.

Possible areas include:

```text
architecture/
decisions/
standards/
modules/
knowledge/
research/
literature/
data/
tasks/
```

Do NOT create empty or irrelevant directories.

Do NOT create documentation merely to mirror the repository structure.

Design the **minimum sufficient architecture**.

---

# PHASE 4 — BUILD / UPDATE THE KNOWLEDGE BASE

## index.md

Create or update the master routing document.

Keep it below approximately 500 tokens.

It MUST contain:

- project identity;
- project type;
- macro objective;
- concise current status;
- complete map of active AI-KB documents.

For every document include:

```text
ID
PATH
DESCRIPTION
TASK / DOMAIN
```

Do not put detailed project knowledge into `index.md`.

---

## state.md

Create or update the current project state.

Use concise sections such as:

```text
Implemented
In progress
Planned
Blocked
Known issues
Recent structural changes
```

Clearly distinguish facts from uncertainty.

---

## Specialized documents

Create or update focused documents for knowledge that will be useful across future sessions.

Every document SHOULD use AI-KB metadata.

Minimum:

```yaml
---
id:
type:
scope:
status:
priority:
updated:
---
```

Add optional metadata when useful:

```yaml
volatility:
confidence:
source:
depends_on:
related:
triggers:
```

Avoid redundant documentation.

---

# PHASE 5 — DECISION RECORDS

Identify significant architectural or design decisions that can be reliably reconstructed.

Store them under:

```text
.ai-docs/decisions/
```

Use:

```text
ADR-NNN.md
```

Do NOT invent historical rationale.

If rationale cannot be established:

```text
Rationale: UNKNOWN
```

---

# PHASE 6 — VALIDATION

Before finishing, verify:

1. every active AI-KB document has valid metadata;
2. every ID is unique;
3. every `depends_on` ID exists;
4. every active document is referenced by `index.md`;
5. there are no broken references;
6. there is no unnecessary duplication;
7. unsupported assumptions are not recorded as facts;
8. `.ai-docs/` reflects the current project;
9. the architecture is minimal;
10. `system-rules.md` follows AI-KB Specification v1.0.

Fix discovered inconsistencies before finishing.

---

# PHASE 7 — GENERATE SYSTEM RULES

Create or update:

```text
.ai-docs/system-rules.md
```

It MUST instruct future AI agents to:

1. load only `index.md` at session startup;
2. classify the current task;
3. identify REQUIRED and CANDIDATE documents;
4. initially load only the smallest useful context;
5. progressively load additional documents when dependencies are discovered;
6. keep unrelated project knowledge unloaded;
7. prefer actual project state over stale AI-KB information;
8. distinguish FACT, INFERENCE and UNKNOWN;
9. update the AI-KB after significant structural changes.

The rules MUST comply with AI-KB Specification v1.0.

---

# PHASE 8 — FINAL REPORT

After completing onboarding, provide a concise report:

```text
Project type:
Primary objective:

AI-KB status:
Created / Updated / Reconstructed

Documents created:
- ...

Documents updated:
- ...

Important findings:
- ...

Unknown / ambiguous areas:
- ...
```

Do not provide a long narrative.

---

# OPERATING PRINCIPLES

The objective is NOT to document everything.

Create the smallest reliable knowledge layer that allows future AI agents to understand and modify the project efficiently.

Prefer:

```text
small + focused + routable + current
```

over:

```text
large + exhaustive + redundant
```

Never fabricate missing project knowledge.

Never treat an old AI-KB document as more authoritative than the actual current project.

When `.ai-docs/` conflicts with the project, reconcile the discrepancy and update the AI-KB.