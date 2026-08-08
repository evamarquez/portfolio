# Automations

Systems that run on their own and give somebody hours back every week.
Ordered by complexity, not by where I built them.

---

# ⭐ Full client lifecycle

**Onboarding and offboarding automated end to end**, orchestrating Slack, Google
Drive, Airtable and Fillout in a single chain.

`Make` · `Slack API` · `Google Drive API` · `Airtable` · `Fillout`
🏢 Client work · blueprints not published

### What it is

When an agency signs a new client there are about twenty things that have to happen,
in order, without a single one being forgotten. And when a client leaves, another
twenty. All of it was done by hand, with a checklist, and steps got missed.

I turned it into an automated chain.

**When a client comes in:**
1. The onboarding form arrives, the ID is validated and the data loaded
2. Slack channels get created, internal and shared with the client
3. The right people are invited to each channel
4. The client folder is created in Drive, with 4+ templates already copied in
5. Every generated ID is written back to Airtable
6. The PR document bookmark is added to the client channel
7. When the client accepts the Slack invite, that fires the welcome message, assigns
   the technical audit to the developer, creates the task in Airtable, and notifies
   the founder for the billing documents

**When a client leaves:**
Channels are archived, the folder moves to "Archived Brands", the offboarding flags
update in Airtable, and operations gets notified with **the checklist of what stays
manual**.

### Design decisions

**Idempotency over retries.** These chains touch external systems that fail. Every
step checks whether its effect already exists before running, so a retry does not
create the Slack channel twice or duplicate the folder.

**Offboarding hands over a checklist of what stays manual.** Not everything can be
automated. There are accesses and contracts a person has to close. Instead of
pretending full coverage, the system ends by stating exactly what is left.

**The old version is documented as deprecated, with its bugs.** The previous
onboarding ran on Zapier and had five identified defects: wrong IDs, a hardcoded
channel and malformed JSON. It is archived with those bugs written down, because
knowing why something was replaced is worth more than deleting it.

---

# ⭐ AI blog generation pipeline

**A multi-stage chain that researches, drafts and delivers SEO articles**, with async
callbacks between Make, Google Apps Script and three different AI providers.

`Make` · `Google Apps Script` · `OpenAI` · `Claude` · `Perplexity` · `Reddit API` · `Airtable`
🏢 Client work · blueprints not published

### What it is

The system behind the 200+ articles. It is not a call to a model: it is a pipeline
with several phases, each in a different system, coordinated by callbacks.

It produces two article types with different structures, *"Brand vs Competitor"* and
*"Alternatives to competitor"*, and each has its own chain.

**How one generation runs:**
1. A checkbox in Airtable triggers the flow, or somebody launches it manually
2. Make calls Google Apps Script and **releases the thread**, because generation takes
   minutes
3. Research phase: Perplexity for the research, and **the Reddit API with OAuth to mine
   real comments** about the brand and the competitor, with retries and error handling
4. Drafting phase: four chained OpenAI prompts, switching models per task
5. The Google Doc gets created in the right sprint folder
6. The script calls back to the Make webhook, which updates Airtable with the URL

### Design decisions

**Async with callback, not blocking wait.** A flow that waits minutes for a model to
finish burns operations and dies on timeout. Generation gets fired, the flow ends, and
the script reports back when it's done. That is the difference between a pipeline that
scales and one that breaks under volume.

**Each provider where it is best.** Perplexity for sourced research, OpenAI for long
drafting, Claude for processing scraped content. Marrying the system to a single
provider would have meant using the worst tool for two of the three stages.

**Reddit as a source, not filler.** The difference between a generic article and a
useful one is whether it contains what people actually say about the product. Mining
real comments was a quality decision, not a volume one.

---

# ⭐ SC Lead Finder

**Finds local businesses with bad or missing websites and scores which product to
approach them with.** Runs on its own every Monday.

`TypeScript` · `Trigger.dev`
🔒 Private repo · available on request

### What it is

A prospecting automation for my agency. Every Monday, untouched, it walks local
businesses in South Carolina, evaluates the state of their web presence, and returns a
list **ordered by opportunity**.

For each business it checks whether there is a site, whether it works, whether it's
current and how bad it is. From that it **scores which product makes sense to
approach with**: a site from scratch for one with none, ad spend for one with a decent
site but no lead capture, automation for the more advanced ones.

The output is what the sales side starts Monday morning with.

### Design decisions

**Genuinely unattended.** It does not notify to ask permission or wait for
confirmation at an intermediate step. If it needs weekly supervision, it did not solve
the problem, it just moved it.

**It scores, it does not just list.** A list of 200 businesses with no priority is as
useless as no list. The value is the ordering.

`[MISSING: sample output, without real business data]`

---

# ⭐ Payment data reconciliation

**Two complementary strategies for the same problem**: matching Stripe customers to
internal records.

`Make` · `Stripe API` · `Airtable`
🏢 Client work · blueprints not published

### What it is

Billing and the internal CRM lived apart, so nobody knew with certainty which Airtable
record matched which Stripe customer. That breaks revenue reporting and renewal
tracking.

I solved it with two automations that complement each other:

**Bulk reconciliation** walks every Stripe customer and looks for a match in Airtable
by email or name, writing the Customer ID where it belongs. It cleans up history.

**Real-time listener** watches Stripe checkout events and, if it is that customer's
first payment, captures the Customer ID right then. It stops the problem from growing
back.

### Design decision

**Clean the past and close the leak, separately.** The listener alone would have left
the entire backlog unresolved. Bulk reconciliation alone would have needed rerunning
forever. Together they turn a recurring problem into a solved one.

---

# ⭐ Structured scraping pipeline

**Extracts the structure of competitor sites and distills a reusable template.**

`Firecrawl` · `Claude Code` · markdown workflows

### What it is

It solves a concrete problem for my agency: **when a new client arrives in a niche,
don't build the page from scratch.**

You point it at 2-3 competitors in the vertical, HVAC technicians for example, and the
pipeline scrapes their sites, analyzes what structure, sections and conversion
elements they have in common, and **produces a generic template** for that niche. Then
with the real client you only change data, colors and copy.

It is the difference between shipping a site in two weeks and shipping it in two days.

### Design decisions

**The output is not raw data, it is a template.** Scraping three competitors and
saving the HTML is worth nothing. The value is in what they share and what of that can
be reused. That analysis is part of the pipeline, otherwise the pipeline only moved
the work instead of removing it.

**The process lives in markdown, execution lives in code.** SOPs describe what to do
and in what order; the tools execute. Changing the analysis criteria is editing a
document.

---

## The rest of the catalog

**40 automations documented**, each with its exportable blueprint and notes on what it
does, what it depends on, and how to migrate it. A sample:

| Automation | What it does |
|---|---|
| **Backlink load balancing** | Assigns each backlink to the sprint slot with the lightest load, balancing by delivery date |
| **Store monitor** | Watches Shopify theme changes on client stores and alerts on modification |
| **Inbox watcher** | Captures Ahrefs and SEMrush reports from Gmail, stores them, waits for domain linking and notifies the client channel |
| **Competitor RSS** | Daily cron reading competitor site RSS and storing new articles in a dedicated base |
| **Sprint folder structure** | On sprint creation, generates the Drive folder hierarchy and writes the IDs back to the record |
| **Per-page documents** | Copies the right template by page type and links the document to the record |
| **Monthly Slack report** | Iterates clients and brands, assembles and sends the performance report |
| **Weekly delivery digest** | Friday cron: summary of backlinks and pages delivered, to each brand channel |
| **Scraper with AI processing** | Scrapes a page's live URL, processes it with Claude and generates the document, skipping if one already exists |
| **Client subscenario** | Reusable component returning all clients with their brands, called by the other automations |

### How I think about this work

**Automate the repeatable, keep judgment human.** Every system removes mechanical work
and leaves the decision with a person.

**Subscenarios exist for a reason.** When ten automations need the client list, you
build it once and the rest call it. Copying the logic ten times guarantees nine of
them go stale.

**Write the SOP or it didn't happen.** A system only one person can operate is a
liability. All 40 were documented with their blueprint and notes, which is why the
team could keep running them after my contract ended.

**Document the bugs, including your own.** Several automations carry written warnings:
a lookup without a filter that can break with multiple clients, an ID used against the
wrong table, a partial blueprint. They are noted for whoever comes next, not hidden.
