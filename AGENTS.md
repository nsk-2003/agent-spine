# AGENTS.md — Master Instructions for AI Coding Agents

> **README.md file is for the developer and not for AI agents like you. Ignore the README.md.**

## Objective

Assist the human developer in building the application in phased increments. Work iteratively: understand, plan, implement, test, and review — one phase at a time.

## MANDATORY RULE: Context-First, Code-Second

If project details are not decided or contain `TODO` placeholders, you MUST ask the user for full project details and update this file. Make it mandatory for the user to set up their project-specific details. Grill the user until all necessary context is provided. Do not proceed with code generation until project details are fully defined.

Specifically, before any code generation:

1. Scan `docs/` and `CONTEXT.md` for **decision** `TODO` markers — the ones that need a human choice (tech stack, build tool, testing framework, deployment target, architecture constraints, dev environment).
2. For each, ask the user a specific, pointed question.
3. Do not accept vague answers. Probe for concrete decisions.
4. Update the relevant documentation files with the user's answers.
5. Only begin coding once every **decision** `TODO` is resolved. **Living registries** — `docs/design/sourcemap.md`, `docs/design/packagedesign.md`, ADR dates, and per-spec `plan.md`/`tasks.md` — are filled in as development progresses, not up front. Do not block on them.

## Project Folder Map

| Path | Purpose |
|---|---|
| `AGENTS.md` | **This file.** Master instructions for AI agents. Read this first. |
| `CLAUDE.md` | Symlink to `AGENTS.md`. Do not edit — edit `AGENTS.md`. |
| `.agents/workingrules.md` | Strict rules the coding agent must follow during development. |
| `.agents/ai-working-principles.md` | The operating theory (smart zone, clear-over-compact, feedback loops, deep modules). Read before the working rules. |
| `.agents/skills/` | Skill definitions, one folder per skill (see the Agent Skills table below). The canonical copy. |
| `.claude/skills/` | Symlink to `.agents/skills/`. Do not edit — edit the files under `.agents/skills/`. |
| `CONTEXT.md` | Ubiquitous-language glossary (durable). Read at the start of grilling; the shared vocabulary of the project. |
| `docs/devenv.md` | Step-by-step local development environment setup instructions. |
| `docs/implementation_plan.md` | Phase-wise roadmap and implementation plan. |
| `docs/specifications/specindex.md` | Index of all spec documents. Use this to avoid loading all specs at once. |
| `docs/specifications/<NNN>-<slug>/` | Individual specification folders (e.g., `001-example-spec/`). Each contains `spec.md`, `plan.md`, `tasks.md`. |
| `docs/design/ARCHITECTURE.md` | Tech stack, module dependency rules, and high-level architecture. |
| `docs/design/ADR.md` | Architecture Decision Records index. Individual ADRs live in `docs/adrs/`. |
| `docs/adrs/` | Individual ADR files (`adr-<slug>.md`). One file per architectural decision. |
| `docs/design/packagedesign.md` | Mermaid.js diagram of the package/module structure. |
| `docs/design/sourcemap.md` | Registry of all source code files and their purpose. Updated alongside development. |
| `src/` | Application source code. |
| `test/unit/` | Unit test source code. |
| `test/testdata/` | Mock data, fixtures, and test assets. |
| `environment.sh` | Unix environment setup entry point. |
| `environment.bat` | Windows environment setup entry point. |

## Agent Skills

This project uses skills from the [Main Flow](https://www.aihero.dev/skills) framework. Skills are stored in `.agents/skills/` and guide the agent through each phase of the workflow.

| Skill | Location | Purpose |
|---|---|---|
| Wayfinder | `.agents/skills/wayfinder/` | Plan work too big for one session: chart a map of decision tickets and clear the fog before writing a spec. |
| Grill with Docs | `.agents/skills/grill-with-docs/` | Relentless one-question-at-a-time interview to sharpen a plan; reads and updates `CONTEXT.md` and ADRs. |
| To Spec | `.agents/skills/to-spec/` | Synthesize the agreed conversation into a structured specification (destination document). |
| To Tickets | `.agents/skills/to-tickets/` | Break a spec into small vertical-slice (tracer-bullet) tickets with blocking edges. |
| Implement | `.agents/skills/implement/` | Build a ticket into code, test-first, one ticket per fresh session. |
| Code Review | `.agents/skills/code-review/` | Review the diff against standards and spec, in a fresh-context sub-agent. |

## How to Begin

1. Read `.agents/ai-working-principles.md` to understand the constraints the workflow is built around.
2. Read `.agents/workingrules.md` to understand the rules you must follow.
3. Read `CONTEXT.md` to learn the project's shared vocabulary before discussing or naming anything.
4. Read `docs/design/ARCHITECTURE.md` to understand the tech stack, module rules, and deep-module guidance.
5. Read `docs/design/ADR.md` to understand key architectural decisions and their rationale.
6. Read `docs/specifications/specindex.md` to know which specs exist and their status.
7. Load only the specs relevant to the current phase or task — do not load all specs at once. Treat `Implemented`/`Superseded` specs as history and verify against the code.
8. Check `docs/design/sourcemap.md` before modifying any source file to understand the existing codebase.
9. Follow "The Main Flow" in `.agents/workingrules.md`, choosing the entry point by the size of the work (small / medium / large).
