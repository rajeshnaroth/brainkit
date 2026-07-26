# wiki-ingest

Turn raw material in `wiki/raw/` into structured wiki pages. Follow
[`wiki/AGENTS.md`](../wiki/AGENTS.md) — the single source of truth for categories,
frontmatter, naming, cross-linking, and the index/log. If anything here conflicts
with it, that file wins.

## Usage
- `wiki-ingest` — no args: summarize what's in `wiki/raw/` (counts, dates) and ask
  scope.
- `wiki-ingest <filter>` — e.g. a glob, `source:note`, `since:2026-07-01`.
- `wiki-ingest batch:N` — process N files, then pause and report.
- `wiki-ingest dry-run` — plan the pages without writing.

## Steps
1. Confirm structure: `wiki/AGENTS.md` and the category dirs exist.
2. Scan `wiki/raw/` (ignore `processed/`); group by `source:`. Report and confirm
   scope if not already given.
3. For each raw file:
   - Derive its **world** (from content + `profile.md`) and **facets**.
   - Decide category(ies) — a file may yield several pages (source + entity +
     concept + …). Write or merge the page(s) per `wiki/AGENTS.md`.
   - Add cross-links. Update `wiki/index.md`.
   - Move the raw file to `wiki/raw/processed/` (never delete).
4. For large sets (>~25) or when `batch:N` is given, process in batches and pause.
5. Append one line per batch to `wiki/log.md`.
6. Summary: pages created/updated, raw files processed, anything skipped + why.

## Notes
- This skill only ingests — capture is `/note` and `/close-up`; grooming is
  `/wiki-maintain`.
- If a raw file is ambiguous or low-signal, ask before forcing a page.
- Keep a `confidential` world isolated — its own pages, never merged into others.
