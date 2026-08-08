# Apps

Full products: frontend, backend, database, and real people using them on the other
side.

---

# ⭐ De 0 a Remoto

**A learning platform for people moving into remote work**, with three tracks:
virtual assistant, digital marketing and project management.

`Next.js 15` · `Supabase` · `Stripe` · `Tailwind` · `TypeScript`
🟢 Live · 🔒 Private repo

### What it is

De 0 a Remoto is a business I own. I teach people with no prior experience how to
land their first remote job in three areas. Each area is a track with its own
content, exercises and path into the market.

The platform is where all of that lives. Someone buys access, creates an account,
and lands in a dashboard where they see their track, work through the modules and
download the material. On the other side there is an admin panel where I manage
content, students and access.

It is not a course dropped in a folder. It is an application with authentication,
a database, purchase-gated access and server-rendered content.

### The problem

Teaching people to find remote work does not scale if every student needs
individual attention. And existing course platforms take a cut of every sale,
impose their design, and don't let you build the experience the product needs.

Content, access and payments had to run on their own, under my control.

### What I built

- **Student accounts** with authentication, persistent sessions and password
  recovery, on Supabase
- **Content structured by track**, versioned in the repository and server-rendered
- **Stripe payments** wired into the access lifecycle: paying unlocks the track
- **Admin panel** to manage content, students and access
- **Versioned database migrations**, not manual schema edits

### Design decisions

**Content lives in the repository, not in the database.** Courses are versioned
files. A content change is a commit: it has history, it can be reviewed, it can be
reverted. The database only holds what changes per user, which is accounts, access
and progress. Putting content in the database would have meant building an editor,
maintaining it, and losing the record of what changed and when.

**Server-side rendering from day one.** This is a platform that needs to be found by
people searching for how to work remotely. Rendering on the server was not a later
optimization, it was the reason for picking the framework.

**Supabase instead of rolling my own auth.** Auth is the kind of thing where
building from scratch only adds surface area for mistakes. Row Level Security
handles isolation between users **at the database level**, not in application code
you can forget to write on one endpoint.

`[MISSING: screenshots of the student dashboard and admin panel]`

---

# ⭐ AI article generation system

**A content production system** for an agency serving 17+ e-commerce brands.

`Python` · `Generative AI` · `Google Workspace APIs`
🏢 Client work · code not published

### What it is

An internal tool used by the agency's content team. You give it a **topic and a
brand**, and it returns a draft article with its structure, its research folded in
and the formatting done, inside the workflow the team already worked in.

Every client brand has its own profile: tone, vocabulary, topics that are in and
topics that are out. The system reads that profile before writing, so an article
for a mattress brand does not come out sounding like a supplements brand.

The content lead and the editorial team used it. I built and maintained the system;
editorial judgment always stayed with them.

### The problem

Producing one article took **about two days**: research, outline, draft, internal
review, formatting. With 17 brands to serve, throughput was the bottleneck, and it
was not going to be solved by hiring. It had to be solved by changing the process.

### Result

- **200+ articles** produced
- From **~2 days per article** to **minutes plus editor review**

### Design decisions

**The editor never leaves the loop.** The system does not publish, it produces a
draft. Taking the human out of a content pipeline is how you end up shipping
something embarrassing at scale, and a 7-9 figure e-commerce brand cannot afford
that. The gain was never in removing review. It was in removing everything that
came before it.

**One brand, one config file.** Each client's tone and constraints live in
configuration, not inside the prompt. Adding a new brand means adding a file. If the
tone lived in the prompt, every new client would be a rewrite of the system.

### Architecture

```
topic + brand
     ↓
[brand profile]  →  research  →  outline
                                    ↓
                                  drafting
                                    ↓
                            formatting + delivery
                                    ↓
                        draft → human editor → publication
```

---

# ⭐ Internal CRM

**Replaced the Airtable a 12-person team was running on.**

`TypeScript` · `Lovable` · custom database
🏢 Client work · code not published · 🟢 in daily use today

### What it is

The system where the agency runs its operation: clients, projects, the state of every
deliverable and who owns what. An internal dashboard built around the team's real
workflow, with the views each role needs.

All 12 people on the team use it every day. It fully replaced the Airtable base they
had been working in.

### The problem

The team ran on Airtable. It worked until it didn't: the schema had grown past what a
spreadsheet-shaped tool handles well, and the workflows the team actually needed were
being **simulated** rather than supported. Status fields that were really process
steps. Filtered views that were really separate screens.

Once you are using a tool against its design, every improvement costs more than the
last one.

### What I built

I led the full migration: defining the real schema, building the CRM and dashboard,
moving the data, and walking the team through the change.

### Result

In daily use by all 12 people. **Still running after my contract ended**, which is
the only real proof that an internal tool was built right.

### What I learned

**The hard part of a migration is never the data.** It is the assumptions the old
tool had encoded that nobody ever wrote down. You find them when something breaks for
the person who depended on it.

That is why the migration was not a single event. It ran as a period where both
systems coexisted, with the team using the new one and reporting what was missing.

---

# ⭐ Multi-platform scheduler

**Programs and publishes content across 9+ platforms, every day.**

`TypeScript`
🏢 Client work · code not published

### What it is

An internal tool where the team loads the week's content and the system handles
publishing: **9+ platforms, 3 posts each, daily**.

It holds the publishing queue, the calendar of what is going out and the log of what
already went. For five of the nine platforms publishing is fully automated. For the
other four, the system prepares the content and flags it, and a person posts it.

### The problem

Publishing across nine platforms, three posts each, every day, by hand. Repetitive,
and the kind of task where a skipped day is invisible until it compounds and someone
notices a channel has been dead for two weeks.

### Result

**9+ platforms × 3 posts daily**, with the automated set running unattended.

### The limit, stated out loud

**Four of the nine stayed manual** because their APIs did not support third-party
scheduled publishing. That is not a backlog item, it is the boundary of the system,
and it is documented as such along with what it would take to lift it.

A system that declares where it stops is more trustworthy than one that promises full
coverage and fails silently.

---

## Everything else

| Project | What it is | Stack | Code |
|---|---|---|---|
| **CRM prototype** | First version of the internal CRM, before the full migration | TypeScript | 🏢 Client |
| **SEO web app** | Internal tool for analysis and rank tracking | TypeScript | 🏢 Client |
