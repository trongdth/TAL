# Use XML Tags to Structure Complex Instructions

> **Category:** prompt-engineering
> **Date:** 2026-03-31
> **Agent/Tool:** Claude (especially effective), works with others

## The Problem

Claude behaves like a brilliant new employee with no context on your norms, workflows, or expectations. Vague or ambiguous prompts lead to generic, off-target outputs.

## What I Learned

- Give context, not just commands — explain why the task exists, who the audience is, and where this fits in your workflow. Claude performs better when it understands the end goal.

- State the desired output format explicitly — if you want only code, only JSON, or a 3-bullet summary, say so directly; Claude will not infer your preference from tone alone.

- Use numbered or sequential steps — breaking instructions into an ordered list reduces ambiguity and ensures Claude follows your exact intended flow.

- Be specific over polite — replace soft phrases like "maybe include…" or "feel free to…" with firm directives: "Include X. Do not include Y."

- Request "above and beyond" explicitly — Claude defaults to a safe, minimal interpretation; if you want thorough or creative output, ask for it outright.

## Example

```markdown
# ❌ Vague

Summarize this feedback.

# ✅ Clear, Direct, Specific

You are processing raw customer feedback for a B2B SaaS product.
Task: Anonymize and summarize the feedback below.

Follow these steps in order:

1. Remove all names, company names, and email addresses — replace with [REDACTED].
2. Write a 2-sentence summary of the core complaint or praise.
3. Assign one of these sentiment labels: Positive | Neutral | Negative.
4. Output only a JSON object with keys: "anonymized_text", "summary", "sentiment".
   Do not include any preamble or explanation outside the JSON.

<feedback>
Hi, I'm Jane from Acme Corp (jane@acme.com). The dashboard is super slow
and my team can't export reports reliably. Very frustrating.
</feedback>
```

## Why It Matters

Explicit, context-rich prompts cut down on retry loops, reduce hallucinations, and directly translate to faster, cheaper, production-ready outputs at scale.

---

_Tags: `prompt-engineering`, `claude`, `best-practices` _
