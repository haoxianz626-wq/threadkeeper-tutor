# ThreadKeeper Tutor | Never Lose Your Learning Thread

[English](README.en.md) | [简体中文](README.md)

> A free, open-source, bilingual Agent Skill for learning in tiny steps, asking tangential questions without losing your place, and recovering after distraction or chat context loss.

**v1.2.0 adds English and Chinese support.** The tutor replies in your preferred language by default. Switch at any time without resetting progress; opt in to side-by-side bilingual explanations.

## Why use it?

- **AI answers feel overwhelming.** Learn one small concept, with one practice task, per turn.
- **You think of another question before finishing the answer.** Park it or ask a brief side question, then return to the same checkpoint.
- **The AI assumes you finished reading.** Reading, assessment, and mastery are tracked separately. Nothing advances without confirmation.
- **You open short-form videos and forget your learning thread.** Say `I'm back` to see the original task and one tiny next action, without judgment.
- **You change agents or start a new chat.** Export a portable checkpoint and restore it on the next agent.

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
