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

## Frame / Page Corner Radius — Selalu 16px

Setiap frame atau page design yang di-push ke canvas Figma **WAJIB** diberi corner radius 16px.

```js
// ✅ WAJIB — set setelah frame dibuat
frame.cornerRadius = 16

// Jika tiap sudut berbeda (jarang):
frame.topLeftRadius = 16
frame.topRightRadius = 16
frame.bottomLeftRadius = 16
frame.bottomRightRadius = 16
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

### Step 2 — Export all image assets + resolve all icons (MANDATORY)

**Lakukan ini sebelum menulis satu baris kode pun.**

**2A — Images (photos, illustrations, backgrounds):**
- Untuk setiap image fill node: call `get_screenshot(nodeId)` → save ke `/assets/images/{nama}.png`
- ❌ FORBIDDEN: pakai URL `localhost:` apapun di output code

**2B — Icons (WAJIB `get_metadata` per icon node):**
- Kumpulkan semua node ID yang merupakan icon (nama mengandung prefix `ic`)
- Call `get_metadata(nodeId)` untuk **setiap** icon node — jangan skip
- Baca `componentProperties.System.value` → `"Outline"` atau `"Filled"`
- Map ke file lokal: `icons/outline/icName.svg` atau `icons/filled/icName-filled.svg`
- ❌ FORBIDDEN: nebak variant dari visual atau default rule tanpa `get_metadata`
- ❌ FORBIDDEN: pakai URL `localhost:` untuk icon

```
// Checklist sebelum nulis kode:
// ✅ Semua image → get_screenshot → /assets/images/
// ✅ Semua icon → get_metadata → baca System variant → icons/outline/ atau icons/filled/
// ✅ Semua icon → gunakan file lokal, bukan localhost URL
// ❌ NEVER pakai localhost: URL di output code (image maupun icon)
// ❌ NEVER nebak variant icon tanpa get_metadata
// ❌ NEVER placeholder URL
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

---

## Workflow — Update Existing Screen

Untuk memodifikasi frame/screen yang **sudah ada** di canvas Figma — tanpa rebuild dari awal.

**Trigger phrases:** "update screen ini", "tambah section ke", "ganti komponen di", "ubah warna di", "revisi design ini", "tambahkan ke frame yang sudah ada"

### Kapan dipakai
- Tambah section/komponen baru ke screen yang sudah ada
- Swap komponen atau variant (misal ganti Button state, ubah icon)
- Update teks, warna, atau spacing di node tertentu
- Tambah/hapus item dari list

### Step 1 — Minta URL + deskripsi perubahan
Jika user belum provide, tanyakan:
```
"Share Figma URL screen yang mau diupdate, dan jelaskan perubahan apa yang diinginkan."
```
Extract `fileKey` dan `nodeId` dari URL.

### Step 2 — Inspect kondisi saat ini (WAJIB sebelum modify apapun)
```js
// Lihat kondisi visual dulu
get_screenshot(nodeId)

// Baca struktur: child nodes, hierarchy, IDs, properties
get_metadata(nodeId)
```
Pahami betul struktur yang ada sebelum menyentuh apapun. **Jangan skip step ini.**

### Step 3 — Navigasi ke page yang benar
```js
const targetPage = figma.root.children.find(p => p.name === "<page-name>");
await figma.setCurrentPageAsync(targetPage);
```

### Step 4 — Load keys yang dibutuhkan dari libraries.md
Hanya load keys yang relevan dengan perubahan yang akan dilakukan — component keys, variable keys, text style keys.

### Step 5 — Lakukan perubahan secara atomic (satu per satu)
```js
// ✅ Satu use_figma call = satu perubahan
// Verifikasi setelah tiap step sebelum lanjut ke step berikutnya

// Contoh: tambah komponen baru ke existing frame
const frame = await figma.getNodeByIdAsync("<existing-frame-id>")
const comp = await figma.importComponentByKeyAsync("<component-key>")
const inst = comp.createInstance()
frame.appendChild(inst)

// WAJIB return semua node ID yang dimodifikasi
return { mutatedNodeIds: [frame.id], createdNodeIds: [inst.id] }
```

**Rules saat modify:**
- **Surgical** — ubah hanya node yang perlu, jangan sentuh sisanya
- **Satu perubahan per call** — jangan batch semua perubahan dalam satu script besar
- **Return semua mutated + created node IDs** — wajib di setiap call
- ❌ JANGAN pakai hardcoded hex — tetap gunakan `importVariableByKeyAsync`
- ❌ JANGAN rebuild frame yang tidak perlu diubah

### Step 6 — Verifikasi hasil
```js
get_screenshot(nodeId) // bandingkan dengan kondisi awal dari Step 2
get_metadata(nodeId)   // pastikan struktur sesuai ekspektasi
```

### Step 7 — Fix jika ada issue
Jika screenshot tidak sesuai, tulis **targeted fix script** — hanya perbaiki bagian yang salah, jangan recreate ulang semua.

### Strategi kunci
| Prinsip | Penjelasan |
|---|---|
| Inspect before touch | `get_metadata` dulu sebelum modify apapun |
| Atomic changes | Satu perubahan per `use_figma` call |
| Verify each step | `get_screenshot` setelah setiap perubahan signifikan |
| Return all IDs | Semua created/mutated node IDs wajib di-return |
| Non-destructive | Jika ragu, tambah node baru — jangan overwrite yang lama |

---

## Image Assets — WAJIB Download Sebelum Dipakai di Code

**ANY URL yang mengandung `localhost:` adalah URL sementara Figma MCP — DILARANG dipakai di output code.** URL ini hanya aktif selama sesi MCP berlangsung dan akan broken begitu sesi tutup.

```
// ❌ FORBIDDEN — URL sementara, akan broken
<img src="http://localhost:3845/assets/abc123.png" />

// ✅ WAJIB — path lokal setelah download
<img src="/assets/images/banner-promo.png" />
```

### Workflow Wajib (sebelum nulis kode apapun)

1. Scan semua image fill di design via `get_design_context`
2. Untuk setiap image node: call `get_screenshot(nodeId)` → save ke `/assets/images/{nama-deskriptif}.png`
3. Gunakan path lokal di kode: `<img src="/assets/images/nama-deskriptif.png" />`
4. **JANGAN tulis kode dulu sebelum semua image sudah di-download ke lokal**

```
// Asset export checklist (WAJIB sebelum kode):
// ✅ Photos, product images → get_screenshot → /assets/images/
// ✅ Custom illustrations → get_screenshot → /assets/images/
// ✅ Background images → get_screenshot → /assets/images/
// ✅ System Icons → gunakan file dari icons/ directory (lihat Icon Resolution di bawah)
// ❌ NEVER pakai localhost: URL di output code
// ❌ NEVER pakai placeholder URL (picsum, via.placeholder, dll)
```

---

## Icon Resolution — Wajib Cross-check ke DS Icons (untuk Code)

Saat implement design ke code, setiap icon **WAJIB** di-resolve ke file lokal di `icons/` — **bukan** dari URL localhost atau raw SVG export dari Figma MCP.

### Workflow Wajib

> ⚠️ **JANGAN nebak variant dari visual atau default rule.** `get_design_context` TIDAK mengembalikan `componentProperties` — jadi variant Outline/Filled tidak bisa dibaca dari sana. WAJIB call `get_metadata` untuk setiap icon node.

1. Dari `get_design_context`, catat semua node yang namanya mengandung prefix `ic` atau terlihat seperti icon — **catat node ID-nya**
2. Untuk setiap icon node ID, **wajib call `get_metadata(nodeId)`**
3. Dari hasil `get_metadata`, baca `componentProperties` → cari property `System`:
   ```
   componentProperties.System.value === "Outline" → icons/outline/icName.svg
   componentProperties.System.value === "Filled"  → icons/filled/icName-filled.svg
   ```
4. Gunakan file lokal tersebut di kode — **bukan URL localhost, bukan inline SVG**

```
// Contoh output get_metadata yang benar:
{
  "name": "icChevronRightCircle",
  "componentProperties": {
    "System": { "value": "Filled", "type": "VARIANT" }
  }
}
// → gunakan: icons/filled/icChevronRightCircle-filled.svg
```

### Naming Convention

| Variant | Pattern | Contoh |
|---|---|---|
| Outline (default) | `icons/outline/{icName}.svg` | `icons/outline/icSearch.svg` |
| Filled | `icons/filled/{icName}-filled.svg` | `icons/filled/icCart-filled.svg` |

### Contoh Resolusi

| Node Figma | Variant | File yang dipakai |
|---|---|---|
| `icChevronRightCircle` | Outline | `icons/outline/icChevronRightCircle.svg` |
| `icCart` | Filled | `icons/filled/icCart-filled.svg` |
| `icSearch` | Outline | `icons/outline/icSearch.svg` |
| `icHome` | Outline | `icons/outline/icHome.svg` |
| `icDiscount` | Outline | `icons/outline/icDiscount.svg` |

```jsx
// ❌ FORBIDDEN — raw export dari Figma MCP server
<img src="http://localhost:3845/.../icChevron.svg" />

// ❌ FORBIDDEN — inline SVG dari raw Figma export
<svg xmlns="http://www.w3.org/2000/svg" viewBox="..."><path d="..."/></svg>

// ✅ WAJIB — file lokal dari DS icons directory
<img src="icons/outline/icChevronRightCircle.svg" alt="chevron" />

// ✅ atau sebagai komponen jika sudah di-setup
<IcChevronRightCircle />
```

> **Total icons tersedia:** 318 outline + 312 filled = 630 SVG files di `icons/` directory.
> Jika nama icon tidak ditemukan di `icons/`, cek ejaan dari node name di Figma — nama file identik dengan nama node DS.

---

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

---

## Workflow — Figma Design Review

Audit screen Figma secara sistematis terhadap Astro Mobile Buyer DS rules. Output: checklist report per node.

**Trigger phrases:** "review design ini", "audit figma screen", "cek design sudah sesuai DS?", "apakah design ini benar?"

### Step 1 — Minta Figma URL
Jika belum ada, tanyakan:
```
"Share Figma URL screen yang mau di-review."
```

### Step 2 — Inspect design
```
get_design_context(url)   → baca full layout & node tree
get_screenshot(frameId)   → lihat kondisi visual keseluruhan
get_metadata(frameId)     → inspect properties level node (fills, sizes, bindings)
```

### Step 3 — Cek per kategori

**Layout**
- Frame width = 360px?
- Side margin = 12px kiri & kanan?
- Corner radius = 16px untuk frame/page design?

**Color & Background**
- Semua fills pakai `boundVariables` ke token? Tidak ada hardcoded hex?
- Background frame = `BackgroundColor/Light` (bukan default abu-abu Figma)?

**Components**
- Semua komponen (Button, Chip, Alert, Divider, dll) diimport dari DS `LD5Y3L9vAvw3MAU2POgseI`?
- Tidak ada manual frame/rectangle yang mensimulasikan komponen DS?

**Icons**
- Untuk setiap icon node: `get_metadata(iconNodeId)` → baca `componentProperties.System.value`
- Pastikan variant Outline/Filled sesuai dengan intent design
- Icon dari DS, bukan drawn manually

**Spacing**
- Gap horizontal product card = 12px?
- Divider antar section = 8px?
- Jarak antar section/widget = 16px?

**Screen-specific rules**
- CheckoutBar + Navigation pattern sesuai tipe halaman? (Cart = keduanya visible; Search/PDP = CheckoutBar menggantikan Nav)
- Bottom Nav hanya muncul di 5 halaman utama: Home, Kategori, Keranjang, Order, Profile?
- Header type sesuai? (Title 48px vs SearchBox 56px)

### Step 4 — Output report
```
Format tiap item:
✅ PASS  [Kategori] — [deskripsi] — node: [name / ID]
❌ FAIL  [Kategori] — [masalah] — node: [name / ID] — Fix: [rekomendasi]
⚠️ WARN  [Kategori] — [perlu konfirmasi] — node: [name / ID]

Contoh:
✅ PASS  Layout — frame width 360px ✓
❌ FAIL  Color — Button fill hardcoded #0066CC — node: "btn-checkout" — Fix: bind ke BackgroundColor/Primary variable
⚠️ WARN  Icon — icCart variant tidak terbaca dari get_design_context, perlu get_metadata konfirmasi
❌ FAIL  Background — frame default abu-abu — Fix: importVariableByKeyAsync BackgroundColor/Light
```

Tutup report dengan **Summary**: total PASS / FAIL / WARN + prioritas fix.

---

## Workflow — Code UI Review

Audit implementasi code/HTML terhadap Astro Mobile Buyer DS rules. Untuk developer atau PM yang vibe-code dari clone GitHub.

**Trigger phrases:** "review code ini", "cek UI implementasi", "apakah code sudah sesuai DS?", "review UI dari file ini"

### Step 1 — Minta path file atau folder
Jika belum ada, tanyakan:
```
"Share path file atau folder yang mau di-review (bisa satu file atau seluruh folder screen)."
```

### Step 2 — Read files
```
Read(filePath) untuk setiap file yang relevan
Pahami: struktur komponen, styling approach, routing, conditional rendering
```

### Step 3 — Cek per kategori

**Color & Token**
- Warna pakai `var(--token-name)` atau CSS variable → ✅
- Warna hardcoded hex (`#1A1A2E`, `rgba(...)`) → ❌ FAIL
- Background pakai `var(--BackgroundColor-Light)` → ✅

**Typography**
- Font family: Nunito Sans?
- Text style mengacu ke token DS, bukan hardcode `font-size: 14px`?

**Layout & Spacing**
- `max-width: 360px` atau `width: 360px`?
- Side padding `12px` kiri & kanan?
- Gap product card horizontal `12px`?
- Section spacing `16px`?

**Components**
- Menggunakan DS components (Button, Chip, Alert, dll) atau manual `<div>` dengan styling custom?
- Setiap simulasi komponen DS dengan manual element → ❌ FAIL

**Icons**
- Icon diambil dari `icons/outline/icName.svg` atau `icons/filled/icName-filled.svg`?
- Bukan inline SVG dari Figma export atau URL localhost?
- Nama file sesuai konvensi: `icName.svg` (outline) / `icName-filled.svg` (filled)?

**Pattern**
- CheckoutBar hanya muncul di halaman yang benar?
- Bottom Nav hanya di 5 halaman utama?
- Tidak ada `localhost:` URL di src image atau icon?

### Step 4 — Output report
```
✅ PASS  Color — background pakai var(--BackgroundColor-Light) ✓
❌ FAIL  [Button] manual <div class="btn"> dengan #0066CC — seharusnya DS Button component
⚠️ WARN  [Icon] icChevronRight pakai inline SVG — seharusnya icons/outline/icChevronRight.svg
❌ FAIL  Side margin 16px — seharusnya 12px
✅ PASS  Layout — max-width 360px ✓
```

Tutup dengan **Summary**: total PASS / FAIL / WARN + file & line number yang bermasalah.

---

## Workflow — UX Flow Review

Review kelengkapan dan kebenaran experience dari sebuah user flow. Input bisa code/HTML atau Figma URL.

**Trigger phrases:** "review UX flow ini", "cek user journey", "ada UX yang missing?", "apakah UX-nya sudah lengkap?"

### Step 1 — Tentukan input type & minta file/URL
```
Code/HTML → Read files → parse screens, routing, conditional rendering
Figma URL → get_design_context + get_screenshot per screen
```

### Step 2 — Map user flow yang ada
Identifikasi:
- Screen apa saja yang ada?
- Transisi antar screen (user bisa ke mana dari sini?)
- Entry point dan exit point dari flow

### Step 3 — Cek per kategori

**State Coverage**
- Loading state tersedia di setiap async operation?
- Empty state tersedia (cart kosong, hasil search kosong, dll)?
- Error state tersedia dengan pesan yang jelas dan actionable?
- Success state tersedia dengan feedback yang jelas?

**Flow Gaps**
- Ada screen/step yang hilang dari journey?
- User bisa stuck di tengah flow tanpa jalan keluar?
- Dead end screen (tidak ada back / next action)?

**Edge Cases**
- Produk OOS (Out of Stock) ter-handle?
- Kondisi jaringan buruk / timeout ter-handle?
- Input tidak valid ter-handle dengan pesan error?

**Feedback & Komunikasi**
- User mendapat feedback setelah setiap action penting? (add to cart, checkout, dll)
- Toast / snackbar / notifikasi tersedia?
- CTA label jelas dan tidak ambigu?

**Navigation**
- Back navigation logic benar di setiap screen?
- User tidak bisa tersesat (lost in flow)?
- Deep link / direct URL ter-handle?

**Astro-specific Patterns**
- Entry point ke Cart sudah benar?
- Search → PDP → Cart → Checkout flow lengkap?
- PWP (Purchase With Purchase) flow ter-cover jika relevan?
- Promo/voucher flow ter-cover jika relevan?

### Step 3b — Buyer Lens (WAJIB jika fitur adalah buyer-facing)

Load `knowledge/buyer-personas.md`. Identifikasi persona target dari PRD atau konteks. Evaluasi flow dari sudut pandang persona tersebut:

**Pertanyaan per persona:**
- Apakah jumlah step sudah sesuai dengan patience level persona ini? (New Parent SOS → harus minimal; Impulse Snacker → harus satu tap; Family Feeder → boleh lebih panjang asal terasa lengkap)
- Apakah empty state / error message sudah bicara dalam bahasa yang resonan dengan persona ini?
- Apakah ada momen di flow ini yang akan membuat persona ini drop off?
- Apakah visual hierarchy membantu persona ini menemukan apa yang mereka butuhkan dengan cepat?

**Output tambahan:**
```
👤 BUYER LENS — [nama persona]
✅ SERVES    Flow checkout minimal — sesuai untuk SOS persona
❌ FRICTION  OOS state tidak kasih alternatif produk — Family Feeder akan frustrated
⚠️ RISK      Empty cart state terlalu "cold" — Impulse Snacker butuh curated suggestion
```

Jika tidak ada PRD dan persona tidak jelas, gunakan **Family Feeder** sebagai default (24% users, 30% GMV).

### Step 4 — Output report
```
✅ COVERED  Success state Checkout sudah ada
❌ MISSING  State OOS (produk habis) belum ada di screen PDP
❌ MISSING  Empty state Cart belum di-handle
⚠️ GAP      Add to cart tidak ada feedback ke user (toast/notifikasi)
⚠️ GAP      Back dari Checkout ke Cart tidak ada CTA yang clear
✅ COVERED  Error state network sudah ter-handle

👤 BUYER LENS — [persona]
✅ SERVES    ...
❌ FRICTION  ...
⚠️ RISK      ...
```

Tutup dengan **Summary**: total COVERED / MISSING / GAP + BUYER LENS findings + rekomendasi prioritas fix.

---

## Workflow — Full Review (Code UI Review + UX Flow Review)

Menjalankan Code UI Review dan UX Flow Review sekaligus. Output satu report dengan dua section.

**Trigger phrases:** "full review", "review lengkap", "cek UI dan UX sekalian", "review semua"
**Input:** Code / HTML files

### Steps
```
Step 1 — Jalankan Code UI Review → hasilkan UI Report
Step 2 — Jalankan UX Flow Review → hasilkan UX Report
Step 3 — Gabungkan output
```

### Output format
```
════════════════════════════════
  SECTION 1: UI DS Compliance
════════════════════════════════
✅ PASS  ...
❌ FAIL  ...
⚠️ WARN  ...

════════════════════════════════
  SECTION 2: UX Flow
════════════════════════════════
✅ COVERED  ...
❌ MISSING  ...
⚠️ GAP      ...

════════════════════════════════
  SUMMARY
════════════════════════════════
UI  : X FAIL, X WARN, X PASS
UX  : X MISSING, X GAP, X COVERED

🔴 Critical (fix sekarang):
  - [item paling blocking]

🟡 Important (fix sebelum launch):
  - [item penting tapi tidak blocking]

🟢 Nice to have:
  - [item yang bisa diimprove]
```

---

## Workflow — PRD to UX Spec

Translate sebuah PRD atau deskripsi fitur menjadi UX specification lengkap: screen flow, state map, copy table, edge cases.

**Trigger phrases:** "buatkan UX spec dari PRD ini", "translate PRD ke UX", "generate UX spec", "uraikan flow dari PRD ini", "bikin screen flow dari PRD ini", "breakdown UX-nya"

### Step 1 — Gather Input

Baca PRD yang diberikan (file path atau paste di chat). Jika tidak ada PRD, minta deskripsi fitur minimal:
- Apa yang bisa dilakukan user?
- Siapa user-nya (buyer / mitra)?
- Apa goal utama dari fitur ini?

Juga load:
- `knowledge/astro-context.md` — terminologi dan konteks bisnis
- `knowledge/buyer-personas.md` — identifikasi persona yang relevan
- `references/platform-rules.md` — rules mobile (navigation, header type, dll)
- `references/screens.md` — peta semua screen yang ada (iOS source of truth)
- `references/production-copy.md` — copy aktual production untuk reference copy table

### Step 2 — Identifikasi Persona Target

Dari PRD atau konteks, tentukan:
- Ini untuk buyer, mitra, atau internal?
- Jika buyer: persona mana yang paling relevan? (refer ke `knowledge/buyer-personas.md`)
- Jika tidak jelas: default ke **Family Feeder**

### Step 3 — Hasilkan UX Specification

Structure output:

**1. User Flow Overview**
Narasi singkat end-to-end journey — dari trigger awal sampai success state.

**2. Screen / State Map (ASCII)**
```
[Entry Point]
    ↓
[Screen A: nama]
    ├─ tap CTA → [Screen B]
    ├─ error → [Error State A]
    └─ back → [Previous Screen]
[Screen B: nama]
    ├─ success → [Success State]
    └─ OOS → [OOS State]
```

**3. Screen Specifications** — per screen:
- **Default state** — konten dan layout saat normal
- **Loading state** — feedback saat async operation
- **Empty state** — saat tidak ada data (explain + next action)
- **Error state(s)** — per jenis error (network, validation, OOS)
- **Success state** — konfirmasi setelah action berhasil

**4. Copy & Microcopy Table**
| Screen | Element | Copy (BI/EN) | Notes |
|--------|---------|-------------|-------|
| Cart | Empty state headline | "Keranjangmu kosong" | Bahasa Indonesia |
| Cart | Empty state CTA | "Mulai Belanja" | |
| Checkout | Error payment | "Pembayaran gagal. Coba metode lain." | Spesifik + actionable |

**5. Edge Cases & Error Handling**
| Skenario | System Response |
|----------|----------------|
| Produk OOS saat checkout | Show alternatif produk serupa |
| Jaringan putus | Offline state dengan retry CTA |
| Session timeout | Redirect ke login + preserve cart |

**6. Open UX Questions**
List pertanyaan yang belum terjawab di PRD dan perlu konfirmasi PM / stakeholder.

### Step 4 — Buyer Lens Check

Evaluasi spec dari sudut pandang persona target:
- Apakah jumlah screen dan step masuk akal untuk persona ini?
- Apakah copy sudah resonan (tone, bahasa, urgency level)?
- Apakah ada step yang akan membuat persona ini frustrated atau berhenti?

### Step 5 — Save

Simpan ke file jika diminta: `[nama-fitur]-ux-spec.md`
Laporkan Open UX Questions yang perlu input.

---

## Workflow — Brand Voice Check

Cek apakah copy di design (banner, empty state, error message, button label, CTA) sudah sesuai brand voice Astro.

**Trigger phrases:** "cek copy ini sudah sesuai brand belum", "review tone of voice", "apakah copy ini on-brand?", "brand voice check", "cek bahasa di design ini"

### Step 1 — Load brand context
Baca `knowledge/brand-voice.md`.

### Step 2 — Kumpulkan semua copy
Dari Figma URL (`get_design_context`) atau dari paste langsung di chat.
Kumpulkan semua user-facing string: headline, subheadline, body, CTA, label, error message, empty state.

### Step 3 — Evaluasi per copy

Untuk setiap string, cek:
- **Bahasa benar?** (BI untuk buyer/mitra, EN untuk internal/admin)
- **Tone sesuai?** (hangat, direct, tidak kaku, tidak alay)
- **Panjang sesuai?** (banner headline max 20 karakter)
- **Actionable?** (error message spesifik + ada next step)
- **Button label action verb?** (bukan "OK" atau "Ya")
- **Empty state ada penjelasan + CTA?**
- **Confirmation dialog spesifik?** (bukan "Apakah kamu yakin?")

### Step 4 — Output report
```
✅ ON-BRAND   Banner: "Promo Tanggal Tua" — benefit-first, BI ✓
❌ OFF-BRAND  Error: "Terjadi kesalahan" — tidak spesifik, tidak actionable
              Fix: "Pembayaran gagal. Coba lagi atau gunakan metode lain."
⚠️ REVIEW    CTA: "OK" — ganti dengan action verb seperti "Mengerti" atau "Lanjutkan"
❌ OFF-BRAND  Empty state: "Data tidak tersedia" — tidak ada penjelasan + tidak ada next action
              Fix: "Belum ada pesanan. Mulai belanja dan pesan pertamamu!"
```

Tutup dengan **Summary**: total ON-BRAND / OFF-BRAND / REVIEW + prioritas fix.

---

## Knowledge Files — Cara Pakai

Skill ini punya 3 knowledge file yang bisa dipanggil kapan saja:

| File | Isi | Trigger |
|------|-----|---------|
| `knowledge/buyer-personas.md` | 20 buyer personas, data real | *"review dari perspektif buyer"*, *"persona mana yang pakai fitur ini?"*, *"apakah ini cocok untuk [persona]?"* |
| `knowledge/brand-voice.md` | Brand voice, copy rules, tone BI/EN, button labels, status labels, logo rules | *"apakah copy ini on-brand?"*, *"apa bahasa yang tepat untuk ini?"*, *"brand voice check"* |
| `knowledge/astro-context.md` | Company context, terminologi PRD, order flow, stakeholders, leadership | *"apa artinya [term]?"*, *"ini buat siapa?"*, *"jelaskan konteks bisnis"* |
| `references/screens.md` | Peta lengkap semua screen Astro Buyer dari iOS source of truth — tab bar, full screen, bottom sheets | *"screen apa saja yang ada?"*, *"dari mana bisa ke screen ini?"*, *"navigation flow-nya gimana?"* |
| `references/production-copy.md` | Semua copy production aktual dalam BI — error states, empty states, button labels, cart, promo | *"copy yang dipakai di app untuk ini apa?"*, *"gimana nulis error message yang sesuai?"* |
| `references/design-tokens-ios.md` | Token system iOS (UniverseUI) — color scales, semantic tokens, component list, feature flags | *"token ini padanannya apa di Figma?"*, *"hex berapa primary color-nya?"* |

---

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
