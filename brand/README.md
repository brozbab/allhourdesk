# AllHourDesk brand kit — "Night Log" (direction 4A)

## Palette
| Token | Hex | Use |
|---|---|---|
| Oxblood | `#5B1A1E` | Primary accent. Hero field, CTAs, labels, the mark. |
| Oxblood deep | `#241012` | Dark surface for after-dark pages and social posts. |
| Ink | `#1A1614` | Text, structural hairlines, footer band. |
| Bone | `#F7F4EF` | Page background, reversed text on dark. |
| Bone 2 | `#EFEAE1` | Alternate band, log strips. |
| Clay | `#D9A08A` | Accent **on dark only** (replaces oxblood there). |
| Ink 70 | `#4A423E` | Body copy. |
| Ink 45 | `#8A817B` | Captions, section numbers. |
| Rule | `#D7CFC4` | Hairlines on bone. |

Social-post recipe: oxblood field, bone text, one clay or bone hairline. Timestamp in mono, top-left. Never gradients, never a third colour.

## Frame
The page sits under a **6px ink (`#1A1614`) top border** — a fixed part of the layout, not decoration. Keep it on every page and template.

## Type
- **Instrument Serif** — headlines only, 26px+, letter-spacing −0.015em.
- **Archivo** — all body and UI text, 400/600/700.
- **JetBrains Mono** — timestamps, labels, buttons, codes. Uppercase, .08–.14em tracking. Never a sentence.

Google Fonts:
`https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=Archivo:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;700&display=swap`

## Logo
- `logo/allhourdesk-lockup-*.svg` — **primary lockup**: mark + wordmark. Use this everywhere by default (nav, decks, email, social profile).
- `logo/allhourdesk-wordmark-*.svg` — text only, tight spaces.
- `logo/allhourdesk-stacked-*.svg` — with "NIGHT DESK · 24/7" strapline.
- `logo/allhourdesk-mark-*.svg` — mark alone (24-hour ring + voice waveform); use above 24px.
- `logo/allhourdesk-appicon-*.svg`, `favicon.svg` — 512px app icon.

Clear space: one ring-diameter on all sides. Minimum lockup width 140px. Do not recolour outside the palette, do not add effects, do not place the oxblood mark on the deep-oxblood surface.

## Icons
`icons/*.svg` — 24px grid, 1.4px stroke, round caps, `currentColor`. Set colour via CSS (`color: var(--ahd-oxblood)`).

## Tokens
- `tokens.css` — CSS custom properties + usage rules.
- `tokens.json` — for JS/design tooling.
- `tailwind.tokens.js` — Tailwind theme.extend fragment. Drop into `frontend/`'s Tailwind config to keep the dashboard and the marketing site on the same palette if they ever need to share a component.

## Voice
Headline: **Your night manager never sleeps.**
Plain, factual, specific to hotel operations. Timestamps and locators over adjectives. No exclamation marks.

## About the exported page (`index.html`)
The 4A layout is deliberately **type-only** — the wordmark in the nav is live text (Instrument Serif) and section headings use mono labels rather than icons, so the page stays crisp at any size and needs no asset loading beyond the favicon. The logo and icon SVGs in this kit are therefore not referenced by that file; they are there for app UI, favicon, social, decks and any place the page's typography can't do the job.

Swap in the SVG lockup if you prefer:
```html
<img src="brand/logo/allhourdesk-lockup-oxblood.svg" alt="AllHourDesk" height="34">
```
Icons inherit text colour, so `<span style="color:var(--ahd-oxblood)">` around an inlined icon is all the tinting needed.

Source: designed in Claude Design (`claude.ai/design`), project "AllHourDesk website design", pulled into this repo via the design-sync MCP.
