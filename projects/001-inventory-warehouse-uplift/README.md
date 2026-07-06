# Project 001 — Inventory & Warehouse Management Uplift

**Organisation**: Cycle Motion Pty Ltd (ABN 80 162 266 604)
**Project ID**: 001
**Created**: 2026-06-29

## Summary

Strategic IT uplift for Cycle Motion, an Australian manufacturer and distributor of
performance cycling components trading across wholesale (B2B) and direct-to-consumer
(B2C) channels. The project aims to establish a reliable, automated **single source of
inventory truth** across all sales channels, eliminate manual order re-keying and
oversell, and introduce disciplined, system-guided warehouse operations — while
preserving manufacturing / BOM capability and scaling with channel and volume growth.

The gating architectural decision is *where the single source of inventory truth should
live*: keep the accounting platform as the inventory master and add a WMS layer (Path 1),
or introduce an inventory/order hub as the master and demote accounting to the books
(Path 2).

## Artifacts

| Type | Document | Status |
|------|----------|--------|
| Stakeholder Analysis | ARC-001-STKE-v1.0 | DRAFT |

## Related cross-project artifacts (000-global)

- ARC-000-PRIN-v1.0 — Cycle Motion Enterprise Architecture Principles

See `external/` for reference documents specific to this project.
</content>
