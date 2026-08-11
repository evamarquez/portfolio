# Agents

Systems where a model makes decisions inside a structure I designed. The important
question is not whether a model is involved; it is what the system lets the model
decide, what deterministic code handles, and where a human stays in control.

---

# Reporting Agent

**Removed a recurring manual reporting process end to end.**

`Python` · deterministic data processing · report assembly
🏢 Client work · public showcase planned · production system private

### What it is

A recurring report used to be assembled manually: pull the data, organize it, format
it and deliver it. I built an agentic workflow that removed the repeatable work from
the process.

The system pulls the required inputs, structures the report and delivers the output in
the format the team needs. It is designed around repeatability and auditability, not
around asking a model to improvise an explanation.

### Result

The manual process disappeared end to end. Not reduced. Removed.

### Design decision

**The agent presents the numbers; it does not interpret them.** Asking a model to draw
performance conclusions can turn reporting into storytelling. This system extracts,
calculates and formats deterministically; analysis stays with the person who knows the
client.

### Public version plan

The public showcase can use fake CSVs, mock KPIs and a generated report example. The
production version stays private because it contains client context, source mappings
and internal reporting logic.

---

# Executive Assistant

**A personal executive assistant built as a multi-agent operating system, not a chat
window with a long prompt.**

`Model Context Protocol` · `Git` · skills · sub-agents · persistent context
Private repo · showcase planned with personal context removed

### The problem with chat

A chat assistant forgets. Every conversation starts from zero, so you re-explain the
business, priorities and preferences before asking for anything useful.

The goal was to make the assistant compound over time: files hold context, projects
hold outputs, and decisions are logged so future work starts from what was already
learned.

### Architecture

```text
root instructions     pointers, not all context
context/              business, priorities, preferences, goals
rules/                one file per topic: tone, decision criteria, public voice
skills/               invokable procedures with clear trigger rules
agents/               sub-agents with focused context windows
projects/             active workstreams and outputs
decisions/log.md      append-only record of decisions and reversals
```

### Design decisions

**The main instruction file holds pointers, not content.** The assistant loads only
what it needs, when it needs it. That keeps the starting context small without making
the system ignorant.

**Skills and sub-agents solve different problems.** A skill is a procedure to follow
inside the current context. A sub-agent is useful when the task produces lots of
intermediate work that should not pollute the main conversation.

**Decisions are append-only.** When something changes, a new entry explains why. The
reasoning is often more valuable than the final answer.

### Public version plan

The public version should show the structure, not the private brain. It can include a
fake context pack, example skills, sample decision logs and a mock project folder.
Personal business context, private goals, client names and live integrations should be
removed.

---

# SC Lead Finder

**An unattended prospecting workflow that finds local businesses and ranks which offer
fits each one.**

`TypeScript` · `Trigger.dev` · scheduled workflows
Private repo · public showcase planned

### What it is

Every Monday, the workflow evaluates local businesses, checks the state of their web
presence and returns a prioritized list of opportunities.

The valuable part is the scoring. It does not only ask, “does this business need a
website?” It asks which product makes the most sense to approach with first.

### Design decisions

**An unordered list is not an outcome.** Sales does not need more raw names. It needs a
starting point and a reason.

**Unattended means no mid-run approval.** A scheduled automation that waits for a
person every week has only moved the work.

### Public version plan

The showcase can include fake businesses, a transparent scoring model, sample output
and the scheduled-job structure. It should not include real prospect lists or outreach
strategy.

---

# Newsletter Kit

**Say “I need a newsletter about X” and the system researches, writes, renders charts,
generates an illustration and leaves a draft ready to send.**

`Python` · `Jinja` · `Playwright` · `premailer` · `GitHub Actions` · `Cloudflare R2`
[Public code](https://github.com/evamarquez/newsletter-kit) · MIT

### Architecture

Built on the WAT pattern: workflows describe the work, the agent orchestrates, and
Python scripts execute deterministic steps.

```text
topic -> research -> schema-validated issue.json -> charts + illustration
      -> email-safe HTML -> draft delivery -> archive
```

### Design decisions

**The agent never writes HTML.** It produces structured data. Fixed templates render
email-safe markup, which keeps every issue consistent and makes visual bugs one-file
fixes.

**Numbers never go inside generated images.** A script draws charts from actual values.
Generated art stays conceptual.

**Sending has guardrails.** Scheduled runs create drafts, not live campaigns, and send
paths are restricted to avoid irreversible mistakes.

→ [See the full repository](https://github.com/evamarquez/newsletter-kit)

---

## Other Agent Work

| Project | What it shows | Public status |
|---|---|---|
| **Skills library** | Reusable procedures with trigger rules and structured instructions | Selected examples can be public |
| **Controlled image generation workflow** | Parameterized prompts and quality constraints | Case study possible |
| **Frontend design workflow** | Design critique and implementation guidance for generated UIs | Case study possible |
| **Video-to-website workflow** | Turns source media into an animated scroll-driven site | Case study possible |
