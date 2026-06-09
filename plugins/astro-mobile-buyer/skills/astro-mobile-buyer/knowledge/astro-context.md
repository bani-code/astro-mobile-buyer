# Astro Company Context — Quick Reference
> Source: internal docs + session history | Last updated: March 2026
> Untuk: designer yang perlu memahami konteks bisnis saat membaca PRD atau merancang UX

---

## Apa itu Astro?

PT Astro Technologies Indonesia — **Indonesia's #1 Quick Commerce app.**
Tagline: *"Anything You Need, Fast."*
Pengiriman secepat 15 menit, 24/7, di seluruh Jabodetabek.

- 15.000+ produk, 57+ kategori
- Fully vertically integrated — punya sendiri inventory, fulfillment, dan last-mile delivery
- Dark stores (hub): radius 2–3km, 24/7, zona ambient/chiller/freezer
- **Digital payments only** (e-wallet, virtual account)
- **Area layanan: Jabodetabek saja**

---

## Stakeholders — Siapa yang Pakai Apa

| Stakeholder | Tool/Channel | Bahasa | Catatan |
|-------------|-------------|--------|---------|
| **Buyer** (customer) | Astro App (mobile) | Bahasa Indonesia | 85% perempuan, 25–35, Jabodetabek |
| **Mitra** (frontline: Driver, Picker, Packer, IC, QA, Kitchen Crew) | Crew App, SEUIC scanner, WMS | Bahasa Indonesia | Bukan karyawan langsung — tone: jelas, hormat, no jargon |
| **Astronauts** (internal staff/HQ) | Admin Web, dashboard internal | English | |
| **Vendor** | — | Mixed | Supplier, Advertiser, White-label, Staffing |

---

## Terminologi yang Sering Muncul di PRD

| Term | Artinya |
|------|---------|
| Astronauts | Karyawan HQ |
| Mitra | Frontline workers — **jangan sebut "MP" atau "Manpower"** |
| Hub / Dark Store | Pusat fulfillment |
| Buyer | Customer (jangan sebut "user" saja di PRD Astro) |
| SO | Sales Order |
| PO | Purchase Order |
| GRN | Goods Receipt Note |
| DCC | Daily Cycle Count |
| SLOC | Storage Location |
| Koli | Packaged unit |
| WMS | Warehouse Management System |
| Crew App | Aplikasi mobile untuk Mitra |
| SEUIC | Scanner barcode yang dipakai Mitra |
| Jaminan Segar | Freshness guarantee (brand promise) |
| P0 | Must-have, blocks launch |
| P1 | Needed for full adoption / scale |
| P2 | Nice-to-have, bisa defer |
| RAG | Red / Amber / Green (status inisiatif) |
| PWP | Purchase With Purchase (promo mechanic) |
| OOS | Out of Stock |
| ARPU | Average Revenue Per User |
| AOV | Average Order Value |
| CM1/CM2 | Contribution Margin 1 / 2 |
| GMV | Gross Merchandise Value |

---

## Order Flow

```
Customer order di app
    ↓
Hub menerima order
    ↓
Picker (ambil barang dari rak)
    ↓
Packer (kemas order)
    ↓
Driver (antar ke customer)
    ↓
Customer menerima dalam ~15 menit
```

---

## Product Domains (yang sering muncul di PRD)

| Domain | Fungsi |
|--------|--------|
| **WMS** | Warehouse Management System — operasional gudang |
| **Crew App** | Mobile tool untuk Mitra (picking, packing, delivery) |
| **Admin Web** | Dashboard internal untuk Astronauts |
| **Buyer App** | Aplikasi utama customer (iOS & Android) |
| **HRIS** | HR platform internal |
| **ERP** | Enterprise operations |
| **ATS** | Applicant Tracking System (hiring) |
| **IMS** | Inventory Management System |
| **Approval Engine** | Configurable internal workflow approval |

---

## Tech Stack

| Layer | Teknologi |
|-------|-----------|
| Mobile Android | Kotlin |
| Mobile iOS | Swift |
| Frontend (admin web) | TypeScript + React |
| Backend | Go |
| Middleware | Kong |
| Message Queue | Google Cloud Pub/Sub |
| Cache | Redis |
| Database | PostgreSQL |

---

## Leadership

| Nama | Role |
|------|------|
| Vincent Tjendra | CEO |
| Harvey Tjiupek | SVP — Head of Product, Data, and Supply Chain |
| Yosua Wasita | AVP — Head of Product Buyer & Platform |
| Andra Wisata | AVP — Head of Product WMS, HRIS, ERP |
| Vandhi Leofatwa | AVP — Head of Product Fulfillment, Commercial, SCMS |

---

## Mission & Prinsip Desain

- **Mission:** Make people's lives simpler and easier
- **Vision:** Most loved company by customers
- **CX adalah primary success metric** — setiap keputusan design harus bisa dijawab dengan "apakah ini membuat experience buyer/mitra lebih baik?"
- **Speed dan reliability non-negotiable** — terutama di moments kritis (checkout, pembayaran, SOS orders)
- **Mitra adalah ujung tombak brand promise** — experience Mitra di Crew App/WMS berdampak langsung ke delivery experience buyer
