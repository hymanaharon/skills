# product-designer-agnostic

[![skills.sh](https://skills.sh/b/judojourneyapp/product-designer-agnostic)](https://skills.sh/judojourneyapp/product-designer-agnostic)

An [Agent Skill](https://agentskills.io) that walks a feature design top-down: problem → logic → process → UX → UI. The UI comes last. Each layer ends at a gate you confirm before the next one opens.

Works on any project. It looks for that repo's own docs, glossary, and design system instead of hard-coding one product.

## Install

```bash
npx skills add judojourneyapp/product-designer-agnostic
```

Or point your agent at this repo / the `SKILL.md` folder the way your client prefers.

## When to use it

- You want a product-design pass before tickets or code
- You named `product-designer-agnostic` / asked for the five-layer flow
- UI mocks keep showing up before the problem and rules are settled

## How it works

1. **Problem** — what's broken, for whom, and what "solved" means
2. **Logic** — entities, states, transitions, edge cases
3. **Process** — owners, approvals, automation, permissions
4. **UX** — flows, routes, empty/loading/error states
5. **UI** — screens on whatever design surface the session can reach

Every layer closes with a gate summary. Confirm it (or change it) before the next layer starts. If a lower layer breaks an earlier decision, that layer reopens.

## Recommended companion

Layer 1 calls a **grilling** skill to stress-test the problem. Install one of these (or use your own grill skill with the same name):

```bash
npx skills add mattpocock/skills --skill grilling
# or
npx skills add mattpocock/skills --skill grill-me
```

Without a grill skill, the agent should still ask hard problem questions; the dedicated skill just makes that pass sharper.

## Notes for publishers / forks

- Folder name must stay `product-designer-agnostic` to match the `name` frontmatter ([spec](https://agentskills.io/specification)).
- `disable-model-invocation: true` is optional client metadata. Other agents can ignore it.
- Keep `SKILL.md` lean. Put long project examples in `references/` if you add them later.

## License

MIT
