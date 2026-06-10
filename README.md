# Lumière — Premium Custom Storefront (Shopify-Ready)

A production-grade, niche-agnostic B2C e-commerce frontend built with Next.js 14, Tailwind CSS, and Framer Motion. Designed to use Shopify as a headless product catalog while delivering a completely custom, premium UI/UX.

---

## ✨ Phase 1 Includes

- **Design System** — Editorial luxe palette (ink / bone / cream / gold / sage), Cormorant Garamond display + Inter UI, motion presets
- **Layout** — Sticky header with hover mega-menu, mobile slide-in nav, dark footer, rotating announcement bar
- **Home Page (12 sections)** — Parallax hero, featured collections, best sellers carousel, promo banner, new arrivals, why-choose-us, brand story, marquee testimonials, featured products, Instagram grid, newsletter
- **Shop Page** — Sticky filter & sort bar, slide-in filter sheet, animated 4-up grid
- **Product Detail Page** — Multi-image gallery with cursor-tracking zoom, color swatches, size pills, sticky Add to Bag + Buy Now, animated accordions, related products
- **Cart Drawer** — Spring-physics slide-in, free-shipping progress bar, persistent via localStorage
- **Checkout** — Full form with order summary, discount codes, Shopify Payments handoff
- **Shopify Integration Layer** — GraphQL client with graceful fallback to local catalog when no credentials are set

---

## 🚀 Quick Start

```bash
# 1. Install dependencies
yarn install

# 2. Configure environment variables (see .env)
#    The site works out-of-the-box with placeholder Shopify credentials
#    (falls back to the local catalog in lib/products.js)

# 3. Start the dev server
yarn dev
```

Open http://localhost:3000

---

## 🛍️ Connecting to a Real Shopify Store

Edit `.env`:

```env
SHOPIFY_STORE_DOMAIN=your-store.myshopify.com
SHOPIFY_STOREFRONT_ACCESS_TOKEN=your_real_token
SHOPIFY_API_VERSION=2024-10
```

That's it. `lib/shopify.js` auto-detects real credentials and switches from the local catalog to live Storefront API calls. No other code changes required.

**Where to get the Storefront Access Token:**
Shopify Admin → Settings → Apps and sales channels → Develop apps → Create app → Configure Storefront API scopes → Install → Copy Storefront access token.

---

## 📁 Folder Structure

```
lumiere/
├── app/
│   ├── api/[[...path]]/route.js        # Backend (Shopify proxy + MongoDB)
│   ├── checkout/page.js                # Checkout flow
│   ├── products/[handle]/page.js       # Product detail
│   ├── shop/page.js                    # Shop listing
│   ├── globals.css                     # Design system + tokens
│   ├── layout.js                       # Root layout (fonts, header, footer)
│   ├── page.js                         # Home page
│   └── providers.js                    # React Query + Cart context
├── components/
│   ├── storefront/
│   │   ├── announcement-bar.jsx
│   │   ├── cart-drawer.jsx
│   │   ├── footer.jsx
│   │   ├── header.jsx
│   │   ├── mega-menu.jsx
│   │   ├── product-card.jsx
│   │   ├── product-view.jsx
│   │   └── reveal.jsx                  # Scroll-reveal animation wrapper
│   └── ui/                             # shadcn/ui primitives
├── lib/
│   ├── cart-context.jsx                # Cart state + localStorage persistence
│   ├── products.js                     # Placeholder product catalog
│   ├── shopify.js                      # Shopify Storefront API client
│   └── utils.js
├── hooks/                              # Custom React hooks
├── public/                             # Static assets
├── .env                                # Environment variables (Shopify, Mongo)
├── components.json                     # shadcn config
├── jsconfig.json                       # Path aliases (@/...)
├── next.config.js                      # Next.js config (image hosts, headers)
├── package.json
├── postcss.config.js
└── tailwind.config.js                  # Brand colors + custom animations
```

---

## 🧩 Tech Stack

| Layer | Tech |
|---|---|
| Framework | Next.js 14 (App Router) |
| Styling | Tailwind CSS · shadcn/ui · custom design tokens |
| Animation | Framer Motion |
| State | React Context (cart) · TanStack Query (data) |
| Backend | Next.js API routes · MongoDB |
| Product Catalog | Shopify Storefront API (GraphQL) — with local fallback |
| Payments | Shopify Payments (via Shopify hosted checkout) |
| Icons | lucide-react |
| Notifications | sonner |

---

## 🗺️ Roadmap (Phase 2+)

- Wishlist page + persistent state
- Customer accounts (login / register / order history)
- Order tracking page
- Product reviews & ratings UGC
- Smart search with cmdk
- Quick view modal
- About / FAQ / Contact / Policy pages
- SEO: JSON-LD product schema, sitemap.xml, robots.txt
- Real Shopify connection

---

## 📦 Replacing the Placeholder Catalog

The local catalog lives in `lib/products.js`. You can:

1. Edit it directly with your own products (no Shopify needed for prototyping), OR
2. Set real Shopify env vars and the site automatically pulls from your store.

The product shape mirrors Shopify's schema (handle, options, variants, priceRange-equivalent) so the swap is seamless.

---

## 🎨 Customizing the Brand

- **Colors**: `tailwind.config.js` → `colors` object (`ink`, `bone`, `cream`, `gold`, `sage`, `line`)
- **Typography**: `app/layout.js` (swap `Cormorant_Garamond` for any Google Font)
- **Logo & Name**: `components/storefront/header.jsx` and `footer.jsx` (search for "Lumière")
- **Hero imagery**: `app/page.js` → `Hero` component
- **Announcement messages**: `components/storefront/announcement-bar.jsx`

---

© Lumière — Built with care.
