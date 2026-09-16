# Source Map

This file is the registry of ALL source code files in the project. It explains what each file contains and its role in the application.

> **IMPORTANT:** This file MUST be updated alongside development. Every time a new source file is created or an existing file's purpose changes significantly, update this registry. Use this file to decide which files to modify during code generation.

## Format

Each entry must follow this format:

| File (relative to project root) | Purpose |
|---|---|
| `src/example_module/module_core.py` | **Good example:** This module handles the core parsing logic for user input strings, tokenizing them into structured operations. |
| `src/example_module/utils.py` | **Bad example:** Utility functions. _(Too vague — does not explain what specific utilities or why they exist.) |

### Guidelines for Purpose Comments

- **Be specific:** State what the file does, not just its category.
- **Mention responsibilities:** What problem does this file solve?
- **Avoid generic labels:** "Utils", "helpers", "common" are not purposes.
- **Keep it concise:** One to two sentences maximum.

## Source Code Registry

> TODO: Populate this table as source files are created during development.

| File (relative to project root) | Purpose |
|---|---|
| _(no entries yet)_ | _Entries will be added as development progresses._ |
