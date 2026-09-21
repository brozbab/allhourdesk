# AllHourDesk Website Components

## 1. Global navigation

Desktop:
**AllHourDesk | Platform ▾ | Solutions ▾ | Integrations | Trust | Company ▾ | Resources ▾ | Book a demo**

Behaviour:
- starts on bone background
- sticky after the initial scroll
- subtle bottom rule
- Archivo, sentence case
- primary CTA always visible

Mobile:
- logo + menu button
- full-height or sheet-style menu
- Book a demo remains prominent
- no horizontal-scrolling navigation

## 2. Hero — Product Proof

### Layout
Two-column desktop:
- left 42–46%: eyebrow, headline, subhead, CTAs
- right 54–58%: live-call/product visual

### Copy hierarchy
Eyebrow: **AI GUEST COMMUNICATIONS FOR HOTELS**

H1:
**Every guest call answered. Every opportunity handled.**

Body:
Explain answering, reservations, guest requests and PMS connection in one concise paragraph.

Actions:
- Book a demo →
- See how it works

### Product visual
Show a believable state sequence:
Incoming call → language detected → PMS availability → room selected → payment link → payment received → reservation confirmed.

## 3. Trust strip

A compact row beneath the hero:
- Live PMS connectivity
- Hosted payments
- Multilingual voice
- Existing-number routing
- Interaction history

Use icons + short text, not vendor logos unless approved.

## 4. Use-case cards

Three or four cards:
- After-hours coverage
- Front-desk overflow
- Direct reservations
- Routine guest service

Each card:
- simple icon
- 3–5 word title
- 1–2 sentence explanation
- optional Learn more →

Cards should be scannable and equal height.

## 5. Reservation workflow

A horizontal desktop journey that stacks vertically on mobile:

1. Guest calls
2. Intent/language understood
3. PMS queried
4. Room/rate selected
5. Secure payment link
6. Reservation confirmed

Use actual HTML/SVG for the canonical implementation rather than embedding text into a raster image.

## 6. Live Call component

A reusable product-proof module.

Suggested structure:
- status: Live Call
- timer
- transcript
- detected language
- action timeline
- connected system status
- final outcome

Semantic states:
- neutral
- processing
- connected
- warning/escalated
- confirmed

## 7. Integrations architecture

Central **AllHourDesk** node connected to:
- Hotel Phone
- PMS
- Messaging
- Payments
- Audit Trail

Below the visual:
**Your PMS remains the source of truth. AllHourDesk connects guest conversations to the systems your hotel already operates.**

Use real partner/vendor names only where the integration is currently available and public use is appropriate.

## 8. Multilingual component

Show:
- live call transcript
- language detected
- same workflow in different languages
- common-property-question cards

Do not imply unlimited or equal production quality across every language. Published language support must match tested product capability.

## 9. Trust cards

Four pillars:
- Grounded data
- Secure payments
- Human / configured escalation
- Audit trail

Each includes:
- icon
- concise title
- concrete operational explanation
- optional proof/state UI

Avoid security theatre. The value is control and traceability.

## 10. Pilot rollout

Five stages:
1. Discovery
2. Test line
3. Property setup
4. Limited forwarding
5. Expand coverage

This component is especially useful on:
- homepage
- demo page
- onboarding / how-it-works page

Use a progress journey rather than a dense process diagram.

## 11. Corporate trust block

Show:
- Allhourdesk Limited
- Ireland
- company number
- contact channels
- founders / leadership link

Purpose: establish a real accountable vendor, not inflate company size.

## 12. CTA band

Dark ink or oxblood surface.

Headline:
**See AllHourDesk handle a real hotel call.**

Body:
Invite prospects to bring their PMS, phone setup and real scenarios.

Primary action:
**Book a 20-minute demo →**

## 13. Footer

Columns:
- Platform
- Solutions
- Trust
- Company
- Legal

Include legal company identity and monitored contact details.

## 14. Forms

Use:
- 48px input height minimum
- labels above fields
- clear inline validation
- no placeholder-only labels
- straightforward success confirmation
- minimal fields on demo form

Recommended demo fields:
Name, work email, hotel/company, country, properties, PMS, primary use case, message.

## 15. Interaction patterns

- hover: subtle border/surface change
- selected state: oxblood accent
- success: muted green + icon + text
- loading: skeleton/progress, never indefinite spinner without context
- errors: explain what failed and what happens next
- links: visible focus and hover states

## 16. Breakpoints

Suggested:
- mobile: < 768px
- tablet: 768–1023px
- desktop: ≥ 1024px
- wide: ≥ 1280px

Components should be content-driven rather than dependent on fixed heights.
