# Atera Design System

**Atera** is an all-in-one, AI-powered IT management platform for MSPs and IT departments — RMM (remote monitoring & management), PSA (helpdesk / ticketing / billing), network discovery, patch management, and a heavy AI layer (Autopilot, AI Copilot) that resolves tickets and automates IT work. Atera's product vocabulary is dense with IT terms: *monitored assets*, *tickets*, *patches*, *compliance*, *customers/contacts*, *technicians*, *alerts*, *agents*, *contracts*.

This design system captures **Atera Theme 2.0** — the current semantic-token-driven system in production use on the web app.

## Sources

- **Figma (mounted)** — `Screens Atera.fig`, one page ("Page-1") with four frames: a Cheat Sheet of primitive components, a Desktop app screen (AI Center overview), a Monitored Assets table, and a Patching-compliance tooltip. Pseudocode in `/Page-1/**/*.jsx`.
- **Codebase** — [AteraAIOPlatform/WebApp.Nga](https://github.com/AteraAIOPlatform/WebApp.Nga) @ `master`, subtree `libs/shared/ui-core/src/`. Imported: `design-tokens/colors.ts`, `design-tokens/roles-from-figma.ts`, `foundations/colors/**/*.mdx`, `lib/style/atera-theme-2/**`, `lib/style/variables.scss`. These are the canonical source of truth for colors, typography and semantic role tokens.
- **Uploads** — `Atera-logo.svg`, `atera logo symbol svg.txt` (brand red-pink mark #FF1638), and the Gellix font family.

> ⚠️ **Font note.** The uploaded Gellix family does **not match** what the codebase uses in Theme 2.0: the SCSS and Figma variables declare **Inter** (headings/display) and **Roboto** (body/caption) with **Roboto Mono** for code. I've built `colors_and_type.css` against the codebase truth (Inter/Roboto) and left Gellix in `uploads/` untouched. **If Gellix is the correct brand face, let me know** and I'll swap the stack and copy the `.otf`s into `fonts/`.

---

## Index

- `colors_and_type.css` — primitive hues, semantic role tokens, radii, spacing, shadows, type classes. **Start here** for any new UI.
- `assets/` — logos (wordmark + red-pink mark).
- `preview/` — Design System cards (type, color, spacing, components, brand).
- `ui_kits/webapp/` — React recreation of the Atera web app (AI Center, Monitored Assets table, patching tooltip).
- `libs/shared/ui-core/` — reference-only imports from the codebase. Do not edit.
- `SKILL.md` — skill descriptor for use as an Agent Skill.

---

## CONTENT FUNDAMENTALS

**Voice.** Flat, direct, informational. Atera writes like a calm enterprise IT tool that happens to have an opinion. Zero marketing fluff in the product itself; taglines live on marketing pages and never leak into the app.

- **Sentence case everywhere** except the product name Atera. Nav items, buttons, page titles, section headers: `Monitored assets`, `Open tickets`, `All customers`, `Install agent`, `Upgrade to Growth`.
- **"You" is implied, not written.** Most UI copy addresses the user by stating a task, not describing who does it. Empty states break the rule and speak to the user directly: *"Manage your organization's inventory. Create asset types, view your devices in the inventory, control statuses and assign assets to contacts — all in one place."*
- **Verbs are imperative on action surfaces.** Buttons read `Install agent`, `Sync Azure`, `Save view`, `New device`, `Upgrade to Growth`. No "Click here," no exclamation marks, no trailing periods on buttons.
- **Labels are nouns.** Table columns and fields: `Device name`, `Customer`, `Folder`, `Last login`, `Availability`, `Last patch scan`, `Available patches`, `Pending reboot`, `Open tickets`.
- **Numbers win over words.** Atera loves single-number KPIs: `247 All monitored assets`, `25 hr Total hours saved`, `88% Users satisfaction`, `9% Reopen rate`, `4 hr Daily Avg`. Always a terse lowercase label underneath.
- **Time is casual.** `a minute`, `2 min`, `4 min`, `an hour`, `18 hours`, `a day`, `2 days`, `a month`, `3 months`, `a year ago` — relative, never absolute, in tables.
- **Status language is neutral.** `Fully Patched`, `In Progress`, `Unresponsive`, `Failed` — Title Case *only* in status enumerations. `New`, `Retired`, `Moderate-risk devices`, `High-risk devices` follow the same pattern.
- **AI copy is task-first, not magical.** `AI Center`, `AI Filter`, `Actionable insights`, `AI optimization tasks`, `Autopilot hours saved on tickets`, `Sync Azure AD & Microsoft 365 — Boost AI with continuous syncs for updated info and seamless resolution`. No "sparkles ✨", no anthropomorphising ("Let me help you…").
- **No emoji in product UI.** A violet sparkle icon (`BrandSparks`) is the only glyph that reads "AI", and it's a vector, not an emoji.
- **Error copy is blunt.** `Error text` appears in red below a field; no apology, no "Oops."

Specific example strings you'll see on real screens:

> **Page title:** `Monitored assets` · **Subhead filter pill:** `Default view ▾` · **Primary CTA:** `+ New device` · **Sidebar section:** `AI Center · Overview · Analytics · Actionable insights · Custom instructions · Optimization` · **KPI row:** `247 All monitored assets · New` · `11 Open tickets · New` · `32 Active alerts · New` · `5 Security issues · +2 to` · **Banner:** `Note: Banner text massage — Link button  Button  Button`

---

## VISUAL FOUNDATIONS

**Overall vibe.** Dense, information-first enterprise IT dashboard. White card surfaces on a warm-off-white page. Crisp, unsentimental. One **loud pink** brand accent (`#ff176b`) used exclusively for brand moments (primary CTAs, logo mark, brand KPI lines). A muted dark teal/green (`#023233`) forms the vertical sidebar — Atera's signature navigation color.

### Color

- **Brand = Pink.** `--fill-brand-bold: #ff176b` is the primary CTA fill. Hover `#e41560`, pressed `#c61253`. Used sparingly — one primary CTA per view.
- **Accent = Blue.** `#1d7afc` / `#0c66e4` for links, info banners, "AI assisted" data lines, secondary actions.
- **AI = Violet.** `#8f47ae` text, `#a851cd` icon, `#f9ecff` subtle fill. AI-specific surfaces (buttons, avatars, hero panels) use **flat violet** — no gradients. The pink→teal→black radial gradient is **not** part of the system; do not introduce it.
- **Neutrals.** 11-step gray ramp (`#f9f9f9 → #1a1a1a`). Backgrounds use `#f4f4f4` (page) / `#ffffff` (cards). Body text `#1a1a1a`, secondary `#6b6b6b`, tertiary/placeholder `#959595`.
- **Status.** Success lime/green (`#1f845a` bold, `#d3f1a7` subtle); Danger red (`#c9372c` / `#ffeceb`); Warning orange (`#c25100` / `#fff3eb`); Info blue (same as Accent).
- **Discovery/Purple** (`#6e5dc6`) distinguishes discovery states from AI violet.
- **Sidebar** uses neutral `#1a1a1a` (with `#2a2a2a` for hover/active rows). The old dark green (`#023233`) has been retired — do not introduce it.

### Type

- **Inter** — all headings and display. `32/42px SemiBold -1px` for page titles, down to `20px SemiBold -0.5px` for card titles. The negative letter-spacing is consistent across every heading size.
- **Roboto** — all body, caption, table cells, and form input text. 14/20 is the workhorse size.
- **Roboto Mono** — code blocks and API payload renderings.
- No italics except one utility class (`body-md-regular-italic`) for muted inline quotes.
- No underlines except on `<a>` hover.

### Spacing & Layout

- **4-point grid.** `4/8/12/16/20/24/32/40/48/64`. Card interior padding is typically 16 or 24. Table row height 44px.
- **Cards.** `background: #ffffff`, `border-radius: 12px` (sometimes 16), `border: 1px solid #e9e9e9` OR `box-shadow: 0 1px 3px rgba(26,26,26,0.08)`. Rarely both.
- **Density.** Tables cram ~14 rows above the fold on a 1080p screen. Sidebar is narrow (64–72px collapsed icon rail) plus a 240px secondary nav when a section is opened.
- **Fixed chrome.** 56px top header, 64px sidebar — both fixed. Content scrolls underneath.

### Backgrounds & Imagery

- **Flat fills only.** No illustrations, no textures, no hand-drawn anything. One wordmark + one mark + monochrome product icons.
- **Hero surfaces are flat.** AI moments use a flat near-black surface (`#1a1a1a`) with a violet (`#8f47ae`) accent or sparks mark — never a radial pink→black gradient. Brand surfaces use the linear pink wash (`--gradient-brand`) only.
- **Charts** — pastel fills (purple `#b8acf6`, pink `#ff7495`, blue `#85b8ff`) on white, thin 1px gridlines in `#e9e9e9`, dashed avg-line in brand pink.

### Motion

- **Subtle, functional.** 150–200ms ease-in-out for hovers, 250ms for drawers/menus, no bouncy springs.
- **Loading states** use a spinning circle in brand pink.
- **No celebratory confetti** outside one-off moments (a `confetti` component exists in the lib but is used maybe twice a year).

### Hover / Press

- **Primary button.** hover → `#e41560` (one step down on the pink ramp), pressed → `#c61253`.
- **Secondary/neutral button.** hover → `#f4f4f4` background + `#444444` text; pressed → `#e9e9e9`.
- **Icon-only button.** hover adds a `#e9e9e9` circle behind the icon.
- **Table rows.** hover `#f9f9f9`.
- **No scale transforms**, no shadow jumps. Only color.

### Borders, Shadows, Radii

- **Borders** are `1px` `#e9e9e9` (secondary) or `#d8d8d8` (primary). Never darker in body UI.
- **Shadow system.** `xs` (0 1px 2px rgba(26,26,26,0.06)) for inputs; `sm` for cards; `md` for dropdowns; `lg` for modals; `menu` uses a brand-blue tinted shadow `0 4px 16px rgba(0,99,255,0.10)`.
- **Corner radii.** Chips/pills `9999px`. Buttons `8px`. Cards `12px`. Modals/drawers `16–24px`. Inputs `8px`.

### Transparency & Blur

- Used **only** for scrims and tooltip backdrops. No frosted glass in the product.
- Modal scrim: `rgba(26,26,26,0.40)`. Tooltip background: solid `#1a1a1a`, no alpha.

### Layout rules

- **Page title** always top-left, `24px SemiBold Inter`. Optional view picker chip immediately to its right.
- **Primary CTA** always top-right, pink.
- **Left rail** always dark green, fixed 64px wide.
- **Secondary nav** appears as a 240px inner sidebar when a section (AI Center, Settings) is active.
- **KPI row** sits above tables: four to six mini-cards, each `[icon · bold number · small label]`.

---

## ICONOGRAPHY

Atera uses a **custom in-house icon set** — name-coded in Figma and code under tokens like `Format=Outline, Weight=Bold`, `Format=Stroke, Weight=Bold`, `Format=Outline, Weight=Fill`. The Figma file contains 27 "FormatOutlineWeightBold-N" and 13 "FormatStrokeWeightBold-N" instances — hundreds of unique vector icons drawn to Atera's own grid.

- **Visual style.** 24px artboard, ~1.75–2px stroke, rounded joins, outline-first. Two weight modes: **Bold Outline** (most common) and **Stroke** (for fine UI glyphs like chevrons). Fill variants exist (e.g. `Format=Outline, Weight=Fill`) for selected/active states.
- **Color.** Icons take their color from surrounding content tokens — neutral `#6b6b6b` by default, brand `#ff176b` in active state, status colors in chips/badges. Never multicolor.
- **No icon font.** Icons are individual SVG components (see `libs/shared/ui-core/src/lib/components/icon/`). They are imported and rendered as inline SVG.
- **No emoji** anywhere in the product. The only ✨-adjacent mark is `BrandSparks` / `IconSparksGradientFull` — a custom 4-pointed sparkle used exclusively to indicate AI affordances, rendered with the AI gradient.
- **Sparse decorative illustrations.** Empty states use a custom outline illustration (`IllustrationEnvelope` and a handful of others) — single-weight, monochromatic neutral gray, in a 200×200px artboard.
- **Substitution (this design system only).** Because the real Atera icon SVGs aren't bundled in the open ui-core tree, the UI kits here use **Lucide** at the same 24/1.75px stroke. This is a stand-in. The moment Atera's icon folder is made available, swap `lucide-static` for `@atera/icons`.

### Story icons (`assets/story-icons/`)

A separate library of **241 hand-illustrated SVGs** (`assets/story-icons/[name].svg`) used at *guidance moments* — verification dialogs, info tooltips, empty-state hero, wizard heads, benefits rows. They are **not UI icons** and follow different rules from Phosphor/Lucide:

- **Always render at `64 × 64` px.** Set both `width="64" height="64"` on the `<img>`. Don't let CSS pick the size; never `transform: scale()`; never `max-width:100%`.
- **Allowed sizes are 64 (default), 48 (tight info), 96 (once-per-feature celebration).** No 32, no 24, no inline-glyph sizes — for inline / status / toolbar glyphs reach for Phosphor instead.
- **Story-moment surfaces only.** Dialogs, info tooltips, empty states, wizard heros, benefits rows. Never in toolbars, nav, lists, status chips, buttons, or table cells.
- **Use as-drawn.** No tinting, no `filter: invert()`, no `hue-rotate`, no recolor. On dark surfaces use the white-silhouette pattern documented in `preview/components-story-icons.html`.

The full guidance — anatomy, sizing, do/don't contexts, dark-surface treatment — lives in `preview/components-story-icons.html`. **Read it before placing any story icon.**

Key assets copied to `assets/`:

- `atera-logo.svg` — full wordmark in brand red `#FF1638`.
- `atera-mark.svg` — the triangular symbol alone, for favicons and square surfaces.

---

## Workspace manifest

```
colors_and_type.css        Design tokens — START HERE
README.md                  This file
SKILL.md                   Agent-skill descriptor

assets/
  atera-logo.svg           Full wordmark
  atera-mark.svg           Triangle mark

preview/                   Design-System tab cards
  type-*.html  color-*.html  spacing-*.html
  components-*.html  brand-*.html

ui_kits/
  webapp/                  Web app recreation
    index.html             Runnable AI Center + Monitored Assets flow
    *.jsx                  Componentised recreations

libs/                      REFERENCE ONLY — imported from the codebase
  shared/ui-core/src/...
```
