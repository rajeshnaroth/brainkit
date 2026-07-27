# wiki-maintain

Groom the wiki — fix broken links, merge duplicates, split overloaded pages, prune
stale ones, refresh the index. Follow the Maintain workflow in
[`wiki/AGENTS.md`](../wiki/AGENTS.md); if anything here conflicts, that file wins.

## Usage
- `wiki-maintain` — audit and propose a plan; ask before editing.
- `wiki-maintain apply` — skip confirmation and apply the obvious fixes.

## Steps
1. Read `wiki/AGENTS.md`; do what its Maintain workflow says.
2. **Propose-then-apply**: find issues, list them in logical batches, get an OK per
   batch (unless `apply`).
3. Work **one world at a time** (`work/`, then `personal/`). Fixes: broken/relative
   links, duplicate pages (merge conservatively — a bad merge is hard to undo),
   overloaded pages (split), stale pages (**archive, never hard-delete**), and a
   refreshed `wiki/index.md`.
4. **Flag any link that crosses the work/personal wall** as an error to fix, and
   never merge a page from one world into another.
5. Log a maintenance line to `wiki/log.md`.

## Notes
- Doesn't ingest. If `wiki/raw/` is non-empty, suggest `/wiki-ingest` but don't run
  it.
- Treat `wiki/AGENTS.md` itself as read-only here — changing conventions is a
  separate, deliberate conversation.
