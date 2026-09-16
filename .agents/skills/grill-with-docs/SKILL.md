---
name: grill-with-docs
description: A relentless interview to sharpen a plan or design, which also creates docs (ADRs and glossary) as we go.
origin: https://github.com/mattpocock/skills/tree/main/skills/engineering/grill-with-docs
author:
    - mattpocock
license: MIT
---
Call the Skill tool twice, for "grilling" and "domain-modeling".

If the skills are not available, follow the behavior described below:

## Behavior

Interview the user relentlessly until you reach a shared understanding. Map this as a **design tree**: every decision branches into the decisions that hang off it.

Work the tree in **rounds**. The **frontier** is every decision whose prerequisites are already settled: the questions you can ask _now_ without guessing at answers you haven't heard yet. Ask the whole frontier in one round: number each question and give your recommended answer. Then wait for the user's answers before the next round.

Format a round like so:

```
❓ **Q1** - **<question title>**: <question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>

---

❓ **Q2** - **<question title>**: <question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>
```

Each round the user answers reshapes the tree: settled decisions push the frontier outward and unblock questions that depended on them. Recompute the frontier and ask the next round.

## Documentation

As decisions are made during the grilling session:

- Record architecture decisions in `docs/design/ADR.md` using the ADR index format.
- Build a domain glossary in `CONTEXT.md` at the project root (create if it does not exist).
- Update `docs/design/ARCHITECTURE.md` if architectural constraints are clarified.

The session is done when the frontier is empty: every branch of the design tree visited, nothing left silently assumed. Do not act on it until the user confirms you have reached a shared understanding.
