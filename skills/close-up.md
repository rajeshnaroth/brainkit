# close-up

End a work session cleanly: capture what happened, update the project page, and fold
durable knowledge into the wiki.

## Steps
1. **Review the session — completely.** Walk the whole session and list every: topic
   covered, decision made **and its rationale**, artifact created/changed, external
   reference or link, person/team/product involved, open question, blocker, and
   concrete next step. Favor completeness over brevity — this file is raw and
   `/wiki-ingest` distills it later, so don't drop details to sound concise. If detail
   is lost here, it's lost for good.
2. **Preserve verbatim artifacts.** For anything whose *exact wording* matters and a
   summary would lose — email or chat threads, pasted documents/specs, meeting notes,
   quotes, contracts, important command output or logs, code snippets — save it
   **unedited** to `wiki/raw/artifact-{YYYY-MM-DD}-{slug}.md`, one artifact per file.
   Copy faithfully; never paraphrase, trim, or reorder. Frontmatter:
   ```yaml
   ---
   about: <one line — what this is and why it's kept>
   created: {YYYY-MM-DD}
   source: artifact
   ---
   ```
   If it's personal, add a `world: personal` line to the body. Name the slug for the
   thing (e.g. `artifact-2026-08-05-acme-renewal-email-thread.md`). These become
   durable `sources/` pages at ingest and are what you'll cite later.
3. **Write a session brief** to `wiki/raw/session-brief-{YYYY-MM-DD}-{slug}.md` with
   frontmatter (`facets`, `created`, `source: session-brief`; add `world: personal`
   in the body only if the session was personal) and sections:
   Summary · Key decisions (with rationale) · Artifacts · Open questions · Next steps.
   In **Artifacts**, link each verbatim file you saved in step 2 by relative path
   (e.g. `[Acme renewal email thread](artifact-2026-08-05-acme-renewal-email-thread.md)`)
   alongside any external links. This is raw — `/wiki-ingest` structures it later.
4. **Update the focused project page** (`projects/<name>.html`) — anchored regions
   only:
   - Prepend a new `<article class="act">` right after `<!-- activity:top -->`
     (newest first): Did · State · Next, dated today.
   - If more than ~5 entries sit above `<!-- prime:stop -->`, move the oldest into
     `projects/_activity/<name>.html` — prepend it at `<!-- archive:top -->` (newest
     first) and drop that page's "No archived entries yet" placeholder once real
     entries exist. The archive page already exists (created with the project) and the
     project page already links it, so the "Full activity log" link always resolves.
   - Refresh the **Now** block between `<!-- now:start -->` / `<!-- now:end -->`
     (State · optional Blocker · Next).
   - Add any durable links before `<!-- links:end -->`.
5. **Ingest** — always finish by running `/wiki-ingest` on the brief **and the
   artifacts** (and anything else queued in `wiki/raw/`) so the session's knowledge and
   its verbatim sources land in the structured wiki. Don't leave it merely queued.
6. **Back up** (opt-in add-on) — the brain stays local by default. If the user has
   set up a git remote, commit and offer to push; otherwise stay local.

## Optional (runtime-dependent)
- If your agent exposes session memory/checkpoints, harvest durable facts from them
  into the brief before writing it.

## Notes
- Never fabricate activity or artifacts. If little happened, a one-line brief is fine
  and there may be nothing to preserve — only save artifacts that actually appeared in
  the session.
- Only touch anchored regions on the project page; leave the rest byte-stable.
- At root (no focused project), still write the brief, preserve artifacts, and ingest;
  skip the project-page update.

---

## Self-Improvement Protocol

See [Shared Self-Improvement Protocol](./_shared/self-improvement-protocol.md).
