# brainkit

A seed for your own **second brain** — a personal wiki + project workspace that an AI
agent builds and tends for you. Works for anyone: a CEO, an engineer, a head of
people. Once planted it grows its own shape; there's nothing to keep in sync with
this seed.

## Set it up (one line)

You need two things: an agent CLI (**Claude Code** or **GitHub Copilot CLI**) and
**git**.

In an empty folder, launch your agent and paste:

> **Build my second brain from github.com/rajeshnaroth/brainkit**

The agent fetches this seed, interviews you for about two minutes, generates your
brain in place, backs it up to a private git repo if you're signed in, and cleans up
after itself. No manual installs, no config files to hand-edit.

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
| `profile.md` | Your config — the one file that personalizes everything. |
| `wiki/` | Your knowledge base (`sources` · `entities` · `concepts` · `synthesis`) + its SOP. |
| `projects/` | HTML project pages (bookmarkable) + the portfolio index. |
| `skills/` | The SOPs the agent runs — canonical source; clone one to write your own. |
| `.claude/commands/` | Thin stubs so Claude Code / Copilot CLI auto-discover the skills above as invocable commands. |

## The idea

Two superpowers, in tension by design: **focus** (work deep in one project) and
**cross-reference** (surface a theme across everything). Knowledge stays durable and
structured; work stays focused and resumable. Your agent does the filing so you
don't.

---
_A seed, not a framework. Fork it, restyle it, make it yours._
