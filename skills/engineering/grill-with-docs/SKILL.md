---
name: grill-with-docs
description: A relentless interview to sharpen a plan or design, which also creates docs (ADR's and glossary) as we go.
disable-model-invocation: true
---

Call the Skill tool twice, for "grilling" and "domain-modeling".

## Composition rules

Grilling owns the conversation; domain-modeling owns the artifacts. On timing,
grilling wins: **write nothing until the user confirms the specific decision it
records** (an ADR, a glossary term, a sketch line). "Resolved" in domain-modeling
means *the user just confirmed it*, not *the agent inferred it*.

**Notarize every write.** In the same reply as the write, list exactly what was
added or changed — the terms and the decision paragraphs — so the user sees what
got locked in before the session ends.
