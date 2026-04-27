# Sample Data — Produk Astro

Data nyata dari Google Spreadsheet Astro product catalog.
CDN: `image.astronauts.cloud` (production)

---

## Cara Pakai Image di Figma (via upload_assets MCP)

`figma.createImageAsync()` TIDAK didukung di MCP environment. Gunakan workflow `upload_assets` sebagai gantinya.

### Workflow Upload Image ke Node Figma

```
Step 1: Build semua frames di Figma → return node IDs tiap image frame
Step 2: Untuk tiap product card image node:
        a. Call upload_assets dengan fileKey + nodeId image frame → dapat upload URL
        b. Download image dari Astro CDN (curl ke /tmp/img.jpg)
        c. POST raw bytes ke upload URL dengan Content-Type: image/jpeg
        d. Image otomatis masuk sebagai fill ke node tersebut
```

### Kode referensi (di Figma script — bukan upload_assets)

```js
// Saat build frames, JANGAN pakai createImageAsync
// Biarkan image frame kosong dengan fill abu-abu dulu:
const imageFrame = figma.createFrame()
imageFrame.resize(cardWidth, cardWidth)
imageFrame.clipsContent = true
imageFrame.fills = [{ type: 'SOLID', color: { r: 0.93, g: 0.93, b: 0.93 } }]
// Return nodeId-nya → lalu upload_assets akan mengisinya
return { imageNodeId: imageFrame.id }
```

---

## Sample Products (dari Google Spreadsheet)

Spreadsheet: `https://docs.google.com/spreadsheets/d/1P-lVVeAR-1scxgyLr-qMO4mYvJSUrXQX8G-7g0qKB34`

```js
const ASTRO_SAMPLE_PRODUCTS = [
  {
    name: 'Freeze Dried Fruit Strawberry Astro Goods 20gram',
    price: 'Rp29.000',
    priceOriginal: 'Rp32.500',
    discount: '8%',
    rating: 4.9,
    packSize: '20gram',
    imageUrl: 'https://image.astronauts.cloud/product-images/2025/1/astrogoodsstroberi_1bf4b59e-d13c-43b7-b6c4-fae233e26839_900x900.jpg',
  },
  {
    name: 'Garlic Blaze Chili Oil Astro Goods 150ml',
    price: 'Rp41.400',
    priceOriginal: 'Rp45.000',
    discount: '8%',
    rating: 4.7,
    packSize: '150ml',
    imageUrl: 'https://image.astronauts.cloud/product-images/2025/8/GarlicBlazenewsticker1_c61a8406-a7dc-4525-b1b9-c642075f4e46_900x900.jpg',
  },
  {
    name: 'Gourmet Popcorn Sweet & Salty Astro Goods 50gram',
    price: 'Rp22.698',
    priceOriginal: 'Rp23.400',
    discount: '3%',
    rating: 4.8,
    packSize: '50gram',
    imageUrl: 'https://image.astronauts.cloud/product-images/2024/7/sweetsalty1_faa2896f-1127-4c7c-9317-153fc73cfe0c_900x900.jpg',
  },
  {
    name: 'Setra Ramos Beras Premium Astro Goods 5kg',
    price: 'Rp74.593',
    priceOriginal: 'Rp76.900',
    discount: '3%',
    rating: 4.9,
    packSize: '5kg',
    imageUrl: 'https://image.astronauts.cloud/product-images/2025/5/BerasPremiumSetraRamosAstroGoodsRice5kga20bc5adc4ad4b7cabed237e0a2f803c900x900removebgpreview_2e1e0a0a-615c-46a1-84a7-a767088e43cd_900x900.png',
  },
  {
    name: 'Sourdough Astro Goods x BRAUD 500gram',
    price: 'Rp38.790',
    priceOriginal: 'Rp43.100',
    discount: '10%',
    rating: 4.7,
    packSize: '500gram',
    imageUrl: 'https://image.astronauts.cloud/product-images/2025/5/SourdoughFullBraud1e75109ca8ef4493f8401f4c25d857a7c900x900removebgpreview_871fa4b2-0e9b-4e27-9a8f-d140ca73d0ae_900x900.png',
  },
  {
    name: 'Basreng Original Astro Goods 100gram',
    price: 'Rp17.100',
    priceOriginal: 'Rp19.000',
    discount: '10%',
    rating: 4.9,
    packSize: '100gram',
    imageUrl: 'https://image.astronauts.cloud/product-images/2025/8/BasrengOriginal1_eb014c39-7d90-497b-86b6-b328e406c29d_900x900.jpg',
  },
]
```

---

## CDN URL Pattern (Production)

Format URL image produk Astro:
```
https://image.astronauts.cloud/product-images/{YYYY}/{MM}/{ProductName}_{uuid}_{WxH}.{ext}
```

| Segment | Keterangan |
|---|---|
| `image.astronauts.cloud` | CDN production |
| `{YYYY}/{MM}` | Tahun dan bulan upload |
| `{ProductName}` | Nama produk tanpa spasi |
| `{uuid}` | UUID unik per gambar |
| `{WxH}` | Dimensi (biasanya `900x900`) |
| `.ext` | `jpg` atau `png` |

---

## Aturan Penggunaan dalam Design Generation

1. **JANGAN pakai `figma.createImageAsync()`** — tidak didukung di MCP
2. **Gunakan `upload_assets` MCP tool** untuk upload image ke node Figma setelah frame dibuat
3. **Workflow 2 tahap:**
   - Tahap 1: Build semua frames → return semua image node IDs
   - Tahap 2: Download tiap image → upload ke Figma via `upload_assets` dengan `nodeId`
4. **Rotate produk secara siklus** — `ASTRO_SAMPLE_PRODUCTS[i % ASTRO_SAMPLE_PRODUCTS.length]`
5. **Gunakan nama & harga asli** — bukan "Product Name" atau "Rp0"
6. **Semua produk punya diskon** — tampilkan harga coret + label diskon %
