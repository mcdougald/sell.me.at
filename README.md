<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/hero-dark.png">
    <img src=".github/assets/hero.png" alt="sell.me.at landing page" width="880">
  </picture>
</p>

<h1 align="center">sell.me.at</h1>

<p align="center"><strong>Sell digital products without a middleman holding the money.</strong></p>

<p align="center">
  <img src="https://img.shields.io/badge/status-in%20development-171717?style=flat-square" alt="Status: in development">
  <img src="https://img.shields.io/badge/license-source--available-404040?style=flat-square" alt="License: source-available">
  <img src="https://img.shields.io/badge/part%20of-me.at-737373?style=flat-square" alt="Part of me.at">
</p>

<p align="center">
  <a href="#features">Features</a> ·
  <a href="#how-it-works">How it works</a> ·
  <a href="#built-with">Built with</a>
</p>

Most storefronts for digital goods collect the money first and pay you out later, on their schedule. I built sell.me.at so buyers pay on your own Stripe account: there is no platform balance in between and nothing here that could hold up a payout. It is a hosted storefront for downloads, license keys and content bundles, and it is a platform, not a merchant of record. Your sales, your tax, your payouts.

> **Status:** in development. The storefront and seller dashboard run in test mode only. Live checkout stays switched off in code until billing go-live and a review of the payment code are complete.

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/overview-dark.svg">
    <img src=".github/assets/overview.svg" alt="sell.me.at at a glance: you are the seller, your own signing key, counted downloads, buyers never stranded" width="880">
  </picture>
</p>

## Why sell.me.at

| The usual digital storefront | sell.me.at |
| --- | --- |
| Holds your money in a platform balance | Buyers pay on your own Stripe account |
| License keys signed with the platform's key | Signed with your own Ed25519 key |
| Download links that work forever | Short-lived links, a download allowance, every request logged |
| Closing the shop strands your buyers | A closed storefront is suspended, and buyers keep their purchases |

## Features

- **You are the seller of record**: checkout hands the buyer to a Stripe-hosted payment page on the seller's connected account. sell.me.at never sets the charge amount and has no tax field.
- **Your own license signing key**: each seller gets an Ed25519 keypair, and license keys are signed with it, never with a shared platform key. The private key is stored encrypted.
- **Storefront and seller dashboard**: a public storefront per seller, plus a dashboard for drafts, multipart file uploads, prices, publishing and archiving (test mode).
- **Counted downloads**: each purchase carries a download allowance, links are short-lived, and every download request is logged, including refusals.
- **One payment, one order, one entitlement**: verified Stripe webhooks create orders and entitlements idempotently, and refunds and disputes revoke access.
- **Promo codes applied by Stripe**: codes are validated at checkout and the discount is applied through a coupon on the seller's own account.
- **Leaving does not strand customers**: closing a storefront suspends it, so buyers keep their purchases and the public key that verifies their licenses.
- **Fails safe by default**: without Stripe keys the app runs against a mock payment provider and charges nobody.

## How it works

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/flow-dark.svg">
    <img src=".github/assets/flow.svg" alt="How sell.me.at works: list, checkout, grant, deliver, revoke" width="880">
  </picture>
</p>

A seller uploads files, sets a price and publishes. Checkout happens on a Stripe-hosted page on the seller's own account, and a verified webhook turns one payment into one order and one entitlement, idempotently. Downloads go out through short-lived, counted links, and a refund or dispute revokes access.

## Built with

<p>
  <img src="https://img.shields.io/badge/Next.js-16-000000?style=flat-square&logo=nextdotjs&logoColor=white" alt="Next.js 16">
  <img src="https://img.shields.io/badge/React-19-171717?style=flat-square&logo=react&logoColor=white" alt="React 19">
  <img src="https://img.shields.io/badge/TypeScript-5-262626?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript">
  <img src="https://img.shields.io/badge/Tailwind%20CSS-4-404040?style=flat-square&logo=tailwindcss&logoColor=white" alt="Tailwind CSS 4">
  <img src="https://img.shields.io/badge/Drizzle-Postgres-525252?style=flat-square&logo=drizzle&logoColor=white" alt="Drizzle ORM and Postgres">
  <img src="https://img.shields.io/badge/Stripe-Connect-737373?style=flat-square&logo=stripe&logoColor=white" alt="Stripe">
</p>

- Next.js 16 (App Router), React 19, TypeScript
- Tailwind CSS 4
- Drizzle ORM + Postgres
- Better Auth
- oRPC + TanStack Query
- Stripe (hosted checkout on connected accounts, verified webhooks)
- Upstash rate limiting

## Part of the me.at family

sell.me.at is one of my [`*.me.at`](https://me.at) apps. They share one design system, one account, and one app shell. Development happens in a private monorepo; this repository is the project's public-facing home.

## License

Source-available. See [LICENSE](LICENSE).
