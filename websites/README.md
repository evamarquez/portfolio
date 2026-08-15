# Websites & Delivery Systems

Sites I designed and built from code, plus the delivery systems behind them. This
section matters because the web work is not separate from the automation work: the
same pattern appears again and again, turning repeated service delivery into reusable
systems.

---

# Eras Conversion

**Agency website plus a repeatable delivery system for local-service businesses.**

`Next.js` · `TypeScript` · `Tailwind` · `next-intl` · `OpenNext` · `Cloudflare`
🟢 [eraconversions.com](https://eraconversions.com) · private production repo

Eras Conversion is an agency I run with two partners. We serve local service
businesses such as HVAC, landscaping and cleaning companies: businesses where the
website exists to make the phone ring. I lead the web service and the automation layer.

### The problem

The partnership began with Meta advertising, but clients also needed websites. The
delivery process had to become faster and more affordable without making every client
site look generic or forcing different niches into the same structure.

### The plan

Use the agency website as the first version of a reusable production system: study two
or three competitors in each niche, identify the conversion structure that actually
fits that market, and turn it into a coded starting point. The template changes by
niche; the delivery method stays repeatable.

### Creation: errors and learnings

The first instinct was to treat the site as a polished agency brochure. That was too
far from the business problem. The stronger direction was to organize the offer around
the decisions a local business owner needs to make: what service is offered, whether it
fits their niche, what it costs and how to start a conversation.

The main learning was that reusable does not mean identical. A good system standardizes
the research, content structure and implementation patterns while leaving room for the
real differences between an HVAC company, a cleaning company and a landscaper.

### Production

- Built a bilingual Spanish/English marketing site with localized content and routing.
- Created pages for the offer, services, cases, company information and contact.
- Added niche-specific service language instead of one generic agency message.
- Routed advertising and web inquiries to the appropriate WhatsApp conversation.
- Connected the contact form to Google Forms/Sheets for lead capture.
- Added Metricool tracking and responsive interaction patterns.
- Deployed the current version through OpenNext and Cloudflare.

### Security boundary

The production repository remains private. The public site exposes the agency offer and
brand, not client data, credentials, internal lead records or the private delivery
system. Any public portfolio version can describe the method and use representative
examples without copying private client work.

### Post-production

The result is more than one agency site: it is the foundation for a niche-based web
delivery service. Future client sites can reuse the coded design system and the
research-to-template workflow while adapting the message, proof and conversion path to
each vertical.

---

# by-evamarquez.com

**Bilingual personal website and publishing hub for my work in AI, project delivery,
automation and digital products.**

`Next.js 15` · `Supabase` · `Tailwind` · `TypeScript` · `Vercel`
🟢 [Live](https://www.by-evamarquez.com/) · private production repo

This is the front door to my professional ecosystem: who I am, what I build, what I
teach and where to find the deeper work. It connects the personal brand to De 0 a
Remoto, the portfolio, educational content and direct contact.

### The problem

My work spans AI, project management, automation, marketing and remote-work education.
A single site had to hold that range without making every visitor understand the whole
history before finding the relevant next step.

### The plan

Create a bilingual, lightweight hub that answers four questions quickly: who I am, what
I can build, which product or project is relevant, and how to continue. The site routes
people to the right destination instead of trying to contain every detail on the home
page.

### Creation: errors and learnings

The main communication risk is breadth. Listing every role equally can make the site
feel like “a little bit of everything” instead of a clear professional profile. The
stronger direction is to keep one primary positioning—AI solutions and technical
project delivery—and use the other areas as supporting proof.

The site also separates the personal story, the De 0 a Remoto product and the future
blog. That keeps product navigation distinct from professional positioning.

### Production

- Built Spanish and English versions with a language switcher.
- Added a home page, About page, De 0 a Remoto route, blog route and contact path.
- Linked the personal site to the product, social channels and professional profiles.
- Added light/dark theme switching and responsive presentation.
- Used direct WhatsApp contact for the primary conversion path.
- Kept the production source private while making the public result easy to inspect.

### Security boundary

The production repository remains private. The public site does not expose private
operating-system files, credentials, personal databases, client work or live
integration configuration. Public content should describe the work without becoming a
dump of the private assistant or business context.

### Post-production

The next improvement is to make the site portfolio-first: lead with the AI solutions
and technical project-management positioning, give the strongest projects a clear path
from the homepage, and turn the blog placeholder into a useful index for case studies,
frameworks and lessons learned.

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

**Related community resource:** [Website Builder SOP](https://github.com/evamarquez/community-resources/tree/main/website-builder)

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
