# AI & Automation Pipelines

Systems that remove repeated operational work and leave judgment with the people who
understand the business. The production automations are private when they contain
client workflows, credentials, internal IDs or proprietary process details.

---

# [AI Article Generation Pipeline](https://github.com/evamarquez/ai-content-pipeline-case-study)

**A multi-stage content production system that took articles from about two days to
minutes plus editor review.**

`Python` · `OpenAI` · `Perplexity` · `Google Workspace APIs` · `Airtable`
🏢 Client work · public showcase planned · production system private

### What it is

A pipeline for an agency serving 17+ e-commerce brands. The system took a topic and a
brand, gathered research, followed the brand's voice constraints, produced an outline,
drafted the article and delivered it into the team's editorial workflow.

It was not a single prompt. It was an operational system with multiple stages,
provider-specific responsibilities and handoff points for human editors.

### Result

- 549 articles produced across 882 jobs
- Median time from keyword to Google Doc: 4.7 minutes
- Production time reduced from about two days per article to minutes plus editor review
- Brand-specific constraints moved into configuration instead of being buried in prompts

### Design decisions

**Editor-in-the-loop by design.** Publishing was never automated. The system removed
research, structuring and formatting work, while final judgment stayed with the content
team.

**Provider responsibilities were separated.** Research, drafting and processing do not
need the same model or tool. The system used different providers where they fit best.

**Brand context lived outside the prompt.** One config file per brand made onboarding
new clients safer and easier than rewriting the pipeline.

### Public version

The sanitized architecture, reliability work and measurement corrections are documented
in the [public case study](https://github.com/evamarquez/ai-content-pipeline-case-study).

The showcase will use fake brands, mock research inputs, sample constraints and a
simplified draft flow. It will not include client names, production prompts, private
source documents or real article outputs.

---

# Full Client Lifecycle Automation

**Onboarding and offboarding automated end to end** across Slack, Google Drive,
Airtable and Fillout.

`Make` · `Slack API` · `Google Drive API` · `Airtable` · `Fillout`
🏢 Client work · case study only · blueprints private

### What it is

When a new agency client signed, about twenty operational steps had to happen in the
right order: validate intake data, create Slack channels, invite the right people,
create Drive folders, copy templates, write generated IDs back to Airtable and trigger
follow-up tasks.

Offboarding had its own chain: archive channels, move folders, update records and tell
operations what still required manual closure.

### Design decisions

**Idempotency over blind retries.** Every step checks whether its effect already exists
before running, so a retry does not create duplicate channels, folders or records.

**Manual leftovers are documented.** Some accesses and contracts require a human. The
automation ends by listing what remains instead of pretending the whole process is
fully automated.

---

# Reporting Agent

**Public access:** no public version yet. The production system remains private.

**Removed a recurring manual reporting process end to end.**

`Python` · data extraction · deterministic report assembly
🏢 Client work · public showcase planned · production system private

### What it is

A recurring report used to be assembled by hand: pull the data, organize it, format it
and deliver it. I built an agentic workflow that handled the repeatable parts and
produced the report reliably.

### Design decision

**The agent presents the numbers; it does not invent the narrative.** Data extraction,
calculation and formatting are deterministic. Interpretation stays with the person who
knows the client and the business context.

### Public version plan

The showcase can use fake CSVs, mock KPIs and a generated report example. It should
show the orchestration pattern without exposing client data, private dashboards or
performance results.

---

# SC Lead Finder

**Educational version:** [Lead Finder SOP](https://github.com/evamarquez/community-resources/tree/main/lead-finder)

**Finds local businesses with weak or missing websites and scores which product to
offer first.**

`TypeScript` · `Trigger.dev` · scheduled workflows
Private repo · public showcase planned

### What it is

A prospecting workflow for my agency. Every Monday, unattended, it evaluates local
businesses in South Carolina and returns an ordered list of opportunities.

The important part is not only finding leads. It scores what product makes sense for
each business: a website from scratch, ad support, lead capture improvements or a more
advanced automation offer.

### Design decisions

**It scores, not just lists.** A list of 200 businesses with no priority creates more
work. The value is the ranking and the reasoning.

**It runs without weekly babysitting.** If the workflow needs a person to move it
forward every Monday, it did not solve the problem.

### Public version plan

The showcase can use sample businesses, public/mock website data and a transparent
scoring model. It should not publish real prospect lists or outreach strategy.

---

# Payment Data Reconciliation

**Two complementary strategies for matching Stripe customers to internal records.**

`Make` · `Stripe API` · `Airtable`
🏢 Client work · case study only · blueprints private

### What it is

Billing and the internal CRM lived apart, so revenue reporting depended on matching
Stripe customers to Airtable records. I solved it with two automations: one to clean
the past, one to stop the problem from growing again.

### Design decision

**Clean the backlog and close the leak separately.** A real-time listener would not
fix the historic records. A bulk reconciliation would need to be repeated forever.
Together they made the problem stay solved.

---

## Catalog Sample

Across the engagement, I shipped 80+ automations and documented 40 with blueprints,
dependencies and migration notes. Examples include:

| Automation | What it does |
|---|---|
| **Backlink load balancing** | Assigns each backlink to the sprint slot with the lightest load |
| **Store monitor** | Watches Shopify theme changes and alerts on modification |
| **Inbox watcher** | Captures Ahrefs and Semrush reports, stores them and notifies the right channel |
| **Competitor RSS** | Reads competitor RSS feeds and stores new articles for review |
| **Sprint folder structure** | Generates Drive folder hierarchies when a sprint is created |
| **Per-page documents** | Copies the right template by page type and links the document to the record |
| **Monthly Slack report** | Assembles and sends a performance report by client and brand |
| **Weekly delivery digest** | Sends Friday summaries of backlinks and pages delivered |
| **Scraper with AI processing** | Scrapes a page, processes it and generates the working document |
| **Client subscenario** | Reusable component returning client and brand records for other automations |

### Operating principles

**Automate the repeatable, keep judgment human.** Every system removes mechanical work
and leaves the decision with a person.

**Write the SOP or it did not happen.** A system only one person can operate is a
liability. Documentation is part of delivery, not decoration.

**Document the bugs, including your own.** Known issues and migration notes make the
next operator safer.
