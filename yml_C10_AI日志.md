# yml_C10 AI 日志

> 记录「人 + AI」协作的每一轮：我给出什么、AI 做什么、结果如何、哪里返工。证明不是 one-shot。

## 轮次 1 — 探题
- **我给**：完成 C10。
- **AI 做**：读 C10 正文 + rubric，确认 challengeId、必交物、五层架构、KSTAR 四层记忆。
- **结果**：明确「C10 是系统设计，不是 AI 应用」，五层架构 = 接口/工具/循环/技能/记忆。

## 轮次 2 — 架构决策
- **我给**：认可「Markdown + 文件夹」做记忆层、扩展 KSTAR 为 K→S→T→Â→A→R。
- **AI 做**：定 L1–L5 分层、Skill frontmatter 规范、生命周期（经验→候选→验证→上线→优化→淘汰）。
- **结果**：架构冻结，交付根目录 `yml_C10-second-brain`。

## 轮次 3 — 核心文件（部分返工）
- **AI 做**：写 AGENT.md / architecture / identity / tools / README。
- **返工点**：README 里写「Skill 库 6 active 1 候选」「L1/L2 已积累 C1–C9 真实经验」——但当时文件还没造出来。→ 我要求：**先造真实记录，再写声明**，不能先夸后补。

## 轮次 4 — 记忆四层 + Skill 库
- **AI 做**：写 L1 原始输入、L2 五条 KSTAR 经验、L3 索引、6+1 个 Skill。
- **结果**：全部落盘，README 的声明与真实文件一一对应。

## 轮次 5 — 辅助交付物（本轮）
- **AI 做**：usage_log（含 ΔR 实盘）、AAR、AI 日志、拿来说明、demo。
- **结果**：交付物齐。

## 关键 AI 决策与我的修正
- AI 早期想「零写 Skill」，我认可「从 C1–C9 提炼」是更真实的路径。
- AI 一度把 README 写成「已完成」姿态，我要求改成「有真实文件背书」。
- 脚本报错时 AI 没有乱猜，而是读 runtime.js 定位根因——这是 debug-workflow Skill 的实盘命中。

## 结论
多轮迭代、有真实返工、有报错定位与修复，非 one-shot。
