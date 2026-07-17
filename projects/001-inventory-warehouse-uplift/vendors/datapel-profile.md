# Vendor Profile: Datapel

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-VEND-datapel-v1.0 |
| **Document Type** | Vendor Profile |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-06-29 |
| **Last Researched** | 2026-06-29 |
| **Owner** | Cycle Motion solution architecture advisor (Velma Dinkley) |
| **Confidence** | High (5+ data points: pricing, MYOB integration, BOM, WMS depth, reviews, version compatibility) |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-06-29 | ArcKit AI | Initial creation from `/arckit:research` agent | PENDING | PENDING |

---

## Overview

Datapel Systems Pty Ltd is an Australian/New Zealand vendor of **Datapel Cloud.WMS**, a cloud order- and warehouse-management system purpose-built as an **MYOB-native add-on**. It is designed for SMEs (wholesalers, retailers, manufacturers, distributors) that run MYOB and need warehouse discipline and inventory control beyond what MYOB alone provides. Trusted by 200+ MYOB customers across AU/NZ. It is the lead candidate for **Path 1** (keep MYOB AccountRight as inventory master; add a WMS layer) in the Cycle Motion uplift.

## Products & Services

- **Datapel Cloud.WMS** — bins/locations, directed pick/pack/putaway, barcode scanning, backorder management, batch/expiry; 50+ reports.
- **Manufacturing module** — Bill of Materials + Work Orders; components decrement from stock and finished goods are added, traceable back to the original purchase order.
- **MYOB integration** — native two-way sync to MYOB AccountRight (orders, bills, inventory, invoices) with audit trails. The Datapel/Connector adaptor supports WMS v9 and MYOB AccountRight v8.5–19.7.
- **eCommerce/fulfilment integrations** — available (specific platforms to confirm in demo; Starshipit lists Datapel as a supported shipping integration).

## Pricing Model

Subscription. Entry from **A$120/month**; no free version (free trial available). Positioned as "pay for the onboarding support you need", "no hidden costs", "no lock-in". Realistic multi-bin/BOM/multichannel configuration will exceed the entry price — obtain a quote against discovery data (SKU count, order volume, bin count). Indicative 3-year TCO for Cycle Motion's Path 1 core: ~A$34k (subscription + onboarding + hardware + training), excluding a companion Shopify-automation workstream and shipping layer.

## UK Government Presence

- G-Cloud listed: no (not applicable — AU/NZ vendor; Cycle Motion is a private Australian company)
- DOS listed: no (not applicable)
- UK data centres: unknown (not relevant; AU/NZ focus)

## Government Award History

> Not applicable. Cycle Motion is a private Australian company; no UK procurement-notice evidence applies. `{unknown}`

- Total awarded value (UK gov contracts): unknown / not applicable
- Award count: unknown / not applicable
- Sample awards: {none on record}

## Strengths

- MYOB-native two-way sync to AccountRight — no middleware in the MYOB path (supports loose coupling and idempotent-sync principles).
- Genuine WMS depth: bins, guided pick/pack/putaway, barcode scanning.
- Built-in BOM / work-order manufacturing — keeps component master native to MYOB (single source of truth).
- AU/NZ vendor with AU-relevant support; low entry price; "no lock-in".
- Preserves the existing Magento↔MYOB integration (lowest-disruption migration).

## Weaknesses

- Does not, by itself, automate the five manual Shopify stores — a separate Shopify-to-MYOB workstream is needed.
- MYOB AccountRight remains the multichannel inventory ceiling (long-term scaling concern).
- Cycle-count and lot/serial depth not clearly evidenced publicly — confirm in demo/pilot.
- Smaller review base (~53 Capterra); some reports of slow query turnaround and multi-product onboarding complexity (~3 months in one case).

## Projects Referenced In

- Project 001 — Inventory & Warehouse Management Uplift (Cycle Motion) — Path 1 lead candidate.

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RSCH | ARC-001-RSCH-v1.0.md | Research Findings | 001-inventory-warehouse-uplift/research/ | Source research with full citations |

### Citations

| Citation ID | Source | Category | Captured Claim |
|-------------|--------|----------|----------------|
| RSCH-C1 | https://datapel.com/integrations/myob-integration/ | MYOB integration | Native two-way MYOB AccountRight sync; bins, picking, barcode |
| RSCH-C2 | https://www.myob.com/au/apps/datapel-warehouse-management-system | Vendor/pricing | From A$120/mo; 200+ AU/NZ MYOB customers |
| RSCH-C7 | https://www.datapel.com/manufacturing/ | BOM | BOM + Work Orders; components decrement, finished stock added |
| RSCH-C8 | https://www.capterra.com.au/software/199201/wms | Reviews | ~53 reviews; support mixed-positive; onboarding pace |
| RSCH-C9 | https://www.squizz.com/docs/connector/Connector-Adaptor-Datapel-Warehouse-Management-System-(version-9).html | Compatibility | MYOB AccountRight v8.5–19.7 supported |

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
