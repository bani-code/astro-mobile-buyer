# Design Token System — Astro Buyer iOS (UniverseUI)
> Source: astro-buyer-ios/Modules/Design/UniverseUI/Sources/UniverseUI/Resources/JSON/tokens.json
> Last updated: June 2026
> Ini adalah token system yang dipakai di iOS app — gunakan sebagai cross-reference dengan libraries.md Figma

---

## Naming System

Token di iOS pakai **naming convention berbeda dari Figma Astro Mobile Buyer DS**.
Figma DS: `BackgroundColor/Light`, `TextColor/PrimaryDark` (slash separator, Title Case)
iOS tokens: `bgColor.light`, `textColor.primaryDark` (camelCase, dot separator)

Mapping di bawah ini menghubungkan keduanya.

---

## Color Scale — Global Palette

### Primary (Galaxy Blue)
| Token Name | Hex | Note |
|-----------|-----|------|
| `primary.galaxy-8` | `#246EE5` | **Primary baseline** — main brand color |
| `primary.galaxy-9` | `#2063CE` | Slightly darker primary |
| `primary.galaxy-10` | `#1D58B7` | Dark primary |
| `primary.galaxy-11` | `#194DA0` | Button hover |
| `primary.galaxy-13` | `#123773` | Button selected/pressed |
| `primary.galaxy-7` | `#669AED` | Light primary |
| `primary.galaxy-3` | `#BDD4F7` | Outline button hover bg |
| `primary.galaxy-2` | `#D3E2FA` | Very light primary |
| `primary.galaxy-1` | `#E9F1FC` | Lightest primary tint |

### Secondary (Nebula Red)
| Token Name | Hex | Note |
|-----------|-----|------|
| `secondary.nebula-8` | `#FF1E00` | **Secondary baseline** — error/urgent red |
| `secondary.nebula-11` | `#B31500` | Dark red |
| `secondary.nebula-3` | `#FFBCB3` | Light red bg |
| `secondary.nebula-1` | `#FFE9E6` | Lightest red tint |

### Neutral
| Token Name | Hex | Note |
|-----------|-----|------|
| `neutral.neutral-10` | `#212121` | **Neutral baseline** — primary dark text |
| `neutral.neutral-1` | `#ffffff` | White |
| `neutral.special` | `#fafafa` | Off-white / disabled bg |
| `neutral.neutral-2` | `#e9e9e9` | Light grey / button disabled |
| `neutral.neutral-3` | `#d3d3d3` | Stroke default |
| `neutral.neutral-6` | `#909090` | Icon default, secondary text |
| `neutral.neutral-7` | `#7A7A7A` | Grey dark |
| `neutral.neutral-8` | `#646464` | Secondary text |

---

## Semantic Tokens — Background Colors

| iOS Token | Figma Token (approx) | Resolved Hex | Usage |
|-----------|---------------------|-------------|-------|
| `bgColor.light` | `BackgroundColor/Light` | `#ffffff` | Page & card background |
| `bgColor.disable` | `BackgroundColor/Disable` | `#fafafa` | Disabled state bg |
| `bgColor.primary` | `BackgroundColor/Primary` | `#246EE5` | Primary brand bg |
| `bgColor.secondary` | `BackgroundColor/Secondary` | `#FF1E00` | Secondary/error bg |
| `bgColor.lightPrimary` | `BackgroundColor/LightPrimary` | `#E9F1FC` | Soft primary tint |
| `bgColor.lightSecondary` | `BackgroundColor/LightSecondary` | `#FFE9E6` | Soft red tint |
| `bgColor.lightGrey` | `BackgroundColor/LightGrey` | `#e9e9e9` | Section separator |
| `bgColor.dark` | `BackgroundColor/Dark` | `#212121` | Dark mode bg |
| `bgColor.green` | `BackgroundColor/Green` | *(sys.green.gr-8)* | Success bg |
| `bgColor.lightGreen` | `BackgroundColor/LightGreen` | *(sys.green.gr-1)* | Light success tint |
| `bgColor.red` | `BackgroundColor/Red` | *(sys.red.rd-8)* | Error bg |
| `bgColor.lightRed` | `BackgroundColor/LightRed` | *(sys.red.rd-1)* | Light error tint |
| `bgColor.orange` | `BackgroundColor/Orange` | *(sys.orange.or-8)* | Warning bg |
| `bgColor.lightOrange` | `BackgroundColor/LightOrange` | *(sys.orange.or-1)* | Light warning tint |
| `bgColor.yellow` | — | *(qd.yellow.yl-8)* | In-progress bg |
| `bgColor.lightYellow` | — | *(qd.yellow.yl-1)* | Light in-progress tint |
| `bgColor.lightBlue` | — | `#E9F1FC` | Info tint (same as lightPrimary) |
| `bgColor.lightCyan` | — | *(qd.cyan.cy-1)* | Cyan tint |
| `bgColor.lightPurple` | — | *(qd.purple.pr-1)* | Purple tint |
| `bgColor.lightMagenta` | — | *(qd.magenta.mg-1)* | Magenta tint |

---

## Semantic Tokens — Button Colors

| State | Primary Button | Secondary Button |
|-------|---------------|-----------------|
| Default | `#246EE5` (galaxy-8) | `#FF1E00` (nebula-8) |
| Hover | `#194DA0` (galaxy-11) | `#B31500` (nebula-11) |
| Selected | `#123773` (galaxy-13) | `#991200` (nebula-13) |
| Disabled | `#e9e9e9` (neutral-2) | `#e9e9e9` (neutral-2) |
| Outline default | `#246EE5` | `#FF1E00` |
| Outline hover bg | `#BDD4F7` (galaxy-3) | `#FFBCB3` (nebula-3) |
| Outline disabled | *(strokeColor.default)* | *(strokeColor.default)* |

---

## Component Library — UniverseUI

Komponen yang ada di `Modules/Design/UniverseUI` (iOS source of truth untuk nama komponen):

| iOS Component | Nama di Figma DS | Keterangan |
|---------------|-----------------|------------|
| `Button.swift` | Button | Primary, secondary, outline, ghost |
| `AstroBadges.swift` | Label/Badge | Status badge, color variants |
| `AstroCheckbox.swift` | Checkbox | Standard checkbox |
| `AstroCountdown.swift` | Countdown | Timer countdown / count-up |
| `AstroLabel.swift` | Label | Text label |
| `AstroToggle.swift` / `CustomToggle.swift` | Toggle | Switch toggle |
| `AstroToolTip.swift` | Tooltip | Tooltip overlay |
| `AstroHeaderNavigation.swift` | TopBar | Navigation bar / header |
| `AlertView.swift` | Alert | Inline alert banner |
| `BottomSheetViewController.swift` | BottomSheet | Modal dari bawah |
| `CarouselIndicator.swift` / `CarouselIndicatorV2.swift` | CarouselIndicator | Dot indicator carousel |
| `ChipCollectionViewCell.swift` | Chips | Filter/tag chip |
| `CounterView.swift` | Counter | Quantity +/- stepper |
| `FloatTextField.swift` | TextInput | Text field dengan floating label |
| `TextArea.swift` | TextArea | Multiline text field |
| `SearchTextField.swift` | Search | Search input |
| `SnackBarView.swift` / `ToasterModifier.swift` | Snackbar | Toast notification |
| `OverlayView.swift` | Overlay | Full-screen backdrop |
| `PopupViewController.swift` | Popup/Dialog | Center modal dialog |
| `TickerContentView.swift` | Ticker | Scrolling ticker/marquee |
| `ASNavigation.swift` | Navigation | Navigation component |
| `AstroLottie.swift` | — | Lottie animation wrapper |
| `ShimmerView` *(referenced)* | Shimmer | Loading skeleton |

---

## Features di App (dari Features directory)

Feature yang ada = screen/flow yang perlu di-cover saat design:

**Core Features (selalu ada):**
Account, Auth (Login/OTP/PIN), Cart, Category, Home, Location, Main/TabBar, Notification, Order, OrderDetail, Payment, ProductDetail, Search

**Promo & Monetization:**
FlashSale, FlexiCombo, PWP, Promo/Voucher, BulkPurchase, PackSizeBMSM, BenefitLandingPage, DynamicLandingPage, VoucherGimmick

**Loyalty & Engagement:**
AstroBalance, Loyalty, Milestone, Referral, ReferralMission, Rating, Review

**Utility:**
Chat, LiveTrack, MediaUploader, Onboarding/GettingStarted, AppUpdate, Reorder, SendAsGift, WebView, Refund, EditAccount, SeeAllProductAndFavorite, ProductSuggestion, ProductForm, ProductModifier, ProductVariant, AllCategory, AppMenuShortcuts

**Eksperimen / Revamp (feature flags):**
Direktori `Revamp/` — fitur yang sedang dalam proses revamp/eksperimen. Termasuk: InAppCall, Milestone revamp, Product revamp.

---

## Remote Config / Feature Flags yang Relevan

Feature flags yang menentukan UI behavior (dari RemoteConfig files):

| Flag Key | Effect |
|----------|--------|
| Tab bar variant | `initialTabs` vs `defaultTabs` vs `categoryTabs` — menentukan bottom nav |
| `RemoteConfigNewArchitecture` | Switch ke arsitektur baru per feature |
| `rc_voucher_gimmick_slider_interval` | Interval slider voucher gimmick |
| `rc_milestone_confetti_url` | URL konfetti milestone |
| `RemoteConfigCartTicker` | Ticker di cart |
| `RemoteConfigStreamCapabilities` | Kemampuan stream (chat/call) |
| `RemoteConfigDownloadInvoice` | Download invoice feature |
| `RemoteConfigUnfinishedKeyword` | Keyword search yang belum selesai |

> **Implikasi untuk design:** Tab bar layout bisa berbeda tergantung experiment. Selalu design untuk default 5-tab layout kecuali PRD spesifik menyebut variant lain.
