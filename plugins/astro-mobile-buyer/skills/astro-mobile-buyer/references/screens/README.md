# Screen References — Astro Mobile Buyer

Folder ini berisi dokumentasi struktur tiap tipe halaman, di-generate dari Figma.

## Cara Menambahkan Screen Baru

1. Di Figma, select frame screen yang ingin didokumentasikan
2. Copy link: klik kanan → "Copy link to selection"
3. Share link ke Claude dengan instruksi: "dokumentasikan screen ini"
4. Claude akan fetch → analisis struktur, komponen, spacing → simpan sebagai `.md` di folder ini

## Screens yang Perlu Didokumentasikan

Kirimkan Figma link untuk masing-masing:

| Screen | Status | File |
|---|---|---|
| Home / Beranda | ⏳ belum | home.md |
| Product Listing Page (PLP) | ⏳ belum | plp.md |
| Product Detail Page (PDP) | ⏳ belum | pdp.md |
| Keranjang / Cart | ⏳ belum | cart.md |
| Checkout | ⏳ belum | checkout.md |
| Riwayat Pesanan | ⏳ belum | order-history.md |
| Detail Pesanan | ⏳ belum | order-detail.md |
| Profil | ⏳ belum | profile.md |
| Login / Register | ⏳ belum | auth.md |
| Search Results | ⏳ belum | search.md |
| Notifikasi | ⏳ belum | notification.md |

## Format Setiap Screen `.md`

Setiap file screen berisi:
- Screenshot / deskripsi visual
- Struktur layer dari atas ke bawah
- Komponen DS yang dipakai (dengan key)
- Spacing & layout values
- State variants (loading, empty, error jika ada)
- Notes khusus untuk screen tersebut
