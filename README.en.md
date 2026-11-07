# ThreadKeeper Tutor | Never Lose Your Learning Thread

[English](README.en.md) | [简体中文](README.md)

> A free, open-source, bilingual Agent Skill for learning in tiny steps, asking tangential questions without losing your place, and recovering after distraction or chat context loss.

**v1.4.0 adds on-demand technical terms, concrete examples and Mermaid flowcharts to interview practice**, retaining English / Chinese support. Switch languages without resetting your learning thread; opt in to paired bilingual explanations.

## Why use it?

- **AI answers feel overwhelming.** Learn one small concept, with one practice task, per turn.
- **You think of another question before finishing the answer.** Park it or ask a brief side question, then return to the same checkpoint.
- **The AI assumes you finished reading.** Reading, assessment, and mastery are tracked separately. Nothing advances without confirmation.
- **You open short-form videos and forget your learning thread.** Say `I'm back` to see the original task and one tiny next action, without judgment.
- **You change agents or start a new chat.** Export a portable checkpoint and restore it on the next agent.

## v1.3.0: Mock Interview Mode (opt-in)

Enter `Mock interview: Vue3 frontend engineer`. The tutor asks one question at a time, waits for your answer, then gives brief evidence-based feedback and at most one targeted follow-up. Say `Next question` to advance. `I lost my place` or `I'm back` reconstructs **the same question**; `End interview` produces a portable checkpoint.

Voice interviews require a host app with microphone input, speech recognition and optional speech synthesis. The Skill itself does not record audio. When using cloud models or cloud speech, selected excerpts and your prompts/answers may leave your device. Raw private files must remain outside the cloud agent's scope; redaction and Skill instructions alone do not guarantee confidentiality.
## v1.4.0 Explanation aids and security

Use `Explain terms` / `术语解释`, `Give an example` / `举个例子`, or `Show a flowchart` / `画流程图`. Each request stays on the same question and returns only the requested aid: 1–3 definitions, one concrete scenario, or a small Mermaid diagram with a textual fallback. The tutor does not volunteer spoilers before an interview answer; explicitly requested help does not count as mastery.

This is an opt-in Skill. Retrieved documents are untrusted data, not authorization to perform tool actions. See [SECURITY.md](SECURITY.md).

## Install

This repository follows the [Agent Skills specification](https://agentskills.io/specification). Copy the **entire folder** into a Skills location supported by your agent, keeping the root `SKILL.md` file:

| Agent | Typical Skills location |
| --- | --- |
| OpenAI Codex | `.agents/skills/threadkeeper-tutor/` or `~/.agents/skills/threadkeeper-tutor/` |
| Claude Code | `.claude/skills/threadkeeper-tutor/` or `~/.claude/skills/threadkeeper-tutor/` |
| GitHub Copilot Agent | `.github/skills/threadkeeper-tutor/` (where Skills are supported) |
| General chatbots | Paste [PROMPT.en.md](PROMPT.en.md) (or [PROMPT.md](PROMPT.md) for Chinese) |

Exact paths and activation behavior vary by platform and version. These are guidance, not claims of full compatibility testing.

## Get started

```text
Start learning Vue3 watch.
I've read it.
Side question: What is computed?
I lost my place.
Save progress.
```

| English command | 中文命令 | What it does |
| --- | --- | --- |
| `Start learning [topic]` | `开始学习 [主题]` | Start/resume your main thread |
| `I've read it` | `我看完了` | Ask one check; don't assume mastery |
| `Side question: ...` | `插问：...` | Answer briefly, preserve your place |
| `Park: ...` | `暂存：...` | Queue a tangent without answering |
| `I'm back` / `I lost my place` | `我回来了` / `我断片了` | Recover the original step |
| `Save progress` / `Restore progress` | `保存进度` / `恢复进度` | Move a checkpoint between agents |
| `English mode` / `Bilingual mode` | `中文模式` / `双语模式` | Change output language, not progress |
| `Mock interview: Vue3` | `模拟面试：Vue3` | One question at a time, with recovery |

Also supported: `Next step`, `Pause learning`, `Explain again`, and `Switch topic: ...`.

## Language behavior

**Auto:** follow the learner's explicit preference, or the most recent substantive message's language. **English mode / 中文模式:** switch response language without clearing your thread, learning status, unanswered questions, or last task. **Bilingual mode / 双语模式:** use short Chinese and English explanations together only when requested, while retaining low-output limits.

The neutral JSON keys are identical in both templates: [Chinese template](assets/learning-state.template.json) and [English template](assets/learning-state.en.template.json). They contain `language` and `language_mode` to support portable recovery.

## Project files

| File | Purpose |
| --- | --- |
| [SKILL.md](SKILL.md) | Canonical bilingual Skill and equivalent command mapping |
| [PROMPT.en.md](PROMPT.en.md), [PROMPT.md](PROMPT.md) | Standalone prompts for agents without Skills |
| [examples/conversation.en.md](examples/conversation.en.md), [examples/conversation.md](examples/conversation.md) | Illustrative interruption/recovery dialogs |
| [tests/scenarios.en.md](tests/scenarios.en.md), [tests/scenarios.md](tests/scenarios.md) | Manual acceptance tests |
| [CONTRIBUTING.en.md](CONTRIBUTING.en.md), [CONTRIBUTING.md](CONTRIBUTING.md) | Contribution guidance |
| [PUBLISHING.en.md](PUBLISHING.en.md), [PUBLISHING.md](PUBLISHING.md) | Publishing and release guidance |

## Persistence, safety, and privacy

**An Agent Skill is not a persistent memory service.** In ordinary chat, `Save progress` prints a checkpoint you can copy. To truly write a private `learning-state.json`, your agent needs explicit filesystem or storage permission. This repository does not monitor phones, TikTok activity, reading positions, or attention. Never commit real personal learning states, secrets, or private conversations to a public repository.

## Contributing

Read [CONTRIBUTING.en.md](CONTRIBUTING.en.md), test changes against both languages, and keep examples fictional and de-identified.

**The goal is not for AI to remember every message. The goal is for learners to know exactly where to resume.**

License: [MIT](LICENSE).
