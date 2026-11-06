# Changelog / 更新日志

## v1.2.0 — 2026-11-07

- **EN:** Added English README, standalone tutor prompt, examples, tests, contribution and publishing docs.
- **EN:** Made `SKILL.md` bilingual with Chinese/English command aliases, automatic language selection and explicit language switching without resetting progress.
- **EN:** Added a matching English JSON learning-state template and `language_mode` field; cross-language checkpoint semantics remain stable.
- **中文：** 增加英文 README、独立提示词、对话示例、测试、贡献及发布说明。
- **中文：** 核心 Skill 加入中英指令对照、默认语言识别与手动切换；切换语言不清空主线或掌握状态。
- **中文：** 新增英文 JSON 学习状态模板和 `language_mode`；跨语言恢复保持原学习断点。

## v1.1.0 — 2026-11-07

- 新增 Focus Guard 专注守卫：分心后无责返回、30 秒可启动的微动作。
- 新增 `我分心了`、`我回来了` 和 `暂停学习` 指令。
- 扩充状态模板、对话示例及回归测试。
- 明确无法监测手机使用情况、不可擅自标记已读。

## v1.0.0

- 极简逐步教学；主线与临时问题分流；阅读与掌握状态分离；可迁移学习快照。