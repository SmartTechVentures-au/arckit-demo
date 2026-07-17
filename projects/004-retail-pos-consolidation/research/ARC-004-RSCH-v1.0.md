# Technology and Service Research: Retail POS Consolidation

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-004-RSCH-v1.0 |
| **Document Type** | Technology & Service Research Findings |
| **Project** | Retail POS Consolidation (Project 004) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT — FICTIONAL DEMONSTRATION |
| **Version** | 1.0 |
| **Created Date** | 2026-07-06 |
| **Owner** | Betty Rubble (GM Retail) |
| **Distribution** | Executive team, store managers, solution architecture advisor |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-06 | ArcKit AI | Initial market scan from `/arckit:research` | [PENDING] | [PENDING] |

---

## Research Scope

Cloud POS platforms suited to a 12-store Australian specialty bicycle chain
requiring: hub-integrated multi-store inventory, workshop/servicing job
management, serialised inventory, loyalty via external CRM, least-cost routing
terminal support, and offline resilience. Two incumbents (Retail Express,
Square) are competed, not defaulted. Pricing indicative; re-verify at
evaluation.

## Options Landscape

| Option | Class | Multi-store | Workshop/service | Serialised stock | LCR terminals (AU) | Indicative 3-yr TCO | Notes |
|---|---|---|---|---|---|---|---|
| **Lightspeed Retail (X-Series)** | Specialty retail cloud POS | STRONG | GOOD (service/work orders) | GOOD | Via supported acquirers / Lightspeed Payments AU | ~A$350–500k | Strong bike-shop pedigree (ex-Vend); large AU install base |
| **Retail Express (Maropost)** — incumbent ×7 | AU retail POS/ERP-lite | STRONG | MODERATE | GOOD | Via integrated acquirers | ~A$300–450k | Lowest retraining for the largest cohort; already profiled in ARC-001-RSCH |
| **Square for Retail** — incumbent ×3 | SMB cloud POS | MODERATE | WEAK (needs add-on) | MODERATE | Square routing policies to be verified against BR-006 | ~A$250–380k | Fast, cheap; workshop and hub-integration depth are the risks |
| **Shopify POS Pro** | Commerce-native POS | GOOD | WEAK (app-dependent) | MODERATE | Via Shopify Payments AU (verify LCR posture) | ~A$300–420k | Compelling *only if* Project 005 lands on Shopify — unified commerce play |
| **Hike / Kounta-class AU POS** | SMB POS | MODERATE | WEAK | WEAK | Varies | ~A$200–300k | Fails FR-005/FR-006 depth; culled |

## Analysis Against Requirements

- **Workshop management (BR-005/FR-005):** the sharpest differentiator.
  Lightspeed's work-order lineage is the strongest native story; Retail
  Express adequate; Square and Shopify depend on third-party apps — scored
  risk against T-2.
- **Hub-first integration (NFR-I-001):** all shortlisted platforms offer APIs;
  the evaluation must test *event granularity* (per-line stock movements,
  transfer states), not just "has an API".
- **Payments economics (BR-006):** platform-locked payments (Square, Shopify
  Payments) simplify operations but must demonstrate least-cost routing and
  compliant surcharge configuration; acquirer-choice platforms (Lightspeed,
  Retail Express) allow LCR negotiation with the bank.
- **Cohort retraining (T-1):** Retail Express minimises retraining for 7
  stores; Lightspeed spreads moderate retraining across all 12; Square
  minimises for only 3.
- **Portfolio coupling:** Shopify POS creates a hard dependency on the Project
  005 platform decision — evaluated jointly (see R-2).

## Shortlist & Recommendation for Evaluation

1. **Lightspeed Retail (X-Series)** — best specialty-bike + workshop fit.
2. **Retail Express (Maropost)** — incumbent value case; strongest continuity.
3. **Shopify POS Pro** — carried *conditionally*, evaluated jointly with
   Project 005; scored only if 005 shortlists Shopify.

Square retained as reference bid (price floor). Hike-class culled.

## Risks Identified

| ID | Risk | Mitigation |
|---|---|---|
| R-1 | Workshop capability oversold in demos | Scripted job lifecycle scenario incl. parts decrement from hub stock |
| R-2 | POS decision pre-empts or contradicts Project 005 platform decision | Joint 004/005 checkpoint before ADR approval (mirrors 002/003 pattern) |
| R-3 | June 2027 renewal used as leverage against us by incumbent | Month-to-month bridge negotiated now (ARC-000-PORT PR-4) |
| R-4 | Offline mode weaker than claimed | Pilot includes forced-offline trading test in each cohort store |
