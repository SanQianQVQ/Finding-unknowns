# Post-Implementation: Handoff and Verification

Two artifacts close the loop: a pitch that transfers your context to reviewers, and a quiz that proves the requester actually holds that context.

## 1. Pitch / Explainer

Package prototype, spec, and implementation notes into ONE document a reviewer can absorb without re-deriving your unknowns.

For code changes, the PR description IS this document.

Structure — every part REQUIRED:
- Lead with the artifact itself (demo GIF, screenshot, or the rendered deliverable)
- What was asked / what was built
- Decisions and deviations — transcribed in full from implementation-notes.md into this document, `needs review: yes` items first and stated verbatim. "See implementation-notes.md" is not surfacing; the reviewer reads this document, nothing else.
- Open assumptions the requester must confirm before sign-off

The notes file itself never ships — its contents move here, then it is deleted (see during-implementation).

Example prompt:
- "Package the prototype, spec, and implementation notes into a single doc I can drop into Slack for buy-in. Start with a demo GIF."

Why it works: reviewers start from the same unknowns you did. Showing you already surfaced and resolved them is what makes approval fast.

## 2. Quiz — for long sessions

After a long working session, verify the human actually understands what changed before they sign off or merge. Generate a report with a quiz at the bottom; a perfect score is the merge gate.

Example prompt:
- "Make an HTML report that helps me understand every change, with a must-pass quiz at the bottom. I don't merge until I score 100%."

The quiz catches the final unknown: the gap between what was built and what the requester THINKS was built.
