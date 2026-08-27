---
name: my-skill-name
description: Use when <the trigger. Name the situation, not the topic>. <One sentence on what the skill does>.
domain: <optional grouping, e.g. devops or data>
status: active
---

# My Skill Name

One paragraph: what this skill accomplishes and when the agent should reach
for it. If the trigger in the description fires, this body must deliver.

## Steps

1. First step. Write it as an imperative with a concrete tool or action:
   "Read the file with `read_file`", not "Examine the file".

2. Second step. Keep the procedure deterministic. Every command or tool call
   should be unambiguous enough that two agents would run it identically.

3. Third step. If the task branches (edge cases, error paths), say so here:
   "If X, do Y. Otherwise continue to step 4."

4. Final step. State the exact output shape the user expects, e.g. "Return a
   report with one line per match".

## Pitfalls

- PITFALL: <the mistake, stated specifically>. <What to do instead>.
- PITFALL: <another real mistake from experience>. <What to do instead>.
- PITFALL: <generic advice is useless, be specific>. <What to do instead>.

## Verification

How the agent proves the work is done: file exists, count matches, output
parses, tests pass, or an explicit honest description of what partial
confirmation looks like when full verification is impossible.

## Related

- Optional pointers to sibling skills, docs, or upstream sources.
- Remove this section if there is nothing useful to link.
