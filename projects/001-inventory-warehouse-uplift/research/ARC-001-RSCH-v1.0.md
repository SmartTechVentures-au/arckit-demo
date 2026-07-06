# Technology and Service Research: Inventory & Warehouse Management Uplift

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-RSCH-v1.2 |
| **Document Type** | Technology & Service Research Findings |
| **Project** | Inventory & Warehouse Management Uplift (Project 001) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.2 |
| **Created Date** | 2026-06-29 |
| **Last Modified** | 2026-06-30 |
| **Review Cycle** | Per phase gate |
| **Next Review Date** | 2026-09-29 |
| **Owner** | Nathan Dyke, CEO — Cycle Motion (Executive Sponsor) |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Cycle Motion leadership (Nathan & Kirralee Dyke), Order & Supply Chain team, solution architecture advisor (Chris McKelt) |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-06-29 | ArcKit AI | Initial creation from `/arckit:research` agent — vendor research, build-vs-buy confirmation, Path 1 vs Path 2 comparison, 3-year TCO | PENDING | PENDING |
| 1.1 | 2026-06-29 | ArcKit AI | Added Odoo (open-source ERP) option with MYOB integration analysis — integrated into options, comparison tables, TCO, requirements coverage, shortlist and recommendation; introduced Path 3 framing (Odoo could eventually replace MYOB) | PENDING | PENDING |
| 1.2 | 2026-06-30 | ArcKit AI | Broadened MYOB-integrating inventory/retail systems landscape (open-source and proprietary) — added MYOB Acumatica (Path 4), Ostendo (MYOB-native, Path 1 rival), Retail Express by Maropost, ERPNext, and a culled landscape scan; updated comparison tables, TCO framing, shortlist, requirements coverage, recommendation and risks | PENDING | PENDING |

---

## Executive Summary

### Research Scope

This document researches commercial inventory and warehouse-management products that can resolve Cycle Motion's fragmented systems architecture, in line with the company brief, the stakeholder goals (G-1…G-7), and the Cycle Motion architecture principles (ARC-000-PRIN-v1.0). No formal requirements specification (`ARC-001-REQ`) exists yet; the company brief, stakeholder analysis, and architecture principles are used as the authoritative basis. **Build-vs-buy is treated as settled (BUY)** per the brief, and this research confirms that position with current market evidence. The bulk of the work is therefore a **Path 1 vs Path 2 source-of-truth comparison** and a focused evaluation of the three shortlisted vendors plus credible alternatives. **v1.1 adds Odoo** — a full open-source ERP — at user request, framed primarily as a Path 2 hub ("Odoo with MYOB integration") and noting a more radical **Path 3** (Odoo eventually replacing MYOB). **v1.2 broadens the landscape** with additional MYOB-integrating inventory/retail systems (proprietary and open-source), most importantly **Ostendo** (a genuinely MYOB-AccountRight-native operations add-on — a Path 1 rival to Datapel) and **MYOB Acumatica** (MYOB's own cloud ERP — a distinct **Path 4**: upgrade the MYOB platform itself), plus Retail Express by Maropost, ERPNext, and a culled scan of weaker-fit options.

**Inputs analysed**: Company brief (Part A entity profile, Part B project overview); 6 stakeholder drivers (SD-1…SD-6) → 7 goals (G-1…G-7) → 4 outcomes (O-1…O-4); 18 architecture principles.

**Research categories identified**: 4 (see below). Categories are derived from the brief and principles, not a fixed list.

**Research approach**: Market research and vendor evaluation via WebSearch / WebFetch — vendor pricing pages, MYOB App Marketplace, Capterra / G2 / Software Advice reviews, Shopify App Store reviews, and Australian integration-partner sites. UK Government Digital Marketplace / G-Cloud and government-code-reuse steps are **not applicable** — Cycle Motion is a private Australian company, not a public-sector body. All currency is **Australian dollars (AUD, A$)** unless stated; some vendor list prices are published in USD and are flagged where used.

### Key Findings

- **Build-vs-buy: confirmed BUY.** WMS and multichannel inventory sync are mature, commoditised categories with proven Australian/NZ products purpose-built for the MYOB + Shopify + Magento stack. A custom build would breach Principle 1 (Buy Over Build) and create exactly the key-person and API-treadmill risk the brief warns against. No further build case is entertained.
- **The decisive technical fact for Path selection: MYOB-native integration is rare.** Datapel is purpose-built as an MYOB-native WMS with deep two-way sync to **MYOB AccountRight** (Connector supports AccountRight versions 8.5–19.7) and its own BOM / work-order manufacturing module. By contrast, **neither Cin7 nor Unleashed ships a native MYOB AccountRight connector** — both natively target Xero/QuickBooks, so a Path 2 hub requires **third-party middleware** (e.g. SAAS Integrator, GrowthPath, Amaka, Zoho Flow) in the critical sync path. This adds cost, a coupling point, and an extra vendor to the very integration that must be idempotent (Principle 10).
- **Path 1 (Datapel) is the lowest-risk move; Path 2 (a hub) is the stronger long-term architecture but a larger, more carefully managed change** — exactly as the brief frames it. Path 1 leaves the five manual Shopify stores as a separate workstream; Path 2 solves warehouse, Shopify automation, and multichannel truth in one architecture at higher migration risk and an extra MYOB-middleware dependency.
- **Cin7's reliability/support reputation concern is real and current.** 2025–2026 reviews (Shopify App Store, GetApp, Capterra) repeatedly report Shopify sync drops, stock disconnects, and slow/email-only support. This does not disqualify Cin7 but makes the brief's reference-check-support and pilot steps mandatory before any commitment. Unleashed reviews are generally stronger on reliability but flag a rigid UI and a poorly-communicated paid-support tier; Datapel reviews are smaller in number and mixed on onboarding speed but generally positive on support.
- **Odoo (added v1.1) is powerful but does not change the recommendation — it reinforces it.** Odoo is a genuinely strong open-source ERP (multi-level BOM/MRP, barcode-driven multi-warehouse WMS, native multi-store Shopify + Magento connectors) and, as Community edition, avoids the per-seat lock-in the brief dislikes. But "Odoo **with** MYOB" reintroduces — arguably *worse* — the exact non-native-accounting risk that makes Path 2 harder than Path 1: **Odoo has its own accounting and does not natively integrate with MYOB AccountRight.** The only Odoo↔MYOB options found are a low-maturity paid app (Warlock "MYOB Odoo Connector", ~US$315 one-time, MYOB edition unconfirmed, import-skewed, two-way unconfirmed), an OCA module targeting the *older AccountEdge* (not AccountRight), or middleware/custom — all sitting in the idempotent-sync critical path (tensions Principles 9 & 10). On top of that, Community/self-hosted means **owning maintenance** — a direct tension with Principle 1 and the brief's "no maintenance treadmill" stance. Odoo is a credible Path 2/Path 3 contender only if Cycle Motion deliberately accepts an ERP-scale project and the accounting-integration risk.
- **The broadened landscape (v1.2) surfaces two genuinely MYOB-native contenders that join Datapel — and confirms the rest re-hit the same middleware wall.** **Ostendo** (Development-X, AU/NZ) is **natively integrated with MYOB AccountRight** (live link posting every few minutes) and is *deeper* than Datapel on manufacturing — BOM-with-routings, job costing, three-way matching — plus Freeway barcode WMS and POS. It is a **direct Path 1 rival to Datapel** and should join the evaluate/score shortlist. **MYOB Acumatica** (MYOB's own cloud ERP, formerly MYOB Advanced) is a distinct **Path 4** — *replace AccountRight with MYOB's enterprise tier* (inventory, WMS, manufacturing built in, no third-party accounting integration at all) — credible if Cycle Motion is willing to migrate accounting platforms, but materially more expensive (A$104–179/user/mo + A$50k–150k implementation). **Every other newly-scanned option re-introduces the middleware/no-MYOB-native problem**: ERPNext (open-source, strong BOM, *no* native MYOB — middleware + self-maintenance, same caveat as Odoo); Retail Express by Maropost (AU retail/POS, Sydney-hosted, but MYOB *Business* oriented and retail- not manufacturing-focused); and Fishbowl/Katana/inFlow/Linnworks/Lightspeed/Square etc. are Xero/QuickBooks-native and culled as weak MYOB fit. **Net: the MYOB-native shortlist grows from one (Datapel) to a credible three — Datapel, Ostendo, and (if platform migration is on the table) MYOB Acumatica — which strengthens, not weakens, the Path 1 / stay-MYOB-native thesis.**
- **A shipping/carrier layer (Starshipit) is a likely fourth component** regardless of Path, integrating Australia Post / Aramex / Sendle etc. to all three candidate cores and to Shopify/MYOB — keeping carrier integration off the critical-build path (Principle 1).

### Build vs Buy Summary

> All figures are indicative 3-year TCO for a small Australian business (~5–7 storefronts, modest order volume), AUD, list prices, before negotiation. They depend on the open discovery data (SKU count, order volume per channel, MYOB edition, confirmed storefront count) per goal G-6 and must be re-quoted against reality before procurement.

| Approach | Categories | Indicative 3-Year TCO (AUD) | Rationale |
|----------|-----------|------------------------------|-----------|
| **BUILD** (Custom WMS/hub) | — | A$450k–900k+ | Rejected — high-risk, breaches Principle 1; permanent maintenance and API-treadmill liability |
| **BUY — Path 1** (Datapel MYOB-native WMS + separate Shopify automation + shipping) | 4 | **~A$55k–95k** | Lowest disruption; MYOB stays the brain; fastest to warehouse value |
| **BUY — Path 1 (Ostendo)** (MYOB-AccountRight-native operations/ERP add-on + Shopify automation + shipping) | 4 | **~A$50k–95k** | MYOB stays the brain; *deeper* manufacturing/job-costing than Datapel; live AccountRight link |
| **BUY — Path 4 (MYOB Acumatica)** (replace AccountRight with MYOB's own cloud ERP; inventory/WMS/mfg built in) | 4 | **~A$140k–280k** | Stay in MYOB family but upgrade the platform; no third-party accounting integration; largest spend |
| **BUY — Path 2** (Cin7 or Unleashed hub + MYOB middleware + shipping) | 4 | **~A$95k–175k** | Single source of truth across all channels; larger change + MYOB-middleware dependency |
| **BUY/ADOPT — Path 2 (Odoo hub + MYOB connector/middleware + shipping)** | 4 | **~A$75k–155k** | Open-source ERP hub; strong BOM/WMS; *but* non-native MYOB integration + (if Community) self-maintenance |
| **ADOPT — Path 3 (Odoo as near-full ERP, eventually replacing MYOB)** | 4+ | **~A$95k–200k+** | Removes the MYOB-integration problem by removing MYOB; largest change, ERP migration risk, out of current scope |
| **RECOMMENDED (blended, phased)** | 4 | **~A$70k–120k** | Decide source of truth first (G-1); pilot one channel; phase rollout |

### Top Recommended Vendors (for the deeper evaluation, `/arckit:evaluate` + `/arckit:score`)

1. **Datapel Cloud.WMS** — *Path 1 lead*: MYOB-native two-way sync to AccountRight; bins, directed picking, barcode scanning, BOM/work-orders; AU/NZ vendor; lowest-disruption route to warehouse discipline.
2. **Unleashed** — *Path 2 lead*: strongest manufacturing/BOM fit of the hubs, generally good reliability/support reputation, supported Shopify connector; needs MYOB middleware and warehouse-depth/Magento validation.
3. **Cin7 Core** — *Path 2 alternative*: broadest connector library incl. native Magento + Shopify, light manufacturing/MRP; **reference-check support and sync reliability specifically** before committing; needs MYOB middleware.
4. **Ostendo** — *Path 1 rival to Datapel (added v1.2)*: **MYOB-AccountRight-native** (live link), with *deeper* manufacturing — BOM-with-routings, job costing, three-way matching — plus Freeway barcode WMS and POS. Strongest new MYOB-native contender; **should join Datapel in the evaluate/score shortlist**.
5. **MYOB Acumatica** — *Path 4: upgrade the MYOB platform (added v1.2)*: MYOB's own cloud ERP with inventory, WMS and manufacturing built in — removes the accounting-integration problem entirely by replacing AccountRight. Credible if Cycle Motion will migrate accounting platforms; materially higher cost.
6. **Odoo** — *Path 2/Path 3 contender (added v1.1)*: strongest BOM/MRP and barcode-WMS depth of any *open-source* option, native multi-store Shopify + Magento, no per-seat lock-in (Community); **but** non-native MYOB AccountRight integration and open-source self-maintenance push it below the MYOB-native options for this brief. **ERPNext** is its open-source peer (strong BOM, no native MYOB) — same caveats.

### Requirements Coverage

Mapped against the 7 stakeholder goals (used in lieu of `ARC-001-REQ`):

- ✅ **~86%** (6 of 7 goals) have an identified product-backed solution path under either Path.
- ⚠️ **G-2 (eliminate Shopify re-keying)** is only fully solved by Path 1 *plus a separate Shopify-automation workstream*, or natively by Path 2 — this is the key Path differentiator.
- 🔍 **G-6 (quantify the operation)** is a prerequisite gap: SKU count, per-channel order volume, MYOB edition, BOM complexity, and the confirmed 5-vs-7 storefront count must be captured before vendors quote.
- ⚠️ **G-7 (preserve BOM)** is met strongly by Odoo and ERPNext (multi-level MRP) — but for both, **G-1's source-of-truth and the MYOB accounting integration become the binding constraint**, not BOM capability.
- ✅ **G-7 is met MYOB-natively and deeply by Ostendo** (BOM-with-routings, job costing) and **wholly inside the platform by MYOB Acumatica** (manufacturing edition) — the v1.2 scan improves coverage for the manufacturing/BOM goal without the middleware penalty.

---

## Research Categories

> Categories are derived from the company brief and architecture principles, not a fixed list. Cycle Motion is a private Australian company; UK-Government categories (One Login, Pay, Notify, G-Cloud) do not apply.

1. **Inventory Source of Truth & Multichannel Sync** — the gating architectural decision (Path 1 vs Path 2). Maps to Principles 2, 6, 8, 10; goals G-1, G-2, G-3.
2. **Warehouse Management (WMS)** — bins/locations, directed picking, barcode scanning, cycle counts, lot/serial. Maps to Principle 6; goal G-4.
3. **Manufacturing / Bill of Materials (BOM)** — assemblies and work orders for the custom wheel-build line. Maps to Principle 6; goal G-7.
4. **Carrier / Shipping Integration** — multi-carrier label printing and tracking for Australia Post, Aramex, Sendle, etc. Maps to Principles 1, 9; supports G-4.

---

## Category 1: Inventory Source of Truth & Multichannel Sync (the gating decision)

**Goals addressed**: G-1 (decide source of truth), G-2 (eliminate re-keying), G-3 (idempotent sync / no oversell). **Principles**: 2 (Scalability), 6 (Single Source of Truth), 8 (Data Quality), 9 (Loose Coupling), 10 (Idempotent Sync).

**Why this category**: Every downstream choice hangs off one question — *where should the single source of inventory truth live?* (Principle 6; brief B4). Two architectural answers are on the table:

- **Path 1** — keep **MYOB AccountRight** as inventory master and add an **MYOB-native WMS/operations layer** (**Datapel** *or* **Ostendo** — both natively integrate with AccountRight). Magento↔MYOB continues largely as today; Shopify automation is a separate workstream. *(v1.2: Ostendo joins Datapel as a MYOB-native Path 1 option — deeper on manufacturing/job-costing.)*
- **Path 2** — introduce an **inventory/order hub** (Cin7, Unleashed, **or Odoo**) as the master; all channels (Magento + all Shopify stores) connect to the hub; MYOB is demoted to accounting only. **Odoo's framing**: the user asked for "Odoo **with** MYOB integration", i.e. Odoo as the hub feeding MYOB for accounting — this is the Path 2 reading and is led on below.
- **Path 3 (Odoo-specific, more radical)** — adopt **Odoo as a near-full ERP** (inventory + manufacturing + sales + purchase + barcode/WMS *and its own accounting*) that could **eventually replace MYOB**. This *removes* the MYOB-integration problem by removing MYOB, but is the largest change with full ERP-migration risk and is **out of the current project's scope** (the brief's goal is a single source of inventory truth with minimal disruption, not an accounting-platform replacement). Flagged for completeness; not recommended as the near-term move.
- **Path 4 (added v1.2) — upgrade *within the MYOB family*: adopt MYOB Acumatica** (MYOB's own cloud ERP, formerly MYOB Advanced) with inventory, WMS and manufacturing built in, retiring AccountRight. Like Path 3 it *removes* the third-party accounting-integration problem (the ERP **is** the accounting system) — but unlike Odoo/ERPNext it keeps Cycle Motion in the MYOB vendor relationship and is a commercially-supported, AU-hosted product. It is the most expensive route (A$104–179/user/mo + A$50k–150k implementation) and a genuine platform migration, so it is a strategic option for if/when AccountRight becomes the ceiling — not the minimal-disruption move the brief asks for first.

### The decisive integration fact: MYOB-native vs middleware-dependent

| Candidate core | Native MYOB AccountRight connector | Native accounting it targets | MYOB path for Cycle Motion |
|----------------|-----------------------------------|------------------------------|----------------------------|
| **Datapel** (Path 1) | ✅ Yes — purpose-built; two-way; AccountRight v8.5–19.7 via the Datapel/Connector adaptor [RSCH-C1][RSCH-C9] | MYOB AccountRight (its whole reason for existing) | Native — no middleware |
| **Cin7 Core/Omni** (Path 2) | ❌ No native AccountRight connector found [RSCH-C5] | Xero, QuickBooks Online | Third-party middleware (SAAS Integrator / GrowthPath / Zoho Flow) [RSCH-C5][RSCH-C10] |
| **Unleashed** (Path 2) | ❌ No native AccountRight connector found [RSCH-C6] | Xero, QuickBooks Online | Third-party middleware (Zoho Flow / connector platform) [RSCH-C6] |
| **Ostendo** (Path 1) — *added v1.2* | ✅ **Native** to MYOB AccountRight (incl. AccountRight Live); live link posts every few minutes (near-real-time financials) [RSCH-C24] | MYOB AccountRight (purpose-built operations layer for it) | Native — no middleware. **Co-leads with Datapel on the MYOB-native axis** |
| **MYOB Acumatica** (Path 4) — *added v1.2* | ✅ N/A — **it IS the accounting system** (replaces AccountRight); inventory/WMS/manufacturing built in [RSCH-C23] | MYOB Acumatica's own GL | No integration needed — single platform. Removes the connector problem by removing AccountRight |
| **ERPNext** (Path 2/3) — *added v1.2* | ❌ No native MYOB connector; middleware/custom (Integrator.io etc. cover AccountRight generically) [RSCH-C25] | ERPNext's own accounting | Middleware/custom — **same caveat as Odoo**, plus open-source self-maintenance |
| **Retail Express by Maropost** (Path 2, retail-leaning) — *added v1.2* | ⚠️ Listed on MYOB App Marketplace; integration oriented to **MYOB Business** (not AccountRight-native); Sydney-hosted (Azure) [RSCH-C26] | — (POS/inventory platform) | Connector via MYOB marketplace; retail/POS focus, weak manufacturing fit |
| **Odoo** (Path 2; or Path 3 = no MYOB) | ❌ No native, maintained AccountRight connector. Only: a low-maturity paid app (Warlock, MYOB edition unconfirmed, import-skewed) [RSCH-C17]; an OCA module for *AccountEdge*, not AccountRight [RSCH-C18]; or middleware/custom | **Odoo's own accounting** (Community or Enterprise) — so MYOB is redundant in Path 3 | Connector/middleware/custom — **arguably the weakest MYOB story of all candidates** [RSCH-C17][RSCH-C18] |

This is the single most important finding for the Path decision. Path 2 keeps MYOB only for accounting, but it still has to **write to MYOB reliably and idempotently** — and that link is not vendor-native for either hub. It introduces a third-party connector into the path that Principle 10 says must be idempotent and recoverable, and Principle 9 says should be loosely coupled. That risk is manageable (these middleware products exist and are used in Australia) but it must be priced, owned, and pilot-tested. **For Odoo the same risk is more acute**: because Odoo ships its own accounting, the MYOB link is not its product focus, and no maintained two-way AccountRight connector was found — so "Odoo + MYOB" places possibly the *least proven* connector of any option into the idempotent-sync critical path. The cleaner Odoo answer is Path 3 (let Odoo's own accounting be the books), which is exactly what the user's "with MYOB integration" framing rules out for now. **The v1.2 landscape scan reinforces this pattern from both ends**: the only newly-found options that *avoid* the middleware-in-the-critical-path problem are the ones that stay MYOB-native — **Ostendo** (native AccountRight link) and **MYOB Acumatica** (the ERP *is* MYOB) — while every non-MYOB-native newcomer (ERPNext, and the Xero/QuickBooks-native crowd) hits the same wall as Cin7/Unleashed/Odoo. The decision axis is therefore unchanged and sharpened: **stay MYOB-native (Datapel / Ostendo / — at greater cost — MYOB Acumatica) for lowest integration risk, or accept middleware (any hub) for single-platform multichannel truth.**

### Option 1A: Build Custom (rejected)

**Description**: A bespoke inventory/sync engine and/or WMS. **Verdict: do not build.** A real WMS/hub is deceptively deep (bins, pick paths, wave/batch picking, barcode scanning, cycle counts, lot/serial, returns, multi-warehouse, carrier integration, BOM) and a custom build means owning all of it plus a permanent treadmill chasing MYOB/Shopify/Magento/carrier API changes — the opposite of the brief's low-risk goal and a direct breach of Principle 1. Indicative 3-year TCO A$450k–900k+ (≥ 300–600 person-days at ~A$1,200/day plus indefinite maintenance) with high schedule and key-person risk. **No further build analysis is presented.**

### Option 1B: Path 1 — Datapel Cloud.WMS (MYOB-native, lowest disruption)

**Description**: A cloud WMS purpose-built as an MYOB add-on. MYOB AccountRight remains the inventory and accounting master; Datapel layers warehouse discipline (bins, guided pick/pack/putaway, barcode scanning) and its own BOM/work-order manufacturing on top, syncing stock movements, orders, bills and invoices back to MYOB in real time with full audit trails [RSCH-C1][RSCH-C2].

**Vendor**: Datapel Systems Pty Ltd (Australia/NZ). Trusted by **200+ MYOB customers across AU/NZ** [RSCH-C2].

**Pricing model**: Subscription, from **A$120/month** entry; "only pay for the onboarding support you need… no hidden costs… no lock-in" [RSCH-C2][RSCH-C8]. Real-world tier for a multi-bin, BOM, multichannel SME will be materially above the A$120 floor — confirm by quote against G-6 data.

**Indicative 3-year cost (Path 1 core WMS only; Shopify automation + shipping costed separately below)**:

| Cost item | Year 1 | Year 2 | Year 3 | Notes |
|-----------|--------|--------|--------|-------|
| Subscription (est. mid-tier) | A$6,000 | A$6,300 | A$6,600 | ~A$500/mo est.; confirm by quote |
| Onboarding / implementation | A$8,000 | A$0 | A$0 | Pay-for-what-you-need model [RSCH-C8] |
| Warehouse hardware (scanners, labels) | A$4,000 | A$500 | A$500 | Barcode-guided picking enablement |
| Training | A$2,000 | A$0 | A$0 | Ops team (5 staff) |
| **Total** | **A$20,000** | **A$6,800** | **A$7,100** | |
| **3-Year TCO (Datapel core)** | | | **~A$34,000** | Excludes Shopify automation + shipping |

**Pros**:

- ✅ MYOB-native two-way sync to AccountRight — no middleware in the MYOB path (Principles 9, 10).
- ✅ Preserves the working Magento↔MYOB integration; preserves MYOB as the trusted system of record (Principle 18, safe migration).
- ✅ Genuine WMS depth: bins/locations, guided pick/pack/putaway, barcode scanning [RSCH-C1].
- ✅ Built-in BOM / work-order manufacturing — assemblies decrement components and add finished stock (G-7) [RSCH-C7].
- ✅ AU/NZ vendor, AU-relevant support, low entry price, no lock-in claim.

**Cons**:

- ❌ Does **not** by itself automate the five manual Shopify stores — a separate Shopify-to-MYOB automation workstream is required (G-2 only partially solved).
- ❌ MYOB AccountRight remains the multichannel inventory ceiling (Principle 2 scaling concern long-term).
- ❌ Cycle-count and lot/serial depth not clearly evidenced on the public site — confirm in demo/pilot.
- ❌ Smaller review base (~53 Capterra reviews); some reports of slow query turnaround and multi-product onboarding complexity [RSCH-C8].

**Companion workstream for Path 1 — Shopify→MYOB automation**: To close G-2 under Path 1, add a supported Shopify-to-MYOB connector (e.g. **Amaka** "Shopify by Amaka", listed on the MYOB App Marketplace [RSCH-C6]) per active store, or route Shopify orders through Datapel where supported. Budget ~A$15–40/store/month plus setup; confirm whether Datapel can ingest Shopify orders directly to avoid a second integration vendor.

### Option 1C: Path 2 — Cin7 (Core / Omni) inventory & order hub

**Description**: A multichannel inventory and order-management platform that becomes the system of record. **Cin7 Core** is the turnkey SME product (purchasing, sales, WMS, light manufacturing) with native connectors to Shopify, Amazon, eBay, **Magento** and WooCommerce; **Cin7 Omni** is the customisable, multi-entity enterprise tier (700+ integrations, multi-brand) better suited to many storefronts/entities [RSCH-C3][RSCH-C4]. MYOB is demoted to accounting and fed via middleware.

**Vendor**: Cin7 — founded 2011 in **Auckland, New Zealand** by Danny Ing; acquired by Rubicon Technology Partners (2019, ~US$133M); **~8,000 customers across 75 countries**; platform **hosted on Microsoft Azure** [RSCH-C11]. Confirm Australian data residency / Azure region and APP posture directly with the vendor before commitment.

**Pricing model (list, USD, +taxes)** [RSCH-C3][RSCH-C4]:

- **Cin7 Core — Standard**: US$349/mo · 5 users · 6,000 sales orders/yr · 2 integrations · barcode scanning, standard WMS, unlimited locations; assembly/kits (MRP add-on); B2B portal add-on.
- **Cin7 Core — Pro** (most popular): US$599/mo · 10 users · 24,000 orders/yr · 4 integrations · includes MRP.
- **Cin7 Core — Advanced**: US$999/mo · 15 users · 120,000 orders/yr · 6 integrations · advanced WMS + RMA.
- **Cin7 Omni**: custom pricing · 8 users base · uncapped orders · 5 integrations · multi-entity.

> For ~5–7 storefronts, **Cin7 Core Pro** (4 integrations) is the likely floor; more than 4 connectors pushes toward Advanced or Omni. At ~US$599/mo ≈ **A$0.9k–1.0k/mo** before middleware, shipping, and add-ons.

**Indicative 3-year cost (Cin7 Core Pro path)**:

| Cost item | Year 1 | Year 2 | Year 3 | Notes |
|-----------|--------|--------|--------|-------|
| Subscription (Core Pro, ~A$11.5k/yr) | A$11,500 | A$12,650 | A$13,900 | USD list +10%/yr; FX risk |
| MYOB middleware (third-party) | A$3,600 | A$3,600 | A$3,600 | SAAS Integrator/GrowthPath/Zoho Flow [RSCH-C5][RSCH-C10] |
| Implementation/onboarding | A$15,000 | A$0 | A$0 | Multichannel migration; partner-led |
| Warehouse hardware | A$4,000 | A$500 | A$500 | |
| Training | A$3,000 | A$0 | A$0 | |
| **Total** | **A$37,100** | **A$16,750** | **A$18,000** | |
| **3-Year TCO (Cin7 Core path)** | | | **~A$72,000** | Excludes shipping layer |

**Pros**:

- ✅ Single source of truth across **all** channels in one architecture — natively solves G-2 (Shopify re-keying) and multichannel truth (G-3).
- ✅ Broadest connector library, incl. **native Magento and Shopify** (Core) and multi-entity (Omni) for many storefronts [RSCH-C3][RSCH-C4].
- ✅ Light manufacturing/MRP for BOM (G-7) — assembly/kits on Standard, MRP on Pro [RSCH-C3].
- ✅ Built to scale channels and volume (Principle 2).

**Cons**:

- ❌ **No native MYOB AccountRight connector** — middleware required, adding a vendor and a coupling point in the idempotent-sync path (Principles 9, 10) [RSCH-C5].
- ❌ **Reliability/support reputation risk is real and current**: 2025–2026 reviews report Shopify sync drops, stock disconnecting while "connected", blank/partial orders, variant-mapping breakage, frequent price increases, and slow/email-only support [RSCH-C12][RSCH-C13]. Directly threatens G-3 and Principle 10 — reference-check and pilot are mandatory (Risk R-2).
- ❌ USD list pricing → FX exposure; high tiers get expensive for a small business.
- ❌ Larger migration; reworks the MYOB relationship (Principle 18 risk).

### Option 1D: Path 2 — Unleashed inventory & order hub

**Description**: A multichannel inventory platform with a strong manufacturing pedigree, popular with Australian/NZ manufacturers. Supported, vendor-maintained connectors for Shopify, WooCommerce and Amazon; digital BOM, assemblies/disassembly, MRP and Kanban production planning [RSCH-C3a][RSCH-C14]. MYOB fed via middleware (native targets are Xero/QuickBooks) [RSCH-C6].

**Vendor**: Unleashed Software (NZ-origin; part of the Access Group). 14-day free trial.

**Pricing model (list, AUD)** [RSCH-C3a]:

- **Core**: A$449/mo · 3 users · 100 sales orders/mo (upgradable to 500/1,500/3,000/unlimited) · 250k API calls/mo · 3 integrations · +A$69/user.
- **Pro**: A$819/mo · 5 users · 100 orders/mo (same upgrades) · 500k API calls/mo · 5 integrations · +A$79/user.
- **Optional add-ons**: Advanced Inventory Manager/MRP A$129/mo · Warehouse Management & Multi-Bin **A$149/mo** · Production & Manufacturing A$69/mo · B2B eCommerce A$119/mo · Warehouse Devices A$49 each [RSCH-C3a].

> Important: Unleashed's **WMS multi-bin depth and production module are paid add-ons**, and the base order allowance is only 100/month — order-volume and add-on selection (driven by G-6 data) materially change the price. A realistic Cycle Motion configuration is **Pro + Warehouse/Multi-Bin + Production + an order-volume uplift**, i.e. well above the A$819 headline.

**Indicative 3-year cost (Unleashed Pro + WMS + Production)**:

| Cost item | Year 1 | Year 2 | Year 3 | Notes |
|-----------|--------|--------|--------|-------|
| Subscription (Pro + Multi-Bin + Production + order uplift, ~A$1.4k/mo) | A$16,800 | A$18,480 | A$20,300 | Add-ons + order tier; +10%/yr est. |
| MYOB middleware (third-party) | A$3,600 | A$3,600 | A$3,600 | Zoho Flow / connector platform [RSCH-C6] |
| Implementation/onboarding | A$14,000 | A$0 | A$0 | Multichannel migration |
| Warehouse hardware | A$4,000 | A$500 | A$500 | |
| Training | A$3,000 | A$0 | A$0 | |
| **Total** | **A$41,400** | **A$22,580** | **A$24,400** | |
| **3-Year TCO (Unleashed path)** | | | **~A$88,000** | Excludes shipping layer |

**Pros**:

- ✅ Strongest **manufacturing/BOM** fit of the hubs (assemblies, MRP, Kanban) — best match to G-7 and the custom wheel-build line [RSCH-C14].
- ✅ Generally **good reliability and support reputation** — praised for inventory accuracy and responsive follow-up; one manufacturer cited near-flawless results at 500 orders/1,500 items per week [RSCH-C15].
- ✅ Supported, vendor-maintained Shopify connector; single source of truth across channels (G-2, G-3) [RSCH-C14].
- ✅ AUD list pricing (no FX), transparent published tiers.

**Cons**:

- ❌ **No native MYOB AccountRight connector** — middleware required (Principles 9, 10) [RSCH-C6].
- ❌ **WMS multi-bin and production are paid add-ons** and base order allowance is low — real cost climbs quickly with order volume and warehouse depth [RSCH-C3a].
- ❌ Reviews flag a **rigid UI / steep learning curve** and a **poorly-communicated paid "premium support" tier** (A$79/mo) that some customers paid for without receiving, with refund disputes [RSCH-C15].
- ❌ Magento integration fit needs validation (native connectors emphasised are Shopify/WooCommerce/Amazon) [RSCH-C14].

### Option 1E: Path 2 — Odoo (open-source ERP as hub; "Odoo with MYOB integration") — *added v1.1*

**Description**: Odoo is a full open-source **ERP** — Inventory, Manufacturing/MRP (multi-level BOM), Sales, Purchase, Barcode/WMS, eCommerce connectors, **and its own Accounting**. It is therefore **not a like-for-like Datapel/Cin7/Unleashed swap**: it spans the whole back office. In the user's **"Odoo with MYOB integration"** framing (Path 2), Odoo becomes the inventory/order/manufacturing **hub** and MYOB AccountRight is *kept for accounting only*, fed from Odoo. (The more radical **Path 3** — Odoo's own accounting replaces MYOB — is noted but out of current scope.)

**Vendor / project**: Odoo S.A. (Belgium). **Community edition** is free and open-source (LGPL-3.0); **Enterprise** is a per-user + per-app subscription; hosting via **Odoo Online**, **Odoo.sh** (PaaS), or **on-premise/self-hosted**. Large global partner ecosystem incl. Australian implementation partners.

**The MYOB integration reality (the crux)** — investigated honestly:

- **No native, maintained, two-way Odoo↔MYOB AccountRight connector was found.** The closest options are:
  - **Warlock Technologies "MYOB Odoo Connector"** on apps.odoo.com — ~**US$315 one-time**, Odoo 15–17, syncs customers/suppliers/products/CoA/taxes/sales+purchase orders; **MYOB edition (AccountRight vs Business) is not specified**, the feature set is **import-skewed (MYOB→Odoo)** and **two-way sync is unconfirmed** [RSCH-C17]. Low maturity for a mission-critical accounting link.
  - **OCA `connector-accountedge`** — open-source, but targets **MYOB *AccountEdge*** (the older Mac/desktop product), **not AccountRight** [RSCH-C18].
  - **Middleware / custom** — SAAS Integrator-style middleware or a bespoke integration in the sync path.
- **Architectural tension (Principles 9 & 10)**: any of these puts a **non-native accounting integration into the idempotent-sync critical path** — the same problem flagged for Cin7/Unleashed, but **arguably worse**, because (a) no proven two-way AccountRight connector exists, and (b) MYOB is peripheral to Odoo's design (Odoo *expects* to own accounting). The cleanest fix is Path 3 (drop MYOB), which the "with MYOB" framing excludes.

**Deployment / licensing for a small AU business**:

- **Odoo Community** — free, self-hosted; **you own hosting, upgrades, patching and maintenance** — a direct tension with Principle 1 (buy-over-build) and the brief's explicit "don't take on a maintenance treadmill" stance.
- **Odoo Enterprise** — ~**A$45–65/user/month** (annual billing); managed updates/support; Studio, external API, multi-company [RSCH-C19].
- **Reality check**: Odoo's headline licence cost understates TCO — **value (and cost) comes from the implementation partner**. Typical AU SME Odoo implementations run **A$15k–60k** (partner fees A$8k–50k+; partners charge ~A$120–350/hr), plus **A$5k–10k/yr ongoing** [RSCH-C20].

**BOM/MRP and WMS depth (genuinely strong)**: multi-level BOMs, finite-capacity MRP, barcode-driven multi-warehouse operations, and a Barcode app integrated with Manufacturing [RSCH-C21]. **Native multi-store eCommerce**: maintained **Shopify** and **Magento 2** connectors map multiple stores to Odoo warehouses with per-location stock sync (BOM-aware availability) [RSCH-C22].

**Indicative 3-year cost (Odoo Enterprise hub + MYOB connector/middleware + partner)**:

| Cost item | Year 1 | Year 2 | Year 3 | Notes |
|-----------|--------|--------|--------|-------|
| Odoo Enterprise subscription (~6 users, Inventory/Mfg/Sales/Purchase apps) | A$5,500 | A$5,800 | A$6,100 | ~A$45–65/user/mo; Community = A$0 licence but +hosting/maintenance [RSCH-C19] |
| MYOB connector / middleware | A$2,500 | A$2,000 | A$2,000 | Low-maturity app + likely custom hardening [RSCH-C17][RSCH-C18] |
| AU implementation partner | A$28,000 | A$3,000 | A$3,000 | Discovery, config, data migration, go-live; partner-dependent [RSCH-C20] |
| Warehouse hardware | A$4,000 | A$500 | A$500 | |
| Training | A$3,500 | A$0 | A$0 | Broader ERP surface to learn |
| **Total** | **A$43,500** | **A$11,300** | **A$11,600** | |
| **3-Year TCO (Odoo Enterprise hub)** | | | **~A$66,000** | Excludes shipping; **partner-dependent range A$60k–110k** |

> If Odoo **Community** is chosen, the ~A$17k Enterprise licence over 3 years disappears but is **replaced by self-hosting + maintenance** effort (you own upgrades, security patching, connector upkeep) — often a net wash or worse for a 5-person team, and a Principle-1 concern. Figures are a **range pending G-6 data** and dominated by partner scope.

**Pros**:

- ✅ Strongest **BOM/MRP and barcode-WMS depth** of any candidate (multi-level BOM, finite-capacity MRP) — excellent G-7 fit [RSCH-C21].
- ✅ **Native multi-store Shopify + Magento** connectors — solves G-2/G-3 natively at the hub [RSCH-C22].
- ✅ **No per-seat lock-in** with Community (LGPL-3.0); open data; avoids the proprietary-SaaS lock-in the brief dislikes.
- ✅ One platform spans inventory, manufacturing, sales and purchasing (scales per Principle 2).

**Cons**:

- ❌ **Weakest MYOB story of all candidates** — no maintained two-way AccountRight connector; "Odoo + MYOB" puts the least-proven integration into the idempotent-sync critical path (Principles 9, 10) [RSCH-C17][RSCH-C18].
- ❌ **Open-source self-maintenance** (Community) or per-user subscription (Enterprise) — Community tensions Principle 1 and the brief's no-treadmill stance.
- ❌ **ERP-scale change**: broader surface, larger implementation, more training and migration risk than a focused WMS/hub — heavier than the brief's "minimal disruption" intent.
- ❌ TCO **dominated by implementation-partner scope**, not licence — harder to bound until G-6 + partner scoping.

### Build vs Buy Recommendation for Category 1

**Recommended approach**: **BUY.** Then make the source-of-truth decision (G-1) as a hard gate before product selection, per Principle 6 and the brief's de-risking sequence. On current evidence:

- If the priority is **warehouse discipline with least disruption and lowest risk**, **Path 1 (Datapel *or* Ostendo)** is the right move — MYOB-native, no middleware, preserves Magento↔MYOB, fastest to value — with a **parallel Shopify-automation workstream** to close G-2. *(v1.2: **Ostendo** is the new MYOB-native rival — deeper on manufacturing/job-costing than Datapel; both should be evaluated head-to-head.)*
- If the goal is to fix **the warehouse, the five manual Shopify stores, and multichannel truth in one architecture**, **Path 2 (a hub)** is the stronger long-term answer, accepting a larger migration and an **MYOB-middleware dependency**. Of the hubs, **Unleashed leads on manufacturing fit and reliability reputation**; **Cin7 Core leads on connector breadth (native Magento) but carries the reliability/support reputation risk the brief flags**.
- **Odoo (Path 2) is the most capable but the least aligned to *this* brief.** Its BOM/MRP and WMS depth and native multi-store connectors are best-in-class, and Community avoids lock-in — but "Odoo **with** MYOB" reintroduces the non-native-accounting risk in its sharpest form (no maintained two-way AccountRight connector) and adds open-source self-maintenance. **Recommend Odoo only if Cycle Motion deliberately elects an ERP-scale transformation** — and in that case the honest endgame is **Path 3** (Odoo's own accounting replaces MYOB), which is out of current scope. For the stated goal (single inventory truth, minimal disruption), Odoo ranks behind Datapel and Unleashed. **ERPNext** (v1.2) sits in the same place as Odoo among open-source ERPs — strong BOM, no native MYOB, self-maintenance — and is not recommended ahead of the MYOB-native options for this brief.
- **MYOB Acumatica (Path 4, v1.2) is the strategic long-game, not the first move.** Replacing AccountRight with MYOB's own cloud ERP removes the integration problem entirely and keeps Cycle Motion in the MYOB family with AU hosting and commercial support — but it is a full accounting-platform migration at A$140k–280k 3-yr TCO. Recommend it only when/if AccountRight becomes the genuine ceiling (the brief's Principle-2 scaling concern), not as the minimal-disruption uplift requested now.

**Key decision factors**:

- ✅ **MYOB integration depth** — decisively favours the MYOB-native options (**Datapel, Ostendo**, and — by being MYOB itself — **MYOB Acumatica**) over any middleware route; **Odoo/ERPNext are weakest here** (no maintained native AccountRight connector).
- ✅ **Appetite for change** (G-1 must record this) — incremental → Path 1; transformational → Path 2 (hub); ERP-transformational → Odoo, ideally Path 3.
- ✅ **Reliability of idempotent sync** (Principle 10, Risk R-2) — favours native (Datapel) and the better-reviewed hub (Unleashed) over Cin7/Odoo unless references and pilot clear it.
- ✅ **Manufacturing/BOM** (G-7) — **Odoo/ERPNext strongest in absolute terms** (multi-level MRP), but among *MYOB-native* options **Ostendo is notably deep** (BOM-with-routings, job costing, three-way matching) and **MYOB Acumatica** has a dedicated Manufacturing edition; Datapel (native work orders) and Unleashed (strong MRP) all fit; Cin7 light-MRP adequate. For Odoo/ERPNext, BOM is *not* the constraint — the MYOB accounting link is.
- ✅ **Maintenance burden / lock-in** (Principle 1) — SaaS options (Datapel/Cin7/Unleashed) externalise maintenance; **Odoo Community shifts maintenance in-house** (treadmill risk), Odoo Enterprise re-introduces a per-user subscription.

---

## Category 1b: Broadened MYOB-Integrating Landscape Scan (added v1.2)

> User request: *"find more retail inventory management systems both open source and proprietary that integrate with MYOB."* This is an **additive landscape scan**. Strong-fit candidates are profiled; weak-fit ones are culled to a one-line reason rather than over-detailed. The recurring crux is unchanged: **any non-MYOB-native option re-introduces middleware in the idempotent-sync critical path (Principles 9 & 10), and open-source adds self-maintenance vs buy-over-build (Principle 1).**

### Strong-fit additions (profiled)

#### Ostendo (Development-X) — MYOB-AccountRight-NATIVE; Path 1 rival to Datapel

- **MYOB integration**: ✅ **Native** to MYOB AccountRight / AccountRight Live — a purpose-built operations layer; the link posts automatically every few minutes, giving near-real-time integrated financials (no third-party middleware) [RSCH-C24].
- **Fit**: manufacturing + distribution + service (and retail/POS). Strong wholesale **and** manufacturing fit — well-matched to Cycle Motion's custom wheel-build line.
- **BOM/MRP**: ✅ **Deep** — bills of material *with routings*, assembly orders, work orders, job costing, job scheduling, labour timesheets, three-way purchase matching [RSCH-C24]. Arguably deeper than Datapel on manufacturing.
- **WMS**: ✅ Freeway mobile app — barcode picking, receiving, warehouse, multi-location; full POS (touchscreen, multi-station, barcode, EFTPOS) [RSCH-C27].
- **Shopify multi-store / Magento**: ⚠️ E-commerce/web-store and POS integration available (live stock sync, multi-warehouse) but **Shopify multi-store and Magento depth must be confirmed** — typically via AU integrators (e.g. iBis/MyIntegrator) rather than a first-party multi-store connector [RSCH-C27].
- **AU presence**: ✅ AU/NZ vendor (Development-X), listed on MYOB App Marketplace; established AU integrator network.
- **Indicative pricing**: transparent, all-modules pricing (no per-module upsell); Freeway mobility ~A$50/user/yr-class add-on. Confirm a current quote against G-6. Indicative 3-yr TCO comparable to or slightly above Datapel (~A$50k–95k all-in, partner-dependent).
- **Path fit**: **Path 1** (MYOB-native). **Verdict: a genuine new MYOB-native contender — should join Datapel in the evaluate/score shortlist.** Confirm Shopify-multi-store/Magento connector depth in the demo/pilot, since that is the one open question vs the brief.

#### MYOB Acumatica (formerly MYOB Advanced) — MYOB's OWN cloud ERP; a distinct Path 4

- **MYOB integration**: ✅ N/A in the connector sense — **it replaces AccountRight**. Inventory, WMS and manufacturing are built into MYOB's own enterprise cloud ERP, so there is *no* third-party accounting integration to maintain [RSCH-C23].
- **Fit**: mid-market ERP — financials, distribution/inventory, and a dedicated **Manufacturing edition** (production, MRP, cost control).
- **BOM/MRP**: ✅ Strong (Manufacturing edition). **WMS**: ✅ Built-in warehouse capability. **Shopify/Magento**: via Acumatica's commerce connectors / AU partners (confirm multi-store).
- **AU presence**: ✅ MYOB's own product, AU-hosted, AU partner channel and support.
- **Indicative pricing**: A$104/user/mo (Standard), A$139 (Plus), A$179 (Enterprise); implementation **A$50k–150k**; ongoing ~A$2k–5k/mo [RSCH-C23]. Indicative 3-yr TCO **~A$140k–280k** — the most expensive option.
- **Path fit**: **Path 4 — upgrade the MYOB platform.** A serious "stay in the MYOB family but outgrow AccountRight" answer; a genuine accounting-platform migration. **Recommend as the strategic option when AccountRight becomes the ceiling — not as the minimal-disruption first move.**

#### ERPNext (Frappe) — open-source ERP; Odoo's peer

- **MYOB integration**: ❌ **No native MYOB connector**; middleware/custom only (e.g. Integrator.io's generic AccountRight connector) — **same caveat as Odoo** [RSCH-C25].
- **BOM/MRP**: ✅ Strong — multi-level BOMs, work orders, production planning, capacity planning, subcontracting. **WMS**: multi-warehouse, barcode. **Shopify/Magento**: connectors available.
- **AU presence / licensing**: open-source (GPL/MIT-family via Frappe), self-hosted or Frappe Cloud; **self-maintenance tensions Principle 1** and the brief's no-treadmill stance.
- **Path fit**: **Path 2/Path 3** (like Odoo). **Verdict: capable open-source alternative to Odoo, but the same non-native-MYOB + self-maintenance penalties apply — not recommended ahead of the MYOB-native options for this brief.** Recorded so the open-source field is complete.

#### Retail Express by Maropost — AU retail/POS specialist (partial fit)

- **MYOB integration**: ⚠️ Listed on the MYOB App Marketplace; integration is oriented to **MYOB Business** (not AccountRight-native); data **hosted in Sydney on Azure** [RSCH-C26].
- **Fit**: **retail/POS** (purchasing, dynamic replenishment, transfers, stocktake, fulfilment) — strong for bricks-and-mortar retail, **weak on manufacturing/BOM** (no real fit for the wheel-build line).
- **Shopify/Magento**: ✅ Integrates with Shopify and Adobe Commerce/Magento.
- **Path fit**: **Path 2 (retail-leaning).** **Verdict: relevant for the B2C/retail side and AU-hosted, but its retail-not-manufacturing bias and MYOB-Business (not AccountRight) orientation make it a partial fit — not a front-runner for a manufacturer needing BOM.** Worth a look only if Cycle Motion's priority shifts to POS/retail.

### Culled — weak fit for this brief (one-line reasons)

| Candidate | Type | MYOB-AccountRight reality | Cull reason |
|-----------|------|---------------------------|-------------|
| **Fishbowl** | Proprietary inventory/mfg | QuickBooks-native (deepest); no MYOB-native | Built around QuickBooks; MYOB only via custom integration |
| **Katana MRP** | Proprietary MRP | Xero + QuickBooks native; no MYOB-native | Modern MRP but no MYOB path without middleware |
| **inFlow Inventory** | Proprietary inventory | QuickBooks/Xero; no MYOB-native | SME inventory, no MYOB-native, weak AU manufacturing fit |
| **Linnworks** | Proprietary multichannel | Xero/QuickBooks; no MYOB-native | Multichannel order mgmt, UK-centric, no MYOB-native |
| **SkuVault** | Proprietary WMS | No MYOB-native | Warehouse/inventory only; no MYOB path |
| **Brightpearl** | Proprietary retail ops | No MYOB-native (Xero/QuickBooks) | Retail ops platform, enterprise-priced, no MYOB-native |
| **Lightspeed Retail (X-Series)** | Proprietary POS | Xero/QuickBooks; no MYOB-native | Retail POS, not a manufacturing inventory SoT |
| **Square for Retail** | Proprietary POS | No MYOB-native | Lightweight POS; no manufacturing/BOM, no MYOB-native |
| **SalesIn** | Proprietary sales-order app | ✅ Connects to MYOB (and Xero/Fishbowl) | A B2B sales-order/rep tool, *not* an inventory source-of-truth or WMS — complements, doesn't replace |
| **Spotlight** | Reporting/analytics | n/a (reads MYOB) | Reporting add-on, not an inventory/WMS system |
| **Tryton** | Open-source ERP | No MYOB integration found | Capable Python ERP but no MYOB connector; thin AU support |
| **Apache OFBiz** | Open-source ERP framework | No MYOB integration found | Developer framework, not a turnkey product; no MYOB |

**Scan conclusion**: the broadened search **did not find a non-MYOB-native option that beats the Path 1 MYOB-native route on integration risk** — but it *did* find **Ostendo**, a strong new MYOB-native Path 1 contender, and confirmed **MYOB Acumatica** as the credible "upgrade the platform" Path 4. The MYOB-native shortlist therefore grows from one to three (Datapel, Ostendo, + MYOB Acumatica if platform migration is in appetite). Everything else either repeats the middleware caveat (ERPNext, the hubs) or is a poor manufacturing fit (retail/POS tools).

---

## Category 2: Warehouse Management (WMS)

**Goal addressed**: G-4 (system-guided warehouse discipline, ≥98% stock accuracy). **Principle**: 6.

**Why this category**: Replacing the paper-based warehouse with bins/locations, directed picking, barcode scanning, and cycle counts is the originally-stated project need and a hard requirement under either Path.

| Capability | Datapel (Path 1) | Cin7 Core (Path 2) | Unleashed (Path 2) | Odoo (Path 2/3) |
|-----------|------------------|--------------------|--------------------|-----------------|
| Bins / multi-location | ✅ Yes [RSCH-C1] | ✅ Unlimited locations; WMS standard/advanced [RSCH-C3] | ➕ **Add-on** (Warehouse Mgmt & Multi-Bin A$149/mo) [RSCH-C3a] | ✅ Multi-warehouse, locations [RSCH-C21] |
| Directed pick / pack / putaway | ✅ Guided [RSCH-C1] | ✅ Standard→Advanced WMS [RSCH-C3] | ✅ With WMS add-on | ✅ Yes (Barcode app) [RSCH-C21] |
| Barcode scanning | ✅ Yes [RSCH-C1] | ✅ Yes [RSCH-C3] | ✅ Warehouse Devices A$49 each [RSCH-C3a] | ✅ Barcode app, incl. manufacturing [RSCH-C21] |
| Cycle counts | ⚠️ Confirm in demo | ✅ Typically supported | ✅ Typically supported | ✅ Yes |
| Lot / serial / batch | ⚠️ Confirm in demo | ✅ Yes | ✅ Yes | ✅ Yes |
| RMA / returns | ⚠️ Confirm | ✅ Advanced tier [RSCH-C3] | ✅ Yes | ✅ Yes |

**Added v1.2 (WMS depth of the new candidates)**: **Ostendo** — ✅ strong: Freeway barcode app for picking/receiving/warehouse, multi-location, plus full POS [RSCH-C27], MYOB-native. **MYOB Acumatica** — ✅ built-in warehouse capability within the ERP [RSCH-C23]. **ERPNext** — ✅ multi-warehouse + barcode (open-source). **Retail Express** — ✅ retail-grade stock control (stocktake, transfers, replenishment) but POS-oriented [RSCH-C26].

**Recommendation**: WMS depth is adequate-to-strong across all candidates; **Odoo's and Ostendo's barcode-driven multi-warehouse WMS are among the deepest** (and Ostendo delivers it MYOB-native). The differentiator is **delivery model**, not feature ticks. Path 1 (Datapel **or Ostendo**) gets WMS depth MYOB-native; Path 4 (MYOB Acumatica) gets it inside the ERP. For the hubs, note Unleashed's WMS is a **paid add-on** (price it in) while Cin7's is tiered; Odoo's/ERPNext's WMS is included but arrives as part of an ERP-scale implementation. Confirm cycle-count and lot/serial depth for Datapel, and Shopify-multi-store handling for Ostendo, in the demo/pilot.

---

## Category 3: Manufacturing / Bill of Materials (BOM)

**Goal addressed**: G-7 (preserve BOM/manufacturing — custom wheel-build line). **Principle**: 6 (BOM ownership defined).

**Why this category**: Cycle Motion runs in-house manufacturing with BOM requirements; capability must survive the change with a clearly-owned system.

| Capability | Datapel | Cin7 Core | Unleashed | Odoo |
|-----------|---------|-----------|-----------|------|
| BOM / assemblies | ✅ BOM + Work Orders; components decrement, finished stock added; traceable to PO [RSCH-C7] | ✅ Assembly/kits (Standard); MRP add-on/Pro [RSCH-C3] | ✅ Digital BOM, assembly/disassembly, MRP, Kanban [RSCH-C14] | ✅ Multi-level BOM, work orders, by-products [RSCH-C21] |
| Multi-level assemblies | ⚠️ Confirm depth | ✅ MRP supports | ✅ Strong | ✅ **Strong** (multi-level, kits, phantom BOMs) [RSCH-C21] |
| Production planning | Work-order workflow | MRP (Pro) | ✅ Kanban planner [RSCH-C14] | ✅ Finite-capacity MRP, work centres [RSCH-C21] |
| Best fit | Native to MYOB master | Adequate | Strongest of the hubs (SaaS) | **Deepest overall — but ERP-scale** |

**Added v1.2 (BOM/MRP depth of the new candidates)**: **Ostendo** — ✅ **deep and MYOB-native**: BOM *with routings*, assembly/work orders, job costing, scheduling, three-way matching [RSCH-C24] — arguably the strongest *MYOB-native* manufacturing fit, ahead of Datapel. **MYOB Acumatica** — ✅ dedicated **Manufacturing edition** (production, MRP, cost control) inside the ERP [RSCH-C23]. **ERPNext** — ✅ multi-level BOM, work orders, production/capacity planning, subcontracting (open-source, but non-native MYOB) [RSCH-C25].

**Recommendation**: All candidates preserve BOM. In absolute terms **Odoo/ERPNext are deepest**, but the standout for *this* brief is **Ostendo**, which delivers deep manufacturing **MYOB-natively** (BOM-with-routings + job costing) — strengthening the Path 1 case for a manufacturer; **MYOB Acumatica** owns BOM inside the platform (Path 4). **Datapel keeps BOM native to the MYOB master** (supports Principle 6). For Odoo/ERPNext, manufacturing depth is *not* the deciding factor — the MYOB accounting integration and ERP-scale change are. Document single-vs-multi-level assembly complexity in discovery (G-6) so the pilot acceptance test (G-7) is concrete.

---

## Category 4: Carrier / Shipping Integration

**Goal addressed**: supports G-4 (disciplined fulfilment). **Principles**: 1 (Buy not build), 9 (Loose coupling).

**Why this category**: Multi-carrier label printing and tracking (Australia Post, Aramex, Sendle, DHL, Toll, etc.) is commodity capability that should never be custom-built (Principle 1) and should sit in a replaceable layer (Principle 9).

**Recommended product — Starshipit** (ANZ shipping-automation aggregator): integrates with **Shopify, Magento/Magento 2, MYOB, Cin7, DEAR, Unleashed and Datapel** (and Odoo via its own delivery-carrier connectors / Starshipit modules), and with carriers incl. **Australia Post, Aramex, Sendle, DHL, Toll, Hunter Express** and many more [RSCH-C16]. Tiered pricing by monthly shipment volume: **Starter from A$45 (0–100), Starter Plus A$125 (101–500), Professional A$180 (501–1,000), Professional Plus A$270 (1,001–5,000), Enterprise Plus A$500 (5,001–10,000)** [RSCH-C16].

**Indicative 3-year cost (Starter Plus tier)**: ~A$125/mo → **~A$4,500–5,000 over 3 years** plus modest setup. Works under both Paths, keeping carrier integration off the critical-build path.

**Recommendation**: **BUY Starshipit** (or a comparable aggregator) as the shipping layer under whichever Path is chosen. Confirms loose coupling — it connects to the chosen core *and* to Shopify/MYOB without bespoke code.

---

## Total Cost of Ownership (TCO) Summary

### Blended TCO by Path (indicative, AUD, list, pre-negotiation)

| Component | Path 1 (Datapel) | Path 1 (Ostendo) | Path 2 (Cin7 Core) | Path 2 (Unleashed) | Path 2 (Odoo, Enterprise) | Path 4 (MYOB Acumatica) |
|-----------|------------------|------------------|--------------------|--------------------|---------------------------|-------------------------|
| Core platform (3-yr) | ~A$34,000 | ~A$32,000 (all-modules) | ~A$72,000 | ~A$88,000 | ~A$17,000 licence + ~A$34,000 partner ≈ A$51,000 | ~A$45,000 subscription (≈6 users) |
| Shopify automation | ~A$6,000–18,000 | ~A$6,000–18,000 | included | included | included | via connector/partner |
| MYOB middleware | n/a (native) | n/a (native) | included above | included above | ~A$6,500 | n/a (MYOB *is* the platform) |
| Implementation/partner | (in core) | (in core) | (in core) | (in core) | (in core) | ~A$50,000–150,000 |
| Shipping layer (Starshipit) | ~A$5,000 | ~A$5,000 | ~A$5,000 | ~A$5,000 | ~A$5,000 | ~A$5,000 |
| **Indicative 3-Year TCO** | **~A$45,000–57,000** | **~A$45,000–60,000** | **~A$77,000** | **~A$93,000** | **~A$62,000–66,000** (partner-dependent A$60k–110k) | **~A$140,000–280,000** |
| With contingency (see below) | **~A$55,000–70,000** | **~A$55,000–72,000** | **~A$95,000** | **~A$115,000** | **~A$80,000–135,000** | **~A$170,000–340,000** |

> **Odoo TCO caveat**: the Odoo figure is **dominated by implementation-partner scope** and is the widest range of all options. Odoo **Community** removes the ~A$17k Enterprise licence but substitutes **self-hosting + maintenance** (you own upgrades/patching/connector upkeep) — often a net wash for a 5-person team and a Principle-1 concern. The MYOB-connector line carries the highest *quality* risk of any option (no maintained two-way AccountRight connector found).

> Ranges, not point estimates, because the price is dominated by undecided discovery variables (G-6): SKU count, per-channel order volume (drives Unleashed/Cin7 order tiers), MYOB edition, BOM complexity, and the confirmed **5-vs-7 storefront count** (drives connector count and licensing — Risk R-6). Re-quote against reality before procurement.

### Alternative Scenarios

- **Scenario A — Build everything**: ~A$450k–900k+. Maximum control; highest cost/risk; breaches Principle 1. **Rejected.**
- **Scenario B — Buy a hub (Path 2)**: ~A$77k–115k. One architecture solves all three problems; larger change + MYOB-middleware dependency + (for Cin7) reliability risk.
- **Scenario C — Buy MYOB-native WMS (Path 1) + companion Shopify automation**: ~A$55k–70k. Lowest disruption and cost; leaves MYOB as the long-term ceiling.
- **Scenario D — Recommended phased blend**: ~A$70k–120k. Decide source of truth (G-1) → pilot one channel → phase rollout, allowing a Path-1-now / Path-2-later option if appetite is incremental.
- **Scenario E — Odoo as hub, MYOB kept for accounting (Path 2)**: ~A$80k–135k risk-adjusted. Best BOM/WMS depth and no per-seat lock-in (Community), **but** the weakest MYOB-integration story (no maintained two-way AccountRight connector) and ERP-scale change. Recommend only with deliberate appetite for an ERP project.
- **Scenario F — Odoo as near-full ERP, replace MYOB (Path 3)**: ~A$95k–200k+. Removes the MYOB-integration problem by removing MYOB; largest change, full accounting-migration risk; **out of current scope** (the brief is about inventory truth, not replacing the accounting platform). Noted for completeness.
- **Scenario G — MYOB-native operations layer on AccountRight (Path 1, Ostendo)** *(added v1.2)*: ~A$55k–72k risk-adjusted. Like the Datapel scenario but with deeper MYOB-native manufacturing/job-costing; same companion Shopify-automation workstream. **A direct alternative to Scenario C** — evaluate Ostendo vs Datapel head-to-head.
- **Scenario H — Upgrade the MYOB platform to MYOB Acumatica (Path 4)** *(added v1.2)*: ~A$170k–340k risk-adjusted. Replaces AccountRight; inventory/WMS/manufacturing built in; removes all third-party accounting integration but is a full platform migration at the highest cost. **Strategic option for when AccountRight becomes the ceiling — not the first move.**

### TCO Assumptions

- Consulting/implementation day rate: ~A$1,200/day (blended AU SME integrator).
- SaaS list prices with ~10%/yr increase; Cin7 USD list converted at ~A$1.55/US$1 (FX risk flagged).
- Warehouse hardware: scanners + label printers ~A$4,000 up front.
- Order volume assumed modest-SME; **Unleashed/Cin7 order-tier uplifts not fully priced** pending G-6 — could move Path 2 figures up.
- Excludes internal staff time and any MYOB edition upgrade if AccountRight version is below Datapel's supported range (v8.5–19.7) [RSCH-C9].
- **Odoo**: Enterprise ~A$45–65/user/mo for ~6 users; AU implementation A$15k–60k + A$5k–10k/yr ongoing [RSCH-C19][RSCH-C20]; Community removes licence but adds self-hosting/maintenance. Odoo's +35% contingency reflects the unproven MYOB connector and ERP-scale uncertainty.
- **Ostendo (v1.2)**: transparent all-modules pricing (no per-module upsell) + Freeway mobility add-on; MYOB-native (no middleware line). Modelled comparable to Datapel; +20% contingency for Shopify-multi-store/Magento connector confirmation [RSCH-C24][RSCH-C27].
- **MYOB Acumatica (v1.2)**: A$104–179/user/mo + A$50k–150k implementation + ~A$2k–5k/mo ongoing [RSCH-C23]; the highest-cost option and a platform migration (no separate accounting integration).

### Risk-Adjusted TCO

| Scenario | Base TCO | Contingency | Risk-Adjusted | Risk factors |
|----------|----------|-------------|---------------|--------------|
| Build everything | A$450k+ | +30% | A$585k+ | Scope creep, key-person, API treadmill |
| Path 2 — Cin7 | A$77k | +25% | ~A$96k | Sync reliability (R-2), middleware, FX, order-tier uplift |
| Path 2 — Unleashed | A$93k | +20% | ~A$112k | Add-on/order-tier uplift, MYOB middleware, UI learning curve |
| Path 2 — Odoo (Enterprise) | A$66k | +35% | ~A$89k | Unproven MYOB connector, ERP-scale implementation, partner scope, open-source maintenance |
| Path 1 — Ostendo *(v1.2)* | A$55k | +20% | ~A$66k | Shopify-multi-store/Magento connector confirmation; otherwise MYOB-native low-risk |
| Path 1 — Datapel | A$52k | +15% | ~A$60k | Shopify-automation workstream scope, onboarding pace |
| Path 4 — MYOB Acumatica *(v1.2)* | A$200k | +25% | ~A$250k | Platform migration, implementation scope, change magnitude (but no accounting-integration risk) |

---

## Requirements Traceability (mapped to stakeholder goals, in lieu of ARC-001-REQ)

| Goal | Description | Category | Recommended solution | Rationale |
|------|-------------|----------|----------------------|-----------|
| G-1 | Decide & document source of truth first | 1 | **Process gate** (ADR) before product selection | Principle 6; brief B4 — gating decision, not a product |
| G-2 | Eliminate Shopify re-keying | 1 | Path 2 hub (Cin7/Unleashed/**Odoo** native) **or** Path 1 + Shopify-automation connector (Amaka) [RSCH-C6][RSCH-C22] | Key Path differentiator |
| G-3 | Idempotent sync / no oversell / no duplicates | 1 | Native sync (Datapel/**Ostendo**) or hub (Unleashed preferred on reliability) + pilot test (G-5); MYOB Acumatica avoids the connector entirely | Principle 10; Risk R-2 |
| G-4 | Warehouse discipline (≥98% accuracy) | 2 | Datapel or **Ostendo Freeway** WMS (MYOB-native), Cin7/Unleashed WMS, Odoo/ERPNext WMS, or **MYOB Acumatica** built-in + Starshipit [RSCH-C27] | All adequate-to-strong |
| G-5 | Buy proven product + real-data pilot | 1–4 | BUY confirmed; pilot one channel, test duplicate-order & oversell | Principle 17; brief B7 |
| G-6 | Quantify the operation | — | **Discovery data pack** (prerequisite gap) | Needed before any quote; Risk R-6 |
| G-7 | Preserve BOM/manufacturing | 3 | **Ostendo BOM-with-routings + job costing (MYOB-native)**, Datapel work-orders, Unleashed MRP, Odoo/ERPNext multi-level MRP (deepest, non-native MYOB), or **MYOB Acumatica** Manufacturing edition [RSCH-C7][RSCH-C14][RSCH-C21][RSCH-C24] | All preserve BOM; Ostendo is the deepest *MYOB-native* fit |

### Coverage Summary

- ✅ **6 of 7 goals (~86%)** have an identified product-backed path under at least one Path.
- ⚠️ **G-2** depends on Path choice (native in Path 2; companion Shopify-automation workstream in Path 1 for Datapel/Ostendo).
- ✅ **v1.2** strengthens coverage: the MYOB-native shortlist for G-3/G-4/G-7 grows from one (Datapel) to three (Datapel, Ostendo, MYOB Acumatica), reducing reliance on middleware.
- 🔍 **G-6** is a prerequisite gap — capture before vendors quote.

**GAP-1 — Operational quantification (G-6)**: SKU count, per-channel order volume, MYOB AccountRight edition/version, BOM depth, warehouse bin count, and the confirmed **5-vs-7 storefront count** are unknown. *Impact*: vendors cannot quote accurately; order-tier and connector-count drive Path 2 cost. *Recommendation*: complete the discovery data pack (G-6) and confirm storefront count (Risk R-6) before procurement.

**GAP-2 — MYOB AccountRight version compatibility**: Datapel's adaptor supports AccountRight v8.5–19.7 [RSCH-C9]; if Cycle Motion runs a newer/older or cloud-only edition, confirm compatibility. *Recommendation*: capture exact MYOB edition/version in discovery.

**GAP-3 — Australian data residency / APP posture for Path 2 hubs**: Cin7 is NZ-based on Azure [RSCH-C11]; Unleashed is NZ-origin; Odoo hosting is buyer-chosen (Online/EU, Odoo.sh, or self-hosted AU). *Impact*: Principle 7 (APPs, cross-border transfer). *Recommendation*: obtain written data-residency and APP/sub-processor statements from any Path 2 vendor and the middleware provider; for Odoo, choose hosting region deliberately.

**GAP-4 — Odoo↔MYOB AccountRight connector maturity (added v1.1)**: No maintained two-way AccountRight connector was found; the available paid app does not confirm AccountRight support or two-way sync, and the OCA module targets AccountEdge [RSCH-C17][RSCH-C18]. *Impact*: HIGH — this link would sit in the idempotent-sync critical path (Principles 9, 10). *Recommendation*: if Odoo is shortlisted, treat the MYOB connector as a **proof-of-concept gate** before any commitment, or accept Path 3 (Odoo's own accounting).

---

## Australian Context, Compliance & Privacy

> Replaces the template's UK-Government section. Cycle Motion is a private Australian company (Perth, WA); UK Digital Marketplace / G-Cloud / GOV.UK platforms and government-code-reuse do not apply.

### Australian Privacy Principles (APPs)

Per Principle 7, customer/personal data must be handled in line with the **Australian Privacy Principles (Privacy Act 1988)**. Path 2 introduces overseas-hosted platforms (Cin7 on Azure; both hubs NZ-origin) and a middleware vendor into the customer/order data path — engaging APP 8 (cross-border disclosure) and data-residency considerations. **Action**: obtain written data-residency, hosting-region, and sub-processor statements from any selected vendor and middleware provider; consider `/arckit:au-pia` for a full Privacy Impact Assessment if Path 2 is chosen. Confirm whether the Privacy Act small-business exemption applies (turnover/threshold); APP-aligned handling is the recommended baseline regardless.

### PCI-DSS / Payment Handling

Per Principle 14, card data must stay within compliant providers' boundaries and never enter Cycle Motion's internal systems. **None of the researched products is a payment processor** — Shopify and Magento already tokenise payments through compliant gateways. The inventory/WMS/hub layer should receive **order and fulfilment data only, never raw card numbers**, keeping PCI-DSS scope minimised. **Action**: verify in the pilot that no PAN flows from storefront → core → MYOB; confirm order payloads carry tokens/last-4 only.

### Australian Vendor / Support Posture

- **Datapel** — AU/NZ vendor, 200+ AU/NZ MYOB customers; AU-relevant support [RSCH-C2].
- **Unleashed** — NZ-origin, AUD pricing, ANZ manufacturer base; generally good support reputation [RSCH-C15].
- **Cin7** — NZ-origin (Auckland), USD pricing, global support but reputation concerns on responsiveness [RSCH-C11][RSCH-C13].
- **Starshipit** — ANZ-built shipping aggregator with deep Australia Post/Aramex/Sendle coverage [RSCH-C16].
- **Odoo** — Belgium-based; large AU implementation-partner network; hosting region buyer-chosen (Online/EU, Odoo.sh, or self-hosted AU); support via Enterprise subscription or the partner (Community) [RSCH-C19][RSCH-C20].

---

## Reliability & Support Reputation (the brief's explicit concern)

The brief flags that reviews report **sync drops and support-quality concerns for Cin7** and asks for an even-handed verification.

**Cin7 — concern confirmed, current**: 2025–2026 reviews (Shopify App Store, GetApp, Capterra) report: Shopify connection "riddled with issues" (variant deletion, inability to remap/add variants or update stock/prices), **stock disconnecting while showing "connected"**, blank/partial orders pulling through, order-routing logic gaps, **frequent price increases**, and **slow, email-only support with multi-week/-month ticket delays** [RSCH-C12][RSCH-C13]. Cin7 retains genuine strengths (broadest connectors incl. native Magento; large customer base ~8,000) [RSCH-C4][RSCH-C11], but these reports bear directly on G-3 and Principle 10. **Reference-check support specifically and pilot the Shopify sync before any commitment (Risk R-2, R-4).**

**Unleashed — generally stronger, with caveats**: praised for inventory accuracy and responsive support follow-up; one manufacturer cited near-flawless results at 500 orders / 1,500 items per week. Caveats: **rigid UI / steep learning curve**, occasional third-party-integration sync issues, and a **poorly-communicated paid "premium support" tier (A$79/mo)** with refund disputes [RSCH-C15].

**Datapel — smaller sample, mixed-positive**: ~53 Capterra reviews; generally positive on ease of use and proactive support, but some reports of **slow query turnaround** and **multi-product onboarding complexity (~3 months in one case)** [RSCH-C8].

**Odoo — strong product reputation, but support depends on edition/partner**: Odoo itself is well-reviewed for capability and value; the key reliability variable here is **not the Odoo core but the MYOB connector and the implementation partner**. With Community, there is no vendor SLA — support is the partner's or the community's; with Enterprise, Odoo provides support but **not for the third-party MYOB connector**. The idempotent-sync risk for "Odoo + MYOB" therefore concentrates on an unproven connector with no clear single owner — the opposite of what Principle 10 and Risk R-2 require. **Treat the MYOB link as a proof-of-concept gate.**

**Implication**: support quality is where these platforms live or die. Make the brief's **reference-check-support** and **failure-mode pilot** non-negotiable gates (Principle 17; goals G-5), regardless of Path.

---

## De-Risking Sequence (framing the recommendation per brief B7)

The recommendation is framed around the brief's evidence-led sequence and the architecture principles:

1. **Confirm build vs buy → BUY** (settled; this research confirms it — Principle 1).
2. **Decide the inventory source of truth (G-1, Principle 6) — the gating decision — *before* product selection.** Record appetite for change (incremental → Path 1; transformational → Path 2) as an ADR.
3. **Quantify the operation (G-6):** SKU count, per-channel order volume, **MYOB AccountRight edition/version** (vs Datapel's v8.5–19.7 support), BOM complexity, bin count, and the confirmed **5-vs-7 storefront count** — so vendors quote against reality (Risk R-6).
4. **Pilot one channel with real data (G-5, Principle 17)** — explicitly provoke the two failure modes that break these integrations: **duplicate orders** and **oversell on simultaneous sales**. For Path 2, the pilot must also exercise the **MYOB middleware** for idempotency.
5. **Reference-check vendor support specifically (Risk R-2)** — weighted heavily for Cin7.
6. **Phase the rollout (Principle 15)** — start with the pain bleeding most (the manual Shopify stores), not a big-bang cutover; keep a verified backup and rollback (Principle 18).

**Plain recommendation**: **BUY, and decide source-of-truth first.** If appetite is **incremental and warehouse-discipline-led**, choose **Path 1 (Datapel)** now — MYOB-native, lowest-risk — and run a parallel Shopify-automation workstream, keeping Path 2 open for later. If appetite is **transformational** and leadership accepts a larger, carefully-managed migration, choose **Path 2** — with **Unleashed favoured on manufacturing fit and reliability**, and **Cin7 Core only if reference checks and the pilot clear its sync-reliability and support concerns**. **Odoo (added v1.1) does not displace this ordering**: it is the most capable platform but, framed as "Odoo *with* MYOB", it carries the weakest accounting-integration story (no maintained two-way AccountRight connector) plus open-source self-maintenance — so it is recommended **only if Cycle Motion deliberately chooses an ERP-scale transformation**, in which case the honest target is Path 3 (Odoo's own accounting), which exceeds the current brief. Either way, the carrier layer (Starshipit) and the failure-mode pilot are constants.

---

## Vendor Shortlist for Further Evaluation

### 1. Datapel Cloud.WMS — Path 1 lead

**Overall rating**: ⭐⭐⭐⭐☆ (4/5)

- **Strengths**: MYOB-native two-way sync to AccountRight; bins/guided picking/barcode; native BOM/work-orders; AU/NZ vendor; low entry price; preserves Magento↔MYOB.
- **Concerns**: doesn't auto-solve Shopify; MYOB remains the ceiling; cycle-count/lot-serial depth and onboarding pace to confirm.
- **Next steps**: demo (confirm cycle counts, lot/serial, Shopify ingestion); quote against G-6; 3 AU MYOB reference checks; confirm AccountRight version compatibility.

### 2. Unleashed — Path 2 lead

**Overall rating**: ⭐⭐⭐⭐☆ (4/5)

- **Strengths**: strongest hub manufacturing/BOM (MRP, Kanban); good reliability/support reputation; AUD pricing; supported Shopify connector; single source of truth across channels.
- **Concerns**: no native MYOB connector (middleware); WMS/production are paid add-ons + low base order tier (cost creep); rigid UI; premium-support communication.
- **Next steps**: price full config (Pro + Multi-Bin + Production + order tier) against G-6; confirm MYOB middleware + Magento fit; pilot Shopify + MYOB idempotency.

### 3. Cin7 Core — Path 2 alternative

**Overall rating**: ⭐⭐⭐☆☆ (3/5) — *contingent on reference checks*

- **Strengths**: broadest connectors incl. native Magento + Shopify; multi-entity Omni for many storefronts; light MRP; large customer base.
- **Concerns**: **sync-reliability and support reputation (current)**; no native MYOB connector; USD/FX; tier costs climb.
- **Next steps**: **reference-check support and Shopify sync specifically (mandatory)**; pilot duplicate-order/oversell + MYOB middleware; confirm AU data residency/APP posture before any commitment.

### 4. Odoo — Path 2/Path 3 contender (added v1.1)

**Overall rating**: ⭐⭐⭐☆☆ (3/5) for "Odoo with MYOB" (Path 2) — *capability is 5/5; the MYOB-integration fit and maintenance model pull it down for this brief*

- **Strengths**: deepest BOM/MRP and barcode-WMS of any option; native multi-store Shopify + Magento; no per-seat lock-in (Community, LGPL-3.0); one platform spans the back office.
- **Concerns**: **no maintained two-way MYOB AccountRight connector** (weakest accounting story); open-source self-maintenance (Community) or per-user subscription (Enterprise); ERP-scale change heavier than the brief's "minimal disruption"; TCO dominated by partner scope.
- **Next steps**: **MYOB-connector proof-of-concept as a hard gate** (or accept Path 3 = drop MYOB); scope an AU implementation partner against G-6; pilot Shopify + the MYOB link for idempotency; decide hosting region (APP).

### 5. Ostendo (Development-X) — Path 1 rival to Datapel (added v1.2)

**Overall rating**: ⭐⭐⭐⭐☆ (4/5) — *strong new MYOB-native contender; one open question on Shopify multi-store*

- **Strengths**: **MYOB-AccountRight-native** (live link, near-real-time financials, no middleware); **deep manufacturing** — BOM-with-routings, job costing, scheduling, three-way matching; Freeway barcode WMS + POS; AU/NZ vendor; transparent all-modules pricing.
- **Concerns**: **Shopify multi-store and Magento connector depth must be confirmed** (typically via AU integrators, not a first-party multi-store connector); smaller brand profile than the SaaS hubs.
- **Next steps**: demo head-to-head vs Datapel; confirm Shopify-multi-store + Magento handling; quote against G-6; AU reference checks (manufacturing/wholesale). **Add to the evaluate/score shortlist alongside Datapel.**

### 6. MYOB Acumatica — Path 4, upgrade the MYOB platform (added v1.2)

**Overall rating**: ⭐⭐⭐⭐☆ (4/5) as a *strategic* option — *not the minimal-disruption first move*

- **Strengths**: MYOB's own cloud ERP — inventory, WMS, manufacturing built in; **no third-party accounting integration** (removes the connector risk entirely); AU-hosted, commercially supported, MYOB partner channel; scales well (addresses Principle 2 ceiling).
- **Concerns**: full **accounting-platform migration** (replace AccountRight); **highest cost** (A$104–179/user/mo + A$50k–150k implementation); larger change than the brief asks for now.
- **Next steps**: hold as the **scaling-ceiling answer**; revisit if/when AccountRight limits growth; if pursued, scope as an ERP migration with full discovery, not a WMS bolt-on.

### 7. ERPNext (Frappe) — open-source ERP, Odoo's peer (added v1.2)

**Overall rating**: ⭐⭐⭐☆☆ (3/5) for "ERPNext with MYOB" — *capable, but same caveats as Odoo*

- **Strengths**: strong multi-level BOM/MRP, work orders, capacity planning, subcontracting; multi-warehouse + barcode; Shopify/Magento connectors; fully open-source (no licence lock-in).
- **Concerns**: **no native MYOB connector** (middleware/custom); open-source **self-maintenance** (Principle 1); ERP-scale change.
- **Next steps**: only if an open-source ERP is deliberately preferred over Odoo — otherwise not ahead of the MYOB-native options; MYOB-connector PoC as a hard gate.

---

## Risks and Mitigations

**VR-1 — Non-native MYOB integration (Path 2)**: Hubs and open-source ERPs lack native MYOB connectors; a third-party connector enters the idempotent-sync path. **For Odoo and ERPNext this is most acute** — no maintained two-way AccountRight connector was found, so the connector is the least proven of any option. *Impact* HIGH · *Likelihood* HIGH for Path 2 (HIGHEST for Odoo/ERPNext). *Mitigation*: price and own the connector/middleware explicitly; make it a proof-of-concept gate; pilot it for idempotency/recovery (Principle 10); keep it in a replaceable layer (Principle 9); consider Path 3/Path 4 (drop the external accounting link — Odoo's own books, or MYOB Acumatica) to remove the connector entirely. **The MYOB-native options (Datapel, Ostendo) avoid this risk by design (v1.2).**

**VR-2 — Vendor reliability/support (esp. Cin7)**: sync drops and slow support reported [RSCH-C12][RSCH-C13]. *Impact* HIGH · *Likelihood* MEDIUM. *Mitigation*: reference-check support; pilot failure modes; contractual support SLA; retain a second shortlisted vendor as fallback (Risk R-2).

**VR-3 — Price increases / FX (Path 2)**: SaaS increases + USD exposure (Cin7). *Impact* MEDIUM. *Mitigation*: multi-year fixed pricing; cap clauses; budget +10%/yr and FX buffer.

**TR-1 — Order-tier / connector under-scoping (Risk R-6)**: 5-vs-7 storefront ambiguity and order volume drive Path 2 cost. *Impact* MEDIUM. *Mitigation*: complete G-6; build connector contingency into quotes.

**CR-1 — Australian data residency / APP (Path 2)**: overseas hosting + middleware. *Impact* MEDIUM–HIGH. *Mitigation*: written residency/sub-processor statements; `/arckit:au-pia` if Path 2.

**VR-4 — Open-source self-maintenance / ERP scope (Odoo)**: Odoo Community shifts hosting, upgrades, patching and connector upkeep in-house — a Principle-1 and brief "no maintenance treadmill" tension; an ERP-scale implementation is a larger change than the brief intends. *Impact* MEDIUM–HIGH · *Likelihood* MEDIUM. *Mitigation*: prefer Odoo Enterprise (managed) over Community for a 5-person team if Odoo is chosen; engage a certified AU partner with a support retainer; scope tightly to inventory/manufacturing/WMS first, not a big-bang ERP.

**VR-5 — Accounting-platform migration risk (Path 4, MYOB Acumatica)** *(added v1.2)*: replacing AccountRight is a full GL/accounting migration — the largest change of any option, with data-migration, retraining and cutover risk, at the highest cost. *Impact* HIGH · *Likelihood* MEDIUM (only if Path 4 chosen). *Mitigation*: treat as a distinct ERP-migration project with its own discovery and business case; defer until AccountRight is the genuine ceiling; phased, with verified backup and parallel-run.

**MR-1 — Migration risk (Path 2/4)**: reworking the working Magento↔MYOB integration (Principle 18); for Odoo/ERPNext a broader ERP migration; for MYOB Acumatica a full accounting-platform migration. *Impact* HIGH. *Mitigation*: verified backup + rollback; phased cutover starting with highest-pain channel; preserve the existing integration until deliberately reworked with a fallback.

---

## Next Steps and Recommendations

### Immediate (0–2 weeks)

1. **Record the source-of-truth decision (G-1)** as an ADR — Path 1 vs Path 2 — with appetite-for-change, *before* shortlisting (Risk R-3).
2. **Complete the discovery data pack (G-6)** — SKUs, per-channel order volume, MYOB edition, BOM depth, bin count, confirmed storefront count (Risk R-6).
3. **Approve the shortlist** (MYOB-native: **Datapel** and **Ostendo**; hubs: Unleashed, Cin7 Core; **Odoo/ERPNext** if ERP-scale change is in appetite; **MYOB Acumatica** as the strategic Path-4 option) and the carrier layer (Starshipit). *(v1.2: Ostendo joins Datapel as a MYOB-native front-runner.)*

### Evaluation (2–6 weeks)

4. **Demos + quotes** against G-6 for the shortlisted core(s) on the chosen Path.
5. **Reference checks** — support quality specifically, weighted for Cin7 (Risk R-2).
6. **Failure-mode pilot** on one channel with real data — duplicate orders and oversell; for Path 2, exercise the MYOB middleware (Principle 17, G-5). **If Odoo is shortlisted, run a MYOB-connector proof-of-concept first as a go/no-go gate** (or confirm appetite for Path 3).

### Decision & rollout (6–12 weeks)

7. **Select** via `/arckit:evaluate` + `/arckit:score` (weighted matrix: MYOB depth, Shopify multi-store, Magento, BOM, WMS depth, reliability, AU support, TCO). **Run Datapel vs Ostendo head-to-head on the MYOB-native axis**; keep one hub (Unleashed) as the Path-2 comparator.
8. **Contract** with support SLA, price caps, data-residency/APP and exit/data-portability clauses.
9. **Phase the rollout** — Shopify pain first; verified backup + rollback (Principle 18).

### Integration with other ArcKit commands

- `/arckit:wardley` — position WMS/sync/carrier/BOM on the evolution axis (all product/commodity → buy).
- `/arckit:sobc` — feed this TCO and options into the Economic Case.
- `/arckit:evaluate` / `/arckit:score` — weighted vendor scoring on the chosen Path.
- `/arckit:sow` — RFP/SOW to the shortlisted vendor(s) with the pilot as a gated milestone.
- `/arckit:au-pia` — Privacy Impact Assessment if Path 2 (overseas hosting + middleware).

---

## Appendices

### Appendix A: Research Methodology

**Data sources**: vendor websites and pricing pages (Datapel, Unleashed, Cin7, Starshipit, Odoo); MYOB App Marketplace; **Odoo Apps Store (apps.odoo.com)** and **OCA GitHub** (MYOB connector maturity); AU Odoo-partner pricing/implementation-cost write-ups; Capterra / G2 / Software Advice / GetApp; Shopify App Store reviews; Australian integration-partner sites (SAAS Integrator, GrowthPath); the SQUIZZ Connector adaptor documentation (MYOB AccountRight version support). **v1.2 added**: MYOB Acumatica product/pricing pages and AU partner cost guides; Ostendo (ostendo.info) and AU integrator sites (iBis/MyIntegrator); Frappe/ERPNext docs; Retail Express by Maropost (MYOB marketplace, GetApp); Katana/Fishbowl/SalesIn integration docs (cull-list verification); Tryton/Apache OFBiz project pages. v1.0–v1.1 sources accessed 2026-06-29; v1.2 sources accessed 2026-06-30.

**Evaluation criteria**: MYOB integration depth and edition compatibility; Shopify multi-store support; Magento/Adobe Commerce integration; BOM/manufacturing; WMS depth (bins, directed picking, barcode, cycle counts, lot/serial); multichannel sync and idempotency; carrier/shipping integration; Australian support/data residency; pricing and 3-year TCO; reliability/support reputation; PCI-DSS/APP posture — mapped to ARC-000-PRIN principles and ARC-001-STKE goals.

**Limitations**: list prices only (discounts likely); Cin7 in USD (FX-converted); order-tier/add-on costs depend on undecided G-6 data; review sentiment is a current snapshot (valid ~6 months); vendor data-residency/APP claims must be confirmed in writing.

### Appendix B: Glossary

- **WMS** — Warehouse Management System (bins, picking, scanning, counts).
- **BOM** — Bill of Materials (components of an assembled/manufactured item).
- **MRP** — Material Requirements Planning.
- **Idempotency** — processing the same message twice has no ill effect (no duplicate orders / double stock movement).
- **APP** — Australian Privacy Principles (Privacy Act 1988).
- **Middleware** — third-party connector bridging two systems lacking a native integration.
- **TCO** — Total Cost of Ownership (all costs over time).
- **ERP** — Enterprise Resource Planning (integrated suite spanning inventory, manufacturing, sales, purchasing, accounting — e.g. Odoo).
- **OCA** — Odoo Community Association (publishes community-maintained Odoo modules).
- **AccountEdge** — older MYOB desktop product (distinct from MYOB AccountRight); the OCA Odoo connector targets AccountEdge, not AccountRight.
- **MYOB Acumatica** (formerly MYOB Advanced) — MYOB's own cloud ERP (built on the Acumatica platform); inventory/WMS/manufacturing built in; the Path-4 "upgrade the platform" option.
- **Job costing** — tracking costs (materials, labour, overhead) against a specific job/work order; a strength of Ostendo.
- **Routings** — the sequence of operations/work-centres to manufacture an item; Ostendo supports BOMs with routings.

---

## External References

> Traceability from generated content back to source documents and web sources captured at fetch time (2026-06-29).

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| CB | company-brief.md | Company Brief & Project Overview | 000-global/external/ | Verified company profile + inventory/warehouse project brief (Cycle Motion) |
| STK | ARC-001-STKE-v1.0.md | Stakeholder Drivers & Goals | 001-inventory-warehouse-uplift/ | Stakeholders, drivers SD-1..6, goals G-1..7, outcomes, risks R-1..6 |
| PRIN | ARC-000-PRIN-v1.0.md | Architecture Principles | 000-global/ | 18 Cycle Motion architecture principles |
| ODOO | apps.odoo.com / odoo.com / OCA GitHub | Vendor & module sources (web) | external (web) | Odoo pricing, MYOB connector maturity, BOM/WMS and eCommerce connector evidence (added v1.1) |
| LAND | myob.com / ostendo.info / frappe.io / retailexpress.com.au + AU partner sites | Landscape-scan sources (web) | external (web) | MYOB Acumatica, Ostendo, ERPNext, Retail Express and cull-list MYOB-integration evidence (added v1.2) |

### Citations

| Citation ID | Source | Category | Captured Claim |
|-------------|--------|----------|----------------|
| RSCH-C1 | https://datapel.com/integrations/myob-integration/ | MYOB integration | Datapel integrates natively/two-way with MYOB AccountRight; orders, bills, inventory updates sync automatically with audit trails; bins, guided pick/pack/putaway, barcode scanning |
| RSCH-C2 | https://www.myob.com/au/apps/datapel-warehouse-management-system | Vendor/pricing | Datapel Cloud.WMS on MYOB App Marketplace; from A$120/mo; trusted by 200+ MYOB customers across AU/NZ |
| RSCH-C3 | https://www.cin7.com/pricing/ | Pricing | Cin7 Core Standard US$349 / Pro US$599 / Advanced US$999; users, order limits, integration counts; native Magento/Shopify; assembly/MRP |
| RSCH-C3a | https://www.unleashedsoftware.com/en-au/pricing/ | Pricing | Unleashed Core A$449 / Pro A$819 (AUD); order/API limits; Warehouse Mgmt & Multi-Bin A$149/mo, Production A$69/mo, MRP A$129/mo add-ons; B2B A$119/mo |
| RSCH-C4 | https://www.cin7.com/blog/cin7-core-or-omni-which-one-is-right-for-your-business/ | Product fit | Cin7 Core vs Omni; Core native Magento/Shopify/Amazon/eBay/WooCommerce; Omni multi-entity, 700+ integrations |
| RSCH-C5 | https://www.growthpath.com.au/Business-IT/ (+ saasintegrator.com) | MYOB integration | No native Cin7 Core ↔ MYOB AccountRight connector; integration via third-party middleware |
| RSCH-C6 | https://www.zohoflow.com/en-in/apps/myob-accountright-live/integrations/unleashed-software/ ; https://www.myob.com/au/apps/shopify-by-amaka | MYOB/Shopify integration | Unleashed↔MYOB AccountRight via integration platform (no native connector evidenced); Shopify by Amaka on MYOB marketplace |
| RSCH-C7 | https://www.datapel.com/manufacturing/ ; https://help.datapel.com/support/solutions/articles/51000489348 | BOM/manufacturing | Datapel BOM + Work Orders; components decrement, finished stock added; traceable to PO |
| RSCH-C8 | https://www.capterra.com.au/software/199201/wms | Reviews | ~53 Capterra reviews; positive on ease/support; some slow query turnaround; multi-product onboarding ~3 months in one case; "no lock-in, pay for onboarding you need" |
| RSCH-C9 | https://www.squizz.com/docs/connector/Connector-Adaptor-Datapel-Warehouse-Management-System-(version-9).html | MYOB compatibility | Datapel/Connector adaptor supports WMS v9 and MYOB AccountRight v8.5–19.7 |
| RSCH-C10 | https://www.saasintegrator.com/cin7core-inventory-integration/ | MYOB middleware | SAAS Integrator provides Cin7 Core ↔ MYOB integration (Acumatica emphasised); two-way module-based sync |
| RSCH-C11 | https://www.cin7.com/about-us/ ; https://news.microsoft.com/en-nz/2022/06/07/ | Vendor profile | Cin7 founded 2011 Auckland NZ; acquired by Rubicon (2019, ~US$133M); ~8,000 customers/75 countries; hosted on Microsoft Azure |
| RSCH-C12 | https://apps.shopify.com/cin7-connected-inventory-v2/reviews | Reviews/reliability | Shopify↔Cin7 "riddled with issues": variant deletion, can't remap/add variants or update stock/prices; order-routing logic gaps |
| RSCH-C13 | https://www.getapp.com/operations-management-software/a/cin7/reviews/ | Reviews/support | Inventory-sync errors, stock disconnects while "connected", blank orders; slow email-only support, multi-week/month ticket delays; frequent price increases |
| RSCH-C14 | https://apps.shopify.com/unleashed-software ; https://www.unleashedsoftware.com/ | Manufacturing/Shopify | Unleashed digital BOM, assembly/disassembly, MRP, Kanban; supported Shopify/WooCommerce/Amazon connectors maintained by Unleashed |
| RSCH-C15 | https://www.capterra.com/p/126644/Unleashed/reviews/ ; https://www.g2.com/products/unleashed/reviews | Reviews | Praised for inventory accuracy + responsive follow-up (500 orders/1,500 items/wk near-flawless); rigid UI/learning curve; premium-support (A$79/mo) communication + refund disputes |
| RSCH-C16 | https://starshipit.com/integrations ; https://starshipit.com/au/partner/myob | Carrier/shipping | Starshipit integrates Shopify, Magento, MYOB, Cin7, DEAR, Unleashed, Datapel; carriers incl. Australia Post, Aramex, Sendle, DHL, Toll; tiers A$45–A$500/mo by volume |
| RSCH-C17 | https://apps.odoo.com/apps/modules/15.0/wt_myob_connector | MYOB integration (Odoo) | Warlock "MYOB Odoo Connector", ~US$315 one-time, Odoo 15–17; syncs customers/suppliers/products/CoA/taxes/sales+purchase orders; MYOB edition (AccountRight vs Business) unspecified; import-skewed; two-way unconfirmed |
| RSCH-C18 | https://github.com/OCA/connector-accountedge | MYOB integration (Odoo) | OCA Odoo modules connect to MYOB *AccountEdge* (older desktop product), not AccountRight |
| RSCH-C19 | https://www.odoo.com/pricing ; https://solwing.com.au/blog/erp-odoo-insights-2/odoo-enterprise-pricing-in-australia-2025-8 | Pricing (Odoo) | Odoo Community free (LGPL-3.0, self-hosted); Enterprise ~A$45–65/user/mo (annual); Online/Odoo.sh/on-premise hosting |
| RSCH-C20 | https://tryexcept.com.au/blog/odoo-implementation-cost-2026/ ; https://www.auboros.com/blog/odoo-erp-australia-6/odoo-erp-implementation-in-australia-complete-guide-for-2026-87 | Implementation (Odoo) | AU SME Odoo implementation A$15k–60k (2–4 modules); partner fees A$8k–50k+; ~A$120–350/hr; +A$5k–10k/yr ongoing |
| RSCH-C21 | https://www.odoo.com/documentation/19.0/applications/inventory_and_mrp/manufacturing.html | BOM/WMS (Odoo) | Multi-level BOMs, finite-capacity MRP, barcode app integrated with manufacturing; barcode-driven multi-warehouse operations |
| RSCH-C22 | https://apps.odoo.com/apps/modules/19.0/integration_shopify ; https://apps.odoo.com/apps/modules/16.0/integration_magento2 | eCommerce (Odoo) | Maintained Shopify and Magento 2 connectors; multiple stores → Odoo warehouses, per-location stock sync, BOM-aware availability |
| RSCH-C23 | https://www.myob.com/au/erp-software/products/myob-acumatica ; https://www.cloudfactory.co/solutions/erp/myob-acumatica/pricing ; https://businesshub.com.au/erp/how-much-does-myob-acumatica-cost | MYOB Acumatica (v1.2) | MYOB's own cloud ERP; Standard A$104 / Plus A$139 / Enterprise A$179 per user/mo; Manufacturing edition; implementation A$50k–150k; ongoing ~A$2k–5k/mo; inventory/WMS/mfg built in |
| RSCH-C24 | https://www.ostendo.info/ostendo/accounting/myob.php ; https://www.ostendo.info/ | Ostendo (v1.2) | Native MYOB AccountRight Live link, posts every few minutes (near-real-time financials); BOM with routings, assembly/work orders, job costing, scheduling, three-way matching |
| RSCH-C25 | https://frappe.io/erpnext/open-source-manufacturing-erp-software ; https://www.erpresearch.com/en-us/erpnext | ERPNext (v1.2) | Open-source ERP; multi-level BOM, work orders, production/capacity planning, subcontracting; no native MYOB connector (middleware/custom) |
| RSCH-C26 | https://www.myob.com/au/apps/retail-express ; https://retailexpress.com.au/integration | Retail Express (v1.2) | AU retail/POS by Maropost; on MYOB App Marketplace (MYOB Business oriented); data hosted Sydney/Azure; Shopify + Adobe Commerce; retail not manufacturing |
| RSCH-C27 | https://www.ostendo.info/ ; https://www.myintegrator.com.au/integrate/ostendo/ | Ostendo WMS/POS (v1.2) | Freeway mobile app — barcode picking/receiving/warehouse, multi-location; full POS (touchscreen, multi-station, EFTPOS); e-commerce/web-store + POS integration with live stock sync |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| README.md | 001-inventory-warehouse-uplift/ | Project scaffolding, no research content |
| .gitkeep | 000-global/external/ | Placeholder, no content |

## Spawned Knowledge

The following standalone knowledge files were created or updated from this research:

### Vendor Profiles

- `vendors/datapel-profile.md` — Created (confidence: High)
- `vendors/unleashed-profile.md` — Created (confidence: High)
- `vendors/cin7-profile.md` — Created (confidence: High)
- `vendors/starshipit-profile.md` — Created (confidence: Medium)
- `vendors/odoo-profile.md` — Created (confidence: High) [added v1.1]
- `vendors/ostendo-profile.md` — Created (confidence: High) [added v1.2]
- `vendors/myob-acumatica-profile.md` — Created (confidence: High) [added v1.2]
- `vendors/erpnext-profile.md` — Created (confidence: Medium) [added v1.2]

### Tech Notes

- `tech-notes/myob-accountright-integration.md` — Updated [v1.1: Odoo; v1.2: broadened native/connector landscape — Ostendo, MYOB Acumatica, ERPNext, Retail Express, cull-list]
- `tech-notes/idempotent-multichannel-inventory-sync.md` — Updated [v1.1: added Odoo MYOB-connector path]

---

**Generated by**: ArcKit `/arckit:research` agent
**Generated on**: 2026-06-29 (v1.0–v1.1); 2026-06-30 (v1.2)
**ArcKit Version**: 5.15.1
**Project**: Inventory & Warehouse Management Uplift (Project 001)
**AI Model**: Claude Opus 4.8 (1M context)

<!-- arckit-provenance:start -->

## Build Provenance

_Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix._

| Field | Value |
|-------|-------|
| Requested Effort | `max` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-06-29T23:26:55.930Z |

<!-- arckit-provenance:end -->
