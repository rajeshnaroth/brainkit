# note

Quick-capture a thought into the wiki inbox. Single responsibility: **capture**.
Classification, cross-linking, and page placement are `/wiki-ingest`'s job — don't do
them here.

## Steps
1. Take the thought (typed, pasted, or dictated).
2. Give it a short title and lightly clean it up — fix obvious typos, keep the meaning
   faithful. Do **not** rewrite or embellish.
3. **Save it first** to `wiki/raw/note-{YYYY-MM-DD}-{slug}.md` with frontmatter:
   ```yaml
   ---
   title: ...
   created: {YYYY-MM-DD}
   source: note
   ---
   ```
   Saving before anything else means a failed ingest never loses the note. If the
   note is personal, add a line to its body like `world: personal` so `/wiki-ingest`
   files it under `wiki/personal/`; otherwise it defaults to work.
4. **Ingest** — always finish by running `/wiki-ingest` on the note so it's filed into
   the wiki. The raw file is already saved (step 3), so a failed ingest never loses it;
   don't just leave the note queued.

## Notes
- If the note is clearly personal, flag it (see step 3) so it lands in the personal
  world and stays out of any work context.
- One thought per note; if the user dumps several, split them.

---

## Self-Improvement Protocol

See [Shared Self-Improvement Protocol](./_shared/self-improvement-protocol.md).
