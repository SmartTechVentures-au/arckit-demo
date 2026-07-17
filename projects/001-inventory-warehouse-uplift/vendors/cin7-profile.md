# Vendor Profile: Cin7

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-VEND-cin7-v1.0 |
| **Document Type** | Vendor Profile |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-06-29 |
| **Last Researched** | 2026-06-29 |
| **Owner** | Cycle Motion solution architecture advisor (Velma Dinkley) |
| **Confidence** | High (5+ data points: pricing, product tiers, integrations, MYOB path, reviews, company/hosting) |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-06-29 | ArcKit AI | Initial creation from `/arckit:research` agent | PENDING | PENDING |

---

## Overview

Cin7 is a New Zealand-origin (Auckland, founded 2011) cloud **inventory and order-management** vendor, acquired by Rubicon Technology Partners in 2019 (~US$133M), serving ~8,000 customers across 75 countries and hosted on Microsoft Azure. It offers two products: **Cin7 Core** (turnkey SME inventory/WMS/light-manufacturing with native connectors incl. Magento + Shopify) and **Cin7 Omni** (customisable, multi-entity enterprise tier, 700+ integrations). It is a **Path 2** hub alternative for the Cycle Motion uplift. The company brief explicitly flags reliability/support concerns that this research confirms as current.

## Products & Services

- **Cin7 Core** — purchasing, sales, standard/advanced WMS, light manufacturing (assembly/kits; MRP add-on or Pro tier); native connectors to Shopify, Amazon, eBay, Magento, WooCommerce; B2B portal add-on; RMA on Advanced.
- **Cin7 Omni** — multi-entity/multi-brand, customisable, 700+ integrations, open API; suited to many storefronts/entities.
- **Accounting integration** — native Xero / QuickBooks Online; no native MYOB AccountRight connector (middleware required, e.g. SAAS Integrator / GrowthPath).

## Pricing Model

List prices in USD (+taxes), FX exposure for an Australian buyer:

- **Cin7 Core — Standard**: US$349/mo · 5 users · 6,000 orders/yr · 2 integrations.
- **Cin7 Core — Pro** (most popular): US$599/mo · 10 users · 24,000 orders/yr · 4 integrations · includes MRP.
- **Cin7 Core — Advanced**: US$999/mo · 15 users · 120,000 orders/yr · 6 integrations · advanced WMS + RMA.
- **Cin7 Omni**: custom pricing · 8 users base · uncapped orders · 5 integrations.

For ~5–7 storefronts, Core Pro (4 integrations) is the likely floor; more connectors push toward Advanced/Omni. Indicative 3-year TCO for the Cycle Motion Path 2 (Cin7 Core) config: ~A$72k incl. MYOB middleware, implementation, hardware, training (excludes shipping layer; FX risk).

## UK Government Presence

- G-Cloud listed: unknown (not applicable — Cycle Motion is a private Australian company)
- DOS listed: unknown (not applicable)
- UK data centres: hosted on Microsoft Azure; specific region/AU residency to confirm directly

## Government Award History

> Not applicable. No UK procurement-notice evidence applies. `{unknown}`

- Sample awards: {none on record}

## Strengths

- Broadest connector library, including native Magento and Shopify (Core) and multi-entity management (Omni) for many storefronts.
- Light manufacturing/MRP for BOM (assembly/kits on Standard, MRP on Pro).
- Large, established customer base (~8,000 across 75 countries); Azure-hosted.
- Built to scale channels and volume.

## Weaknesses

- No native MYOB AccountRight connector — third-party middleware required (adds a vendor and a coupling point in the idempotent-sync path).
- Reliability/support reputation risk is real and current (2025–2026): Shopify sync drops, stock disconnecting while "connected", blank/partial orders, variant-mapping breakage, frequent price increases, slow email-only support with multi-week/-month ticket delays.
- USD list pricing → FX exposure; higher tiers expensive for a small business.
- Path 2 migration reworks the MYOB relationship — implementation quality and support become the principal risk.

## Projects Referenced In

- Project 001 — Inventory & Warehouse Management Uplift (Cycle Motion) — Path 2 hub alternative; proceed only if reference checks and pilot clear the sync-reliability/support concerns.

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RSCH | ARC-001-RSCH-v1.0.md | Research Findings | 001-inventory-warehouse-uplift/research/ | Source research with full citations |

### Citations

| Citation ID | Source | Category | Captured Claim |
|-------------|--------|----------|----------------|
| RSCH-C3 | https://www.cin7.com/pricing/ | Pricing | Core Standard US$349 / Pro US$599 / Advanced US$999; users, orders, integrations |
| RSCH-C4 | https://www.cin7.com/blog/cin7-core-or-omni-which-one-is-right-for-your-business/ | Product fit | Core native Magento/Shopify; Omni multi-entity, 700+ integrations |
| RSCH-C5 | https://www.growthpath.com.au/Business-IT/ | MYOB integration | No native Cin7↔MYOB AccountRight connector; middleware required |
| RSCH-C11 | https://www.cin7.com/about-us/ | Company/hosting | Founded 2011 Auckland NZ; Rubicon 2019; ~8,000 customers; Azure-hosted |
| RSCH-C12 | https://apps.shopify.com/cin7-connected-inventory-v2/reviews | Reviews | Shopify sync issues: variant deletion, can't update stock/prices |
| RSCH-C13 | https://www.getapp.com/operations-management-software/a/cin7/reviews/ | Reviews/support | Stock disconnects, blank orders; slow email-only support; price increases |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| — | — | — |

---

**Generated by**: ArcKit `/arckit:research` agent
**Generated on**: 2026-06-29
**ArcKit Version**: 5.15.1
**Project**: Inventory & Warehouse Management Uplift (Project 001)
**Model**: Claude Opus 4.8 (1M context)
