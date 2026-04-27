# Screen: Search Page (Hasil Pencarian)

**File:** `9xuDPzF47hOTP3KuYwbWVT` | **Node:** `7504:3779` → child "Search Page"
**Dimensi:** 360×1618px (scrollable) | **Platform:** iOS (reference)

---

## Anatomi Layar (atas ke bawah)

```
[ Status Bar iOS — 44px ]           ← sticky/fixed
[ Header SearchBox — 56px ]         ← sticky/fixed, state=Filled
[ Filter & Sort Bar — 60px ]        ← sticky/fixed, padding top/bottom 16px, left 8px
  └── Chip filter + sort options (horizontal scroll)
─────────────── scrollable content ──────────────────
[ List Product — grid 2 kolom ]
  └── Product Card Large (162×248) — Type=Default & Type=OOS
      gap horizontal: 12px, gap vertikal: 10px
      padding kiri-kanan: 16px
─────────────── fixed bottom ─────────────────────────
[ .Gimmick bar — 40px ]             ← opsional, hanya saat ada promo aktif
[ Sticky Amount Type=Default — 64px ]
```

---

## Detail Layout

- Total sticky header: **160px** (44px Status Bar + 56px SearchBox + 60px Filter Bar)
- Filter bar: padding **16px top/bottom**, **8px left** — horizontal scroll untuk chip filter
- Product grid: padding **16px** kiri-kanan, gap horizontal **12px**, gap vertikal **10px**
- Sticky Amount (Type=Default): fixed di bottom, **menggantikan** Bottom Nav

---

## Grid Produk

| Property | Value |
|---|---|
| Kolom | 2 kolom |
| Card width | 162px |
| Gap horizontal | 12px |
| Gap vertikal | 10px |
| Padding sides | 16px |
| Card type | Product Card Large |

---

## Komponen DS yang Dipakai

- `Status Bar → iOS`
- `Top Bar → Type=SearchBox` (state=Filled)
- `Alert` component (filter/sort chips area)
- `Product Card Large` (Type=Default, Type=OOS)
- `Sticky Amount` (Type=Default) — dengan .Gimmick opsional

---

## Background & Warna Frame

| Area | Background |
|---|---|
| Page / frame utama | `BackgroundColor/Light` ← WAJIB, bukan abu-abu |
| Product grid area | `BackgroundColor/Light` |
| Filter bar area | `BackgroundColor/Light` |
| Sticky header (Status Bar + SearchBox) | `BackgroundColor/Light` |

> ⚠️ **Jangan biarkan frame background abu-abu** — selalu bind ke variable `BackgroundColor/Light` via `importVariableByKeyAsync`.

---

## Rules Khusus Halaman Ini

- **Background frame utama: `BackgroundColor/Light`** — wajib, bukan default abu-abu Figma
- **Tidak ada Bottom Nav** — digantikan Sticky Amount Type=Default
- Header (Status Bar + SearchBox + Filter Bar) bersifat **sticky** saat scroll
- Sticky Amount bersifat **fixed** di bottom
- Saat produk OOS: tampilkan `Type=OOS` card dengan CTA "Lihat Produk Serupa"
- Filter bar: horizontal scroll — chip-chip filter dan tombol sort
