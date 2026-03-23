# 🧠 Today Agent Learned (TAL)

> A collection of concise write-ups on things I learn day to day while working with AI agents. Inspired by [jbranchaud/til](https://github.com/jbranchaud/til).

---

## Categories

- [Prompt Engineering](#prompt-engineering) — Interaction patterns, system prompts, structured outputs
- [Tool Use & MCP](#tool-use--mcp) — Model Context Protocol, tool design, server configs
- [Claude Code](#claude-code) — Agentic coding, CLI workflows, automation
- [Multi-Agent](#multi-agent) — Orchestration, delegation, agent-to-agent patterns
- [Custom Skills](#custom-skills) — Building plugins, skill design, packaging & sharing

---

### Prompt Engineering

- [Ask for a Plan Before Execution](01-prompt-engineering/ask-for-a-plan-before-execution.md)
- [Use XML Tags to Structure Complex Instructions](01-prompt-engineering/use-xml-tags-for-structure.md)

### Tool Use & MCP

- [MCP Servers Persist Within a Conversation](02-tool-use-mcp/mcp-servers-persist-within-conversation.md)
- [Design Tools with Clear Failure Modes](02-tool-use-mcp/design-tools-with-clear-failure-modes.md)

### Claude Code

- [Scope Agent Permissions with allowedTools](03-claude-code/scope-permissions-with-allowed-tools.md)
- [Use CLAUDE.md as Persistent Memory](03-claude-code/use-claude-md-as-persistent-memory.md)

### Multi-Agent

- [Fan-Out Then Synthesize for Research Tasks](04-multi-agent/fan-out-then-synthesize.md)

### Custom Skills

- [A SKILL.md is the Only Required File](05-custom-skills/skill-md-is-the-only-required-file.md)

---

## What is a TAL?

A TAL is a short, focused write-up about something you discovered while working with AI agents. The best TALs are:

- **Concise** — Under 200 words. If it needs more, it's a blog post.
- **Actionable** — Includes a code snippet, command, or concrete example.
- **Surprising** — Documents the non-obvious. Things that took you 30 minutes to figure out but should take the next person 30 seconds.
- **Honest** — "This didn't work" is just as valuable as "this worked great."

## Contributing

1. Fork this repo
2. Create a markdown file in the appropriate category folder
3. Use the [template](TEMPLATE.md) as a starting point
4. Add your entry to the README table of contents
5. Submit a PR

See [CONTRIBUTING.md](CONTRIBUTING.md) for full guidelines.

## Roadmap

| Phase                      | Status   | Description                              |
| -------------------------- | -------- | ---------------------------------------- |
| 📝 Personal TIL repo       | ✅ Now   | Publish learnings as markdown in GitHub  |
| 🌐 Community contributions | 🔜 Next  | Open PRs, add review guidelines          |
| 🤖 Agent-readable skill    | 🔮 Later | Package as a skill that agents can query |
| 🔍 Searchable website      | 🔮 Later | Static site with full-text search        |

## License

MIT — use these learnings however you want.
