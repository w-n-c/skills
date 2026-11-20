---
"mattpocock-skills": patch
---

`implement-spec` now states that subagents start read-only, so every subagent that has to save files — exploration, implementer, merger, fix-up — must be launched with write access. Previously the only hint was step 2's "ensure the exploration subagent can save files", which a wave of implementer subagents launched without write access would not read as an instruction.
