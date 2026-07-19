# Debate Framework

> 结构化辩论框架：就某一命题、事物或文档，由持正反立场的匿名专家进行基于事实和逻辑的多轮辩论。裁判（主持人）主导流程、查证数据、挑出事实错误。

## 为什么要有这个框架？

日常讨论容易陷入三个陷阱：
- **立场先行**：先有结论，再找论据
- **各说各话**：双方不在同一个维度上对话
- **无法收敛**：讨论了半天，不知道分歧到底在哪

这个框架通过**裁判制** + **回合制攻防** + **ASCII 框架图**，把发散的观点收束到结构化的分歧地图上。

## 三种输入模式

| 模式 | 示例 | 说明 |
|------|------|------|
| **概念辩论** | "AI 是否会替代人类智能？" | 抽象议题，专家基于专业知识辩论 |
| **事物辩论** | "某股票当前价位值不值得投资？" | 具体标的，裁判先拉数据简报作为共识基础 |
| **文档辩论** | 基于投决会资料的立场辩论 | 双方基于同一份文档做不同解读 |

## 快速开始

### 依赖

- Python 3.8+
- [akshare](https://github.com/akfamily/akshare)（可选，股票类辩题需要）

```bash
pip install akshare
```

### 作为 Hermes Agent Skill 使用

将本 repo 克隆到 Hermes skills 目录：

```bash
git clone https://github.com/YOUR_USERNAME/debate-framework.git ~/.hermes/skills/creative/debate
```

加载 skill：

```bash
skill_view(name='debate')
```

### 独立使用

框架本身不依赖 Hermes Agent，你可以直接阅读 `references/debate-flow.md` 了解辩论流程，手动执行。

## 辩论流程一览

```
Phase 0：裁判准备
  ├── 解析辩题
  ├── 生成框架概览
  └── 数据准备（如适用）

Phase 1：立论陈词
  ├── 正方立论
  ├── 反方立论（针对正方论点）
  └── 裁判点评 + 事实核查

Phase 2：回合制攻防（多轮）
  ├── 正方发言（回应反方 + 推进）
  ├── 反方发言（回应正方 + 推进）
  └── 裁判点评 + ASCII 框架图 + 指令菜单

Phase 3：终结与收敛
  ├── 辩论历程回顾
  ├── 事实共识表
  ├── 持续争议表
  ├── 全景框架图
  └── 裁判最终意见
```

## 核心原则

- **求真 > 求胜**：辩论的目的是澄清事实和逻辑，不是压倒对方
- **基于事实和逻辑**：论据必须有来源，推理必须可追溯
- **裁判中立**：主持人不参与立场，只管理流程和事实核查
- **每轮回应式攻防**：反方必须针对正方上一轮的论点做出回应

## 文件结构

```
debate-framework/
├── README.md                           ← 本文档
├── LICENSE                             ← MIT 许可证
├── SKILL.md                            ← Hermes Agent skill 格式
└── references/
    ├── debate-flow.md                  ← 完整辩论流程规范
    ├── data-sources.md                 ← 股票类辩题数据源指南
    └── comparative-debate-template.md  ← 同赛道竞品对比辩论模板
```

## License

MIT
