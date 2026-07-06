# Project Requirements: E-Commerce Consolidation

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:requirements`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-005-REQ-v1.0 |
| **Document Type** | Business and Technical Requirements |
| **Project** | E-Commerce Consolidation (Project 005) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT — FICTIONAL DEMONSTRATION |
| **Version** | 1.0 |
| **Created Date** | 2026-07-06 |
| **Review Date** | 2026-08-06 |
| **Owner** | Sam Whitford (Digital & E-Commerce Lead) — Sponsor |
| **Distribution** | Executive team, wholesale team, shortlisted vendors, solution architecture advisor |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-06 | ArcKit AI | Initial creation from `/arckit:requirements` | [PENDING] | [PENDING] |

## Document Purpose

Defines requirements for consolidating the six-property web estate (1× Magento
B2B, 5× Shopify B2C) into a rationalised, hub-integrated commerce
architecture. Drives the platform decision (ARC-005-ADR-001), storefront
rationalisation, migration planning, and acceptance. Traces to
ARC-005-STKE-v1.0, ARC-000-PRIN, ARC-000-PORT.

---

## Executive Summary

Six independently maintained web properties duplicate catalogue and pricing
work, diverge from hub inventory truth, fragment customer identity, and carry
a self-managed Magento security burden. This project rationalises storefronts
(target ≤ 3 B2C + 1 B2B), replatforms to SaaS/PaaS, sources availability from
the hub, authenticates customers against the CRM, and enables click-and-collect
with Project 004.

---

## 1. Business Requirements

| ID | Requirement | Priority | Traces to |
|----|-------------|----------|-----------|
| BR-001 | Rationalise to ≤ 3 B2C storefronts + 1 B2B trade portal (CEO decision on final count) | MUST | G-4, T-1 |
| BR-002 | Retire the self-managed Magento infrastructure; all commerce on SaaS/PaaS | MUST | G-2 |
| BR-003 | Single product-information source feeding all storefronts | MUST | G-1 |
| BR-004 | All storefronts show hub-sourced availability; no locally-held stock figures | MUST | G-3 |
| BR-005 | B2B parity-plus at cutover: tiered/contract pricing, credit status, invoice history, backorder ETAs | MUST | G-6, T-3 |
| BR-006 | Customer accounts authenticate against the CRM identity (Project 002) | MUST | G-5 |
| BR-007 | Click-and-collect and ship-from-store across 12 stores (with Project 004) | SHOULD | G-7 |
| BR-008 | SEO equity preserved through migrations (redirect maps, structured data) | MUST | G-4 |
| BR-009 | Buy SaaS/PaaS platforms; custom development limited to themes and integration | MUST | PRIN |
| BR-010 | 3-year TCO ≤ A$550k incl. replatform, migrations, and licence | MUST | CEO constraint |

## 2. Functional Requirements

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-001 | Multi-storefront from one admin: shared catalogue, per-storefront branding/pricing visibility rules (MAP compliance per brand) | MUST |
| FR-002 | B2B: company accounts with multiple buyers, roles, order approval workflows | MUST |
| FR-003 | B2B: tiered/contract pricing, credit-limit display, pay-on-account checkout | MUST |
| FR-004 | B2C: full catalogue with faceted search, fitment/compatibility data (e.g. wheel↔frame standards) | MUST |
| FR-005 | Availability display: in-stock by location, backorder with ETA (hub-supplied) | MUST |
| FR-006 | Checkout: hosted/redirect card fields, PayPal, Apple/Google Pay; ACL-compliant pricing incl. GST display | MUST |
| FR-007 | Order orchestration via the hub: web never allocates stock directly | MUST |
| FR-008 | Click-and-collect selection with per-store availability and pickup notifications | SHOULD |
| FR-009 | Consent-aware marketing capture wired to CRM consent objects (Spam Act) | MUST |
| FR-010 | Content workflows: shared product content, per-brand storytelling pages | SHOULD |

## 3. Non-Functional Requirements

| ID | Category | Requirement | Priority |
|----|----------|-------------|----------|
| NFR-P-001 | Performance | Core Web Vitals "good" on product and listing pages (P75) | MUST |
| NFR-A-001 | Availability | 99.9%; sale-event scalability without pre-provisioning | MUST |
| NFR-S-001 | Security | No cardholder data touches our environment (SAQ-A posture); platform-managed patching | MUST |
| NFR-S-002 | Security | Admin SSO + MFA; least-privilege storefront roles | MUST |
| NFR-C-001 | Compliance | WCAG 2.2 AA on all customer-facing storefronts | MUST |
| NFR-C-002 | Compliance | ACL pricing/refund/warranty content reviewed; GST-inclusive display | MUST |
| NFR-D-001 | Data | Customer PII residency/adequacy assessed per APP 8 (aligns Project 002 NFR-D-001) | MUST |
| NFR-I-001 | Integrability | Hub-first: no direct web→MYOB/ERP or web→POS integration (ARC-000-PORT §2) | MUST |

## 4. Integration Requirements

| ID | Integration | Direction | Notes |
|----|-------------|-----------|-------|
| INT-001 | Inventory/Order hub | Bidirectional | Availability feeds, order capture, fulfilment states, C&C states |
| INT-002 | CRM (Project 002) | Bidirectional | Account identity, consent objects, order-history views |
| INT-003 | Payments PSP | Hosted | SAQ-A checkout; settlement to finance via standard reports |
| INT-004 | Shipping/3PL (via hub, per Project 001 Starshipit-class integration) | Hub-side | Web consumes tracking states only |
| INT-005 | POS (Project 004) | Via hub only | Ship-from-store and C&C choreography |

## 5. Data Requirements

| ID | Requirement |
|----|-------------|
| DAT-001 | Product master and pricing sourced from the hub/PIM; storefronts hold presentation data only |
| DAT-002 | Migration: customer accounts merged under Project 002 dedupe rules before storefront cutover; guest order history archived |
| DAT-003 | 301-redirect maps for every retired storefront URL with ≥ 12-month monitoring (BR-008) |
| DAT-004 | Trade pricing agreements versioned; effective-dated to prevent mid-order price drift |

## 6. Out of Scope

Marketplace channels (eBay/Amazon — future phase via the hub); in-store POS
(Project 004); ERP financials (Project 003).

## 7. Australian Regulatory Overlay Applicability

| Overlay / obligation | Applicable | Rationale |
|---|---|---|
| Australian Consumer Law | **YES — core** | Pricing display, refunds, warranties online |
| Privacy Act / APPs + Spam Act | **YES** | Accounts, consent capture (Project 002 PIA extension) |
| PCI DSS (SAQ-A posture) | **YES** | Hosted checkout requirement NFR-S-001 |
| WCAG 2.2 AA | **YES (policy)** | NFR-C-001 — good practice and DDA risk reduction |
| `/arckit-au:essential-eight` | YES (baseline) | Admin access hygiene |
| PSPF / ISM / DISP / SOCI-CIRMP | No | Private retailer |

## 8. Acceptance Summary

Cutover acceptance per storefront: hub-availability parity checks pass; SEO
redirect coverage 100% of indexed URLs; WCAG 2.2 AA audit clean on templates;
B2B pilot accounts confirm parity-plus (BR-005); zero web oversell in the
first 60 days (G-3).
