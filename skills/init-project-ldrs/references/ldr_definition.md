# The Living Domain Rulebook: An LLM-Optimized ADR Framework

## 1. Purpose and Definition
The **Living Domain Rulebook** is an evolution of the traditional Architecture Decision Record (ADR), explicitly re-engineered to serve as an infallible Single Source of Truth (SSOT) for agentic Large Language Models (LLMs).

Standard ADRs fail in agentic workflows because they are immutable, chronologically fragmented, and designed for human archeology. This causes context window bloat, retrieval errors, and hallucinated implementations.

A Living Domain Rulebook solves this by representing the **absolute present truth** of a specific architectural domain. It contains strict boundaries, explicitly forbidden anti-patterns, and forced verification steps.

## 2. Core Principles
* **Living, Not Static:** Rulebooks are updated in place. We rely on Git for historical versioning. The agent only ever reads the current, active `main` branch version, guaranteeing zero ambiguity.
* **Domain-Driven, Not Point-In-Time:** Instead of writing an ADR for "Decision to use Library X," rulebooks are written for the governing domain (e.g., "Frontend Reactive State Management").
* **Explicit Negative Constraints:** LLMs suffer from "helpful fallback" behavior, often reverting to standard industry patterns when blocked. Rulebooks utilize strict "Excluded Options & Anti-Patterns" sections to hard-code dead ends and forbid hallucinated workarounds.
* **Procedural Proof (Forced TDD):** An LLM cannot be trusted to self-certify its architecture. Rulebooks mandate automated verification (TDD) as the only accepted Definition of Done.

---

## 3. The Anatomy of a Rulebook
Every Living Domain Rulebook strictly adheres to the following structural requirements:

1. **YAML Frontmatter:** Machine-parseable metadata (`domain`, `status`, `created`, `last_updated`).
2. **System Directives:** A hardcoded blockquote commanding the LLM to obey the document.
3. **Hard Constraints & Boundaries:** The non-negotiable architectural walls (e.g., "Must be single-process," "No IPC allowed").
4. **Excluded Options & Anti-Patterns:** A growing list of rejected tools, libraries, or paradigms, accompanied by the reason for rejection.
5. **Verification & Automation:** The specific testing tools and TDD workflow required to prove compliance.
6. **Current Directives:** The accepted technological stack and implementation standard.
7. **Evolution & Audit Log:** An append-only chronological list tracking *why* the rules changed over time.

---

## 4. Agent Operating Procedures (How to Work With Rulebooks)
When an LLM agent interacts with a repository governed by Living Domain Rulebooks, it **MUST** adhere to the following strict operational protocol:

### Phase 1: Context Acquisition
Before writing any code or proposing any architecture, the agent must identify the relevant domain for the task and read the corresponding Living Domain Rulebook.
* **Rule:** An agent MUST NOT span logic across domains if it violates the boundaries defined in the respective rulebooks.

### Phase 2: Strict Implementation
The agent must treat the "Hard Constraints" and "Current Directives" as absolute laws.
* **Rule:** If the agent encounters a roadblock, it MUST NOT fall back to any pattern or library listed in the "Excluded Options & Anti-Patterns" section.

### Phase 3: Active Mutation (The Feedback Loop)
Because these are *Living* documents, the agent is an active maintainer of the rulebook.
* **Rule:** If the agent discovers through execution that a specific library, API, or architectural path is fundamentally incompatible with the Hard Constraints, it **MUST** immediately update the rulebook.
* **Action:** The agent will add the failed path to Section 3 (Excluded Options & Anti-Patterns) with a clear reason, and append a timestamped entry to Section 6 (Evolution & Audit Log).
* **Rule:** The agent must perform this mutation if explicitly instructed by the human user to avoid a specific technology or pattern.

### Phase 4: Verification
The agent's task is only complete when it has written the automated tests mandated by the rulebook, and those tests pass. Code that "looks correct" but lacks the procedural proof demanded by Section 4 is considered a failure.
