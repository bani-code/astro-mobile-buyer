# Brand Voice & Identity — Astro Indonesia
> Source: Brand/Design Guideline (last updated: 22 April 2025)
> Untuk: designer yang perlu tahu arah brand saat buat copy, pilih visual direction, atau review design

---

## Brand Essence

| Dimensi | Deskripsi |
|---------|-----------|
| **Personality** | Friendly, fast, trustworthy — seperti tetangga yang helpful dan bergerak secepat cahaya |
| **Tone** | Hangat dan langsung (direct); tidak kaku/formal; tidak terlalu slang/alay |
| **Space theme** | Metafora luar angkasa boleh dipakai tipis-tipis — *"galactic grocery adventure"*, *"AstroFriends"* — jangan overdone |
| **Mascot** | **Airo** — karakter explorer yang melambangkan rasa ingin tahu dan penemuan |
| **Tagline** | "Anything You Need, Fast." |

---

## Bahasa per Audience

| Audience | Bahasa | Contoh konteks |
|----------|--------|---------------|
| Customers (app Buyer) | **Bahasa Indonesia** | Order confirmation, push notif, banner promo, copy produk |
| Mitra (gudang/driver) | **Bahasa Indonesia** | Crew app, instruksi picking, status label |
| Astronauts (internal) | **English** | Admin web, dashboard, internal tools |
| Mixed | BI untuk label, EN untuk UI chrome | Status chip "Aktif", button "Save" |

---

## Copy Rules — App Buyer (Bahasa Indonesia)

### Banner & Promo
- Headline: **max 20 karakter**
- Lead dengan benefit atau occasion: *"Promo Tanggal Tua"*, *"Payday Deals"*, *"Fresh Today"*
- Asterisk (*) setelah % atau Rp: *"50%\*"*, *"Rp10.000\*"*
- CTA button: action verb, max 3–4 kata — *"Beli Sekarang"*, *"Lihat Promo"*, *"Tambah ke Keranjang"*

### Empty States
- ✅ Explain why + next action: *"Belum ada pesanan. Mulai belanja sekarang!"*
- ❌ Jangan hanya: *"Tidak ada data"*

### Error Messages
- ✅ Spesifik + actionable: *"Nomor HP tidak valid. Masukkan nomor yang terdaftar di Astro."*
- ❌ Jangan: *"Invalid input"* atau *"Terjadi kesalahan"*

### Confirmation Dialogs
- ✅ Spesifik tentang apa yang terjadi: *"Hapus produk ini? Tindakan ini tidak bisa dibatalkan."*
- ❌ Jangan: *"Apakah kamu yakin?"*

### Post-Purchase
- Konfirmasi diterima: *"Pesananmu sedang diproses!"*
- Set ekspektasi: sebutkan estimasi waktu
- Celebrate completion: hangat, singkat

### Refund Flow
- Empathetic — acknowledge inconvenience
- Active voice: *"Kami akan memproses refundmu dalam 1x24 jam"*
- ❌ Hindari passive: *"Refund akan diproses"*

---

## UX Copy Quick Reference

### Button Labels

| Aksi | Bahasa Indonesia | English (admin) |
|------|-----------------|-----------------|
| Save | Simpan | Save |
| Cancel | Batal | Cancel |
| Delete | Hapus | Delete |
| Submit | Kirim / Submit | Submit |
| Add | Tambah | Add |
| Edit | Ubah / Edit | Edit |
| Confirm | Konfirmasi | Confirm |
| View detail | Lihat Detail | View Details |

### Status Labels

| Status | Label | Warna |
|--------|-------|-------|
| Active / Done | Aktif / Selesai | Green |
| In Progress | Dalam Proses | Yellow/Orange |
| Pending | Menunggu | Red/Pink |
| Inactive | Nonaktif | Grey |
| Cancelled | Dibatalkan | Red |

---

## Product Naming

Format: **Nama Produk** (Montserrat Semi Bold) + **Volume/Berat** (Montserrat Italic, ukuran lebih kecil)

Contoh:
- "Tempe Chips Black Truffle" + "60 gr"
- "Air Mineral" + "600 ml"
- "Mie Goreng" + "85 gr"

Rules:
- Sentence case — bukan ALL CAPS atau Title Case Every Word
- Volume/berat selalu di text element terpisah, lebih kecil, italic
- Unit standar: gr, ml, kg, L

---

## Logo & Visual Rules (ringkasan untuk digital)

- **Default use (digital):** `logo-main-lockup-color.png` — Astro wordmark + Airo mascot
- **Pada background gelap/biru:** `logo-main-lockup-white.png`
- **Icon/favicon:** `logo-logomark-color.png`
- Jangan stretch, skew, rotate, atau recolor logo
- Jangan pakai wordmark tanpa karakteristik italic-nya
- Clear space wajib dijaga — jangan terlalu rapat dengan elemen lain
- Latar yang oke: putih, Sky Blue, Galaxy Blue

## Brand Colors (untuk referensi copy/visual direction, bukan coding token)

| Warna | Hex | Kegunaan |
|-------|-----|----------|
| Galaxy Blue (primary) | `#2455B0` | Brand utama |
| Deep Sky Blue | `#246EE5` | Variant primer baru |
| Cosmic White | `#FFFFFF` | Background utama |
| Nebula Green | `#00AA5B` | Success, selesai |
| Alert Red | `#EC465C` | Error, urgent |
| Solar Orange | `#FA591D` | Alert, darurat |
| Star Yellow | `#FFBB0C` | In-progress |

> Untuk coding — gunakan **token name** dari `references/libraries.md`, bukan hex langsung.
