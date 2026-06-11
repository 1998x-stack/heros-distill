# CLAUDE.md

This file provides guidance to Claude Code when working with code in this repository.

## Project: 英雄蒸馏 (Hero Distillation)

A meta-framework for distilling the core capabilities of exceptional thinkers (heroes) into reusable, shareable GitHub repositories. Each distilled hero becomes a standalone repo containing behavioral guidelines, actionable principles, and a loadable AI skill — so the hero's thinking patterns can be invoked on demand.

**Distillation skill**: `.claude/skills/distill-hero/` with bundled `TEMPLATE/`. Invoke via `/distill-hero` or by saying "蒸馏XX".

Reference implementations: `andrej-karpathy-skills/` and `musk-decision-interrogation/`. Distilled heroes: `heros/陈平/`, `heros/张良/`.

## Repository Architecture

```
heros-distill/                    # This repo — the distillery
  CLAUDE.md                       # Project guidance
  README.md + README.zh.md        # Public documentation
  .claude/skills/distill-hero/    # Distillation skill (loadable)
    SKILL.md                      # Pipeline + quality standards
    TEMPLATE/                     # Starter kit for new hero repos
      info.md, principles.md, CONTEXT.md, EXAMPLES.md
      CLAUDE.md, README.md, README.zh.md
      skills/<name>/SKILL.md
      .cursor/rules/<name>.mdc
      .claude-plugin/
  heros/                          # Distilled heroes (each → independent gh repo)
    <name>/
      info.md, principles.md, CONTEXT.md, CLAUDE.md
      EXAMPLES.md, README.md, README.zh.md
      skills/, .cursor/rules/, .claude-plugin/
  andrej-karpathy-skills/         # Reference: behavioral distillation
  musk-decision-interrogation/    # Reference: framework distillation
```

## Distillation Workflow

When asked to distill a hero, follow this pipeline:

### Phase 1: Research
- Gather primary sources (writings, speeches, biographies, decisions)
- Identify the hero's domain and what makes them exceptional
- Find 3-5 critical decision points or signature moves
- Read `TEMPLATE/` files to understand target output shape

### Phase 2: Extract Patterns
- What **first principles** did they discover or operate from?
- What **decision chain** defines their signature approach? (2-3 critical forks)
- What did they see that **everyone else missed**?
- What **anti-patterns** did they reject?

### Phase 3: Write Distillation

Create files in this order:

1. **`info.md`** — Deep analysis. Structure:
   - Core philosophy / first principles (with source evidence)
   - Decision chain: critical forks with rationale
   - Key cases / signature moves (story + analysis)
   - How their thinking differs from conventional wisdom
   - Historical evaluations (both praise and critique)

2. **`principles.md`** — Actionable principles. Each principle:
   - Name + one-line definition
   - Historical prototype (what the hero did)
   - Underlying logic (why it works — the human nature or system property)
   - Modern application (business + career, concrete and copyable)

3. **`CONTEXT.md`** — Domain glossary of the hero's conceptual terms

4. **`CLAUDE.md`** — Behavioral guidelines that make Claude embody the hero's thinking. Must include when to apply (routing rule) and style/tone.

5. **`EXAMPLES.md`** — Before/after examples showing conventional thinking vs. hero-guided thinking

6. **`README.md`** + `README.zh.md` — Public explanation: problem, solution, install

### Phase 4: Package
- Write `skills/<name>/SKILL.md` (keep in sync with CLAUDE.md)
- Write `.cursor/rules/<name>.mdc` (keep in sync with CLAUDE.md)
- Write `.claude-plugin/plugin.json` and `marketplace.json`

### Phase 5: Publish
```bash
gh repo create <hero-name> --public --description "<one-line>"
# Push TEMPLATE content customized for this hero
```

## Core Distillation Framework

For any hero, answer these four questions. If you can't, you haven't understood them yet:

| Question | What It Surfaces |
|----------|-----------------|
| **What fundamental truth did they see?** | First Principles — the bedrock insight others missed |
| **What decision chain defines them?** | The 2-3 forks where they chose differently and why |
| **What can I reuse tomorrow?** | Actionable principles — not admiration, but adoption |
| **What trap did they avoid?** | The anti-pattern — what conventional wisdom gets wrong |

## Writing Standards

### Principles must be:
- **Actionable** — "When X happens, do Y" not "they were wise about X"
- **Grounded** — Each principle traces to a specific historical event
- **Dual-use** — Every principle gets both business AND career application
- **Honest** — Include failures, costs, and limits; don't hagiographize

### info.md must be:
- **Evidence-based** — Quote sources directly, cite chapter/verse
- **Analytical** — Not chronological biography; extract patterns from events
- **Candid** — Include missteps, critiques, and where the hero was wrong

## File Synchronization Rule

Three files contain the core framework and MUST stay in sync within each hero repo:
1. `CLAUDE.md` — root instruction file
2. `.cursor/rules/<name>.mdc` — Cursor project rule
3. `skills/<name>/SKILL.md` — loadable skill

When changing principles, update all three.

## Existing Heroes

| Hero | Domain | Core Insight |
|------|--------|-------------|
| 陈平 (Chen Ping) | 人性谋略 / Strategic Psychology | All human behavior is interest-driven; exploit weaknesses, don't fight them |

## Reference Templates

- **andrej-karpathy-skills**: Four principles (Think Before Coding, Simplicity First, Surgical Changes, Goal-Driven Execution) derived from observed LLM failure patterns. Shows how to distill behavioral observations into prescriptive guidelines.
- **musk-decision-interrogation**: Two-question framework (First Principles Decision Chain + STAR Hardest Problem) that forces deep first-person analysis. Shows how to distill a thinking style into a prompt structure.
