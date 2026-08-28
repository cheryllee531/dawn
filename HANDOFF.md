# The Quiet Page — Shopify Theme Merchant & Maintainer Handoff Guide

**Theme**: The Quiet Page (Bespoke Shopify 2.0 Theme)  
**Foundation**: Shopify Dawn v16.0.0  
**Store Niche**: Premium Mindful Stationery, Guided Journals, Desk Objects & Gift Sets  
**Author / Engineering Team**: The Quiet Page Engineering  
**Date**: August 2026  
**Status**: 100% Production Verified & E2E Test Passed  

---

## 1. Executive Summary & Architecture Overview

"The Quiet Page" is an editorial, mindful, and high-performance Shopify 2.0 theme crafted upon Shopify's Dawn architecture. It replaces generic ecommerce tropes with warm tactile aesthetics, serene typography, lay-flat craftsmanship storytelling, and frictionless shopping experiences.

### Key Architectural Pillars:
- **Design Tokens**: Centralized in `assets/quiet-page.css` and `config/settings_data.json` providing warm cream (`#F7F3ED`), soft ivory (`#FFFDF9`), deep charcoal (`#2B2927`), muted terracotta (`#B96F57`), soft clay (`#D9A18E`), warm beige borders (`#E8DED3`), and muted sage (`#AAB2A0`).
- **Typography Scale**: High-contrast pairings of refined serif headings (*Cormorant Garamond* / *Playfair Display*) with crisp sans-serif body (*Inter* / *DM Sans*).
- **11 Modular Shopify 2.0 Liquid Sections**: Rich JSON schemas with full Theme Customizer visual controls, typed blocks, and merchant presets.
- **Cart Subsystem**: Real-time $70 free shipping progress tracker (`snippets/quiet-shipping-threshold.liquid`) and reassurance banner (`snippets/cart-drawer.liquid`).
- **Multi-Page Templates**: Pre-assembled JSON templates for Homepage, Products (with 6 collapsible accordion tabs & cross-sell), Collections (4-col desktop / 2-col mobile), Predictive Search, About, Contact (with studio email `cheryllee531@outlook.com` and order number field), and Store Policies.
- **Pristine Backup Snapshot**: Safe fallback created in `dawn_backup_initial` prior to customizations.

---

## 2. Complete File Inventory

Below is the verified inventory of all newly created and modified theme files:

| File Path | Type | Purpose & Description |
|---|---|---|
| `assets/quiet-page.css` | Asset (CSS) | Master design tokens, typography rules, terracotta buttons, card styles, sticky header, search modal, cart count badge pill, shipping threshold progress bar, and mobile drawer accordion styles. |
| `config/settings_data.json` | Config (JSON) | Color schemes 1–5, typography font assignments, button corner radii (6px), and `cart_type: "drawer"`. |
| `layout/theme.liquid` | Layout (Liquid) | Global HTML wrapper, Google Fonts preconnect, inclusion of `quiet-page.css` after `base.css`, and cart drawer mounting. |
| `sections/header-group.json` | Section Group (JSON) | Header section group with announcement bar ("Free U.S. standard shipping on orders $70+"), sticky header configuration (`on-scroll-up`), and logo alignment. |
| `sections/announcement-bar.liquid` | Section (Liquid) | Top utility bar with $70+ free shipping message default and customizer schema. |
| `sections/contact-form.liquid` | Section (Liquid) | Studio contact form with name, email, order number field (`contact[Order Number]`), message textarea, and `cheryllee531@outlook.com` studio notice. |
| `sections/quiet-hero.liquid` | Section (Liquid) | **Section 1**: Split editorial hero banner with dual CTAs ("Shop Journals", "Explore Gift Sets"), lifestyle media, and padding controls. |
| `sections/quiet-brand-story.liquid` | Section (Liquid) | **Section 2**: Centered editorial brand narrative with quote accent, philosophy text, and "About The Quiet Page" CTA. |
| `sections/quiet-collection-grid.liquid` | Section (Liquid) | **Section 3**: 4-card editorial collection grid (Journals, Notebooks, Creative Supplies, Gift Sets) with subtle link arrows and mobile responsive columns. |
| `sections/quiet-featured-products.liquid` | Section (Liquid) | **Section 4**: 4–8 product grid with comparison pricing, Best Seller tags, and quick-add actions. |
| `sections/quiet-bundle-kit.liquid` | Section (Liquid) | **Section 5**: Curated "Build your quiet kit" split feature with bundled items list, price summary, and dual background styling. |
| `sections/quiet-benefits.liquid` | Section (Liquid) | **Section 6**: 3-column benefit cards for "Thoughtfully curated", "Made for your rhythm", and "Gift-ready moments" with line icons. |
| `sections/quiet-inspiration.liquid` | Section (Liquid) | **Section 7**: 3-card editorial inspiration and blog post showcase with "Read more" links. |
| `sections/quiet-newsletter.liquid` | Section (Liquid) | **Section 8**: Value-driven "A little space in your inbox" email signup with consent checkbox and privacy guarantee. |
| `sections/quiet-image-with-text.liquid` | Section (Liquid) | **Section 9**: Split editorial storytelling feature highlighting artisanal craftsmanship and 120gsm paper quality. |
| `sections/quiet-policy-header.liquid` | Section (Liquid) | **Section 10**: Refined header for legal, shipping, and return policy pages. |
| `sections/quiet-shipping-threshold.liquid` | Section (Liquid) | **Section 11**: Modular section wrapper for shipping threshold calculation and progress bar. |
| `snippets/cart-drawer.liquid` | Snippet (Liquid) | Slide-out cart drawer with dynamic $70 shipping threshold progress bar integration and "Secure checkout. Thoughtful tools for your everyday pages." reassurance banner. |
| `snippets/quiet-shipping-threshold.liquid` | Snippet (Liquid) | Real-time calculation snippet (7000 cents / $70.00 threshold) rendering remaining balance and progress percentage bar. |
| `snippets/cart-icon-bubble.liquid` | Snippet (Liquid) | Cart icon with terracotta live item count badge pill. |
| `templates/index.json` | Template (JSON) | 10-section editorial homepage assembly in exact storytelling sequence with default merchant presets. |
| `templates/product.json` | Template (JSON) | Product page with gallery, pricing, variant pickers, 6 collapsible accordion tabs (Details, Materials, Dimensions, Shipping & Returns, Care, FAQ), and "Pair it with" cross-sells. |
| `templates/collection.json` | Template (JSON) | 4-column desktop / 2-column mobile collection catalog grid with filtering and breadcrumbs. |
| `templates/search.json` | Template (JSON) | Predictive search and catalog results template. |
| `templates/page.about.json` | Template (JSON) | Editorial brand origin and materials showcase template. |
| `templates/page.contact.json` | Template (JSON) | Studio contact template with order number field and `cheryllee531@outlook.com`. |
| `templates/page.policy.json` | Template (JSON) | Policy and legal layout template. |
| `locales/en.default.schema.json` | Locale (JSON) | Schema translations with default announcement text updated to $70+ shipping. |
| `PROJECT.md` | Doc (Markdown) | Master architecture specification, feature inventory, and milestone tracking. |
| `TEST_INFRA.md` | Doc (Markdown) | Test architecture and runner specifications. |
| `TEST_READY.md` | Doc (Markdown) | Automated E2E test suite execution guide. |

---

## 3. Merchant Theme Customizer Guide

All sections and templates are 100% configurable visually within the Shopify Theme Customizer without writing any code.

### 3.1 Global Colors & Typography
1. Open **Shopify Admin > Online Store > Themes > Customize**.
2. Click the **Theme Settings** (gear icon) on the left sidebar:
   - **Colors**: Schemes 1–5 are pre-configured with Quiet Page tokens. Scheme 1 provides Warm Cream background (`#F7F3ED`) with Deep Charcoal text (`#2B2927`).
   - **Typography**: Headings use *Cormorant Garamond* / *Playfair Display*; Body uses *Inter* / *DM Sans*.
   - **Buttons & Cards**: Configured with 6px subtle corner radius.
   - **Cart**: Set to `Drawer` for slide-out cart drawer experience.

### 3.2 Announcement Bar & Sticky Header
1. In the Customizer sidebar under **Header Group**:
   - Click **Announcement bar**: Edit the announcement text (Default: `"Free U.S. standard shipping on orders $70+"`) or add additional announcement slides with rotation speed.
   - Click **Header**: Choose logo position (`middle-left`, `middle-center`, `top-left`, `top-center`), sticky behavior (`on-scroll-up`), and desktop menu type (`dropdown` or `mega-menu`).

### 3.3 Homepage Sections Configuration
The homepage (`templates/index.json`) is arranged in 10 editorial sections. To edit:
1. **Quiet Page Hero**: Update headline, eyebrow, body, primary & secondary button labels/links, and upload high-resolution lifestyle photography.
2. **Centered Brand Story**: Edit philosophy copy and CTA button.
3. **Editorial Collection Grid**: Add or reorder collection cards, assign target collections, custom titles, and preview imagery.
4. **Featured Products**: Select product collection, number of products (4–8), grid columns, and toggle quick-add.
5. **Curated Bundle / Quiet Kit**: Edit kit pricing ($84.00 vs $102.00 compare-at), add or edit included items in the block list, and set featured bundle image.
6. **Three-Column Benefits**: Edit benefit cards (icon, title, description).
7. **Editorial Blog / Inspiration Cards**: Connect your Shopify blog or configure custom static cards with "Read more" links.
8. **Quiet Image With Text**: Adjust split layout ("Image First" vs "Text First"), brand narrative, and CTA button.
9. **Calm Newsletter Signup**: Customize gentle headline, subtext, consent checkbox, and privacy note.
10. **Shipping Threshold Section**: Set threshold amount (default: $70) and custom messaging.

### 3.4 Product Details & 6 Collapsible Tabs
1. Navigate to any Product template in the Customizer:
2. Under **Product Information**, expand each of the 6 collapsible tabs to customize copy:
   - **Details**: Paper weight, page count, lay-flat Smyth-sewn binding.
   - **Materials**: Belgian linen, FSC-certified archival paper, fountain pen testing.
   - **Size & Dimensions**: Exact measurements (A5: 5.8" x 8.3", thickness, weight).
   - **Shipping & Returns**: 1–3 business days processing, $70+ free shipping notice, 30-day return policy.
   - **Care Instructions**: Linen spot-cleaning and storage tips.
   - **FAQ**: Ink compatibility and personalization questions.
3. Under **Complementary Products**, select cross-sell items ("Pair it with").

### 3.5 Cart Drawer & Free Shipping Threshold
- The cart drawer automatically calculates remaining amount to reach $70.00:
  - When under $70: Displays `"You’re $X.XX away from free U.S. standard shipping."` with dynamic terracotta progress bar.
  - When reaching $70+: Displays `"You’ve unlocked free U.S. standard shipping."` with sage filled bar.
- Footer displays the reassurance banner: `"Secure checkout. Thoughtful tools for your everyday pages."`

### 3.6 Contact Page
- Located at `/pages/contact` (`templates/page.contact.json`).
- Includes fields for Name, Email, Order Number (optional), and Message.
- Highlights studio support contact at `cheryllee531@outlook.com` with 1–2 business day response expectation.

---

## 4. Automated E2E Testing & Verification Results

The automated 4-tier test harness in `.agents/test_suite/run_all_tests.ps1` validates the theme across 100+ assertions.

### Execution Results Summary:
| Test Tier | Scope | Total Assertions | Result | Status |
|---|---|---|---|---|
| **Tier 1** | Unit & Feature Coverage (All 35 Features, Tag Balance, Schemas, Templates) | 65 | 65 PASS / 0 FAIL | **100% PASS** |
| **Tier 2** | Boundary & Corner Cases ($0 to $10,000 cart math, Schema types, Breakpoints) | 22 | 22 PASS / 0 FAIL | **100% PASS** |
| **Tier 3** | Cross-Feature Combinations (Header sync, CSS order, Tab mappings, Cart integration) | 7 | 7 PASS / 0 FAIL | **100% PASS** |
| **Tier 4** | Real-World Customer Workloads (5 Full simulated end-to-end shopping journeys) | 6 | 6 PASS / 0 FAIL | **100% PASS** |
| **GRAND TOTAL** | **Complete Suite** | **100** | **100 PASS / 0 FAIL** | **100% PASS** |

To re-run tests anytime:
```powershell
powershell -ExecutionPolicy Bypass -File ".agents\test_suite\run_all_tests.ps1"
```

---

## 5. Maintenance & Developer Extension Guide

- **Adding New Sections**: Create `sections/quiet-<name>.liquid` following the established BEM and design token conventions (`var(--color-quiet-...)`, `var(--font-quiet-...)`, `var(--quiet-radius-base)`).
- **Extending Design Tokens**: Modify `:root` variables in `assets/quiet-page.css`.
- **Modifying Shipping Threshold**: Update `shipping_threshold_cents` (default: `7000`) in `snippets/quiet-shipping-threshold.liquid` and `sections/quiet-shipping-threshold.liquid`.

---
*The Quiet Page Shopify Theme is complete, verified, and ready for merchant publishing.*