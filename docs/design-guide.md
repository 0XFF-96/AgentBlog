# Design System: "Diagram"

The blog looks like a clear architecture diagram. Each section is a tinted **panel** with a coloured border. Panels hold white **cards**, and indigo **connectors** link one layer to the next.
The tokens are in [`styles/tokens.css`](../styles/tokens.css).

## 1. Principles
1. **Layers, not pages.** Each section is a numbered layer (① ② ③ ④) and answers one question.
2. **A question under every title.** Each panel title has an italic grey line under it that says what the section answers. For example: *What do I think?*
3. **Connectors explain the relationships.** An indigo arrow between panels carries a short italic label such as *distills into*.
4. **Dense inside, calm outside.** Rows are compact and lists are tight, with even spacing between panels.
5. **A dashed border means "not yet".** Use it for drafts, upcoming channels and optional parts.

## 2. Colour

| Role | Tint | Border | Used for |
|---|---|---|---|
| Blue | `#e9eff9` | `#5b7cc4` | ① Essays: the primary layer |
| Green | `#ebf4ea` | `#6aa36a` | ② Notes: work in progress |
| Amber | `#fdf3e2` | `#d29a3a` | ③ Me: identity and settings |
| Violet | `#f2ecf8` | `#8c68bd` | ④ Ask: endpoints for people and agents |
| Rose | `#fae8e7` | none | Rules, caveats and "what I won't do" |
| Wire | `#2b35a8` | — | Arrows, links and focus states |

Text is near-black `#1c1c1e`, with muted `#5f6168` for subtitles. Inline code uses `#f1f1f3` chips.
Dark mode keeps the same border hues and drops each tint to a very dark version of that colour.

## 3. Type
- **Source Serif 4:** an academic serif for body text (15px) and titles. Japanese text falls back to **Noto Serif JP**.
- **Source Sans 3:** only for tiny UI labels such as the OK/NG badges.
- **Serif italic in the muted colour** for the question line under each title and for connector labels.
- **Source Code Pro** at 12.5px in grey chips, for dates, versions and anything that looks like code.
- **Bold** only for key terms inside a list item, for example "**Virtual key** budget · rate limit".

## 4. Components

| Component | Spec |
|---|---|
| **Panel** | tint background, 1.5px coloured border, 8px radius, 16–24px padding |
| **Panel title** | `① Title — subtitle`, centred or left-aligned, 18px |
| **Question line** | italic, muted, 13.5px, directly under the title |
| **Card** | white, no border or a 1px hairline, 4px radius, sits inside a panel |
| **Row** | `chip(date) · title · chip(version)`, 6px vertical padding |
| **Node** | white box with a 1.5px `--hair` border and bold centred text (channels, providers); dashed when "not yet" |
| **Connector** | 1.5px `--wire` line with an arrowhead and an italic label beside it |
| **Callout** | rose tint, bold heading, numbered list |

## 5. Layout (blog index)
- On the blog index, colour is used **only as labels**, not as large panels. Full panels and connectors are kept for diagrams inside posts.
- One narrow column, **580px** wide, with lots of space around it: 112px above the page, 56px between sections and 144px at the bottom.
- Each section starts with a small **tinted label** (`① Essays`, then the muted italic question) in that section's colour.
- Rows are dense: `chip(date) · title · chip(version)`, with 5px padding and no dividers.
- The Ask input uses the violet tint. The agent rules are a single rose note.
- Sections appear in this order: Header → ① Essays → ② Notes → ③ Me → ④ Ask → rose note.

## 6. Motion
- Connectors draw downward (stroke-dashoffset, 600ms) as each panel scrolls into view.
- Panels fade in with a 10px rise over 500ms.
- On hover, a row's title turns `--wire` and an arrow `→` slides in.
- Respect `prefers-reduced-motion`.
