# L3 技能索引（Skill Index）

> L3 = 从 L2 多条经验中抽象出的可复用 Skill。索引在这，实体在 `yml_C10_skills/`。

| Skill | 一句话 | 状态 | 种子经验 | 使用次数 | 迭代 |
|-------|--------|------|----------|---------|------|
| translation-workflow | 术语表 → 翻译 → README → AAR | active | ep-001 | ≥2 | 1 次 |
| paper-writing | 文献核验 → 正文 → 编译 PDF | active | ep-002 | ≥2 | 1 次 |
| benchmark-building | 定义能力 → 出题 → 打分 → 验证 | active | ep-003 | ≥2 | 1 次 |
| debug-workflow | 复现 → 定位根因 → 修 → 回归 | active | ep-003/005 | ≥3 | 2 次 |
| version-management | 命名 → 权限 → 版本记录 → 回退 | active | ep-004 | ≥2 | 1 次 |
| aar-generator | 经历 → R̂ vs R → 教训 → 改进 | active | 贯穿 | ≥8 | 2 次 |
| project-execution | 需求 → 拆解 → 执行 → 交付 | 候选 | C8 | 1 | 0（待提炼） |

**生命周期规则**：连续 3 次类似 L2 经验 → 提炼候选 Skill；手动验证一次 → active；连续 N 次不调用/效果差 → deprecated（标原因，不删除）。
