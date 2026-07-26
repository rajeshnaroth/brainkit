---
# profile.md — the ONE config for your second brain.
# The onboarding interview fills this in. Everything else (skills, wiki, project
# pages) reads from here at runtime, so personalizing your brain means editing
# THIS file, not the skills. Keep it short and true.
name: "{{YOUR_NAME}}"
role: "{{YOUR_ROLE}}"          # e.g. "CEO" · "Staff Engineer" · "Head of People"

# One or two plain sentences describing what you actually work on. The system
# DERIVES your facets (topical tags) from this — you never enumerate them.
domain: >
  {{DESCRIBE_WHAT_YOU_WORK_ON}}

# Worlds = the coarse top-level boundaries of your work/life. Set during
# onboarding. Most people start with one. Add "confidential" only if you handle
# sensitive material that must never mix with the rest (HR, legal, M&A, etc.).
worlds:
  - work

# Optional. How you like the agent to write in your voice. Delete if you don't care.
tone: >
  {{HOW_YOU_LIKE_TO_BE_WRITTEN_FOR}}

# Set automatically during onboarding if you're signed in to a git host; else empty.
backup:
  remote: "{{GIT_REMOTE_OR_EMPTY}}"
---

# Profile

This file is your brain's configuration. It is **data, not code** — the skills stay
generic and read these values. Edit it whenever your role, focus, or worlds change;
nothing else needs to change with it.

## Facets — derived, not hand-maintained

The agent keeps a short, evolving vocabulary of topical tags ("facets") inferred
from your `domain` and the pages you create. They live on wiki pages as
`facets: [...]`. You rarely touch this directly; `/wiki-maintain` keeps it coherent.
