# Use XML Tags to Structure Complex Instructions

> **Category:** prompt-engineering
> **Date:** 2026-03-31
> **Agent/Tool:** Claude (especially effective), works with others

## The Problem

Standard Claude responses sometimes fall short on complex multi-step reasoning tasks, and you need more accuracy without sacrificing transparency into how the model arrived at its answer.

## What I Learned

- Extended thinking = Claude's "scratch paper" — the model reasons through a problem first, then generates a final response.

- Response structure changes from a simple text block to two parts: a thinking block (reasoning trace) + a text block (final answer).

- A cryptographic signature is attached to each thinking block — this prevents tampering with Claude's reasoning chain, which could steer the model unsafely.

- Redacted thinking blocks appear when internal safety systems flag the reasoning; the content is encrypted but can still be passed back in multi-turn conversations without losing context.

- When to use it: run your prompts without thinking first → optimize your prompt → only then enable extended thinking if accuracy still falls short.

- Trade-offs to weigh: higher token cost, increased latency, and more complex response parsing.

## Example

```python
import anthropic

client = anthropic.Anthropic()

def chat(
    messages,
    system=None,
    temperature=1.0,       # must stay at 1.0 when thinking=True
    stop_sequences=[],
    tools=None,
    thinking=False,
    thinking_budget=1024   # minimum: 1024; must be < max_tokens
):
    params = {
        "model": "claude-opus-4-5",
        "max_tokens": thinking_budget + 1024,  # must exceed thinking_budget
        "messages": messages,
    }

    if system:
        params["system"] = system

    if thinking:
        params["thinking"] = {
            "type": "enabled",
            "budget_tokens": thinking_budget
        }

    response = client.messages.create(**params)
    return response

# --- Basic usage ---
messages = [{"role": "user", "content": "Solve this step by step: ..."}]
response = chat(messages, thinking=True, thinking_budget=2048)

# --- Parse the structured response ---
for block in response.content:
    if block.type == "thinking":
        print("REASONING:", block.thinking)      # may be redacted
        print("SIGNATURE:", block.signature)     # cryptographic token
    elif block.type == "text":
        print("ANSWER:", block.text)

# --- Force a redacted thinking block (testing only) ---
test_messages = [{
    "role": "user",
    "content": "ANTHROPIC_MAGIC_STRING_TRIGGER_REDACTED_THINKING_46C9A13E"
}]
test_response = chat(test_messages, thinking=True)
# → Returns an encrypted thinking block; verify your app handles it gracefully
```

## Why It Matters

Use extended thinking when standard prompting + prompt optimization still can't reach your accuracy target on complex reasoning tasks — it's the last-resort upgrade, not the default.

---

_Tags: `extended-thinking`, `claude`, `advanced-prompting`, `reasoning` _
