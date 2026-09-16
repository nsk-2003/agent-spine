# Architecture Decision Record (ADR) Index
This is an index of key architecture decision records.

The index format is of two types:
- `<relative document path>` : {{short 2-3 lines description of document content}}
- `{{decision description for short decisions}}`

## ADR Index
- Do NOT use 'eval' methods to evaluate the inputs anywhere.
- Use regular expressions or third-party BNF parser to parse the input string. Do not write own parser from scratch.
- `./packagedesign.md` : Documents the package/module design and their dependencies in mermaid.js format.
