# Screen: Homepage

**File:** `9xuDPzF47hOTP3KuYwbWVT` | **Node:** `7504:3779` → child "Homepage"
**Dimensi:** 360×5087px (scrollable) | **Platform:** iOS (reference)

---

## Anatomi Layar (atas ke bawah)

```
[ Status Bar iOS — 44px ]
[ Custom Header — address + action buttons ]  ← BUKAN Top Bar standar
[ Balance / Astro Koin bar — 42px ]
[ Hero Banner — 180px, full width ]
─────────────────── scroll content ───────────────────
[ Section: Spesial di Astro ]        ← tanpa "Lihat Semua"
[ Second Banner — horizontal scroll ]
[ Astro Milestone Widget ]
[ Section: Brand Pilihan ]
[ Section: Kebutuhan Dapur ]
[ Section: Feeding Essentials ]
[ Section: Body, Skin & Face Care ]
[ Product Carousel — horizontal scroll ]
[ Catalog Vertical / Super Special Banner ]
[ Section: Flash Sale ]
[ Banner Section ]
[ Section: Product Category ]
[ Kombo Hemat Widget ]
[ Section: All Products — grid 2 kolom ]
─────────────────── fixed bottom ─────────────────────
[ Bottom Navigation — 52px ] (Active=Home)
[ Home Indicator iOS — 34px ]
```

---

## Header Custom (bukan Top Bar standar)

- Tidak memakai komponen `Top Bar` dari DS
- Berisi: info alamat pengiriman + action button (Chat CS, icon lainnya)
- Height: bagian dari "Head Content" (total 352px termasuk hero banner)
- Background: gradient/image (bukan flat color)

---

## Spacing & Layout

- Gap antar section/widget: **16px** (standar semua halaman)
- Padding konten kiri-kanan: **16px** (semua section)
- Padding top product grid: **0px** (langsung dari section sebelumnya)
- Product grid gap antar card: **8px** horizontal, **10px** vertikal

---

## Section Details

| Section | Tipe | Kolom/Layout | Catatan |
|---|---|---|---|
| Spesial di Astro | Banner list | VERTICAL, gap=8 | Tanpa "Lihat Semua" |
| Second Banner | Horizontal scroll | gap=8 | Full bleed (tidak ada side margin) |
| Astro Milestone Widget | Custom widget | — | Instance komponen khusus |
| Brand Pilihan | Banner + produk | VERTICAL, gap=8 | Ada "Lihat Semua" |
| Kebutuhan Dapur | Banner + produk | VERTICAL, gap=8 | Ada "Lihat Semua" |
| Feeding Essentials | Horizontal scroll | gap=12 | Ada "Lihat Semua" |
| Body, Skin & Face Care | Horizontal scroll | gap=12 | Ada "Lihat Semua" |
| Product Carousel | Horizontal scroll cards | gap=14 | Padding top/bottom 12px |
| Flash Sale | Product cards | VERTICAL, gap=8 | Inside frame dengan padding 16px |
| Banner Section | Horizontal scroll | gap=8 | |
| Product Category | Product cards horizontal | gap=8 | |
| Kombo Hemat Widget | Custom widget | gap=16 | Instance komponen khusus |
| All Products | Grid 2 kolom | gap=10 vertikal | Padding sides 12px |

---

## Komponen DS yang Dipakai

- `Navigation` (Active=Home)
- `Status Bar → iOS`
- `Product Card Large` (Type=Default, Type=OOS)
- `_master/ title` (section header)
- `Carousel Indicator`

---

## Rules Khusus Homepage

- **Tidak pakai Top Bar standar** — header custom dengan alamat & aksi
- **Bottom Nav selalu visible** (Active=Home)
- Gap antar section **20px** (lebih besar dari halaman lain yang 16px)
- Hero banner area: full width, tidak ada side margin
- Semua section konten: padding kiri-kanan **16px**
- Section "Spesial di Astro" dan "Semua Kategori": tanpa "Lihat Semua"
