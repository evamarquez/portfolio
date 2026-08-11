# Websites & Delivery Systems

Sites I designed and built from code, plus the delivery systems behind them. This
section matters because the web work is not separate from the automation work: the
same pattern appears again and again, turning repeated service delivery into reusable
systems.

---

# Eras Conversion

**Agency site for a Meta advertising partnership serving local service businesses.**

`Next.js` · `TypeScript` · `Tailwind` · `Netlify` · multilingual site
🟢 [eraconversions.com](https://eraconversions.com) · private repo

### What it is

Eras Conversion is an agency I run with two partners. We serve local service
businesses such as HVAC, landscaping and cleaning companies: businesses where the
website exists to make the phone ring.

Inside the partnership, I lead the web service and the automation layer. The site is
the public face of that offer.

### The system behind the site

Clients started asking for websites, not only ads. To make those sites affordable, the
process had to become faster without becoming generic.

The delivery system is built around niche templates: analyze 2-3 competitors in a
vertical, identify the shared conversion structure, and turn that into a reusable
starting point. A cleaning company and an HVAC company should not get the same page,
but the process for building each niche site can be systematized.

### Design decisions

**Templates per niche, not one generic template.** A template that fits everything fits
nothing. The structure comes from the real vertical.

**The design system lives in code.** Type scale, spacing and palette decisions are
codified so the tenth site is faster than the first without looking cloned.

---

# by-evamarquez.com

**My personal site, bilingual, built on the same stack I use for product work.**

`Next.js 15` · `Supabase` · `Tailwind` · `TypeScript` · `Vercel`
🟢 [Live](https://www.by-evamarquez.com/) · private repo

### What it is

My public site: who I am, what I build and what I write about automation, AI and
operations. It runs in English and Spanish because my audience is split between Latin
America and the US.

### Design decisions

**Content lives in files, not a CMS.** Writing and updating content is versioned like
code. No extra admin panel, no database to maintain for a one-person publishing flow.

**The stack can grow with the site.** Next.js and Supabase make it possible to add
accounts, gated content or product features later without rebuilding from scratch.

---

# De 0 a Remoto Product Site

**The acquisition side of my remote-work training platform.**

🟢 [Live](https://de-0-a-remoto.vercel.app) · private repo

### What it is

The public-facing site for De 0 a Remoto. It explains the tracks, the method and the
path into the product. The student platform is separate because paid-user workflows
should not be coupled to landing-page experiments.

### Design decision

**Marketing and product are separated.** The site can change quickly; the platform has
to remain stable.

---

# Remote Role Fit Test

**A browser-based assessment that routes people to the right remote career track.**

`HTML` · `JavaScript` · serverless functions
Private repo · demo possible

### What it is

The test asks about background, experience and work preferences, then returns a
recommended track: virtual assistant, digital marketing, project management or AI.

It works as the front door to De 0 a Remoto. A person arrives unsure which path fits
and leaves with a concrete recommendation.

### Design decisions

**No account required to get value.** The result comes before contact capture, which
reduces friction and makes the tool useful before it asks for anything.

**Simple architecture for a simple job.** The assessment logic can run without a full
backend, which keeps cost and maintenance low.

---

## Other Website Work

| Project | What it is | Public status |
|---|---|---|
| **Bienestar Natural** | Product landing page for a wellness business | Private |
| **Client service sites** | Websites for local-service agency clients | Not publishable without client approval |
| **Niche template workflow** | System for turning competitor structure into reusable page templates | Case study possible |
