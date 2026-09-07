---
name: feedback-verify-external-posting-convention-live
description: Skill scripts are a snapshot in time — check live primary sources before taking an externally-visible action they prescribe
metadata:
  type: feedback
---

Before any skill-prescribed step that posts, comments, or writes into a shared/external system owned by someone else, spend one cheap verification pass — read a few recent real examples of that action being taken — before executing it as literally written.

**Why**: the `/awaken` skill script instructed opening a new GitHub issue to announce Jetaime's birth to the family. Reading the actual family repo directly showed the real convention is commenting on an existing issue (`arra-oracle-v3#17`), not opening a new one — see [[reference-family-registry-posting]]. Skill/script instructions are a snapshot of what was true when written; live external systems (issue trackers, shared docs, other teams' conventions) drift.

**How to apply**: generalizes beyond `/awaken` — any skill with a baked-in "post to X" or "call this API this way" step should get the same live check when X is external and being wrong is public or hard to undo.
