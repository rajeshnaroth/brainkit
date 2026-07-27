# wiki/AGENTS.md — the SOP for this wiki

The single source of truth for how knowledge is captured and organized here. The
`wiki-*` skills (`wiki-ingest`, `wiki-query`, `wiki-maintain`) defer to this file;
if any skill conflicts with it, this file wins.

The wiki is an **LLM-maintained knowledge base**: small, cross-linked pages that an
agent writes and grooms so that "what do I know about X?" is always one query away.
Favor many small pages over few big ones. Never fabricate; link, don't duplicate.

## Worlds are folders — `work/` and `personal/`

The wiki is split into two top-level **worlds**, and the folder *is* the world:

- **`wiki/work/`** — your default. Everything goes here unless it's clearly personal.
- **`wiki/personal/`** — a private wall. Personal details live here and **never**
  surface in a work answer.

The path carries the world, so pages do **not** need a `world:` frontmatter field —
where the file lives decides which world it's in. The rule that makes the wall real:

> **Cross-reference operates *inside* a world and stops at the wall.** Link freely
> within `work/` and within `personal/`; **never** link a `work/` page to a
> `personal/` page or vice-versa. A work query never reads `personal/`.

Want a third walled world later (e.g. `confidential/`)? Add a sibling folder with the
same four sub-categories — the model extends unchanged.

## Directory = category. Put each page where its *purpose* fits.

Inside each world, the same four categories apply — a page lives at
`wiki/<world>/<category>/<slug>.md`:

| Category | Holds | Answers |
|---|---|---|
| `sources/` | Provenance — one page per source you read/heard (article, talk, chat, doc). What it is + key takeaways + a link. | "Where did I get this?" |
| `entities/` | The nouns — people, teams, products, tools, orgs, projects. | "Who/what is X?" |
| `concepts/` | Reusable ideas, patterns, how-tos — knowledge not tied to one source. | "How does X work? What's the pattern?" |
| `synthesis/` | Your own conclusions, decisions, strategy, opinions. | "What do I think? What did we decide?" |

A single raw input often yields **several** pages across categories — decompose it.

## Frontmatter (every page)

```yaml
---
title: Human-readable title
facets: [pricing, competitors]   # derived topical tags; 1–4 is plenty
created: 2026-07-26
updated: 2026-07-26
source: <url-or-name>  # sources/ pages only — where it came from
---
```

- No `world:` field — the world is the folder the page lives in (`work/` or
  `personal/`).
- **`facets`** are derived from the content; keep the vocabulary small and
  consistent. Reuse an existing facet before coining a new one.

## Naming

Kebab-case, descriptive, no dates in the name (dates live in frontmatter), always
under a world + category:
`work/entities/acme-corp.md`, `work/concepts/zero-based-budgeting.md`,
`work/synthesis/q3-pricing-decision.md`. `sources/` pages may keep a source slug:
`work/sources/hbr-pricing-2026.md`.

## Cross-linking

- On first mention of an entity/concept that has (or deserves) a page, link it with
  a relative path: `[Acme Corp](../entities/acme-corp.md)` (same world).
- **Never cross the world wall.** A `work/` page links only to other `work/` pages;
  a `personal/` page links only within `personal/`.
- Prefer linking over restating. If two pages keep repeating each other, one of them
  should become a link.
- Add a backlink when it genuinely helps navigation — don't link-spam.

## index.md and log.md

- **`index.md`** — the catalog, grouped **by world, then by category**. Update it
  whenever you create or rename a page. Most-relevant first within a group.
- **`log.md`** — append-only. One line per ingest or maintain batch:
  `- 2026-07-26 — ingested 3 raw notes → 2 concepts, 1 entity (work).`

## Raw lifecycle

`wiki/raw/` is a single shared inbox. `/note` and `/close-up` drop files there;
`/wiki-ingest` classifies each — **including which world it belongs to** — writes the
structured page(s) under `wiki/<world>/…`, then **moves the raw file to
`wiki/raw/processed/`** (never deletes it). Ambiguous or low-signal raw files: ask
before forcing a page. If a raw file is personal, route its pages into
`wiki/personal/` and keep them out of any work context.

## Workflows the skills follow

- **Ingest** (`/wiki-ingest`) — for each raw file: decide **world** (work by
  default; personal only when clearly personal or told so) → pick category(ies) →
  derive `facets` → write/merge page(s) under `wiki/<world>/…` → cross-link *within
  that world* → update `index.md` → move raw to `processed/`. Batch large sets and
  pause to report.
- **Query** (`/wiki-query`) — read-only, **work-scoped by default**: read only
  `wiki/work/…` unless the user explicitly asks about personal. Prefer
  `synthesis/`+`concepts/` for "what/how/pattern" questions, `entities/` for
  "who/what is X", `sources/` for provenance. Cite the pages you used. If coverage is
  thin, say so — don't guess.
- **Maintain** (`/wiki-maintain`) — propose-then-apply, **one world at a time**. Fix
  broken links, merge duplicates, split overloaded pages, prune stale ones
  (**archive, never delete**), refresh `index.md`. **Flag any link that crosses the
  work/personal wall** as an error to fix. Never merge across worlds. Be conservative
  with merges.
