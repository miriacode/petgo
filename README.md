<div align="center">

# 🐾 PetGo

**A direct-to-consumer (B2C) pet e-commerce platform — built mobile-first, USA-first, multi-country by design.**

[![Live Demo](https://img.shields.io/badge/Live_Demo-petgo--store.click-1b9247?style=for-the-badge&logo=vercel&logoColor=white)](https://petgo-store.click)
[![Portfolio](https://img.shields.io/badge/Portfolio-miriacode.vercel.app-000?style=for-the-badge)](https://miriacode.vercel.app)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/miriam-acuna-enciso/)

<br />

<p align="center">
  <img src="screenshots/01-main-page.png" alt="PetGo Storefront" width="900" style="border-radius: 12px; box-shadow: 0 8px 30px rgba(0,0,0,0.12);" />
</p>

</div>

---

## ✨ What is PetGo?

PetGo is a full-stack **direct-to-consumer (B2C)** pet e-commerce platform engineered for pet parents — offering food, toys, accessories, and health products. While created as a portfolio and learning project, its engineering follows enterprise-grade architecture: electronic tax documents, regional shipping rules, cash on delivery, and multi-country expansion are modeled cleanly into the schema rather than retrofitted.

The storefront targets the **United States** as its launch market, with the underlying data model and pricing rules already equipped to onboard **Colombia** and **Peru** without schema changes (currencies, tax rates, locales, and shipping zones are per-country configurations).

> **Note** — The core source code is maintained in a private repository. This repository serves as the official public showcase and architectural overview.

---

## 📸 Visual Tour

A visual walkthrough of the PetGo web experience across discovery, shopping, personalization, and customer account workflows:

| 01. Storefront Home & Discovery | 02. Mega Category Menu |
|:---:|:---:|
| <img src="screenshots/01-main-page.png" alt="Storefront Home" width="450" /> | <img src="screenshots/02-menu.png" alt="Mega Menu" width="450" /> |
| **03. Weekly Deals & Promotions** | **04. Dynamic Search & Multi-Facet Filters** |
| <img src="screenshots/12-this-week-deals.png" alt="Weekly Deals" width="450" /> | <img src="screenshots/11-search-result.png" alt="Search & Filters" width="450" /> |
| **05. Instant SSR Rails & Personalized Picks** | **06. Pet-Aware Favorites & Allergy Shield** |
| <img src="screenshots/04-last-purchased-products.png" alt="Personalized Last Purchased" width="450" /> | <img src="screenshots/08-favorites-for-my-dog.png" alt="Pet Favorites" width="450" /> |
| **07. Shopping Cart & Free Shipping Goal** | **08. Streamlined Checkout & Payment** |
| <img src="screenshots/05-cart.png" alt="Shopping Cart" width="450" /> | <img src="screenshots/06-checkout.png" alt="Checkout" width="450" /> |
| **09. Order History & One-Tap Reordering** | **10. Pet Profiles & Active Roster Switcher** |
| <img src="screenshots/07-my-orders.png" alt="My Orders" width="450" /> | <img src="screenshots/09-my-pets.png" alt="My Pets" width="450" /> |
| **11. Real-Time In-App Notifications** | **12. Clean Authentication & Security** |
| <img src="screenshots/10-notifications.png" alt="Notifications" width="450" /> | <img src="screenshots/03-signin.png" alt="Sign In" width="450" /> |

---

## 🎥 Live Application

Experience the live storefront directly in your browser:

🔗 **[petgo-store.click](https://petgo-store.click)**

---

## 🧱 Tech Stack

<div align="center">

![Next.js](https://img.shields.io/badge/Next.js_15-000000?logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React_19-61DAFB?logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)
![Bun](https://img.shields.io/badge/Bun-000000?logo=bun&logoColor=white)
![GraphQL](https://img.shields.io/badge/GraphQL-E10098?logo=graphql&logoColor=white)
![Apollo](https://img.shields.io/badge/Apollo_Client_v4-311C87?logo=apollographql&logoColor=white)
![Hono](https://img.shields.io/badge/Hono-E36002?logo=hono&logoColor=white)
![Postgres](https://img.shields.io/badge/Postgres-4169E1?logo=postgresql&logoColor=white)
![Drizzle](https://img.shields.io/badge/Drizzle_ORM-C5F74F?logo=drizzle&logoColor=black)
![Tailwind](https://img.shields.io/badge/Tailwind_v4-06B6D4?logo=tailwindcss&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?logo=vercel&logoColor=white)
![GCP](https://img.shields.io/badge/GCP_Compute_Engine-4285F4?logo=googlecloud&logoColor=white)

</div>

| Layer | Technologies & Libraries |
|---|---|
| **Storefront** | Next.js 15 (App Router) · React 19 · Turbopack · Apollo Client v4 · Serwist (PWA) · Tailwind v4 · next-themes · next-intl |
| **API Backend** | Bun runtime · Hono · GraphQL Yoga · better-auth · Drizzle ORM · DataLoader registry · Resend |
| **Database** | PostgreSQL (Neon serverless in production) |
| **Email Service** | Resend (transactional auth OTPs & password recovery) |
| **Monorepo & Tooling** | Bun Workspaces · Turborepo · Biome linter/formatter · GraphQL Code Generator (client-preset + fragment masking) |

---

## 🎯 Architecture & Feature Highlights

### 🌐 High-Performance Storefront

- ⚡ **Zero-Skeleton Initial Paint**: Apollo Client v4 + RSC integration with `PreloadQuery` pre-renders catalog carousels and top-selling rails on the server, eliminating layout shifts and delayed loading skeletons.
- 🐾 **Server-Synchronized Species Preload**: Fast `petgo_species` cookie sync allows the Next.js edge server to immediately prefetch products matching the customer's active pet (Dog or Cat) before client-side hydration.
- 🛡️ **Active-Pet Allergen Guard**: The catalog automatically filters or flags ingredients containing proteins that the shopper's active pet is allergic to across discovery rails, category trees, and product details.
- 🌎 **Bilingual Internationalization (EN / ES)**: Native localized routing (`/en/...` and `/es/...`) via `next-intl` with localized currencies, shipping threshold bars, and tax summaries.
- 🛒 **Unified Guest & Account Cart**: Session tokens power guest cart persistence and seamlessly claim carts into the customer's account upon authentication.
- 📦 **Resilient Catalog Media**: Graceful branded paw fallback artwork for items with missing or retired product images.
- 🌗 **Adaptive Themes**: Refined light and dark modes with dedicated brand palettes powered by `next-themes`.
- 📲 **Progressive Web App (PWA)**: Installable web app with Service Worker caching and custom offline fallback pages powered by Serwist.

### 🔌 Robust GraphQL API

- 🧱 **3-Layer Hexagonal Architecture**: Every feature is split cleanly into **Resolvers** (GraphQL schema plumbing), **Services** (domain rules & validations), and **Repositories** (Drizzle ORM queries).
- ⚙️ **DataLoader Batching**: Hand-crafted DataLoader registry guarantees zero N+1 database queries when joining product variants, images, brand data, and review score aggregates.
- 🔐 **Authentication & Security**: Email + password login, password-reset OTP verification via Resend, and bearer tokens engineered for cross-origin security.
- 🛡️ **Defensive API Stack**: GraphQL Armor depth and cost limiting, IP-level rate limiting, strict CORS allowlists, disabled production introspection, and automated scanner blocking.
- 🚚 **Transactional Inventory**: Atomic stock verification during checkout prevents overselling and handles partial stock gracefully.

### ✅ Rigorous Automated Testing

- **182 unit tests (100% pass rate)** across 18 test suites executed in milliseconds via `bun:test`.
- **Financial & Order Integrity**: Deep test coverage for cart totals, coupon logic (percentage, fixed amount, and free shipping), tax rules, and order transitions.
- **IDOR Multi-Tenant Guardrails**: Explicit security tests verifying that customer-scoped records (pets, favorites, addresses, orders) reject foreign user IDs with clean `NotFoundError` exceptions.

### 🚀 Production Infrastructure & DevOps

- **Storefront**: Hosted on Vercel with automatic CI/CD deployment from `main`.
- **API Server**: Packaged as a lightweight multi-stage Docker container (~150MB) running on a Google Cloud Platform (GCP) Compute Engine e2-micro instance.
- **Global DNS**: Managed through AWS Route 53 with automated HTTPS certificate provisioning.
- **Observability**: Vercel Analytics and Speed Insights tracking Core Web Vitals in real-time.

---

## 👋 Author

Designed and engineered by **Miriam Acuña**.

- 💼 **LinkedIn**: [Miriam Acuña](https://www.linkedin.com/in/miriam-acuna-enciso/)
- 🌐 **Portfolio**: [miriacode.vercel.app](https://miriacode.vercel.app)
- 🐙 **GitHub**: [@miriacode](https://github.com/miriacode)
