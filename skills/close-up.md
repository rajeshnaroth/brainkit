# close-up

End a work session cleanly: capture what happened, update the project page, file the
next steps as todos, and fold durable knowledge into the wiki.

## Steps
1. **Review the session** — topics, decisions, artifacts created/changed, open
   questions, concrete next steps.
2. **Write a session brief** to `wiki/raw/session-brief-{YYYY-MM-DD}-{slug}.md` with
   frontmatter (`world`, `facets`, `created`, `source: session-brief`) and sections:
   Summary · Key decisions · Artifacts · Open questions · Next steps. This is raw —
   `/wiki-ingest` structures it later.
3. **File next steps as todos** via `/todo` (the sole writer). Don't write todos into
   the project page yourself.
4. **Update the focused project page** (`projects/<name>.html`) — anchored regions
   only:
   - Prepend a new `<article class="act">` right after `<!-- activity:top -->`
     (newest first): Did · State · Next, dated today.
   - If more than ~5 entries sit above `<!-- prime:stop -->`, move the oldest into
     `projects/_activity/<name>.html`.
   - Refresh the **Now** block between `<!-- now:start -->` / `<!-- now:end -->`
     (State · optional Blocker · Next).
   - Add any durable links before `<!-- links:end -->`.
5. **Ingest** the brief with `/wiki-ingest` (or note that raw is queued).
6. **Back up** — if `profile.md` has `backup.remote`, commit and offer to push.

## Optional (runtime-dependent)
- If your agent exposes session memory/checkpoints, harvest durable facts from them
  into the brief before writing it.

## Notes
- Never fabricate activity. If little happened, a one-line brief is fine.
- Only touch anchored regions on the project page; leave the rest byte-stable.
- At root (no focused project), still write the brief + ingest; skip the project-page
  update.
