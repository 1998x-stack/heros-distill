# 英雄蒸馏 (Hero Distillation)

一个元框架——将卓越思考者的核心能力蒸馏为可复用的独立 GitHub 仓库。每个英雄包含：行为指南（CLAUDE.md）、可行动原则、深度分析、可加载 AI 技能和 Cursor IDE 集成。

[English](./README.md) | 简体中文

## 解决的问题

伟大的思考者通过数十年经验发展出独特思维模型，但这些能力随他们一起死去。传记描述他们做了什么，却不能让你**像他们一样思考**。

大多数智慧文献**描述性强、指令性弱**（告诉你英雄很厉害，不告诉你该怎么做），且**无法被 AI 加载**（不能作为技能改变 AI 分析问题的方式）。

## 解决方案

结构化的五阶段蒸馏管线：研究英雄 → 提取可行动原则 → 从 TEMPLATE 构建完整仓库 → Grilling 质量审计 → 发布。

| 阶段 | 做什么 |
|------|--------|
| **1. 研究** | 收集原始资料，识别关键决策和第一性原理 |
| **2. 撰写核心** | info.md（深度分析）→ principles.md（可行动原则） |
| **3. 构建仓库** | CONTEXT.md, CLAUDE.md, SKILL.md, .cursor/rules, EXAMPLES.md, README, plugin 文件 |
| **4. Grill** | 术语审计 → 结构审计 → 同步审计 → 质量审计 —— 修复一切 |
| **5. 发布** | `git init` → `gh repo create` → push |

每个英雄被四个问题审讯：

| 问题 | 产出 |
|------|------|
| **他看到了什么根本真理？** | 第一性原理——别人错过的基石洞察 |
| **他的关键决策链是什么？** | 2-3个他选择不同路径并承担高风险的分叉点 |
| **我明天能复用的是什么？** | 可行动原则——不是崇拜，是采用 |
| **他避开了什么陷阱？** | 反模式——常规思维错在哪里 |

## 仓库架构

```
heros-distill/
├── .claude/skills/distill-hero/   # 蒸馏技能 + 打包的 TEMPLATE
│   ├── SKILL.md                   # 完整管线与质量标准
│   └── TEMPLATE/                  # 新英雄仓库起始模板（11个文件）
├── CLAUDE.md                      # 项目指南
├── README.md / README.zh.md       # 你在这里
├── heros/                         # 进行中的蒸馏（每个 → 独立仓库）
│   ├── 陈平/                      #   info.md, principles.md, ...
│   └── 张良/                      #   info.md, principles.md, ...
├── andrej-karpathy-skills/        # 参考：行为蒸馏型
└── musk-decision-interrogation/   # 参考：框架蒸馏型
```

## 每个英雄仓库包含什么

| 文件 | 用途 |
|------|------|
| `info.md` | 深度分析：第一性原理、决策链、案例、历史评价 |
| `principles.md` | 8-10条可行动原则：历史原型 + 底层逻辑 + 商业应用 + 职场应用 |
| `CONTEXT.md` | 领域词汇表：核心概念、决策框架、原则到管线映射 |
| `CLAUDE.md` | AI 行为指南：管线、路由规则、何时不用 |
| `EXAMPLES.md` | 3个前后对比场景：常规做法 vs. 英雄引导分析 |
| `skills/<name>/SKILL.md` | 可加载 AI 技能（与 CLAUDE.md 同步） |
| `.cursor/rules/<name>.mdc` | Cursor IDE 规则（与 CLAUDE.md 同步） |
| `.claude-plugin/` | 插件打包 |

**三文件同步**：CLAUDE.md ↔ SKILL.md ↔ .mdc 核心框架必须一致。

## 已蒸馏英雄

| 英雄 | 仓库 | 领域 | 核心洞察 |
|------|------|------|----------|
| 陈平 | [chenping-human-strategy](https://github.com/1998x-stack/chenping-human-strategy) | 人性谋略 | 所有行为都是利益驱动；顺应人性而非对抗人性 |
| 张良 | [zhangliang-grand-strategy](https://github.com/1998x-stack/zhangliang-grand-strategy) | 格局战略 | 先看棋盘再落子；先拆解前提条件再接受模板 |

## 快速开始

### 蒸馏新英雄

```bash
git clone https://github.com/1998x-stack/heros-distill.git
# 在 Claude Code 中说 "/distill-hero" 或 "蒸馏 <英雄名>"
# 技能自动运行完整管线：研究 → 撰写 → 构建 → grill → 发布
```

### 使用已有英雄技能

```bash
# 项目级：复制 CLAUDE.md
curl -o CLAUDE.md https://raw.githubusercontent.com/1998x-stack/<hero-repo>/main/CLAUDE.md

# 或安装为插件
/plugin install <hero-name>
```

## 设计原则

1. **可行动** —— "当 X 发生时做 Y"，而不是"他们在 X 方面很睿智"
2. **有依据** —— 每条原则追溯到具体历史事件
3. **双重用途** —— 每条原则同时提供商业和职场应用
4. **诚实** —— 包含失败、批评和英雄错误的地方
5. **AI 可嵌入** —— CLAUDE.md 必须真正改变 AI 的思考方式

## 参考实现

| 参考 | 类型 |
|------|------|
| [andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills) | 从观察到的失败模式中蒸馏行为指南 |
| [musk-decision-interrogation](https://github.com/1998x-stack/musk-decision-interrogation) | 将思维风格蒸馏为结构化提示框架 |

## License

MIT
