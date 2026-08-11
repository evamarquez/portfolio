# Internal Software & Apps

Full systems with users, workflows, data models and operational consequences. Some
production repositories stay private because they contain business logic, client data
or live integration context. Where useful, I publish sanitized showcases instead.

---

# Internal CRM Migration

**Replaced the Airtable a 12-person team was running on with a custom CRM and
dashboard.**

`TypeScript` · `Lovable` · custom database · migration planning
🏢 Client work · [public case study](https://github.com/evamarquez/internal-crm-case-study) · production system private · in daily use

### What it is

The CRM became the operating system for a boutique Shopify SEO agency: clients,
brands, projects, deliverables, ownership and status. It replaced the Airtable base
the team had been using to coordinate daily work.

I led the full migration: mapping the real process, redefining the schema, building
the dashboard, moving the data, and running a coexistence period so the team could
adopt the new system without losing operational continuity.

### Why it mattered

The old Airtable had stopped being a database and had become a collection of process
workarounds: status fields acting as workflow stages, filtered views acting as role
screens, and implicit rules that lived in people's heads.

A migration like this is not just a data move. The hard part is discovering the rules
that were never written down and designing the new system around how the team actually
works.

### What I built and managed

- Data model and workflow states for clients, brands, projects and deliverables
- Role-specific dashboard views for the team
- Migration plan, coexistence period and adoption support
- Decision log, known-issues register and operating documentation
- Handoff materials so the system could keep running after my contract ended

### Result

The CRM is still used daily by the full 12-person team. That is the real test: not
whether a tool can be built, but whether the team keeps using it when the builder is
no longer in the room.

### Public case study

The public case study shows the migration thinking, representative architecture,
mock data model, privacy boundary and rollout approach without exposing client data or
production code.

→ [See the CRM case study](https://github.com/evamarquez/internal-crm-case-study)

---

# De 0 a Remoto

**A learning platform for people moving into remote work**, with student accounts,
purchase-gated access, course content and admin workflows.

`Next.js 15` · `Supabase` · `Stripe` · `Tailwind` · `TypeScript`
🟢 Live product · production repo private · demo/showcase planned

### What it is

De 0 a Remoto is a business I own. It teaches people with no prior remote-work
experience how to move into virtual assistance, digital marketing, project management
and AI-adjacent roles.

The platform handles the product side: a student buys access, creates an account,
lands in a dashboard, works through modules and downloads material. On the admin side,
I manage content, students and access.

### What I built

- Authentication, sessions and password recovery through Supabase
- Purchase-gated access connected to Stripe
- Course content structured by track and rendered by the app
- Admin workflows for content, students and access
- Database migrations instead of manual schema edits

### Design decisions

**Content lives in the repository, not in the database.** Course material changes like
product code: reviewable, revertible and versioned. The database stores user-specific
state, not the whole course.

**Marketing site and platform are separate.** The acquisition site changes often. The
student platform changes carefully. Keeping them separate protects paying users from
copy tests and landing-page experiments.

### Public version plan

The public version should be a reduced demo with sample content, fake users, no real
course material, no live Stripe keys and no student data.

---

# AI Article Generation System

**A content production pipeline for an agency serving 17+ e-commerce brands.**

`Python` · `OpenAI` · `Perplexity` · `Google Workspace APIs` · brand config files
🏢 Client work · public showcase planned · production code private

### What it is

An internal pipeline used by a content team. Given a topic and a brand, it produced a
draft article with research, structure, brand-specific tone and formatting inside the
workflow the editors already used.

Every brand had its own configuration for voice, vocabulary, constraints and topics.
The system used that configuration before drafting, so onboarding a new brand meant
adding a file, not rewriting the system.

### Result

- 200+ articles produced
- Production reduced from about two days per article to minutes plus editor review
- Editorial judgment stayed with the human team

### Design decisions

**The editor never leaves the loop.** The system drafts; it does not publish. The gain
was in removing the repetitive work before review, not removing review itself.

**One brand, one config file.** The prompt stayed general. Brand context lived in data,
which made the system easier to extend and safer to maintain.

### Public version plan

The showcase version can demonstrate the pipeline with fake brands, sample research,
mock content constraints and a simplified draft flow. It should not include client
brands, real prompts tied to client strategy, source documents or production outputs.

---

# Multi-platform Scheduler

**Programs and publishes content across 9+ platforms, every day.**

`TypeScript` · workflow orchestration
🏢 Client work · case study only · production code private

### What it is

An internal tool where the team loads weekly content and the system handles the
publishing queue, calendar and execution log across 9+ platforms, with 3 posts per
platform daily.

For five platforms, publishing was fully automated. For the remaining platforms, API
limits made full automation impossible, so the system prepared the content and flagged
what needed a person.

### Design decision

**A system that declares where it stops is more trustworthy than one that promises full
coverage and fails silently.** The manual boundary was documented instead of hidden.

---

## Other Product Work

| Project | What it is | Public status |
|---|---|---|
| **CRM prototype** | First CRM version before the full migration | Private |
| **SEO web app** | Internal analysis and rank-tracking tool | Private |
| **Role fit test** | Browser-based assessment that routes people to the right remote career path | Private · demo possible |
