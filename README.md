# Finding Unknowns

> Surface what you don't know before it ships as a bug.

An [Agent Skill](https://agentskills.io) that forces the unknowns out of a task — before, during, and after implementation. Works in any agent that supports the Agent Skills format: **Claude Code, Cursor, Codex, OpenCode**, and 70+ others.

Built from two Anthropic engineering posts: [*A Field Guide to Claude Fable: Finding Your Unknowns*](https://claude.com/blog/a-field-guide-to-claude-fable-finding-your-unknowns) and [*The New Rules of Context Engineering for Claude 5 Generation Models*](https://claude.com/blog/the-new-rules-of-context-engineering-for-claude-5-generation-models).

## Why

The request is a map; the codebase and real-world constraints are the territory. Every gap between them gets filled with a guess — cheap to surface before implementation, expensive to discover after delivery.

| Quadrant | What it is | How to eliminate |
|---|---|---|
| Known knowns | Stated in the request | Already on the map |
| Known unknowns | Questions noticed but unanswered | Interview: ask, one at a time |
| Unknown knowns | Obvious to the requester, never stated | Prototype/mockup; ask for a reference example |
| Unknown unknowns | Questions nobody thought to ask | Blind spot pass |

## What it does

- **Pre-implementation** — the agent's first output is an **Unknowns Inventory**: every gap routed to a resolution (ask / reference / mockup / logged conservative default), backed by five discovery techniques (blind spot pass, throwaway prototypes, one-question-at-a-time interviews, reference hunting, decision-first plans).
- **During implementation** — a notes protocol tracks decisions and deviations in a working file instead of letting edge cases silently reshape the work; every deviation takes the conservative option and gets logged.
- **Post-implementation** — deviations are transcribed verbatim into the PR description / handoff pitch (`needs review` items first), and a comprehension quiz gates sign-off after long sessions.
- **Scales down** — a fully-specified mechanical change (rename, typo fix, version bump) collapses to one verification action, not a printed ritual.
- **Pressure-resistant** — an unreachable user or a hard deadline makes the inventory *more* important, not less: it becomes the assumption log delivered with the work.

## Install

### One command, any supported agent

```bash
npx skills add SanQianQVQ/Finding-unknowns
```

The [skills CLI](https://skills.sh) installs into Claude Code, Cursor, Codex, OpenCode, Windsurf, Gemini CLI, and 70+ other agents.

### Claude Code (plugin marketplace)

```
/plugin marketplace add SanQianQVQ/Finding-unknowns
/plugin install finding-unknowns@finding-unknowns
```

### Manual

Copy `skills/finding-unknowns/` into your agent's skills directory:

| Agent | Global path |
|---|---|
| Claude Code | `~/.claude/skills/` |
| Cursor | `~/.cursor/skills/` |
| OpenCode | `~/.config/opencode/skills/` |
| Cross-runtime (Codex, Copilot CLI, Gemini CLI) | `~/.agents/skills/` |

## How it triggers

The skill activates itself on any non-trivial task — ambiguous requirements, unfamiliar domain or codebase, client-facing deliverables, changes spanning multiple files — before plans or code are written, and again when mid-implementation edge cases force deviation, and before handoff or merge. No slash command needed.

It is fully self-contained — no companion skills required: the inventory doubles as the question list for design discussion, and its resolved/unresolved items flow into the plan as requirements and documented assumptions.

## Anatomy

```
skills/finding-unknowns/
├── SKILL.md                          # Trigger rules + the Unknowns Inventory contract
└── references/                       # Loaded on demand (progressive disclosure)
    ├── pre-implementation.md         # Five discovery techniques
    ├── during-implementation.md      # Notes protocol, deviation rule, assumption log
    └── post-implementation.md        # Handoff pitch + sign-off quiz
```

Metadata costs ~100 tokens at startup; the body loads only when the skill activates; references load only for the phase you're in.

## Testing

Developed with RED-GREEN skill TDD: every rule was written against a documented baseline failure (subagent pressure scenarios run *without* the skill), then verified to pass with it — including ceremony-scaling on mechanical tasks, working-file hygiene at commit time, self-contained operation with no companion skills, and a deadline-pressure regression on the core inventory behavior.

## License

[Apache-2.0](LICENSE)
