# TEMPLATE — Hero Distillation Starter Kit

Copy this directory to start a new hero repo. Replace `HERO_NAME` and `hero-name` throughout.

## Files to customize (in order)

1. `info.md` — research and write first; everything else derives from this
2. `principles.md` — extract actionable principles from the research
3. `CONTEXT.md` — define the hero's conceptual vocabulary
4. `CLAUDE.md` — translate principles into AI behavioral guidelines
5. `EXAMPLES.md` — show before/after with concrete cases
6. `README.md` + `README.zh.md` — write last, after content is solid
7. `skills/hero-name/SKILL.md` — sync from CLAUDE.md
8. `.cursor/rules/hero-name.mdc` — sync from CLAUDE.md
9. `.claude-plugin/plugin.json` + `marketplace.json` — fill in metadata

## File Synchronization Rule

These three MUST stay in sync when principles change:
- `CLAUDE.md`
- `.cursor/rules/hero-name.mdc`
- `skills/hero-name/SKILL.md`
