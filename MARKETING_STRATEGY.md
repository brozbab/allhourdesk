# Allhourdesk — Marketing & Go-to-Market Strategy

**Version:** 1.0  
**Date:** 21 November 2026  
**Status:** Internal strategy / website content source of truth (subject to product and commercial sign-off)  
**Audience:** Founders, marketing agency, product, engineering, sales and customer success  
**Repository:** `brozbab/allhourdesk`  
**Initial objective:** Acquire and validate the first **5–10 paying hotels**, initially through the Apaleo customer ecosystem, without positioning Allhourdesk as an Apaleo-only product.

> **Important scope rule:** This document uses `product-scope-v1.md` as the most recent explicit product-scope decision. The older `HOTELIER_EXPERIENCE.md` and `website content/WEBSITE_CONTENT.md` contain valuable design and onboarding concepts but also describe broader features that V1 explicitly defers. Any capability statement on the live website must pass an engineering/product verification check.

---

## 1. Executive decision

**Public brand:** Allhourdesk is an **AI-powered hotel reservations and guest-call platform** that answers booking enquiries, uses trusted property information and connected live distribution data, and guides eligible callers towards completed reservations and secure payments. It is designed to fit alongside the hotel's existing phone and reservation stack.

**Initial distribution strategy:** Prioritise direct outreach to hotels currently using **Apaleo**, because Allhourdesk already has an Apaleo integration asset and can learn from a focused first cohort. This is a *customer acquisition wedge*, not the permanent definition of the product or a claim that Apaleo is the mandatory V1 integration architecture.

**Longer-term integration and commercial architecture:** The agreed V1 technical direction centres reservation commerce on **channel-manager / distribution connectivity**, with additional direct PMS operational features deferred. Pursue channel-manager partnerships when commercially justified; use first paying hotel evidence to strengthen those discussions.

**Customer-facing promise (proposed):**
> **Turn more hotel calls into confirmed reservation opportunities.**  
> Allhourdesk answers booking enquiries, checks connected availability and rates, and guides guests through approved booking and payment workflows—while your hotel remains in control.

**What not to say:** “new OTA marketplace,” “we bring guests from a new consumer booking network,” “sell unused hours,” “guaranteed incremental demand,” “instant installation,” “all PMS operations supported,” or “every call converts.” None is established by the current V1 scope.

### What we are selling

1. **Coverage:** answer hotel calls during after-hours, busy periods or no-answer routing.
2. **Conversion:** help guests make *new* reservations using availability, rates and restrictions from an authorised connected system.
3. **Consistent guest information:** respond to approved property FAQs and escalate when information or permissions are unavailable.
4. **Operational fit:** preserve the hotel's existing public phone number, source-of-truth systems and agreed human escalation.
5. **Financial control:** use secure hosted payment workflows, with the hotel's merchant/payment ownership model as specified and validated.
6. **Proof:** show measured answered calls, booking conversations, test reservations, successful bookings and attributable reservation value—not projections dressed as outcomes.

## 2. Product truth and documentation precedence

### 2.1 Documents reviewed (all Markdown files on `main` as of this strategy)

| File | Relevant guidance | Treatment |
| --- | --- | --- |
| [product-scope-v1.md](../product-scope-v1.md) | Latest V1 decision: AI reservation channel; channel-manager/distribution primary abstraction; only Allhourdesk-originated reservations can be serviced where allowed; broad PMS operations excluded. | **Authoritative for V1 product scope** |
| [HOTELIER_EXPERIENCE.md](../HOTELIER_EXPERIENCE.md) | Hotel-owned Stripe Connect, PMS/payment/phone onboarding, call forwarding, test reservation and verification gates, operational dashboard. | Experience blueprint; reconcile with newer distribution-first V1 architecture |
| [website content/WEBSITE_CONTENT.md](../website%20content/WEBSITE_CONTENT.md) | Earlier website sitemap, AI-voice/reservations/trust story, pilot rollout, claims discipline. | Reuse structure, but narrow overbroad operational promises |
| [brand/README.md](../brand/README.md) | Night Log identity, oxblood/bone palette, brand voice, logos. | Retain brand vocabulary and identity, subject to newer design system |
| [website design assets/README.md](../website%20design%20assets/README.md) | Website direction and concept assets. | Design reference |
| [website design assets/DESIGN_SYSTEM.md](../website%20design%20assets/DESIGN_SYSTEM.md) | vNext style: premium hospitality software, Instrument Serif/Archivo, oxblood, product proof, no generic blue. | **Authoritative visual direction** |
| [website design assets/COMPONENTS.md](../website%20design%20assets/COMPONENTS.md) | Hero proof, phone-to-reservation workflow, trust, staged pilots, vendor logo discipline. | Component guidance |
| [website design assets/IMAGE_STYLE_GUIDE.md](../website%20design%20assets/IMAGE_STYLE_GUIDE.md) | Realistic product UI; no invented metrics, claims or certifications. | Art direction |
| [website design assets/VISUAL_ASSET_MAP.md](../website%20design%20assets/VISUAL_ASSET_MAP.md) | Existing reference visuals and production implementation caveats. | Visual reference map |

**Precedence rule:** latest explicit product-scope decision > verified implementation > earlier experience/website aspirations > new marketing proposals. Marketing copy does not grant a product capability.

### 2.2 Material differences discovered

| Earlier assumption or previous marketing idea | Repository truth / risk | Strategy correction |
| --- | --- | --- |
| Allhourdesk is mainly an additional OTA/marketplace that independently creates traveller demand | V1 describes **AI-powered hotel reservation conversations** and booking fulfilment, not a consumer demand marketplace | Lead with **missed calls, direct reservation conversion and guest coverage**, not invented marketplace reach |
| Hourly/day-use stays are the key use case | No basis for an hourly-stay proposition in the reviewed V1 spec | Do not lead with day-use/hourly revenue without an explicit product decision |
| Universal direct-PMS integrations underpin V1 | Latest V1 explicitly moves core reservation commerce toward **channel managers/distribution networks** | Present PMS and channel-manager integrations separately; describe capability per connected system |
| Full AI front-desk automation, including modification of any reservation and early-check-in operations | V1 explicitly excludes arbitrary non-Allhourdesk reservation edits and PMS-native operations | Scope booking changes/cancellations to **Allhourdesk-originated reservations**, only where terms/API allow |
| “Payments collected by Allhourdesk” / universal commission model | Hotelier specification prefers hotel-owned Stripe Connect; fee model unresolved | Explain the hotel-owned merchant intent; verify actual payment flow and do not publish an invented fee |
| “Instant setup” and guaranteed ROI from day one | Activation depends on integration permissions, Stripe verification, telephony and end-to-end tests | Promise a **guided process with early test visibility**; measure real setup times before publishing numbers |
| Apaleo is the sole integration / entire platform identity | Strategic goal is multi-integration; Apaleo is the first outreach cohort | Keep homepage vendor-neutral and build a dedicated Apaleo landing page |
| Mews, Cloudbeds, Oracle and D-EDGE are ready | User explicitly says only Apaleo is ready now; other named systems are not ready | Show explicit status labels and avoid implying current functionality |
| Website concept graphics are actual screenshots | Design docs identify them as concepts | Label demos as illustrations until backed by verified production UI |

### 2.3 Release and readiness gates before external claims

Product/engineering must verify: Apaleo connection path and required scopes; whether the pilot reservation path uses Apaleo directly or distribution connectivity; availability/rate/restriction lookup; reservation create/confirm/cancel permissions; payment account ownership, test/live readiness and refunds; message delivery; call forwarding and failover; supported languages; dashboard metrics; privacy/data residency; activation time; pilot commercial agreement. No unverified statement becomes public copy.

## 3. Audience and positioning

### Ideal first cohort

**Primary:** independent and small-group hotels using Apaleo, initially Ireland/UK and suitable European markets, selected for accessible decision makers, meaningful inbound phone booking enquiries, readiness for a limited forwarding pilot and ability to support the required booking/payment workflow.

**Decision makers:** owner/GM (revenue, staffing and low-risk adoption), revenue/commercial manager (booking conversion and rate integrity), front-office lead (coverage, exceptions and team handover), IT/PMS owner (permissions, security and reversibility).

**Not a fit yet:** hotels seeking extensive PMS-native operations, servicing arbitrary third-party bookings, an immediate large-scale multilingual call centre guarantee, or access to a proven consumer traveller marketplace.

### Differentiation

| Hotelier problem | Allhourdesk message | Required proof |
| --- | --- | --- |
| Missed calls after-hours or during peaks | Keep the hotel reachable for booking enquiries | Call routing demo / answered call counts |
| Reception staff cannot simultaneously answer every question | AI handles appropriate guest questions and booking intent, with escalation | Sample call and exception examples |
| Hotel booking enquiries often stop before payment | Move eligible conversations toward valid availability, secure payment and reservation confirmation | Real end-to-end reservation test |
| Fear of changing PMS, phone number or merchant setup | Connect alongside existing systems; retain approved controls | Onboarding walkthrough and ownership explanation |
| Skepticism about AI improvising bookings | Ground rates/policies in authorised connected systems and enforce capability boundaries | Product safeguards and real transaction states |

**Preferred corporate category:** “AI Voice & Reservations for Hotels” or “AI-powered hotel guest communications and reservations.” Avoid positioning V1 as a general-purpose PMS operations suite.

## 4. Messaging hierarchy and approved draft copy

**Primary headline option:**  
**Every booking enquiry deserves an answer.**

**Primary supporting line:**  
Allhourdesk helps hotels handle guest calls, answer routine questions and turn eligible booking enquiries into reservations using connected availability and secure payment workflows.

**Commercial alternative:**  
**More conversations answered. More booking opportunities captured.**

**Brand-neutral integration line:**  
Designed to work with the hotel systems you already use, with capabilities and availability shown for each integration.

**Recommended CTAs:** “Book a demo” (primary), “See how it works” (secondary), “Explore integrations” (supporting), “Discuss a pilot” (mid-funnel).

**Apaleo landing page headline:**  
**Using Apaleo? See how Allhourdesk can handle booking calls for your hotel.**

**Apaleo landing supporting line:**  
Explore our Apaleo connection, test a real call-to-reservation workflow and see what your hotel needs to activate a controlled pilot. Exact capabilities depend on integration permissions and pilot configuration.

**Trust message:**  
Your hotel retains control over its guest-facing phone identity, connected systems and merchant relationship. We recommend a safe limited pilot before extending coverage.

**Voice:** precise, calm, warm and operationally credible. No hype, unsubstantiated statistics, guaranteed revenue, fake partner endorsements or “replace your receptionist” framing.

## 5. Integration strategy and website status model

The website communicates a **growing multi-platform approach**. Targeted outbound messaging is **Apaleo-first**.

### Integration display — commercial planning snapshot (21 November 2026)

| Platform | Type | Website label | Readiness note |
| --- | --- | --- | --- |
| **Apaleo** | PMS | **Available** | User-confirmed current integration; product team must verify exactly which V1 actions are available |
| **SiteMinder** | Channel manager | **Coming February 2027** | User-stated target, not a guaranteed vendor commitment; show “Target: February 2027” if dependencies or certification remain |
| **Mews** | PMS | **In Progress** | Not available for production hotel activation |
| **Cloudbeds** | PMS | **In Progress** | Not available for production hotel activation |
| **Oracle OPERA Cloud** | PMS | **In Progress** | Not available for production hotel activation |
| **D-EDGE** | Channel manager | **In Progress** | Not available for production hotel activation |

**Status semantics:** “Available” means tested and onboardable for the published use case; “In Progress” means real engineering or formal integration work is underway; otherwise use “Planned” or “Under consideration.” “Coming February 2027” is a *target*, not a service-level commitment. Each tile must have the correct call to action: **Connect / Book demo** for verified available; **Join waitlist / Request update** for others. Avoid a combined row of logos beneath “Works with” unless status is adjacent and obvious. Do not imply formal vendor partnerships/certification unless approved.

**Integration landing architecture:** `/integrations` (all systems, statuses and request flow), `/integrations/apaleo` (active high-intent acquisition), and future provider-specific pages only when there is meaningful technical and commercial content.

**V1 architecture caveat:** An Apaleo direct-PMS path is an existing asset, but `product-scope-v1.md` says channel-manager connectivity is the primary V1 abstraction. Before launch, engineering and founders must explicitly approve the Apaleo pilot transaction path and whether it meets V1's reservations-first scope.

## 6. Site architecture and conversion experience

The website is a commercial software site, **not a guest-facing travel marketplace**.

### Navigation

- **Platform:** AI Voice, Reservations, Guest Enquiries, Payments (capability-qualified).
- **Solutions:** After-hours, Overflow, Booking Enquiries, Independent Hotels.
- **Integrations:** Overview, Apaleo, Request Integration.
- **How It Works:** Call -> approved information -> real availability -> booking/payment -> confirmation/escalation.
- **Trust:** Privacy, Payments, Responsible AI, Operational Controls.
- **Company:** About, Contact.
- **Primary CTA:** Book a demo.

### Homepage information flow

1. **Hero:** missed-call / booking opportunity headline; software-first live-call visual; Book demo.
2. **The problem:** after-hours and busy reception lead to unanswered guest requests.
3. **How it works:** guest calls; AI understands intent and approved property knowledge; checks connected inventory when needed; uses authorised booking/payment path; escalates unsupported cases.
4. **Use cases:** after-hours coverage, front-desk overflow, new reservations, property FAQs.
5. **Integration compatibility:** one Apaleo Available tile; five future/in-progress cards with precise statuses, including SiteMinder target date.
6. **Pilot plan:** discovery; test line; property configuration; end-to-end test; limited forwarding; measured expansion.
7. **Trust:** source-of-truth data, hosted payment link, hotel-owned merchant design, human escalation and clear interaction trail; verify before claiming fully implemented.
8. **Proof:** real demo now; first verified pilot stories later. No fake customer quotes, logos or metrics.
9. **FAQ:** existing number; how bookings enter the hotel system; what happens on error; which reservations can be changed; payments; supported languages; time to launch.
10. **Final CTA:** “See Allhourdesk handle a real hotel booking call.”

### Apaleo landing page

Single job: turn a qualified Apaleo hotel visitor into a **demo or controlled pilot**. Show Apaleo-specific compatibility/permissions, actual product demo, activation steps, hotel control, technical prerequisites, common objections and a compact form. Do not describe the whole company as “for Apaleo hotels.” Personalise campaign links and CRM tags to the Apaleo cohort.

### Conversion form

Capture name, work email, hotel, country, hotel website, current PMS/channel manager, approximate phone enquiry volume (optional), requested use case and permission to contact. Keep the default form short; collect deeper technical prerequisites after qualification.

## 7. Day-one value demonstration and pilot

**Day one means clarity and testability, not guaranteed revenue.**

Recommended activation journey:
1. Qualify hotel / use case.
2. Configure property and approved property knowledge.
3. Connect the supported reservation source and verify actual permissions.
4. Configure the permitted payment workflow; Stripe verification may take additional time.
5. Set up a test phone line or forwarding route.
6. Run a test booking enquiry and, where possible, a sandbox reservation/payment.
7. Show test result, failed gates and next action.
8. Enable limited live forwarding only when all production gates pass.

**First-day proof:** connection status, valid availability query, successful test call, approved FAQ answer, test reservation/payment outcome, readiness checklist and clear exceptions. **After go-live proof:** live calls, answered calls, booking-intent calls, confirmed Allhourdesk-originated reservations, attributable reservation value and payment status.

**Controlled pilot:** begin with no-answer or selected out-of-hours forwarding. Retain the public hotel number and a human fallback. Expand only when real-world outcomes, operational error rates and hotel feedback warrant it.

## 8. First 5–10 paying hotels: acquisition plan

### Initial account-based motion

Start with a curated, permission-respecting list of approximately **150 qualified Apaleo-connected properties**. This is a planning assumption, not a verified market-size or conversion rate.

Prioritise independently managed hotels and small groups with active inbound phone booking demand. Personalise the outreach with a specific hotel problem: uncovered calls, multilingual enquiries or reservation conversion. **Never claim that Allhourdesk will bring a separate traveller audience unless a separate demand channel is actually live.**

### Outreach sequence (illustrative)

- **Day 1:** concise personalised email introducing AI booking-call handling and the limited pilot.
- **Day 4–6:** one concrete workflow example or 60-second demo clip.
- **Day 10–14:** low-pressure follow-up asking whether the hotel wants to test a call using its existing setup.
- Respect local marketing/privacy laws, consent/legitimate-interest rules, unsubscribes and suppression lists.

**Email angle:** “We noticed your property uses Apaleo. We are inviting a small number of hotels to test how AI can handle booking enquiries and support a connected reservation flow, starting with a controlled phone-routing pilot. Would a short product demo be relevant?”

### Supporting channels

- Apaleo ecosystem discovery and relationships, subject to listing and certification requirements.
- Founder-led LinkedIn education (missed calls, safe AI bookings, call forwarding pilots).
- Hotel referrals earned from actual measurable pilot results.
- Small retargeting or paid-search tests only after website demo conversion is proven.
- Parallel channel-manager partnership discovery, with SiteMinder targeted for Feb 2027 subject to readiness.

### Offer: Founding Hotel Partner Programme

Invite up to ten eligible hotels to structured pilots with direct support, transparent fees, documented success criteria and explicit conversion to paid terms. Avoid indefinite free pilots being counted as paying customers.

**Pilot commercial checklist:** duration, eligible calls/booking flow, fees and commission (if any), Stripe/merchant setup and costs, cancellation/refund treatment, who handles guest support, liability, data processing, minimum performance review, exit and phone-routing rollback.

## 9. Commercial performance and measurement

**Primary business outcome:** **5–10 contracted and paying hotel customers**, each with an active and technically valid deployment or agreed activation milestone. Report paid and technically active hotels separately.

**Core funnel:**
Target account -> relevant reply -> discovery/demo -> technical qualification -> pilot agreement -> successful test call -> successful reservation test -> live pilot -> first real reservation -> paid conversion / retention.

### Measurement catalogue

| Metric | Reason / caveat |
| --- | --- |
| Qualified Apaleo accounts researched | Prospect universe quality, not platform TAM |
| Outreach reply and demo rates | Message relevance |
| Demo -> pilot -> paid conversion | Commercial validation |
| Time to first successful test call | Ease-of-adoption proof |
| Time to first test reservation | Reservation system functionality |
| Percentage of pilots requiring manual setup intervention | Genuine self-service maturity |
| Calls answered and booking-intent calls | Measured opportunity capture |
| Confirmed Allhourdesk-originated reservations | Actual V1 transaction value |
| Attributable reservation value and collected payments | Separate booking value from realised cash; do not call all revenue “incremental” without a baseline |
| Transfer/escalation, failures and reconciliation exceptions | Reliability and hotel control |
| Hotel satisfaction and 30/60-day retention | Sustainability |

Avoid a public ROI calculator that assumes incremental guests or every booking is incremental. If using a calculator, model **missed booking-intent calls x eligible conversion x average reservation value** as a scenario only, distinguish gross booking value from revenue/profit, and disclose fees, costs, cancellation risk and uncertainty.

### Initial targets (planning assumptions, not forecasts)

150 researched properties; 20–30 conversations; 12–18 demos/evaluations; 8–12 pilots; **5–10 paying hotels** over an approximately 90-day validation programme. Reforecast weekly using observed numbers.

## 10. 90-day execution plan (proposed)

| Phase | Timing | Work | Proposed owner role | Exit criteria |
| --- | --- | --- | --- | --- |
| **1. Truth and positioning** | Weeks 1–2 | Verify feature matrix and Apaleo path; settle merchant and pricing model; audit existing page claims; approve strategy | Founder + product/engineering + marketing | Approved claim register and pilot scope |
| **2. Conversion foundation** | Weeks 3–4 | Rewrite homepage; ship Apaleo landing and integration statuses; create authentic demo clip; set up forms/CRM/analytics | Marketing/design + engineering | Live conversion pages and tested handoff |
| **3. Pilot sales** | Weeks 5–8 | Account research, outreach, demos, guided tests, signed pilots, workflow and message iteration | Founder/sales + customer success | First active pilots and operational data |
| **4. Evidence and scale test** | Weeks 9–13 | Convert pilot cohort to paid, publish approved case evidence, evaluate funnel, capture channel-manager partnership proof | Founder + customer success + marketing | 5–10 paying hotel goal or honest diagnosis of blockers |

All dates are relative to kickoff; holiday response rates, technical gates and partner certification can shift milestones. Do not invent named role assignments.

### Operating cadence

Weekly founder/product/marketing review of (a) prospect -> demo progression, (b) technical activation blockers, (c) pilot performance, (d) claims changed by new evidence and (e) next week's single highest-leverage action.

## 11. Visual and brand implementation

Follow `website design assets/DESIGN_SYSTEM.md` and `brand/README.md`:
- Colours: **oxblood `#5B1A1E`**, bone `#F7F4EF`, ink `#1A1614`, clay accents; green only for real success states.
- Type: Instrument Serif headlines; Archivo UI/body; JetBrains Mono only for operational metadata. Do not replace with blue/teal generic SaaS branding.
- Product proof first: incoming call -> understood intent -> valid availability -> selected room -> secure payment link -> reservation result (or escalation).
- Use realistic responsive HTML/CSS/SVG interfaces; concept `.webp` visuals are references, **not verified screenshots**.
- Keep visual focus on hotel software rather than hotel-room marketplace browsing, robots, neon AI or generic stock call centres.
- Present legal company details, monitored contact routes and a trust section without invented audits or certifications.
- WCAG AA contrast, semantic states, mobile CTA, reduced-motion support and keyboard focus.

## 12. Claims policy and approval register

All public statements require a status:
- **LIVE / VERIFIED:** demonstrated in current production environment.
- **PILOT:** only available to selected pilot hotels.
- **IN PROGRESS:** work underway; not onboardable.
- **TARGET DATE:** planned availability, subject to dependencies.
- **VISION:** future ambition, not a current capability.

**Explicitly prohibited without evidence:** “fully integrated” for non-ready PMSs; “official Apaleo partner” if not certified; “available February 2027” as a guarantee for SiteMinder; untested language coverage; “PCI certified”; blanket GDPR or AI Act certification; guaranteed booking lifts; zero-touch onboarding; fabricated ROI, testimonials or case studies; management of all existing OTA reservations; 24/7 human support if not staffed.

### Claims requiring product approval before publishing

| Claim / asset | Approval needed |
| --- | --- |
| “Apaleo — Available” | Which property, availability, rate, reservation and cancellation actions pass production tests |
| “SiteMinder — Target: Feb 2027” | Engineering/commercial feasibility and owner-approved date |
| “Mews / Cloudbeds / OPERA / D-EDGE — In Progress” | Confirm actual integration work underway; otherwise change to Planned |
| “Phone calls can be forwarded without changing the published number” | Supported provider/market and test procedure |
| “Hotel receives payments directly” | Confirm hotel-owned Stripe Connect implementation and contracts |
| “Send secure payment links” | Supported channels, account readiness and webhook reconciliation |
| “Complete bookings on call” | Exact flow, timing, confirmation/payment sequence and reliability |
| “Multi-language” | Specific tested languages and fallback quality |
| “See impact on day one” | Define actual tested dashboard events, no implied guaranteed bookings |
| “Go live in X minutes” | Empirical onboarding-time evidence |
| “X% incremental revenue” | Auditable baseline and statistically defensible attribution |

## 13. Conflicts to resolve before building the new website

1. **Pilot architecture:** Is the initial Apaleo hotel flow direct PMS booking, an authorised distribution/channel connection, or a hybrid? The latest product scope identifies distribution as the V1 abstraction, while Apaleo is an existing direct-PMS asset.
2. **Product packaging:** Is V1 called “Allhourdesk Reservations,” with broader “PMS Operations” explicitly future, as `product-scope-v1.md` suggests?
3. **Payments:** Confirm whether the preferred hotel-owned Stripe Connect model from `HOTELIER_EXPERIENCE.md` is implemented and if fees are charged per reservation, per month or otherwise.
4. **Available versus planned features:** Which of call forwarding, multilingual voice, messaging, reservation creation/amendment and dashboard views are live, pilot-only or conceptual?
5. **Integration progress:** Confirm the five non-Apaleo labels and whether the February 2027 SiteMinder target is sufficiently supported for a public date.
6. **Commercial definition:** What constitutes a “paying hotel” and what fees apply during a pilot?
7. **Website legacy claims:** The older website content includes broad existing-reservation management and general PMS operations; these must be revised before publication.

These are **explicit approval gates**, not invitations for marketing to invent answers.

## 14. Next website-content sprint

After this strategy is accepted, prepare in order:
1. Homepage copy and SEO metadata centred on call coverage and reservation conversion.
2. Integration section and `/integrations` page with six clearly differentiated statuses.
3. `/integrations/apaleo` targeted campaign/activation page.
4. `/how-it-works` and an honest end-to-end demo storyboard.
5. Pilot page, onboarding FAQs, trust/payment explanation and case-study template.
6. CRM/source tracking and copy-to-product claim audit checklist.

**Acceptance criteria:** a non-Apaleo hotel immediately understands the platform; an Apaleo hotel has a direct path to an appropriate pilot; no visitor is misled into believing a future integration is ready; no copy promises capabilities outside approved V1; agency visual work respects the existing design system.

---

## Appendix: Source-of-truth principle

This strategy is an **overlay on the current repository documentation**, not a rewrite of the product. Where previous strategy conversations conflicted with `product-scope-v1.md`, the latest explicit V1 scope wins. Marketing must update alongside product decisions, and new public claims require evidence and an accountable reviewer.
