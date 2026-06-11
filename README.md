# 英雄蒸馏 (Hero Distillation)

A meta-framework for distilling the core capabilities of exceptional thinkers into reusable, shareable repositories. Each distilled hero becomes a standalone GitHub repo with behavioral guidelines (CLAUDE.md), actionable principles, deep analysis, a loadable AI skill, and Cursor IDE integration.

English | [简体中文](./README.zh.md)

## The Problem

Great thinkers develop unique mental models through decades of experience. Their capabilities die with them. Biographies describe what they did — they don't give you the ability to **think like them**.

Most wisdom literature is **descriptive, not prescriptive** (tells you the hero was brilliant, not what to DO) and **not AI-embeddable** (can't be loaded as a skill to change how an AI analyzes problems).

## The Solution

A structured distillation pipeline: research the hero, extract actionable principles, build a complete repo from TEMPLATE, grill for quality, publish via `gh`.

| Phase | What Happens |
|-------|-------------|
| **1. Research** | Gather primary sources, identify critical decisions and first principles |
| **2. Write Core** | info.md (deep analysis) → principles.md (actionable rules) |
| **3. Build Repo** | CONTEXT.md, CLAUDE.md, SKILL.md, .cursor/rules, EXAMPLES.md, READMEs, plugin files |
| **4. Grill** | Terminology audit, structure audit, sync audit, quality audit — fix everything |
| **5. Publish** | `git init` → `gh repo create` → push |

The framework interrogates every hero through four questions:

| Question | What It Surfaces |
|----------|-----------------|
| **What fundamental truth did they see?** | First Principles — the bedrock insight others missed |
| **What decision chain defines them?** | The 2-3 forks where they chose differently and why |
| **What can I reuse tomorrow?** | Actionable principles — not admiration, but adoption |
| **What trap did they avoid?** | The anti-pattern — what conventional wisdom gets wrong |

## Repository Architecture

```
heros-distill/
├── .claude/skills/distill-hero/   # Distillation skill + bundled TEMPLATE
│   ├── SKILL.md                   # Full pipeline with quality standards
│   └── TEMPLATE/                  # Starter kit for new hero repos (11 files)
├── CLAUDE.md                      # Project guidance
├── README.md / README.zh.md       # You are here
├── heros/                         # Work-in-progress (each → independent repo)
│   ├── 陈平/                      #   info.md, principles.md, ...
│   └── 张良/                      #   info.md, principles.md, ...
├── andrej-karpathy-skills/        # Reference: behavioral distillation
└── musk-decision-interrogation/   # Reference: framework distillation
```

## What Each Hero Repo Contains

| File | Purpose |
|------|---------|
| `info.md` | Deep analysis: first principles, decision chains, case studies, evaluations |
| `principles.md` | 8-10 actionable principles: historical prototype + logic + business + career apps |
| `CONTEXT.md` | Domain glossary: core concepts, decision framework, principle-to-pipeline mapping |
| `CLAUDE.md` | AI behavioral guidelines: pipeline, routing rule, when NOT to use |
| `EXAMPLES.md` | 3 before/after scenarios: conventional vs. hero-guided analysis |
| `skills/<name>/SKILL.md` | Loadable AI skill (synced with CLAUDE.md) |
| `.cursor/rules/<name>.mdc` | Cursor IDE rule (synced with CLAUDE.md) |
| `.claude-plugin/` | Plugin packaging |

**Three-file sync**: CLAUDE.md ↔ SKILL.md ↔ .mdc must stay identical in core framework.

## Existing Heroes

| Hero | Repo | Domain | Core Insight |
|------|------|--------|-------------|
| 陈平 (Chen Ping) | [chenping-human-strategy](https://github.com/1998x-stack/chenping-human-strategy) | 人性谋略 / Strategic Psychology | All behavior is interest-driven; exploit human nature, don't fight it |
| 张良 (Zhang Liang) | [zhangliang-grand-strategy](https://github.com/1998x-stack/zhangliang-grand-strategy) | 格局战略 / Grand Strategy | See the board before moving; deconstruct to first principles before accepting templates |

## Quick Start

### Distill a new hero

```bash
git clone https://github.com/1998x-stack/heros-distill.git
# Say "/distill-hero" or "蒸馏 <hero-name>" in Claude Code
# The skill runs the full pipeline: research → write → build → grill → publish
```

### Use an existing hero skill

```bash
# Per-project: copy CLAUDE.md
curl -o CLAUDE.md https://raw.githubusercontent.com/1998x-stack/<hero-repo>/main/CLAUDE.md

# Or install as plugin (if published to marketplace)
/plugin install <hero-name>
```

## Design Principles

1. **Actionable** — "When X happens, do Y" not "they were wise about X"
2. **Grounded** — every principle traces to a specific historical event
3. **Dual-use** — every principle gets both business AND career application
4. **Honest** — includes failures, critiques, and where the hero was wrong
5. **AI-embeddable** — CLAUDE.md must change how AI thinks, not just describe human thinking

## Reference Implementations

| Reference | Type |
|-----------|------|
| [andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills) | Behavioral distillation from observed failure patterns |
| [musk-decision-interrogation](https://github.com/1998x-stack/musk-decision-interrogation) | Framework distillation of a thinking style into prompt structure |

## License

MIT
