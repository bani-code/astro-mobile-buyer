# Platform Rules — Astro Mobile Buyer

> iOS, Android, dan Web Mobile harus menghasilkan UI yang identik secara visual.
> Perbedaan hanya pada elemen platform-native (status bar, keyboard, gesture area).

---

## iOS

### Layout
- Status Bar height: 44px (non-notch) / 59px (notch / Dynamic Island)
- Gunakan komponen: `Status Bar → iOS`
- Bottom safe area (gesture home indicator): 34px tambahan padding di bawah konten terakhir
- Ketika ada keyboard: konten di-scroll ke atas, safe area tetap terjaga

### Komponen Platform-Native
- Date Picker: gunakan `Date Picker → iOS`
- Time Picker: gunakan `Time Picker → iOS`
- Keyboard default: `Keyboard → iOS, Default`
- Keyboard numerik: `Keyboard → iOS, Numerals`

### Navigasi
- Back navigation: swipe dari kiri (gesture) + tombol back di Top Bar
- Modal dismiss: swipe ke bawah (untuk Bottom Sheet)

---

## Android

### Layout
- Status Bar height: 24px
- Gunakan komponen: `Status Bar → Android`
- Bottom navigation bar (system): apakah app pakai gesture navigation atau 3-button? → ?
- Jika gesture navigation: tambah padding bawah ? px
- Jika 3-button nav: tambah padding bawah ? px

### Komponen Platform-Native
- Date Picker: gunakan `Date Picker → Android`
- Time Picker: gunakan `Time Picker → Android`
- Keyboard default: `Keyboard → Android, Default`
- Keyboard numerik: `Keyboard → Android, Numerals`

### Navigasi
- Back navigation: tombol back hardware / gesture + tombol di Top Bar
- Modal dismiss: tombol back hardware menutup Bottom Sheet

---

## Web Mobile (Mobile Browser)

### Layout
- Tidak ada native Status Bar → tidak pakai Status Bar component
- Browser address bar: diperhitungkan dalam tinggi viewport?
  - Gunakan `100dvh` (dynamic viewport height) untuk full-screen sections
- Bottom area: browser UI bisa overlap → padding bawah minimum: ? px

### Perbedaan dari Native
- Tidak ada native keyboard component → tidak perlu ditampilkan di mockup
- Tidak ada Date/Time Picker native → pakai komponen Astro custom
- Scrollbar: disembunyikan di web mobile (pakai `scrollbar-width: none`)

### Kesamaan dengan Native
- Semua komponen UI: identik dengan iOS/Android
- Layout, spacing, warna: sama persis
- Bottom Navigation: tetap ada, posisi fixed bottom

---

## Aturan Umum Lintas Platform

- Frame width di Figma: selalu **360px** untuk semua platform
- Frame height referensi: **800px**
- Content margin kiri & kanan: **12px** masing-masing
- Komponen yang digunakan: sama — tidak ada versi berbeda per platform kecuali yang disebutkan di atas
- Semua frame di Figma harus menggunakan `Clip content: ON`

---

## Catatan Khusus

> Tambahkan di sini jika ada perbedaan platform lain yang spesifik untuk Astro.

- ?
