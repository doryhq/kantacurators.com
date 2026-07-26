# Kanta Curators Website

A 5-page, mobile-first, inquiry-only site for **www.kantacurators.com** — no cart, no visible pricing, every product routes to a WhatsApp or email inquiry. Built to migrate cleanly to Shopify later (see `SHOPIFY_MIGRATION.md`).

## Preview it right now

Double-click **`index.html`** — the whole site runs from local files, no server required, so you can open every page and click around before anything goes live.

## Pages

| File | Purpose |
|---|---|
| `index.html` | Homepage — hero, shop-by-category, brand statement, Instagram grid, contact CTA |
| `about.html` | Who we are, how we work, our philosophy, collections |
| `products.html` | The dynamic catalog — 100 products, filterable, with inquiry modal |
| `contact.html` | Services, contact cards, inquiry form, map |
| `follow-us.html` | Instagram grid, newsletter signup, WhatsApp channel |

## Structure

```
website/
  index.html, about.html, products.html, contact.html, follow-us.html
  css/styles.css          all styling — brand colors, layout, responsive rules
  js/app.js                catalog filtering, search, product modal
  data/
    products.json           100 products, structured for future Shopify import
    categories.json         category → subcategory map
    data.js                 same product data, loaded directly by products.html
  images/
    products/                one photo per product, named by Product Code (e.g. TT1.jpg)
    site/hero-home.jpg       homepage hero banner
  sitemap.xml, robots.txt   basic SEO plumbing, already pointed at kantacurators.com
  SHOPIFY_MIGRATION.md      step-by-step guide for when you're ready to move to Shopify
```

## What's real vs. placeholder — please read before going live

- **WhatsApp inquiries** (+91 85100 03195) — fully live, pre-filled messages, works immediately.
- **Email inquiries** (komal_gupta@outlook.in) — fully live via `mailto:` links, works immediately.
- **64 of 100 products** have a real, matched photo. **36** show a branded "Photo Coming Soon" card because no reliable photo match existed in the "Catalogue gpt" folder (see `Kanta_Curators_Image_Match_Review.xlsx` for exactly which ones — mostly rakhis, jewellery, a few bags and torans). Send real photos named to match the Product Code (e.g. a photo for `R1` → `R1.jpg`) and I'll drop them in.
- **Instagram grid** (home + Follow Us) — a static grid of your real product photos linking out to @kanta.curators, not a live feed. A live feed needs a free embed app (SnapWidget, Elfsight, etc.) — quick to add later, just tell me if you want that now.
- **Newsletter signup** (Follow Us page) — front-end only right now; it shows a thank-you message but doesn't actually store anyone's email anywhere, since that needs a connected email service (Mailchimp, Klaviyo, etc.). Don't rely on it to collect real subscribers until it's connected.
- **Contact form** — opens the visitor's email app with a pre-filled message (works with zero setup, but does mean they need an email client configured on their device). If you want silent in-page submission instead, that requires a small form backend (Formspree is a common free option) — I can wire that up if you'd like.
- **Map on Contact page** — a generic "Delhi, India" map, since no exact street address was provided. Give me the real address and I'll pin it precisely.

## Deploying to www.kantacurators.com (GoDaddy)

I can't upload files to your hosting directly — I don't have your GoDaddy login. Here's how to do it yourself in a few minutes:

**If you have GoDaddy Web Hosting (cPanel):**
1. Log in to GoDaddy → My Products → find your hosting plan → **Manage**.
2. Open **File Manager** (or connect via FTP with an FTP client like FileZilla).
3. Go to the `public_html` folder (this is what serves your domain).
4. Upload every file and folder from this `website/` folder into `public_html`, keeping the same structure (`css/`, `js/`, `data/`, `images/` all need to stay alongside the `.html` files).
5. Visit **www.kantacurators.com** — it should load `index.html` automatically.

**If your domain is only registered with GoDaddy (no hosting yet), or you're using GoDaddy's Website Builder:**
GoDaddy's drag-and-drop Website Builder doesn't accept raw HTML/CSS/JS files like this — you'd need a traditional hosting plan (GoDaddy cPanel hosting, or any static host: Netlify, Vercel, Cloudflare Pages all have generous free tiers and work well for a site like this). Point kantacurators.com's DNS at whichever you choose; happy to walk through that once you tell me which route you want.

## Updating products later (zero-code workflow)

1. Edit `Kanta_Curators_Catalogue shopify.xlsx` (add/edit rows) and/or add new images.
2. Send me the updated file — I regenerate `data/data.js` and the image set from it, no page edits needed.

## Still open

- Real photos for the 36 placeholder products.
- Exact street address for the Contact page map (currently generic Delhi).
- Whether to connect the newsletter form to a real email service.
- Which hosting route you're using, so I can tailor the deploy steps.
