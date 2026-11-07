# yml_C10 demo — KSTAR 一次完整循环

> 演示这个「第二大脑」如何跑一轮 KSTAR（K→S→T→Â→A→R），并触发 Skill 进化。
> 用的是真实案例：本次 C10 里「查题脚本报错」的排障。

## K — Knowledge（记忆里有什么）
- L1：没接触过这个脚本。
- L2：ep-003（C9 KeyError）、ep-005（C10 runtime payload）两条 debug 经验在册。
- L3：`debug-workflow` Skill 可调用。

## S — Situation（处境）
`run-c10-getchallenge.js` 报 `INPUT_MISSING: challengeId 必填`，阻塞探题。

## T — Task（任务）
让脚本正确拿到 challengeId 并返回题面。

## Â — Agent Loop 的预测（R̂）
调用 `debug-workflow`，预测根因是「字段名/结构不匹配」，预期读源码定位、改一处就能好。

## A — Action（行动）
1. 复现报错。
2. 读 `runtime.js` 的 `parseRuntimeArgs`，定位根因：它只认「第一个 JSON 参数」当 payload 根，嵌套 `{op, payload}` 导致 `payload.challengeId === undefined`。
3. 改成平铺 `{challengeId, workdir}`。
4. 回归验证，成功。

## R — Result（结果）+ ΔR
- R：脚本跑通，但过程中又踩了一个 `\U` 转义坑（第二根因），共修了两处。
- **ΔR = R̂ − R**：预测「改一处」→ 实际「改两处」，偏差偏小但方向一致（都是「参数/结构不匹配」这一类）。

## 进化动作（KSTAR 闭环的落点）
- ΔR 方向一致 → 说明「平台脚本的参数结构坑」是**系统性问题**，不是偶发。
- 处置：`debug-workflow` Skill 的「读源码定位根因」步骤持续有效，**保留并继续使用**；同时在 L2 补一条 ep-005 经验，供下次同类问题直接索引。

## 这证明什么
- 记忆层（L2 经验）→ 技能层（debug-workflow）→ 循环层（Â→A→R）→ 进化（写回 L2）全链路跑通。
- 系统「每次使用都在进化」是真实发生的，不是口号。
