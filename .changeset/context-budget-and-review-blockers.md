---
"mattpocock-skills": patch
---

`implement` now reads every `Reference:` path in the ticket before coding, returns tickets whose acceptance criteria cannot be checked in a browser or a test, refuses to mark a ticket done while a follow-up contradicts an acceptance criterion, keeps one wave per context, verifies with the targeted-run rule from `docs/agents/` and the full gate once at the end, and stops and reports after a subagent failure instead of implementing the ticket in the coordinator.

`code-review` now treats a missing or contradicted numeric spec value as a blocker that sorts first in the Spec report, runs the repo's smoke or browser check before the two axes so "implemented but wrong" findings are verified against something running, and ignores what a pre-commit hook already enforces.
