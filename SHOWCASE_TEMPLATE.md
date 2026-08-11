# Public Showcase Template

Use this template when turning a private production project into a public repository
that can be evaluated safely.

The goal is not to publish the real system. The goal is to show enough architecture,
code quality and decision-making for a reviewer to understand the work without
exposing clients, credentials, business logic or private context.

---

## Recommended Repository Structure

```text
README.md
architecture.md
privacy.md
.env.example
sample-data/
demo/
screenshots/
```

## README.md

The README should answer:

- What problem did this solve?
- Who used it?
- What did I build?
- What changed after it shipped?
- What can a reviewer run or inspect?
- What was removed from the public version?

Recommended sections:

```text
# Project Name

## What It Is
## Problem
## What I Built
## Architecture
## Design Decisions
## Demo / How to Run
## What Was Sanitized
## Results
```

## architecture.md

Include the system shape without exposing private implementation details.

Safe to include:

- component diagrams
- data flow diagrams
- fake schema examples
- queue/job structure
- integration boundaries
- tradeoffs and why they were chosen

Avoid:

- internal URLs
- client names
- account IDs
- private table/base IDs
- exact proprietary workflows that create competitive risk

## privacy.md

Document what was removed and why. This makes the repo look intentional, not empty.

Example:

```text
This is a sanitized showcase of a private production system.

Removed:
- real client names and records
- API keys and credentials
- production database IDs
- private prompts tied to client strategy
- screenshots with identifying information
- historical commits from the production repository

Replaced with:
- mock data
- .env.example
- simplified adapters
- sample outputs
```

## .env.example

Include variable names, never values.

```text
OPENAI_API_KEY=
SUPABASE_URL=
SUPABASE_ANON_KEY=
STRIPE_SECRET_KEY=
```

If a variable name itself exposes private context, rename it generically.

## sample-data/

Use fake data that demonstrates the shape of the system.

Good examples:

- `sample-clients.json`
- `sample-report-input.csv`
- `sample-businesses.json`
- `sample-brand-config.yaml`

Do not use copied production exports, even if they look harmless.

## demo/

The demo can be reduced. It should prove the pattern, not replicate the whole
business.

Good demo patterns:

- mock adapters instead of live APIs
- local JSON or CSV instead of production databases
- fake brands, fake clients, fake users
- one representative workflow instead of all workflows

## Screenshots

Only include screenshots if every visible field has been checked.

Redact:

- names
- emails
- phone numbers
- addresses
- order/customer IDs
- financials
- private URLs
- Slack/channel names
- Airtable base/table IDs

When in doubt, use a recreated screenshot with mock data.

## Security Checklist Before Publishing

- No `.env` files
- No service account JSON files
- No API keys, tokens, passwords or webhooks
- No real customer, student, lead or client data
- No production database exports
- No private prompts tied to client or business strategy
- No internal URLs, account IDs or base IDs
- No screenshots with identifying data
- No production git history
- No files ignored locally but accidentally included in the new repo

## Recommended Commit History

Start the public showcase as a fresh repository with clean history.

Use professional commit messages such as:

```text
Create sanitized CRM case study
Add mock schema and migration notes
Add reporting demo with sample data
```

Do not clone and publish the private repository history.
