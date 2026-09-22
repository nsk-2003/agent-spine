# ADR: Spec Lifecycle and Doc-Rot Policy

**Date:** TODO: Set date when adopted
**Status:** Accepted

## Context

Specs, tickets, and planning maps are planning artifacts. As the code evolves, these documents drift from reality. A stale spec is worse than no spec: an agent that finds an out-of-date document will trust it over the code and take a wrong turn ("doc rot").

There is a real tension. One school (fully non-persistent specs) deletes the spec the moment the code lands, keeping only the code, `CONTEXT.md`, and ADRs as durable truth. That eliminates doc rot but discards the audit trail and the decision history that is valuable on long-running projects.

## Decision

Adopt a **hybrid** lifecycle. Keep the numbered spec-folder history under `docs/specifications/`, but treat those artifacts as sprint-scoped and status-tracked rather than as living documentation:

- Every spec carries a **Status**: `Draft` → `Active` → `Implemented` (or `Superseded`).
- When the code lands, the spec is marked `Implemented` and is **not** edited further. It is a historical record of where a sprint was headed, not a description of current behaviour.
- **The code is the source of truth.** Where a spec and the code disagree, the code wins; the spec is stale by definition once `Implemented`.
- The **durable** documentation set stays small and is kept true: `CONTEXT.md`, ADRs, `ARCHITECTURE.md`, `sourcemap.md`, `packagedesign.md`.
- **Sprint-scoped** artifacts — specs, tickets, and Wayfinder maps — are closed or deleted once their work has landed.

## Consequences

- The decision history is preserved (useful for long projects and onboarding) without inviting agents to trust stale specs as current.
- Agents must be instructed: read an `Implemented`/`Superseded` spec as history; verify against the code before acting. This instruction lives in `.agents/workingrules.md`.
- Someone must actually set the Status when work completes — this is part of the review / merge step, not optional.
- This is a hard-to-reverse convention (it shapes the folder structure and every skill that reads or writes specs), which is why it is recorded here rather than left implicit.
