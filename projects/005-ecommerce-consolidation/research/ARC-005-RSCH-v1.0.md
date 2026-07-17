# Technology and Service Research: E-Commerce Consolidation

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-005-RSCH-v1.0 |
| **Document Type** | Technology & Service Research Findings |
| **Project** | E-Commerce Consolidation (Project 005) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT — FICTIONAL DEMONSTRATION |
| **Version** | 1.0 |
| **Created Date** | 2026-07-06 |
| **Owner** | George Jetson (Digital & E-Commerce Lead) |
| **Distribution** | Executive team, wholesale team, solution architecture advisor |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-06 | ArcKit AI | Initial market scan from `/arckit:research` | [PENDING] | [PENDING] |

---

## Research Scope

SaaS/PaaS commerce platforms for a dual-channel Australian specialty retailer:
multi-storefront B2C (rationalising 5 Shopify stores), a demanding B2B trade
portal (replacing self-managed Magento), hub-first integration, and CRM-based
identity. The architectural question is **one platform vs a deliberate B2B/B2C
split**. Pricing indicative; re-verify at evaluation.

## Options Landscape

| Option | Pattern | B2C multi-store | B2B depth | Ops burden | Indicative 3-yr TCO | Notes |
|---|---|---|---|---|---|---|
| **Shopify Plus (B2C + B2B on Shopify)** | One platform | STRONG (expansion stores) | GOOD and improving (company accounts, price lists) | LOW | ~A$350–500k | Team already fluent (5 stores today); B2B depth vs Magento parity is the test |
| **Adobe Commerce Cloud (PaaS)** | One platform | STRONG | STRONG (incumbent capability) | MEDIUM | ~A$450–650k | Removes self-hosting (G-2) but keeps Magento complexity and cost |
| **BigCommerce Enterprise (B2B Edition)** | One platform | GOOD (multi-storefront) | STRONG | LOW | ~A$300–450k | Credible both-channel challenger; smaller AU partner pool |
| **Split: Shopify Plus (B2C) + BigCommerce B2B or Adobe Commerce Cloud (B2B)** | Two platforms | STRONG | STRONG | MEDIUM | ~A$420–600k | Best-fit per channel; two platforms to run, one hub keeps them honest |
| **Headless/composable (commercetools-class)** | Composable | STRONG | STRONG | HIGH | ~A$700k+ | Over-scaled for 160-staff retailer; fails BR-010; culled |

## Analysis Against Requirements

- **B2B parity-plus (BR-005):** the decisive test. Trade customers get tiered
  pricing, credit visibility, pay-on-account, and backorder ETAs today on
  Magento. Shopify B2B has closed much of this gap but must *demonstrate* it
  with our pricing-agreement complexity (DAT-004); Adobe and BigCommerce B2B
  meet it natively.
- **Multi-storefront rationalisation (BR-001/FR-001):** Shopify expansion
  stores and BigCommerce multi-storefront both support the ≤3-storefront
  target with shared catalogue; Adobe strongest for complex catalogue rules
  but at ops cost.
- **Hub-first (NFR-I-001):** all options integrate; the evaluation must test
  *availability-feed latency* and order-orchestration webhooks, since G-3
  (zero web oversell) is the portfolio's founding promise re-applied to web.
- **Team capability:** five Shopify stores mean deep in-house Shopify skill —
  a real TCO factor favouring Shopify-inclusive options.
- **Project 004 coupling:** a Shopify Plus decision unlocks the Shopify POS
  scenario (ARC-004-RSCH option 3); a split decision effectively removes it.

## Shortlist & Recommendation for Evaluation

1. **Shopify Plus (single platform, B2C + B2B)** — lowest ops burden, existing
   skills; must pass a scripted B2B parity-plus demo against BR-005.
2. **Split: Shopify Plus (B2C) + BigCommerce B2B** — protects wholesale
   experience if Shopify B2B falls short; accepts two-platform ops.
3. **BigCommerce Enterprise (single platform)** — both-channel value option.

Adobe Commerce Cloud carried as reference (incumbent-capability benchmark);
composable culled (BR-010).

## Risks Identified

| ID | Risk | Mitigation |
|---|---|---|
| R-1 | Shopify B2B gaps discovered post-decision | Parity-plus scripted demo with real trade pricing agreements before ADR approval |
| R-2 | Storefront rationalisation damages brand-principal relationships | Brand consultation round before CEO count decision (T-1); per-brand landing experiences within shared storefronts |
| R-3 | SEO loss during consolidation | DAT-003 redirect programme with pre/post ranking monitoring |
| R-4 | Decision deadlock with Project 004 | Joint 004/005 architecture checkpoint with a single decision paper to the COO |
