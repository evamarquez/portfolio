# Agents

Systems where a model makes decisions inside a structure I designed.

The interesting part is never that an agent writes something. It is what you let it
decide and what you take out of its hands.

---

# ⭐ Newsletter Kit

**Say "I need a newsletter about X"** and the system researches the topic, writes the
issue, draws the data charts, generates the editorial illustration, renders email-safe
HTML and leaves a draft ready to send. It can also run itself on a schedule.

`Python` · `Jinja` · `Playwright` · `premailer` · `GitHub Actions` · `Cloudflare R2`
🟢 **[Public code](https://github.com/evamarquez/newsletter-kit)** · MIT

### The architecture

Built on the **WAT** pattern (Workflows, Agents, Tools): markdown SOPs describe the
work, the agent orchestrates, Python scripts execute. Probabilistic reasoning stays
where it helps; everything repeatable is deterministic code.

```
topic ─→ research_topic.py ──→ [issue.json] ──┬─→ make_infographic.py ──┐
         (5 parallel angles)   (schema-        │   (Playwright → PNG)    │
                                validated)     └─→ generate_image.py ────┤
                                                                         ↓
   log_issue.py ←── send_gmail.py ──────────────────── render_newsletter.py
   (archive)        (SMTP + inline CID images)          (Jinja + premailer)
```

### The two rules the design rests on

**The agent never writes HTML.** It produces a schema-validated `issue.json`, and
fixed Jinja templates render it. Email HTML is not web HTML: Outlook renders through
the Word engine, Gmail strips most of `<head>`, flexbox and grid are unusable.
Hand-generated markup breaks differently every issue. This split is why issue #1 and
issue #40 look identical, and why a visual bug is a one-file fix instead of a
re-prompt.

**Numbers never go inside a generated image.** A generative model cannot guarantee
that a bar drawn for 47% is proportionally 47%, and it can alter a digit invisibly.
Two separate lanes: one model draws concepts, a script draws data from the actual
values. The schema enforces it by rejecting digits in image prompts.

### Guardrails

Sending is the one irreversible action in the system, so it is guarded in layers:
brand-level send restriction, a scheduled workflow with no send flag anywhere, one
message per recipient rather than exposing the list, and a broken image reference
treated as a fatal error rather than a warning. A sent campaign cannot be recalled.

### Documented learnings

The README includes a section on what went wrong: Jinja autoescaping silently breaking
a CSS font stack, `strftime` using the machine's locale instead of the content's, CI
artifacts reporting success while uploading nothing. They are there because that is
the part that saves time for whoever builds something similar.

→ **[See the full repository](https://github.com/evamarquez/newsletter-kit)**

---

# ⭐ Executive Assistant

**A personal executive assistant built as a multi-agent system**, not a chat window
with a long prompt.

`Claude Code` · `Model Context Protocol` · `Firecrawl` · `Git`
🔒 Private repo, contains personal business context

### The problem with chat

A chat assistant forgets. Every conversation starts from zero, so you re-explain your
business, your priorities and your preferences before you can ask for anything. It
gets you 50% of the way there instead of 90%, and the gap is entirely context you
already provided last week.

### The architecture

```
CLAUDE.md          pointers, not content. Loaded on every message
context/           who I am, the business, priorities, goals
.claude/
  rules/           one file per topic: tone, public voice, decision criteria
  skills/          invokable procedures with YAML front matter
  agents/          sub-agents with their own context and model
projects/          one folder per active workstream, outputs live there
decisions/log.md   append-only: what was decided and why
```

### Three design decisions

**The brain holds pointers, not content.** `CLAUDE.md` loads in full on every message,
so putting business context in it would burn the window before the first question.
Instead it says *"if you need to know about priorities, read this file."* Context loads
on demand. The file stays under 150 lines and the system still knows everything.

**Skills and sub-agents are different tools.** A skill runs in the current context with
the current model: it is a procedure you want followed. A sub-agent gets a fresh
context window and can run a different, cheaper model: it is for work that produces a
lot of intermediate output nobody needs to see. Research that sweeps twenty sources
goes to a sub-agent; the main conversation gets the report, not the process.

**Decisions are append-only.** Entries are never edited. When something changes, a new
one reverts it and explains why. Six months later the reasoning is the valuable part:
*"we tried this and it did not work because X"* is expensive information to lose.

### Why it improves with use

Every report, draft and decision is written to a file inside the project. Clear the
conversation and the assistant picks up by reading them. The system compounds instead
of resetting.

---

# ⭐ Reporting agent

**Removed a recurring manual process end to end** at an SEO agency.

🏢 Client work · code not published

### The problem

A recurring report assembled by hand: pull the data, order it, format it, deliver it.
The kind of task that eats a predictable slice of every week and leaves nothing anyone
remembers doing.

### What I built

An agent that pulls the data from the sources, assembles the report and delivers it.

### Result

The manual process disappeared end to end. It was not reduced, it was removed.

### Design decision

**The agent presents the numbers, it does not interpret them.** Asking a model to draw
conclusions from performance data is asking it to invent a narrative. It extracts,
calculates and formats deterministically; the analysis is done by whoever knows the
client.

---

## Everything else

Claude Code skills built during a 7-day AI systems challenge:

| Skill | What it does |
|---|---|
| **Excalidraw diagrams** | Generates editable diagrams from a description |
| **Controlled image generation** | Parameterized JSON prompts for hyper-realistic images, avoiding the plastic AI look |
| **Frontend design** | Interfaces with real design judgment, avoiding generic output |
| **Video to website** | Turns a video into an animated scroll-driven site |

Each one with YAML front matter defining **when** to invoke it, not just what it does.
