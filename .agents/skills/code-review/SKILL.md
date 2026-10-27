---
name: code-review
description: Review the changes since a fixed point (commit, branch, tag, or merge-base) along two axes -> Standards and Spec compliance.
license: MIT
metadata:
  origin: https://github.com/mattpocock/skills/tree/main/skills/engineering/code-review
  author: mattpocock
---
Two-axis review of the diff between `HEAD` and a fixed point the user supplies:

- **Standards**: does the code conform to this repo's documented coding standards?
- **Spec**: does the code faithfully implement the originating issue / spec?

> **Fresh context is recommended** — the context that wrote the code is in the dumb zone and attached to its own work. Prefer a stronger model for review than was used to implement. **Push** the standards sources into the reviewer's context so it always checks against them rather than having to remember to look. See `.agents/ai-working-principles.md`.

## Process

### 0. Choose the review context

Before doing anything else, ask the user with the `AskUserQuestion` tool, as a single question, which context to run the review in. Put "Fresh context" first, labeled "(Recommended)":

1. **Fresh context**: run the review in a new agent or sub-agent with no prior conversation history.
2. **Current context**: run the review in the existing agent or sub-agent, continuing with the current conversation context.

**Stop and wait** for the answer, then run steps 1–4 as follows:

- **Fresh context**: spawn a new sub-agent and give it everything it needs, since it has no history: the fixed point (or ask the user for it first, per step 1), the spec source or intent, and the standards sources. Have it perform steps 2–4 and return the report.
- **Current context**: perform steps 1–4 yourself in this conversation, reusing what is already known (the fixed point, spec, and intent discussed so far) instead of re-asking.

If the user picks "Current context", do not push back or re-ask; the choice is theirs.

### 1. Pin the fixed point

Whatever the user said is the fixed point (a commit SHA, branch name, tag, `main`, `HEAD~5`, etc.). If they didn't specify one, ask for it.

Capture the diff command once: `git diff <fixed-point>...HEAD` (three-dot, so the comparison is against the merge-base).

### 2. Identify the spec source

Look for the originating spec:

1. A spec file under `docs/specifications/` matching the branch name or feature.
2. A path the user passed as an argument.
3. If nothing is found, ask the user where the spec is.

For **small work with no spec** (the `grill → implement → code-review` path), use the agreed grilling outcome / conversation as the intent for the Spec axis. If no intent source exists at all, say so and review the Standards axis only.

### 3. Identify the standards sources

Check `docs/design/ARCHITECTURE.md`, `docs/design/ADR.md`, and `.agents/workingrules.md` for documented standards.

Apply the **smell baseline** (Fowler code smells) on top of documented standards:

- **Duplicated Code**, **Feature Envy**, **Data Clumps**, **Primitive Obsession**
- **Shotgun Surgery**, **Divergent Change**, **Speculative Generality**
- **Mysterious Name**, **Message Chains**, **Middle Man**

### 4. Review

Present findings under `## Standards` and `## Spec` headings. Do not merge or rerank findings between axes.

End with a one-line summary: total findings per axis, and the worst issue within each axis.
