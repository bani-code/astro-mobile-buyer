# Component Recipes — Astro Mobile Buyer

> Dokumen ini berisi pola kombinasi komponen yang dipakai berulang di seluruh app.
> Sumber: file Figma komposisi terpisah (bukan DS utama).
>
> Untuk menambahkan recipe dari Figma:
> 1. Share link frame/node dari file komposisi
> 2. Saya akan fetch → ekstrak struktur, spacing, komponen yang dipakai → tulis di sini

---

## Cara Membaca Recipe

Setiap recipe berisi:
- **Struktur**: susunan elemen dari atas ke bawah / kiri ke kanan
- **Komponen DS yang dipakai**: key dari `libraries.md`
- **Spacing**: padding & gap yang digunakan (dalam token atau px)
- **Rules**: aturan kapan/bagaimana komponen ini dipakai

---

## Figma File Komposisi

| File | Key |
|---|---|
| Molecules — AstroSystem | `H55AMcAaJ1sK49u210M5sS` |
| Product Card Revamp V4 | `F44AeFArfOOwpHvjiMatwL` |

---

## Recipe 1: Product Card

**Sumber:** `H55AMcAaJ1sK49u210M5sS`, node `387:15193`

### Dua Ukuran

| | Large | Small |
|---|---|---|
| Dipakai untuk | Grid **2 kolom** | Grid **3 kolom** |
| Lebar card | **162px** | **104px** |
| Tinggi card | ~248px (variable) | ~200px (variable) |
| Image area | 162×162, radius=16 | 104×104, radius=12 |
| Layout | VERTICAL, gap=8px | VERTICAL, gap=8px |

### Grid Layout Rules
- Margin kiri & kanan layar: **12px**
- Gap horizontal antar card: **12px**
- Gap vertikal antar row: **16px**
- Kalkulasi lebar: `(360 - 12 - 12 - gap×(col-1)) / col`
  - 2 kolom: `(360 - 24 - 12) / 2 = 162px`
  - 3 kolom: `(360 - 24 - 24) / 3 = 104px`

### Struktur Card (Top → Bottom)
```
[ Top Content ] — image area, background BackgroundColor/LightGrey
  ├── Product Image (1:1, IMAGE fill)
  ├── Label badge (Terlaris / Produk Baru) — pojok kiri atas
  ├── Status badge (organic, dll) — pojok kanan atas
  ├── Gimmick/promo quantity helper (opsional, dark overlay)
  └── Qty Editor button — pojok kanan bawah
      ├── Sebelum ditambah: icon "+" saja (40×40, stroke StrokeColor/Active)
      └── Setelah ditambah: [-] [qty] [+] (100×40, bg BackgroundColor/Primary)

[ Product Details ] — background BackgroundColor/Light, gap=4px
  ├── Price Info (HORIZONTAL, gap=4)
  │   ├── Harga: "Rp" (Caption/Tiny-Bold) + angka (Body/Default-Bold) — TextColor/PrimaryDark
  │   └── Diskon: Label X% (RedDark, Filled) + harga coret (Body/Tiny, TextColor/SecondaryDark)
  ├── Nama Produk — Body/Tiny, TextColor/PrimaryDark, max 2 baris
  ├── Variant Tags — bg LightGrey, stroke 0.5px Subtle, radius=4, Caption/Tiny
  ├── Pack Size & Rating — Caption/Small, TextColor/SecondaryDark
  └── Progress Bar stok (opsional)

[ "Ad" label ] — Caption/Tiny-Bold, TextColor/SecondaryDark (hanya untuk produk iklan)
```

### Variant States
| Variant | Kondisi |
|---|---|
| `Type=Default` | Produk tersedia normal |
| `Type=OOS` | Stok habis — tampil label "Habis" + CTA "Lihat Produk Serupa" |
| `Type=Coming Soon` | Belum tersedia |

---

## Recipe 2: Error & Failure

**Sumber:** `H55AMcAaJ1sK49u210M5sS`, node `120:4024`

### Struktur
Error & Failure selalu tampil sebagai **Bottom Sheet** di atas overlay:
```
[ Full Screen Frame 360×800 ]
  ├── Overlay (Opacity=50%, full screen)
  └── Bottom Sheet (anchored to bottom)
      ├── Content area
      │   ├── Illustration (dari library tWd29HOmovgLvK5NdqbxB0)
      │   ├── Title — Headline/Large
      │   └── Description — Body/Small
      └── Footer (padding top=16px, kiri-kanan=16px)
          └── Button(s)
```

### Variants

| Variant | Bottom Sheet Height | Tombol | Copy |
|---|---|---|---|
| `Type=404` | 422px | 1 tombol horizontal | "Wah, lagi gangguan 😅" |
| `Type=No Internet Connection` | 476px | 2 tombol vertikal | "Koneksi terputus 😕" |
| `Type=Server Error` | 476px | 2 tombol vertikal | "Wah, lagi gangguan 😅" |
| `Type=Timeout` | 476px | 2 tombol vertikal | — |
| `Type=App Update Required` | 476px | 2 tombol vertikal | — |
| `Type=Location Access` | 476px | 2 tombol vertikal | — |

### Bottom Sheet Config
- `Type=Single btn`: `Bottom Sheet → Type=Single btn, Swipe Indicator=Yes`
- `Type=2 btn vertical`: `Bottom Sheet → Type=Ver Btn, Swipe Indicator=Yes`
- Semua varian pakai **Swipe Indicator = Yes** (Handle style)

---

## Recipe 3: Empty State

**Sumber:** `H55AMcAaJ1sK49u210M5sS`, node `126:125850`

### Struktur
```
[ EmptyState Frame — 328px wide ]
  padding: left=16px, right=16px
  layout: VERTICAL, gap=24px
  align: CENTER

  ├── Illustration (280×168, dari library tWd29HOmovgLvK5NdqbxB0)
  └── Content (gap=16px)
      ├── Copy (gap=4px)
      │   ├── Title — Headline/Large, TextColor/PrimaryDark
      │   └── Description — Body/Small, TextColor/SecondaryDark
      └── CTA Button — Primary, Size=Medium
```

### Positioning Rules
- **Posisi horizontal**: center di layar
- **Spacing dari konten/section di atasnya**: **64px**
- Width: 328px (bukan full 360 — ada padding 16px kiri-kanan)

### Variants
| Variant | Ilustrasi | Judul | Sub-teks | CTA |
|---|---|---|---|---|
| `Type=UserStorage` | ilusEmptyCart | "Belum ada produk di sini" | "Tambahkan produk pilihanmu untuk mulai belanja dengan lebih mudah." | "Mulai Belanja" |
| `Type=NoContent` | ilusNoContent | "Barang belum tersedia" | "Belum ada produk yang ditampilkan. Coba cari kategori atau produk lain." | "Lihat Produk Lain" |

---

## Recipe 4: CheckoutBar

**Sumber:** `H55AMcAaJ1sK49u210M5sS`, node `292:19144`

### Dua Type

| | Type=Default | Type=Cart |
|---|---|---|
| Dipakai di | Search, Campaign, Flash Sale, Category, Produk Serupa, Discovery | Cart page saja |
| Posisi | Fixed bottom — **menggantikan** Bottom Nav | Fixed bottom — **di atas** Bottom Nav |
| Action kanan | Icon cart (40×40) + Notification badge | Button Primary Small "Bayar" (128×40) |
| Lebar area payment | 272px | 184px |

### Struktur (keduanya sama)
```
[ CheckoutBar — 360×64px ]
  padding: top=8px, bottom=8px, left=16px, right=16px
  layout: HORIZONTAL, gap=16px, align CENTER

  ├── Payment Info (VERTICAL, left side)
  │   ├── Label "Subtotal" — Body/Tiny, TextColor/SecondaryDark
  │   ├── Harga total — Body/Default-Bold, TextColor/PrimaryDark
  │   └── Info hemat (opsional) — Caption/Small, TextColor/Link
  └── Action (right side)
      ├── [Default] Icon button 40×40 — icCart Filled + Notification Hint badge
      └── [Cart] Button Primary Small — "Bayar" (128×40, radius=8)

[ .Gimmick bar — 360×40px ] ← opsional, muncul di atas CheckoutBar
  padding: top=8px, bottom=8px, left=16px, right=16px
  layout: HORIZONTAL, gap=8px
  isi: icVoucher + teks promo + icChevronDown + countdown timer
```

### Aturan Kemunculan
- **Type=Default**: muncul saat ada produk dalam konteks halaman listing. Tidak muncul bersamaan dengan Bottom Nav.
- **Type=Cart**: muncul di Cart page, tepat di atas Bottom Nav (keduanya visible bersamaan).
- **.Gimmick bar**: opsional — tampil di atas CheckoutBar saat ada promo aktif.

---

## Recipes Lainnya (belum didokumentasikan)

Kirimkan Figma link untuk menambahkan:
- [ ] Section Header (judul + "Lihat Semua")
- [ ] Promo Banner
- [ ] Category Card
- [ ] Cart Item Row
- [ ] Order Card
- [ ] Loading / Skeleton State
