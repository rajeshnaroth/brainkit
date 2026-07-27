---
# profile.md — optional personalization for your second brain.
# Everything works out of the box; edit this only if you want to. The skills read
# these values at runtime, so personalizing means editing THIS file, not the skills.

# What the agent calls you. Leave as-is or change it anytime.
name: "you"

# Optional: how you'd like the agent to write in your voice. Delete if you don't care.
# tone: "plain and brief"
---

# Profile

This file is your brain's optional config — **data, not code**. There's no setup
interview; the brain ships ready to use. Come back and edit this whenever you want to
personalize it.

## Worlds are folders, not settings

Your two worlds live as folders under `wiki/` — `work/` (your default) and
`personal/` (a private wall). Nothing to configure here; where a page lives decides
its world. Want another walled world later (e.g. `confidential/`)? Add a sibling
folder with the same sub-categories.

## Facets — derived, not hand-maintained

The agent keeps a short, evolving vocabulary of topical tags ("facets") inferred from
the pages you create. They live on wiki pages as `facets: [...]`. You rarely touch
this directly; `/wiki-maintain` keeps it coherent.

## Backup — a later add-on

The brain stays local by default. Backing up to a private git repo is an opt-in step
you can set up whenever you like — just ask the agent to help you push it to git.
