---
name: finding-unknowns
description: Use whenever requirements are ambiguous, vague, or underspecified — no matter how small the task sounds ("make it look better", "clean this up", "nothing fancy") — and when starting any non-trivial task: unfamiliar domain or codebase, client-facing deliverables, or changes spanning multiple files. Run before writing plans or code; again during implementation when edge cases force deviation from the plan; and after implementation before handoff, sign-off, or merge. Especially when time pressure or an unreachable user tempts you to skip clarification and build on assumptions.
license: Apache-2.0
metadata:
  author: SanQianQVQ
  version: "1.2.1"
---

# Finding Unknowns

## Overview

The request is a map; the codebase and real-world constraints are the territory. Every gap between them gets filled with a guess — cheap to surface before implementation, expensive to discover after delivery.

**Core principle: spend minutes surfacing unknowns before spending hours building on them.**

## The Four Quadrants

| Quadrant | What it is | How to eliminate |
|---|---|---|
| Known knowns | Stated in the request | Already on the map |
| Known unknowns | Questions noticed but unanswered | Interview: ask, one at a time |
| Unknown knowns | Obvious to the requester, never stated — house templates, client standards, contract formats | Prototype/mockup (seeing it exposes the standard); ask for a reference example |
| Unknown unknowns | Questions nobody thought to ask | Blind spot pass |

## The Rule

Before writing any plan or implementation code, your FIRST output is an **Unknowns Inventory**:

```
## Unknowns Inventory
- [known unknown] <question> → resolve by: ask / reference / conservative default (logged)
- [unknown known] <suspected unstated standard> → resolve by: mockup / example / ask
- [blind spot] <area not yet examined> → resolve by: blind spot pass
```

Every item gets a resolution route: **ask** the user, request a **reference**, build a cheap **prototype/mockup**, or — only when the user is unreachable — take the **conservative default and log it** as a deviation.

An unreachable user makes the inventory MORE important, not less: it decides which defaults are safe and becomes the assumption log delivered with the work.

**Scale the inventory to the ambiguity, not the ritual.** When the request names its exact targets and leaves no format, convention, or scope choice open (a rename, a typo fix, a version bump), the whole inventory is one verification action — confirm the stated scope (e.g. a repo-wide grep), then do the work. The printed block earns its length only when items genuinely route to different resolutions.

## Phase Routing

| You are... | Read |
|---|---|
| Starting a task (no code written yet) | [references/pre-implementation.md](references/pre-implementation.md) |
| Mid-implementation, plan didn't cover this case | [references/during-implementation.md](references/during-implementation.md) |
| Done, preparing handoff / review / sign-off | [references/post-implementation.md](references/post-implementation.md) |

## From Inventory to Plan

The inventory is not a report — it drives what happens next:

- It is the question list for whatever design discussion follows; work through it with the user before committing to a direction.
- When the plan gets written, resolved items feed it as requirements; unresolved items enter it as documented assumptions, never as silent guesses.

## Rationalizations

| Excuse | Reality |
|---|---|
| "User is offline and the deadline is now" | The inventory takes two minutes and changes what you build. Do it, pick conservative defaults, log every one. |
| "Waiting for clarification costs more than delivering on assumptions" | Unlogged assumptions cost the most — the user finds them after delivery. Speed and surfacing unknowns are not in conflict. |
| "The request is clear enough" | Clear requests still hide the requester's unstated standards. One mockup exposes them. |
| "I'll list my assumptions at the end" | By then the work is already shaped by them. Surface them first. |
| "Asking questions looks incompetent" | Shipping the wrong thing looks worse. |

## Red Flags — STOP and build the inventory

- About to write code for a one-sentence task description
- Choosing a format, library, or convention the user never mentioned
- Thinking "they probably want..."
- A client-facing or sign-off deliverable with no example of what the recipient expects
- Three unstated decisions made in a row
