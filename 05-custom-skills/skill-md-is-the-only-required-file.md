# A SKILL.md is the Only Required File

> **Category:** custom-skills
> **Date:** 2026-03-20
> **Agent/Tool:** Claude Skills system

## The Problem

I thought building a custom skill required a complex setup — manifest files, package configs, registries. I kept overthinking the structure.

## What I Learned

A skill is just a folder with a `SKILL.md` file. That's the only required file. The SKILL.md contains the instructions the agent reads before executing. Everything else (scripts, references, assets) is optional supporting material.

## Example

```
my-skill/
├── SKILL.md            # ← Required: instructions for the agent
├── scripts/            # ← Optional: script files
├── references/         # ← Optional: reference files
└── assets/             # ← Optional: asset files
```

Minimal `SKILL.md`:

```markdown
---
name: my-cool-skill
description: Generates changelog entries from git commits.
---

## Instructions

1. Run `git log --oneline` to get recent commits
2. Group commits by type (feat, fix, chore)
3. Write a changelog entry in Keep a Changelog format

## Output

Save the result as `CHANGELOG-new.md`
```

The agent reads SKILL.md, follows the instructions, and uses any supporting files you've included. No build step, no manifest, no registry.

## Why It Matters

The barrier to creating a skill is literally one markdown file. Start there and add complexity only when you need it.

---

_Tags: `skills`, `getting-started`, `minimal-viable`_
