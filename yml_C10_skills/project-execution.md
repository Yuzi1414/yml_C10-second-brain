---
name: project-execution
description: 把一个真实项目目标拆成可验收交付物，按依赖顺序执行、交付、收尾复盘（C8 选题 B 的种子经验）。
status: candidate
---

# project-execution

## What
一条「把模糊目标拆成可执行、可验收的交付物链」的流程。仍在候选期，尚未在多种项目类型上验证通用性。

## When to Use（待验证）
- 一个「选题 → 提案 → 开发 → 演示 → 复盘」的完整真实项目。

## Input
- 项目目标 + 约束 + 交付清单。

## Steps（草案）
1. 需求拆解：目标 → 可验收交付物清单。
2. 排依赖：哪些必须先做，哪些可并行。
3. 执行：按依赖顺序做，边做边记录。
4. 演示：可运行 demo + 自测全绿。
5. 收尾：AAR + 交付清单核对。

## Tools
- LLM、bash、write_file、Git。

## Output
- 项目仓库 + 提案 + demo + AAR + 交付清单核对。

## 使用与迭代记录
- 使用次数：1（C8「企业本体 Agent 系统」）。
- 状态：candidate —— 只在「本体 Agent 系统」一种项目上验证过，再攒 2 条同类经验后转 active。
- 淘汰标记：无。
