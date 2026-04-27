# Screen: Search — Initial State (Focus)

**File:** `9xuDPzF47hOTP3KuYwbWVT` | **Node:** `7504:3779` → child "Initial State Saerch - Focus"
**Dimensi:** 360×800px | **Platform:** iOS (reference)

---

## Anatomi Layar (atas ke bawah)

```
[ Status Bar iOS — 44px ]
[ Header SearchBox — 56px ]         ← Type=SearchBox, state=Focus (keyboard aktif)
─────────────────────────────────────
[ All Search Recent — scrollable ]
  ├── Riwayat Pencarian (label + list keyword) — gap=16px
  ├── Pencarian Populer (label + chip/keyword list) — gap=12px
  └── Kategori / Suggestions — gap=12px
[ Divider 8px ]                     ← pemisah sebelum keyboard
─────────────────────────────────────
[ Keyboard iOS — 291px ]            ← muncul karena SearchBox dalam state Focus
```

---

## Detail Layout

- Total Top Bar: **100px** (44px Status Bar + 56px Header SearchBox)
- Konten search recent: padding **16px kiri-kanan**, gap antar grup **24px**
- Divider 8px memisahkan konten dari keyboard
- Keyboard iOS height: 291px

---

## State: Search Focus

Ini adalah state ketika user tap pada search box:
- Keyboard muncul di bawah
- Search box dalam kondisi aktif/focus
- Menampilkan: riwayat pencarian + pencarian populer + kategori

---

## Komponen DS yang Dipakai

- `Status Bar → iOS`
- `Top Bar → Type=SearchBox` (state focus)
- `Divider 8px`
- `Keyboard → iOS, Default`

---

## Rules Khusus Halaman Ini

- Tidak ada Bottom Nav
- Tidak ada Sticky Amount
- Seluruh area di bawah header: konten search history yang scrollable
- Saat keyboard aktif: konten di-push ke atas, keyboard fixed di bawah
- Padding konten: **16px** kiri-kanan
