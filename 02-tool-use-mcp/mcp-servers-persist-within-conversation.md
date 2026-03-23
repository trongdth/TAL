# MCP Servers Persist Within a Conversation

> **Category:** tool-use-mcp
> **Date:** 2026-03-20
> **Agent/Tool:** Claude.ai, any MCP-compatible client

## The Problem

I kept re-specifying my MCP server configuration in follow-up messages, thinking each turn was stateless.

## What I Learned

Once an MCP server is connected in a conversation, it stays available for all subsequent turns. You don't need to mention it again. But each **new** conversation starts fresh — there's no cross-session memory of which servers were connected.

## Example

```
Turn 1: "Connect to my Asana MCP server and list my tasks"
→ Agent connects, lists tasks ✅

Turn 2: "Mark the first one as complete"
→ Still connected, works fine ✅

New conversation: "Mark my Asana task as complete"
→ ❌ No MCP server connected — need to reconnect
```

## Why It Matters

Understanding the session lifecycle prevents both redundant setup (re-connecting every turn) and confusing failures (expecting persistence across conversations).

---

_Tags: `mcp`, `session-lifecycle`, `gotcha`_
