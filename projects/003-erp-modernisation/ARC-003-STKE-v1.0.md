# Stakeholder Drivers & Goals Analysis: ERP Modernisation

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:stakeholders`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-003-STKE-v1.0 |
| **Document Type** | Stakeholder Drivers & Goals Analysis |
| **Project** | ERP Modernisation (Project 003) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT — FICTIONAL DEMONSTRATION |
| **Version** | 1.0 |
| **Created Date** | 2026-07-06 |
| **Review Cycle** | Quarterly |
| **Owner** | Grace Liu, Finance Manager — Project Sponsor |
| **Distribution** | Executive team, finance team, Order & Supply Chain team, solution architecture advisor |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-06 | ArcKit AI | Initial creation from `/arckit:stakeholders` | [PENDING] | [PENDING] |

---

## Executive Summary

### Purpose

Identifies stakeholders and drivers for replacing/uplifting MYOB AccountRight
as the financial system of record. ARC-001-ADR-001 deliberately **retained**
MYOB during the inventory uplift; this project defines the controlled
supersession path. The scenario stressors: multi-entity consolidation (parent +
retail entity), multi-state payroll for ~160 staff (STP Phase 2), landed-cost
accounting on imported componentry, Peppol e-invoicing for trade customers, and
month-end close currently taking 12 business days.

### Key Findings

Finance (Grace Liu) is the driving stakeholder — MYOB constraints land on her
team monthly. The CEO's driver is the opposite risk: an ERP migration is the
single most disruptive project in the portfolio, and starting it too early
would destabilise Projects 001–005 integrations. The COO's condition is that
the hub-first pattern makes ERP cutover a *contained* change (re-point one
integration), which the portfolio roadmap encodes as a hard gate (ARC-000-PORT
PR-5). Alignment is HIGH on destination, MEDIUM on timing.

---

## Stakeholder Identification

| Stakeholder | Role | Influence | Interest | Engagement Strategy |
|-------------|------|-----------|----------|---------------------|
| Grace Liu | Finance Manager — Sponsor [STK-E1] | HIGH | HIGH | Manage Closely — owns close, payroll, compliance calendar |
| Nathan Dyke | CEO [STK-E2] | HIGH | HIGH | Manage Closely — sequencing, investment, risk appetite |
| Kirralee Dyke | COO [STK-E3] | HIGH | MEDIUM | Manage Closely — operational continuity conditions |
| Payroll officer + AP/AR (3 staff) | Finance ops [STK-E4] | LOW | HIGH | Involve — process design, UAT |
| Order & Supply Chain team | Operations [STK-E5] | MEDIUM | MEDIUM | Keep Informed — purchasing/landed cost workflows |
| Priya Nair / Tom Barker / Sam Whitford | Channel leads [STK-E6] | MEDIUM | LOW | Keep Informed — downstream reporting consumers |
| Chris McKelt | Architecture advisor [STK-E7] | MEDIUM-HIGH | HIGH | Involve — supersession design of ADR-001 |
| External accountant / tax agent | Advisory firm [STK-E8] | MEDIUM | MEDIUM | Consult — chart of accounts, tax config sign-off |
| ATO | Regulator [STK-E9] | LOW (until non-compliance) | LOW | Comply — STP Phase 2, BAS, Peppol readiness |

---

## Drivers → Goals → Outcomes

### Drivers

| ID | Driver | Stakeholder | Type |
|----|--------|-------------|------|
| SD-1 | Month-end close takes 12 business days across two entities with manual consolidation | Finance | Efficiency |
| SD-2 | Multi-state payroll (~160 staff, WA/VIC/NSW awards, STP Phase 2) run partly outside MYOB | Finance | Compliance |
| SD-3 | Landed-cost accounting for imported components handled in spreadsheets — margin figures unreliable | Finance, COO | Accuracy |
| SD-4 | Trade customers increasingly request Peppol e-invoicing; MYOB setup is limited | Finance, Wholesale | Growth/Compliance |
| SD-5 | ERP migration risk — worst possible time is mid-portfolio | CEO, COO | Risk |
| SD-6 | Reporting: no consolidated channel P&L (wholesale vs retail vs online) | CEO | Insight |

### Goals

| ID | Goal | Traces to | Measure |
|----|------|-----------|---------|
| G-1 | Month-end close ≤ 5 business days, consolidated | SD-1 | Close calendar evidence, 3 consecutive months |
| G-2 | Payroll fully in-platform, STP Phase 2 compliant, all states | SD-2 | Zero out-of-system payroll runs; ATO lodgement success 100% |
| G-3 | Landed costs captured at receipt; true margin by SKU/channel | SD-3, SD-6 | Spreadsheet landed-cost model retired |
| G-4 | Peppol e-invoicing live for trade customers | SD-4 | ≥ 50% of trade invoices via Peppol in 12 months |
| G-5 | Cutover executed as a contained change: only the hub→ERP integration re-pointed | SD-5 | Zero rework in Projects 002/004/005 integrations at cutover |
| G-6 | Channel P&L reported monthly without manual assembly | SD-6 | Board pack automated |

### Outcomes

| ID | Outcome |
|----|---------|
| O-1 | Finance operates as a 5-day-close, compliance-clean function (G-1, G-2, G-4) |
| O-2 | Pricing and range decisions made on true landed margin (G-3, G-6) |
| O-3 | ARC-001-ADR-001 superseded in a governed, dated, traceable way (G-5) |

---

## Conflicts & Tensions

| ID | Tension | Resolution approach |
|----|---------|---------------------|
| T-1 | Finance wants FY27 start; CEO wants post-004/005 go-live | Hard gate adopted (ARC-000-PORT PR-5): implementation starts FY27 Q4, cutover FY28 |
| T-2 | "Upgrade within MYOB family" vs "open evaluation" | ARC-003-RSCH evaluates MYOB Acumatica alongside NetSuite, Dynamics BC, Odoo — no incumbency default |
| T-3 | Payroll in-ERP vs best-of-breed payroll (AU award complexity) | Evaluated as a scored criterion; decision recorded in ADR-003-001 §7 |

## Regulatory Note (arckit-au overlay)

ATO obligations (STP Phase 2, BAS/GST, Peppol/e-invoicing) are core
requirements, not overlays. Essential Eight baseline applies to ERP admin
access. PSPF/ISM/DISP/SOCI: **not applicable**.
