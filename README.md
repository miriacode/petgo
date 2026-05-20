<div align="center">

# 🐾 PetGo

**A direct-to-consumer (B2C) pet e-commerce platform — built mobile-first, USA-first, multi-country by design.**

[![Live Demo](https://img.shields.io/badge/Live_Demo-petgo--store.click-1b9247?style=for-the-badge&logo=vercel&logoColor=white)](https://petgo-store.click)
[![Portfolio](https://img.shields.io/badge/Portfolio-miriacode.vercel.app-000?style=for-the-badge)](https://miriacode.vercel.app)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/miriam-acuna-enciso/)

</div>

---

## ✨ What is PetGo?

PetGo is a full-stack **direct-to-consumer (B2C)** pet e-commerce app — food, toys, accessories and health products, sold straight to pet owners. The codebase is a portfolio + learning project, but the architecture is wired for real-world expansion: electronic tax docs, payment gateways and additional countries are all stubbed out behind feature flags rather than hard-coded out.

The storefront targets the **USA** as the launch country, with the data model and pricing rules already shaped to onboard **Colombia** and **Perú** without refactoring (currency, tax rate, locale and shipping zone are all per-country fields on the schema).

> **Note** — The source code lives in a private repository. This repo exists as the public showcase.

---

## 🎥 Live demo

🔗 **[petgo-store.click](https://petgo-store.click)**

---

## 🧱 Tech stack

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

| Layer | Choices |
|---|---|
| **Storefront** | Next.js 15 App Router · React 19 · Turbopack · Apollo Client v4 · Serwist (PWA) · Tailwind v4 · next-themes · next-intl |
| **API** | Bun runtime · Hono · GraphQL Yoga · better-auth (email + OTP) · Drizzle ORM · DataLoader |
| **Database** | PostgreSQL (Neon free-tier in prod) |
| **Email** | Resend (transactional auth OTPs) |
| **Tooling** | Bun workspaces · Turborepo · Biome · GraphQL Code Generator (client-preset) |

---

## 🎯 Highlights

### 🌐 Storefront

- 🌎 **Bilingual EN / ES** via `next-intl`, locale-prefixed routes (`/en/...` `/es/...`)
- 🌗 **Dark mode** with tuned brand palette per theme — not a default Tailwind invert
- 📱 **Mobile-first** with dedicated desktop layouts (not just responsive — different chrome on every breakpoint)
- 📲 **PWA-ready** via Serwist (installable, offline fallback page)
- 🐾 **Active-pet awareness** — products with proteins the user's pet is allergic to are filtered out automatically across home, search, category, shop and brand surfaces
- 🛒 **Guest cart** via cryptographically-random session tokens, auto-claims into the user's account on sign-in
- ⚡ **Apollo Client v4 + RSC** with `PreloadQuery` for SSR-streamed product data — no skeleton flash on the first paint of the home page

### 🔌 API

- 🧱 **Strongly-typed GraphQL schema** generated end-to-end with `graphql-codegen` (client preset + fragment masking)
- ⚙️ **Hexagonal-ish architecture** — every feature has its own `service` (business logic), `repository` (Drizzle queries) and `resolvers` (GraphQL plumbing) with thin handoffs in each direction
- 🔐 **Auth via `better-auth`** — email + password, password-reset OTP, bearer tokens (cookie-less by design, CORS-friendly)
- 📨 **Resend integration** — graceful fallback to stdout-log when `RESEND_API_KEY` isn't set so local dev and CI never need a live mail provider
- 🛠 **Hand-rolled DataLoader registry** — per-request loaders for catalog joins (variants, images, reviews aggregate) keep N+1 queries off the wire

### ✅ Testing

- **113+ unit tests** across 13 service-layer suites (`bun:test`)
- Money-touching code (cart totals, coupons, tax documents, order placement) is exercised end-to-end with happy + error paths
- IDOR-style ownership checks tested explicitly — a foreign user-id surfaces as `NotFoundError`, never silently writes

### 🚀 DevOps

- **Storefront** auto-deploys from `main` to Vercel on every push
- **API** runs from a tracked Dockerfile (multi-stage Bun + Alpine, ~150MB), pushed to GCP Artifact Registry and deployed to a Compute Engine e2-micro VM
- **DNS** managed in AWS Route 53 — apex domain on Vercel, `api.*` subdomain on the VM
- **Vercel Analytics + Speed Insights** wired for Core Web Vitals

---

## 👋 About me

Built by **Miriam Acuña** — software engineer shipping side projects to explore the parts of the stack day-job tickets don't always touch.

- 💼 [LinkedIn](https://www.linkedin.com/in/miriam-acuna-enciso/)
- 🌐 [Portfolio](https://miriacode.vercel.app)
- 🐙 [GitHub](https://github.com/miriacode)
