---
name: grill-with-docs
description: A relentless one-question-at-a-time interview to sharpen a plan or design, grounded in the repo's glossary and ADRs, which it reads at the start and updates as decisions are made.
license: MIT
metadata:
  origin: https://github.com/mattpocock/skills/tree/main/skills/engineering/grill-with-docs
  author: mattpocock
---
Call the Skill tool for "grilling" if available.

If the skill is not available, follow the behavior described below:

## Behavior

Interview the user relentlessly until you reach a shared understanding. Map this as a **design tree**: every decision branches into the decisions that hang off it, and you walk it resolving dependencies **one by one**.

**Ask exactly one question at a time**, using the `AskUserQuestion` tool. Do not batch multiple questions into a single call. Put your recommended answer first in the options list, labeled "(Recommended)". **Stop and wait** for the user's reply before asking the next. This is a back-and-forth conversation, not a questionnaire — each answer reshapes the tree and determines what to ask next.

Pick the next question from the **frontier**: the decisions whose prerequisites are already settled, so you never ask something that depends on an answer you haven't heard yet. Always resolve the question that most unblocks the rest.

After the user answers, incorporate it, recompute the frontier, and ask the next single question via `AskUserQuestion`. Keep going until every branch is visited.

## Documentation

`grill-with-docs` differs from a plain grilling interview in that it is **grounded in the repo's docs** and keeps them current.

**At the start:** read `CONTEXT.md` (the domain glossary) and any ADRs in the area you're touching. Use that shared vocabulary throughout. Surface tensions early — if the idea collides with an existing definition, raise it before going further.

**As decisions are made during the session:**

- Sharpen fuzzy language and record terms in the domain glossary in `CONTEXT.md` at the repo root (create it if it does not exist). Challenge new language against the existing glossary and cross-reference it with the code, so a term means one thing everywhere.
- Create an ADR (`docs/adrs/adr-<slug>.md`, plus an entry in the index at `docs/design/ADR.md`) **only** when a decision is **hard to reverse**, would be **surprising without context**, and reflects a **real trade-off**. Interchangeable choices you could swap later do not need an ADR.
- Update `docs/design/ARCHITECTURE.md` when architectural constraints or previously-`TODO` project details are clarified.

The session is done when the frontier is empty: every branch of the design tree visited, nothing left silently assumed. Do not act on it until the user confirms you have reached a shared understanding.
