# Eva Marquez

**AI Solutions Engineer · Automation & Internal Tools**

I build the systems that make manual work disappear. Over the last year I shipped
80+ automations into production: agents that generate content, schedulers that
publish across nine platforms daily, and internal tools that replaced the
spreadsheets a whole team was running on.

I did not come to this from engineering. I came from running things — I founded and
scaled an e-commerce company, coordinated 120+ agency projects, and ran international
procurement. That is why the systems I build solve business problems and not just
technical ones.

📍 South Carolina, US · Remote · Authorized to work in the US without sponsorship
🌐 [by-evamarquez.com](https://www.by-evamarquez.com/) ·
💼 [LinkedIn](https://www.linkedin.com/in/byevamarquez/) ·
✉️ evapatriciamarquez@gmail.com

---

## Selected work

### 📰 [Newsletter Kit](https://github.com/evamarquez/newsletter-kit) · Python · Open source

Say *"I need a newsletter about X"* and it researches the topic across five parallel
angles, writes the issue, draws the data charts, generates the editorial illustration,
renders email-safe HTML, and leaves a draft ready to send. It can also run itself on
a schedule.

The interesting part is not that an agent writes a newsletter. It is the two rules
that keep the output stable across forty issues:

- **The agent never writes HTML.** It emits a schema-validated `issue.json`; fixed
  Jinja templates render it. Email HTML is not web HTML — Outlook renders through the
  Word engine, Gmail strips most of `<head>`, flexbox and grid are unusable.
  Hand-generated markup breaks differently every issue. This split is why a visual
  bug is a one-file fix instead of a re-prompt.
- **Numbers never go inside a generated image.** A generative model cannot guarantee
  a bar drawn for 47% is proportionally 47%, and it can alter a digit invisibly. Two
  separate lanes: one model draws concepts, a script draws data from actual values.
  The schema enforces it by rejecting digits in image prompts.

Sending is the one irreversible action in the system, so it is guarded in layers:
brand-level send restrictions, a scheduled workflow with no send flag anywhere, one
message per recipient rather than a shared `To:`, and a dangling image reference
treated as fatal rather than a warning.

`Python` `Jinja` `Playwright` `premailer` `GitHub Actions` `Cloudflare R2`

→ [Read the full README](https://github.com/evamarquez/newsletter-kit)

---

### ⚙️ [Automation systems at scale](projects/automation-systems.md)

80+ automations shipped into production for an agency running 17+ e-commerce brands
across the US, Australia and the UK. Article generation that went from two days to
minutes. A scheduler covering nine platforms daily. A custom CRM that replaced the
team's Airtable. A reporting agent that removed a manual process end to end.

→ [How they were built](projects/automation-systems.md)

---

### 🤖 [Executive Assistant](projects/executive-assistant.md) · Multi-agent system

A personal executive assistant built as a real agent system rather than a chat
window: persistent context files, scoped rule files, invokable skills, and a
sub-agent running on a smaller model so heavy research never pollutes the main
context. Everything version controlled.

→ [Architecture and design decisions](projects/executive-assistant.md)

---

### 🎯 SC Lead Finder · TypeScript · Trigger.dev

Weekly unattended automation that finds local businesses in South Carolina with poor
or missing websites and scores which product to approach them with. Runs every Monday
without supervision.

*Private repository — available on request.*

---

## What I work with

| | |
|---|---|
| **AI & Agents** | RAG, multi-agent systems, LangChain, LangGraph, Model Context Protocol, prompt engineering, vector databases (Chroma, FAISS), Claude Code |
| **Automation** | Make, Trigger.dev, scheduled workflows, API integration, webhooks, GitHub Actions |
| **Engineering** | Python, TypeScript, JavaScript, Git, REST APIs |
| **Data & platforms** | Airtable, Supabase, Lovable, Vercel, Netlify, Cloudflare, Stripe |
| **Delivery** | Agile, Kanban, RACI, SOP design, stakeholder management, risk matrices |

---

## Background

**MBA** — Florida Global University
**B.S. International Trade** — Universidad Alejandro de Humboldt

**IBM RAG and Agentic AI Professional Certificate** — *in progress*
**Google Project Management Professional Certificate**

English (C1) · Spanish (native) · French (B1)

---

## Currently

Open to remote **AI Solutions Engineer**, **AI Automation Engineer** and
**Implementation Engineer** roles in the US.

If you are building something where the hard part is making AI actually reliable in
production, I would like to hear about it.
