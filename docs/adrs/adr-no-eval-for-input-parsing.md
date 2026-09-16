# ADR: Do Not Use Eval for Input Parsing

**Date:** TODO: Set date when adopted
**Status:** Accepted

## Context

The application processes user input strings that need to be parsed and evaluated.

## Decision

Do NOT use `eval` or equivalent methods to evaluate inputs anywhere in the codebase.

## Consequences

- Use regular expressions or third-party BNF parsers to parse input strings.
- Do not write a parser from scratch unless no suitable third-party option exists.
- This decision applies to all layers of the application, including tests and scripts.
