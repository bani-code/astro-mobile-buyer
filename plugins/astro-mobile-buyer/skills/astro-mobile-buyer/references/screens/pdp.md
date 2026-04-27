# Screen: PDP (Product Detail Page)

**File:** `9xuDPzF47hOTP3KuYwbWVT` | **Node:** `7504:3779` → child "PDP"
**Dimensi:** 360×1738px (scrollable) | **Platform:** iOS (reference)

---

## Anatomi Layar (atas ke bawah)

```
[ PDP Media Area — 454px total ]
  ├── Top Nav — floating di atas image (44px status bar + 50px nav = 94px)
  │   ├── Status Bar iOS (44px)
  │   └── Top Nav: back btn + share/wishlist icons (50px, padding 10px top/bottom, 16px sides)
  └── Product Image Carousel (360×360, full width)
      ├── Carousel Indicator (On White Bg)
      └── Label badge (promo/diskon)

─────────────── scrollable content ──────────────────
[ Countdown Timer — 92px ]          ← hanya muncul saat ada flash sale
[ Main Product Info — 144px ]       ← padding 16px sides
  ├── Label badges (row horizontal)
  ├── Rating & stock info
  ├── Harga (Rp + angka + harga coret + label diskon)
  └── Astro Koin info

[ Jaminan Garansi — 58px ]          ← padding 12px, bg light, ada icon
[ Value Property — 80px ]           ← info pengiriman, dll (2 rows)
[ Product Detail accordion — 314px ]← State=Expand
  ├── Title section
  ├── Highlight points
  └── Info table
[ Deskripsi — 158px ]
[ Product Carousel "Produk Serupa" — 294px ]

─────────────── fixed bottom ─────────────────────────
[ .Gimmick bar — 40px ]             ← opsional, hanya saat ada promo
[ Sticky Amount — 56px ]            ← "+ Keranjang" CTA, tanpa Bottom Nav
```

---

## Catatan Kritis PDP

- **Top Nav FLOATING** di atas image — bukan di bawah status bar, overlap dengan gambar produk
- **Tidak ada Bottom Nav** — digantikan Sticky Amount
- Image area: **360×360px**, full width, no margin
- Setelah image area: konten diberi padding **16px kiri-kanan**
- Countdown Timer: hanya muncul saat produk ada flash sale aktif

---

## Spacing

- Padding konten (setelah image): 16px kiri & kanan
- Antar sub-section dalam konten: 8–12px
- Sticky Amount height: 56px (pad 8px top/bottom, 16px left/right)
- Gimmick bar (opsional): 40px, muncul tepat di atas Sticky Amount

---

## Komponen DS yang Dipakai

- `Status Bar → iOS`
- `Carousel Indicator` (On White Bg, Quantity=>6)
- `Label` (promo/diskon badge di image)
- `Divider 1px` (di atas sticky amount)
- Sticky Amount custom (`_sticky amount/ master`, h=56px)
- `Product Card Large` (di carousel "Produk Serupa")

---

## Rules Khusus PDP

- Top Nav bersifat **floating/transparent** di awal scroll, bisa berubah solid saat scroll ke bawah
- CTA utama: **"+ Keranjang"** di Sticky Amount (bukan di body konten)
- Carousel image: swipe horizontal, indicator di pojok kanan bawah image
- Section "Produk Serupa": horizontal scroll, Product Card Large
- Tidak ada Bottom Navigation di halaman ini
