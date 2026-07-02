# Use CLAUDE.md as Persistent Memory

> **Category:** claude-code
> **Date:** 2026-03-20
> **Agent/Tool:** Claude Code

## The Problem

Every new Claude Code session starts from zero. The agent re-discovers your project structure, coding conventions, and preferences each time.

## What I Learned

A `CLAUDE.md` file in your project root acts as persistent memory. Claude Code reads it automatically at session start. Put your project context, conventions, and common commands here.

## Example

```markdown
# CLAUDE.md

## Project
This is a FastAPI backend for a SaaS billing system.

## Stack
- Python 3.12, FastAPI, SQLAlchemy 2.0, Pydantic v2
- PostgreSQL 16, Redis for caching
- pytest for tests, ruff for linting

## Conventions
- All endpoints go in `src/api/routes/`
- Use `Annotated[Depends(...)]` pattern for DI
- Every new endpoint needs a test in `tests/api/`

## Common Commands
- `make test` — run all tests
- `make lint` — ruff check + format
- `make migrate` — alembic upgrade head
```

The agent now starts every session already knowing your stack, your patterns, and how to run things.

## Why It Matters

10 minutes writing a good CLAUDE.md saves hours of repeated context-setting across sessions.

---

_Tags: `claude-code`, `memory`, `developer-experience`, `project-setup`_
