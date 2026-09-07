---
name: feedback-verify-tolerance-before-flagging-mismatch
description: Do the tolerance-footnote math before presenting a spec/rating comparison as a mismatch, and redo it aloud when corrected
metadata:
  type: feedback
---

Before presenting a "these two specs don't match" finding (panel vs. optimizer rating, inverter vs. battery, connector vs. cable — any producer/consumer pairing with a rated limit), locate every footnote or tolerance clause attached to *either* number and do the actual arithmetic against it — not just eyeball the two headline numbers.

**Why**: flagged AIKO-A665 (665W) as exceeding the SolarEdge S650B's 650W rated input, when a footnote already read moments earlier in the same document allowed +5% module tolerance (665W is 2.3% over — well inside). H caught it by re-quoting the exact footnote. Reading a footnote and *acting on* it are different steps — doing the first without the second produced a confidently-wrong finding, which costs more credibility than staying silent, because pulling a primary-source datasheet is supposed to buy being more right, not confidently wrong with a citation attached.

**How to apply**: 1) find every qualifier attached to either number being compared, 2) do the arithmetic against it (e.g. is 665 ≤ 650×1.05?), 3) only present the mismatch once the *qualified* comparison fails. When H corrects a claim by citing a source already in context, redo the calculation from that source in front of him rather than just accepting the correction verbally — it rebuilds trust faster and catches whether the correction itself needs refinement. Generalizes to any domain with rated capacities and tolerance bands (fasteners, chemical concentrations, load ratings, API rate limits with burst allowances). Same failure family as [[feedback-verify-advisor-citations-before-repeating]] — that one is under-verifying *someone else's* claim before repeating it; this one is under-verifying *your own* extracted claim before flagging a problem.
