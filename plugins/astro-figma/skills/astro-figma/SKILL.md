---
name: astro-figma
description: >
  AstroSystem design rules for ALL Figma tasks. ALWAYS invoke this skill when the
  user shares a Figma URL, asks to push/create a design to the Figma canvas, asks
  to implement/code a Figma design, or asks to create any UI screen or component
  in Figma — even if they don't mention the design system explicitly. This skill
  enforces silent defaults: AstroSystem components, Astro Icon library, AstroSystem
  style tokens (by token name never hex), and strict 1:1 faithfulness to the design.
  Trigger on phrases like "push to Figma", "create in Figma", "code this design",
  "implement this Figma", "add to canvas", "buat design", "push ke canvas",
  "bikin screen", "implement design ini", "push ke figma", "design ini ke figma".
---

# AstroSystem Figma Rules

These rules apply automatically to every Figma task. Never ask the user to remind you — enforce them silently.

## The Four Non-Negotiable Rules

1. **Components** — MANDATORY: Import EVERY AstroSystem component (Button, Chips, Divider, TextField, Checkbox, Navigation, Avatar, Badges, Toggle, Search, Label, Icon Button, FAB, Counter, etc.) via `importComponentByKeyAsync`. NEVER build a manual frame, rectangle, or shape group to simulate a component that exists in the library. If the key is not in `references/libraries.md`, search for it in Figma first.

2. **Icons** — MANDATORY: Import EVERY icon from the Astro Icon library (`tWd29HOmovgLvK5NdqbxB0`) via `importComponentByKeyAsync`. NEVER draw icons manually, use SVG paths, or copy icon shapes. If the icon key is not listed, use the search snippet in `references/libraries.md` to find it.

3. **Style tokens** — MANDATORY: Apply EVERY color, text, and effect style via `importStyleByKeyAsync` using the token name from `references/libraries.md`. Set `node.fillStyleId`, `node.textStyleId`, `node.strokeStyleId`, or `node.effectStyleId`. NEVER use raw hex values, NEVER use hardcoded colors in fills arrays, NEVER set `fills: [{ type: "SOLID", color: { r, g, b } }]` for any styled element.

4. **Faithful** — Reproduce the design 1:1. No improvisation, no substitutions, no invented elements.

## FORBIDDEN Patterns (will break the rules above)

```js
// ❌ NEVER — manual frame pretending to be a Button
const btn = figma.createFrame();
btn.fills = [{ type: "SOLID", color: { r: 0.12, g: 0.4, b: 0.9 } }];

// ❌ NEVER — raw hex / hardcoded color
node.fills = [{ type: "SOLID", color: { r: 0.1, g: 0.1, b: 0.1 } }];

// ❌ NEVER — creating icon shapes manually
const icon = figma.createVector();
```

```js
// ✅ ALWAYS — import component from library
const comp = await figma.importComponentByKeyAsync("2015aad25bead31342fb8f232d4ca82a2941058f");
const btn = comp.createInstance();

// ✅ ALWAYS — import style by token name
const style = await figma.importStyleByKeyAsync("b24cd4dbb129bee6e9bf08efb8acccc49d59ee7d"); // textColor/link
node.fillStyleId = style.id;
```

## Library Reference

**MANDATORY: Read `references/libraries.md` before starting any Figma task.** It contains all style keys, component keys, and icon keys. You MUST load this file and use the keys from it — do not invent or guess keys.

## Workflow — Push Design to Figma Canvas

### Step 1 — Read the source design
Call `get_design_context` on the Figma URL to get layout, dimensions, screenshot.

### Step 2 — Load all keys from references/libraries.md

### Step 3 — Switch to the target canvas page
```js
const targetPage = figma.root.children.find(p => p.id === "76:3098");
await figma.setCurrentPageAsync(targetPage);
```
Target file: `n5K0Da0g4Z8nbpPMN0zjbh` | Page: `76:3098` ("Claude to Figma")

### Step 4 — Import styles and components (NEVER use raw hex)
```js
// Import style → assign to styleId property
const style = await figma.importStyleByKeyAsync("<key>");
node.fillStyleId   = style.id;  // background or text color
node.textStyleId   = style.id;  // text style
node.strokeStyleId = style.id;  // border
node.effectStyleId = style.id;  // shadow

// Import AstroSystem component or Astro Icon
const comp = await figma.importComponentByKeyAsync("<key>");
const inst = comp.createInstance();
```

### Step 5 — Build frame matching design exactly
- Dimensions, spacing, and positions must match the design pixel-perfectly
- Every color → `importStyleByKeyAsync` by token name
- Every text style → `importStyleByKeyAsync` by token name
- Every button/chip/divider → `importComponentByKeyAsync`
- Every icon → `importComponentByKeyAsync` from Astro Icon library
- Load fonts: `await figma.loadFontAsync({ family: "Nunito Sans", style: "Regular" })`

### Step 6 — Screenshot and verify
Take `get_screenshot` and compare to original. Fix misalignments.

## Workflow — Implement Figma Design to Code

### Step 1 — Get design via `get_design_context`

### Step 2 — Map tokens to CSS variables (never hex)
```css
/* ✅ correct */
color: var(--textColor-primaryDark);
background: var(--bgColor-light);

/* ❌ wrong */
color: #1A1A2E;
```

### Step 3 — Use AstroSystem components in code (Button, Chips, etc.)
### Step 4 — Use Astro Icon components (`<IcHub />`, `<IcTime />`, etc.)
### Step 5 — Match spacing, radius, font size exactly — no improvisation

## Quick Token Cheatsheet

| Token | Use for |
|---|---|
| `textColor/primaryDark` | Main body text |
| `textColor/secondaryDark` | Subtitles, secondary text |
| `textColor/primaryLight` | Text on dark/primary bg |
| `textColor/placeholder` | Input placeholder |
| `textColor/link` | Links |
| `bgColor/light` | White/card bg |
| `bgColor/primary` | Primary blue |
| `bgColor/vlightPrimary` | Light blue page bg |
| `strokeColor/default` | Default borders |
| `display/tiny` | Large titles |
| `headline/small` | Section headings |
| `body/default` | Body copy (16px) |
| `paragraph/small` | Compact body (14px) |
| `caption/small` | Fine print (12px) |

Full keys → `references/libraries.md`
