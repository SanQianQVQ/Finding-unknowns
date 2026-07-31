---
description: Force-run the finding-unknowns workflow — build the full Unknowns Inventory for a task right now
---

Force-invoke the **finding-unknowns** skill on the following task, skipping the "is this non-trivial enough?" judgment — the user explicitly asked for the full workflow:

**Task:** $ARGUMENTS

If the task above is empty, apply it to the task currently being discussed in this conversation.

Rules for this forced run:

1. Load and follow the finding-unknowns skill (via the Skill tool if available; otherwise read its `SKILL.md` from your skills directory).
2. Your FIRST output is the printed **Unknowns Inventory** block — this forced invocation overrides the skill's scale-down clause: the user wants the full inventory even for a task that looks mechanical.
3. Route every item to a resolution (ask / reference / mockup / conservative default, logged) and proceed per the skill's phase routing.
