# Architecture Decision Record (ADR) Index

This file is the index of Architecture Decision Records. Individual ADRs are stored as separate files in `docs/adrs/`.

## How ADRs Are Organized

- **Index:** This file (`docs/design/ADR.md`) — provides a quick overview of all decisions.
- **Individual files:** `docs/adrs/adr-<slug>.md` — full context, decision, and consequences for each decision.

When making a new architectural decision, create a new file in `docs/adrs/` and add an entry to the index below.

## Index Format

- `` <relative path to ADR file> `` : {{short 2-3 line description of the decision}}

## ADR Index

- [`docs/adrs/adr-no-eval-for-input-parsing.md`](../adrs/adr-no-eval-for-input-parsing.md) : Do NOT use `eval` or equivalent methods to evaluate inputs. Use regular expressions or third-party BNF parsers instead.
- [`docs/adrs/adr-package-design-location.md`](../adrs/adr-package-design-location.md) : Package/module design and dependencies are documented in `docs/design/packagedesign.md` using Mermaid.js format.

## Creating a New ADR

1. Create a new file: `docs/adrs/adr-<descriptive-slug>.md`
2. Use the following structure:

```markdown
# ADR: <Title>

**Date:** <date adopted>
**Status:** Accepted | Superseded | Deprecated

## Context

What is the issue or motivation behind this decision?

## Decision

What decision was made?

## Consequences

What are the consequences (positive and negative) of this decision?
```

3. Add an entry to the index above.
