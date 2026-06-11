# CLAUDE.md

This file provides guidance to Claude Code when working with code in this repository.

## Project: 英雄蒸馏 (Hero Distillation)

A meta-framework for distilling exceptional thinkers into reusable GitHub repositories. Each hero becomes a standalone repo with behavioral guidelines, actionable principles, deep analysis, and loadable AI skills.

**Distillation skill**: `.claude/skills/distill-hero/` with bundled `TEMPLATE/`. Invoke via `/distill-hero` or by saying "蒸馏XX".

## Repository Architecture

```
heros-distill/
  .claude/skills/distill-hero/    # Distillation skill + TEMPLATE (11 files)
  CLAUDE.md                       # You are here
  README.md + README.zh.md
  heros/                          # Work-in-progress (each → independent gh repo)
  andrej-karpathy-skills/         # Reference: behavioral distillation
  musk-decision-interrogation/    # Reference: framework distillation
```

## Distillation Pipeline

When asked to distill a hero, follow these phases in order:

| Phase | What | Key Rule |
|-------|------|----------|
| **1. Research** | Web-search primary + secondary sources. Spawn research subagent for complex heroes. | Don't write files yet |
| **2. Write Core** | info.md first (5 sections: insights → decision chains → cases → evaluations → synthesis), then principles.md (8-10 actionable, grounded, dual-use) | Gate check: can someone apply each principle tomorrow without knowing the hero? |
| **3. Build Repo** | Discover natural pipeline grouping of principles (3-5 phases) → write CONTEXT.md, CLAUDE.md, SKILL.md, .mdc, EXAMPLES.md, READMEs, plugin files | Never ship flat principles. Three-file sync: CLAUDE.md ↔ SKILL.md ↔ .mdc |
| **4. Grill** | Terminology audit, structure audit, sync audit, completeness audit, quality audit, cross-reference audit | Fix everything. Commit per batch. |
| **5. Publish** | `git init` → `gh repo create --public --source=. --push` | Verify repo URL |

## Core Quality Standards

- **Principles must be actionable** — "When X happens, do Y" not "they were wise about X"
- **Grounded** — each principle traces to a specific event with source evidence
- **Dual-use** — every principle gets both business and career applications
- **Honest** — include failures, critiques, where the hero was wrong
- **Pipeline, not list** — group principles into 3-5 sequential phases that form a thinking pipeline
- **Three-file sync** — CLAUDE.md, SKILL.md, .cursor/rules must share the same core framework
- **alwaysApply: false** for domain-specific skills (only universal coding guidelines use `true`)
- **"When NOT to Use"** section required in CLAUDE.md, SKILL.md, and .mdc

## Common Failure Modes

| Failure | Prevention |
|---------|------------|
| Flat principle list (10 items, no grouping) | Discover pipeline in Phase 3 before writing CLAUDE.md |
| Descriptive principles ("they understood X") | Gate check: "can someone apply this tomorrow?" |
| Hagiography (no failures or critiques) | Explicitly search for hero's mistakes during research |
| Missing "When NOT to Use" | Required in all three synced files |
| alwaysApply: true for domain skill | Set to false; only universal coding rules get true |
| Terminology drift across files | Grep for concept names; standardize in CONTEXT.md |
| Missing principle-to-pipeline mapping | Add to CONTEXT.md when linear numbering ≠ pipeline grouping |

## Existing Heroes

| Hero | Repo | Domain |
|------|------|--------|
| 陈平 | [chenping-human-strategy](https://github.com/1998x-stack/chenping-human-strategy) | Human nature / strategic psychology |
| 张良 | [zhangliang-grand-strategy](https://github.com/1998x-stack/zhangliang-grand-strategy) | Grand strategy / structural thinking |

## Reference Implementations

- `andrej-karpathy-skills/` — Behavioral distillation from observed failure patterns
- `musk-decision-interrogation/` — Framework distillation of thinking style into prompt structure
