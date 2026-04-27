# Color Usage Rules — Astro Mobile Buyer

> Map semantic contexts to actual color tokens. Leave `?` if unknown.
> Token names refer to variables in DS file `LD5Y3L9vAvw3MAU2POgseI`.

---

## Background

| Context | Token |
|---|---|
| Background halaman utama (screen bg) | `BackgroundColor/Light` |
| Background card / white section | `BackgroundColor/Light` |
| Background section abu-abu (alternating sections) | `BackgroundColor/Disable` |
| Background input field | `BackgroundColor/Light` |
| Background disabled state | `BackgroundColor/Disable` |
| Background image placeholder di product card | `BackgroundColor/LightGrey` |
| Background halaman form / checkout | `BackgroundColor/Light` |
| Background success state | `BackgroundColor/LightGreen` |
| Background warning state | `BackgroundColor/LightOrange` |
| Background error state | `BackgroundColor/LightRed` |
| Bottom Sheet / Modal background | `BackgroundColor/Light` |
| Overlay background | `BackgroundColor/Dark` opacity **50%** (default) / 30% (khusus) |

---

## Text

| Context | Token |
|---|---|
| Body text utama | `TextColor/PrimaryDark` |
| Body text sekunder / sub-info | `TextColor/SecondaryDark` |
| Placeholder input | `TextColor/Placeholder` |
| Disabled text | `TextColor/Disable` |
| Link / teks yang bisa diklik | `TextColor/Link` |
| Nama produk | `TextColor/PrimaryDark` |
| Harga normal (tidak ada diskon) | `TextColor/PrimaryDark` |
| Harga setelah diskon (harga yang ditonjolkan) | `TextColor/PrimaryDark` |
| Harga coret (sebelum diskon) | `TextColor/SecondaryDark` |
| Label persentase diskon ("50% OFF") | Komponen `Label`, Size=Small, Filled=True, Color=RedDark |
| Teks "Hemat Rp X" | `TextColor/Link` |
| Info stok hampir habis ("Tersisa 3") | `TextColor/Error` |
| Teks info sekunder produk (berat, satuan, rating) | `TextColor/SecondaryDark` |
| Teks di atas background gelap / tombol primary | `TextColor/PrimaryLight` |
| Teks error | `TextColor/Error` |
| Teks success | `TextColor/Success` |
| Teks warning | `TextColor/Warning` |

---

## Icon

| Context | Token |
|---|---|
| Icon default (di atas bg putih) | `IconColor/Default` |
| Icon di atas background gelap/berwarna | `IconColor/Light` |
| Icon navigasi aktif | `IconColor/PrimarySelected` |
| Icon navigasi tidak aktif | `IconColor/DefaultDark` |
| Icon dalam tombol primary | `IconColor/Light` |
| Icon disabled | `IconColor/Disable` |
| Icon error | `IconColor/Red` |
| Icon success | `IconColor/Green` |

---

## Stroke / Border

| Context | Token |
|---|---|
| Product card | tidak ada border/stroke |
| Border card/container default | `StrokeColor/Subtle` |
| Border input default | `StrokeColor/Default` |
| Border input focus / active | `StrokeColor/Active` |
| Border input error | `StrokeColor/Error` |
| Border input disabled | `StrokeColor/Disable` |
| Border card yang dipilih / active state | `StrokeColor/Active` |
| Divider antar list item | `StrokeColor/Subtle` |

---

## Catatan Khusus Astro

| Context | Komponen & Variant |
|---|---|
| Label "50% OFF" / persentase diskon | `Label` Size=Small, Filled=True, Color=RedDark |
| Label "Terlaris" | `Label` Size=Small, Filled=False, Color=Blue |
| Label "Produk Baru" | `Label` Size=Small, Filled=False, Color=Blue |
| Label "Stok Terbatas" | ? |
| Badge notifikasi / cart count | Komponen `Notification (Hint)`, Colors=Red |
