# Use XML Tags to Structure Complex Instructions

> **Category:** prompt-engineering
> **Date:** 2026-03-20
> **Agent/Tool:** Claude (especially effective), works with others

## The Problem

Long system prompts with mixed concerns (rules, context, examples, output format) turn into a wall of text the model struggles to prioritize.

## What I Learned

Wrapping distinct sections in XML tags gives the model clear semantic boundaries. It's not just formatting — it measurably improves instruction-following on complex prompts.

## Example

```xml
<role>You are a code reviewer for a Python backend team.</role>

<rules>
- Flag any function longer than 50 lines
- Check for missing type hints
- Ignore test files
</rules>

<output_format>
Return a JSON array of findings:
[{"file": "...", "line": 0, "severity": "warn|error", "message": "..."}]
</output_format>

<context>
The codebase uses FastAPI, SQLAlchemy, and Pydantic v2.
</context>
```

This consistently outperforms the same content written as flat paragraphs because the model can "index" into sections rather than parsing a blob.

## Why It Matters

When your prompt grows past ~500 words, structure isn't cosmetic — it's functional. XML tags are the lowest-effort, highest-impact way to add it.

---

_Tags: `prompt-pattern`, `xml`, `system-prompt`, `claude`_
