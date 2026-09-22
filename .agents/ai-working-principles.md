# AI Working Principles

> The operating theory behind "The Main Flow." Every skill and rule in this template is downstream of the constraints below. Read this before the working rules.

These principles come from the way LLM coding agents actually behave, not from any one tool. They apply whatever harness, model, or language you use.

## The two constraints every session works around

### 1. The smart zone and the dumb zone

An LLM does its best work when its context is small and fresh. As you add tokens, attention relationships grow quadratically and quality degrades — the model starts making careless decisions, hallucinating, and forgetting earlier instructions. Empirically this begins around **~100k tokens**, regardless of whether the advertised context window is 200k or 1M. A bigger window mostly buys you more *dumb zone*; it is good for retrieval, not for coding.

**Implications:**
- Size every task to be completable inside ~100k tokens — the "smart zone."
- Break large work into slices that each fit one smart-zone session (see `to-tickets`, and `wayfinder` for work too big to plan in one session).
- Keep the system prompt / always-on context as small as possible. A bloated always-on context pushes you into the dumb zone before any work starts. Prefer **pull** over **push** (below).
- Delegate exploration to **sub-agents**. A sub-agent has its own isolated context window; it can burn 90k tokens exploring and report back a small summary, leaving the parent agent in the smart zone.

### 2. The agent is like the man from Memento

Every session resets to the same starting state. The agent does not remember previous sessions. Design for this rather than fighting it.

- **Prefer `clear` over `compact`.** Clearing returns you to a clean, predictable starting state. Compacting produces a lossy, sediment-filled history that quietly degrades quality over many cycles. Compact only when you must retain rich in-session state you cannot easily reconstruct; otherwise finish the unit of work, then clear.
- Because state resets, the durable knowledge must live in the repo — `CONTEXT.md` (the glossary), ADRs, and the code itself — not in a long-running conversation.

## Human-in-the-loop vs. AFK work

Classify every task as one of two kinds:

- **Human-in-the-loop** — alignment work that needs your judgement and taste: grilling, writing/approving the spec, breaking work into tickets, and validating the finished result. These cannot be automated away without producing slop.
- **AFK (away-from-keyboard)** — execution work an agent can run unattended: implementing a well-specified ticket. The whole point of the planning phases is to queue up enough well-formed AFK work that implementation can run without you ("day shift plans, night shift builds").

## Feedback loops are the ceiling

The quality of your feedback loops sets the maximum quality an agent can reach in your codebase. Without fast, trustworthy feedback (tests, type-checks, a runnable app), the agent is coding blind and no amount of prompting will save it. If agent output is bad, improve the feedback loops first. This is why writing tests first and a testable architecture are load-bearing, not optional.

## Push vs. pull

Two ways to get information to an agent:

- **Push** — always-on context (e.g. the always-loaded portion of `AGENTS.md`). Costs smart-zone tokens on every session. Reserve for what is *always* needed.
- **Pull** — information the agent fetches only when relevant (skills, ADRs, `CONTEXT.md`, spec files). Costs nothing until needed.

Default to pull. One deliberate exception: when running an **automated reviewer**, *push* the coding standards into its context so it always checks against them — the reviewer must not have to remember to go look.

## Roles and models

- Review code in a **fresh-context sub-agent**, never in the same context that wrote it. An agent that just wrote code is a poor judge of it (it is in the dumb zone and attached to its own work); a clean context reviews in the smart zone.
- Use a **fast, capable model to implement** and a **stronger model to review** — reviewing well needs more reasoning than producing a first draft.

## Deep modules, shallow modules, and the gray box

(Full guidance in `docs/design/ARCHITECTURE.md`; summarized here because it shapes how you plan.)

- **Deep module:** a simple, thin interface hiding substantial functionality. Easy for an agent to navigate and to test at its boundary.
- **Shallow module:** many small, undifferentiated files with tangled dependencies. Hard to navigate, unclear where to draw test boundaries. Left unsupervised, agents *default* to producing shallow modules — steer deliberately toward deep ones.
- **Gray box:** design the *interface* of a module yourself, then delegate the *implementation* to the agent. You keep a map of the system's shapes and behaviours without having to read every line — this is how you retain a sense of the codebase while moving fast.

## Documents rot — keep the durable set small

Stale documents actively mislead agents: an agent that finds an out-of-date spec will trust it over the code. Keep the *durable* documentation set minimal and true:

- **Durable:** `CONTEXT.md` (glossary), ADRs (hard-to-reverse decisions), `ARCHITECTURE.md`, `sourcemap.md`, `packagedesign.md`.
- **Sprint-scoped, then closed:** specs, tickets, and Wayfinder maps. Mark them done when the code lands; treat **the code as the source of truth** and distrust any spec that disagrees with it. See the spec-lifecycle ADR.
