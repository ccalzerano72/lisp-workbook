# AI Knowledge Base Specification

**Version:** 1.0

## 1. Purpose

This specification defines a standard architecture and operating protocol for AI-oriented project knowledge bases.

An AI-KB is a compact, structured, incrementally loadable knowledge layer that enables AI agents to work effectively on a project across multiple sessions.

The AI-KB is **not a copy of the project** and must not attempt to document everything.

Its purpose is to maximize:

- relevant context;
- reliability;
- traceability;
- maintainability;

while minimizing:

- context size;
- redundant information;
- unnecessary file loading;
- obsolete knowledge.

---

# 2. Core Principles

Every AI-KB MUST follow these principles:

1. **Minimality** — store only knowledge useful for future AI work.
2. **Non-duplication** — do not reproduce information already obvious from project files.
3. **Modularity** — separate independent knowledge into focused documents.
4. **Lazy loading** — load only knowledge relevant to the current task.
5. **Progressive disclosure** — start with minimal context and expand when necessary.
6. **Traceability** — distinguish facts, inferences and unknowns.
7. **Freshness** — keep the KB synchronized with significant project changes.
8. **Human readability** — use Markdown as the primary content format.
9. **Machine routability** — metadata must support efficient document selection.
10. **Source precedence** — current project reality takes precedence over stale KB information.

---

# 3. Standard Location

The project AI-KB MUST be located at:

```text
.ai-docs/
```

Minimum structure:

```text
.ai-docs/
├── index.md
├── system-rules.md
└── state.md
```

Additional directories MUST be created only when justified by the project.

Possible directories include:

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

Do not create empty, redundant or irrelevant directories.

The target is the **minimum sufficient architecture**.

---

# 4. Mandatory Documents

## 4.1 index.md

`index.md` is the **master routing layer**.

It MUST remain compact and SHOULD stay below 500 tokens.

It MUST contain:

- project identity;
- project type;
- primary objective;
- concise current status;
- complete map of active AI-KB documents.

Each document entry SHOULD include:

- ID;
- path;
- one-line description;
- relevant task/domain.

`index.md` MUST NOT contain detailed project knowledge.

Its purpose is:

> determine which knowledge documents should be loaded for a task.

---

## 4.2 state.md

`state.md` represents the current project state.

It SHOULD contain:

```text
Implemented
In progress
Planned
Blocked
Known issues
Recent structural changes
```

Keep it concise.

State information is inherently volatile and MUST NOT be assumed to be authoritative when the actual project can be checked.

---

## 4.3 system-rules.md

`system-rules.md` defines how future AI agents interact with the AI-KB.

It MUST cover:

- startup;
- task routing;
- lazy loading;
- progressive context expansion;
- source precedence;
- conflict resolution;
- maintenance.

---

# 5. Document Metadata

Every AI-KB Markdown document SHOULD use YAML frontmatter.

Minimum fields:

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

Optional fields:

```yaml
volatility:
confidence:
source:
depends_on:
related:
triggers:
```

---

# 6. Metadata Definitions

## 6.1 id

A stable unique logical identifier.

Format:

```text
lowercase-kebab-case
```

Example:

```yaml
id: architecture-overview
```

IDs MUST be unique within the AI-KB.

IDs SHOULD remain stable even if the physical file is moved.

---

## 6.2 type

Defines the semantic role of a document.

Standard values:

```text
architecture
module
standard
decision
state
domain
workflow
api
data
research
literature
experiment
requirement
task
glossary
reference
index
other
```

Projects MAY introduce additional domain-specific types when necessary.

---

## 6.3 scope

Defines the semantic scope.

Allowed values:

```text
global
subsystem
module
task
```

---

## 6.4 status

Allowed values:

```text
active
draft
deprecated
archived
```

Only `active` documents SHOULD normally be selected for new tasks.

---

## 6.5 priority

Defines loading priority for task routing.

Allowed values:

```text
critical
high
medium
low
```

Priority indicates expected usefulness during task execution, not overall project importance.

---

## 6.6 updated

Date of the latest substantive update.

Format:

```text
YYYY-MM-DD
```

---

## 6.7 volatility

Indicates how quickly the information may become obsolete.

Allowed values:

```text
low
medium
high
```

Examples:

```text
Architecture principles → low
API specification       → medium
Current project state   → high
```

---

## 6.8 confidence

Indicates the reliability of the documented information.

Allowed values:

```text
high
medium
low
```

Confidence refers to the strength of the underlying evidence, not to the AI's subjective confidence.

---

## 6.9 source

Identifies the origin of the information.

Allowed values:

```text
repository
user
documentation
conversation
external
inference
```

Multiple values are allowed.

---

## 6.10 depends_on

Lists documents that are semantically required to understand the current document.

Example:

```yaml
depends_on:
  - architecture-overview
  - data-model
```

Dependencies MUST reference document IDs, not paths.

---

## 6.11 related

Lists documents that may be useful but are not required.

Example:

```yaml
related:
  - authentication-decision
  - security-standard
```

---

## 6.12 triggers

Lists keywords or concepts associated with the document.

Example:

```yaml
triggers:
  - authentication
  - login
  - JWT
  - OAuth
  - session
```

Triggers SHOULD improve task routing.

---

# 7. Knowledge Classification

Information SHOULD be classified as:

### FACT

Directly supported by:

- current project files;
- explicit user instructions;
- reliable project documentation.

### INFERENCE

Reasonably derived from available evidence but not explicitly documented.

### UNKNOWN

Information that cannot currently be established.

AI agents MUST NOT silently convert an inference into a fact.

Unknown information MUST NOT be fabricated.

---

# 8. Source-of-Truth Hierarchy

When sources conflict, use this precedence:

```text
1. Current explicit user instruction
2. Actual current project/workspace state
3. Primary project documentation
4. AI-KB
5. AI inference
```

The AI-KB is therefore a **knowledge-routing layer**, not an unquestionable source of truth.

If an AI-KB document conflicts with the actual project:

1. trust the current project;
2. identify the discrepancy;
3. update the AI-KB when appropriate.

---

# 9. Lazy-Loading Protocol

At the beginning of a new session:

```text
LOAD .ai-docs/index.md
```

Do NOT automatically scan the entire workspace or the entire AI-KB.

For every task:

### Step 1 — Classify the task

Identify:

- domain;
- relevant components;
- required knowledge;
- likely dependencies.

### Step 2 — Route documents

Use:

- type;
- scope;
- priority;
- triggers;
- dependencies;
- current state.

Classify candidate documents as:

```text
REQUIRED
CANDIDATE
IRRELEVANT
```

### Step 3 — Initial loading

Load the smallest useful context first.

Normally begin with approximately 2–3 high-value documents.

This is a heuristic, NOT a hard limit.

### Step 4 — Progressive expansion

If context is insufficient:

```text
discover dependency
        ↓
select document
        ↓
load document
        ↓
continue analysis
```

Stop loading when sufficient context has been obtained.

---

# 10. Context Isolation

Documents unrelated to the current task SHOULD remain unloaded.

The existence of a document in `.ai-docs/` does not justify loading it.

Large documents SHOULD be split when their contents contain independently useful knowledge.

---

# 11. Maintenance

Update the AI-KB when changes affect:

- architecture;
- components;
- APIs;
- workflows;
- conventions;
- dependencies;
- project state;
- significant design decisions;
- objectives.

Routine local changes SHOULD NOT automatically trigger KB updates.

When updating:

1. update the affected document;
2. update its `updated` field;
3. update `state.md` when appropriate;
4. update `index.md` if routing or structure changed.

Obsolete documents SHOULD be updated, replaced or archived.

Dead documentation MUST NOT accumulate.

---

# 12. Decision Records

Significant architectural or design decisions SHOULD be stored under:

```text
.ai-docs/decisions/
```

Recommended naming:

```text
ADR-NNN.md
```

Each decision SHOULD contain:

```text
Decision
Status
Context
Rationale
Alternatives
Consequences
```

Never invent historical rationale.

If the rationale is unknown:

```text
Rationale: UNKNOWN
```

---

# 13. Document Design

AI-KB documents SHOULD be:

- concise;
- focused;
- modular;
- independently understandable;
- low in redundancy;
- easy to route;
- easy to update.

Prefer:

```text
authentication.md
database.md
deployment.md
```

over:

```text
everything.md
```

---

# 14. Project-Specific Extensions

Projects MAY extend this specification with:

- additional document types;
- additional metadata;
- additional directories;
- domain-specific routing rules.

Extensions MUST NOT contradict the core principles of this specification.

---

# 15. Versioning

This specification uses:

```text
MAJOR.MINOR
```

Breaking changes increment MAJOR.

Backward-compatible additions increment MINOR.

The specification version SHOULD be recorded in project onboarding metadata.

---

# 16. Primary Objective

The objective of an AI-KB is NOT to maximize documentation.

The objective is:

> **maximize relevant, reliable and current context while minimizing the amount of information an AI agent must load to complete the current task.**