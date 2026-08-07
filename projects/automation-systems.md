# Automation systems at scale

**Context:** SEO agency running 17+ e-commerce brands across the United States,
Australia and the United Kingdom. 12-person team. My scope was the automation and
internal tooling layer — the systems the team runs on, not the client work itself.

**Outcome:** 80+ automations shipped into production over seven months, with the
core set still running after my contract ended.

> Client names and internal code are not published here. What follows is the
> architecture and the reasoning, which is mine to describe.

---

## Article generation system

**The problem.** Producing one SEO article took roughly two days: research, outline,
draft, internal review, formatting. With 17 brands to serve, throughput was the
bottleneck and it did not scale by hiring.

**What I built.** A generation system that takes a topic and brand and produces a
draft ready for editorial review. Research, structure, drafting and formatting are
handled by the system; judgment stays with the editor.

**Result.** 200+ articles produced. Production time went from ~2 days per article to
minutes plus editor review.

**The design decision that mattered.** The editor stays in the loop. The system does
not publish — it produces a draft. Removing the human from a content pipeline is how
you ship something embarrassing at volume. The gain was never in removing review; it
was in removing everything before it.

---

## Multi-platform publishing scheduler

**The problem.** Publishing across nine platforms, three posts each, every day.
Entirely manual, entirely repetitive, and the kind of task where a missed day is
invisible until it compounds.

**What I built.** A scheduler that programs and publishes across the platform set,
automating five of the nine end to end. The remaining four stayed manual because
their APIs did not support what was needed — a limit worth stating rather than
hiding.

**Result.** Daily publishing at 9+ platforms × 3 posts, with the automated set
running unattended.

---

## Internal CRM migration

**The problem.** The team ran on Airtable. It worked until it did not: the schema
had grown past what a spreadsheet-shaped tool handles well, and the workflows the
team actually needed were being simulated instead of supported.

**What I built.** Led the migration into a custom internal CRM and dashboard, built
to the team's real workflow rather than to a template.

**Result.** In daily use across the full 12-person team, still running today.

**What I would tell someone doing this.** The hard part of a migration is never the
data. It is that the old tool encodes assumptions nobody wrote down, and you only
find them when something breaks for the person who depended on it.

---

## Reporting agent

**The problem.** A recurring manual reporting process — the kind of task that eats a
predictable slice of every week and produces nothing anyone remembers doing.

**What I built.** An agent that pulls the data, assembles the report and delivers it.

**Result.** The manual process was removed end to end.

---

## Page and collection optimization

~200 collection and category pages optimized across client brands, with the
repetitive portion of the work systematized rather than done by hand each time.

---

## How I think about this work

**Automate the repeatable, keep judgment human.** Every system above removes
mechanical work and leaves the decision with a person. That is not caution, it is
where the actual leverage is — the two days spent researching and formatting were
never the valuable part.

**Deterministic where it can be, probabilistic where it must be.** Language models
are good at reasoning over messy input and bad at doing the same thing identically
forty times. Anything repeatable should be code. This is the same principle behind
[Newsletter Kit](https://github.com/evamarquez/newsletter-kit).

**Write the SOP or it did not happen.** I authored the operating procedures for these
systems. A system only one person can run is a liability, not an asset — and the
proof is that these kept running after I left.

**State the limits.** Four of nine platforms stayed manual. Saying which parts did
not work is what makes the rest credible.
