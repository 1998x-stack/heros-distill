# 英雄蒸馏 (Hero Distillation)

A meta-framework for distilling the core capabilities of exceptional thinkers into reusable, shareable repositories. Each distilled hero becomes a standalone GitHub repo containing behavioral guidelines (CLAUDE.md), actionable principles, deep analysis, a loadable AI skill, and Cursor IDE integration — so the hero's thinking patterns can be invoked on demand.

English | [简体中文](./README.zh.md)

## The Problem

Great thinkers — strategists, engineers, leaders, artists — develop unique mental models through decades of experience. But their capabilities die with them. Biographies describe what they did; they don't give you the ability to **think like them**.

Most "wisdom literature" has two fatal flaws:
- **Descriptive, not prescriptive** — tells you the hero was brilliant, doesn't tell you what to DO
- **Not AI-embeddable** — can't be loaded as a skill that changes how an AI analyzes problems

## The Solution

A structured distillation pipeline that extracts actionable thinking patterns and packages them as dual-use artifacts: readable by humans, executable by AI.

| Phase | What Happens | Output |
|-------|-------------|--------|
| **1. Research** | Gather primary sources, identify critical decisions | Raw material |
| **2. Extract** | Find first principles, decision chains, reusable patterns | Structured notes |
| **3. Write** | Fill TEMPLATE — info.md, principles.md, CONTEXT.md, CLAUDE.md, EXAMPLES.md | Complete repo content |
| **4. Package** | Sync CLAUDE.md → SKILL.md → .cursor/rules | AI-loadable skill |
| **5. Publish** | `gh repo create` + push | Standalone GitHub repo |

## The Distillation Framework

Every hero is interrogated through four questions:

| Question | What It Surfaces |
|----------|-----------------|
| **What fundamental truth did they see?** | First Principles — the bedrock insight others missed |
| **What decision chain defines them?** | The 2-3 forks where they chose differently and why |
| **What can I reuse tomorrow?** | Actionable principles — not admiration, but adoption |
| **What trap did they avoid?** | The anti-pattern — what conventional wisdom gets wrong |

## Repository Architecture

```
heros-distill/                    # This repo — the distillery
├── CLAUDE.md                     # Project guidance for Claude Code
├── README.md                     # You are here
├── TEMPLATE/                     # Starter kit for new hero repos
│   ├── info.md                   # Deep analysis template
│   ├── principles.md             # Actionable principles template
│   ├── CONTEXT.md                # Domain glossary template
│   ├── EXAMPLES.md               # Before/after examples template
│   ├── CLAUDE.md                 # AI behavioral guidelines template
│   ├── README.md + README.zh.md  # Public documentation template
│   ├── skills/<name>/SKILL.md    # Loadable AI skill template
│   ├── .cursor/rules/<name>.mdc  # Cursor IDE rule template
│   └── .claude-plugin/           # Plugin packaging template
│
├── andrej-karpathy-skills/       # Reference: behavioral distillation
├── musk-decision-interrogation/  # Reference: framework distillation
└── heros/                        # Work-in-progress distillations
    └── <name>/                   # (each → independent gh repo)
```

## The TEMPLATE: What Each Hero Repo Contains

Every distilled hero ships with these files:

| File | Purpose | Audience |
|------|---------|----------|
| `info.md` | Deep analysis: first principles, decision chains, case studies, historical evaluations | Humans who want to understand the thinking |
| `principles.md` | Actionable principles: each with historical prototype, underlying logic, modern business + career application | Humans who want to apply the thinking |
| `CONTEXT.md` | Domain glossary: canonical terms, decision framework, style vocabulary | Writers maintaining the repo |
| `CLAUDE.md` | AI behavioral guidelines: routing rule, thinking pipeline, when NOT to use | Claude Code |
| `EXAMPLES.md` | Before/after scenarios: conventional approach vs. hero-guided approach | Humans evaluating the skill |
| `README.md` / `README.zh.md` | Public explanation: problem, solution, install | Everyone |
| `skills/<name>/SKILL.md` | Loadable AI skill (synced with CLAUDE.md) | Claude Code plugin |
| `.cursor/rules/<name>.mdc` | Cursor IDE project rule (synced with CLAUDE.md) | Cursor IDE |
| `.claude-plugin/` | Plugin packaging for marketplace distribution | Plugin system |

**Three-file sync rule**: `CLAUDE.md` ↔ `skills/<name>/SKILL.md` ↔ `.cursor/rules/<name>.mdc` must stay identical in their core framework.

## Existing Heroes

| Hero | Repo | Domain | Core Insight |
|------|------|--------|-------------|
| 陈平 (Chen Ping) | [chenping-human-strategy](https://github.com/1998x-stack/chenping-human-strategy) | 人性谋略 / Strategic Psychology | All human behavior is interest-driven; exploit weaknesses, don't fight them |

## Reference Implementations

Two approaches to distillation, both in this repo as reference:

| Reference | Type | What It Teaches |
|-----------|------|----------------|
| [andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills) | Behavioral distillation | How to extract principles from observed failure patterns and turn them into prescriptive guidelines |
| [musk-decision-interrogation](https://github.com/1998x-stack/musk-decision-interrogation) | Framework distillation | How to distill a thinking style into a structured prompt framework with routing rules |

## Quick Start

### Distill a new hero

1. Clone this repo:
   ```bash
   git clone https://github.com/1998x-stack/heros-distill.git
   ```

2. Copy the template:
   ```bash
   cp -r TEMPLATE/ heros/<hero-name>/
   ```

3. Fill in the files in order: `info.md` → `principles.md` → `CONTEXT.md` → `CLAUDE.md` → `EXAMPLES.md` → `README.md`

4. When ready, create the standalone repo:
   ```bash
   cd heros/<hero-name>
   git init && git add -A && git commit -m "feat: initial distillation"
   gh repo create <hero-name> --public --source=. --push
   ```

### Use an existing hero as a Claude Code skill

```bash
# Install via plugin marketplace
/plugin marketplace add 1998x-stack/heros-distill
/plugin install <hero-name>

# Or use per-project
curl -o CLAUDE.md https://raw.githubusercontent.com/1998x-stack/<hero-name>/main/CLAUDE.md
```

## Design Principles

The distillation framework itself follows these rules:

1. **Principles must be actionable** — "When X happens, do Y" not "they were wise about X"
2. **Every claim must be grounded** — each principle traces to a specific historical event with source evidence
3. **Dual-use by default** — every principle gets both business AND career application
4. **Honest about costs** — include failures, critiques, and where the hero was wrong; no hagiography
5. **AI-embeddable** — the CLAUDE.md must actually change how an AI thinks, not just describe how a human should think

## License

MIT
