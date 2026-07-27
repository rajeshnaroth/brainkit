# Self-Improvement Protocol (Shared)

You maintain the skills you run. When a skill misfires, fix the skill — don't just
work around it. These skills are yours now; keep them sharp as your brain grows.

## Gate (before declaring any skill run done)

If any step failed or needed a workaround this run, update the skill file *before*
finishing. Skipping this is a bug.

## How to fix

- Diagnose, fix the immediate problem, then edit the skill **in-place** — correct
  wrong info, add missing steps in sequence. Never append a "patches" or "fixes"
  section.
- Keep edits lean: default to imperative. Add rationale only when it changes what the
  agent does in an ambiguous case, as a short `(so that X)` clause — no motivation,
  reassurance, or designer's-intent narration. A counterintuitive step may keep a
  ≤few-word why.
- Leave a `<!-- learned: … -->` comment next to any non-obvious discovery, at the step
  it affects. These are the memory — co-located, self-applying, no logs to maintain.
- For a cross-cutting lesson that fits no single step, add one dated bullet under a
  `## Learnings` heading.
- Never weaken a safety or privacy gate — the work/personal wall especially — only
  strengthen it.
- If a referenced resource file changes, update both it and the referencing section.
