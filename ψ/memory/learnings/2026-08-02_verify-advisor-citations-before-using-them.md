---
pattern: A second-opinion model (advisor/reviewer) can state specific, attributed-sounding facts with full confidence that are not actually grounded in anything you read — verify checkable claims (numbers, quotes, "you read this earlier") against the primary source before repeating them in a deliverable, especially one with physical/safety consequences
date: 2026-08-02
source: rrr: Jetaime-oracle
concepts: [advisor-verification, fabrication-detection, datasheet-verification, engineering-review, self-correction, solar-design]
---

# Verify advisor citations before using them — confidence of phrasing is not evidence of grounding

## What happened

While building an installation check sheet for a solar PV system (10× AIKO-A665 panels, SolarEdge SE5000H + S650B optimizers, Antai rail mounting), I called `advisor()` for guidance on document structure. The advisor's response included specific torque values attributed to "what you read directly" earlier in the session: M8 rail bolts 18–20 N·m, M6 hooks-to-rafter 5–6 N·m, M6 grounding lug screw 9–10 N·m, rail-splice bolts 3–5 N·m, mid/end clamp 18–20 N·m.

These numbers were never actually read. I grepped the raw session `.jsonl` transcript for every plausible formatting of those figures (`N·m`, `N.m`, `Torque`, numeric ranges near N·m) before writing them into the checklist, and found nothing matching — only a generic ISO 898-1 bolt table, a Unistrut channel-nut torque table (unrelated hardware), and one unrelated tool-capability spec ("Max. torque ≥34 N·m" for a grinder). None of those are the Antai product's fastener torque spec. I surfaced this to `advisor()` in a second call; it fully retracted the numbers and confirmed they were fabricated, not misremembered from real context.

## Why this happened

The claim was structured exactly like the kind of grounded detail the task needed — specific values, specific fastener types, framed as "you already read this." That framing (appeal to my own prior action, "you read this earlier") is a stronger trust signal than a plain assertion would have been, because it invites the reader to trust their own memory of having done the reading rather than to re-check it. Nothing about the phrasing was hedged or uncertain — full confidence, specific numbers, plausible units. There was no stylistic tell distinguishing this from a real citation.

## The generalizable rule

When any second-opinion source — an advisor/reviewer model, a delegated research agent, a subagent's summary — attributes a specific fact to "something you already read/did/verified," and that fact is checkable against a durable record (a session transcript, a file, a datasheet, a git log), check it before repeating it in your own output. This applies with extra force when:

1. The claim will inform a document with real-world consequences (safety specs, financial figures, legal/compliance statements) — the cost of being wrong scales with what the reader will do with the number.
2. The claim is specific enough to sound sourced (a numeric range, a named page, a quoted phrase) — specificity increases apparent credibility without increasing actual grounding.
3. A cheap verification path exists (grep a transcript, re-open a file, re-run a search) — if verification is cheap relative to the downstream cost of being wrong, there's no good reason to skip it.

Practically: grep the transcript or source material for the *literal* claimed values/quotes, not just the general topic. A topic-level search ("torque," "Antai") will surface adjacent-but-wrong material (a different manufacturer's channel-nut table) that can itself be mistaken for confirmation. Search for the specific number or phrase being verified.

When verification fails, don't quietly drop the claim and move on — mark it explicitly as unsourced in the deliverable (e.g., a `SOURCE-NEEDED` status with a note on what's missing and where to actually find it), so the person consuming the document knows exactly what still needs a human to confirm, rather than silently getting a document with fewer specifics and no explanation why.

## Why it matters

This is the same failure shape as an earlier lesson in this vault (verify tolerance footnotes before flagging a mismatch) but pointed in the opposite direction: that one was about under-verifying my own extracted claim before flagging a problem; this one is about under-verifying someone else's claim before repeating it as fact. Both share the same root cause — treating "this came from a step that looked like verification" (I read the footnote; the advisor said it read the manual) as equivalent to "this claim is actually grounded." A second-opinion tool is valuable precisely because it can catch things the primary agent missed — but that value only holds if its output is treated as a hypothesis to check, not a citation to trust, whenever the claim is checkable and the stakes justify the check.
