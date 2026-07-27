# dashboard

Own the *look* of the projects system — the shared stylesheet, the page template,
the portfolio index, and the per-project welcome. This is the one presentational
skill; every other skill writes content into the structures it defines.

## What it governs
- `projects/_style.css` — palette + typography. One edit reskins every page.
- `projects/_template.html` — the shape of a project page.
- `projects/index.html` — the bookmarkable portfolio.
- The welcome/priming read `/project` prints when you focus a project.

## Invariants — do not break (the other skills depend on them)
- **Anchored, flat, no JS.** Keep the exact comment anchors (`now:start/end`,
  `activity:top`, `prime:stop`, `links:end`) so `/close-up` can make exact-string
  edits. Pages open over `file://`.
- **`prime:stop` within ~150 lines** so `/project`'s priming read is cheap.
- **Reading order = resume order** (identity → now → links → key files →
  recent activity).

## Usage
- `dashboard theme` — adjust colors/typography/spacing via the CSS variables at the
  top of `_style.css`; the whole system follows. Keep light + dark in sync.
- `dashboard template` — evolve `_template.html`. If you add an anchored region other
  skills should write to, name the anchor and note it in `AGENTS.md`.
- `dashboard index` — regenerate `projects/index.html` from the current project pages.
- `dashboard welcome` — tune what `/project` prints on focus.

## Notes
- Ships a good default; there is no live "pull" from upstream. Want a newer look?
  Restyle here — you won't clobber anyone, and no one clobbers you.
- Test a change by opening a project page in a browser — it's just a file.
