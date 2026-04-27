# Content & Copy Rules — Astro Mobile Buyer

> Fill in Astro-specific content standards. Leave `?` if unknown.

---

## Bahasa & Tone

- Bahasa utama: Bahasa Indonesia
- Bahasa sekunder: tidak ada
- Tone: friendly, singkat, langsung ke poin. Gunakan "kamu" (bukan "Anda")
- Sapaan user: tidak ada sapaan khusus

---

## Format Harga

- Currency symbol: `Rp`
- Separator ribuan: titik (`.`) → contoh: `Rp12.000`
- **Tidak ada spasi** antara "Rp" dan angka → `Rp12.000` (bukan `Rp 12.000`)
- Harga coret: tampilkan dengan `TextColor/SecondaryDark` + strikethrough
- Format diskon: **tergantung tempat**
  - Di product card: tampilkan persentase saja → `X%` (menggunakan komponen Label Size=Small, Filled=True, Color=RedDark)
  - Di tempat lain (mis: checkout, promo detail): bisa "Hemat RpX"

---

## Format Kuantitas / Satuan

- Format satuan produk: ? (mis: "250 gr", "1 kg", "1 pcs")
- Format berat: gram atau kilogram? threshold konversinya? (mis: di bawah 1000gr tampilkan gr, di atas tampilkan kg)
- Format volume: ml / liter?

---

## Label Status Produk

| Kondisi | Teks yang Ditampilkan |
|---|---|
| Stok hampir habis | tidak ada — langsung "Habis" saja |
| Stok habis | "Habis" |
| Produk terlaris | "Terlaris" (Label Size=Small, Filled=False, Color=Blue) |
| Produk baru | "Produk Baru" (Label Size=Small, Filled=False, Color=Blue) |
| Ada promo/diskon | `X%` di card (Label Size=Small, Filled=True, Color=RedDark) |
| Pre-order | ? |

---

## CTA (Call-to-Action) Standard

| Aksi | Teks CTA |
|---|---|
| Tambah ke keranjang — di product card | icon `+` saja (tanpa teks) |
| Tambah ke keranjang — di PDP | `+ Keranjang` |
| Lanjut ke checkout | `Lanjut` |
| Bayar | `Bayar` |
| Coba lagi (error) | `Coba Lagi` |
| Kembali ke beranda | `Kembali ke Beranda` |
| Lihat semua (section) | `Lihat Semua` (atau icon ArrowRight jika space terbatas) |
| Masuk / Login | `Masuk` |
| Daftar akun baru | `Daftar` |

---

## Empty States

| Konteks | Judul | Sub-teks |
|---|---|---|
| Keranjang kosong | "Belum ada produk di sini" | "Tambahkan produk pilihanmu untuk mulai belanja dengan lebih mudah." |
| Pencarian tidak ada hasil | "Barang belum tersedia" | "Belum ada produk yang ditampilkan. Coba cari kategori atau produk lain." |
| Riwayat pesanan kosong | "Belum ada produk di sini" | "Tambahkan produk pilihanmu untuk mulai belanja dengan lebih mudah." |
| Notifikasi kosong | "Belum ada notifikasi" | "Info pesanan, promo, dan update terbaru akan muncul di sini." |

---

## Error & Feedback Messages

| Kondisi | Judul | Sub-teks |
|---|---|---|
| Koneksi internet bermasalah | "Koneksi terputus 😕" | "Kamu lagi nggak terhubung ke internet. Cek koneksi lalu coba lagi, ya!" |
| Server error (500) | "Wah, lagi gangguan 😅" | "Ada masalah di sistem kami. Coba lagi sebentar, ya." |
| Session expired / perlu login ulang | — | "Sesimu sudah habis. Masuk lagi untuk melanjutkan, ya." |
| Stok tidak cukup saat checkout | ? | ? |
| Minimum order tidak terpenuhi | ? | ? |
| Promo code tidak valid | ? | ? |

---

## Informasi Pengiriman

- Label "gratis ongkir": ?
- Label minimum pembelian: ? (format: "Min. pembelian Rp X")
- Label estimasi pengiriman: ? (format: "Tiba dalam X jam" / "Besok, DD Mon")
- Label area pengiriman (jika di luar jangkauan): ?

---

## Catatan Khusus Astro

> Aturan konten/copy spesifik Astro yang tidak tercakup di atas.

- ?
