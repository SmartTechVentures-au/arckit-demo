# Vendor Profile: MYOB Acumatica (formerly MYOB Advanced)

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-VEND-myob-acumatica-v1.0 |
| **Document Type** | Vendor Profile |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-06-30 |
| **Last Researched** | 2026-06-30 |
| **Owner** | Cycle Motion solution architecture advisor (Chris McKelt) |
| **Confidence** | High (5+ data points: editions, per-user pricing, implementation cost, manufacturing/WMS scope, AU hosting/support) |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-06-30 | ArcKit AI | Initial creation from `/arckit:research` agent (added during RSCH v1.2 landscape scan) | PENDING | PENDING |

---

## Overview

MYOB Acumatica (formerly MYOB Advanced) is **MYOB's own cloud ERP**, built on the Acumatica platform, with financials, distribution/inventory, warehouse management and manufacturing built in. For the Cycle Motion uplift it represents a **distinct Path 4** — *upgrade the MYOB platform itself*: retire AccountRight and adopt MYOB's enterprise-tier cloud ERP. This removes the third-party accounting-integration problem entirely (the ERP **is** the accounting system) while keeping Cycle Motion inside the MYOB vendor relationship with AU hosting and commercial support. It is the most capable and most expensive option, and a genuine accounting-platform migration — best positioned as the strategic answer for when AccountRight becomes the growth ceiling, not the minimal-disruption first move the brief requests.

## Products & Services

- **Editions**: Standard, Plus, Enterprise, and a dedicated **Manufacturing edition** (production, MRP, materials planning, cost control); also project- and service-based editions.
- **Capabilities**: financials/GL, inventory/distribution, warehouse management, manufacturing/MRP, multi-entity, external API.
- **eCommerce**: via Acumatica commerce connectors / AU partners (confirm Shopify-multi-store and Magento handling).
- **Accounting integration**: not applicable — it replaces AccountRight; no third-party accounting connector required.

## Pricing Model

Per-user, per-month subscription: **A$104 (Standard) / A$139 (Plus) / A$179 (Enterprise)**. Implementation typically **A$50,000–150,000** depending on scope; ongoing subscription ~A$2,000–5,000/month (covers cloud hosting, security, backups). Indicative 3-year TCO for Cycle Motion: **~A$140,000–280,000** (risk-adjusted ~A$170k–340k) — the highest-cost option, reflecting that it is an ERP platform migration, not a WMS add-on.

## UK Government Presence

- G-Cloud listed: not applicable (Cycle Motion is a private Australian company)
- DOS listed: not applicable
- UK data centres: not applicable; AU-hosted (relevant to Australian Privacy Principles — confirm region)

## Government Award History

> Not applicable. No UK procurement-notice evidence applies. `{unknown}`

- Sample awards: {none on record}

## Strengths

- MYOB's own product — inventory, WMS and manufacturing built in; **no third-party accounting integration to maintain** (removes the connector/idempotent-sync risk that affects every Path 2 option).
- AU-hosted, commercially supported, MYOB partner channel; dedicated Manufacturing edition fits Cycle Motion's BOM needs.
- Scales well — directly addresses the Principle 2 concern that AccountRight is the multichannel/volume ceiling.
- Keeps Cycle Motion in a familiar vendor relationship (reduced vendor-change risk).

## Weaknesses

- Full **accounting-platform migration** (replace AccountRight) — the largest change of any option, with data-migration, retraining and cutover risk.
- **Highest cost** by a wide margin (A$104–179/user/mo + A$50k–150k implementation).
- Heavier than the brief's "minimal disruption / single source of inventory truth" intent for the near term.
- Shopify-multi-store and Magento connector depth must be confirmed with MYOB/partners.

## Projects Referenced In

- Project 001 — Inventory & Warehouse Management Uplift (Cycle Motion) — Path 4 strategic option (added in RSCH v1.2). Recommended as the scaling-ceiling answer for when AccountRight limits growth, not as the first move; if pursued, scope as a distinct ERP-migration project with its own business case.

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RSCH | ARC-001-RSCH-v1.0.md (now v1.2) | Research Findings | 001-inventory-warehouse-uplift/research/ | Source research with full citations |

### Citations

| Citation ID | Source | Category | Captured Claim |
|-------------|--------|----------|----------------|
| RSCH-C23 | https://www.myob.com/au/erp-software/products/myob-acumatica ; https://www.cloudfactory.co/solutions/erp/myob-acumatica/pricing ; https://businesshub.com.au/erp/how-much-does-myob-acumatica-cost | MYOB Acumatica | MYOB's cloud ERP; Standard A$104 / Plus A$139 / Enterprise A$179 per user/mo; Manufacturing edition; implementation A$50k–150k; ongoing ~A$2k–5k/mo; inventory/WMS/mfg built in |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| — | — | — |

---

**Generated by**: ArcKit `/arckit:research` agent
**Generated on**: 2026-06-30
**ArcKit Version**: 5.15.1
**Project**: Inventory & Warehouse Management Uplift (Project 001)
**Model**: Claude Opus 4.8 (1M context)
