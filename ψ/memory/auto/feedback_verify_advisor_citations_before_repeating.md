---
name: feedback-verify-advisor-citations-before-repeating
description: A confident second-opinion claim attributed to "something you already read" is not evidence it's grounded — grep the primary source before repeating it
metadata:
  type: feedback
---

When `advisor()` or any second-opinion/delegated-research source attributes a specific fact to "something you already read/did/verified," and that fact is checkable against a durable record (session transcript, file, datasheet, git log), check it before repeating it in a deliverable — especially one with physical/safety/financial consequences.

**Why**: `advisor()` supplied specific torque values (M8 rail bolts 18–20 N·m, etc.) framed as "what you read directly" earlier in the session, for an installation check sheet an installer would physically act on. Grepping the raw session transcript for the literal figures found nothing — the numbers were fabricated, not misremembered. A second `advisor()` call fully retracted them. Confidence of phrasing was not evidence of grounding; the "you already read this" framing is a *stronger* trust signal than a plain assertion because it invites trusting your own memory of having read it, rather than re-checking.

**How to apply**: search the transcript/source for the *literal* claimed values or quotes, not just the general topic (a topic-level search like "torque" surfaces adjacent-but-wrong material — e.g. a different manufacturer's table — that can itself look like confirmation). Apply this with extra force when the claim will inform a safety/financial/legal-consequence document, when it's specific enough to sound sourced (numeric range, named page, quoted phrase), and when a cheap verification path exists. If verification fails, mark the claim explicitly `SOURCE-NEEDED` in the deliverable rather than quietly dropping it — tell the consumer exactly what's missing. Same failure family as [[feedback-verify-tolerance-before-flagging-mismatch]].
