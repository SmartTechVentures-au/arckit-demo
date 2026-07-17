# Vendor Profile: Unleashed

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-VEND-unleashed-v1.0 |
| **Document Type** | Vendor Profile |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-06-29 |
| **Last Researched** | 2026-06-29 |
| **Owner** | Cycle Motion solution architecture advisor (Velma Dinkley) |
| **Confidence** | High (5+ data points: pricing, manufacturing/BOM, integrations, MYOB path, reviews) |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-06-29 | ArcKit AI | Initial creation from `/arckit:research` agent | PENDING | PENDING |

---

## Overview

Unleashed Software (NZ-origin; part of the Access Group) is a cloud **inventory and order-management platform** with a strong manufacturing pedigree, popular with Australian/NZ manufacturers and assembly-driven businesses. It is the lead **Path 2** hub candidate for the Cycle Motion uplift (inventory/order hub as system of record, MYOB demoted to accounting). Its native accounting targets are Xero and QuickBooks Online; MYOB AccountRight is reached via third-party middleware.

## Products & Services

- **Inventory & order management** — purchasing, sales orders, multichannel stock, multi-warehouse.
- **Manufacturing** — digital BOM, assembly/disassembly, MRP (Advanced Inventory Manager), Kanban production planning. Strongest manufacturing fit of the researched hubs.
- **Warehouse Management & Multi-Bin** — available as a paid add-on (A$149/mo); Warehouse Devices A$49 each.
- **eCommerce connectors** — supported, vendor-maintained for Shopify, WooCommerce, Amazon. B2B eCommerce add-on (A$119/mo).
- **Accounting integration** — native Xero / QuickBooks Online; MYOB via middleware (e.g. Zoho Flow / connector platforms).

## Pricing Model

AUD subscription tiers (transparent, published):

- **Core**: A$449/mo · 3 users · 100 sales orders/mo (upgradable to 500/1,500/3,000/unlimited) · 250k API calls/mo · 3 integrations · +A$69/user.
- **Pro**: A$819/mo · 5 users · 100 orders/mo (same upgrades) · 500k API calls/mo · 5 integrations · +A$79/user.
- **Add-ons**: MRP A$129/mo · Warehouse Mgmt & Multi-Bin A$149/mo · Production & Manufacturing A$69/mo · B2B A$119/mo · Access Analytics A$79/mo.

WMS depth and production are paid add-ons and the base order allowance is low (100/mo) — a realistic Cycle Motion configuration (Pro + Multi-Bin + Production + order-volume uplift) sits well above the A$819 headline. Indicative 3-year TCO for the Cycle Motion Path 2 (Unleashed) config: ~A$88k incl. MYOB middleware, implementation, hardware, training.

## UK Government Presence

- G-Cloud listed: unknown (not applicable — Cycle Motion is a private Australian company)
- DOS listed: unknown (not applicable)
- UK data centres: unknown (NZ-origin; confirm AU data residency directly)

## Government Award History

> Not applicable. No UK procurement-notice evidence applies. `{unknown}`

- Sample awards: {none on record}

## Strengths

- Strongest manufacturing/BOM fit of the hubs (MRP, Kanban, assembly/disassembly) — good match to a custom wheel-build line.
- Generally good reliability and support reputation; praised for inventory accuracy and responsive follow-up (one manufacturer cited near-flawless results at 500 orders / 1,500 items per week).
- Supported, vendor-maintained Shopify connector; single source of truth across channels.
- AUD list pricing (no FX exposure); transparent published tiers.

## Weaknesses

- No native MYOB AccountRight connector — third-party middleware required (adds a vendor and a coupling point in the idempotent-sync path).
- WMS multi-bin and production are paid add-ons and base order allowance is low — real cost climbs with order volume and warehouse depth.
- Reviews flag a rigid UI / steep learning curve and a poorly-communicated paid "premium support" tier (A$79/mo) with refund disputes.
- Magento/Adobe Commerce integration fit needs validation (native emphasis is Shopify/WooCommerce/Amazon).

## Projects Referenced In

- Project 001 — Inventory & Warehouse Management Uplift (Cycle Motion) — Path 2 lead hub candidate.

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RSCH | ARC-001-RSCH-v1.0.md | Research Findings | 001-inventory-warehouse-uplift/research/ | Source research with full citations |

### Citations

| Citation ID | Source | Category | Captured Claim |
|-------------|--------|----------|----------------|
| RSCH-C3a | https://www.unleashedsoftware.com/en-au/pricing/ | Pricing | Core A$449 / Pro A$819; add-ons Multi-Bin A$149, Production A$69, MRP A$129 |
| RSCH-C6 | https://www.zohoflow.com/en-in/apps/myob-accountright-live/integrations/unleashed-software/ | MYOB integration | Unleashed↔MYOB AccountRight via integration platform (no native connector evidenced) |
| RSCH-C14 | https://apps.shopify.com/unleashed-software | Manufacturing/Shopify | Digital BOM, assembly/disassembly, MRP, Kanban; supported Shopify connector |
| RSCH-C15 | https://www.capterra.com/p/126644/Unleashed/reviews/ | Reviews | Inventory accuracy + responsive support; rigid UI; premium-support communication |

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
