# ThreadKeeper Tutor｜不断线 AI 私人导师

> 一个开源、轻量、可中断、可恢复的 AI 学习 Skill。解决：AI 回答太多、学一半想问别的问题、上一条消息被挤走、跨会话学习断片。

## 30 秒了解

- **一口一口学**：每次只教一个知识点，而不是一整份教程。
- **双层进度**：区分“讲过、读完、真正掌握”。未经确认不推进。
- **临时插问**：旁支问题不会覆盖学习主线。
- **断片恢复**：重现当前练习，不要求上滑找旧消息。
- **可迁移存档**：用纯文本快照或 JSON 状态文件跨 Agent 接力。
- **Focus Guard 专注守卫（v1.1）**：AI 等待期间减轻分心触发；离开后用一句话 + 一个微动作回到原断点。

## 项目结构

```text
threadkeeper-tutor/
├── SKILL.md                           # 核心标准 Skill（必须）
├── README.md                          # 使用与分享
├── PROMPT.md                          # 不支持 Skills 的聊天机器人版本
├── CHANGELOG.md                       # 版本记录
├── CONTRIBUTING.md                    # 贡献指南
├── PUBLISHING.md                      # GitHub 发布指南
├── assets/
│   └── learning-state.template.json   # 可选状态模板
├── examples/
│   └── conversation.md                # 学习中断/恢复示例
├── tests/
│   └── scenarios.md                   # 手动验收场景
└── LICENSE                            # MIT 开源协议
```

## 安装 / 使用

此 Skill 基于开放的 [Agent Skills 规范](https://agentskills.io/specification)。支持 Skill 的 Agent 可读取根目录 `SKILL.md`。不同平台发现 Skill 的目录不同，常见方式：

- **OpenAI Codex**：复制整个 `threadkeeper-tutor` 文件夹到项目的 `.agents/skills/`，或个人目录 `~/.agents/skills/`；在对话中提及 `$threadkeeper-tutor` 或让 Agent 自动匹配。
- **Claude Code**：复制到项目 `.claude/skills/` 或个人目录 `~/.claude/skills/`；按产品支持的方式调用。
- **VS Code / GitHub Copilot**：复制到项目 `.github/skills/`，然后在支持 Skills 的 Agent 会话中使用。
- **其他 Agent / 网页聊天**：若支持 Skills，按平台的导入方式加载 `SKILL.md`；否则复制 `PROMPT.md` 作为提示词。

这些是通用安装路径示例，不表示所有 Agent 都已验证兼容；具体调用方式取决于产品和版本。

## 先用四条指令

| 输入 | 效果 |
| --- | --- |
| `开始学习 Vue3 watch` | 开启/恢复一条主线，一次只讲一小段 |
| `插问：computed 与 watch 区别` | 简短回答，主线不变 |
| `我看完了` | 出一道检查理解的问题，不直接推进 |
| `保存进度` | 生成能带到其他 Agent 的学习快照 |
| `我回来了` | 复现断点，给一个 30 秒内能开始的最小动作 |

补充：`暂存：...`、`我断片了`、`回到主线`、`下一步`、`重讲`、`恢复进度`、`我分心了`、`暂停学习`。

## 如何真正实现跨会话记忆

本 Skill 是**行为规则，不是永久记忆服务**。纯聊天环境请在结束时输入 `保存进度`，将快照存到你能访问的笔记；下次粘贴快照并说 `恢复进度`。如果 Agent 有授权的文件访问能力，可以让它把 JSON 状态保存在个人或项目目录，随后另一个 Agent 读取同一个文件。

不要声称只安装 SKILL.md 就能自动云端同步、监测你实际读到哪行，或定时主动追踪学习：这些功能需要宿主应用的存储、界面或自动化支持。

## Focus Guard：分心后怎么回到学习主线？

如果 AI 正在生成答案时，你不自觉拿起手机刷短视频，下次只需对导师说：**`我回来了`**。

导师应该用很短的回复恢复此前主线、重现当前任务，并给一个 30 秒内能**开始**的小动作。它不会默认你已经看完上一条答案，更不能监测你的手机或 TikTok 使用情况。

## 自己部署与公开分享

1. 将整个目录上传至 GitHub 仓库（或放到现有仓库的 skills 子目录）。
2. README 首页说明应用场景、安装方式和示例，保留 MIT LICENSE。
3. 发布前按照 `tests/scenarios.md` 在目标 Agent 中实际测试，特别检查“未读完时问新问题”和“无历史恢复”的行为。
4. 公开发布时不要上传真实的个人学习快照、账号信息或敏感资料。仅分享 `assets/learning-state.template.json` 和虚构示例。

发布到 GitHub 的具体步骤见 [PUBLISHING.md](PUBLISHING.md)。

## 设计原则

**不是让 AI 记住所有消息，而是让用户永远知道自己停在哪里。**

参考：[Agent Skills 规范](https://agentskills.io/specification) · [OpenAI Skills 文档](https://learn.chatgpt.com/docs/build-skills)