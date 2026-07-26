# AGENTS.md — the constitution for this second brain

@profile.md

This file governs how any AI agent (Claude Code, Copilot CLI, Cursor, …) works in
this repository. It loads automatically: `CLAUDE.md` and
`.github/copilot-instructions.md` both point here. Read it fully at the start of a
session, then read `@profile.md` (imported above) for whose brain this is.

## What this repository is

A personal **second brain**: a **wiki** (durable knowledge) plus a **project
workspace** (focused, active work). It grew from the `brainkit` seed and is now
yours — it will diverge and take its own shape. There is no upstream to sync with.

Two superpowers, in tension by design:

- **Focus** — work inside one project with its references at hand.
- **Cross-reference** — surface a theme across every project and note.

## The model: worlds · projects · facets

- **World** — a coarse top-level boundary ("a life"): e.g. `work`, `personal`,
  `confidential`. Worlds exist for separation and privacy, and are declared in
  `profile.md`. **Never mix a `confidential` world into others.**
- **Project** — an active area of focus within a world. Each has a page under
  `projects/` (an HTML file that is its single source of truth), plus todos and
  links.
- **Facet** — an orthogonal topical tag on a wiki page (`hiring`, `pricing`,
  `kubernetes`, …). Facets are **derived** by the agent from your domain and
  content, never enumerated by you.

## Focus is non-persistent — start at root

Every session starts at **root** (the global view). Root is where cross-referencing
lives — you can act across all projects and the whole wiki. You enter a project's
focus only by asking (`project <name>`); that focus lasts the session and is never
sticky. Keeping the global view one step away is the point.

## Skills

Skills are plain-Markdown SOPs in `skills/` — this is the canonical, agent-agnostic
home; edit the SOP here. Invoke one by name ("close up", `/close-up`) or by
describing the intent. When invoked, **read that SOP file and follow it**. Each is
also a worked example — clone one to author your own.

**Discovery note:** Claude Code and Copilot CLI only auto-discover invocable
commands from `.claude/commands/*.md` — a folder named `skills/` alone is invisible
to that mechanism, even though the concept is generic. So `.claude/commands/`
carries one thin stub per skill (a couple of lines pointing at the real SOP in
`skills/`); that's why both exist. If you add a new skill, add both: the real SOP in
`skills/`, and a matching stub in `.claude/commands/` so it's actually invocable.
Agents without that native mechanism (Cursor, etc.) can just be told to read
`skills/` directly using the table below.

| Invoke | SOP | Does |
|---|---|---|
| `project` · `project <name>` · `project add` | `skills/project.md` | Switch focus to a project (or root); register a new one |
| `dashboard` | `skills/dashboard.md` | Customize the look of project pages + the index |
| `close-up` | `skills/close-up.md` | End of session: write a brief, update the project page, file next steps as todos, ingest |
| `todo` | `skills/todo.md` | The ONLY writer of todo state (source file + project-page mirror) |
| `note` | `skills/note.md` | Quick-capture a thought into `wiki/raw/` for later ingestion |
| `wiki-ingest` | `skills/wiki-ingest.md` | Turn `wiki/raw/` material into structured wiki pages |
| `wiki-query` | `skills/wiki-query.md` | Answer a question grounded in the wiki, with citations |
| `wiki-maintain` | `skills/wiki-maintain.md` | Audit + repair the wiki (links, dupes, splits, index) |

The authoritative rules for the wiki itself live in **`wiki/AGENTS.md`**; the
`wiki-*` skills defer to it.

## Conventions (hold these everywhere)

- **Never fabricate.** If you don't know, say so. Cite wiki pages when asserting
  facts drawn from them.
- **Tag by world.** Every wiki page carries a `world:` matching one of
  `profile.md`'s worlds. Never let a `confidential` world leak into another.
- **Anchored flat files.** Project pages carry HTML comment anchors
  (`<!-- now:start -->`, `<!-- todos:top -->`, `<!-- activity:top -->`,
  `<!-- prime:stop -->`). Skills edit *between* anchors with exact-string edits —
  keep the anchors intact.
- **Sole writer.** Only `/todo` writes todo state. Other skills call it.
- **Capture before process.** `/note` saves raw before anything ingests it.
- **Propose before destroying.** `/wiki-maintain` lists changes and gets an OK
  before merges/prunes; it archives, never hard-deletes.
- **Reading order = resume order.** A project page reads top-to-bottom the way you'd
  resume the work: identity → now → todos → links → key files → recent activity.
- **Smart defaults.** When a skill needs input, propose a sensible default and let
  the user accept with one keystroke; never force a long questionnaire.

## Backup

If `profile.md`'s `backup.remote` is set, offer to commit and push after meaningful
changes. If it's empty, stay local and mention once that backup is available. Never
push a `confidential` world to a shared remote without explicit confirmation.

## When you learn something durable

If you hit a repeatable gotcha while running a skill, add a one-line
`<!-- learned: … -->` note at the failing step in that skill's SOP. The system
improves itself in place.
