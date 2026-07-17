# Vendor Profile: Odoo

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-VEND-odoo-v1.0 |
| **Document Type** | Vendor Profile |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-06-29 |
| **Last Researched** | 2026-06-29 |
| **Owner** | Cycle Motion solution architecture advisor (Velma Dinkley) |
| **Confidence** | High (5+ data points: editions/pricing, MYOB connector maturity, BOM/MRP, WMS, eCommerce connectors, implementation cost) |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-06-29 | ArcKit AI | Initial creation from `/arckit:research` agent (added during RSCH v1.1) | PENDING | PENDING |

---

## Overview

Odoo S.A. (Belgium) develops **Odoo**, a full open-source **ERP** spanning Inventory, Manufacturing/MRP, Sales, Purchase, Barcode/WMS, eCommerce, and its own Accounting. For the Cycle Motion uplift it was added at user request as "Odoo with MYOB integration". Because Odoo is a whole back-office suite rather than a focused WMS or inventory hub, it is **not a like-for-like Datapel/Cin7/Unleashed swap**. It can play **Path 2** (Odoo as inventory/order/manufacturing hub, MYOB kept for accounting) or the more radical **Path 3** (Odoo's own accounting eventually replaces MYOB — out of the current project's scope). Odoo's manufacturing and warehouse depth is best-in-class among the candidates; its weakness for this brief is the MYOB accounting integration and the open-source maintenance model.

## Products & Services

- **Editions**: Community (free, open-source, LGPL-3.0, self-hosted) and Enterprise (per-user + per-app subscription, managed updates/support, Studio, external API, multi-company).
- **Hosting**: Odoo Online (Odoo-hosted, Enterprise only), Odoo.sh (PaaS, supports custom modules), or on-premise/self-hosted (Community or Enterprise).
- **Relevant modules**: Inventory (multi-warehouse, multi-bin), Manufacturing/MRP (multi-level BOM, finite-capacity planning, work centres), Barcode (incl. manufacturing operations), Purchase, Sales, eCommerce connectors.
- **eCommerce connectors**: maintained Shopify and Magento 2 connectors map multiple stores to Odoo warehouses with per-location, BOM-aware stock sync.
- **MYOB integration**: NOT native. Options found: a low-maturity paid app (Warlock "MYOB Odoo Connector", ~US$315 one-time, MYOB edition unconfirmed, import-skewed, two-way unconfirmed); an OCA module targeting MYOB *AccountEdge* (not AccountRight); or middleware/custom.

## Pricing Model

- **Community**: A$0 licence (open-source) — but you own hosting, upgrades, patching, and connector maintenance.
- **Enterprise**: ~A$45–65 per user per month (annual billing); apps/modules priced individually.
- **Implementation (the dominant cost)**: AU SME projects typically A$15k–60k (partner fees A$8k–50k+; ~A$120–350/hr), plus ~A$5k–10k/yr ongoing. Indicative 3-year TCO for a Cycle Motion Odoo-Enterprise hub: ~A$62k–66k base, partner-dependent range A$60k–110k (risk-adjusted A$80k–135k), excluding the shipping layer.

## UK Government Presence

- G-Cloud listed: not applicable (Cycle Motion is a private Australian company)
- DOS listed: not applicable
- UK data centres: hosting region is buyer-chosen (Odoo Online/EU, Odoo.sh, or self-hosted AU) — relevant to Australian Privacy Principles, confirm region deliberately

## Government Award History

> Not applicable. No UK procurement-notice evidence applies. `{unknown}`

- Sample awards: {none on record}

## Strengths

- Deepest BOM/MRP and barcode-driven multi-warehouse WMS of any candidate (multi-level BOM, finite-capacity planning).
- Native, maintained multi-store Shopify and Magento 2 connectors with per-location, BOM-aware stock sync.
- No per-seat lock-in with Community (LGPL-3.0); open data; one platform spans inventory, manufacturing, sales and purchasing (scales well).
- Large global and Australian implementation-partner ecosystem.

## Weaknesses

- Weakest MYOB story of all candidates — no maintained two-way MYOB AccountRight connector; the available paid app does not confirm AccountRight support or two-way sync, and the OCA module targets AccountEdge. This puts the least-proven integration into the idempotent-sync critical path (tensions Principles 9 and 10).
- Open-source self-maintenance (Community) or per-user subscription (Enterprise) — Community tensions Principle 1 (buy-over-build) and the brief's "no maintenance treadmill" stance.
- ERP-scale change: broader surface, larger implementation, more training and migration risk than a focused WMS/hub — heavier than the brief's "minimal disruption" intent.
- TCO dominated by implementation-partner scope, hard to bound until G-6 and partner scoping; widest cost range of all options.

## Projects Referenced In

- Project 001 — Inventory & Warehouse Management Uplift (Cycle Motion) — Path 2/Path 3 contender (added in RSCH v1.1). Recommended only if an ERP-scale transformation is deliberately chosen; in that case the honest target is Path 3 (Odoo's own accounting), which exceeds the current brief. For the stated goal (single inventory truth, minimal disruption) it ranks behind Datapel and Unleashed.

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RSCH | ARC-001-RSCH-v1.0.md (now v1.1) | Research Findings | 001-inventory-warehouse-uplift/research/ | Source research with full citations |

### Citations

| Citation ID | Source | Category | Captured Claim |
|-------------|--------|----------|----------------|
| RSCH-C17 | https://apps.odoo.com/apps/modules/15.0/wt_myob_connector | MYOB integration | Warlock "MYOB Odoo Connector" ~US$315 one-time, Odoo 15–17; MYOB edition unspecified; import-skewed; two-way unconfirmed |
| RSCH-C18 | https://github.com/OCA/connector-accountedge | MYOB integration | OCA module connects to MYOB AccountEdge, not AccountRight |
| RSCH-C19 | https://www.odoo.com/pricing ; https://solwing.com.au/blog/erp-odoo-insights-2/odoo-enterprise-pricing-in-australia-2025-8 | Pricing | Community free (LGPL-3.0); Enterprise ~A$45–65/user/mo; Online/Odoo.sh/on-premise hosting |
| RSCH-C20 | https://tryexcept.com.au/blog/odoo-implementation-cost-2026/ | Implementation | AU SME Odoo implementation A$15k–60k; partner ~A$120–350/hr; +A$5k–10k/yr ongoing |
| RSCH-C21 | https://www.odoo.com/documentation/19.0/applications/inventory_and_mrp/manufacturing.html | BOM/WMS | Multi-level BOM, finite-capacity MRP, barcode app integrated with manufacturing; barcode-driven multi-warehouse |
| RSCH-C22 | https://apps.odoo.com/apps/modules/19.0/integration_shopify ; https://apps.odoo.com/apps/modules/16.0/integration_magento2 | eCommerce | Maintained Shopify and Magento 2 connectors; multi-store → Odoo warehouses, per-location BOM-aware stock |

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
