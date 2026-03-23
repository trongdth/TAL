# Design Tools with Clear Failure Modes

> **Category:** tool-use-mcp
> **Date:** 2026-03-20
> **Agent/Tool:** Any agent using function calling / tool use

## The Problem

My custom tool returned `null` on failure. The agent had no idea what went wrong and kept retrying the same call with the same parameters, burning through its loop budget.

## What I Learned

Tools should return **structured error messages** that tell the agent *what failed* and *what to try instead*. Agents can't debug silent failures, but they're surprisingly good at recovering from descriptive ones.

## Example

```json
// ❌ Bad: agent has no idea what happened
{ "result": null }

// ✅ Good: agent can adapt
{
  "error": "FILE_NOT_FOUND",
  "message": "No file at /data/report.csv",
  "suggestion": "Available files in /data/: ['summary.csv', 'report_v2.csv']"
}
```

With descriptive errors, the agent self-corrects on the next call ~80% of the time instead of looping.

## Why It Matters

A tool is only as useful as its error messages. When building for agents, design the unhappy path first.

---

_Tags: `tool-design`, `error-handling`, `function-calling`_
