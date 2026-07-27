# project

Switch focus to a project — or, with no argument, sit at **root** (the global view).
Also registers new projects (`project add`).

Focus is non-persistent: every session starts at root. You enter a project only by
asking, and that focus lasts only the session.

## Usage
- `project` — root/global view: list projects and remind that cross-cutting actions
  live here.
- `project <name|alias>` — focus that project for this session.
- `project list` — list all registered projects.
- `project add [brief description]` — register a new project.

## Switch: `project <name>`
1. Resolve `<name>` against `projects/index.html` (match name or alias,
   case-insensitive, prefix OK). Ambiguous → list candidates and ask. None → offer
   `project add`.
2. Read the project page's **priming zone** — everything above `<!-- prime:stop -->`
   (identity, Now, Links, Key files, recent activity). One cheap read resumes
   the work; that is what the ≤~150-line priming zone is for.
3. Open the page's Key files.
4. Print a compact reference card: name + one-liner, Now (state/blocker/next),
   links, key files. Then hold this project's context for the session.
5. _Optional (if your agent exposes a session store):_ warn if another live session
   is focused on the same project, to avoid conflicting edits.

## Root: `project` (no arg)
Show the portfolio (from `projects/index.html`) and remind that at root you can query
and maintain across ALL projects and the whole wiki (`wiki-query`, `wiki-maintain`).
Do not auto-focus anything — root is the cross-reference superpower.

## Add: `project add`
From a one-line description, derive everything and register the project with minimal
questions. Always offer smart defaults the user accepts with one keystroke.
1. Take (or ask for) a brief description.
2. Derive and propose: `name`, 1–2 `aliases`, a one-liner, `world` (from
   `profile.md`'s worlds — ask only if there are several and it's unclear), and
   `status` (default: active). Let the user tweak.
3. Copy `projects/_template.html` → `projects/<name>.html`; fill the tokens; delete
   sections that don't apply (Run + repo/branch for non-code work).
4. Register a new `<li>` in `projects/index.html` (next id, name, aliases, one-liner).
5. Confirm, and offer to focus the new project.

## Notes
- The HTML page IS the project's definition and single source of truth. Never keep a
  parallel markdown copy.
- Keep `<!-- prime:stop -->` within ~150 lines so the priming read stays cheap.
