# During Implementation: The Notes Protocol

Unknowns don't stop appearing once the plan is approved — the territory pushes back. Track them in a working file instead of letting them silently reshape the work.

## implementation-notes.md

Keep a temp file `implementation-notes.md` next to the work (or in the scratchpad) with two sections:

```markdown
# Implementation Notes — <task>

## Decisions
- <decision made within the plan's intent, and why>

## Deviations
- <plan said X; territory forced Y; chose conservative option Z; needs review: yes/no>
```

## The Deviation Rule

When an edge case forces you off the plan:

1. Choose the **conservative** option — the one that is easiest to reverse and least surprising to the requester.
2. Record it under **Deviations** with one line of why.
3. Keep working. Do not stall the task to relitigate the plan, and do not silently improvise.

If a deviation would change something from the plan's "most likely to be overturned" list (data model, interfaces, user-visible behavior), mark it `needs review: yes` — it must be surfaced in the handoff, not buried.

## Assumption Log

When the user was unreachable during pre-implementation, unanswered interview questions live here too — every conservative default taken is a Deviation entry. This file becomes the assumption log delivered with the work (see post-implementation).

## The File's Fate

`implementation-notes.md` is a working artifact, not a deliverable. At commit time:

1. Its contents are transcribed into the handoff pitch / PR description (see post-implementation) — the notes travel as text the reviewer will actually read.
2. The file itself stays out of version control: never stage it, and delete it once the handoff document exists.
