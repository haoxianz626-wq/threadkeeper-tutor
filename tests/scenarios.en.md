# Manual acceptance scenarios (English)

1. **Unread answer + new question**: Tutor teaches A; learner immediately asks unrelated B. B is parked by default and A remains unread.
2. **Explicit tangent**: Learner says "Side question: B", then "I lost my place". Tutor briefly answered B and reconstructs A without requiring scrollback.
3. **Read is not mastered**: "I've read it" triggers exactly one check, not an automatic mastery claim or new chapter.
4. **Cross-agent handoff**: Export a checkpoint from agent A, restore in agent B. Original thread, reading status, task, and parked question queue stay intact.
5. **No available history**: Learner says "Continue yesterday". Tutor cannot access old state; it asks for a checkpoint without hallucinating details.
6. **Explicit request for full guide**: Tutor honors user override instead of enforcing short replies at all costs.
7. **Focus Guard**: "I'm back" produces a neutral re-entry and one action that can be started within 30 seconds; mastery remains unchanged.
8. **Privacy**: Tutor never claims to observe TikTok, device usage, learner attention, or how far down the screen they have read.
9. **Pause/resume**: "Pause learning" prints a checkpoint; "Restore progress" in another chat reconstructs it accurately.
10. **Mid-lesson language switch**: During an unread A, "中文模式" or "English mode" changes output language only. A is still unread; task and pending questions remain unchanged.
11. **Bilingual opt-in**: "Bilingual mode" gives compact Chinese and English together; default English/Chinese modes only show one language.
12. **Cross-language command aliases**: "我看完了" must work in English output mode, and "Side question:" must work in Chinese output mode.
13. **Cross-language checkpoint**: Restore a Chinese-labeled snapshot while in English mode. Preserve actual mastery, task, and statuses; translate only display labels.
14. **No automatic persistence claims**: Without authorized storage tools, "Save progress" outputs text and does not claim a file was written.

15. **Opt-in only**: `Mock interview: frontend engineer` starts with exactly one question, no premature answer; regular study remains default.
16. **No automatic advancement**: After an answer, provide one grounded improvement and at most one follow-up; wait for `Next question` to move on.
17. **Same question after interruption**: A side question or `I'm back` preserves the current interview question; checkpoint and restore keep question state and distinct study mastery.
18. **Private KB control**: Never assume permission to open raw documents, send full DBs or reveal secrets. Only reviewed, approved minimal excerpts may be used; redaction is not a zero-leak guarantee.
19. **Voice is optional**: Without host recording/ASR/TTS, offer text. With cloud speech, do not imply spoken answers stay local.
20. **v1.2 backward compatibility**: A v1.2 checkpoint lacking `interview` defaults to study mode without resetting the original learning thread.
