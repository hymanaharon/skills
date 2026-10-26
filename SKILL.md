---
name: product-designer-agnostic
description: Design a feature top-down for any project (problem, logic, process, UX, then UI), stopping after each layer to settle it with the user. Use when the user names product-designer-agnostic, or asks for the project-agnostic five-layer product design flow.
disable-model-invocation: true
license: MIT
---

Design a feature the way a product designer does: the UI comes **last**. Work five **layers** in order, each one resting on the layers above it:

1. **Problem**: what's actually broken, and for whom.
2. **Logic**: rules, states, edge cases.
3. **Process**: who owns what, what happens when.
4. **UX**: flows and structure.
5. **UI**: screens, drawn in the design surface this session can reach.

Each layer ends at a **gate**: post a summary of what you settled, then wait for the user to confirm it before you open the next layer. A question that belongs to a lower layer gets parked as an open question for that layer. When a lower layer exposes a flaw in a settled one, say so, reopen that layer, and re-gate it.

## Gate summary

Close every layer with this block, carrying forward everything settled so far so the latest gate is always the whole brief:

```
### ✅ Layer N settled: <name>

**Decided**
- <each decision, one line>

**Assumptions** (unverified, flag to confirm later)
- …

**Parked for later layers**
- Layer M: <question>

Confirm, or tell me what to change, and I'll open Layer N+1.
```

## Layer 1: Problem (grill)

Ground yourself in the project before the first question. Find its sources of truth and read the ones this feature touches:

- The docs index, README, or architecture doc the repo points agents at
- The domain glossary and any recorded decisions
- The relevant spec and plan, if they exist
- The ticket, if one is named

Look at what the product does today in this area: routes, entities, and the persona each surface serves.

Then invoke the `grilling` skill, scoped to the problem only: who hits it (persona, role, scope), what they do today instead, what breaks and how often, what evidence exists, and what "solved" looks like. A proposed solution is a symptom; trace it back to the need it serves.

Done when you can state the problem in one sentence, name the persona it hurts, and give the success measure, and the user agrees with all three. A conflict with a recorded product decision goes to the user as a new decision, never resolved silently.

## Layer 2: Logic

Grill the rules the feature lives by: the entities involved and their **states**, every transition and what triggers it, invariants that must always hold, and **edge cases** (empty, first-time, duplicate, concurrent edit, partial data, the reversal of every action). Reuse the project's glossary and existing domain models; name each new term explicitly.

Done when every state has its entry and exit transitions, and every edge case has an outcome. A state diagram or table in the gate summary is the check.

## Layer 3: Process

Map ownership and time: which persona or role performs each transition, who is notified, who approves, what runs automatically, and what happens when someone doesn't act. Tie each actor to this project's authorization model (roles, relations, scope, and any tenant or account boundary) and name each write the project already records, such as an audit event.

Done when every transition from Layer 2 has an owner, a trigger, and a permission.

## Layer 4: UX

Turn the process into flows: the entry point for each actor, the steps in each flow, the decision points, and where each flow lands on success, failure and cancel. Place each flow in the existing structure: which app or surface, which route, which existing page or feature it extends. Plan the empty, loading, error and permission-denied states.

Done when every flow runs from entry to an exit, and you have a list of the screens Layer 5 must draw, each with its states.

## Layer 5: UI

Draw the screens from the Layer 4 list. Use the design surface this session can reach. In Claude, call the Artifact tool with `action: "quickstart"` and `intent: "design"`, then follow the instructions it returns. Build on the project's look: its design-system tokens and components (read that package's README, or the style source the repo treats as canonical), and every locale and writing direction the product already ships. Draw each screen in its main state, then the states Layer 4 named.

Done when every screen on the list is drawn in every listed state, and the user has reviewed the design. Close with the final gate summary and offer the project's spec step (such as `/to-spec`) to turn the brief into a ticket.
