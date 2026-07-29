# close-up

End a work session cleanly: capture what happened, update the project page, and fold
durable knowledge into the wiki.

## Steps
1. **Review the session** — topics, decisions, artifacts created/changed, open
   questions, concrete next steps.
2. **Write a session brief** to `wiki/raw/session-brief-{YYYY-MM-DD}-{slug}.md` with
   frontmatter (`facets`, `created`, `source: session-brief`; add `world: personal`
   in the body only if the session was personal) and sections:
   Summary · Key decisions · Artifacts · Open questions · Next steps. This is raw —
   `/wiki-ingest` structures it later.
3. **Update the focused project page** (`projects/<name>.html`) — anchored regions
   only:
   - Prepend a new `<article class="act">` right after `<!-- activity:top -->`
     (newest first): Did · State · Next, dated today.
   - If more than ~5 entries sit above `<!-- prime:stop -->`, move the oldest into
     `projects/_activity/<name>.html`. Create that file if it doesn't exist yet, and
     the **first** time you create it, replace the `<!-- archive-link: … -->`
     placeholder (just after `<!-- prime:stop -->`) with the real link
     `<p class="archive-link">→ <a href="_activity/<name>.html">Full activity log</a></p>`
     (so that the "Full activity log" link never points at a page that doesn't exist).
   - Refresh the **Now** block between `<!-- now:start -->` / `<!-- now:end -->`
     (State · optional Blocker · Next).
   - Add any durable links before `<!-- links:end -->`.
4. **Ingest** — always finish by running `/wiki-ingest` on the brief (and anything
   else queued in `wiki/raw/`) so the session's knowledge lands in the structured wiki.
   Don't leave it merely queued.
5. **Back up** (opt-in add-on) — the brain stays local by default. If the user has
   set up a git remote, commit and offer to push; otherwise stay local.

## Optional (runtime-dependent)
- If your agent exposes session memory/checkpoints, harvest durable facts from them
  into the brief before writing it.

## Notes
- Never fabricate activity. If little happened, a one-line brief is fine.
- Only touch anchored regions on the project page; leave the rest byte-stable.
- At root (no focused project), still write the brief + ingest; skip the project-page
  update.

---

## Self-Improvement Protocol

See [Shared Self-Improvement Protocol](./_shared/self-improvement-protocol.md).
