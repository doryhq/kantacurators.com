# Shopify Migration Guide

This site was built so migrating to Shopify later is a data import, not a rebuild.

## 1. Product data → Shopify Products

`data/products.json` already mirrors Shopify's product shape. Map fields like this when you're ready:

| This site (`products.json`) | Shopify product CSV column |
|---|---|
| `id` (e.g. `TT1`) | Handle / SKU |
| `name` | Title |
| `category` | Product Type / Collection |
| `subcategory` | Tag or Collection |
| `description` | Body (HTML) |
| `tags` | Tags |
| `occasion` | Tags or a custom metafield |
| `image` | Image Src |

Shopify's CSV import (Admin → Products → Import) accepts a flat CSV — a short Python/Sheets script can convert `products.json` into that format in minutes.

## 2. Product images → Shopify Media

Upload everything in `images/products/` via Admin → Content → Files, or directly during CSV import (Shopify accepts public image URLs or a zip upload with matching filenames).

**Before migrating:** replace the 36 "Photo Coming Soon" placeholders with real photos first — see `Kanta_Curators_Image_Match_Review.xlsx` for the list. Publishing placeholder images as real Shopify product photos would be a step backward.

## 3. Pages → Shopify theme

- `products.html` → a Shopify collection/catalog template (Liquid), using Shopify's native product-grid + metafields instead of `data.js`.
- `index.html`, `about.html`, `contact.html`, `follow-us.html` → Shopify custom pages, built with the theme editor or as Liquid templates. The CSS in `css/styles.css` is plain CSS (no framework), so it can be pasted into a Shopify theme's `assets/theme.css` largely as-is.

## 4. No cart, no pricing → still possible on Shopify

Two options once you're on Shopify:
- Keep it inquiry-only: hide "Add to cart" and price via theme customization, keep the WhatsApp/Email buttons (same wa.me / mailto links work identically in Liquid).
- Or turn pricing back on and let Shopify's native cart/checkout take over — the product data already has a `Price (INR)` column in the source spreadsheet ready to populate whenever you're ready to sell directly.

## 5. Forms → Shopify + email tooling

- Contact form → Shopify's built-in contact form template, or connect to Klaviyo/Mailchimp for the newsletter signup (currently a front-end-only placeholder on this static site — it doesn't yet send anywhere).
- WhatsApp links transfer as-is, or swap in a Shopify WhatsApp app for richer features (catalog sharing, automated replies).

## 6. Instagram feed

Currently a static grid of real product photos linking out to your profile. On Shopify, install an Instagram feed app (free tier available on most) to pull a live feed automatically.

## 7. Analytics

Add Shopify Analytics (built-in) and a Google Analytics / GA4 snippet — there's no analytics wired up on this static site yet, since that requires an account + tracking ID from you.

## Checklist

- [ ] Real photos in place for all 100 products (36 currently placeholders)
- [ ] Product data (CSV) imported into Shopify Products
- [ ] Product images uploaded to Shopify Media
- [ ] Page content moved into Shopify theme (Liquid) or custom pages
- [ ] Contact form connected (Shopify native, or Klaviyo/Formspree)
- [ ] Newsletter signup connected to an actual email service
- [ ] WhatsApp links verified in the new theme
- [ ] Instagram feed app installed (optional, replaces static grid)
- [ ] Google Analytics / Shopify Analytics added
- [ ] Domain (kantacurators.com) pointed at Shopify
