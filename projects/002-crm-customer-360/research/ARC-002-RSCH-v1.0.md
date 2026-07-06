# Technology and Service Research: CRM & Customer 360

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-RSCH-v1.0 |
| **Document Type** | Technology & Service Research Findings |
| **Project** | CRM & Customer 360 (Project 002) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT — FICTIONAL DEMONSTRATION |
| **Version** | 1.0 |
| **Created Date** | 2026-07-06 |
| **Owner** | Kirralee Dyke (COO) |
| **Distribution** | Executive team, channel leads, solution architecture advisor |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-06 | ArcKit AI | Initial market scan from `/arckit:research` | [PENDING] | [PENDING] |

---

## Research Scope

Commercial SaaS CRM products able to serve **both** a ~250-account B2B pipeline
and a ~38,000-member B2C loyalty base for an Australian SMB, within a 3-year
TCO ≤ A$350k (BR-008), with Australian data residency options (NFR-D-001).
Build-vs-buy is settled: **BUY** (BR-006). Note: vendor pricing and packaging
below reflect the demonstration date and must be re-verified at evaluation.

## Options Landscape

| Option | Class | B2B fit | B2C/loyalty fit | AU residency | Indicative 3-yr TCO | Notes |
|---|---|---|---|---|---|---|
| **HubSpot (Sales + Marketing Hub Pro)** | Suite | GOOD | GOOD (loyalty via app/partner) | Contractual, region-dependent | ~A$180–280k | Fast to value; loyalty needs an add-on; consent tooling strong |
| **Salesforce (Sales Cloud + Marketing Cloud Growth)** | Enterprise suite | STRONG | STRONG | Hyperforce AU | ~A$300–450k | Best capability ceiling; TCO and admin overhead pressure BR-008 |
| **Microsoft Dynamics 365 (Sales + Customer Insights)** | Enterprise suite | STRONG | GOOD | AU regions | ~A$250–380k | Natural fit with Entra ID SSO; heavier implementation |
| **Zoho CRM Plus** | Suite | GOOD | MODERATE | AU DC available | ~A$90–150k | Strong value; partner depth in AU thinner; loyalty via Zoho Thrive |
| **Klaviyo + lightweight B2B CRM (dual-stack)** | Best-of-breed pair | MODERATE | STRONG | US-centric (assess APP 8) | ~A$150–220k | Excellent retail marketing; violates single-master unless CRM is clearly master |
| **Retail-native loyalty (e.g. Marsello) on top of POS/e-com** | Point solution | POOR | GOOD | Varies | ~A$60–100k | Solves loyalty only; defers the customer-master problem — fails BR-001 |

## Analysis Against Requirements

- **Single customer master (BR-001, G-4):** suites (HubSpot, Salesforce,
  Dynamics, Zoho) satisfy directly. Dual-stack options satisfy only with a
  clearly designated master and disciplined sync — added integration risk that
  contradicts the portfolio's hub-and-master pattern (ARC-000-PORT §2).
- **Counter lookup < 10s (FR-006):** all suites achievable via embedded POS
  lookup (Project 004 integration) rather than native CRM UI at the counter.
- **Consent audit (BR-004, FR-004):** HubSpot and Salesforce strongest
  out-of-box; Zoho adequate; dual-stack splits the consent record — a
  compliance smell.
- **TCO (BR-008):** Salesforce full-suite likely breaches the envelope;
  Salesforce *Starter/Pro Suite* tiers could fit but limit Marketing Cloud
  capability. Zoho and HubSpot fit comfortably.

## Shortlist & Recommendation for Evaluation

1. **HubSpot** — best balance of B2B pipeline + B2C marketing + consent within TCO.
2. **Microsoft Dynamics 365** — strongest if the ERP decision (Project 003)
   lands on the Microsoft stack; evaluate jointly with ARC-003-RSCH.
3. **Zoho CRM Plus** — value benchmark; forces the incumbents to justify price.

Salesforce carried as reference bid only. Point-solution loyalty rejected
(fails BR-001). Dual-stack rejected unless evaluation shows suites cannot meet
loyalty needs (revisit trigger documented in ADR-002-001).

## Risks Identified

| ID | Risk | Mitigation |
|---|---|---|
| R-1 | Loyalty capability gaps in suite CRMs force a bolt-on later | Loyalty scenarios scripted into evaluation demos |
| R-2 | APP 8 exposure if marketing data processed offshore | Residency and sub-processor review per vendor before scoring |
| R-3 | Dynamics choice pre-empts the ERP decision informally | Joint checkpoint with Project 003 before ADR approval |
