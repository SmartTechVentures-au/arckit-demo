# Tech Note: MYOB AccountRight Integration for Inventory/WMS Platforms

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-TECH-myob-accountright-integration-v1.0 |
| **Document Type** | Tech Note |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-06-29 |
| **Last Updated** | 2026-06-29 |
| **Owner** | Cycle Motion solution architecture advisor (Velma Dinkley) |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-06-29 | ArcKit AI | Initial creation from `/arckit:research` agent | PENDING | PENDING |
| 1.1 | 2026-06-29 | ArcKit AI | Added Odoo's non-native MYOB AccountRight position (RSCH v1.1) | PENDING | PENDING |
| 1.2 | 2026-06-30 | ArcKit AI | Broadened native/connector landscape — Ostendo (native), MYOB Acumatica (platform replacement), ERPNext, Retail Express, cull-list (RSCH v1.2) | PENDING | PENDING |

---

## Summary

When selecting an inventory or warehouse-management platform to sit alongside **MYOB AccountRight**, the decisive architectural question is whether the platform integrates with MYOB **natively** or via **third-party middleware**. This is often more important than feature-tick comparisons, because the MYOB link must carry orders, stock movements, bills and invoices reliably and idempotently. The market splits sharply: MYOB-native operations/WMS add-ons (e.g. **Datapel**, **Ostendo**) vs. multichannel hubs and open-source ERPs whose native accounting targets are Xero/QuickBooks or their own GL (e.g. Cin7, Unleashed, Odoo, ERPNext), which require middleware to reach MYOB AccountRight. A third option is to **replace AccountRight with MYOB's own cloud ERP (MYOB Acumatica)**, removing the integration question entirely.

## Key Findings

- **MYOB-native is rare.** Datapel Cloud.WMS is purpose-built as an MYOB add-on with native two-way sync to MYOB AccountRight (orders, bills, inventory, invoices) and full audit trails. The Datapel/Connector adaptor supports **MYOB AccountRight versions 8.5–19.7** — so the exact AccountRight edition/version must be captured before procurement.
- **Major multichannel hubs are not MYOB-native.** Both **Cin7** (Core/Omni) and **Unleashed** natively target **Xero and QuickBooks Online**; neither ships a native MYOB AccountRight connector. Reaching MYOB requires third-party middleware (e.g. SAAS Integrator, GrowthPath, Zoho Flow, Amaka) or a custom integration.
- **Middleware is a design trade-off, not a blocker.** It adds a vendor, a cost line (~A$300/mo order-of-magnitude), and a coupling point in the path that must remain idempotent and recoverable. It should be priced, owned, kept in a replaceable layer, and pilot-tested for duplicate-order/oversell handling.
- **Full ERPs make it worse, not better (added v1.1).** Odoo is a full ERP that *ships its own accounting*, so MYOB is peripheral to its design and no maintained two-way MYOB AccountRight connector exists. The available paid app does not confirm AccountRight support or two-way sync, and the OCA `connector-accountedge` module targets the older MYOB *AccountEdge*, not AccountRight. "Odoo + MYOB" therefore places possibly the *least proven* accounting connector of any option into the critical path. The clean Odoo answer is to let Odoo's own accounting be the books (replacing MYOB) — which is precisely what a "with MYOB" requirement rules out.
- **Ostendo is a second genuinely MYOB-native option (added v1.2).** Ostendo (Development-X, AU/NZ) bolts natively onto MYOB AccountRight / AccountRight Live with a live link that posts every few minutes — no middleware — and adds deep manufacturing (BOM with routings, job costing) and a barcode WMS. It is the strongest evidence that "MYOB-native" is a small but real category, not a category of one (Datapel). Confirm its Shopify-multi-store/Magento connector depth, which is its one open question.
- **MYOB Acumatica removes the question by replacing AccountRight (added v1.2).** MYOB's own cloud ERP (formerly MYOB Advanced) has inventory, WMS and manufacturing built in; there is no third-party accounting connector because the ERP *is* the accounting system. This is a platform-migration answer (highest cost), suitable when AccountRight becomes the scaling ceiling.
- **ERPNext repeats the Odoo pattern (added v1.2).** Like Odoo, ERPNext ships its own accounting and has no native MYOB connector — middleware/custom only — plus open-source self-maintenance. Strong BOM, same caveat.
- **Retail/POS and Xero/QuickBooks-native tools are weak MYOB fits (added v1.2).** Retail Express by Maropost is AU-hosted and on the MYOB marketplace but oriented to MYOB *Business* and retail-not-manufacturing. Fishbowl (QuickBooks-native), Katana (Xero/QuickBooks), inFlow, Linnworks, Lightspeed, Square etc. have no MYOB-AccountRight-native path. SalesIn connects to MYOB but is a sales-order tool, not an inventory source of truth.
- **Architectural implication for "source of truth" decisions.** Keeping MYOB as inventory master (Path 1) favours a native MYOB WMS and avoids middleware. Demoting MYOB to accounting behind a hub (Path 2) still requires a reliable MYOB write-path — which, for the major hubs, is middleware-based.
- **Shopify→MYOB** is a separate, well-served niche (e.g. "Shopify by Amaka" on the MYOB App Marketplace) used to automate B2C order entry when MYOB remains the master.

## Relevance to Projects

- **Project 001 — Inventory & Warehouse Management Uplift (Cycle Motion)**: directly drives the Path 1 vs Path 2 decision. Path 1 (Datapel) is MYOB-native; Path 2 (Cin7/Unleashed) needs MYOB middleware. Applicable to any future Australian SME project where MYOB AccountRight is the incumbent accounting/inventory system and a WMS or multichannel hub is being added.

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RSCH | ARC-001-RSCH-v1.0.md | Research Findings | 001-inventory-warehouse-uplift/research/ | Source research with full citations |

### Citations

| Citation ID | Source | Category | Captured Claim |
|-------------|--------|----------|----------------|
| RSCH-C1 | https://datapel.com/integrations/myob-integration/ | MYOB integration | Datapel native two-way MYOB AccountRight sync |
| RSCH-C5 | https://www.growthpath.com.au/Business-IT/ | MYOB integration | No native Cin7↔MYOB AccountRight connector; middleware required |
| RSCH-C6 | https://www.zohoflow.com/en-in/apps/myob-accountright-live/integrations/unleashed-software/ | MYOB integration | Unleashed↔MYOB AccountRight via integration platform |
| RSCH-C9 | https://www.squizz.com/docs/connector/Connector-Adaptor-Datapel-Warehouse-Management-System-(version-9).html | Compatibility | MYOB AccountRight v8.5–19.7 supported by Datapel adaptor |
| RSCH-C10 | https://www.saasintegrator.com/cin7core-inventory-integration/ | MYOB middleware | SAAS Integrator provides Cin7 Core ↔ MYOB integration |
| RSCH-C17 | https://apps.odoo.com/apps/modules/15.0/wt_myob_connector | MYOB integration (Odoo) | Warlock "MYOB Odoo Connector"; MYOB edition unspecified; import-skewed; two-way unconfirmed |
| RSCH-C18 | https://github.com/OCA/connector-accountedge | MYOB integration (Odoo) | OCA module targets MYOB AccountEdge, not AccountRight |

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
