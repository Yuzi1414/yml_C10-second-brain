---
name: benchmark-building
description: 构建一个可复现、能区分「校准质量/能力」的测评基准：定义能力 → 出题 → 打分 → 合成画像验证 → 真实模型测试。
---

# benchmark-building

## What
一条「把模糊的测评需求变成可跑 benchmark」的流程。核心价值：指标必须真能区分好坏，而不是算出个漂亮但没区分度的数字。

## When to Use
- 要评估 AI 的某项能力（校准、元认知、推理、知识）。
- 需要「可复现 + 可证明区分度」的测评，而非一次性评测。

## Input
- 要测的能力定义 + 题目数量 + 打分维度。
- 是否有真实模型可用（API key / 本地 ollama）。

## Steps
1. 定义能力与区分维度（如：校准质量 vs 自我意识）。
2. 出题（64 题量级起，纯 stdlib 可复现）。
3. 打分器（scorer），统一字段名，`--seed 0` 保证可复现。
4. 合成画像验证：先造 calibrated / overconfident / underconfident / blind 四档画像，确认 ECE/AUROC/弃答增益能区分。
5. 跑真实模型（前沿模型），把结果如实写进 README。
6. reliability 证据（多 seed 稳定度 / 构念效度 / 区分效度）。

## Tools
- LLM（出题/打分）、本地运行时（ollama / API）、bash、write_file。

## Output
- benchmark 目录（README + 源码 + 数据 + 结果）+ 合成画像结果 + 真实模型结果。

## 使用与迭代记录
- 使用次数：2（C9 MetaCog-Bench 主流程；C10 复盘时复用其方法）。
- 迭代 v1→v2：v1 只跑合成画像就交差；v2 认清「真实模型测试是硬要求」，补 `--real` 模式 + 本地 ollama qwen2.5。
- 淘汰标记：无。
