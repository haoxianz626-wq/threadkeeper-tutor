# ThreadKeeper Tutor｜不断线 AI 私人导师

[简体中文](README.md) | [English](README.en.md)

> 开源中英双语 AI 私人学习导师 Skill：少量教学、保持学习主线、临时插问、断片恢复与可迁移存档。

**v1.4.0：新增术语、实例和 Mermaid 流程图辅助讲解。** 继续支持中文 / English，可在同一学习进度中切换语言；输入 `双语模式` 才会同时输出简短中英文内容。

## 解决什么问题？

- **AI 输出太多：** 一次只学一个最小概念，一次最多一个任务。
- **看一半就提问：** `插问` 简答后返回主线，`暂存` 记录疑问。
- **还没看完就被推进：** 区分讲解、阅读、理解检测、已掌握。
- **刷短视频后断片：** `我回来了` 恢复原断点，给一个 30 秒内能开始的动作。
- **跨 Agent 容易遗忘：** `保存进度` 导出可复制快照；有授权文件访问时可保存私人 JSON。
- **跨语言使用：** `English mode` / `中文模式` / `双语模式` 切换，不重置学习进度。

## v1.3.0：逐题模拟面试（可选）

输入 `模拟面试：Vue3 前端工程师`，导师每次只问一道题；回答后给出简短反馈和最多一道针对性追问，只有输入 `下一题` 才进入下一题。`我断片了` 或 `我回来了` 会重现**当前题目**；`结束面试` 输出可恢复的面试存档。

语音面试需要宿主应用另外接入麦克风、ASR/TTS；本 Skill 本身不录音。若使用云端模型或语音服务，**发送给它的题目、作答及已放行知识片段可能离开本机**。本地原始资料不可仅靠 Skill 指令保护，应结合权限隔离、人工审核和最小必要传输。详见 [SKILL.md](SKILL.md)。
## v1.4.0 面试辅助讲解与安全性

输入 `术语解释`、`举个例子` 或 `画流程图`（英文 `Explain terms`、`Give an example`、`Show a flowchart`）即可按需解释当前题目。默认每次只展示一种辅助：1～3 个专业术语、一个具体示例或 3～6 节点的 Mermaid 图及文字说明；**不主动提前泄题**，不改变题目、学习进度或断点。

仓库的 Skill 和提示词只在用户主动启用时适用；外部文档与知识库是待处理数据，不能作为提升权限或执行工具的指令。详见 [安全边界](SECURITY.md)。

## 安装

遵循 [Agent Skills 规范](https://agentskills.io/specification)，将**整个仓库文件夹**复制至兼容 Agent 的 Skills 目录，确保根目录存在 `SKILL.md`：

| 环境 | 常见安装位置 |
| --- | --- |
| OpenAI Codex | `.agents/skills/threadkeeper-tutor/` 或 `~/.agents/skills/threadkeeper-tutor/` |
| Claude Code | `.claude/skills/threadkeeper-tutor/` 或 `~/.claude/skills/threadkeeper-tutor/` |
| GitHub Copilot Agent | `.github/skills/threadkeeper-tutor/`（支持 Skills 时） |
| 普通聊天 AI | 复制 [PROMPT.md](PROMPT.md) 或 [PROMPT.en.md](PROMPT.en.md) |

平台能力与路径可能随版本变化，使用时以对应 Agent 的文档为准；本仓库未声称所有 Agent 均经过端到端验证。

## 五条常用指令

| 中文 | English | 效果 |
| --- | --- | --- |
| `开始学习 Vue3 watch` | `Start learning Vue3 watch` | 开始或恢复学习 |
| `我看完了` | `I've read it` | 只进行一题检测，不自动跳下一节 |
| `插问：computed 是什么？` | `Side question: What is computed?` | 简答并保留原学习步骤 |
| `我回来了` | `I'm back` | 无责恢复断点 |
| `保存进度` | `Save progress` | 导出可迁移快照 |
| `模拟面试：Vue3` | `Mock interview: Vue3` | 一次一题，不自动跳题 |

其他命令：`暂存 / Park`、`回到主线 / Back to main topic`、`我断片了 / I lost my place`、`下一步 / Next step`、`暂停学习 / Pause learning`、`恢复进度 / Restore progress`。

## 语言行为

- **自动模式：** 优先用户明确设置，否则使用最近一条实质性消息的语言，或延续现有学习语言。
- **手动切换：** 输入 `中文模式` / `English mode`，仅改变回复语言。
- **双语输出：** 输入 `双语模式` / `Bilingual mode`；此模式下仍保持简短，避免再次造成信息过载。
- **跨语言快照：** 同一状态 JSON 保存 `language` 和 `language_mode`；不因切换语言而修改已验证的掌握进度。

## 仓库结构

```text
threadkeeper-tutor/
├── SKILL.md                         # 双语指令与核心规则
├── README.md / README.en.md         # 中文 / English 介绍
├── PROMPT.md / PROMPT.en.md         # 中文 / English 独立提示词
├── CHANGELOG.md                     # 双语更新日志
├── CONTRIBUTING.md / CONTRIBUTING.en.md
├── PUBLISHING.md / PUBLISHING.en.md
├── assets/
│   ├── learning-state.template.json
│   └── learning-state.en.template.json
├── examples/
│   ├── conversation.md
│   └── conversation.en.md
├── tests/
│   ├── scenarios.md
│   └── scenarios.en.md
└── LICENSE
```

## 跨会话保存与隐私

**Skill 是教学行为规范，不是数据库。** 没有存储权限的 Agent 只能给出文本快照，不能自动跨会话同步。请自行保留快照，下次输入 `恢复进度`；有授权的写文件能力时才可保存私有 `learning-state.json`。请勿将真实学习记录、私人信息或 API 密钥提交至公共仓库。

这不是手机监测工具：AI 无法检测用户读到哪一行，也不能判断是否正在刷 TikTok。

## 示例、测试与贡献

- [中文对话示例](examples/conversation.md) · [English examples](examples/conversation.en.md)
- [中文测试场景](tests/scenarios.md) · [English test scenarios](tests/scenarios.en.md)
- [贡献说明](CONTRIBUTING.md) · [Contributing (EN)](CONTRIBUTING.en.md)
- [发布说明](PUBLISHING.md) · [Publishing (EN)](PUBLISHING.en.md)

**设计原则：不是让 AI 记住所有对话，而是让学习者永远知道自己停在哪里。**

License: [MIT](LICENSE).
