# Route Inputs to Specialized Prompts

> **Category:** workflow
> **Date:** 2026-07-01
> **Agent/Tool:** Any multi-agent framework (CrewAI, LangGraph, Autogen, custom)

## The Problem

A single generic prompt handling many different kinds of input (e.g. a support bot fielding billing, technical, and general questions) ends up mediocre at all of them — it's full of conditional instructions trying to cover every case at once.

## What I Learned

The "routing" pattern works better: classify the input first, then send it down a specialized path built for that category. Each path can have its own focused prompt, and even its own model — a cheap/fast model for simple categories, a stronger model for complex ones.

## Example

```python
# Pseudocode for the pattern
category = await classifier_agent(f"Classify this request: {request}")

if category == "billing":
    response = await billing_agent(request)
elif category == "technical":
    response = await technical_agent(request)
else:
    response = await general_agent(request)
```

The classifier's only job is picking a category; each downstream agent only has to be good at one kind of request.

## Why It Matters

Specialized prompts outperform one-size-fits-all prompts, and routing lets you optimize cost and quality independently per category instead of paying for a powerful model on every request regardless of complexity.

---

_Tags: `workflow`, `pattern`, `routing`, `classification`_
