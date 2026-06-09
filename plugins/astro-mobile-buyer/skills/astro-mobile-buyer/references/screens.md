# Screen Map — Astro Buyer App (iOS Source of Truth)
> Extracted from: astro-buyer-ios router files + TabBarConfiguration
> Last updated: June 2026
> Note: iOS adalah versi paling update. Web output tetap HTML/CSS/JS, tapi screen reference dari sini.

---

## Tab Bar Navigation

Astro Buyer punya **2 konfigurasi tab bar** (ditentukan via Remote Config):

### Default Tabs (5 tab — paling umum)
```
[ Beranda ] [ Rewards/BLP ] [ Keranjang ] [ Pesanan ] [ Akun ]
```

### Category Tabs (5 tab — eksperimen)
```
[ Beranda ] [ Kategori ] [ Keranjang ] [ Pesanan ] [ Akun ]
```

### Initial Tabs (4 tab — first launch / eksperimen)
```
[ Beranda ] [ Keranjang ] [ Pesanan ] [ Akun ]
```

> **Rule di plugin:** Bottom Nav hanya muncul di 5 screen utama ini. Semua screen lain TIDAK punya bottom nav.

---

## Screen Inventory — Lengkap per Feature

### 🏠 Home
| Screen | Deskripsi | Navigation target dari sini |
|--------|-----------|----------------------------|
| Home (Beranda) | Main landing — banner, flash sale, PWP, product grid, DLC | Search, Category, Product Detail, Flash Sale, PWP, Flexi, Loyalty, AstroBalance, All Category, Send As Gift, Live Track, Order Review, DLC |
| See All Dynamic Channel | List produk dari satu channel/widget | Product Detail |
| See All Flash Sale | List semua produk flash sale | Product Detail |

### 🔍 Search
| Screen | Deskripsi |
|--------|-----------|
| Search | Search bar + hasil + filter + suggestion |
| Product Suggestion | Bottom sheet untuk suggest produk baru ke Astro |

### 📦 Product
| Screen | Deskripsi | Bottom Sheets |
|--------|-----------|---------------|
| Product Detail (PDP) | Detail produk — foto, harga, deskripsi, ATC | Product Form, PWP Recommendation, User Age Check, Guarantee |
| Product Form | Modifier/variant selection (untuk kitchen/modifier products) | — |
| Product Modifier | Pilih modifier (toppings, variants) | — |
| Product Variant | Pilih variant produk | — |
| Product Recommendation | Produk serupa (OOS fallback) | — |
| Bulk Purchase | Pembelian dalam jumlah besar | — |
| Pack Size BMSM | Buy More Save More pack size selection | — |

### 🛒 Cart
| Screen / Bottom Sheet | Deskripsi |
|----------------------|-----------|
| Cart (Keranjang) | Main cart — item list, promo, ATC rekomendasi, order summary |
| Address Confirmation | Popup konfirmasi alamat jauh |
| Payment Method | Bottom sheet pilih metode bayar |
| Voucher List | Bottom sheet pilih promo/voucher |
| Voucher TnC | Bottom sheet syarat & ketentuan promo |
| Loyalty in Cart | Bottom sheet tukar Astro Koin |
| Send As Gift | Bottom sheet kirim sebagai hadiah |
| Driver Availability | Bottom sheet info ketersediaan driver |
| Shipping Info | Bottom sheet info ongkir |
| Platform Fee | Bottom sheet info platform fee |
| Saldo Astro | Bottom sheet info saldo astro |
| Scheduled Delivery | Bottom sheet pilih jadwal pengiriman |
| Delivery Options Details | Bottom sheet detail opsi pengiriman |
| Super Full Slot | Bottom sheet slot Astro Super penuh |

### 💳 Payment
| Screen | Deskripsi |
|--------|-----------|
| Payment Method | Pilih metode pembayaran |
| Payment Status | Status pembayaran setelah checkout |
| Credit Card Detail | Input detail kartu kredit |
| GoPay Activation | Aktivasi/sambung GoPay |
| Payment Method List | Daftar semua metode yang tersimpan |

### 📋 Order
| Screen | Deskripsi |
|--------|-----------|
| Order History (Pesanan) | List semua pesanan |
| Order Detail | Detail satu pesanan — items, status, tracking |
| Order Detail Special | Variant order detail untuk kasus khusus |
| Live Track | Real-time tracking driver |
| Tracking Webview | Webview tracking external |
| Order Widget | Widget pesanan aktif di Home |
| Reorder | Re-order dari pesanan lama |

### 👤 Account / Profile
| Screen | Deskripsi |
|--------|-----------|
| Account (Akun) | Main profile menu |
| Detail Akun | Edit profil: nama, HP, email, NIK, tanggal lahir |
| Pengaturan PIN | Setup / ubah / lupa PIN |
| OOS Reminder | Produk yang diingatkan saat stok kosong |
| Metode Pembayaran | Kelola metode bayar tersimpan |
| Alamat Tersimpan | Kelola daftar alamat |
| Pengaturan Notifikasi | Toggle notifikasi |
| Saran Produk | Suggest produk baru ke Astro |
| Syarat & Ketentuan | TnC Astro |
| Kebijakan Privasi | Privacy policy |
| Produk Favorit | Favorit / wishlist |
| Tutup Akun | Close account flow |

### 📍 Location
| Screen / Bottom Sheet | Deskripsi |
|----------------------|-----------|
| Location Management | Kelola daftar alamat |
| Location List | Pilih alamat aktif |
| Pin Location | Geser pin ke lokasi yang tepat |
| Address Precision | Konfirmasi presisi alamat |
| Input Location Detail | Isi detail alamat (nama jalan, gedung, dll) |
| Address Details | Bottom sheet detail alamat |
| Enable Location | Bottom sheet minta izin lokasi |

### 🎁 Promo & Rewards
| Screen | Deskripsi |
|--------|-----------|
| Benefit Landing Page (BLP) | Halaman rewards/promo utama (tab Rewards) |
| Voucher List | Daftar promo yang available |
| Flash Sale | Produk flash sale dengan countdown |
| Flexi Combo | Pilih combo produk |
| PWP (Purchase With Purchase) | Tebus murah setelah beli produk tertentu |
| Dynamic Landing Page (DLP) | Halaman landing dinamis (dikonfigurasi backend) |
| Promo / Campaign | Halaman campaign khusus |

### 🏆 Loyalty & Coins
| Screen | Deskripsi |
|--------|-----------|
| Loyalty Page | Astro Club / program loyalitas |
| Astro Balance | Saldo Astro (refund balance, cashback) |
| Milestone Landing Page | Progress milestone reward |

### 💬 Communication
| Screen | Deskripsi |
|--------|-----------|
| Chat | In-app chat dengan CS |
| In-App Call | Call driver/CS dalam app |
| Notification | Pusat notifikasi |

### ⭐ Post-Purchase
| Screen | Deskripsi |
|--------|-----------|
| Rating / Review | Beri rating & review setelah pesanan selesai |
| Add Review | Form tulis review produk |
| Refund | Pengajuan refund |

### 🔐 Auth / Onboarding
| Screen | Deskripsi |
|--------|-----------|
| Getting Started | Onboarding — pilih masuk/daftar |
| Login | Input nomor HP |
| OTP | Verifikasi kode OTP |
| Input Name | Input nama saat daftar baru |
| PIN Setup | Buat PIN baru |
| User Age Check | Verifikasi umur untuk produk 21+ |

### 🔧 Utility
| Screen | Deskripsi |
|--------|-----------|
| WebView | Webview general untuk URL internal/eksternal |
| App Update | Force update screen |
| Maintenance | Maintenance mode |
| Send As Gift | Kirim pesanan sebagai hadiah |

---

## Bottom Sheets vs Full Screen — Pattern

**Full screen push** (punya navigation bar): PDP, Order Detail, Search, Account screens, Payment Status, Location Management, Flash Sale, etc.

**Bottom sheets** (modal dari bawah): Product Form, Voucher List, Payment Method, Send As Gift, Address Confirmation, Loyalty in Cart, Delivery Options, Driver Availability, dll.

**Popups** (center modal): Confirmation dialogs, User Age Check, Address Confirmation critical.

---

## Delivery Type Labels (dari CartConstants)

| Type | Label |
|------|-------|
| Regular | Astro Instant (15 Menit) |
| Same Day | Astro Super (Same Day) |
| Scheduled | Jadwalkan |

---

## Deep Link Patterns

App mendukung deep link untuk: cart, product detail, promo/campaign page, DLP, category. Format: `applink://` prefix internal, URL exteral via WebView.
