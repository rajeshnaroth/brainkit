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

- **World** — a coarse top-level boundary, and it's a **folder**, not a setting. The
  wiki ships with two: `wiki/work/` (your default) and `wiki/personal/` (a private
  wall). The path *is* the world — pages carry no `world:` tag. **Cross-reference
  stays inside a world and stops at the wall:** never link a `work/` page to a
  `personal/` one, and a work query never reads `personal/`. Add a third walled world
  later (e.g. `confidential/`) by adding a sibling folder.
- **Project** — an active area of focus. Projects live in `work/` only (each is a
  page under `projects/`, an HTML file that is its single source of truth, plus
  links). Personal is a privacy wall for knowledge, not a project space — if you want
  personal *projects*, start a separate brain.
- **Facet** — an orthogonal topical tag on a wiki page (`hiring`, `pricing`,
  `kubernetes`, …). Facets are **derived** by the agent from your content, never
  enumerated by you.

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
`skills/`, and a matching stub in `.claude/commands/` so it's actually invocable. End
every skill SOP with the shared Self-Improvement Protocol footer (see the others).
Agents without that native mechanism (Cursor, etc.) can just be told to read
`skills/` directly using the table below.

| Invoke | SOP | Does |
|---|---|---|
| `project` · `project <name>` · `project add` | `skills/project.md` | Switch focus to a project (or root); register a new one |
| `dashboard` | `skills/dashboard.md` | Customize the look of project pages + the index |
| `close-up` | `skills/close-up.md` | End of session: write a brief, update the project page, ingest |
| `note` | `skills/note.md` | Quick-capture a thought into `wiki/raw/` for later ingestion |
| `wiki-ingest` | `skills/wiki-ingest.md` | Turn `wiki/raw/` material into structured wiki pages |
| `wiki-query` | `skills/wiki-query.md` | Answer a question grounded in the wiki, with citations |
| `wiki-maintain` | `skills/wiki-maintain.md` | Audit + repair the wiki (links, dupes, splits, index) |

The authoritative rules for the wiki itself live in **`wiki/AGENTS.md`**; the
`wiki-*` skills defer to it.

## Conventions (hold these everywhere)

- **Never fabricate.** If you don't know, say so. Cite wiki pages when asserting
  facts drawn from them.
- **File by world folder.** Knowledge lives under `wiki/work/` or `wiki/personal/`;
  the folder is the world (no `world:` tag). Never link or merge across the
  work/personal wall, and never surface `personal/` content in a work answer.
- **Anchored flat files.** Project pages carry HTML comment anchors
  (`<!-- now:start -->`, `<!-- activity:top -->`, `<!-- prime:stop -->`). Skills
  edit *between* anchors with exact-string edits — keep the anchors intact.
- **Capture before process.** `/note` saves raw before anything ingests it.
- **Propose before destroying.** `/wiki-maintain` lists changes and gets an OK
  before merges/prunes; it archives, never hard-deletes.
- **Reading order = resume order.** A project page reads top-to-bottom the way you'd
  resume the work: identity → now → links → key files → recent activity.
- **Smart defaults.** When a skill needs input, propose a sensible default and let
  the user accept with one keystroke; never force a long questionnaire.
- **Ask in chat, not a picker.** Any question a skill needs to ask goes in plain
  chat text, even when the agent's environment offers a built-in interactive
  multiple-choice/key-select tool. Skip that tool for this — it renders as a popup
  that loses the surrounding context once dismissed, which fights the "feels like a
  chat" goal above.

## Backup

The brain stays **local by default** — backup is an opt-in add-on. When the user
asks to back up, help them push to a private git repo; once a remote is set, offer to
commit and push after meaningful changes. Never push without explicit confirmation.

## When you learn something durable

You maintain the skills you run: if one misfires or needs a workaround, fix its SOP
in place before finishing — don't just work around it. Add a one-line
`<!-- learned: … -->` note at the failing step so the system improves itself in place.
Every skill ends with the shared **Self-Improvement Protocol**
(`skills/_shared/self-improvement-protocol.md`) — the full rules live there.
