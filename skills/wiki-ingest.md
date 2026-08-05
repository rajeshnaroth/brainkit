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
1. Confirm structure: `wiki/AGENTS.md`, the world folders (`work/`, `personal/`),
   and their category dirs exist.
2. Scan `wiki/raw/` (ignore `processed/`); group by `source:`. Report and confirm
   scope if not already given.
3. For each raw file:
   - Decide its **world**: `work` by default; `personal` only when the content is
     clearly personal or the note says so.
   - Decide category(ies) — a file may yield several pages (source + entity +
     concept + …). Write or merge the page(s) under `wiki/<world>/<category>/` per
     `wiki/AGENTS.md`.
   - **Verbatim artifacts** (`source: artifact` — email/chat threads, pasted docs,
     logs, etc.): file each as a `sources/` page that **keeps the full text intact**
     under a `## Full text` heading, with a short "what it is / why kept" lead above
     it. Never summarize away or trim the verbatim — the whole point is exact
     preservation. You may *additionally* derive entity/concept/synthesis pages from
     it, but the source page retains the complete original.
   - Add cross-links **within that world only** (never link work↔personal). Update
     `wiki/index.md`.
   - Move the raw file to `wiki/raw/processed/` (never delete).
4. For large sets (>~25) or when `batch:N` is given, process in batches and pause.
5. Append one line per batch to `wiki/log.md`.
6. Summary: pages created/updated, raw files processed, anything skipped + why.

## Notes
- This skill only ingests — capture is `/note` and `/close-up`; grooming is
  `/wiki-maintain`.
- If a raw file is ambiguous or low-signal, ask before forcing a page.
- Keep the `personal` world isolated — its pages live under `wiki/personal/` and are
  never merged into or linked from `work/`.

---

## Self-Improvement Protocol

See [Shared Self-Improvement Protocol](./_shared/self-improvement-protocol.md).
