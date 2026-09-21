# AllHourDesk Website Design System — vNext

## 1. Brand character

The visual system should communicate:

- **Hospitality-aware** — warm, considered and human
- **Operationally credible** — systems, workflows and outcomes are visible
- **Premium but restrained** — no generic neon AI aesthetic
- **Enterprise-aware** — clear hierarchy, trust, integrations and control
- **Software-first** — product UI is the primary proof; photography is supporting atmosphere

Target impression: **boutique hotel precision + enterprise software confidence**.

## 2. Core principles

### Product proof over decoration
Show the guest call, PMS lookup, payment and reservation outcome. Avoid decorative technology imagery that does not explain the product.

### Hospitality cues, not a hotel website
Use warm materials, subtle architectural arches, reception-bell motifs and room imagery sparingly. The visitor should immediately understand that AllHourDesk is software.

### Calm confidence
Prefer whitespace, short copy blocks, strong hierarchy and subtle motion over dense editorial layouts.

### Precision builds trust
Operational facts, statuses and integrations should look structured and traceable. Avoid unsupported metrics, certifications or generated customer claims.

## 3. Colour

Retain the existing brand palette:

| Token | Value | Primary use |
| --- | --- | --- |
| Oxblood | `#5B1A1E` | Primary CTA, selected states, brand accents |
| Oxblood Deep | `#241012` | Dark product surfaces / premium dark bands |
| Ink | `#1A1614` | Main text |
| Bone | `#F7F4EF` | Page background |
| Bone 2 | `#EFEAE1` | Alternate sections / cards |
| Clay | `#D9A08A` | Accent on dark surfaces |
| Ink 70 | `#4A423E` | Body copy |
| Ink 45 | `#8A817B` | Metadata / captions |
| Rule | `#D7CFC4` | Borders and separators |

Add one restrained semantic success colour for confirmed/connected states only: `#247A59`.

Do not introduce generic SaaS blue.

## 4. Typography

### Instrument Serif
Use for:
- hero headline
- major section headings
- occasional editorial accent phrases

### Archivo
Use for:
- navigation
- body copy
- cards
- forms
- buttons
- product UI labels

### JetBrains Mono
Use only where the content is truly operational/data-like:
- timestamps
- call IDs
- booking locators
- technical logs
- small status metadata

**Do not use mono for navigation, general labels or full sentences in vNext.**

## 5. Type scale

Desktop starting point:

- Display XL: 72px / 0.98
- H1: 64px / 1.00
- H2: 44px / 1.08
- H3: 28px / 1.18
- Lead: 20px / 1.55
- Body: 17px / 1.65
- Small: 14px / 1.55
- Meta: 12px / 1.4

Mobile:

- H1: 44–48px
- H2: 34–38px
- H3: 24–26px
- Body remains 16–17px

Use `text-wrap: balance` for major headings and `text-wrap: pretty` for body copy.

## 6. Layout

- Content max width: **1280px**
- Standard readable text width: **620–720px**
- Base spacing unit: **8px**
- Desktop section spacing: **96–128px**
- Mobile section spacing: **56–72px**
- Standard desktop gutters: **40–56px**
- Mobile gutters: **20–24px**

The previous 104px numbered side rail should no longer be the default page structure. It may be retained selectively for a technical timeline or How It Works treatment.

## 7. Surfaces and cards

Cards should be easier to scan than the existing rule-heavy editorial layout.

- Standard card radius: **14px**
- Compact UI radius: **10px**
- Button radius: **8px**
- Pill/status radius: **999px**
- Border: 1px `#D7CFC4`
- Shadows: extremely subtle and only for layered/elevated product UI

Avoid glassmorphism and strong drop shadows.

## 8. Buttons

### Primary
Oxblood background, bone text.

Label style: **Book a demo →**, not uppercase mono.

### Secondary
Bone/transparent background, oxblood or ink border/text.

### Text link
Short, descriptive and directional, e.g. **Explore integrations →**.

Minimum touch target: 44px.

## 9. Product UI visual language

Product visuals should use:
- warm-white cards
- subtle structural borders
- oxblood selected states
- green only for success/connected
- concise real-world hotel data
- simple icons
- thin connector lines
- clear state progression

The product UI should look plausible and usable, not futuristic.

## 10. Photography and illustration

Recommended ratio across the marketing site:

- 60% product UI / diagrams / interface proof
- 25% typography and structured content
- 15% hospitality photography / atmosphere

Avoid:
- generic call-centre headset imagery
- robots / humanoid AI
- glowing neural networks
- blue-purple AI gradients
- fake customer photos or fake testimonials

## 11. Motion

Motion should clarify state changes:
- transcript appears
- PMS lookup resolves
- payment status changes
- reservation confirms

Use 180–300ms transitions. Respect `prefers-reduced-motion`.

Do not use perpetual decorative animation.

## 12. Responsive behaviour

- Desktop hero: 2-column, copy left / product visual right
- Tablet: reduce visual density before reducing type size
- Mobile: stack product visuals vertically
- Use a hamburger navigation; do not horizontally scroll the main nav
- Avoid horizontal-scroll diagrams where a vertical responsive version can communicate the same flow
- Keep primary CTA visible within the first mobile viewport

## 13. Accessibility

- WCAG AA contrast for body text and controls
- visible keyboard focus states
- semantic heading hierarchy
- meaningful alt text for informative visuals
- generated decorative imagery should use empty alt text
- do not encode meaning by colour alone
- all interactive states must have text/icon reinforcement
