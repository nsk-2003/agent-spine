# ARCHITECTURE OF THE APPLICATION

## Key Architecture Guidelines
Always follow the decisions in `docs/design/ADR.md` and the individual ADR files under `docs/adrs/`.

### Modules
- Each folder in the `src/` represents a module or a submodule.
- Modules must have acyclic dependency.
- Higher layer modules can depend on lower layer module.
- Modules in the Same layer cannot depend on each other.
- Frontend modules can depend on backend modules.
- Backend modules cannot depend on the frontend module.

### Module Depth: prefer deep modules
Design modules to be **deep**: a simple, thin interface (the small set of functions/types callers use) hiding substantial functionality. Avoid **shallow** modules — many small, undifferentiated files with tangled cross-dependencies.

- Deep modules are easier for an agent to navigate and to test: wrap one test boundary around the module's interface and you exercise a lot of behaviour.
- Shallow modules force the agent to trace the whole dependency graph to understand anything, and leave test boundaries unclear (which is how bad, over-mocked tests get written).
- Left unsupervised, agents default to producing shallow modules. Steer deliberately toward deep ones.

**Gray-box technique:** design the *interface* of a module yourself, then delegate the *implementation* to the agent. You keep a map of the system's shapes and behaviours — enough to reason about it and to review at the boundary — without reading every internal line. This is how to move fast while retaining a real sense of the codebase.

### Implementation guidelines
- When user enters the input, then pass the string to backend code. The backend will parse the string and generate the appropriate operations code to calculate the result.
- Generate the top level file (containing the main or entry point function) for the application in the `src/` folder.
- Generate and update package design diagram in `docs/design/packagedesign.md`. The file will be in markdown format with diagrams in mermaid.js format.

## Technology Stack
- backend : TODO: Confirm with user and update here
- frontend : TODO: Confirm with user and update here
- build tool : TODO: Confirm with user and update here
- unit test framework : TODO: Confirm with user and update here

## Technology stack specific instructions for Code generation
TODO: Confirm with user and update specific instructions here based on the chosen tech stack.

## Design Documents
- `docs/design/sourcemap.md` : list of source code files and their purpose. Use this information to decide which files to modify or update during the code generation.
- `docs/design/ADR.md` : index of architecture decisions. Individual ADR files live in `docs/adrs/`.
- `docs/design/packagedesign.md` : Mermaid.js diagram of the package/module structure and dependencies.
