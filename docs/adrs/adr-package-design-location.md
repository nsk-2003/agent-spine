# ADR: Package Design Location

**Date:** TODO: Set date when adopted
**Status:** Accepted

## Context

The project needs a single source of truth for the package/module structure and their dependencies.

## Decision

Package/module design and their dependencies are documented in `docs/design/packagedesign.md` using Mermaid.js format.

## Consequences

- The diagram must be updated whenever the package structure changes.
- Use this diagram to understand module dependencies before introducing new modules.
- The diagram enforces acyclic dependency rules between modules.
