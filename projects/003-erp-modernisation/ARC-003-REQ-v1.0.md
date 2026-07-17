# Project Requirements: ERP Modernisation

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:requirements`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-003-REQ-v1.0 |
| **Document Type** | Business and Technical Requirements |
| **Project** | ERP Modernisation (Project 003) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT — FICTIONAL DEMONSTRATION |
| **Version** | 1.0 |
| **Created Date** | 2026-07-06 |
| **Review Date** | 2026-08-06 |
| **Owner** | Jane Jetson (Finance Manager) — Sponsor |
| **Distribution** | Executive team, finance team, shortlisted vendors, solution architecture advisor |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-06 | ArcKit AI | Initial creation from `/arckit:requirements` | [PENDING] | [PENDING] |

## Document Purpose

Defines requirements for replacing MYOB AccountRight as the financial system of
record with a cloud ERP, executed as the **final** portfolio move under the
hub-first pattern. Traces to ARC-003-STKE-v1.0, ARC-001-ADR-001 (the decision
being superseded), ARC-000-PORT (sequencing gate PR-5), and ARC-000-PRIN.

---

## Executive Summary

MYOB AccountRight was consciously retained during the inventory uplift
(ARC-001-ADR-001). The scenario has outgrown it: two entities, ~160 staff on
multi-state payroll, landed-cost imports, Peppol demand from trade customers,
and a 12-day close. This project selects and implements a cloud ERP whose
cutover is a *contained* change — because every channel system integrates via
the inventory/order hub, only the hub→accounting integration re-points.

---

## 1. Business Requirements

| ID | Requirement | Priority | Traces to |
|----|-------------|----------|-----------|
| BR-001 | Multi-entity general ledger with automated consolidation and inter-entity eliminations | MUST | G-1 |
| BR-002 | Month-end close ≤ 5 business days within 3 months of cutover | MUST | G-1 |
| BR-003 | Australian payroll in-platform or via certified integration: STP Phase 2, multi-state, award interpretation, superannuation (SuperStream) | MUST | G-2 |
| BR-004 | Landed-cost capitalisation (freight, duty, insurance) at goods receipt, flowing to inventory valuation and margin | MUST | G-3 |
| BR-005 | Peppol e-invoicing (send and receive) for trade customers | MUST | G-4 |
| BR-006 | Channel-level P&L (wholesale / retail stores / online) without manual assembly | MUST | G-6 |
| BR-007 | Implementation start gated on Projects 004 & 005 go-live (ARC-000-PORT PR-5) | MUST | G-5, T-1 |
| BR-008 | Buy a proven cloud ERP; no custom build; implementation by an accredited AU partner | MUST | PRIN |
| BR-009 | 3-year TCO ≤ A$900k including implementation and migration | MUST | CEO constraint |
| BR-010 | MYOB AccountRight retained read-only for 7 years post-cutover (records retention) | MUST | ATO/Corps Act retention |

## 2. Functional Requirements

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-001 | GL, AP, AR, bank feeds and reconciliation for AU banks | MUST |
| FR-002 | GST/BAS preparation with ATO-aligned tax codes; BAS lodgement workflow | MUST |
| FR-003 | Fixed assets register with AU tax depreciation | SHOULD |
| FR-004 | Purchase-to-pay: PO, receipt (from hub events), 3-way match, approvals | MUST |
| FR-005 | Inventory valuation as a *subscriber* to the hub — ERP values what the hub records; it does not become a second inventory master | MUST |
| FR-006 | Multi-currency purchasing (USD/EUR/CNY suppliers) with realised/unrealised FX | MUST |
| FR-007 | Budgeting and monthly board reporting pack | SHOULD |
| FR-008 | Manufacturing/BOM cost roll-up preserved for the wheel-build line (parity with Project 001 scope) | MUST |
| FR-009 | Role-based approval workflows (delegations of authority) | MUST |

## 3. Non-Functional Requirements

| ID | Category | Requirement | Priority |
|----|----------|-------------|----------|
| NFR-A-001 | Availability | 99.9%; month-end and payroll windows protected | MUST |
| NFR-S-001 | Security | SSO (Entra ID), MFA, least-privilege roles; Essential Eight ML1 alignment for admin | MUST |
| NFR-D-001 | Residency | Financial and payroll data hosted in Australian regions | MUST |
| NFR-I-001 | Integrability | Documented APIs/webhooks; hub→ERP journal and AR/AP event contracts versioned | MUST |
| NFR-M-001 | Migration | Opening balances + 2 years transactional history migrated and reconciled to the cent; older history via BR-010 archive | MUST |
| NFR-C-001 | Compliance | Payroll certified for STP Phase 2; SuperStream conformance | MUST |

## 4. Integration Requirements

| ID | Integration | Direction | Notes |
|----|-------------|-----------|-------|
| INT-001 | Inventory/Order hub | Hub → ERP | Sales/purchase journals, COGS, receipts. The only integration re-pointed at cutover (G-5) |
| INT-002 | CRM (Project 002) | CRM → ERP | Trade account terms/credit sync (via hub where practical) |
| INT-003 | Banking | Bidirectional | Bank feeds, ABA/NPP payment files |
| INT-004 | ATO / Peppol access point | Bidirectional | STP, BAS, e-invoicing |
| INT-005 | Payroll (if best-of-breed per ADR-003-001 §7) | Bidirectional | GL journals back to ERP |

## 5. Data Requirements

| ID | Requirement |
|----|-------------|
| DAT-001 | New chart of accounts designed for channel P&L (BR-006) before migration mapping — no lift-and-shift of the MYOB CoA |
| DAT-002 | Reconciliation evidence pack at cutover: trial balance, AR/AP ageing, inventory valuation, payroll YTD — signed by external accountant [STK-E8] |
| DAT-003 | Employee data migration under Privacy Act APPs; TFN handling per TFN Rule 2015 |

## 6. Out of Scope

POS transactions (Project 004 → hub), e-commerce (Project 005 → hub), CRM
customer master (Project 002). Advanced WMS (delivered in Project 001).

## 7. Australian Regulatory Overlay Applicability

| Overlay / obligation | Applicable | Rationale |
|---|---|---|
| ATO STP Phase 2, SuperStream, BAS/GST | **YES — core** | Payroll and tax compliance |
| Peppol e-invoicing | **YES** | BR-005; ATO-encouraged B2B standard |
| `/arckit-au:pia` | YES (scoped) | Employee PII migration (DAT-003) |
| `/arckit-au:essential-eight` | YES (baseline) | Admin access hygiene |
| PSPF / ISM / DISP / SOCI-CIRMP | No | Private retailer; not critical infrastructure |

## 8. Acceptance Summary

Cutover acceptance requires: DAT-002 reconciliation signed; first STP Phase 2
pay event lodged successfully; first BAS prepared in-platform; G-5 evidenced —
no changes required in Projects 002/004/005 integrations.
