# 英雄蒸馏 (Hero Distillation)

一个元框架——将卓越思考者的核心能力蒸馏为可复用的独立 GitHub 仓库。每个被蒸馏的英雄都包含：行为指南（CLAUDE.md）、可行动原则、深度分析、可加载 AI 技能和 Cursor IDE 集成——让英雄的思维模式可以被随时调用。

[English](./README.md) | 简体中文

## 解决的问题

伟大的思考者——战略家、工程师、领导者、艺术家——通过数十年的经验发展出独特的思维模型。但这些能力随他们一起死去。传记描述了他们做了什么，却不能让你**像他们一样思考**。

大多数"智慧文献"有两个致命缺陷：
- **描述性而非指令性** —— 告诉你英雄很厉害，不告诉你该怎么做
- **无法被 AI 加载** —— 不能作为一个技能来改变 AI 分析问题的方式

## 解决方案

一个结构化的蒸馏管线，提取可行动的思维模式，打包为双重用途的产物：人类可读，AI 可执行。

| 阶段 | 做什么 | 产出 |
|------|--------|------|
| **1. 研究** | 收集原始资料，识别关键决策 | 原始材料 |
| **2. 提取** | 找到第一性原理、决策链、可复用模式 | 结构化笔记 |
| **3. 撰写** | 按 TEMPLATE 填入 info.md, principles.md, CONTEXT.md, CLAUDE.md, EXAMPLES.md | 完整仓库内容 |
| **4. 打包** | 同步 CLAUDE.md → SKILL.md → .cursor/rules | AI 可加载技能 |
| **5. 发布** | `gh repo create` + push | 独立 GitHub 仓库 |

## 蒸馏框架

每个英雄都被四个问题审讯：

| 问题 | 产出 |
|------|------|
| **他看到了什么根本真理？** | 第一性原理——别人错过的基石洞察 |
| **他的关键决策链是什么？** | 2-3个他选择不同路径并承担高风险的分叉点 |
| **我明天能复用的是什么？** | 可行动原则——不是崇拜，是采用 |
| **他避开了什么陷阱？** | 反模式——常规思维错在哪里 |

## 仓库架构

```
heros-distill/                    # 本仓库——蒸馏厂
├── CLAUDE.md                     # 项目指南
├── README.md                     # 你在这里
├── TEMPLATE/                     # 新英雄仓库的起始模板
│   ├── info.md                   # 深度分析模板
│   ├── principles.md             # 可行动原则模板
│   ├── CONTEXT.md                # 领域词汇表模板
│   ├── EXAMPLES.md               # 前后对比案例模板
│   ├── CLAUDE.md                 # AI 行为指南模板
│   ├── README.md + README.zh.md  # 公开文档模板
│   ├── skills/<name>/SKILL.md    # 可加载技能模板
│   ├── .cursor/rules/<name>.mdc  # Cursor IDE 规则模板
│   └── .claude-plugin/           # 插件打包模板
│
├── andrej-karpathy-skills/       # 参考：行为蒸馏型
├── musk-decision-interrogation/  # 参考：框架蒸馏型
└── heros/                        # 进行中的蒸馏工作
    └── <name>/                   # （每个 → 独立仓库）
```

## TEMPLATE：每个英雄仓库包含什么

| 文件 | 用途 | 受众 |
|------|------|------|
| `info.md` | 深度分析：第一性原理、决策链、案例、历史评价 | 想理解思维的人 |
| `principles.md` | 可行动原则：每条附历史原型、底层逻辑、商业+职场应用 | 想应用思维的人 |
| `CONTEXT.md` | 领域词汇表：规范术语、决策框架、风格词汇 | 维护仓库的人 |
| `CLAUDE.md` | AI 行为指南：路由规则、思维管线、何时不用 | Claude Code |
| `EXAMPLES.md` | 前后对比：常规做法 vs. 英雄引导的做法 | 评估技能的人 |
| `README.md` / `README.zh.md` | 公开说明：问题、方案、安装 | 所有人 |
| `skills/<name>/SKILL.md` | 可加载技能（与 CLAUDE.md 同步） | Claude Code 插件 |
| `.cursor/rules/<name>.mdc` | Cursor IDE 规则（与 CLAUDE.md 同步） | Cursor IDE |
| `.claude-plugin/` | 插件打包文件 | 插件系统 |

**三文件同步规则**：`CLAUDE.md` ↔ `skills/<name>/SKILL.md` ↔ `.cursor/rules/<name>.mdc` 核心框架必须保持一致。

## 已蒸馏英雄

| 英雄 | 仓库 | 领域 | 核心洞察 |
|------|------|------|----------|
| 陈平 | [chenping-human-strategy](https://github.com/1998x-stack/chenping-human-strategy) | 人性谋略 | 所有行为都是利益驱动；顺应人性而非对抗人性 |

## 参考实现

两种蒸馏路径，均在本仓库作为参考：

| 参考 | 类型 | 教什么 |
|------|------|--------|
| [andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills) | 行为蒸馏 | 如何从观察到的失败模式中提取原则，转化为指令性指南 |
| [musk-decision-interrogation](https://github.com/1998x-stack/musk-decision-interrogation) | 框架蒸馏 | 如何将一种思维风格蒸馏为结构化的提示框架和路由规则 |

## 快速开始

### 蒸馏新英雄

1. 克隆本仓库：
   ```bash
   git clone https://github.com/1998x-stack/heros-distill.git
   ```

2. 复制模板：
   ```bash
   cp -r TEMPLATE/ heros/<hero-name>/
   ```

3. 按顺序填入文件：`info.md` → `principles.md` → `CONTEXT.md` → `CLAUDE.md` → `EXAMPLES.md` → `README.md`

4. 准备就绪后，创建独立仓库：
   ```bash
   cd heros/<hero-name>
   git init && git add -A && git commit -m "feat: initial distillation"
   gh repo create <hero-name> --public --source=. --push
   ```

### 使用已有英雄作为 Claude Code 技能

```bash
# 通过插件市场安装
/plugin marketplace add 1998x-stack/heros-distill
/plugin install <hero-name>

# 或项目级使用
curl -o CLAUDE.md https://raw.githubusercontent.com/1998x-stack/<hero-name>/main/CLAUDE.md
```

## 设计原则

蒸馏框架本身遵循以下规则：

1. **原则必须可行动** —— "当 X 发生时，做 Y"，而不是"他们在 X 方面很睿智"
2. **每个论断必须有依据** —— 每条原则追溯到具体历史事件和原始资料
3. **默认双重用途** —— 每条原则同时提供商业和职场应用
4. **诚实面对代价** —— 包含失败、批评和英雄错误的地方；不造神
5. **AI 可嵌入** —— CLAUDE.md 必须真正改变 AI 的思考方式，而不只是描述人类应该如何思考

## License

MIT
