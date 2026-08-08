# Websites

Sites I designed and built, from the code. I don't use Figma. I design in the
browser.

---

# ⭐ Eras Conversion

**Agency site for a Meta advertising partnership serving local service businesses.**

`Next.js` · `TypeScript` · `Tailwind` · `Netlify` · multi-language
🟢 [eraconversions.com](https://eraconversions.com) · 🔒 Private repo

### What it is

Eras Conversion is an agency I run with two partners. We specialize in **Meta
advertising for local service businesses**: HVAC technicians, landscaping companies
and cleaning services. The kind of business that lives or dies by the phone ringing.

Inside the partnership **I lead the web service and the automations**. This site is
the agency's public face: who we serve, how we work, and how to start.

The typical visitor is not a startup. It is the owner of an HVAC business who wants
more calls and has no time or interest in learning marketing. The site is written for
that person, not for another agency.

### The business problem behind the site

Our clients started asking for **websites**, not just ad spend. The goal was to offer
the most affordable sites in the niche, and to charge less you have to **take less
time**.

That is the problem I'm solving with systems: an HVAC client and a landscaping client
need the same page structure, the same conversion sections and the same trust
elements. What changes is the copy, the colors and the data. Not the architecture.

### What I built

- The agency site, from scratch, in code
- A **niche template system**: scrape 2-3 competitors in the vertical, analyze what
  structure and conversion elements they share, and distill a reusable template
- Automations for the more advanced clients

### Design decisions

**Templates per niche, not one generic template.** A template that fits everything
fits nothing: an HVAC business needs a 24/7 emergency block that a cleaning company
has no use for. Templates get distilled from the actual niche, not from what a
service site is supposed to have.

**The design system lives in code.** I don't use design tools. The type scale, the
spacing and the palette are tokens in the code, not decisions revisited on every
project. That is what makes the tenth site faster than the first without making it
look identical.

`[MISSING: screenshot]`

---

# ⭐ by-evamarquez.com

**My personal site**, bilingual, on the same stack I use for product.

`Next.js 15` · `Supabase` · `Tailwind` · `TypeScript` · `Vercel`
🟢 [Live](https://www.by-evamarquez.com/) · 🔒 Private repo

### What it is

Where my public work lives: who I am, what I build, and what I write about
automation and AI. It runs in English and Spanish because my audience is split
between Latin America and the US.

It is not a one-page landing. It has content sections, real navigation, and runs on
Next.js with Supabase behind it. The same stack I build product on, which means it
can grow into something with accounts and payments without being rebuilt.

### Design decisions

**Content lives in files, not a CMS.** Writing a post means writing a file and
committing it. No panel to maintain, no database to back up, and a full history of
every change. A CMS for a one-person site is infrastructure you maintain in exchange
for nothing.

**Server-side rendering.** A personal site that doesn't show up in search isn't doing
its job.

**The same stack I use for product.** I could have built it in a visual builder in an
afternoon. I built it in Next.js because the site is also evidence: anyone who opens
it and looks at the code sees how I work.

`[MISSING: screenshot]`

---

# ⭐ De 0 a Remoto, product site

**The public face of my remote-work training platform.**

🟢 [Live](https://de-0-a-remoto.vercel.app) · 🔒 Private repo

### What it is

De 0 a Remoto is a business I own: I teach people how to land remote work in three
areas. This site is the acquisition side, kept separate from the platform where
students live.

It explains the three tracks, the method, and moves a visitor toward the right one.
People arrive not knowing which of the three fits them, so the site's job is to
orient them before selling to them.

### Design decision

**Marketing site and platform, separated.** The site changes often, based on what
converts. The platform changes rarely and cannot break. Coupling them would have made
every copy test a risky deploy on top of accounts that already paid.

`[MISSING: screenshot]`

---

# ⭐ Remote role fit test

**An assessment tool that tells you which remote career track fits you.**

`HTML` · `JavaScript` · serverless functions
🔒 Private repo

### What it is

A test that asks about background, prior experience and work preferences, and returns
**a recommended track**: virtual assistant, digital marketing, project management or
AI. Along with the guide to get started in it.

It works as the front door to De 0 a Remoto: a person arrives wondering whether any
of this is for them, and leaves with a concrete answer and a first step.

### The problem

The question that came up most from people who wanted to work remotely was never
"how do I start". It was **"which one of these am I good for"**. Answering it one at a
time does not scale, and without an answer people don't move at all.

### Design decisions

**No backend, on purpose.** All the assessment logic runs in the browser. Nobody has
to register to get value, there is no personal data to safeguard, and the operating
cost is zero.

**Contact capture comes after the result.** The person gets something useful first,
then gets asked for an email. The other way around, most people abandon before
finishing and you end up with neither the contact nor a person you helped.

`[MISSING: screenshot of the test and the result]`

---

## Everything else

| Project | What it is | Stack | Status |
|---|---|---|---|
| **Bienestar Natural** | Product landing page for a wellness business | HTML | 🔒 Private repo |
| **Client sites** | Websites for agency clients in the local services niche | HTML · TypeScript | 🏢 Not publishable |
