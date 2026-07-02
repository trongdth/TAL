# Fan-Out Then Synthesize for Research Tasks

> **Category:** workflow
> **Date:** 2026-03-20
> **Agent/Tool:** Any multi-agent framework (CrewAI, LangGraph, Autogen, custom)

## The Problem

A single agent doing sequential research (search → read → search → read) is slow and gets tunnel vision — it follows one thread and misses the bigger picture.

## What I Learned

The "fan-out / synthesize" pattern works dramatically better for research: spawn N agents in parallel, each exploring a different angle, then have a synthesizer agent combine their findings.

## Example

```python
# Pseudocode for the pattern
research_angles = [
    "technical feasibility of X",
    "market size and competitors for X",
    "regulatory risks for X",
    "user sentiment about X on forums"
]

# Fan out: parallel execution
findings = await asyncio.gather(*[
    research_agent(angle) for angle in research_angles
])

# Synthesize: one agent combines everything
report = await synthesizer_agent(
    f"Combine these findings into a balanced analysis:\n"
    f"{format_findings(findings)}"
)
```

The parallel agents finish in the time of the slowest one (not the sum), and the synthesizer catches contradictions between sources that a single agent would miss.

## Why It Matters

This is the multi-agent pattern with the best effort-to-quality ratio. Start here before reaching for complex agent graphs.

---

_Tags: `multi-agent`, `pattern`, `research`, `parallelism`_
