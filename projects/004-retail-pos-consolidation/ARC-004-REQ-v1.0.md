# Project Requirements: Retail POS Consolidation

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:requirements`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-004-REQ-v1.0 |
| **Document Type** | Business and Technical Requirements |
| **Project** | Retail POS Consolidation (Project 004) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT — FICTIONAL DEMONSTRATION |
| **Version** | 1.0 |
| **Created Date** | 2026-07-06 |
| **Review Date** | 2026-08-06 |
| **Owner** | Betty Rubble (GM Retail) — Sponsor |
| **Distribution** | Executive team, store managers, shortlisted vendors, solution architecture advisor |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-06 | ArcKit AI | Initial creation from `/arckit:requirements` | [PENDING] | [PENDING] |

## Document Purpose

Defines requirements for consolidating 12 stores onto one POS platform,
integrated hub-first (Project 001) with CRM loyalty (Project 002). Drives
vendor evaluation, the platform decision (ARC-004-ADR-001), pilot design, and
rollout acceptance. Traces to ARC-004-STKE-v1.0, ARC-000-PRIN, ARC-000-PORT.

---

## Executive Summary

Twelve stores run three POS estates inherited from acquisitions; two stores
are unintegrated entirely. This project selects one cloud POS, integrates it
as a spoke of the inventory/order hub, enables loyalty at every counter,
brings workshop/servicing jobs in-platform, fixes payments economics
(least-cost routing, compliant surcharging), and completes rollout before the
June 2027 legacy contract renewal.

---

## 1. Business Requirements

| ID | Requirement | Priority | Traces to |
|----|-------------|----------|-----------|
| BR-001 | One POS platform across all 12 stores; legacy estates decommissioned | MUST | G-1 |
| BR-002 | All rollout complete before 2027-06-30 (Retail Express renewal) | MUST | G-1, SD-3 |
| BR-003 | Chain-wide stock visibility, inter-store transfers, cross-store returns | MUST | G-2 |
| BR-004 | Loyalty identify/earn/burn at every counter against the CRM master | MUST | G-4 |
| BR-005 | Workshop job management: booking, job card, parts from stock, labour, notify, invoice | MUST | G-5 |
| BR-006 | Least-cost routing (eftpos) on the terminal fleet; consistent, RBA-compliant surcharging config | MUST | G-3 |
| BR-007 | Buy a proven cloud POS; no custom build | MUST | PRIN |
| BR-008 | Pilot: one store per legacy cohort (Retail Express, Square, unintegrated) before rollout | MUST | T-1 |
| BR-009 | No store cutovers 15 Nov – 15 Jan (peak trade freeze) | MUST | T-3 |
| BR-010 | 3-year TCO ≤ A$600k incl. hardware, implementation, payments migration | MUST | CEO constraint |

## 2. Functional Requirements

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-001 | Sell, return, exchange, laybuy/deposit, quote → sale; ACL-compliant receipts and refund handling | MUST |
| FR-002 | Real-time availability lookup across stores + warehouse (hub query); reserve and transfer | MUST |
| FR-003 | Offline trading mode: sales continue during connectivity loss; queued sync with conflict handling | MUST |
| FR-004 | Customer lookup/attach at sale (CRM identity), loyalty accrual/redemption, sign-up at counter ≤ 10s (aligns FR-006 of Project 002) | MUST |
| FR-005 | Workshop module: bookings calendar, job status board, parts consumption decrements hub stock, customer notifications (SMS/email via CRM consent) | MUST |
| FR-006 | Serialised inventory support (bikes, e-bike batteries) incl. warranty registration at sale | MUST |
| FR-007 | Click-and-collect / ship-from-store order states consumed from the hub (Project 005 dependency) | SHOULD |
| FR-008 | Cash management: floats, banking, end-of-day with variance reporting | MUST |
| FR-009 | Chain reporting: sales by store/category/staff; workshop utilisation | MUST |
| FR-010 | Staff permissions incl. discount thresholds and manager overrides (audit-logged) | MUST |

## 3. Non-Functional Requirements

| ID | Category | Requirement | Priority |
|----|----------|-------------|----------|
| NFR-P-001 | Performance | Scan-to-total < 300 ms; card tender initiated < 2 s | MUST |
| NFR-A-001 | Availability | Trading continuity via FR-003; platform 99.9% during trading hours across AWST/AEST | MUST |
| NFR-S-001 | Security | Terminal fleet P2PE or acquirer-validated; no PAN storage in POS; SAQ scope minimised (G-6) | MUST |
| NFR-S-002 | Security | Staff SSO where supported; unique operator IDs mandatory (no shared logins) | MUST |
| NFR-C-001 | Compliance | Surcharge configuration cannot exceed cost of acceptance (RBA standard); centrally managed, not per-store | MUST |
| NFR-C-002 | Compliance | Receipts/refunds/warranty text templates reviewed against ACL | MUST |
| NFR-I-001 | Integrability | Hub-first: POS never integrates directly to MYOB/ERP; all stock and order events via the hub (ARC-000-PORT §2) | MUST |
| NFR-T-001 | Trainability | New casual staff member sale-ready in ≤ 2 hours of training | SHOULD |

## 4. Integration Requirements

| ID | Integration | Direction | Notes |
|----|-------------|-----------|-------|
| INT-001 | Inventory/Order hub | Bidirectional | Availability, sales/return events, transfers, click-and-collect states |
| INT-002 | CRM (Project 002) | Bidirectional | Identity lookup, loyalty earn/burn, consented notifications |
| INT-003 | Payments acquirer | Terminal-integrated | Least-cost routing enabled; settlement files to finance |
| INT-004 | E-Commerce (Project 005) | Via hub | Endless aisle / ship-from-store; no direct POS↔web coupling |

## 5. Data Requirements

| ID | Requirement |
|----|-------------|
| DAT-001 | Product master consumed from the hub; POS does not create SKUs locally |
| DAT-002 | Historic sales from the three legacy estates exported and archived for 7 years; only open laybys, gift cards, and workshop jobs migrated live |
| DAT-003 | Gift card and layby liabilities reconciled to finance at each store cutover |
| DAT-004 | Loyalty identifiers issued by CRM; POS stores tokens, not duplicated profiles |

## 6. Out of Scope

Self-checkout; e-commerce storefronts (Project 005); warehouse operations
(Project 001); accounting (Project 003).

## 7. Australian Regulatory Overlay Applicability

| Overlay / obligation | Applicable | Rationale |
|---|---|---|
| PCI DSS v4.x (acquirer-driven) | **YES — core** | NFR-S-001, G-6 |
| RBA surcharging standard + least-cost routing | **YES** | BR-006, NFR-C-001 |
| Australian Consumer Law | **YES** | FR-001, NFR-C-002 |
| `/arckit-au:pia` | YES (scoped) | Loyalty data at the counter — extension of Project 002 PIA |
| `/arckit-au:essential-eight` | YES (baseline) | Store device and admin hygiene |
| PSPF / ISM / DISP / SOCI-CIRMP | No | Private retailer |

## 8. Acceptance Summary

Rollout acceptance: pilot success criteria met in all three cohort stores
(zero unreconciled variance for 2 weeks each); G-1..G-6 instrumented; SAQ
attestation lodged; surcharge audit clean; workshop paper cards retired.
