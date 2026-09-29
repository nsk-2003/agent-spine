# Project Template — For Human Developers

This is a generic, AI-agent-ready project template. Use it as a starting point for any new project.

## How to Use

1. **Clone or copy this template** into your new project directory.
2. **Initialize version control:**
   ```bash
   git init
   ```
3. **Open the project in your AI coding agent.**
4. **Paste the following prompt** to kick off the session:

   > Read AGENTS.md and prepare the project for development.

5. **The AI agent will then:**
   - Read the master instructions (`AGENTS.md`).
   - Detect all `TODO` placeholders across the documentation.
   - Grill you with targeted questions to fill in every project-specific detail (tech stack, architecture, specs, etc.).
   - Update the documentation with your answers.
   - Only begin coding once the key decisions are resolved (living registries like the source map are filled in as you build).

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
| `CLAUDE.md` | Symlink to `AGENTS.md`, for tools that look for this filename. Never edit directly. |
| `.agents/workingrules.md` | Strict rules the AI coding agent must follow. |
| `.agents/ai-working-principles.md` | The operating theory the workflow is built on (reference). |
| `.agents/skills/` | Skill definitions, one folder per skill. The canonical copy. |
| `.claude/skills/` | Symlink to `.agents/skills/`, for tools that look there. Never edit directly. |
| `CONTEXT.md` | The project's shared vocabulary (domain glossary), grown as you go. |
| `docs/` | Shared documentation (human + AI). Contains specs, architecture, and design docs. |
| `src/` | Application source code (populated during development). |
| `test/` | Tests — plans, unit tests, and test data. |
| `environment.sh` / `environment.bat` | Environment setup scripts (stubs, to be customized). |

## Notes

- **Do not edit `AGENTS.md` or `.agents/workingrules.md`** unless you intentionally want to change how the AI agent behaves.
- All `TODO` markers in `docs/` are intentional placeholders. The AI agent will guide you through filling them.
- This template is framework-agnostic. It works with any language, stack, or tooling.
- **The repo is the only source of truth.** Anything worth carrying between sessions is a decision, and decisions are written to an ADR under `docs/adrs/` or to `CONTEXT.md`, where they are reviewable in version control.
- **`AGENTS.md` and `.agents/` hold the real agent instructions and skills**; `CLAUDE.md` and `.claude/skills/` are symlinks into them, not copies. Keeping the content out of any single tool's directory is what lets a new tool be supported by adding one symlink, with nothing to rewrite and no copy to drift.
