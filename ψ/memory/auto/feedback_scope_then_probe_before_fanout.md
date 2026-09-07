---
name: feedback-scope-then-probe-before-fanout
description: Finish enumerating full scope and confirm tool reachability with one probe agent before launching a parallel subagent fan-out
metadata:
  type: feedback
---

Before committing to reading many external documents (Drive, wikis, large repos) or fanning out parallel subagents against a third-party/interactively-authenticated tool: first finish enumerating the full scope and report real counts to H, then send one cheap probe agent to confirm the tool is actually reachable from a subagent context — only launch the full fan-out after both checks pass.

**Why**: "study this folder" hid far more content than the first listing suggested (a 43-file, 4-level-deep tree, several 20-50MB PDFs) — scoping only after full enumeration avoided both under- and over-delivery. Separately, confirming Drive MCP access from a subagent via one probe agent before launching 9 parallel readers meant a failed-access assumption would have cost 1 agent instead of 9 — worth the extra round-trip.

**How to apply**: treat "enumerate everything, then scope" and "probe reachability with one agent before N-way fan-out" as a paired pre-flight check for any bulk external-tool task, not just Drive. When output will mix public-safe and sensitive material, also decide the write destination (public vs. private repo) *before* writing anything — deciding after the fact risks a rewrite or a leak.
