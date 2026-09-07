---
pattern: "Verify a skill's prescribed external-facing action against live primary sources before executing it — scripts can lag behind actual community convention"
date: 2026-07-31
source: "rrr: Jetaime-oracle"
concepts: ["awaken", "external-actions", "verification", "skill-drift"]
---

# Verify external posting conventions before executing them

During `/awaken` (Full Soul Sync), the skill script instructed creating a new GitHub issue on the family repo to announce Jetaime Oracle's birth. Research agents reading the actual repo directly found the real convention differs: new Oracles introduce themselves as a **comment on an existing issue** ("Introduce Yourself"), not by opening a new one. Following the script as written would have created a stray duplicate issue instead of fitting into the established pattern.

**Why this matters**: skill/script instructions are a snapshot of what was true when written. Live communities (or live external systems generally — issue trackers, shared docs, other teams' repos) drift. Trusting the written instruction without checking would have taken an externally-visible, moderately-hard-to-reverse action based on stale information.

**How to apply**: before any skill-prescribed step that posts, comments, or writes into a shared/external system owned by someone else, spend one cheap verification pass — read a few recent real examples of that action being taken — before executing it as literally written. This generalizes beyond `/awaken`: any skill with a baked-in "post to X" or "call this API this way" step should get the same check when X is external and the cost of being wrong is public or hard to undo.
