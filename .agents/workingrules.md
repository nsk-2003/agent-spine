# Working Rules that Coding Agents must follow
Strictly follow these rules. DO NOT VIOLATE UNDER ANY CIRCUMSTANCES.

## Working Rules
- Make small, focused changes.
- Preserve behavior unless the task explicitly requires a change.
- Do not change public APIs unless instructed.
- Follow existing project patterns before introducing new ones.
- Write the unit tests before making any changes.
- Run the unit tests and ensure that all tests are passing after making any changes.
- Do not overwrite any file in docs/ folder.
- Modify files in docs/ folder only when explicitly told by user. Do not modify on your own.
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
For all feature development and code changes, strictly follow this "idea → ship" spine in order. Do not skip steps:
1. `/grill-with-docs`: Get interviewed about a plan, and record the decisions.
2. `/to-spec`: Turn an agreed conversation into a written spec.
3. `/to-tickets`: Split a spec into small tickets an agent can build.
4. `/implement`: Build a finished spec into code, test-first.
5. `/code-review`: Review a diff against your standards and against the spec.

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
