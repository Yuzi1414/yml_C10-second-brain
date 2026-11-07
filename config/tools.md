# L4 Tools — 工具清单（单一事实源）

公式：**Action = Plan × Access Token × Energy**（Plan=Skill 告诉我做什么，Access Token=我能调什么，Energy=实际投入的执行力）。

| 类别 | 工具 | 用途 | 状态 |
|------|------|------|------|
| LLM | CogSeed 对话（Claude/DeepSeek 等） | 推理、生成、分析、执行 Agent Loop | 主用 |
| LLM | 本地 ollama + qwen2.5 | C9 真实模型测试（离线、免 API） | 按需 |
| 代码/脚本 | Node.js / Python | 跑 Skill 脚本、数据处理、自动化 | 主用 |
| 代码/脚本 | EduSeed runtime.js（submit-project 等） | 挑战提交/查分/查题链路 | 按需 |
| 版本控制 | Git + GitHub（Yuzi1414） | Skill 存储、项目协作、版本回退 | 主用 |
| 知识管理 | Markdown 文件夹 | 本系统载体（L1–L4） | 主用 |
| 通讯 | 飞书（Feishu） | C6 版本管理协作、通知 | 按需 |
| 浏览器/API | 网页搜索 + 抓取 | 调研 Skill 的信息输入 | 按需 |

**调用约定**：
- 新增/删除工具 → 改本文件（不散落在别处）。
- 工具对应的操作步骤写进具体 Skill 的 `Tools` 字段，不在本文件展开。
