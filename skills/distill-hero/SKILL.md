---
name: distill-hero
description: Distill exceptional thinkers into reusable GitHub repositories. Use when the user mentions distilling a hero, extracting someone's capabilities, building a hero repo, or says they want to "learn from X's thinking." Covers the full pipeline: research → write info.md + principles.md → build full repo from TEMPLATE → grill iteratively → publish via gh. Also triggers on Chinese phrases like "蒸馏XX", "提取XX的能力", "学习XX的思维", "构建XX仓库."
---

# Hero Distillation

Turn a thinker's core capabilities into a complete, reusable GitHub repository — behavioral guidelines, actionable principles, deep analysis, AI-loadable skill, Cursor rules, plugin packaging.

## The Pipeline

Follow these phases in order. Never skip a phase. Never batch phases together — each produces artifacts the next depends on.

### Phase 1: Research

**Goal:** Gather enough primary and secondary source material to understand the hero's thinking system.

Do this even if the user already provided some information — their request usually surfaces what they want, not the full source material needed.

- Web-search for primary sources (writings, speeches, biographies, historical records) in the hero's original language
- Web-search for secondary analysis (scholarly commentary, critical evaluations, modern interpretations)
- If the hero is complex, spawn a research subagent for deeper multi-source investigation
- Identify: 3-5 critical decisions or signature moves, the hero's first principles, what they saw that others missed

**Output:** Raw research notes. Do NOT write files yet.

### Phase 2: Write Core Documents

**Goal:** Produce `info.md` and `principles.md` — the two foundation documents everything else derives from.

Write `info.md` first, then `principles.md`. Never write them in parallel — principles.md extracts from info.md.

#### info.md structure

Follow this exact structure (see `TEMPLATE/info.md` for the full template):

```
# HERO_NAME：<one-line core insight>

<2-3 paragraph overview>

## 一、核心洞察 / 第一性原理
3-5 insights. Each: declarative truth + evidence from hero's life + why it's non-obvious.

## 二、关键决策链
3-6 critical decision forks. Each fork:
- 背景与约束 (what was at stake)
- 主流做法 (conventional approach — analogical thinking)
- HERO的选择 (what they did differently — first principles)
- 为什么敢冒险 (why they were sure enough to bet on it)
- 结果 (quantified outcome)

## 三、经典案例深度解析
3-5 signature cases. Each: the story + the insight + what makes it brilliant + the transferable lesson.

## 四、历史评价
Both praise AND critique. Include the hero's own self-assessment if available.

## 五、总结与现代启示
Synthesis table + modern applications across 4-5 domains.
```

**Quality bar for info.md:**
- Every insight traces to a specific event with source evidence
- Decision chains show WHY, not just WHAT
- Failures and critiques are included — no hagiography
- The hero's thinking is captured as a SYSTEM, not scattered observations

#### principles.md structure

8-10 principles. Each follows this exact structure:

```
## 原则N：NAME原则——one-line summary

**核心定义**：2-3 sentences in universal terms

**HERO原型**：2-3 specific historical examples

**底层逻辑**：why this works — the human nature, system property, or fundamental truth

**现代商业应用**：
- 3 specific, copyable business scenarios

**现代职场应用**：
- 3 specific, copyable career scenarios
```

**Quality bar for principles.md:**
- Each principle is ACTIONABLE — "When X happens, do Y" not "they were wise about X"
- Each principle is GROUNDED — traces to a specific historical event
- Dual-use by default — every principle gets both business AND career application
- Principles form a coherent system, not a random list

### Phase 3: Build Full Repo from TEMPLATE

**Goal:** Create all remaining files following the TEMPLATE structure.

Use `TEMPLATE/` in the heros-distill repo as the source. Create these files in order:

1. **Directory setup:** Copy TEMPLATE structure to `heros/<hero-name>/`
   ```
   skills/<skill-name>/SKILL.md
   .cursor/rules/<skill-name>.mdc
   .claude-plugin/plugin.json
   .claude-plugin/marketplace.json
   .gitignore
   ```

2. **CONTEXT.md** — Domain glossary. Extract from info.md and principles.md:
   - 10-15 core concepts with precise definitions
   - Decision framework table mapping principles to phases
   - Principle-to-pipeline mapping (if principles are numbered linearly but structured in phases)
   - Style vocabulary (8-12 canonical terms)
   - File synchronization rule

3. **CLAUDE.md** — Behavioral guidelines for AI:
   - Routing rule: when to apply, when to skip
   - Tradeoff statement
   - Core framework: group principles into a pipeline (3-5 phases), not a flat list
   - Each principle under its phase as a behavioral rule
   - Meta-principle if applicable
   - "When NOT to Use" section
   - Style & tone
   - Success criteria

4. **SKILL.md** — Sync from CLAUDE.md (same framework, full detail)

5. **.cursor/rules/<name>.mdc** — Sync from CLAUDE.md (compressed for IDE context). Set `alwaysApply: false` for domain-specific skills (not universally applicable like coding guidelines).

6. **EXAMPLES.md** — 3 full before/after scenarios:
   - Each: Context → ❌ Conventional Thinking → Problems → ✅ Hero-Guided Analysis → Principles applied
   - Cover different domains (business strategy, career decision, competitive dynamics, etc.)
   - Anti-patterns summary table at the end

7. **README.md + README.zh.md** — Bilingual documentation:
   - Problem → Solution → Pipeline/Principles overview → Install instructions → How to know it's working

8. **.claude-plugin/plugin.json + marketplace.json** — Fill in metadata

**Three-file sync rule:** CLAUDE.md, SKILL.md, and .cursor/rules/<name>.mdc MUST contain the same core framework (pipeline structure, principle groupings, routing rule, "When NOT to Use").

### Phase 4: Grill Iteratively

**Goal:** Find and fix gaps, inconsistencies, and fuzzy language before publishing.

Run through this checklist systematically:

1. **Terminology audit:** Are there any terms used in CLAUDE.md that lack definitions in CONTEXT.md? Are any concepts named differently across files? Fix all inconsistencies.

2. **Structure audit:** Do the phases/pipeline in CLAUDE.md map correctly to the principles in principles.md? If principles are numbered 1-10 but the pipeline groups them differently, add a mapping table.

3. **Sync audit:** Diff CLAUDE.md ↔ SKILL.md ↔ .mdc. Core framework must be identical. Verbosity differences are acceptable (SKILL.md = full, .mdc = compressed).

4. **Missing sections:** Does info.md have all 5 sections? Does CONTEXT.md have the decision framework + mapping table? Does CLAUDE.md have routing rule + tradeoff + When NOT to Use?

5. **Quality check:** Are principles actionable (not just descriptive)? Are they grounded in specific events? Do they have both business AND career applications?

6. **Cross-reference check:** If the hero is part of a pair or system (like 张良 + 陈平), are the cross-references accurate?

Fix every issue found. Commit after each batch of fixes.

### Phase 5: Publish

```bash
cd heros/<hero-name>
unset GIT_DIR && unset GIT_WORK_TREE
/usr/bin/git init
git branch -m main
git add -A
git commit -m "feat: initial distillation of <HERO_NAME>"
gh repo create <repo-name> --public \
  --description "<one-line>" \
  --source=. --remote=origin --push
```

Verify the repo is accessible at the returned URL.

## Skill Naming Convention

Derive the skill name from the hero's name + domain:
- 陈平 → `chenping-human-strategy` (domain: human nature / strategic psychology)
- 张良 → `zhangliang-grand-strategy` (domain: grand strategic vision)
- Pattern: `<romanized-name>-<domain-keyword>`

Use lowercase, hyphen-separated English. The skill name is used for the repo name, plugin name, cursor rule filename, and SKILL.md frontmatter.

## When the User Only Names a Capability (Not a Specific Hero)

If the user says something like "I want strategic thinking ability" without naming a hero:

1. Ask: "Which thinker embodies this capability? Is there someone whose approach you admire?"
2. If they have someone in mind → proceed with that hero
3. If they don't → suggest 2-3 heroes known for that capability, let them choose
4. Never pick a hero without the user's confirmation

## Reference Files

- `TEMPLATE/` — Complete starter kit with templates and inline guidance
- `CLAUDE.md` — Project-level distillation methodology
- `heros/陈平/` — Reference implementation: tactical human-nature strategy
- `heros/张良/` — Reference implementation: grand strategic vision
