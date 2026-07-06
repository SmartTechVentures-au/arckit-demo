# Tech Note: Idempotent Multichannel Inventory Sync

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-TECH-idempotent-multichannel-inventory-sync-v1.0 |
| **Document Type** | Tech Note |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-06-29 |
| **Last Updated** | 2026-06-29 |
| **Owner** | Cycle Motion solution architecture advisor (Chris McKelt) |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-06-29 | ArcKit AI | Initial creation from `/arckit:research` agent | PENDING | PENDING |
| 1.1 | 2026-06-29 | ArcKit AI | Added Odoo MYOB-connector path to the middleware-risk finding (RSCH v1.1) | PENDING | PENDING |

---

## Summary

Multichannel commerce breaks on two specific failure modes: **duplicate orders** (a retry or webhook re-delivery creates a second order) and **oversell on simultaneous sales** (two channels sell the last unit before stock syncs). Both are consequences of non-idempotent, too-slow, or unrecoverable synchronisation between storefronts, an inventory source of truth, and accounting. Choosing and proving an inventory platform must therefore centre on *how it handles these failure modes*, not just its happy-path feature list — and the pilot must deliberately provoke them before any cutover.

## Key Findings

- **Idempotency is the core requirement.** Order and stock operations must be safe to retry — processing the same message twice must have no ill effect (no second order, no double stock decrement). This typically relies on idempotency keys / unique external order references and de-duplication on ingest.
- **Sync latency drives oversell exposure.** The window between a sale on one channel and stock updating on the others is the oversell window. Near-real-time sync (and a single authoritative stock figure all channels read) narrows it; batch/manual sync widens it. A single source of truth that every channel reads from is the structural fix.
- **Real products do fail here.** Current (2025–2026) reviews of at least one major hub report stock "disconnecting" while shown as connected, inventory failing to push to Shopify/Amazon, and blank/partial orders — concrete examples of the failure modes this note warns about. Vendor reliability reputation is therefore a first-class selection criterion.
- **Middleware multiplies the risk surface.** Where the accounting write-path is via third-party middleware (common when a hub lacks a native connector to the incumbent accounting system), that hop must also be idempotent and recoverable — it is part of the critical path, not a side channel. **The worst case is an unproven connector with no clear owner (added v1.1):** when a full ERP that ships its own accounting (e.g. Odoo) is bolted to an incumbent accounting platform (e.g. MYOB AccountRight) for which no maintained two-way connector exists, the integration in the critical path is both unproven and unowned — neither the ERP vendor nor an accounting-connector vendor stands behind it. Make such a connector a proof-of-concept go/no-go gate, or remove the link entirely by consolidating accounting into the ERP.
- **Observability closes the loop.** Failed/stuck syncs must alert a named human and be replayable from a retry/exception queue; silent failure is what turns a sync bug into an oversell incident discovered by an angry customer.
- **Prove it with a pilot.** The reliable way to de-risk is a one-channel, real-data pilot that explicitly tests duplicate-order and simultaneous-last-unit scenarios (including the middleware hop, if any) before phased rollout — start with the highest-pain channel and keep a verified backup and rollback.

## Relevance to Projects

- **Project 001 — Inventory & Warehouse Management Uplift (Cycle Motion)**: underpins Principle 10 (Reliable, Idempotent Synchronisation), Principle 15 (Order Integrity), goal G-3 (eliminate oversell), goal G-5 (failure-mode pilot), and Risk R-2/R-4. Applicable to any multichannel commerce project syncing stock and orders across storefronts and an accounting/inventory system of record.

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RSCH | ARC-001-RSCH-v1.0.md | Research Findings | 001-inventory-warehouse-uplift/research/ | Source research with full citations |
| PRIN | ARC-000-PRIN-v1.0.md | Architecture Principles | 000-global/ | Principles 10 & 15 (idempotent sync, order integrity) |

### Citations

| Citation ID | Source | Category | Captured Claim |
|-------------|--------|----------|----------------|
| RSCH-C12 | https://apps.shopify.com/cin7-connected-inventory-v2/reviews | Reliability | Shopify sync issues incl. inability to update stock; variant breakage |
| RSCH-C13 | https://www.getapp.com/operations-management-software/a/cin7/reviews/ | Reliability | Stock disconnects while "connected"; inventory fails to push; blank orders |

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
