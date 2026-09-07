---
name: feedback-drive-mcp-tooling-limitations
description: Known Google Drive MCP sharp edges — no move/rename/delete/update, strict search syntax, silent OCR failure on scanned PDFs, list overflow
metadata:
  type: feedback
---

The Google Drive MCP toolset has structural gaps that cost round-trips or block automation whenever used non-trivially:

- **No move, rename, delete, or update-in-place.** Every correction to an already-created Sheet becomes "H, please edit these two cells"; every folder reorg leaves originals in place needing a manual cleanup ask. `copy_file` does not work on folders — test this assumption with one throwaway call before planning a reorg around it.
- **`list_recent_files` can overflow the tool's token limit** (hit 113K chars once) — pass `excludeContentSnippets: true` to avoid this; it isn't obvious from a quick glance at the schema.
- **`search_files` full-text query syntax is strict and unforgiving** — a bare phrase like `"Solar PPM"` gets rejected ("Unsupported query field"); `fullText contains 'PPM'` alone returns unrelated noise from elsewhere in the Drive. Combine specific terms: `fullText contains 'Antai' and fullText contains 'installation'`.
- **`read_file_content` on scanned/image-only PDFs returns a near-empty string silently — no error, no "this is a scan" flag.** A suspiciously short or generic result (e.g. only cover-page OCR) means "extraction likely failed," not "document has little content." Cross-check with a different read or flag to H that manual review may be needed rather than treating thin output as ground truth. Hit this twice in one project (TF catalog pages 12-26, then Antai_Mounting_Catalog.pdf).
- **`search_files`'s `parentId` supports one folder per query** — mapping a 4-level folder tree took ~14 round-trips; there's no recursive-list option, so this overhead is structural, not a mistake to avoid.

**Why this matters**: this pattern recurred in the friction column of 3 of 3 logged sessions with different specific symptoms each time — the parent CLAUDE.md's "same friction 3 sessions → fix root cause, not another workaround" rule has triggered. As of the last recorded session (2026-08-02) this had not yet been raised with H as a decision point: whether a small internal Drive-quirks reference doc would help, or whether large scanned catalogs should default to "ask H to open the specific page" rather than attempting extraction.

**How to apply**: when starting Drive-heavy work, budget for these limits up front rather than re-discovering each one fresh. If this friction shows up again, raise the standing open question with H rather than absorbing another instance silently.
