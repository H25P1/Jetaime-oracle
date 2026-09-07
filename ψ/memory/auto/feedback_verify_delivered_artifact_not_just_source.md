---
name: feedback-verify-delivered-artifact-not-just-source
description: "\"I fixed the local file\" and \"the delivered copy is fixed\" are different claims — verify the artifact the recipient actually opens"
metadata:
  type: feedback
---

When a deliverable passes through a conversion or upload step between the local working file and what the recipient actually receives (CSV → Google Sheet, in the case this came from), verify the *delivered* copy before declaring the task done — not the source file that produced it.

**Why**: fixed a CSV locally, uploaded it to Drive, then told H "The Sheet was created successfully — done" without checking the uploaded copy matched. A comma-escaping bug had shifted columns in the uploaded Sheet, corrupting exactly the row warning H that a commissioning sequence was unsourced — the single most important row in the document not to lose. Only caught because a mandatory pre-completion `advisor()` call flagged the gap.

**How to apply**: treat a conversion/upload step as a place bugs hide silently. Before saying a task is done, re-open or re-read the artifact as delivered (not the local source), especially when the deliverable carries a safety- or correctness-critical line. This is the second-half check that pairs with calling `advisor()` before declaring completion (global CLAUDE.md rule) — the call only catches this if you actually re-examine the delivered thing, not just narrate that you fixed something.
