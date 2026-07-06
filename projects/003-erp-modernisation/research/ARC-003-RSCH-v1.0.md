# Technology and Service Research: ERP Modernisation

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-003-RSCH-v1.0 |
| **Document Type** | Technology & Service Research Findings |
| **Project** | ERP Modernisation (Project 003) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT — FICTIONAL DEMONSTRATION |
| **Version** | 1.0 |
| **Created Date** | 2026-07-06 |
| **Owner** | Grace Liu (Finance Manager) |
| **Distribution** | Executive team, finance team, solution architecture advisor |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-06 | ArcKit AI | Initial market scan from `/arckit:research` | [PENDING] | [PENDING] |

---

## Research Scope

Cloud ERP products for an Australian dual-channel SMB (~A$48M, 2 entities,
~160 staff) with strong AU tax/payroll compliance, landed costs, Peppol, and a
clean hub-subscriber integration posture. Builds on the Project 001 landscape
work (ARC-001-RSCH v1.2), which already profiled MYOB Acumatica, Odoo, and
ERPNext. Build-vs-buy: **BUY** (BR-008). Pricing indicative; re-verify at
evaluation.

## Options Landscape

| Option | Class | AU payroll (STP2) | Landed cost | Peppol | Indicative 3-yr TCO | Notes |
|---|---|---|---|---|---|---|
| **MYOB Acumatica** | Mid-market cloud ERP | Via MYOB payroll integration | STRONG | Supported | ~A$450–700k | Lowest-friction migration path from AccountRight family; AU-centric partner network |
| **Oracle NetSuite** | Mid-market cloud ERP | Via partner (e.g. Infinet-class localisation) | STRONG | Via add-on | ~A$600–950k | Strong multi-entity + channel P&L; TCO pressure on BR-009 |
| **Microsoft Dynamics 365 Business Central** | Mid-market cloud ERP | Via certified AU payroll ISVs | STRONG | Native | ~A$500–800k | Strong if CRM (002) lands on Dynamics; big AU partner base |
| **Odoo Enterprise** | Open-core ERP | AU localisation improving; payroll typically paired best-of-breed | GOOD | Via module | ~A$300–500k | Value leader; partner quality is the deciding risk (echoes ARC-001-RSCH findings) |
| **ERPNext** | Open-source ERP | Weak AU payroll story | MODERATE | Community | ~A$200–350k | Fails BR-003 without heavy pairing; carried as reference only |
| **Best-of-breed payroll (Employment Hero / KeyPay-class) + any ERP** | Pattern, not product | STRONG | n/a | n/a | +A$60–120k | Resolves award-interpretation risk for any ERP; scored in ADR-003-001 §7 |

## Analysis Against Requirements

- **Multi-entity + channel P&L (BR-001, BR-006):** NetSuite and Business
  Central strongest natively; MYOB Acumatica strong; Odoo adequate with
  analytic accounts.
- **Payroll (BR-003):** the single highest-risk requirement. AU award
  interpretation is where mid-market ERP implementations fail; the best-of-breed
  payroll pattern materially de-risks every option and is likely the
  recommendation regardless of ERP choice.
- **Hub-subscriber posture (FR-005, INT-001):** all shortlisted options can
  consume hub events; the discipline is contractual (versioned event schemas,
  NFR-I-001) rather than product-dependent.
- **TCO (BR-009):** NetSuite likely breaches the envelope at full scope; MYOB
  Acumatica and Business Central fit; Odoo fits with margin but shifts risk to
  partner capability.

## Shortlist & Recommendation for Evaluation

1. **MYOB Acumatica** — continuity path; strongest AU-native compliance story.
2. **Dynamics 365 Business Central** — strongest portfolio synergy if Project
   002 selects Dynamics; joint checkpoint required (mirrors ARC-002-RSCH R-3).
3. **Odoo Enterprise** — value benchmark with a mandated partner-capability
   deep-dive (reference checks with AU retail/wholesale implementations).

NetSuite carried as reference bid. ERPNext excluded (BR-003). Best-of-breed
payroll evaluated as an orthogonal criterion for all three.

## Risks Identified

| ID | Risk | Mitigation |
|---|---|---|
| R-1 | Payroll award misconfiguration → underpayment exposure | Best-of-breed payroll pattern; parallel pay runs ≥ 2 cycles before cutover |
| R-2 | ERP selected before CRM decision fixes the Microsoft-stack question | Joint 002/003 architecture checkpoint before either ADR is approved |
| R-3 | Implementation partner under-scopes migration reconciliation | DAT-002 evidence pack contractualised in the SOW |
| R-4 | Scope creep: ERP team attempts to re-master inventory | Design-review gate enforcing FR-005 (hub remains master) |
