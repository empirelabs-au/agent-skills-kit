# Writing skills.md: the guide

This guide teaches the craft of writing a `skills.md` file. It assumes you have
an agent workflow in mind that repeats often enough to be worth packaging.

## What a skill is

A skill is a plain-text file that packages three things:

1. A **trigger**: the conditions under which the agent should load and use it.
2. A **procedure**: numbered steps that turn a fuzzy task into a checkable sequence.
3. A **memory**: pitfalls, verification steps, and conventions that prevent repeat mistakes.

An agent reads the file, decides whether the trigger matches the current task,
and follows the procedure. If the procedure is well written, the agent can
execute it without asking for clarification at every step.

## Anatomy of SKILL.md

Every skill starts with YAML frontmatter, then a markdown body.

### Frontmatter

```yaml
---
name: my-skill
description: Use when <trigger>. <one line on what the skill does>.
domain: my-domain
status: active
---
```

- `name`: lowercase, hyphens between words. This is the skill's identifier.
- `description`: the most important line in the file. It is what the agent
  reads to decide whether to load the skill. Front-load the trigger: "Use when
  X" beats "This skill provides utilities for X". If the description does not
  say when to use it, the agent will guess, and guesses are unreliable.
- `domain`: optional grouping. Useful when you have many skills.
- `status`: keep it simple. `active` for skills you use, `draft` for work in
  progress.

### Body

The body is plain markdown with a strict internal order:

1. **Purpose** (short): one paragraph on what the skill accomplishes.
2. **Steps** (numbered, imperative): the exact procedure. Write commands as
   concrete examples, not abstractions.
3. **Pitfalls**: the mistakes you have already made so the agent does not
   repeat them. This section is where a skill earns its keep.
4. **Verification**: how to confirm the skill worked. A skill without a
   verification step produces work you cannot trust.
5. **Related**: optional pointers to sibling skills, docs, or upstream sources.

## Rules that matter

### 1. Write the trigger, not the title

The description must answer "when would I reach for this?" in the first
sentence. A description like "Utilities for CSV files" is useless to an agent
deciding what to load. "Use when you need to parse, filter, or join CSV files
in a shell pipeline" is a decision you can make instantly.

### 2. Be imperative and concrete

Prefer:

> 1. Read the file with `read_file`.
> 2. Grep for `TODO` with `search_files`.
> 3. Report each match with its line number.

over:

> 1. Look at the file.
> 2. Search for any TODO comments.
> 3. Summarize what you find.

The first version leaves no ambiguity about which tool to call or what output
to produce. The second leaves the agent to guess, and every guess is a chance
to drift.

### 3. Document pitfalls you have actually hit

The best pitfall entries are specific:

> - PITFALL: `grep` on a directory with no matches returns exit code 1.
>   Handle the no-match case before asserting success.

Generic advice ("be careful with edge cases") adds nothing. Your own scar
tissue is the value.

### 4. End with verification

State how the agent proves the job is done:

> Verification: the report file exists, contains at least one line per match,
> and `wc -l` matches the grep count.

If the skill cannot be verified, say so honestly and describe what partial
confirmation looks like.

### 5. Keep it small

A skill should fit in one or two screens. If it is longer, split it: either
the trigger is too broad, or the procedure belongs in a reference file the
skill points to.

## A template

See `../template/SKILL.md` for a blank, commented template.

## Checklist before you publish

- [ ] Description starts with "Use when" and names the trigger.
- [ ] Steps are numbered and imperative, with concrete tool calls.
- [ ] Pitfalls are specific to this task, not generic advice.
- [ ] Verification step present.
- [ ] No secrets, no internal paths, nothing environment-specific.
- [ ] No em dashes (many style guides reject them; plain text stays portable).

## Common mistakes

1. **Title-first description**: naming the topic instead of the trigger.
2. **Prose instead of procedure**: paragraphs where numbered steps belong.
3. **No pitfalls**: the skill only knows the happy path.
4. **No verification**: the agent cannot tell success from failure.
5. **Over-scoping**: one skill for "everything related to X".

Write the skill you wish you had been given on day one, and the agent will
thank you by doing the job right the first time.
