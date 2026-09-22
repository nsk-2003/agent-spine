# Working Rules that Coding Agents must follow
Strictly follow these rules. DO NOT VIOLATE UNDER ANY CIRCUMSTANCES.

## Working Rules
- Make small, focused changes.
- Preserve behavior unless the task explicitly requires a change.
- Do not change public APIs unless instructed.
- Follow existing project patterns before introducing new ones.
- Write the unit tests before making any changes.
- Run the unit tests and ensure that all tests are passing after making any changes.
- The Main Flow skills are the sanctioned way to write specific docs (specs, tickets, ADRs, `docs/design/ARCHITECTURE.md`, `sourcemap.md`, `packagedesign.md`, `CONTEXT.md`). Use them for those.
- Do not otherwise overwrite or freehand-edit files in `docs/` — especially human-authored guidance and `TODO` placeholders — unless the user explicitly asks.
- Store your memories in .agents/memory/ folder.

## Do Not
- Implement anything that conflicts with approved specs or architecture decisions.
- Rewrite large parts of the codebase unless explicitly asked.
- Reformat unrelated files.
- Remove TODOs/comments without addressing their intent.
- Assume undocumented behavior is safe to change.
- Generate or modify files that I did not explicitly ask.

## When Unsure
- Ask for clarification instead of guessing.
- Briefly state trade-offs in review notes.
  
## Mandatory Execution: The Main Flow

Before feature work, read `.agents/ai-working-principles.md`. It explains the constraints (smart zone, clear-over-compact, human-in-the-loop vs. AFK, feedback loops as the quality ceiling) that the flow below is built to respect.

The "idea → ship" spine is **scale-adaptive**: run as much process as the work needs, and no more. Pick the entry point by the size of the work.

- **Small** — fits one smart-zone session (~100k tokens) and the path is already clear:
  `/grill-with-docs` → `/implement` → `/code-review`.
  Skip spec and tickets — you do not need them for work that fits a single session.

- **Medium** — needs several sessions, but one grilling makes the path clear:
  `/grill-with-docs` → `/to-spec` → `/to-tickets` → `/implement` (one ticket per fresh session, **clear context between tickets**) → `/code-review`.

- **Large / foggy** — too big to plan in a single session:
  `/wayfinder` (charts the work across many planning sessions) → `/to-spec` → `/to-tickets` → `/implement` → `/code-review`.

### Flow steps

1. `/grill-with-docs`: Get interviewed about a plan; record decisions in `CONTEXT.md` and ADRs. (No codebase yet, or a non-engineering idea? The grilling interview still applies; the docs get created as the project takes shape.)
2. `/to-spec`: Turn the agreed conversation into a written spec (the destination document).
3. `/to-tickets`: Split a spec into small vertical-slice tickets an agent can build.
4. `/implement`: Build a ticket into code, test-first.
5. `/code-review`: Review a diff against your standards and against the spec, in a fresh-context sub-agent.

## Spec & Document Lifecycle

Follow `docs/adrs/adr-spec-lifecycle-and-doc-rot.md`:

- Every spec carries a **Status** (`Draft` → `Active` → `Implemented` / `Superseded`), kept in sync between the `spec.md` header and its `specindex.md` row. Set it to `Implemented` when the code lands; do not keep editing an implemented spec.
- **The code is the source of truth.** Where a spec disagrees with the code, the code wins. Read an `Implemented`/`Superseded` spec as history, and verify against the code before acting on it.
- Delete sprint-scoped artifacts once their work has landed (e.g. Wayfinder maps).
- Keep the durable set (`CONTEXT.md`, ADRs, `ARCHITECTURE.md`, `sourcemap.md`, `packagedesign.md`) small and true.

## Code Generation
- Use "The Main Flow" strictly.
- Follow this project's guidelines first, then "The Main Flow" guidelines.
- Add a Purpose comment at the top of every new file.
- Add an entry for the new source code file in docs/design/sourcemap.md. The entry must contain the name of the source code file (path relative to project root) and the purpose of the file.
- Use sourcemap.md to decide which existing files to modify.
- Analyze the changes in specifications and design documents using the version control diff command then update the code for differences in the specification and design documents.

## Code Review
- Follow "The Main Flow" strictly.
- Validate compliance with project guidelines first, then review against the spec.
