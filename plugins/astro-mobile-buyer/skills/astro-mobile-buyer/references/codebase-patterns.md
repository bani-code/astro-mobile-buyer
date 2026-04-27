# Codebase Patterns — astro-mobile-web

Source: `/Users/astriharbaniansyah/Downloads/astro-mobile-web-production`

---

## Monorepo Structure

```
astro-mobile-web-production/
├── apps/
│   ├── astro-mobile-web/   ← Next.js 14 PWA (primary — ini yang utama)
│   └── core-app/           ← Vite + React 19 (WebView: invoice, chat)
├── scripts/
└── pnpm-workspace.yaml
```

---

## Tech Stack (astro-mobile-web — Primary App)

| Aspect | Value |
|---|---|
| Framework | Next.js 14 (App Router) |
| Language | TypeScript 5 (strict) |
| Package Manager | pnpm (always pnpm, never npm/yarn) |
| UI Library | MUI v5 + `@astronautsid/wpe-astro-ui` |
| Icons | `@astronautsid/wpe-icons` |
| Styling | Emotion (CSS-in-JS), sx prop — **NO Tailwind** |
| State | Zustand v4 + Immer |
| Data Fetching | TanStack React Query v5 + Axios |
| Forms | React Hook Form + Zod |
| i18n | next-intl (default locale: `id`, timezone: Asia/Jakarta) |

---

## Design System Packages

```ts
@astronautsid/wpe-astro-ui   // DS components (Box, Button, Typography, TextInput, Skeleton...)
@astronautsid/wpe-icons      // Icon library
@astronautsid/wpe-utils      // Utility functions
```

---

## Import Pattern (WAJIB diikuti)

### Import DS component — selalu per path, BUKAN barrel import

```ts
// ✅ Benar
import { Box } from '@astronautsid/wpe-astro-ui/components/atoms/Box'
import type { BoxPropsType } from '@astronautsid/wpe-astro-ui/components/atoms/Box'
import { Button } from '@astronautsid/wpe-astro-ui/components/atoms/Button'
import { Typography } from '@astronautsid/wpe-astro-ui/components/atoms/Typography'
import { TextInput } from '@astronautsid/wpe-astro-ui/components/atoms/TextInput'
import { Skeleton } from '@astronautsid/wpe-astro-ui/components/atoms/Skeleton'

// ❌ Salah — barrel import
import { Box, Button } from '@astronautsid/wpe-astro-ui'
```

### Import Icon

```ts
import { Search } from '@astronautsid/wpe-icons'
import { ShoppingCart } from '@astronautsid/wpe-icons'
```

### Import order — 3 grup, satu baris kosong antar grup

```ts
// Grup 1: Node modules
import { useState } from 'react'
import { useQuery } from '@tanstack/react-query'

// Grup 2: Bare imports (src/ baseUrl)
import { getCart } from 'utils/apiList/lite/cart'
import ErrorScreen from 'components/ErrorScreen/ErrorScreen'
import { ASSET_PREFIX } from 'config/constants'

// Grup 3: Relative imports
import useProductPricing from './hooks/useProductPricing'
import ProductCardLabel from './ProductCardLabel'
```

---

## Styling (Emotion + MUI sx)

### Gunakan `useTheme` untuk nilai dinamis/token-aware

```ts
import { useTheme } from '@astronautsid/wpe-astro-ui/theme'

const theme = useTheme()

// Contoh penggunaan di sx prop:
sx={{ backgroundColor: theme.palette.bgColor.light }}
sx={{ color: theme.palette.textColor.primaryDark }}
sx={{ borderColor: theme.palette.strokeColor.subtle }}
```

### Token palette mapping (theme.palette)

| Figma Token | theme.palette |
|---|---|
| BackgroundColor/Light | `theme.palette.bgColor.light` |
| BackgroundColor/Disable | `theme.palette.bgColor.disabled` |
| BackgroundColor/LightGrey | `theme.palette.bgColor.lightGrey` |
| TextColor/PrimaryDark | `theme.palette.textColor.primaryDark` |
| TextColor/SecondaryDark | `theme.palette.textColor.secondaryDark` |
| TextColor/Disable | `theme.palette.textColor.disable` |
| TextColor/Link | `theme.palette.textColor.link` |
| TextColor/Error | `theme.palette.textColor.error` |
| TextColor/PrimaryLight | `theme.palette.textColor.primaryLight` |
| IconColor/DefaultDark | `theme.palette.iconColor.defaultDark` |
| IconColor/Light | `theme.palette.iconColor.light` |
| StrokeColor/Subtle | `theme.palette.strokeColor.subtle` |
| StrokeColor/Active | `theme.palette.strokeColor.active` |

### Gunakan token statis untuk konstanta desain

```ts
import { color } from '@astronautsid/wpe-astro-ui/tokens/color'

sx={{ color: color.neutral900 }}
```

Available token categories:
- `tokens/color` — color palette
- `tokens/spacing` — spacing scale
- `tokens/radii` — border radius
- `tokens/elevation` — shadows
- `tokens/text` — typography
- `tokens/breakpoints` — responsive breakpoints

---

## Komponen UI

### Gunakan `<Box>` bukan `<div>`

```tsx
// ✅ Benar
import { Box } from '@astronautsid/wpe-astro-ui/components/atoms/Box'
<Box display="flex" gap="8px" padding="16px">...</Box>

// ❌ Salah
<div style={{ display: 'flex', gap: '8px', padding: '16px' }}>...</div>
```

### Typography

```tsx
import { Typography } from '@astronautsid/wpe-astro-ui/components/atoms/Typography'

<Typography variant="body1" color={theme.palette.textColor.primaryDark}>
  Nama Produk
</Typography>
```

### Skeleton (loading state)

```tsx
import { Skeleton } from '@astronautsid/wpe-astro-ui/components/atoms/Skeleton'

<Skeleton width="42px" height="40px" variant="rounded" sx={{ borderRadius: '999px' }} />
```

---

## Naming Conventions

| Type | Convention | Contoh |
|---|---|---|
| Component folder | PascalCase | `ProductCard/`, `BottomNavigation/` |
| Component file | PascalCase | `ProductCard.tsx`, `Footer.tsx` |
| Prop types | `<Name>PropsType` | `ProductCardPropsType` |
| Hooks | camelCase, prefix `use` | `useProductPricing.ts` |
| Utilities | camelCase | `currencyFormat.ts`, `noop.ts` |
| Stores | camelCase | `cart.ts`, `auth.ts` |
| Tests | co-located, `.test.ts` | `ProductCard.test.ts` |

---

## Project Structure (astro-mobile-web)

```
src/
  app/                    # Next.js App Router
    (auth)/               # Auth-gated routes
    (home)/               # Homepage
    (product)/            # Product pages (PDP)
    (payment)/            # Checkout/payment
    (categoryandcatalogue)/
    account/              # User account & profile
    cart/                 # Cart
    order/                # Orders
    search/               # Search results
    discovery/            # Promo/brand discovery
    login/                # Login
    register/             # Register
    api/                  # API routes (server-side)
  components/             # 52+ shared UI components
    AstroUI/              # Wrapper components (Checkbox, Chip, Dialog, Divider...)
    BottomSheet/
    BottomNavigation/
    CartIncrement/
    GlobalSearchBar/
    Image/                # Custom image wrapper (JANGAN pakai next/image langsung)
    ...
  config/                 # Constants, API service config, storage keys
  hooks/                  # Custom React hooks (use<Feature>.ts)
  store/                  # Zustand stores (cart, auth, location, user, productDetail)
  styles/                 # Global CSS (max-width: 430px mobile)
  types/                  # Shared TypeScript types
  utils/                  # Utility functions
  messages/               # i18n (id.json + en.json)
```

---

## Code Style (Prettier enforced)

- **No semicolons**
- **Single quotes** (JSX: double quotes)
- **Trailing commas**
- **2-space indent**, no tabs
- **100 char print width**
- Prefer `type` over `interface`
- Never `any` — gunakan `unknown`, generics, atau type assertion

---

## Aturan Penting

| Rule | Detail |
|---|---|
| Jangan pakai `<div>` | Selalu `<Box>` dari wpe-astro-ui |
| Jangan barrel import | Selalu import per path komponen |
| Jangan pakai `next/image` langsung | Gunakan `components/Image` |
| Jangan `window.open` | App jalan di native WebView |
| Storage keys | Pakai konstanta dari `config/localStorageKeys.ts` / `config/sessionStorageKeys.ts` |
| Image fallback | `<Image fallbackImageSrc={...} />` |
| Server Components | Default di Next.js App Router; tambah `'use client'` hanya jika perlu |

---

## Loading State Pattern

### Skeleton (per-section)

```tsx
import { Skeleton } from '@astronautsid/wpe-astro-ui/components/atoms/Skeleton'
import { Box } from '@astronautsid/wpe-astro-ui/components/atoms/Box'

const ProductListSkeleton = () => (
  <Box display="flex" gap="8px">
    {[...Array(4)].map((_, i) => (
      <Skeleton key={i} width="110px" height="110px" variant="rounded" />
    ))}
  </Box>
)

// Penggunaan:
const { data, isLoading } = useQuery({ ... })
if (isLoading) return <ProductListSkeleton />
return <ProductList data={data} />
```

---

## i18n

```ts
import { useTranslations } from 'next-intl'

const t = useTranslations('cart')         // feature namespace
const tGlobal = useTranslations('global') // shared strings

t('checkoutButton')
tGlobal('errorMessage')
```

- Default locale: `id`
- Translation files: `src/messages/common/id.json` + `en.json`
- **Selalu update keduanya** saat menambah string baru
- Jangan hardcode UI string — tambahkan ke messages dulu

---

## Webview / Native Integration

App berjalan di dalam React Native WebView. Gunakan `postMessage` dari `utils/webview/postMessage`:

```ts
import { postMessage, ActionEnum, NativePageEnum } from 'utils/webview/postMessage'

postMessage.navPop()                              // back
postMessage.navPush({ page: NativePageEnum.Home }) // navigate ke home native
postMessage.navToHome()                           // reset nav stack ke home
```

Jangan gunakan `window.open` atau `<a target="_blank">`.
