# Pre-Implementation: Five Discovery Techniques

Run these against the Unknowns Inventory before any plan or code. Each is a cheap way to find out what you don't know before it gets expensive. Pick the ones the inventory calls for — not every task needs all five.

## 1. Blind Spot Pass — for unknown unknowns

When entering an unfamiliar domain or codebase, survey it for the questions nobody thought to ask, and explain findings back in plain terms.

Example prompts:
- "I'm adding a new auth provider but don't know this codebase. Do a blind spot pass: what unknown unknowns should I be aware of?"
- "Before I build this export feature: what do people who do this professionally worry about that I haven't mentioned?"

Output: new items for the inventory, each routed to a resolution.

## 2. Brainstorms & Prototypes — for unknown knowns

When the requester "will know it when they see it" (reports, UIs, formats, tone), build throwaway mockups with fake data BEFORE touching the real implementation. Seeing a concrete artifact extracts standards that were never stated.

Example prompts:
- "Make 4 wildly different single-file HTML mockups of this report so we can see the possibilities."
- "Mock up the editor toolbar in one HTML file with fake data — I want to react to the layout before it touches the real app."

A mockup shown before building beats a feature revised after.

## 3. Interviews — for known unknowns

When ambiguity remains, ask questions one at a time, prioritizing answers that would change the architecture (data model, interfaces, user flow) over cosmetics.

Example prompt:
- "Ask me questions one at a time. Prioritize the ones whose answers would change the architecture."

If the user is unreachable: write the interview questions anyway, answer each with the most conservative defensible default, and log every one in the assumption log (see during-implementation).

## 4. References — for things hard to describe

A working example carries more detail than any description. Ask for or find source material: an existing report the client accepted, a library that implements the desired behavior, last quarter's deliverable.

Example prompt:
- "This Rust crate implements the backoff behavior I want. Read it and reimplement the same semantics in TypeScript."

For client-facing deliverables, one accepted past example is the single highest-value reference — it encodes the contract format, required fields, and tone all at once.

## 5. Implementation Plans — for surfacing decisions early

Write the plan so the most-likely-to-change decisions appear first: data model changes, new type interfaces, UX flow. Reviewers correct what they see first.

Example prompt:
- "Write the implementation plan, but lead with the decisions most likely to be overturned: data model, interfaces, anything user-visible."

Write the plan with the Unknowns Inventory attached: resolved items feed the plan as requirements; unresolved items enter it as documented assumptions.
