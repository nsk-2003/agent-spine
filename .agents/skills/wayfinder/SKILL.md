---
name: wayfinder
description: Plan work too big to fit one session -> chart a map of decision tickets across many planning sessions, clearing the fog until the destination is reachable, then hand off to spec and tickets.
license: MIT
metadata:
  origin: https://github.com/mattpocock/skills
  author: mattpocock
---
Call the Skill tool for "wayfinder" if available.

If the skill is not available, follow the behavior described below.

## When to use (and when not to)

Use Wayfinder for **large, foggy** work: you know roughly where you want to end up, but the path is genuinely unclear and there are far too many decisions to settle in a single `grill-with-docs` session (which is bounded by the smart zone — see `.agents/ai-working-principles.md`).

Do **not** use it when the work fits in one session or the path is already clear. In that case just `grill-with-docs` and go. Wayfinder is for clearing fog of war, not for adding ceremony to work you already understand.

## The model: a map of decisions

Wayfinder charts a **map** from where you are to a destination. On the map:

- The **frontier** is every decision you can make *right now* — its prerequisites are settled.
- The **fog** is everything not yet decidable, because it waits on a conversation or a real-world task that hasn't happened.
- Each point on the map is a **decision ticket**, and each ticket is worked in its own fresh session. Resolving a ticket pushes the frontier outward and clears fog, until enough decisions are made that the destination is reachable.

**Decision tickets are not implementation tickets.** Wayfinder produces the decisions that let you *write* a spec; `to-tickets` later produces the implementation slices that *build* it.

## The ticket types

- **grilling** — the default. A discussion (via `grill-with-docs`) to settle an aspect of the plan.
- **task** — something that must happen in the real world or is scheduled behind other work (configure a service, contact a person, provision access).

## Behavior

1. **Set the destination.** Ask what "done" looks like — most often a buildable spec. Explore the repo, then run an initial grilling session to establish the basic premise.

2. **Chart the first map.** Create the parent map and its decision tickets in the issue tracker — a numbered spec folder under `docs/specifications/<NNN>-<slug>/`, with the map as `plan.md` and each decision ticket as a sub-item. Give each ticket a **type** (above) and its **blocking edges**. Only some tickets will be takable immediately; the rest sit in fog.

3. **Work the frontier, one ticket per session.** Invoke Wayfinder again on a specific ticket. Do that ticket's work in a fresh session, then **write the resolution back up to the map** so the record lives in one place. Recompute the frontier: what did resolving this unblock?

4. **Repeat until the fog clears** and the destination is reachable — every branch decided, nothing silently assumed.

5. **Hand off.** The map is usually too dense to be a spec itself. Run `to-spec` against the completed map to produce the destination document, then `to-tickets` to produce the implementation slices, then `implement` / `code-review` as normal.

## The payoff over a plain spec

Because every decision is a ticket that links back to the session where it was made, the resulting spec carries **primary sources**. When a later agent is confused, it can open the original decision ticket rather than trusting a lossy summary. Follow the same lifecycle as any spec (see the spec-lifecycle ADR): the map and its decision tickets are sprint-scoped — close them once the work has landed in the code.
