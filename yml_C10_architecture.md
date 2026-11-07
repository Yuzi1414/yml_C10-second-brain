# yml_C10_architecture.md — 系统架构说明

> C10 目标：把 C1–C9 沉淀的能力，变成一个**可持续进化的第二大脑**。
> 本文档说明五层架构 + 每个设计决策的「为什么」。

---

## 0. 一句话定位

一个人 + 一个运行良好的 Agent 系统 = 一个**不遗忘、持续进化、能力可累积**的超级个体。
这个系统不是「一个 AI 应用」，而是我未来十年的能力基础设施。

---

## 1. 五层架构总览

```
┌──────────────────────────┐
│  L5 Interface   Markdown 驱动 + 对话入口   │
├──────────────────────────┤
│  L4 Tool/Access LLM · Git · 脚本 · 浏览器    │
├──────────────────────────┤
│  L3 Agent Loop  KSTAR 循环（K→S→T→Â→A→R→ΔR）│
├──────────────────────────┤
│  L2 Skill System 可复用行动计划（skill.md）   │
├──────────────────────────┤
│  L1 Memory       KSTAR 四层记忆（L1–L4）      │
└──────────────────────────┘
```

---

## 2. Layer 1：Memory（KSTAR 四层记忆）

四层都在，每一层都可工作：

| 层 | 存什么 | 我的实现 | 落点 |
|----|--------|----------|------|
| L1 原始输入 | 笔记/灵感/对话 | 随手记 Markdown | `memory/L1_raw/` |
| L2 KSTAR 经验 | 结构化 S→T→A→R | 每次任务后写 | `memory/L2_episodes/` |
| L3 Skill | 可复用能力 | skill.md 格式 + 生命周期 | `yml_C10_skills/` |
| L4 Identity | 工具/角色/价值观 | 配置 + 原则 | `config/identity.md`、`config/tools.md` |

**关键转化链（这是记忆系统的灵魂）**：
```
L1 记笔记 → 结构化 → L2 KSTAR 经验 → 抽象 → L3 Skill → 执行 → L4 调用完成任务
```

**设计决策**：选「最简方案」——纯 Markdown + 文件夹，不用 SQLite/向量库。
理由：① 我目前单机使用、数据量在百条级，Markdown 可 grep 可 diff 可版本化，检索成本低；
② 天然兼容 Git，可回滚可迁移；③ 符合「拿来说明」——Obsidian 文件夹结构 + Claude Code skill 格式的混合。
唯一代价是跨文件关联靠人工索引（`memory/L3_index.md`），数据量破千条后再升级 SQLite，不提前过度设计。

---

## 3. Layer 2：Skill System（技能系统）

- **格式**：统一 skill.md（frontmatter `name`/`description`/`status` + What/When/Input/Steps/Tools/Output）。
- **生命周期**：`L2 经验 → 候选 Skill → 手动验证 → 上线(active) → 优化 → 可能淘汰(deprecated)`。
- **≥5 个真实 Skill**（全部来自 C1–C9 真实工作，非凑数）：
  1. `translation-workflow` ← C1 翻译项目
  2. `paper-writing` ← C2 AI4Math 论文
  3. `benchmark-building` ← C9 MetaCog-Bench
  4. `debug-workflow` ← C9 KeyError 定位 + 本次 C10 runtime payload bug
  5. `version-management` ← C6 文件命名/权限/版本恢复
  6. `aar-generator` ← 贯穿 C1–C9 的 AAR 复盘

每个 Skill 含「使用记录」+「最近效果」+「≥1 次迭代改进」，见各 skill 文件。

---

## 4. Layer 3：Agent Loop（KSTAR 认知循环）

完整流程见 `AGENT.md` 第 2 节。这里只强调三个落地要点：

1. **R̂ 必须写下来**——不写预测就没有 ΔR，没有 ΔR 就没有学习信号，循环就断在「做完」而非「变强」。
2. **ΔR 驱动进化**：ΔR 大 → 改 Skill/补知识；连续 ΔR 大 → 淘汰或重构 Skill。
3. **最简实现也成立**：无需代码，Markdown 记 S→T→Â→R̂ → 做完记 R 和 ΔR 即可。关键是「养成循环习惯」。

---

## 5. Layer 4：Tool / Access System（工具层）

公式 **Action = Plan × Access Token × Energy**。我的工具清单见 `config/tools.md`，核心是：

- LLM：CogSeed 对话（Claude/DeepSeek 等）+ 本地 ollama（qwen2.5，C9 装过）
- 代码/脚本：Node/Python、Claude Code 类脚本、runtime.js（EduSeed 提交链路）
- 版本控制：Git + GitHub（Yuzi1414）
- 知识管理：Markdown 文件夹（本系统载体）
- 通讯：飞书（C6 版本管理协作）

**设计决策**：只列 3–5 个核心工具 + 清晰调用方式，不做 20 个工具的空架子。当前真正高频的是「LLM + Git + 脚本」，其余按需启用。

---

## 6. Layer 5：Interface（交互层）

选 **Markdown 驱动（🟢 最简）** 作为主入口：文件夹 + 模板 + 对话。
- 每次把 `AGENT.md` + 相关 Skill + 相关记忆喂给 LLM，即一次 Agent Loop 执行。
- 升级路径：数据量上来后加 CLI（脚本批量跑 Skill）；Chat UI/Voice 暂缓——先让系统「跑起来、用起来」，界面是后话。

---

## 7. 三个必须体现的原则

### 原则 1：拿来主义
不零设计，参考 Obsidian（文件夹+双链）、Claude Code Skill（skill.md 格式）、PARA（四层分类）、LangChain（Agent+Tool 模式），各自拿了什么/改了什么见 `yml_C10_拿来说明.md`。

### 原则 2：自进化
- 从经验生成 Skill（连续 3 次类似做法 → 抽象）
- 优化已有 Skill（ΔR 持续偏大 → 改 Steps/Tools）
- 淘汰无效 Skill（连续 N 次不调用 → deprecated）
- Skill 组合（经常一起调用的两个 → macro-skill）

### 原则 3：长期性
数据可积累（全落 memory/ + logs/）、系统可扩展（加 Skill/工具不动骨架）、可持续使用（Elite20 结束后仍是我日常工具 = 最高验证）。

---

## 8. 与 C1–C9 的沉淀关系

| 来源 | 沉淀进 C10 的什么 |
|------|-------------------|
| C1 翻译 | L2 翻译经验 + L3 `translation-workflow` |
| C2 论文 | L2 写作/文献经验 + L3 `paper-writing` |
| C9 基准 | L2 大量 KSTAR 经验 + L3 `benchmark-building` + `debug-workflow` |
| C6 版本管理 | L4 工具层 + L3 `version-management` |
| C8 项目执行 | L2 项目执行经验 + L3 `project-execution`（候选） |
| 贯穿全程 | L3 `aar-generator` |

C10 的 Skill 库不零写——C1–C9 已积累足够素材，本系统做的是「结构化整理 + 补齐生命周期」。

---

## 9. 目录结构（即系统本体）

```
yml_C10-second-brain/
├── AGENT.md              # Agent 主配置（循环 + 调用规则）
├── yml_C10_architecture.md   # 本文件
├── config/
│   ├── identity.md       # L4 我是谁/原则
│   └── tools.md          # L4 工具清单
├── memory/
│   ├── L1_raw/           # L1 原始输入
│   ├── L2_episodes/      # L2 KSTAR 经验
│   └── L3_index.md       # L3 技能索引
├── yml_C10_skills/       # L3 Skill 库（≥5 个）
├── yml_C10_usage_log.md  # 真实使用记录（含 ΔR）
├── yml_C10_AAR.md        # 系统级 AAR
├── yml_C10_AI日志.md     # AI 使用记录
├── yml_C10_拿来说明.md    # 参考来源
└── yml_C10_demo.md       # 一次完整 KSTAR 循环演示（文字录屏）
```
