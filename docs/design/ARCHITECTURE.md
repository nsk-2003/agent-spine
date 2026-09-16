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
