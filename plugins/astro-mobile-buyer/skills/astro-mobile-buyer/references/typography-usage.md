# Typography Usage Rules — Astro Mobile Buyer

> Map UI contexts to text style tokens. Leave `?` if unknown.
> All keys refer to text styles in DS file `LD5Y3L9vAvw3MAU2POgseI`.

---

## Page-Level

| Context | Text Style |
|---|---|
| Judul halaman di Top Bar | `Body/Default-Bold` |
| Action / link text di Top Bar (kanan) | `Headline/Tiny` |
| Judul section / widget | `Headline/Default` |
| Link "Lihat Semua" | `Headline/Tiny` |

---

## Product

| Context | Text Style |
|---|---|
| Nama produk (di card listing) | `Body/Tiny` |
| Nama produk (di PDP, judul besar) | `Body/Default` |
| Deskripsi produk | `Paragraph/Small` |
| Harga produk — angka utama (menonjol) | `Body/Default-Bold` |
| "Rp" prefix di depan harga | `Caption/Tiny-Bold` |
| Harga coret (sebelum diskon) | `Body/Tiny` |
| Info berat / satuan / rating produk | `Caption/Small` |

---

## Navigation & Actions

| Context | Text Style |
|---|---|
| Label item Bottom Navigation (aktif & non-aktif) | `Caption/Tiny-Bold` |

---

## List & Form

| Context | Text Style |
|---|---|
| Teks utama list item | `Body/Tiny` |
| Teks sekunder / sub-info list item | `Caption/Small` |
| Label di atas input field | `Caption/Tiny` |
| Helper text / supporting text / error di bawah input | `Paragraph/Tiny` |

---

## Feedback & States

| Context | Text Style |
|---|---|
| Judul empty state (mis: "Barang belum tersedia") | `Headline/Large` |
| Sub-teks empty state | `Body/Small` |

---

## Catatan Khusus Astro

- Bottom Navigation: semua label (aktif maupun non-aktif) pakai text style yang sama (`Caption/Tiny-Bold`) — perbedaan hanya pada warna icon & teks
- Top Bar Type=Title: judul pakai `Body/Default-Bold`, bukan Headline — ini berbeda dari konvensi umum
- Harga terdiri dari dua teks berbeda: "Rp" pakai `Caption/Tiny-Bold` (kecil, superscript-style), angkanya pakai `Body/Default-Bold`
