# yml_C10 拿来说明

> 诚实交代：这个系统里哪些是「直接拿来/参考」、哪些是「自己做的」。避免把借鉴说成原创。

## 拿来 / 参考（直接借用或借鉴的）
| 概念/方法 | 来源 | 我做了什么 |
|-----------|------|-----------|
| KSTAR 循环（Situation/Task/Action/Result） | 课程挑战通用的复盘框架（C1–C9 一直用） | 扩展成 K→S→T→Â→A→R，加「预测 R̂ 与实际 R 的偏差 ΔR」 |
| KSTAR 四层记忆（L1 输入→L2 经验→L3 Skill→L4 调用） | 课程对「记忆系统」的约定框架 | 落地为「L1_raw / L2_episodes / L3_index + Skill 库」的具体目录 |
| Skill 的 frontmatter 规范（name/description + What/When/Input/Steps/Tools/Output） | 课程对 Skill 格式的约定 | 严格照此格式写每个 Skill，并加「使用与迭代记录」节 |
| 五层架构（Interface/Tool/Agent Loop/Skill/Memory） | 课程对「Agent 系统」的层模型 | 映射到本系统：L5 接口 / L4 工具 / L3 循环 / L2 技能 / L1 记忆 |
| debug-workflow 的「复现→定位根因→单点修→回归」 | 通用软件工程方法 | 用 C9 KeyError、C10 runtime bug 两次真实案例验证并沉淀 |

## 自己做的（原创部分）
1. **ΔR 进化机制**：把 KSTAR 的 R 拆成 R̂（预测）与 R（实际），用偏差大小/方向触发 Skill 更新或淘汰——这是本系统的核心原创点。
2. **Skill 库的「真实种子」**：7 个 Skill 全部从 C1–C9 我自己的真实经验提炼，不是抄模板。
3. **usage_log 的实盘记录**：把「每次调用 Skill 的 R̂ vs R」记成日志，让「每次使用都在进化」可被审计。
4. **Action = Plan × Access Token × Energy 公式**：本系统对「执行力」的自定义拆解。

## 边界声明
- 本系统是「纯 Markdown + 文件夹」实现，无代码依赖，这是课程明确允许的方式，也是我主动选的轻量方案。
- 记忆层的内容全部来自我真实做过的事（C1–C9 + C10 自身），未伪造任何数据。
