---
domain: "Name of the Architectural Domain (e.g., Frontend Reactive State Management)"
status: "Active"
created: YYYY-MM-DD
last_updated: YYYY-MM-DD
---

# Domain Rulebook: [Domain Name]

> **[SYSTEM DIRECTIVE FOR LLM AGENTS]**
> This document is the Single Source of Truth (SSOT) for the architecture and implementation of this domain.
> 1. You MUST strictly obey all constraints listed here.
> 2. You MUST NOT use any patterns, libraries, or architectures listed in Section 3.
> 3. You MUST apply Test-Driven Development (TDD) as defined in Section 4.
> 4. **MUTABILITY COMMAND:** If you discover a specific approach is not viable (API, library/framework, pattern, etc.), or if the user explicitly instructs you to exclude one, you MUST immediately update Section 3 (Excluded Options) and Section 6 (Audit Log) to reflect this discovery.

## 1. Domain Context & Goals
<!-- Briefly describe the functional goal of this domain. -->
* **Goal:** [e.g., Establish a reliable, reactive UI layer that integrates seamlessly with the backend.]
* **Scope:** [e.g., All web-based frontend components and their state synchronization.]

## 2. Hard Constraints & Boundaries
<!-- Explicit, unyielding rules. The LLM is forbidden from bypassing these. -->
* **Architecture Boundary:** [e.g., The application must operate as a single-process executable. Do not introduce complex Inter-Process Communication (IPC) layers between the backend and frontend.]
* **Dependency Rules:** [e.g., Only actively maintained, open-source dependencies are permitted. Do not introduce abandoned or deprecated packages.]
* **Communication Paradigm:** [e.g., UI interactions must strictly utilize dynamic/reactive communication models (e.g., signals, slots, events, bindings). Polling is forbidden.]

## 3. Excluded Options & Anti-Patterns
<!-- Negative constraints. Agents must actively append to this list when a path fails. -->
* **[e.g., Eel Framework]:** Excluded. Reason: Deprecated and abandoned. Do not attempt to use as a fallback for frontend/backend integration.
* **[e.g., Multi-Process Daemons]:** Excluded. Reason: Violates the strict single-process boundary constraint.
* **[e.g., Vanilla DOM Manipulation]:** Excluded. Reason: Violates the reactive state management paradigm required for this production tool.

## 4. Verification & Automation (Forced TDD)
<!-- How the agent mathematically or procedurally proves the work is complete. -->
* **Mandatory TDD Workflow:** You must write failing automated tests *before* writing the implementation code for any task in this domain.
* **Test Tooling:** [e.g., All UI interaction flows must be verified via Playwright live interaction tests. Backend utilities must be verified via pytest.]
* **Definition of Done:** The implementation is only complete when the test runner passes without warnings, and the architecture strictly adheres to Section 2.

## 5. Current Architecture & Implementation Directives
<!-- The accepted, active path the agent should follow. -->
* **Core Stack:** [e.g., Python backend, modern reactive web UI framework, TypeScript].
* **Implementation Standard:** [e.g., Use standard reactive hooks for state. Ensure all state mutations trigger automated DOM updates without manual network fetch requests.]

## 6. Evolution & Audit Log
<!-- Append-only changelog. Agents must add an entry here whenever they update constraints or anti-patterns. Format: `- **[YYYY-MM-DD] [Topic]:** [Brief reason for the change]` -->
* **[YYYY-MM-DD] Initialized:** Domain rulebook created.
* **[YYYY-MM-DD] Constraint Added:** [e.g., Blocked Library X because it was discovered to implicitly spawn background worker processes, violating the single-process rule.]
