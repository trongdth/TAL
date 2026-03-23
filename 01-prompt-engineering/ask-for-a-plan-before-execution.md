# Ask for a Plan Before Execution

> **Category:** prompt-engineering
> **Date:** 2026-03-20
> **Agent/Tool:** Claude, GPT-4, any agentic LLM

## The Problem

Giving an agent a complex multi-step task often results in wasted tool calls, backtracking, and context window burn when it realizes halfway through that its approach was wrong.

## What I Learned

Adding "outline your plan first, then execute" to your prompt dramatically reduces wasted cycles. The agent catches logical errors in the planning phase — before it starts burning tokens on file reads, API calls, and code execution.

## Example

```
❌ "Refactor the auth module to use JWT tokens"

✅ "Refactor the auth module to use JWT tokens.
    First, outline the files you'll change and your approach.
    Then execute step by step."
```

The second version typically uses 30–50% fewer tool calls because the agent maps out dependencies before touching anything.

## Why It Matters

In agentic coding, each wrong turn costs real context window space. Planning is nearly free compared to undoing bad edits.

---

_Tags: `prompt-pattern`, `efficiency`, `agentic-coding`_
