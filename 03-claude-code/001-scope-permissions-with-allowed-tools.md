# Scope Agent Permissions with allowedTools

> **Category:** claude-code
> **Date:** 2026-03-20
> **Agent/Tool:** Claude Code CLI

## The Problem

Running Claude Code in CI/CD with full tool access is risky. One hallucinated `rm -rf` or unintended network call can ruin your day.

## What I Learned

The `--allowedTools` flag lets you restrict exactly which tools the agent can use. This is essential for automated pipelines where you want the agent to read and suggest but never execute destructive operations.

## Example

```bash
# Read-only analysis: can view files and search, but can't edit or run commands
claude --allowedTools "view,web_search" \
  "Review this PR for security issues"

# Safe editing: can view and edit, but no shell access
claude --allowedTools "view,str_replace,create_file" \
  "Fix the type errors in src/auth.ts"

# Full power (default, for interactive use only)
claude "Refactor the payment module"
```

## Why It Matters

Least-privilege isn't just a security principle for humans. Agents should get the minimum tools needed for the job, especially in unattended automation.

---

_Tags: `claude-code`, `security`, `ci-cd`, `permissions`_
