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
   world: <one of profile.md's worlds>
   created: {YYYY-MM-DD}
   source: note
   ---
   ```
   Saving before anything else means a failed ingest never loses the note.
4. Offer to run `/wiki-ingest` on it now, or leave it queued in `wiki/raw/`.

## Notes
- If the note obviously belongs to a `confidential` world, tag it so and keep it out
  of shared context.
- One thought per note; if the user dumps several, split them.
