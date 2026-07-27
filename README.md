# brainkit

A seed for your own **second brain** — a personal wiki + project workspace that an AI
agent builds and tends for you. Works for anyone: a CEO, an engineer, a head of
people. Once planted it grows its own shape; there's nothing to keep in sync with
this seed.

## Set it up

You need an agent CLI (**Claude Code** or **GitHub Copilot CLI**) and **git**.

Clone the seed in one shot, then step in:

```sh
git clone https://github.com/rajeshnaroth/brainkit.git my-second-brain
cd my-second-brain
```

Now launch your agent in that folder and say:

> **Set up my second brain** (follow `SEED.md`)

It detaches the seed from brainkit, sets up your two worlds — **work** and
**personal** — prints a short welcome, and deletes the seed instructions. No
interview, no config to hand-edit, and no git repo assumed — the brain is just a local
folder. Back it up to a private git repo later, whenever you like.

> **First run only:** your agent doesn't trust a freshly cloned folder yet, so it will
> ask to approve setup's handful of edits. Pick **"allow all edits during this
> session"** once (Claude Code: option 2 / shift+tab) and it finishes quietly. The
> shipped `.claude/settings.json` keeps later sessions quiet on its own.

> Clone it — don't ask the agent to "fetch" the repo. A single clone pulls the whole
> tree at once; fetching file-by-file is slow and triggers an approval per file.

## Using it day to day

Start every session by `cd`-ing into your brain's folder and launching your agent.
You land at **root** — the global view. From there:

- `project <name>` — focus one project (its state, links, and files at hand).
- `note` — capture a thought into your wiki.
- `wiki-query <question>` — ask your own knowledge base, with citations.
- `close-up` — end a session: it records what happened and files your next steps.

Open `projects/index.html` in a browser and bookmark it — that's your dashboard.

## What's inside

| Path | What |
|---|---|
| `AGENTS.md` | The constitution every agent follows — model, skills, conventions. |
| `profile.md` | Optional personalization — everything works without touching it. |
| `wiki/` | Your knowledge base, split into two worlds: `work/` and `personal/` (each with `sources` · `entities` · `concepts` · `synthesis`), plus its SOP. |
| `projects/` | HTML project pages (bookmarkable) + the portfolio index. |
| `skills/` | The SOPs the agent runs — canonical source; clone one to write your own. |
| `.claude/` | `commands/` — thin stubs so Claude Code / Copilot CLI auto-discover the skills; `settings.json` — sane permissions so you're not flooded with approvals. |

## The idea

Two superpowers, in tension by design: **focus** (work deep in one project) and
**cross-reference** (surface a theme across everything). Knowledge stays durable and
structured; work stays focused and resumable. Your agent does the filing so you
don't.

---
_A seed, not a framework. Fork it, restyle it, make it yours._
