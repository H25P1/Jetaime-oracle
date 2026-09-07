---
pattern: Before flagging a spec/tolerance mismatch between two datasheet'd components, redo the percentage math against any qualifying footnote already in your read context — don't paraphrase a citation you haven't computed against
date: 2026-07-31
source: rrr: Jetaime-oracle
concepts: [datasheet-verification, engineering-review, overconfidence, self-correction, solar-design]
---

# Verify tolerance footnotes before flagging a component mismatch

## What happened

While designing a solar PV system (10× AIKO-A665-MDE72Dw panels, 665W nameplate, paired with SolarEdge S650B power optimizers, 650W rated input DC power), I read the S650B datasheet, saw "Rated Input DC Power: 650W" for that model, compared it to the panel's 665W, and flagged this as a spec violation — panel exceeds optimizer's rated input.

The same datasheet, in a footnote I had already read moments earlier, said: *"Rated power of the module at STC will not exceed the Power Optimizer Rated Input DC Power. Modules with up to +5% power tolerance are allowed."* 665W is 2.3% over 650W — comfortably inside the stated +5% allowance. There was no mismatch. The user (a working engineer on this project) caught it by re-citing the exact footnote back to me.

## Why this happened

I extracted the single headline number (650W) that was directly comparable to the other headline number (665W) and reasoned from that comparison alone. The qualifying clause was present in the same document, in the same read, but I didn't re-open it to check whether it changed the comparison before presenting the flag as a finding. Reading a footnote and *acting on* a footnote are different steps; I'd done the first without the second.

## The generalizable rule

When comparing two datasheet'd specs (panel vs. optimizer, inverter vs. battery, connector vs. cable, any producer/consumer pairing with a rated limit), before presenting a "these don't match" finding:

1. Locate every footnote, tolerance clause, or "unless otherwise noted" qualifier attached to *either* of the two numbers being compared — not just the ones near the number that seems most relevant.
2. Do the actual arithmetic against that clause (e.g., is 665 ≤ 650 × 1.05?) rather than eyeballing "665 > 650, that's a problem."
3. Only present the mismatch once the qualified comparison — not just the headline numbers — actually fails.

This generalizes beyond solar/electrical work: any domain with rated capacities and manufacturer tolerance bands (mechanical fasteners, chemical concentrations, load ratings, API rate limits with burst allowances) has the same failure shape — a raw-number comparison that looks like a violation but isn't once the documented tolerance is applied.

## Why it matters

A wrong "mismatch" flag costs more than staying silent would have, because it burns the credibility that pulling primary-source datasheets was supposed to buy in the first place. The whole point of citing a datasheet instead of guessing is to be *more* right, not confidently wrong with a citation attached. Catching this kind of error requires treating "I read the document" and "I applied everything the document said" as two separate checkpoints, not one.
