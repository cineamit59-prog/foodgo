# FoodGo – Food Delivery for Malkangiri, Odisha

Modern food delivery marketplace built with React, TypeScript, Tailwind CSS, and Supabase-ready architecture.

**Demo mode** works fully without any API keys. Orders, cart, auth, admin and partner dashboards are functional using local storage + demo data.

## Features

- Homepage with categories, featured restaurants, offers, how-it-works
- Restaurant discovery with search, cuisine, veg, open filters and sorting
- Restaurant menu with add-to-cart (one restaurant per order)
- Persistent cart with coupon codes (WELCOME50, FOODGO20, FREEDEL)
- Checkout with address validation and demo payment methods
- Order confirmation + status timeline with auto-progression demo
- Customer account, order history, cancel (when allowed)
- Admin dashboard: overview, orders, restaurants, coupons, status updates
- Restaurant partner dashboard: incoming orders, menu availability toggle
- Responsive mobile-first UI with bottom navigation
- Role-based access (customer / partner / admin)

## Tech Stack

- React 19 + Vite + TypeScript
- Tailwind CSS v4
- React Router v7
- Lucide React icons
- Supabase (optional – Auth + Postgres + RLS)
- LocalStorage for demo cart/orders/auth

## Quick Start (Demo Mode)

```bash
cd foodgo
npm install
npm run dev
```

Open http://localhost:5173

### Demo accounts

| Role     | Email                         | Password    |
|----------|-------------------------------|-------------|
| Customer | customer@foodgo.local         | customer123 |
| Admin    | admin@foodgo.local            | admin123    |
| Partner  | partner@spicekitchen.local    | partner123  |

Any other email + password (≥6 chars) also works as a new customer in demo mode.

## Environment Variables

Copy `.env.example` to `.env`:

```
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your-anon-key
VITE_DEMO_MODE=true
```

Leave `VITE_DEMO_MODE=true` (or omit Supabase keys) to stay in fully offline demo mode.

## Database Setup (Optional)

1. Create a free project at [supabase.com](https://supabase.com)
2. Run `supabase/migrations/001_initial_schema.sql` in the SQL editor
3. Set env vars and set `VITE_DEMO_MODE=false`
4. Seed restaurants/menu from `src/data/demo.ts` as needed

RLS policies enforce customer / partner / admin access server-side.

## Scripts

```bash
npm run dev      # development server
npm run build    # production build
npm run preview  # preview production build
npm run lint     # oxlint
```

## Project Structure

```
src/
  components/   # UI, layout, restaurant, cart
  context/      # Auth + Cart providers
  data/         # Demo seed data
  layouts/
  lib/          # supabase client, utils
  pages/        # All routes including admin & partner
  types/
supabase/migrations/
```

## Deployment (Vercel)

1. Push to GitHub
2. Import project in Vercel
3. Framework: Vite
4. Add env vars if using Supabase
5. Deploy

## GitHub Upload

```bash
git init
git add .
git commit -m "Initial FoodGo food delivery platform"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/foodgo.git
git push -u origin main
```

## Extension Plan – Delivery Partner Module

Not included in MVP. To add later:

1. `delivery` role in profiles
2. `delivery_assignments` table (order_id, partner_id, status)
3. Partner app routes: assigned orders, accept/reject, status updates
4. RLS: delivery partners only see assigned orders
5. Real-time via Supabase subscriptions (optional)

## Notes

- Prices and totals are recalculated on checkout (demo server-side validation)
- No card data is stored
- Payment is simulated; ready for Razorpay integration with server verification
- Images use Unsplash (properly licensed for demo)
- No fake reviews or partnership claims

## License

MIT – built as a production-quality portfolio / starter project for Malkangiri local delivery.
