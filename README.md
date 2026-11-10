# Sneaker Symphony: AI-Run Marketplace

> A full online store that one person runs, with supplier scrapers, AI product parsing, and per-pair QC workflows.

**Status:** Live · **Client:** Own product · **Role:** Founder & solo full-stack engineer

**Stack:** `Claude Haiku` `Next.js 15` `Supabase` `Inngest` `Cloudflare R2`

> [!NOTE]
> **Showcase repository.** The source code is private. This repo documents the problem, the architecture, and the results. Screens show demo data. Full case study: https://lesjohnpauloliver.dev/work/sneaker-symphony-ai-run-marketplace

## Summary

A Philippine sneaker marketplace at sneakersymphony.com, built and run by one person. Supplier-catalog scrapers, Claude Haiku product-title parser, GCash, bank transfer, and COD payments with proof-of-payment upload and per-pair QC approval.

## The problem

- A full online store normally needs staff for product entry, pricing, and payment verification.
- Supplier catalogs list hundreds of items with photos and Chinese-yuan prices that have to be cleaned up before they can be sold.
- Filipino buyers expect GCash, bank transfer, or COD payments with proof of payment.

## Problem → fix

### A full online store normally needs staff for product entry, pricing, and payment verification.

Supplier-catalog scrapers pull supplier catalogs into a review queue, and the admin imports items one by one or in bulk. Nothing reaches the store without an admin check. Claude Haiku parses product titles.


### Supplier catalogs list hundreds of items with photos and Chinese-yuan prices that need cleanup before they can be sold.

Each supplier source gets its own importer and table, so a new source cannot break a working one. Images are copied to Cloudflare R2, and unpriced items get tiered price suggestions.


### Filipino buyers expect GCash, bank transfer, or COD payments with proof of payment.

Checkout supports GCash, bank transfer, and COD with proof-of-payment upload verified by the owner. Per-pair QC approval workflow with 8-angle photos before payment release.


## Approach

- Supplier-catalog scrapers pull supplier catalogs into a review queue, so nothing reaches the store without an admin check.
- Each supplier source gets its own importer and table, sharing only the storage and catalog plumbing, so a new source cannot break a working one.
- Claude Haiku parses product titles automatically, saving manual data entry.
- Per-pair QC approval with proof-of-payment verification by the owner.

## What was built

- Supplier-catalog scrapers with images copied to Cloudflare R2
- Claude Haiku product-title parser
- Review queue with one-by-one and bulk import into the catalog
- GCash, bank transfer, and COD checkout with proof-of-payment upload
- Per-pair QC approval workflow with owner verification
- Resend email integration and Messenger integration
- Vercel Cron for scheduled jobs

## Capabilities

**Catalog automation**
- Supplier-catalog scrapers with per-source importer
- Claude Haiku product-title parser
- Admin review queue with single and bulk import
- Tiered price suggestions for unpriced items

**Commerce**
- GCash, bank transfer, and COD checkout
- Proof-of-payment upload verified by owner
- Per-pair QC approval with 8-angle photos
- Invoices on Cloudflare R2, buyer email through Resend

**Roadmap**
- PayMongo integration for automated card and e-wallet payments
- Automated social posting pipeline to FB, IG, and TikTok

## Architecture

- Next.js 15 on Vercel, with Supabase for data and auth.
- Inngest for background jobs, Vercel Cron for scheduled tasks.
- Cloudflare R2 holds product images and invoices; Resend sends buyer email.
- Messenger integration for customer inquiries.

## Engineering

- Schema changes ship as versioned SQL migrations, so every database change is reviewable and repeatable.
- Checkout and admin forms are validated with Zod schemas before anything is written.
- Each supplier importer is isolated in its own table, and scraped items wait in an admin review queue before they reach the store.
- Vercel Analytics and Speed Insights track real-user traffic and page performance in production.

## Where AI does the work

Claude Haiku parses product titles, and scrapers fill the catalog, leaving the owner to review and approve.

## Outcome

- Supplier import and product parsing automated, with per-pair QC and payment workflows.
- Live at sneakersymphony.com.

---

Built by **[Les John Paul Oliver](https://lesjohnpauloliver.dev)**, AI Engineer in the Philippines: agentic AI, RAG, LLM evals, MCP, and business automation. [Case studies](https://lesjohnpauloliver.dev/#projects) · [Hire me](https://lesjohnpauloliver.dev/ai-engineer-philippines)
