# wiki-query

Answer a question grounded in the wiki, with citations. Follow the Query workflow in
[`wiki/AGENTS.md`](../wiki/AGENTS.md); if anything here conflicts, that file wins.

## Usage
- `wiki-query <question>` — answer from the wiki.
- `wiki-query <question> strict` — refuse if the wiki doesn't cover it (no outside
  knowledge).
- `wiki-query <question> trace` — also show which pages were read and why.

## Steps
1. If no question is given, ask for one — don't invent a query.
2. Locate relevant pages: prefer `synthesis/` + `concepts/` for "what/how/pattern"
   questions, `entities/` for "who/what is X", `sources/` for provenance. Read them.
3. Synthesize an answer and **cite the pages** inline.
4. If coverage is thin or missing, say so plainly and suggest what to capture — don't
   guess.
5. Read-only: never edit pages during a query. If you spot something wrong, note it
   at the end for `/wiki-maintain`.

## Notes
- `wiki/raw/` is pre-ingestion; only read it if asked, or if structured pages don't
  cover the topic.
