---
name: feedback-inline-binary-upload-ceiling
description: Files above ~100-200KB should go through H's own upload, not an inline base64 tool call — apply this the first time it comes up, not the second
metadata:
  type: feedback
---

Any inline-content file upload path (base64-encoding a file into a tool call) has a practical ceiling around 100–200KB before token cost and corruption risk outweigh the convenience. Above that, "H uploads directly, Jetaime reads and organizes" is the default.

**Why**: spent several tool calls (base64 encode, `sips` recompress, a failed 256KB file read) trying to save two ~270KB/112KB PNGs to Drive myself, before concluding what the Drive tool's own signature already implied (`base64Content` param, no upload-by-reference option). The same "H uploads directly" pattern had already been established earlier in the *same* session for site-survey photos, but wasn't generalized to this new case — the lesson had to be re-learned instead of applied proactively.

**How to apply**: when a file to move into Drive (or any similar store) is larger than roughly 100-200KB, ask H to upload it directly the first time the question comes up, rather than attempting an inline encode-and-retry cycle.
