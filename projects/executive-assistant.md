# Executive Assistant · Multi-agent system

A personal executive assistant built in Claude Code as a real agent system rather
than a chat window with a long prompt.

---

## The problem with chat

A chat assistant forgets. Every conversation starts from zero, so you re-explain your
business, your priorities and your preferences before you can ask for anything. The
assistant helps you get 50% of the way there instead of 90%, and the gap is entirely
context you already provided last week.

## The architecture

```
CLAUDE.md              pointers, not content — loaded on every message
context/               who I am, the business, priorities, goals
.claude/
  rules/               one file per topic: tone, public voice, decision criteria
  skills/              invokable procedures with YAML front matter
  agents/              sub-agents with their own context window and model
projects/              one folder per active workstream, outputs live here
decisions/log.md       append-only: what was decided, and why
```

## Three design decisions

**The brain holds pointers, not content.** `CLAUDE.md` loads in full on every single
message, so putting the business context in it would burn the context window before
the first question. Instead it says *"if you need to know about priorities, read this
file."* Context is loaded on demand. The file stays under 150 lines while the system
knows everything.

**Skills and sub-agents are different tools.** A skill runs in the current context
with the current model — it is a procedure you want followed. A sub-agent gets a
fresh context window and can run a different, cheaper model — it is for work that
produces a lot of intermediate output nobody needs to see. Research that sweeps
twenty sources goes to a sub-agent; the main conversation gets the report, not the
process.

**Decisions are append-only.** `decisions/log.md` records what was decided and the
reasoning, and entries are never edited. When something changes, a new entry reverts
the old one and explains why. Six months later the reasoning is the valuable part —
"we tried this and it did not work because X" is expensive information to lose.

## Why it gets better with use

Every research report, draft and decision is written to a file inside the project.
Clear the conversation and the assistant picks up where it left off by reading them.
The system compounds instead of resetting.

---

`Claude Code` `Model Context Protocol` `Firecrawl` `Git`
