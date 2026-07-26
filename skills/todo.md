# todo

The **single writer** of todo state. Todos live in two mirrored places and `/todo`
keeps them in sync: the source of truth (`wiki/entities/todo.md`) and the focused
project page (between the `todos:top` / `todos:end` anchors). No other skill edits
either — they call `/todo`.

## Usage
- `todo` / `todo list` — list open todos (optionally for the focused project).
- `todo add <description>` — add one. Infer priority, due date, and a facet from the
  text; assign the next id (`next_id` in `todo.md`). Ask nothing if you can infer
  sensibly; default priority is P2.
- `todo done <id|index|match>` — complete it: move to Done in `todo.md` and remove
  its `<li>` from the project page.
- `todo update <id|match> <change>` — edit text / priority / due.

## Project routing
Attach a new todo to, in order: the focused project → an explicit `@project` in the
text → the project inferable from context → else file-only (in `todo.md`, no page
mirror). Recompute the page's `X open` count on every change.

## Source of truth — wiki/entities/todo.md
- `next_id:` — monotonic counter; assign then increment.
- `## Open` — one line per active todo: id, priority, text, optional due/facet.
- `## Done` — completed items (keep them; history matters).

## Project-page mirror (between the anchors)
```html
<li id="t-7"><span class="pri p1">P1</span> <b>title</b> <span class="tmeta">· note</span></li>
```
Priority classes: `p1` high · `p2` normal · `p3` low. Newest first. Leave the region
empty when zero are open.

## Optional (runtime-dependent)
- If you keep an external reminder system, you may mirror open todos there too. Keep
  `todo.md` authoritative; the external list is a convenience copy.

## Notes
- Sole-writer discipline is the whole point: because only `/todo` edits todo state,
  the source file and every project page never drift.
