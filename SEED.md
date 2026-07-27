# SEED.md — run this once to set up a second brain, then delete yourself

You are an AI agent (Claude Code, Copilot CLI, …) setting up a personal **second
brain** for the human in front of you, from the `brainkit` seed. There is **no
interview** — the brain ships ready to use. Your job is a quick, silent bootstrap,
then a warm welcome. Do it in a few seconds, not a few minutes.

## 1. Orient
- You should already be **inside a clone** of the seed — the whole tree is on disk
  (you're reading this file locally). If instead you were only handed the seed's URL,
  clone it in **one** operation (`git clone <url> .` into the target folder) — never
  fetch files one at a time over HTTP; that is slow and prompts the user per file.
- Confirm you're in the folder the user wants their brain to live in. If `wiki/work/`
  already contains real pages, stop and ask — don't overwrite an existing brain.
- Re-init a clean history so the brain has no upstream and no seed remote:
  `rm -rf .git && git init -q`.

## 2. Set up (silent — no questions)
- The structure already ships ready: two worlds (`wiki/work/`, `wiki/personal/`),
  each with `sources/ entities/ concepts/ synthesis/`; a shared `wiki/raw/` inbox;
  the project dashboard (`projects/index.html`) with one example project; the skills;
  and a permissive `.claude/settings.json` so the user isn't flooded with approvals
  once they trust the folder.
- Leave `profile.md` and `wiki/log.md` as their shipped stubs — no edits needed.
- Keep setup to as few write operations as possible; the shipped tree is already
  correct, so the only writes are the git re-init and this file's deletion.
- **Delete this file (`SEED.md`)** — its job is done. `AGENTS.md` is the durable
  constitution that stays.
- Commit everything: `git add -A && git commit -m "Set up second brain from brainkit"`.

> **First-run heads-up (mention this to the user up front):** a freshly cloned repo
> isn't trusted yet, so the agent's own `.claude/settings.json` isn't active for this
> first session — the tool will ask to approve the setup edits. Tell them to pick
> **"allow all edits during this session"** (Claude Code: option 2 / shift+tab) once,
> and setup finishes quietly. From the next session on, the shipped settings keep it
> quiet automatically.

## 3. Welcome — print this to the user (in plain chat)
Show them exactly this, then stop and let them drive:

> **Your second brain is ready.** Two things it does for you:
>
> **1. It remembers things.**
> Drop any files — notes, PDFs, transcripts — into the `wiki/raw/` folder, then run
> `/wiki-ingest`. I'll turn them into tidy, searchable pages (this can take a bit).
> After that, ask `/wiki-query` and I'll answer from your own notes. Got a quick
> thought? Jot it with `/note`.
>
> **2. It keeps your projects straight.**
> Start one with `/project add <what it's about>` — I'll set up a page for it. Come
> back to it later with `/project <name>`.
>
> Anything private? Just say *"this is personal"* and I'll keep it in a separate
> space, out of your everyday work.
>
> Not sure where to start? Just tell me in plain words what you want — I'll handle the
> rest.

## Acceptance criteria — verify before you call it done
- [ ] Fresh git history (no seed remote); one initial commit exists.
- [ ] `wiki/work/` and `wiki/personal/` both present with their four sub-categories;
      `wiki/raw/` inbox present.
- [ ] `.claude/commands/*.md` stubs are present (they ship with the seed) so skills
      are invocable.
- [ ] `SEED.md` deleted.
- [ ] You printed the welcome and did **not** run an interview.
