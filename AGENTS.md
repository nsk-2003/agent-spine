# AGENTS.md — Master Instructions for AI Coding Agents

> **README.md file is for the developer and not for AI agents like you. Ignore the README.md.**

## Objective

Assist the human developer in building the application in phased increments. Work iteratively: understand, plan, implement, test, and review — one phase at a time.

## MANDATORY RULE: Context-First, Code-Second

If project details are not decided or contain `TODO` placeholders, you MUST ask the user for full project details and update this file. Make it mandatory for the user to set up their project-specific details. Grill the user until all necessary context is provided. Do not proceed with code generation until project details are fully defined.

Specifically, before any code generation:

1. Scan all files under `docs/` for `TODO` markers.
2. For each `TODO`, ask the user a specific, pointed question.
3. Do not accept vague answers. Probe for concrete decisions (tech stack, build tool, testing framework, deployment target, etc.).
4. Update the relevant documentation files with the user's answers.
5. Only begin coding once every `TODO` has been resolved.

## Project Folder Map

| Path | Purpose |
|---|---|
| `AGENTS.md` | **This file.** Master instructions for AI agents. Read this first. |
| `.agents/workingrules.md` | Strict rules the coding agent must follow during development. |
| `.agents/memory/` | Agent's internal memory and state. Store context, decisions, and session notes here. |
| `.agents/skills/` | Agent-specific skill files and tooling configuration. |
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
| Grill with Docs | `.agents/skills/grill-with-docs/` | Stress-test project details and resolve all `TODO` placeholders before coding. |
| To Spec | `.agents/skills/to-spec/` | Transform a feature idea into a structured specification document. |
| To Tickets | `.agents/skills/to-tickets/` | Break a specification into implementation tasks and an execution plan. |
| Implement | `.agents/skills/implement/` | Execute the implementation plan, task by task, with testing. |
| Code Review | `.agents/skills/code-review/` | Review completed work against the spec and project standards. |

## How to Begin

1. Read `.agents/workingrules.md` to understand the rules you must follow.
2. Read `docs/design/ARCHITECTURE.md` to understand the project's tech stack and constraints.
3. Read `docs/design/ADR.md` to understand key architectural decisions and their rationale.
4. Read `docs/specifications/specindex.md` to know which specs exist.
5. Load only the specs relevant to the current phase or task — do not load all specs at once.
6. Check `docs/design/sourcemap.md` before modifying any source file to understand the existing codebase.
7. Follow "The Main Flow" defined in `.agents/workingrules.md` for all feature work.
