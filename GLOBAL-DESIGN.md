# Global Design System

A general-purpose UI foundation. This document is the written source of truth.

**North star.** Colour is spent, not spread. One green marks advancing work, one indigo marks saving inside a card, and everything else that is coloured is coloured because it means something — a state or an ownership. Depth comes from a 1px line, not a shadow. Surfaces are dense because the job is comparison.

---

## 1. Foundations

### Fonts

| Role | Family | Weights | Use |
|------|--------|---------|-----|
| Display / Headings | Inter | 500, 600, 700 | Page titles, section headings, big stat numbers |
| Body | IBM Plex Sans | 400, 500, 600, 700 | Everything textual — descriptions, labels, table content |
| Numeric / Mono | IBM Plex Mono | 400, 500, 600 | Codes, quantities, money, dates in tables |

All three families are free (Google Fonts / IBM) and carry the full weight range used here, so headings render correctly without any separately-licensed font. Inter's optical spacing is tuned for UI, which is why it also carries the display and heading roles.

### Type scale

| Token | Size | Line height | Weight | Family |
|-------|------|-------------|--------|--------|
| `display` | 36px | 120% | 700 | Inter |
| `h1` | 30px | 120% | 700 | Inter |
| `h2` | 24px | 130% | 600 | Inter |
| `h3` | 20px | 130% | 600 | Inter |
| `h4` | 18px | 140% | 600 | Inter |
| `body` | 14px | 150% | 400 | IBM Plex Sans |
| `small` | 13px | 150% | 400 | IBM Plex Sans |
| `caption` | 12px | 150% | 400 | IBM Plex Sans |
| `label` | 11px | — | 600, UPPERCASE, +0.06em | IBM Plex Sans |
| `numeric` | 12–13px | — | 500 | IBM Plex Mono |

**The Comparison Rule.** Anything a person will scan down a column — money, quantity, a document code, a date — is set in mono so the digits align. If two values will be compared, they align.

---

## 2. Colour

Names say what a colour *does*, not what it looks like. Using one in the wrong place should read as wrong.

### Accents

| Token | Hex | Meaning |
|-------|-----|---------|
| `brand.advance` (signal green) | `#8DC63F` | The one green thing on a screen. Marks the action that advances work — submit, approve, send. One per screen. |
| `brand.advance-hover` | `#7AB034` | Advance button hover. |
| `text.on-advance` (green ink) | `#062c12` | Near-black green text that sits *on* signal green. Light text on green is forbidden. |
| `text.on-tint` (green ink on tint) | `#3f6212` | Readable dark green for text/icons where green is a pale wash — active nav, tints. |
| `brand.commit` (commit indigo) | `#4f46e5` | Saving inside a card. Deliberately not green — saving is not advancing. |
| `brand.commit-hover` | `#4338ca` | Commit button hover. |
| `brand.sales` (sales rose) | `#e11d48` | Ownership accent, paired with indigo on the 3px card spine. |

### Neutrals

| Token | Hex | Use |
|-------|-----|-----|
| `surface.page` (page ground) | `#f7f8fa` | The canvas the whole app sits on. **Never white.** |
| `surface.card` (surface white) | `#ffffff` | Cards, tables, sidebar, topbar — a sheet laid on the ground. |
| `text.default` (ink) | `#0f1729` | Primary text. |
| `text.muted` (ink muted) | `#64748b` | Secondary text, column headers, field labels, hints. |
| `border.default` (hairline) | `#e2e8f0` | The default border of every element. Nearly all separation is this one line. |
| `surface.hover` (row hover) | `#f8fafc` | Faint fill under a hovered table row. |
| `chart-grid` | `#eef2f7` | Chart gridlines only. |

### Status anchors

| Token | Hex | Meaning |
|-------|-----|---------|
| `status-amber` | `#d97706` | Waiting. |
| `status-emerald` | `#059669` | Won / done / delivered. |
| `status-red` | `#dc2626` | Overdue / refused. |

### Text on a solid colour (`on-color.*`)

Per Rule 6 (§7), text placed on a solid-coloured surface is pre-resolved to black or white by contrast, so components never guess. `on-color.advance` is the one branded exception — it keeps the near-black green-ink `#062c12` rather than pure black (still passes AA). Values differ by mode because the dark accents are lifted.

| Token | On (fill) | Light text | Dark-mode text |
|-------|-----------|-----------|----------------|
| `on-color.advance` | signal green | `#062c12` (green ink) | `#062c12` |
| `on-color.commit` | commit indigo | white | white |
| `on-color.sales` | sales rose | white | black |
| `on-color.amber` | status amber | black | black |
| `on-color.emerald` | status emerald | black | black |
| `on-color.red` | status red | white | black |

### Greyscale (slate)

`0 #ffffff` · `50 #f7f8fa` · `100 #f1f5f9` · `200 #e2e8f0` · `300 #cbd5e1` · `400 #94a3b8` · `500 #64748b` · `600 #475569` · `700 #334155` · `800 #1e293b` · `900 #0f1729`

### Colour rules

- **The Spent Colour Rule.** Every colour on a screen is state or ownership. If you cannot say which of the two it is doing, it should be slate.
- **The One Green Rule.** Signal green marks advancing the lifecycle, one button per screen. A second green button means one of them is not really an advance.
- **On-green contrast.** Text on signal green is always `#062c12`. White on green fails contrast and is forbidden.
- **Dark mode** ships as a second token set (see §8). Semantic token names are identical across modes; only their values change.

---

## 3. Spacing

Spacing is an 8px-based scale with a 4px half-step. Every margin, padding and gap should be a token from this scale — never an arbitrary value.

### Scale

| Token | px | rem | Typical use |
|-------|----|----|-------------|
| `space-1` | 4 | 0.25 | Icon-to-label gap, tight chip padding, hairline offsets |
| `space-2` | 8 | 0.5 | Table cell padding, gap inside a compact control |
| `space-3` | 12 | 0.75 | Default gap between related controls |
| `space-4` | 16 | 1 | Card padding, gap between fields |
| `space-5` | 20 | 1.25 | — |
| `space-6` | 24 | 1.5 | Gap between sections inside a card |
| `space-8` | 32 | 2 | Page padding, gap between cards |
| `space-10` | 40 | 2.5 | Major section separation |
| `space-12` | 48 | 3 | Page gutters on wide screens |

### Semantic aliases

For readability, these named aliases map onto the scale so intent is obvious at the call site:

| Alias | Value | Meaning |
|-------|-------|---------|
| `cell` | `space-2` (8) | Padding inside a table cell |
| `gap` | `space-3` (12) | Gap between two related elements |
| `card` | `space-4` (16) | Interior padding of a card or panel |
| `section` | `space-6` (24) | Gap between sections within a page region |
| `page` | `space-8` (32) | Outer page padding / gap between top-level cards |

### Spacing rules

1. **Use the scale, never a raw number.** A padding of `10px` or `15px` is a defect even when it looks fine — the next change will miss it. Round to the nearest token.
2. **Stepped hierarchy, not uniform gaps.** Space grows with the size of the boundary it separates: `cell` (8) inside a cell, `gap` (12) between controls, `card` (16) inside a card, `section` (24) between sections, `page` (32) between cards. Never use the same gap for a cell boundary and a section boundary.
3. **Density is the point.** These screens are read on office monitors by people comparing many rows. When in doubt, choose the *tighter* token — information wins over air. Dense table rows commonly run at 8px vertical padding, not 16.
4. **Padding is symmetric by default.** A card is `16` on all four sides unless there's a reason. Asymmetric padding is a signal, not a habit.
5. **Vertical rhythm follows the type.** Space above a heading is larger than space below it, so a heading groups with the content it introduces (e.g. `section` above an `h3`, `gap` below).
6. **Gaps belong to the container, not the child.** Use a parent gap (Figma auto-layout gap / CSS `gap`) rather than margins on each child, so items stay evenly spaced when one is added or removed.
7. **Icon-to-label is always `space-1` (4) or `space-2` (8).** Never wider — a label should read as attached to its icon.

---

## 4. Shape & elevation

### Corner radius

| Token | px | Use |
|-------|----|----|
| `radius-xs` | 4 | Small badges, icon buttons, chart frames |
| `radius-sm` | 6 | **The house radius** — buttons, inputs, most surfaces |
| `radius-md` | 8 | Cards, panels, larger containers |
| `radius-lg` | 12 | Feature cards, modals |
| `radius-xl` | 16 | Large containers |
| `radius-pill` | full | States and counts only — status pills, badges, avatars, toggles |

**The Single Radius Rule.** One house corner (6px) does most of the work. If a surface needs to feel different, change its border or its ground — not its radius. A pill shape means *this is a state or a count*, never merely *this is small*.

### Borders

Borders are 1px and everywhere; the hairline (`#e2e8f0`) is the default. The one deliberate exception is the **3px coloured top rule** that marks ownership on a panel (indigo = one team, rose = another) or the accent on a stat tile — a heavier line used only where it carries meaning.

### Elevation

Almost flat, by rule. Separation between two resting surfaces is a **1px hairline against the off-white ground, not a shadow.**

- `shadow-floating` — `0 10px 15px -3px rgb(0 0 0 / .1), 0 4px 6px -4px rgb(0 0 0 / .1)` — dropdowns, dialogs, tooltips.
- `shadow-menu` — `0 4px 6px -1px rgb(0 0 0 / .1), 0 2px 4px -2px rgb(0 0 0 / .1)` — select / dropdown menus.

**The Hairline Rule.** Depth is a line, not a shadow. Shadows are reserved for layers the browser genuinely floats above the page. If you reach for a shadow to separate two resting surfaces, use a border instead.

---

## 5. Components

### Buttons

House radius (6px), 36–38px tall, 16px horizontal padding, label at 14px / 500.

| Variant | Fill | Label | Use |
|---------|------|-------|-----|
| **Advance** | `#8DC63F` → hover `#7AB034` | `#062c12` (green ink) | The one lifecycle action. One per screen. |
| **Commit** | `#4f46e5` → hover `#4338ca` | white | Saving inside a card. |
| **Secondary** | pale green tint → hover deeper tint | `#3f6212` | Secondary affirmative actions. |
| **Outline** (workhorse) | white, hairline border | ink | The default for almost every secondary action. |
| **Destructive** | `#dc2626` | white | Delete, remove, refuse. |

Focus ring is always **green**, regardless of button colour. Disabled drops to 50% opacity and stops receiving pointer events.

### Inputs

Transparent fill (takes the surface behind it), hairline border, house radius, ~40px tall. Focus is a 1px **green** ring. Error is a red border with a red hint beneath. Disabled is not-allowed cursor at half opacity.

### Selection controls

Checkbox, radio and toggle use **signal green** for the checked / selected / on state — these express active state, which is green's job. Commit indigo is never used here.

### Status pills & badges

Fully round, 1px border, a background/text/border triple per state. A pill means a state or a count — never merely "small". The text on a solid-coloured pill comes from the `on-color.*` token for that colour, which is pre-resolved to black or white by contrast per Rule 6 (and differs by mode — e.g. red takes white text in light mode but black in dark, because the dark red is lifted). Count badges render only when the count is above zero (no empty circle), cap visibly at "9+".

### Cards & panels

House-to-`md` radius, white on the page ground, hairline border, **no shadow**. Working padding is `card` (16). Optional 3px ownership spine on the top edge. Stat tiles carry a 3px accent top rule — **accent on the rule, never on the number**; the number stays ink.

### Charts & data viz

- **Single series → signal green** (line, area fill at ~12% opacity, bar chart, sparkline, progress ring). Bars are all green; grey is reserved for gridlines.
- **Categorical → green, indigo, amber, rose, emerald** (max 5). Use this only when a chart genuinely encodes categories by colour; a plain single-metric bar chart stays all green.
- **Gridlines** are `#eef2f7`; **axes and labels** are slate.
- Tooltips use the ink surface (`#0f1729`) with white text.
- Table should has pagination 10/20/50. And Freeze the header of the table
> Note: the source system defined only the gridline colour for charts. The categorical palette above is a derived default following the Spent Colour Rule; if a canonical chart palette exists in code, use those values instead.

---

## 6. Do & Don't

**Do**
- Reserve signal green for advancing work, one button per screen.
- Separate resting surfaces with a 1px hairline.
- Set anything compared down a column in mono.
- Use a scale token for every margin, padding and gap.
- Put accent colour on the rule beside a number, not on the number.
- State what an empty screen is *for*, not just that it is empty.

**Don't**
- Put light text on signal green.
- Reach for a larger radius expecting a visibly larger corner — pick by meaning, not size.
- Add a decorative shadow. Shadows mean *this floats above your work*.
- Colour anything for mood. Every colour is state or ownership.
- Use a pill shape for anything that is not a state or a count.
- Hand-write a value that already has a token — a duplicated value is a defect even when it renders correctly.

## 7. Dark mode

Dark mode is a second token set, not a separate system. Every semantic token (`surface.card`, `text.default`, `brand.advance`…) keeps its **name** across modes; only its **value** changes. Components reference the semantic name, so nothing in a component needs editing to switch modes.

### Palette

| Semantic token | Light | Dark |
|----------------|-------|------|
| `surface.page` | `#f7f8fa` | `#0b0f1a` |
| `surface.card` | `#ffffff` | `#141a29` |
| `surface.hover` | `#f8fafc` | `#1c2436` |
| `text.default` | `#0f1729` | `#e8ecf3` |
| `text.muted` | `#64748b` | `#94a3b8` |
| `border.default` | `#e2e8f0` | `#2a3346` |
| `chart.grid` | `#eef2f7` | `#232c40` |
| `brand.advance` | `#8DC63F` | `#8DC63F` (unchanged) |
| `brand.commit` | `#4f46e5` | `#6366f1` (lifted) |
| `brand.sales` | `#e11d48` | `#f43f5e` (lifted) |
| `status.amber / emerald / red` | `#d97706 / #059669 / #dc2626` | `#f59e0b / #10b981 / #ef4444` (lifted) |

### Rules for dark mode

1. **Signal green does not change.** `#8DC63F` with dark green-ink text (`#062c12`) passes AA in both modes (contrast 7.5:1), so the Advance button is byte-for-byte identical light and dark. Changing it would weaken the one signal the system depends on.
2. **Lift indigo, rose and status hues, don't darken them.** Saturated colours that read well on white go muddy on near-black; the dark set nudges them lighter/brighter so they keep the same *role strength*.
3. **Surfaces get lighter as they get closer.** The page is the darkest layer (`#0b0f1a`); cards sit above it a step lighter (`#141a29`); hover/raised surfaces lighter still (`#1c2436`). Depth is still a step in value plus a 1px border — never a shadow.
4. **The green-ink-on-tint flips to a light green.** Where light mode uses dark green on a pale wash, dark mode uses light green (`#a5d84f`) on a deep green wash (`#1e2a12`) — same relationship, inverted.
5. **All body/label text must clear AA (4.5:1) on `surface.card`.** The dark ink (`#e8ecf3`) and muted (`#94a3b8`) are chosen to pass; if you introduce a new dark surface, re-check any text placed on it.
6. Any colour should be contrast to each other, between black and white, if label colour in black then text be white, then if label in white the text should be black.

   
## 8. Others


1. **Icons** — install the official **Lucide** Figma plugin (24px grid, ~2px stroke) and use it as the single icon source so glyphs stay consistent across the platform.
2. **Fonts** — Inter, IBM Plex Sans and IBM Plex Mono are all free; enable them in the workspace (all three are on Google Fonts).

*Nothing enforces these rules automatically — they hold by convention and review, which is the reason for writing them down.*
