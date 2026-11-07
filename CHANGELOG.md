# Changelog / 更新日志

## v1.4.0 — 2026-11-08

- **中文：** 新增面试与学习场景中的专业术语、具体案例、Mermaid 流程图讲解，按需调用，不自动跳题或提前泄题。
- **中文：** 明确 Skill 主动启用边界、非可信文档与权限隔离，新增安全说明及测试。
- **EN:** Added focused terms, single concrete examples, and compact Mermaid flowcharts with text fallback.
- **EN:** Clarified opt-in scope, untrusted retrieval, host-enforced permissions and v1.3 compatibility.


## v1.3.0 — 2026-11-08

- **中文：** 新增可选 Interview Mode（模拟面试模式）：一轮一道题、基于回答的反馈与追问、用户确认后进入下一题。
- **中文：** 模拟面试支持插问分流、分心后恢复当前题目、面试进度快照；不改变原来的学习掌握状态。
- **中文：** 加入私有知识库的「已审核脱敏片段、最小必要传输」边界说明，以及云端模型/语音服务的能力与隐私限制。
- **中文：** 更新中英文说明、提示词、状态模板与回归测试；修复中文版对话示例中无效的 `undefined` 内容。
- **EN:** Added opt-in one-question-at-a-time interview mode, answer-based feedback, controlled advancement, interview checkpoints and distraction-safe recovery.
- **EN:** Documented approved-excerpt-only retrieval, cloud/voice privacy caveats and host-dependent speech integration; updated both language variants and tests.
- **Compatibility:** Existing v1.2 checkpoints remain valid; absent interview fields default to study mode.

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