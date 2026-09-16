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
| `plan.md` | Approach, milestones, risks, dependencies |
| `tasks.md` | Numbered, sequential task checklist for implementation |

Optional files (contracts, checklists, diagrams) may be added as needed — they are not pre-created.

## Index Format

- `` <relative folder path> `` : {{short 2-3 line description of spec content}}

## How to Use This File

- Use this file to determine which specification documents to load.
- Do not load all specification documents every time.
- Load only the specs relevant to the current phase or task.

## Specifications Index

- `./001-example-spec/` : Example specification demonstrating the numbered-folder structure. Contains placeholder spec, plan, and tasks files. Replace with your first real spec.
- `./002-example-phase2/` : Example placeholder for a second phase or feature. Follows the same spec.md / plan.md / tasks.md structure.
- `./003-example-phase3/` : Example placeholder for a third phase or feature. Follows the same spec.md / plan.md / tasks.md structure.
