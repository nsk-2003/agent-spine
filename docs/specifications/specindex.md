# Index of Specification Documents

This is the index of specification documents. Update this index whenever you add a new specification document.

## Folder Structure

Each specification lives in its own numbered folder under `docs/specifications/`:

```
docs/specifications/
├── specindex.md                  ← This file
├── 001-<slug>/
│   ├── spec.md                   ← Core: problem, solution, user stories, decisions
│   ├── plan.md                   ← Core: approach, milestones, risks
│   └── tasks.md                  ← Core: checklist of implementation tasks
├── 002-<slug>/
│   └── ...
└── 003-<slug>/
    └── ...
```

Each spec folder contains three core files:

| File | Purpose |
|---|---|
| `spec.md` | Problem statement, user stories, implementation decisions, testing decisions, out of scope |
| `plan.md` | Approach, milestones, risks, dependencies — or a Wayfinder decision map, when the effort was planned with `/wayfinder` |
| `tasks.md` | Numbered, sequential task checklist for implementation |

Optional files (contracts, checklists, diagrams) may be added as needed — they are not pre-created.

## Index Format

- `` <relative folder path> `` — **[Status]** : {{short 2-3 line description of spec content}}

Status is one of `Draft` → `Active` → `Implemented` / `Superseded` (see `docs/adrs/adr-spec-lifecycle-and-doc-rot.md`).

## How to Use This File

- Use this file to determine which specification documents to load.
- Do not load all specification documents every time.
- Load only the specs relevant to the current phase or task.
- **Treat `Implemented`/`Superseded` specs as history, not current truth.** The code is the source of truth; verify against it before acting on a completed spec.

## Specifications Index

- `./001-example-spec/` — **[Draft]** : Example specification demonstrating the numbered-folder structure. Contains placeholder spec, plan, and tasks files. Replace with your first real spec.
