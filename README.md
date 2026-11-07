# yml 的第二大脑（C10 Build Your Own Agent）

> 一个 Markdown 驱动、KSTAR 循环、可自进化的个人 Agent 系统。
> 把 C1–C9 沉淀的能力，变成一个「不遗忘、持续进化」的长期基础设施。

## 是什么

不是「一个 AI 应用」，而是四件事的合一：

| 它是什么 | 它做什么 |
|----------|---------|
| 知识系统 | 记住学过的、做过的、失败过的（L1/L2） |
| 执行系统 | 把重复任务变成可调用的 Skill（L3） |
| 决策系统 | 用积累的经验辅助判断（KSTAR 循环） |
| 进化系统 | 每次使用通过 ΔR 变强，而非原地踏步 |

## 五层架构

L5 Interface（Markdown 驱动）→ L4 Tool/Access → L3 Agent Loop（KSTAR）→ L2 Skill System → L1 Memory（KSTAR 四层）。
详见 `yml_C10_architecture.md`。

## 怎么用（最小闭环）

1. 把 `AGENT.md` + 相关 Skill + 相关记忆喂给 LLM。
2. 走一遍 KSTAR 循环，**先写下 R̂**。
3. 执行，记录 R 和 ΔR。
4. 写 L2 经验；ΔR 大 → 回改 Skill。

## 文件地图

- `AGENT.md` — 主配置（循环 + 调用规则）
- `yml_C10_architecture.md` — 五层架构 + 设计决策
- `config/` — L4 Identity + Tools
- `memory/` — L1 原始输入、L2 KSTAR 经验、L3 技能索引
- `yml_C10_skills/` — ≥5 个真实 Skill（含使用/迭代记录）
- `yml_C10_usage_log.md` — 真实使用记录（含 ΔR）
- `yml_C10_AAR.md` — 系统级反思
- `yml_C10_AI日志.md` — AI 使用记录
- `yml_C10_拿来说明.md` — 参考来源
- `yml_C10_demo.md` — 一次完整 KSTAR 循环演示

## 状态

- Skill 库：6 个 active，1 个候选
- 记忆：L1/L2 已积累 C1–C9 真实经验
- 版本：见 `logs/`（待 Git 化后由 git log 承载）
