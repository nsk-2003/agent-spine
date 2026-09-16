# Project Template — For Human Developers

This is a generic, AI-agent-ready project template. Use it as a starting point for any new project.

## How to Use

1. **Clone or copy this template** into your new project directory.
2. **Initialize version control:**
   ```bash
   git init
   ```
3. **Open the project with your preferred AI coding tool** (e.g., Bionic, Cursor, Claude Code, etc.).
4. **Paste the following prompt** to kick off the session:

   > Read AGENTS.md and prepare the project for development.

5. **The AI agent will then:**
   - Read the master instructions (`AGENTS.md`).
   - Detect all `TODO` placeholders across the documentation.
   - Grill you with targeted questions to fill in every project-specific detail (tech stack, architecture, specs, etc.).
   - Update the documentation with your answers.
   - Only begin coding once all context is resolved.

## What to Expect

The agent will ask you concrete questions about:

- **Technology stack** — backend, frontend, build tools, testing framework.
- **Architecture** — module structure, dependency rules, design constraints.
- **Specifications** — what the application should do, phase by phase.
- **Development environment** — how to set up, run, and test locally.

Be prepared to answer with specificity. Vague answers will be challenged — this is intentional. The quality of the generated code depends on the quality of the context you provide.

## Template Structure

| Path | Purpose |
|---|---|
| `AGENTS.md` | Master instructions for AI agents (not for humans). |
| `.agents/workingrules.md` | Strict rules the AI coding agent must follow. |
| `.agents/memory/` | Agent's internal memory and session state. |
| `.agents/skills/` | Agent-specific skill configuration. |
| `docs/` | Shared documentation (human + AI). Contains specs, architecture, and design docs. |
| `src/` | Application source code (populated during development). |
| `test/` | Tests — plans, unit tests, and test data. |
| `environment.sh` / `environment.bat` | Environment setup scripts (stubs, to be customized). |

## Notes

- **Do not edit `AGENTS.md` or `.agents/workingrules.md`** unless you intentionally want to change how the AI agent behaves.
- All `TODO` markers in `docs/` are intentional placeholders. The AI agent will guide you through filling them.
- This template is framework-agnostic. It works with any language, stack, or tooling.
