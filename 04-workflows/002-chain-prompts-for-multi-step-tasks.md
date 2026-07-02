# Chain Prompts for Multi-Step Tasks

> **Category:** workflow
> **Date:** 2026-07-01
> **Agent/Tool:** Any multi-agent framework (CrewAI, LangGraph, Autogen, custom)

## The Problem

A single prompt asked to do a complex, multi-step task at once (e.g. "research this topic, write an outline, then write a full draft") tends to produce weaker results — the LLM has to juggle every step's requirements simultaneously and quality drops on later steps.

## What I Learned

The "prompt chaining" pattern works better: break the task into a fixed sequence of LLM calls, where each step's output feeds directly into the next step's input. Optionally insert a programmatic "gate" between steps to validate the intermediate output before continuing — this catches errors early instead of letting them propagate to the final result.

## Example

```python
# Pseudocode for the pattern
outline = await outline_agent(f"Write an outline for: {topic}")

# Gate: validate before continuing the chain
if not has_required_sections(outline):
    raise ValueError("Outline missing required sections")

draft = await draft_agent(f"Expand this outline into a full draft:\n{outline}")
final = await polish_agent(f"Polish this draft for clarity and tone:\n{draft}")
```

Each step only has to do one thing well, and a bad outline never makes it to the drafting step.

## Why It Matters

Trading a single big call for a sequence of small, focused calls trades some latency for reliability — each step is easier for the LLM to get right, and gates let you fail fast instead of discovering the problem only in the final output.

---

_Tags: `workflow`, `pattern`, `chaining`, `sequential`_
