---
name: distill-hero
description: >
  Distill any exceptional thinker into a complete, reusable GitHub repository with AI-loadable skills.
  Use whenever the user mentions distilling a hero, extracting someone's thinking patterns, building a hero repo,
  or wanting to learn from a specific thinker's approach. Handles the full pipeline: research, write info.md and principles.md,
  build full repo from TEMPLATE, grill iteratively, publish via gh. Triggers on Chinese phrases like 蒸馏XX, 提取XX的能力,
  学习XX的思维, 构建XX仓库, and English phrases like distill X, extract X's thinking, what would X do, how did X think about Y.
  If a user names a historical figure, thinker, strategist, or leader and wants to understand their methodology, activate.
---

# Hero Distillation

Turn a thinker's core capabilities into a complete, reusable GitHub repository — behavioral guidelines (CLAUDE.md), actionable principles (principles.md), deep analysis (info.md), domain glossary (CONTEXT.md), before/after examples (EXAMPLES.md), AI-loadable skill (SKILL.md), Cursor rules, plugin packaging, and bilingual README.

## The Pipeline

Follow these phases in order. Each phase produces artifacts the next depends on. Within a phase, parallelize independent work. Between phases, verify before proceeding.

### Phase 1: Research

**Why first:** You cannot distill what you don't understand. The biggest quality killer is writing before you've found the hero's actual thinking system.

- Web-search primary sources in the hero's original language (writings, speeches, biographies, historical records)
- Web-search secondary analysis (scholarly commentary, critical evaluations)
- For complex heroes, spawn a research subagent for deep multi-source investigation. The subagent should return structured notes, not prose.
- Identify: 3-5 critical decisions or signature moves, the hero's first principles (what fundamental truths did they see that others missed?), their anti-pattern (what conventional wisdom did they reject?)
- If the hero is part of a known pair or system (e.g., 张良+陈平, Jobs+Wozniak), research the other member too — the contrast sharpens the analysis

**Output:** Structured research notes. Do NOT write any deliverable files yet.

**Gate check before proceeding:** Can you state the hero's 3-5 first principles in one sentence each? Can you name 3 critical decision forks? If not, research more.

### Phase 2: Write Core Documents

**Why this order:** info.md discovers the system. principles.md extracts actionable rules from it. You cannot write good principles from scattered research — you need the synthesized understanding that writing info.md forces.

#### info.md — Write First

Follow this structure. Adapt section numbering to the hero's cultural context:

```
# HERO_NAME：<one-line core insight>

<2-3 paragraph overview: who, what domain, what made them exceptional>

## Core Insights / First Principles  (一、核心洞察)
3-5 insights. Each: declarative truth + evidence from hero's life + why non-obvious.

## Critical Decision Chains  (二、关键决策链)
3-6 decision forks. Each fork:
- Background & constraints (what was at stake)
- Conventional approach (what everyone else did — analogical thinking)
- HERO's choice (what they did differently — first principles)
- Why they bet on it (what made them sure enough to take the risk)
- Result (quantified if possible)

## Case Studies  (三、经典案例深度解析)
3-5 signature cases. Each: the story + what pattern it reveals + what makes it brilliant + the transferable lesson.

## Historical Evaluation  (四、历史评价)
BOTH praise AND critique. Include the hero's own self-assessment if available. Include a comparison to a peer if illuminating (张良 vs 诸葛亮, Karpathy vs Musk).

## Synthesis & Modern Application  (五、总结与现代启示)
Synthesis table (core logic / method / highest expression / ultimate goal) + applications across 4-5 domains.
```

**Quality bar:** Every insight traces to a specific event with source evidence. Decision chains show WHY, not just WHAT. Failures included — no hagiography. The hero's thinking is captured as a SYSTEM.

#### principles.md — Write Second (derives from info.md)

8-10 principles. Number them P1 through P10. Each principle:

```
## 原则N / Principle N：NAME——one-line summary

**Core definition**：2-3 sentences in universal terms

**Historical prototype**：2-3 specific examples from the hero's life

**Why it works**：the human nature, system property, or fundamental truth exploited

**Modern business application**：3 specific, copyable scenarios

**Modern career application**：3 specific, copyable scenarios
```

**Quality bar:** Every principle is ACTIONABLE ("When X, do Y" not "they were wise about X"). Every principle is GROUNDED (traces to a specific event). Every principle gets BOTH business AND career applications. Principles form a coherent system — not a random list.

**Gate check before proceeding:** Read the 10 principles aloud. Can someone apply each one tomorrow without knowing the hero's biography? If a principle requires knowing who the hero was to use it, rewrite it.

### Phase 3: Discover the Pipeline — Then Build from TEMPLATE

**Why this matters:** The single biggest quality failure in both reference distillations was presenting 10 flat principles. The grilling on 陈平 fixed this by restructuring around a 5-step decision framework. The grilling on 张良 fixed this by restructuring around a 4-phase pipeline. **Never ship flat principles.**

#### Step 3a: Discover the Natural Grouping

Look at the 10 principles and ask:
- Which principles answer "what should I see BEFORE acting?" → These form the OBSERVATION phase
- Which principles answer "how should I analyze the situation?" → These form the ANALYSIS phase  
- Which principles answer "when should I act?" → These form the TIMING phase
- Which principles answer "how should I execute?" → These form the ACTION phase
- Is there a meta-principle that governs all others? → This becomes the PHILOSOPHY overlay

The result should be 3-5 phases that form a logical sequence — a thinking pipeline, not a menu. Name each phase as a verb phrase (e.g., "See the Board" not "Strategic Vision").

Create the mapping: P1→Phase X, P2→Phase Y, etc. This mapping will go into CONTEXT.md.

#### Step 3b: Create All Files

Use `TEMPLATE/` as the structural reference. Create files in this order:

1. **Directory structure**: `skills/<skill-name>/`, `.cursor/rules/`, `.claude-plugin/`, `.gitignore`

2. **CONTEXT.md**: Domain glossary with:
   - 10-15 core concepts with precise, canonical definitions
   - Decision framework table: Phase | Question | Method | Principles
   - **Principle-to-pipeline mapping table**: P# | Principle Name | Pipeline Phase | Logic (why it belongs there)
   - Style vocabulary (8-12 canonical terms)
   - File synchronization rule

3. **CLAUDE.md**: Behavioral guidelines with:
   - Routing rule (when to apply, when to skip — be specific about exclusion criteria)
   - Tradeoff statement (what this mode costs)
   - Core framework: the pipeline as the spine, principles grouped under each phase
   - Each principle rendered as a behavioral instruction ("Do X" not "Principle N says X")
   - Meta-principle if applicable
   - **"When NOT to Use" section** — specific exclusion criteria
   - Style & tone
   - Success criteria (observable outcomes that indicate the guidelines are working)

4. **SKILL.md**: Sync from CLAUDE.md — same pipeline, same principle groupings, same routing rule. Full detail, not compressed. Include YAML frontmatter with name + description.

5. **.cursor/rules/<name>.mdc**: Sync from CLAUDE.md — same pipeline, compressed for IDE context. **Set `alwaysApply: false`** for domain-specific skills. Only universally-applicable guidelines (like coding behavior) should use `alwaysApply: true`.

6. **EXAMPLES.md**: 3 full before/after scenarios:
   - Each: Context → ❌ Conventional Thinking (with specific problems listed) → ✅ Hero-Guided Analysis → Principles applied (list which ones)
   - Cover different domains (business strategy, career decision, competitive dynamics)
   - Anti-patterns summary table at the end

7. **README.md + README.zh.md**: Bilingual. Problem → Solution → Pipeline overview → Install → How to know it's working → When NOT to use

8. **.claude-plugin/plugin.json + marketplace.json**: Fill in actual metadata

**Three-file sync rule:** CLAUDE.md, SKILL.md, and .cursor/rules/<name>.mdc MUST contain the same pipeline structure, principle groupings, routing rule, and "When NOT to Use". Verbosity differs (SKILL.md = full, .mdc = compressed) — that's expected and correct.

### Phase 4: Grill Iteratively

**Why this matters:** Every distillation so far needed 4-6 fixes after the initial write. The grilling is not optional — it's where the quality comes from.

Run through this checklist systematically. Fix every issue found. Commit after each batch.

#### 4a. Terminology Audit

- List every term used in CLAUDE.md's principle names and phase descriptions
- Verify each has a precise definition in CONTEXT.md's Core Concepts table
- Check for naming drift: is the same concept called different things in info.md vs principles.md vs CONTEXT.md? (e.g., "对比伤害" vs "对比落差")
- Standardize on the most precise term

#### 4b. Structure Audit

- Verify the pipeline phases map correctly to the principles in principles.md
- If principles are numbered P1-P10 linearly but grouped differently in the pipeline, **add a mapping table to CONTEXT.md** (Principle-to-Pipeline Mapping)
- Verify the pipeline is a logical sequence, not a random grouping — each phase should flow into the next

#### 4c. Sync Audit

- Diff CLAUDE.md ↔ SKILL.md ↔ .mdc
- Core framework (pipeline structure, principle groupings, routing rule, "When NOT to Use") must be identical
- Verbosity differences are acceptable and expected

#### 4d. Completeness Audit

- info.md: all 5 sections present? Decision chains show WHY? Failures included?
- CONTEXT.md: decision framework table? Principle-to-pipeline mapping? File sync rule?
- CLAUDE.md: routing rule? tradeoff? "When NOT to Use"? success criteria?
- .mdc: `alwaysApply: false`? (should be false for domain skills)

#### 4e. Quality Audit

- Are principles ACTIONABLE ("When X, do Y") or merely descriptive ("they understood X")?
- Are principles GROUNDED in specific historical events?
- Does every principle have BOTH business AND career applications?
- Is the pipeline discoverable from the principles, or does it feel grafted on?

#### 4f. Cross-Reference Audit

- If the hero is part of a pair (张良+陈平), are cross-references accurate and fair to both sides?
- Do external references (other repos, historical figures) point to real resources?

### Phase 5: Publish

```bash
cd heros/<hero-name>
unset GIT_DIR && unset GIT_WORK_TREE
/usr/bin/git init
git branch -m main
git add -A
git commit -m "feat: initial distillation of <HERO_NAME>"
gh repo create <repo-name> --public \
  --description "<one-line describing the capability>" \
  --source=. --remote=origin --push
```

Verify the repo is accessible. Confirm the URL with the user.

## Common Failure Modes — Prevent These

These were discovered across real distillations. Check for them proactively.

| Failure | Symptom | Prevention |
|---------|---------|------------|
| **Flat principle list** | 10 principles with no grouping | Always discover the pipeline in Phase 3a before writing CLAUDE.md |
| **Descriptive principles** | "They understood human nature" instead of "Map interests before acting" | Gate check at end of Phase 2: can someone apply each principle tomorrow? |
| **Hagiography** | No failures or critiques in info.md | Explicitly search for the hero's mistakes and critics during Phase 1 |
| **Missing "When NOT to Use"** | CLAUDE.md has no exclusion criteria | Required field in Phase 3b step 3 |
| **alwaysApply: true for domain skill** | .mdc triggers on every conversation | Required check in Phase 4d |
| **Terminology drift** | Same concept named differently across files | Phase 4a: grep for concept names across all files |
| **Missing mapping table** | Principles numbered P1-P10 but pipeline groups them P10+P3+P8 | Phase 4b: if numbering ≠ grouping, add mapping table |
| **No business+career dual-use** | Principles only have historical examples | Required field in Phase 2 principles.md template |
| **README has "When NOT to Use" but CLAUDE.md doesn't** | Exclusion criteria only in public docs | Phase 4c: verify in all three synced files |

## Skill Naming Convention

Derive the skill name from the hero's name + domain:
- 陈平 → `chenping-human-strategy`
- 张良 → `zhangliang-grand-strategy`
- Karpathy → `karpathy-coding-guidelines`
- Pattern: `<romanized-name>-<domain-keyword>`

Use lowercase, hyphen-separated English. The skill name is used for: repo name, plugin name, cursor rule filename, SKILL.md frontmatter `name` field.

## Hero Type Detection

Adapt the output format based on the hero's origin:

| Hero Type | Section Headers | Evidence Style | Principles Language |
|-----------|----------------|----------------|---------------------|
| Chinese historical | 一、二、三... numbering | Classical texts (史记, 汉书, etc.) | Chinese principle names with English subtitles |
| Modern / Western | Standard Markdown headers | Books, talks, interviews, biographies | English principle names |
| Contemporary practitioner | Standard Markdown headers | Talks, blog posts, podcasts, code/output | English principle names, practical bias |

## When the User Names a Capability Without a Hero

1. Ask: "Which thinker embodies this capability? Is there someone whose approach you admire?"
2. If they have someone → proceed
3. If they don't → suggest 2-3 heroes known for that capability with one-line explanations, let them choose
4. Never pick a hero without confirmation

## When the User Names a Complementary Pair

If the user names a hero who is part of a known pair (张良+陈平, Jobs+Wozniak, etc.):
1. Distill the requested hero first (full pipeline)
2. Mention the other member in the README's cross-reference section
3. Offer to distill the other member
4. The two repos should reference each other

## Bundled Resources

- `TEMPLATE/` — Complete starter kit with all template files and inline guidance. Use this as the structural reference for every new hero repo.

## Reference Files (in this repo)

- `CLAUDE.md` — Project-level distillation methodology
- `heros/陈平/` — Reference implementation: tactical human-nature strategy (grilled)
- `heros/张良/` — Reference implementation: grand strategic vision (grilled)

## External Repositories

- [chenping-human-strategy](https://github.com/1998x-stack/chenping-human-strategy)
- [zhangliang-grand-strategy](https://github.com/1998x-stack/zhangliang-grand-strategy)
