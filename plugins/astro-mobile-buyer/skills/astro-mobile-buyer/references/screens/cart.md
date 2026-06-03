# Screen: Cart (Keranjang)

**File:** `9xuDPzF47hOTP3KuYwbWVT` | **Node:** `7609:11406`
**Dimensi:** 360×3711px (scrollable) | **Platform:** iOS (reference)

---

## Anatomi Layar (atas ke bawah)

```
[ Top Bar — 92px ]                       ← StatusBar + Header Type=Title
─────────────────── scrollable content ───────────────────
[ display/cart/alamat pengiriman — 230px ]
  ├── Alert — 328×52px (peringatan alamat)
  ├── alternative — 328×24px (opsi alamat alternatif)
  └── pwp 2 — 328×114px (info alamat + estimasi)
[ Divider 8px ]
[ Section Delivery — 288px ]             ← grup pengiriman pertama
  ├── Header Section — 48px (tipe pengiriman + timer countdown)
  └── List Product — 148px (cart item rows)
[ Divider 8px ]
[ Section Delivery — 240px ]             ← grup pengiriman kedua
[ Divider 8px ]
[ Section Delivery — 486px ]             ← grup pengiriman ketiga
[ Section Delivery — 486px ]             ← dan seterusnya (bisa multiple)
[ Section Delivery — 486px ]
[ Divider 8px ]
[ catatan — 56px ]                       ← text field inline (catatan pesanan)
[ Divider 8px ]
[ Promo / Voucher — 378px ]              ← input kode promo + daftar promo
[ Promo / Voucher — 240px ]              ← promo group kedua
[ Divider 8px ]
[ PWP — 180px ]                          ← Purchase With Purchase (produk bonus)
[ Divider 8px ]
[ Promo Entry Point Card — 84px ]        ← instance komponen promo
[ Divider 8px ]
[ Alert — 92px ]                         ← info/warning sebelum subtotal
[ display/cart/subtotal — 121px ]        ← ringkasan harga
─────────────────── fixed bottom ─────────────────────────
[ CheckoutBar — 104px ]                  ← total + CTA "Bayar"
[ Navigation — 52px ]                    ← Bottom Nav Active=Keranjang
[ Home Indicator iOS — 34px ]
```

---

## Detail Layout

- **Top Bar**: 92px = StatusBar iOS (44px) + Header Type=Title (48px)
- **Padding konten**: kiri-kanan 16px (section header & item)
- **Divider antar section**: 8px (solid divider, bukan spacing)
- **Section Delivery**: bisa lebih dari 4 grup jika user punya banyak item dari toko berbeda

---

## Keunikan Cart — CheckoutBar + Navigation BERSAMAAN

Cart adalah satu-satunya halaman di mana **CheckoutBar dan Navigation muncul bersamaan** di bottom.

```
[ CheckoutBar — 104px ]   ← di atas Navigation
[ Navigation — 52px ]     ← Active=Keranjang
```

> Ini berbeda dengan halaman Search/PDP/Kategori di mana CheckoutBar **menggantikan** Navigation.

---

## Section Delivery — Struktur Per Grup

Tiap grup pengiriman berisi:

```
[ Header Section — 48px ]
  ├── icon (tipe pengiriman)
  ├── label "Pengiriman 1 Jam" + timer countdown
  └── right: button "Ubah" atau info
[ List Product ]
  └── Cart Item Row (per produk):
      ├── Kiri: product image (Square/small — 56×56px)
      ├── Tengah: nama produk + harga
      └── Kanan: Qty-Editor (Size=Small)
```

---

## Cart Item Row

| Elemen | Spec |
|---|---|
| Product image | `Square/small` — 56×56px |
| Nama produk | `Body/Tiny`, `TextColor/PrimaryDark` |
| Harga | `Body/Default-Bold` |
| Qty-Editor | `Size=Small, State=Enabled` — di kanan card |
| Gap kiri-kanan item | 16px padding dalam section |
| Gap antar item | 12px |

---

## Catatan Pesanan

- Komponen: `text field inline`
- Width: 328px (padding 16px kiri-kanan)
- Height: 32px
- Placeholder: "Tambah catatan pesanan..."

---

## Promo / Voucher Section

- Icon: `icDiscount`
- Berisi: input kode promo + daftar promo yang tersedia/dipilih
- Bisa ada 2 grup (misalnya: voucher toko + voucher platform)

---

## Subtotal Area

```
[ display/cart/subtotal — 121px ]
  └── rows berisi:
      ├── Subtotal (label + nilai)
      ├── Diskon (label + nilai, jika ada)
      ├── Biaya pengiriman
      └── Total
```

---

## Komponen DS yang Dipakai

- `StatusBar → iOS`
- `Top Bar → Type=Title`
- `Alert` (peringatan alamat + info bawah)
- `Divider 8px`
- `Qty-Editor → Size=Small`
- `Promo Entry Point Card`
- `CheckoutBar → Type=Cart` ← khusus cart, muncul bersama Navigation
- `Navigation → Active=Keranjang`

---

## Rules Khusus Halaman Ini

- **CheckoutBar Type=Cart + Navigation keduanya visible** — tidak saling menggantikan
- **Multiple Section Delivery** — jumlah grup tergantung jumlah toko/jenis pengiriman
- **Divider 8px** antar setiap section (bukan spacing biasa)
- **Background frame**: `BackgroundColor/Light`
- **Catatan**: text field inline, opsional diisi user
- **PWP section**: muncul jika ada produk Purchase With Purchase yang eligible
