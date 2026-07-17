# Vendor Profile: Ostendo (Development-X)

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-VEND-ostendo-v1.0 |
| **Document Type** | Vendor Profile |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-06-30 |
| **Last Researched** | 2026-06-30 |
| **Owner** | Cycle Motion solution architecture advisor (Velma Dinkley) |
| **Confidence** | High (5+ data points: MYOB-native integration, BOM/job-costing, WMS/Freeway, POS, pricing model, AU presence) |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-06-30 | ArcKit AI | Initial creation from `/arckit:research` agent (added during RSCH v1.2 landscape scan) | PENDING | PENDING |

---

## Overview

Ostendo, by **Development-X Limited** (AU/NZ), is an operations-management / light-ERP product that **bolts natively onto MYOB AccountRight** to add deep inventory, manufacturing, job costing, service and warehouse capability that AccountRight lacks. For the Cycle Motion uplift it is a **Path 1** option — keep MYOB AccountRight as the financial system of record and layer Ostendo for operations — and a **direct rival to Datapel** on the MYOB-native + low-risk axis, with notably deeper manufacturing and job-costing. The one open question for this brief is the depth of its Shopify-multi-store and Magento connectors.

## Products & Services

- **Ostendo Operations** — inventory, assembly/work orders, BOM with routings, job costing, job scheduling, labour timesheets, three-way purchase matching, service management, pricing/discounting.
- **Ostendo Freeway** — mobile barcode app for picking, receiving and warehouse operations (Android/iOS); multi-location.
- **POS** — full point-of-sale: touchscreen, multi-station, barcode scanning, laybys, EFTPOS.
- **MYOB integration** — native, seamless live link to MYOB AccountRight / AccountRight Live; data posts automatically every few minutes for near-real-time integrated financials.
- **eCommerce / web-store** — integration available (live stock sync, multi-warehouse), typically via AU integrators (e.g. iBis / MyIntegrator); Shopify-multi-store and Magento depth to confirm.

## Pricing Model

Transparent, all-modules pricing (no per-module upsell, "no hidden fees"); Freeway mobility add-on (~A$50/user/yr-class). Confirm a current quote against G-6 discovery data. Indicative 3-year TCO for Cycle Motion's Path 1 (Ostendo): ~A$45k–60k all-in (comparable to or slightly above Datapel), partner-dependent, excluding the shipping layer.

## UK Government Presence

- G-Cloud listed: not applicable (AU/NZ vendor; Cycle Motion is a private Australian company)
- DOS listed: not applicable
- UK data centres: not applicable

## Government Award History

> Not applicable. No UK procurement-notice evidence applies. `{unknown}`

- Sample awards: {none on record}

## Strengths

- MYOB-AccountRight-native with a live link (near-real-time financials) — no third-party middleware in the accounting path (supports Principles 9 and 10).
- Deep manufacturing for a MYOB-native product: BOM with routings, assembly/work orders, job costing, scheduling, three-way matching — arguably deeper than Datapel.
- Freeway barcode WMS (picking/receiving/warehouse, multi-location) and full POS.
- AU/NZ vendor, MYOB App Marketplace listed, established AU integrator network; transparent all-modules pricing.

## Weaknesses

- Shopify-multi-store and Magento/Adobe Commerce connector depth must be confirmed — typically delivered via AU integrators rather than a first-party multi-store connector.
- Smaller brand profile / review base than the SaaS hubs (Cin7, Unleashed).
- As a Path 1 option it does not, by itself, create a single multichannel hub — MYOB AccountRight remains the long-term inventory ceiling (Principle 2).

## Projects Referenced In

- Project 001 — Inventory & Warehouse Management Uplift (Cycle Motion) — Path 1 rival to Datapel (added in RSCH v1.2). Recommended to join Datapel in the evaluate/score shortlist; confirm Shopify-multi-store/Magento connector depth in the demo/pilot.

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RSCH | ARC-001-RSCH-v1.0.md (now v1.2) | Research Findings | 001-inventory-warehouse-uplift/research/ | Source research with full citations |

### Citations

| Citation ID | Source | Category | Captured Claim |
|-------------|--------|----------|----------------|
| RSCH-C24 | https://www.ostendo.info/ostendo/accounting/myob.php ; https://www.ostendo.info/ | MYOB integration / manufacturing | Native MYOB AccountRight Live link posting every few minutes; BOM with routings, assembly/work orders, job costing, three-way matching |
| RSCH-C27 | https://www.ostendo.info/ ; https://www.myintegrator.com.au/integrate/ostendo/ | WMS/POS/eCommerce | Freeway barcode app (picking/receiving/warehouse, multi-location); full POS; web-store + POS integration with live stock sync |

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
