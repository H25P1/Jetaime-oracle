---
name: feedback-boq-status-discipline
description: Use an explicit FIRM/SURVEY-DEPENDENT/TBC status column in BOQs and technical takeoffs rather than fabricating or silently omitting unknowns
metadata:
  type: feedback
---

In documents that mix computed, assumed, and genuinely-unknown quantities (BOQs, technical takeoffs, check sheets), an explicit status column — FIRM / SURVEY-DEPENDENT / TBC / SOURCE-NEEDED — is worth more to H than either a fabricated plausible number or a silently omitted line.

**Why**: this discipline, applied across mounting and conduit BOQs, kept documents honest even when roughly a third of line items in one BOQ ended up TBC because the source catalog's fitting/box pages were scanned images with no extractable text (see [[feedback-drive-mcp-tooling-limitations]]). That's a real usability cost, but both alternatives cost more trust when discovered later: a confidently-wrong number, or a gap nobody was told about.

**How to apply**: default every technical deliverable with open unknowns to a status-tagged ledger rather than presenting uniform false precision. When a value can't be sourced (e.g. a scanned datasheet won't OCR), mark it SOURCE-NEEDED with a note on what's missing and where to find it, per [[feedback-verify-advisor-citations-before-repeating]].
