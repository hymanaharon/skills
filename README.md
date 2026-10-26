# product-designer

[![skills.sh](https://skills.sh/b/hymanaharon/skills)](https://skills.sh/hymanaharon/skills)

An [Agent Skill](https://agentskills.io) that walks a feature design top-down: problem → logic → process → UX → UI. The UI comes last. Each layer ends at a gate you confirm before the next one opens.

Works on any project and any skills-compatible agent. It reads that repo's docs, glossary, and design system. For UI it prefers Claude Design when available, and offers agnostic fallbacks (Figma, HTML prototype, images, or annotated wireframes) when it is not.

## Install

```bash
npx skills add hymanaharon/skills
```

Or point your agent at this repo / the `SKILL.md` folder the way your client prefers.

## When to use it

- You want a product-design pass before tickets or code
- You asked for the five-layer design flow / named `product-designer`
- UI mocks keep showing up before the problem and rules are settled

## How it works

1. **Problem** — what's broken, for whom, and what "solved" means
2. **Logic** — entities, states, transitions, edge cases
3. **Process** — owners, approvals, automation, permissions
4. **UX** — flows, routes, empty/loading/error states
5. **UI** — screens in Claude Design when available; otherwise Figma, a visual artifact, or annotated wireframes

Every layer closes with a gate summary. Confirm it (or change it) before the next layer starts. If a lower layer breaks an earlier decision, that layer reopens.

## Optional companion

This skill works best with Matt Pocock's **grilling** skill. Install it if you can; the skill still runs without it:

```bash
npx skills add mattpocock/skills --skill grilling
# or
npx skills add mattpocock/skills --skill grill-me
```

## Notes

- Folder name must stay `product-designer` to match the `name` frontmatter ([spec](https://agentskills.io/specification)).
- `disable-model-invocation: true` is optional client metadata. Other agents can ignore it.
- Keep `SKILL.md` lean. Put long project examples in `references/` if you add them later.

## License

MIT
