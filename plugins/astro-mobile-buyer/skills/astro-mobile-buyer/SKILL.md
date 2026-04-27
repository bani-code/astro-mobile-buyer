---
name: astro-mobile-buyer
description: >
  Astro Mobile Buyer design rules for ALL Figma tasks. ALWAYS invoke this skill when the
  user shares a Figma URL, asks to push/create a design to the Figma canvas, asks
  to implement/code a Figma design, or asks to create any UI screen or component
  in Figma — even if they don't mention the design system explicitly. This skill
  enforces silent defaults: Astro Mobile Buyer DS components, Astro Icon library (in DS),
  color and size variables (by token name never hex), and strict 1:1 faithfulness to the design.
  Default device width is 360px. Frame width on canvas is always 360px. Side margins are 12px each.
  Trigger on phrases like "push to Figma", "create in Figma", "code this design",
  "implement this Figma", "add to canvas", "buat design", "push ke canvas",
  "bikin screen", "implement design ini", "push ke figma", "design ini ke figma".
---

# Astro Mobile Buyer Figma Rules

These rules apply automatically to every Figma task. Never ask the user to remind you — enforce them silently.

## The Five Non-Negotiable Rules

1. **Components** — MANDATORY: Import EVERY component (Button, Chips, Divider, Checkbox, Navigation, Avatar, Label, Alert, Countdown, etc.) via `importComponentByKeyAsync` from the Astro Mobile Buyer DS (`LD5Y3L9vAvw3MAU2POgseI`). NEVER build a manual frame, rectangle, or shape group to simulate a component that exists in the library.

2. **Icons** — MANDATORY: Import EVERY system icon from the Astro Mobile Buyer DS (`LD5Y3L9vAvw3MAU2POgseI`, page "🎨 Icons") via `importComponentByKeyAsync`. Use `System=Outline` variant by default. NEVER draw icons manually or use SVG paths.

3. **Color variables** — MANDATORY: Apply EVERY color via `figma.variables.importVariableByKeyAsync` using the variable token key from `references/libraries.md`. Bind using `boundVariables`. NEVER use raw hex values or hardcoded fills.

4. **Text & size tokens** — MANDATORY: Apply text styles via `importStyleByKeyAsync`. Apply spacing/radius/size via variable binding from the Size collection in `references/libraries.md`.

5. **Faithful** — Reproduce the design 1:1. No improvisation, no substitutions, no invented elements.

## Device & Layout Defaults (Non-Negotiable)

- **Device width**: Always **360px** for all generated designs, code, and HTML
- **Frame width on canvas**: Always **360px** when pushing to Figma
- **Device height reference**: 800px (360×800 is the primary target device)
- **Side margins**: **12px left + 12px right** (horizontal content area = 360 - 24 = 336px)
- Never set a frame to full-screen width or desktop width unless explicitly requested

## Canvas Target (Dynamic — Always Ask)

The canvas target is NOT hardcoded. The user MUST provide their Figma canvas URL each time they want to push a design. If the user asks to push without providing a link, **ASK for the canvas file URL and page name before proceeding**.

```js
// Step 1: Ask user for canvas URL if not provided
// Step 2: Extract fileKey and nodeId from the URL
// Step 3: Navigate to the target page
const targetPage = figma.root.children.find(p => p.name === "<page-name-from-user>");
await figma.setCurrentPageAsync(targetPage);
```

## Frame Background — Selalu BackgroundColor/Light

**Setiap frame/page yang di-push ke canvas WAJIB pakai `BackgroundColor/Light` sebagai background** — bukan warna default abu-abu Figma.

```js
// ✅ WAJIB untuk setiap frame utama
const bgVar = await figma.variables.importVariableByKeyAsync('a9ad299d9bb41d9f8c949e558319413b79f717ba') // BackgroundColor/Light
frame.fills = [{ type: 'SOLID', boundVariables: { color: { type: 'VARIABLE_ALIAS', id: bgVar.id } } }]

// ❌ JANGAN — biarkan frame background default (abu-abu Figma)
// frame.fills = [] atau tidak di-set sama sekali
```

## Product Card Grid — Gap Horizontal 12px

Gap horizontal antar product card dalam grid: **12px**.
Gap vertikal antar baris: **10px**.
Gap 8px tetap berlaku untuk komponen lain (chip, badge, icon button, dll).

```js
// ✅ Benar — khusus product card grid
gridFrame.itemSpacing = 12         // gap horizontal antar card
gridFrame.counterAxisSpacing = 10  // gap vertikal antar baris
```

## FORBIDDEN Patterns (will break the rules above)

```js
// ❌ NEVER — manual frame pretending to be a Button
const btn = figma.createFrame();
btn.fills = [{ type: "SOLID", color: { r: 0.12, g: 0.4, b: 0.9 } }];

// ❌ NEVER — raw hex / hardcoded color
node.fills = [{ type: "SOLID", color: { r: 0.1, g: 0.1, b: 0.1 } }];

// ❌ NEVER — creating icon shapes manually
const icon = figma.createVector();

// ❌ NEVER — frame wider than 360px (unless user explicitly requests)
frame.resize(390, 800);

// ❌ NEVER — push to canvas without user providing a link
```

```js
// ✅ ALWAYS — import component from Astro Mobile Buyer DS
const comp = await figma.importComponentByKeyAsync("1bd2b1db1092117b2884daa2ccec75f8fb73419e"); // Button Solid Large
const btn = comp.createInstance();

// ✅ ALWAYS — apply color via variable
const colorVar = await figma.variables.importVariableByKeyAsync("a9ad299d9bb41d9f8c949e558319413b79f717ba"); // BackgroundColor/Light
node.fills = [{ type: "SOLID", boundVariables: { color: { type: "VARIABLE_ALIAS", id: colorVar.id } } }];

// ✅ ALWAYS — frame width is 360
frame.resize(360, 800);
frame.paddingLeft = 12;
frame.paddingRight = 12;
```

## Library Reference

**MANDATORY: Read `references/libraries.md` before starting any Figma task.** It contains all variable keys, text style keys, component keys, and icon keys. You MUST load this file and use the keys from it — do not invent or guess keys.

## Workflow — Push Design to Figma Canvas

### Step 1 — Read the source design
Call `get_design_context` on the Figma URL to get layout, dimensions, screenshot.

### Step 2 — Load all keys from references/libraries.md

### Step 3 — Ask user for canvas target (if not provided)
```
"Please share your Figma canvas URL and page name where you want to push this design."
```
Extract `fileKey` and page name from the provided URL.

### Step 4 — Navigate to canvas page
```js
const targetPage = figma.root.children.find(p => p.name === "<page-name>");
await figma.setCurrentPageAsync(targetPage);
```

### Step 5 — Import colors via variables (NEVER use raw hex)
```js
// Color variable → bind to node fill
const colorVar = await figma.variables.importVariableByKeyAsync("<variable-key>");
node.fills = [{ type: "SOLID", boundVariables: { color: { type: "VARIABLE_ALIAS", id: colorVar.id } } }];

// Text style → importStyleByKeyAsync
const textStyle = await figma.importStyleByKeyAsync("<text-style-key>");
node.textStyleId = textStyle.id;

// Component → importComponentByKeyAsync
const comp = await figma.importComponentByKeyAsync("<component-key>");
const inst = comp.createInstance();
```

### Step 6 — Build frame at 360px matching design exactly
- Frame width: **360px** always
- Padding left/right: **12px** each
- Every color → `importVariableByKeyAsync` by token name
- Every text style → `importStyleByKeyAsync` by token name
- Every button/chip/divider/alert → `importComponentByKeyAsync`
- Every icon → `importComponentByKeyAsync` from DS icons page (use Outline variant)
- Load fonts: `await figma.loadFontAsync({ family: "Nunito Sans", style: "Regular" })`

### Step 7 — Screenshot and verify
Take `get_screenshot` and compare to original. Fix misalignments.

## Workflow — Implement Figma Design to Code

### Step 1 — Get design via `get_design_context`

### Step 2 — Export all image assets (MANDATORY)
Before writing any code, scan and export every image fill, illustration, photo:
- For each image node, call `get_screenshot` with the node ID
- Save to `/assets/images/` with descriptive filename
- System icons → use as components in code, no export needed
- Illustrations → export as .png (still from `tWd29HOmovgLvK5NdqbxB0` illustration library)

```
// Asset export checklist:
// ✅ Photos, product images → export as .png to /assets/images/
// ✅ Custom illustrations → export as .png to /assets/images/
// ✅ Background images → export as .png to /assets/images/
// ✅ System Icons → use <IcName /> component, no export needed
// ❌ NEVER reference images with placeholder URLs
// ❌ NEVER use broken image paths
```

### Step 3 — Map tokens to CSS/JS variables (never hex)
```css
/* ✅ correct — use token variable names */
color: var(--TextColor-PrimaryDark);
background: var(--BackgroundColor-Light);
padding: 0 12px; /* always 12px side margin */
max-width: 360px; /* always 360px device width */

/* ❌ wrong */
color: #1A1A2E;
```

### Step 4 — Use Astro Mobile Buyer DS components in code
### Step 5 — Use system icon components from new DS (`<IcSearch />`, `<IcCart />`, etc.)
### Step 6 — Reference exported assets using local paths
```jsx
// ✅ correct
<img src="/assets/images/banner-promo.png" alt="Promo banner" />

// ❌ wrong
<img src="https://picsum.photos/..." />
```
### Step 7 — Default container: width 360, padding 12 each side
```css
.screen {
  width: 360px;
  padding-left: 12px;
  padding-right: 12px;
  box-sizing: border-box;
}
```
### Step 8 — Match spacing, radius, font size exactly — no improvisation

## Product Images — Gunakan upload_assets (BUKAN createImageAsync)

`figma.createImageAsync()` TIDAK didukung di MCP environment — jangan dipakai.
Gunakan tool `upload_assets` MCP dengan workflow 2 tahap.

### Workflow 2 Tahap

**Tahap 1 — Build frames, return image node IDs:**
```js
// Di Figma script: buat image frame kosong dulu, return nodeId-nya
const imageFrame = figma.createFrame()
imageFrame.resize(cardWidth, cardWidth) // 1:1 square
imageFrame.clipsContent = true
imageFrame.fills = [{ type: 'SOLID', color: { r: 0.93, g: 0.93, b: 0.93 } }]
// WAJIB return nodeId untuk dipakai di tahap 2
return { imageNodeIds: ['1:23', '1:45', '1:67', ...] }
```

**Tahap 2 — Upload image ke tiap node via `upload_assets` MCP:**
```
Untuk tiap imageNodeId + imageUrl dari sample data:
→ call upload_assets(fileKey, nodeId=imageNodeId, scaleMode='FILL')
→ download image bytes dari image.astronauts.cloud
→ POST ke upload URL yang dikembalikan
→ image langsung masuk sebagai fill ke node tersebut
```

### Sample Data Produk

Data lengkap 6 produk ada di `references/sample-data.md`. Gunakan nama, harga, dan imageUrl dari sana.
- CDN: `image.astronauts.cloud` (production)
- Semua produk punya diskon — tampilkan harga coret + label diskon %
- Rotate siklus: `products[i % products.length]`

**Rules:**
- JANGAN pakai `createImageAsync` — tidak didukung MCP
- SELALU return image node IDs dari Figma script tahap 1
- SELALU upload image setelah frames dibuat (tahap 2)
- Image frame wajib `clipsContent = true`
- Gunakan nama & harga asli — bukan "Product Name" atau "Rp0"

## Quick Token Cheatsheet

| Token | Variable Name | Use for |
|---|---|---|
| `TextColor/PrimaryDark` | Main body text | Dark text on light bg |
| `TextColor/SecondaryDark` | Secondary text | Subtitles, hints |
| `TextColor/PrimaryLight` | Text on dark bg | White text |
| `TextColor/Placeholder` | Input placeholder | Gray placeholder |
| `TextColor/Link` | Links | Clickable text |
| `TextColor/Error` | Error messages | Form errors |
| `TextColor/Success` | Success messages | Confirmations |
| `BackgroundColor/Light` | White/card bg | Page & card background |
| `BackgroundColor/Primary` | Primary brand color | Primary bg |
| `BackgroundColor/LightPrimary` | Light primary tint | Soft accent bg |
| `BackgroundColor/LightGrey` | Grey bg | Section separator |
| `StrokeColor/Default` | Default borders | Card outlines |
| `StrokeColor/Active` | Active/focused border | Active input |
| `StrokeColor/Error` | Error border | Invalid input |
| `IconColor/Default` | Default icons | Standard icon color |
| `IconColor/Primary` | Primary icons | Brand-colored icons |

Full keys → `references/libraries.md`
