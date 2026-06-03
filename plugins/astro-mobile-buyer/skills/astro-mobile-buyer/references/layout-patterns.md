# Layout Patterns — Astro Mobile Buyer

> Fill in the values below. Leave a field as `?` if unknown — it will be fetched from Figma later.

---

## 1. Screen Anatomy (Standar struktur layar dari atas ke bawah)

```
[ Status Bar ]
[ Top Bar / Header ]
[ Content Area ]
[ Bottom Navigation ]
```

### Status Bar
- Height iOS: 44px
- Height Android: 52px
- Style default (light/dark text): light (teks gelap di atas bg terang)

### Top Bar / Header
- Height Type=Title (back-btn, title, action icons): 48px
- Height Type=SearchBox: 56px
- Halaman yang TIDAK pakai Top Bar: **Home** dan **Profile**
  - Home & Profile pakai header custom: baris alamat + tombol "Chat CS" / icon buttons (bukan komponen Top Bar standar)

### Content Area
- Top padding (jarak konten pertama dari bawah Header): 16px
- Bottom padding (jarak konten terakhir dari atas Bottom Nav): 40px
- Kiri & kanan: 12px (sudah ditetapkan)

### Bottom Navigation
- Height: 52px
- Hanya ada di 5 halaman utama: **Home, Kategori, Keranjang, Order, Profile**
- Semua halaman lain (PDP, Checkout, Search, dll.): TIDAK pakai Bottom Nav

---

## 2. Grid System

### Product Listing Grid (PLP)
- Jumlah kolom: **tergantung konteks** — 2, 3, atau 4 kolom
- Gutter (jarak antar kolom / gap horizontal antar product card): **12px**
- Gap vertikal antar baris product card: **10px**
- Product image aspect ratio: selalu **square (1:1)**

> **Catatan gap:** 8px masih dipakai untuk komponen lain (chip, icon button, badge, dll). Khusus **gap horizontal antar product card dalam grid** = **12px**.

### Single Column List
- Item height: **flexible / hug content** (tidak ada fixed height)
- Divider antar item:
  - Antar section/widget di **Home**: tidak pakai divider
  - Antar section/widget di **Cart**: pakai **Divider 8px**
  - Antar item dalam list biasa: pakai **Divider 1px**

---

## 3. Section Spacing (jarak vertikal antar section dalam satu halaman)

- Jarak antar section / widget: **16px**
- Jarak antara Section Header dan konten di bawahnya: **8px**

---

## 4. Section Header Pattern

Format: `[ Judul Section ]` + `[ "Lihat Semua" / icon ArrowRight ]`

- **Tidak semua section punya "Lihat Semua"** — hanya section yang punya halaman detail
- Section yang **TIDAK punya** "Lihat Semua": Spesial di Astro, Semua Kategori
- Jika ruang tidak cukup untuk teks "Lihat Semua" → ganti dengan **button icon bulat ArrowRight**
- Text style judul section: `Headline/Default`
- "Lihat Semua" — text style: `Headline/Tiny` | warna: `TextColor/Link`

---

## 5. Sticky Elements

### CheckoutBar (Bottom Action Bar)
- Sumber komponen: file Molecules `H55AMcAaJ1sK49u210M5sS`, node `292:17548`
- **Height: 64px**
- **Padding: top 8px | bottom 8px | left 16px | right 16px**
- **Gap** antar elemen di dalamnya: 16px
- Layout: HORIZONTAL, vertikal center
- Isi kiri: `payment` frame (VERTICAL) — label "Subtotal" (`Body/Tiny`, 12px) + harga + info hemat
- Isi kanan: icon button 40×40 (padding 8px) — icCart filled + Notification Hint badge
- Opsional di atas CheckoutBar: `.Gimmick` bar (height 40px, padding 8px top/bottom, 16px left/right) — promo info + countdown
- **Posisi: menggantikan Bottom Nav** — keduanya tidak muncul bersamaan di layar yang sama

### Sticky Header
- Ada / tidak ada di halaman mana: ?

---

## 6. Modal & Overlay Patterns

### Bottom Sheet
- **Type=Handle** → untuk interaksi ringan yang bisa ditutup via gesture (swipe down). Digunakan untuk: quick actions, filter, preview. Cocok ketika menutup sheet tidak sengaja tidak mengganggu UX secara signifikan.
- **Type=Close Btn** → untuk konten penting atau kompleks: form, konfirmasi, alur multi-step. Dismiss HANYA via tombol close — mencegah penutupan tidak sengaja yang membuat user frustasi.

### Dialog
- `Dialog` adalah wrapper yang berisi `Content Dialog`
- `Content Dialog` adalah area isi di dalam Dialog — dapat di-hide atau di-replace dengan konten apa pun sesuai kebutuhan
- Gunakan ketika butuh konfirmasi eksplisit dari user atau menampilkan konten modal yang tidak cocok di Bottom Sheet

### Overlay
- Default opacity: **50%** (`Overlay → Opacity=50%`)
- 30% dipakai hanya untuk kasus khusus yang butuh overlay lebih transparan

---

## 7. Safe Area & Platform Notes

### iOS
- Top safe area: ditangani oleh komponen `Status Bar → iOS` (sudah include safe area)
- Bottom safe area (gesture home indicator): pakai **default iOS home indicator size (34px)** — tidak ada padding manual tambahan

### Android
- Status bar: **solid**, warna `BackgroundColor/Light`

### Web Mobile
- Bottom Navigation: **identik dengan native** — tidak ada perbedaan visual
- Status bar: tidak ada native status bar — tidak pakai Status Bar component
