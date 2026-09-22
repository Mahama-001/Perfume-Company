# Aura Luxe Ghana (Haute Parfumerie)
### Production-Ready Luxury Fragrance Storefront & Private Merchant Dashboard

A bespoke, quiet-luxury e-commerce platform and administrative console for **Aura Luxe Ghana**, formulated between Paris and Accra. Strictly adheres to high-fashion editorial aesthetics (Obsidian Black, Deep Charcoal, Dark Slate, and Champagne accents with 1px borders and crisp 0–4px radii).

---

## 1. Tech Stack & Architecture

- **Framework**: Next.js (App Router, Server Actions, TypeScript)
- **Styling**: Tailwind CSS (Strict custom quiet luxury design tokens, zero AI gradients/glows)
- **Database & ORM**: PostgreSQL & Prisma ORM
- **Access Control & Auth**: Next.js Edge Middleware + `jose` (HS256 signed HTTP-only cookies) + `bcryptjs`
- **Payment Gateway**: Paystack API (Native Ghanaian Cedis `GH₵`, MTN Mobile Money, Telecel Cash, AT Money, and Visa/Mastercard)

---

## 2. System Zones

### 1. Public Storefront (Customer Facing)
- **Routes**:
  - `/`: High-fashion editorial campaign, numbered batch showcase, savoir-faire, and interactive acquisition drawer.
  - `/shop`: Complete catalogue archive with olfactive family filtering and Ghanaian Cedi pricing.
  - `/product/[slug]`: Flacon profile, formulation story, olfactive pyramid (Top, Heart, Base), and 50ml/100ml size selection.
  - `/checkout`: Frictionless mobile checkout with recipient delivery details across all 16 Ghanaian administrative regions and local payment method selector.
  - `/checkout/confirmation`: Official digital acquisition certificate and courier dispatch tracking.
- **Customer Guarantee**: Only displays active products (`isActive: true`) and in-stock variants (`stock > 0` and `isActive: true`).

### 2. Merchant Admin Console (Private Back-Office)
- **Routes**:
  - `/admin`: Executive dashboard with settled revenue in GH₵, order volume, active formulations count, and low-inventory warnings.
  - `/admin/login`: Secure access gate; unauthenticated visitors to `/admin/*` are automatically redirected here.
  - `/admin/products`: Complete inventory ledger with instant live/hidden visibility toggle and soft-delete/archive.
  - `/admin/products/new`: Compose and formulate new fragrance flacons with custom notes, variants, prices (GH₵), and initial stocks.
  - `/admin/products/[id]/edit`: Modify fragrance metadata, adjust 50ml/100ml prices in GH₵, and update inventory counts.
  - `/admin/orders`: Customer acquisitions ledger with real-time status transitions (`PENDING_PAYMENT` → `PAID` → `PROCESSING` → `DISPATCHED` → `DELIVERED` → `CANCELLED`).

---

## 3. Merchant Credentials

For testing and administrative access:

| Field | Credential |
| :--- | :--- |
| **Login Portal** | `http://localhost:3000/admin/login` |
| **Email** | `admin@auraluxeghana.com` |
| **Password** | `AuraLuxe2025!` |
| **Role** | `ADMIN` |

---

## 4. Environment Variables (`.env`)

```env
# PostgreSQL Database Connection
DATABASE_URL="postgresql://postgres:postgres@localhost:5432/auraluxe_ghana?schema=public"

# Edge Session Secret
AUTH_SECRET="aura-luxe-ghana-bespoke-secret-key-2025-accra"

# Paystack API Keys (Ghana Cedis GHS)
PAYSTACK_SECRET_KEY="sk_test_aura_luxe_ghana_demo"
NEXT_PUBLIC_PAYSTACK_PUBLIC_KEY="pk_test_aura_luxe_ghana_demo"

# Base Application URL
NEXT_PUBLIC_APP_URL="http://localhost:3000"
```

> **Note on Database Dual-Mode**: If `DATABASE_URL` is unset or unreachable, Aura Luxe seamlessly activates an intelligent in-memory repository with pre-seeded formulations and demo orders, ensuring zero interruptions during evaluation or offline development.

---

## 5. Development & Production Commands

```bash
# Install dependencies
npm install

# Generate Prisma Client
npx prisma generate

# Seed database catalogue & admin
npx prisma db seed

# Run local development server
npm run dev

# Run linting check
npm run lint

# Production build
npm run build
```
