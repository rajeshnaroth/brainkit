# SEED.md — run this once to grow a second brain, then delete yourself

You are an AI agent (Claude Code, Copilot CLI, …) setting up a personal **second
brain** for the human in front of you, from the `brainkit` seed. Do it
conversationally — warm, brief, and assume the user may be non-technical. Offer a
smart default at every step; never make them fill a long form. The whole thing
should feel like a two-minute chat, not an install.

**Ask in plain chat text, never a tool-driven multiple-choice/key-select UI.** If
your environment offers a built-in "ask user" or interactive-picker tool, do not use
it for this interview — type the question and the suggested default as an ordinary
chat message and let the user reply in their own words. Popups lose context once
dismissed and feel like a form, which is exactly what this is not supposed to be.
This applies to every question this file asks, not just the interview below.

## 0. Orient
- Confirm you're in the folder the user wants their brain to live in. If it already
  contains a filled `profile.md`, stop and ask — don't overwrite an existing brain.
- This tree was fetched from the seed. Re-init a clean history so the brain has no
  upstream and no seed remote: `rm -rf .git && git init -q`.

## 1. Interview — the only required input (~5 answers)
Ask one at a time, plain language, each with a suggested default:
1. **Name** — "What should I call you?"
2. **Role** — "What's your role, in a few words?" (CEO, engineer, head of people…)
3. **Domain** — "In a sentence or two, what do you spend your time on?" You will
   **derive facets** from this — never ask the user for tags.
4. **Worlds** — "Want anything walled off from the rest — confidential HR, legal, or
   deal work?" Yes → add a `confidential` world alongside `work`. No → a single
   `work` world. That is the only worlds question.
5. **Projects** — "Name two to four things you're actively working on." → starter
   projects.

Offer but don't force: preferred **tone/voice**.

## 2. Generate
- Fill `profile.md` with name, role, domain, worlds, (optional) tone.
- For each starter project, run the `project add` flow in `skills/project.md`: copy
  `projects/_template.html`, fill it, register it in `projects/index.html`. Then
  **delete the example** (`projects/example-q3-strategy.html`) and its index row.
- Optionally seed one real wiki page if the domain hands you something durable.
- Stamp today's date into `wiki/log.md`'s init line.

## 3. Back up — automatic, don't ask which
- Check for a signed-in git host (`gh auth status`, or a configured git identity).
  - **Authenticated to a personal host** → create a **private** repo and push. If the
    only authed host is an employer/enterprise one, confirm the target once before
    pushing a personal brain into a work org.
  - **Not authenticated / no `gh`** → stay local. Mention once that they can back up
    later by signing in and asking you to push.
- Record the result in `profile.md`'s `backup.remote`.

## 4. Self-delete + first commit
- **Delete this file (`SEED.md`)** — its job is done; `AGENTS.md` is the durable
  constitution that stays.
- Commit everything: `Grow second brain from brainkit`.

## 5. Payoff — show, don't tell
- Open `projects/index.html` in the browser (it's a real file) and tell them to
  bookmark it — that's their dashboard.
- Run one real action end to end: "Say `note` and tell me one thing worth
  remembering," then `wiki-query` it back so they see the loop close.
- Give them the one habit that matters: **start each session by `cd`-ing into this
  folder and launching your agent. You land at root; say `project <name>` to focus.**

## Acceptance criteria — verify before you call it done
- [ ] `profile.md` has real values; no `{{TOKENS}}` remain.
- [ ] At least one real project page exists and is registered in
      `projects/index.html`; the example project is gone.
- [ ] `wiki/` skeleton intact; `log.md` init line is dated.
- [ ] `.claude/commands/*.md` stubs are present (they ship with the seed and need no
      changes) so skills are actually invocable, not just documented in `skills/`.
- [ ] Backup pushed, OR explicitly left local with the user informed.
- [ ] `SEED.md` deleted and a first commit exists.
- [ ] You demonstrated one working action (note/query, or a project focus).
