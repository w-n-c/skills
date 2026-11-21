---
name: implement
description: "Implement a piece of work based on a spec or set of tickets."
disable-model-invocation: true
---

Implement the work described by the user in the spec or tickets.

## 1. Read the ticket before you read the code

Fetch the ticket from the issue tracker and state its title before starting. If the reference is ambiguous, ask.

Then read **every** `Reference:` path the ticket names, `file:line` ranges included, before writing anything. A ticket that cites `src/cart.ts:40-88` is telling you where the seam already is; skipping the reference is how an implementer invents a second seam next to the existing one.

## 2. Refuse tickets you cannot check

A ticket whose acceptance criteria cannot be checked, in a browser or in a test, is returned to the user and not guessed at. Name the criterion and the evidence that would make it checkable: a URL, a selector, a metric, an expected output.

The same rule catches contradictions. If the ticket's own "follow-up" or "out of scope" section contradicts an acceptance criterion, the ticket is **not** done even when the code matches the follow-up. Surface the conflict rather than picking a side.

## 3. One wave per context

One ticket's worth of work per context window. If the ticket is bigger than that, split it and say why, rather than carrying a half-finished seam into the next one.

Call the Skill tool with "tdd" where possible, at pre-agreed seams.

## 4. Verify with the targeted-run rule

Run the narrowest command that can fail while you work; run the full gate once at the end. The rule is documented under `docs/agents/` (this repo's copy is `docs/agents/verification.md`). If the repo documents no rule, default to: the single test file per cycle, then typecheck plus the whole suite once before reporting done.

## 5. Fail loudly when a subagent fails

If a subagent fails (**non-zero exit, empty response, stderr it should not have, or work you can verify did not land**), stop and report. The coordinator does not implement that ticket itself.

The failure is information about the environment: the model, the credentials, the tool access, the prompt. A coordinator that quietly finishes the work anyway destroys that evidence and doubles the context cost. Report which ticket, which subagent, what the failure looked like, and what you need. Then wait.

## 6. Review before you commit

Call the Skill tool with "code-review" once the work is done, and address its findings. Commit to the current branch when the review is clean.

A finding the review calls a violation or a blocker is **fixed or asked about**, never accepted and written up. "It works if you look at it this way" is a finding you did not answer: quote the rule, say why the code does not break it, or ask the user which one gives. Accepting a hard finding in the final report is how a wrong design reaches `main` with green tests around it.

A review can also be wrong in the other direction: if it calls a rule violation "tolerable", that is a prompt to check whether the rule is mechanical (then it needs a guardrail, not a verdict) or genuinely a judgement call. Say which you concluded and why.
