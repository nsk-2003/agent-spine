---
name: code-review
description: Review the changes since a fixed point (commit, branch, tag, or merge-base) along two axes -> Standards and Spec compliance.
origin: https://github.com/mattpocock/skills/tree/main/skills/engineering/code-review
author:
    - mattpocock
license: MIT
---
Two-axis review of the diff between `HEAD` and a fixed point the user supplies:

- **Standards**: does the code conform to this repo's documented coding standards?
- **Spec**: does the code faithfully implement the originating issue / spec?

## Process

### 1. Pin the fixed point

Whatever the user said is the fixed point (a commit SHA, branch name, tag, `main`, `HEAD~5`, etc.). If they didn't specify one, ask for it.

Capture the diff command once: `git diff <fixed-point>...HEAD` (three-dot, so the comparison is against the merge-base).

### 2. Identify the spec source

Look for the originating spec:

1. A spec file under `docs/specifications/` matching the branch name or feature.
2. A path the user passed as an argument.
3. If nothing is found, ask the user where the spec is.

### 3. Identify the standards sources

Check `docs/design/ARCHITECTURE.md`, `docs/design/ADR.md`, and `.agents/workingrules.md` for documented standards.

Apply the **smell baseline** (Fowler code smells) on top of documented standards:

- **Duplicated Code**, **Feature Envy**, **Data Clumps**, **Primitive Obsession**
- **Shotgun Surgery**, **Divergent Change**, **Speculative Generality**
- **Mysterious Name**, **Message Chains**, **Middle Man**

### 4. Review

Present findings under `## Standards` and `## Spec` headings. Do not merge or rerank findings between axes.

End with a one-line summary: total findings per axis, and the worst issue within each axis.
