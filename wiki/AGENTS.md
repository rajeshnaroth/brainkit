# wiki/AGENTS.md — the SOP for this wiki

The single source of truth for how knowledge is captured and organized here. The
`wiki-*` skills (`wiki-ingest`, `wiki-query`, `wiki-maintain`) defer to this file;
if any skill conflicts with it, this file wins.

The wiki is an **LLM-maintained knowledge base**: small, cross-linked pages that an
agent writes and grooms so that "what do I know about X?" is always one query away.
Favor many small pages over few big ones. Never fabricate; link, don't duplicate.

## Directory = category. Put each page where its *purpose* fits.

| Dir | Holds | Answers |
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
world: work            # one of profile.md's worlds
facets: [pricing, competitors]   # derived topical tags; 1–4 is plenty
created: 2026-07-26
updated: 2026-07-26
source: <url-or-name>  # sources/ pages only — where it came from
---
```

- **`world`** is mandatory and must match a world in `profile.md`. Never let a
  `confidential` page mix with another world (own file, own links only).
- **`facets`** are derived from the content + your `domain`; keep the vocabulary
  small and consistent. Reuse an existing facet before coining a new one.

## Naming

Kebab-case, descriptive, no dates in the name (dates live in frontmatter):
`entities/acme-corp.md`, `concepts/zero-based-budgeting.md`,
`synthesis/q3-pricing-decision.md`. `sources/` pages may keep a source slug:
`sources/hbr-pricing-2026.md`.

## Cross-linking

- On first mention of an entity/concept that has (or deserves) a page, link it with
  a relative path: `[Acme Corp](../entities/acme-corp.md)`.
- Prefer linking over restating. If two pages keep repeating each other, one of them
  should become a link.
- Add a backlink when it genuinely helps navigation — don't link-spam.

## index.md and log.md

- **`index.md`** — the catalog, grouped by category (and, if you use multiple
  worlds, sub-grouped or tagged by world). Update it whenever you create or rename a
  page. Most-relevant first within a group.
- **`log.md`** — append-only. One line per ingest or maintain batch:
  `- 2026-07-26 — ingested 3 raw notes → 2 concepts, 1 entity.`

## Raw lifecycle

`wiki/raw/` is the inbox. `/note` and `/close-up` drop files there;
`/wiki-ingest` classifies each, writes the structured page(s), then **moves the raw
file to `wiki/raw/processed/`** (never deletes it). Ambiguous or low-signal raw
files: ask before forcing a page.

## Workflows the skills follow

- **Ingest** (`/wiki-ingest`) — for each raw file: pick category(ies) → derive
  `world` + `facets` → write/merge page(s) → cross-link → update `index.md` → move
  raw to `processed/`. Batch large sets and pause to report.
- **Query** (`/wiki-query`) — read-only. Prefer `synthesis/`+`concepts/` for
  "what/how/pattern" questions, `entities/` for "who/what is X", `sources/` for
  provenance. Cite the pages you used. If coverage is thin, say so — don't guess.
- **Maintain** (`/wiki-maintain`) — propose-then-apply. Fix broken links, merge
  duplicates, split overloaded pages, prune stale ones (**archive, never delete**),
  refresh `index.md`. Be conservative with merges.
