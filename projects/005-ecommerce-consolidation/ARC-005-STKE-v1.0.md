# Stakeholder Drivers & Goals Analysis: E-Commerce Consolidation

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:stakeholders`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-005-STKE-v1.0 |
| **Document Type** | Stakeholder Drivers & Goals Analysis |
| **Project** | E-Commerce Consolidation (Project 005) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT — FICTIONAL DEMONSTRATION |
| **Version** | 1.0 |
| **Created Date** | 2026-07-06 |
| **Review Cycle** | Quarterly |
| **Owner** | Sam Whitford, Digital & E-Commerce Lead — Project Sponsor |
| **Distribution** | Executive team, wholesale team, retail management, solution architecture advisor |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-06 | ArcKit AI | Initial creation from `/arckit:stakeholders` | [PENDING] | [PENDING] |

---

## Executive Summary

### Purpose

Identifies stakeholders and drivers for consolidating six web properties —
one self-managed Magento (Adobe Commerce) B2B trade portal and five Shopify
B2C brand storefronts — into a coherent commerce architecture: consolidated
catalogue, hub-sourced availability, CRM-based identity, and a maintainable
platform footprint.

### Key Findings

The core tension is **brand strategy vs operational sanity**: the five brand
storefronts exist because distributed brands (iGPSport, CYCPLUS, Farsports…)
want distinct presences, yet each duplicate catalogue multiplies content work
and pricing errors. Wholesale (Tom Barker) is protective of the Magento trade
portal — it works, and B2B customers hate change — but it is a self-managed
stack carrying security patching burden and hosting cost. The decision shape:
one platform with multi-storefront capability vs a deliberate two-platform
split (B2B / B2C), each hub-integrated.

### Stakeholder Alignment Score

**Overall Alignment**: MEDIUM — universal agreement the 6-property estate is
unsustainable; genuine disagreement on whether B2B and B2C belong on one
platform, and on how many B2C storefronts survive.

---

## Stakeholder Identification

| Stakeholder | Role | Influence | Interest | Engagement Strategy |
|-------------|------|-----------|----------|---------------------|
| Sam Whitford | Digital Lead — Sponsor [STK-G1] | HIGH | HIGH | Manage Closely — owns platform, content ops, roadmap |
| Tom Barker | Head of Wholesale [STK-G2] | HIGH | HIGH | Manage Closely — trade portal continuity, pricing tiers |
| Nathan Dyke | CEO [STK-G3] | HIGH | MEDIUM | Manage Closely — brand strategy call on storefront count |
| Kirralee Dyke | COO [STK-G4] | HIGH | MEDIUM | Manage Closely — hub integration, fulfilment promises |
| Priya Nair | GM Retail [STK-G5] | MEDIUM | MEDIUM | Consult — click-and-collect, ship-from-store (with 004) |
| Brand principals (suppliers) [STK-G6] | iGPSport, CYCPLUS, etc. | MEDIUM | HIGH | Consult — brand presentation expectations, MAP pricing |
| Trade customers ×250 [STK-G7] | Bike shops | Beneficiary | HIGH | Involve — portal UX testing; change communication |
| B2C customers [STK-G8] | Public | Beneficiary | MEDIUM | Research — analytics, UX testing |
| Chris McKelt | Architecture advisor [STK-G9] | MEDIUM-HIGH | HIGH | Involve — platform decision, hub-first gate |

---

## Drivers → Goals → Outcomes

### Drivers

| ID | Driver | Stakeholder | Type |
|----|--------|-------------|------|
| SD-1 | Six catalogues maintained by hand: duplicated content, inconsistent pricing, MAP breaches risk brand relationships | Digital, Brands | Efficiency/Risk |
| SD-2 | Self-managed Magento: patching burden, security exposure, hosting cost, scarce skills | Digital, COO | Risk/Cost |
| SD-3 | Availability shown online diverges from hub truth → oversell (the Project 001 problem re-emerging at the web tier) | COO | Risk |
| SD-4 | No unified customer identity across storefronts; guest-checkout dominance starves CRM (Project 002) | Digital | Growth |
| SD-5 | Trade customers want retail-grade UX (search, backorder visibility, invoices online) | Wholesale | Experience |
| SD-6 | Click-and-collect / ship-from-store impossible without web↔hub↔POS choreography | GM Retail, Digital | Growth |
| SD-7 | Accessibility and consumer-law hygiene inconsistent across 6 properties | Digital | Compliance |

### Goals

| ID | Goal | Traces to | Measure |
|----|------|-----------|---------|
| G-1 | One product information source feeding all storefronts (PIM-lite in the hub or platform) | SD-1 | Content edited once; zero divergent prices in monthly audit |
| G-2 | Magento self-managed stack retired or replatformed to SaaS/PaaS | SD-2 | No self-patched commerce infrastructure remains |
| G-3 | All storefronts display hub-sourced availability; zero web oversell | SD-3 | Oversell incidents from web: 0/month |
| G-4 | Storefront count rationalised by CEO decision: target ≤ 3 B2C properties + 1 B2B | SD-1, SD-4 | Decision recorded; migrations complete with SEO preserved |
| G-5 | Customer accounts authenticate against the CRM identity (Project 002) | SD-4 | Logged-in checkout share > 45% in 12 months |
| G-6 | Trade portal parity-plus: tiered pricing, credit visibility, invoices, backorder ETAs | SD-5 | Trade NPS uplift; portal order share ≥ 85% of wholesale orders |
| G-7 | Click-and-collect live in all 12 stores (with Project 004) | SD-6 | C&C share of online orders ≥ 15% |

### Outcomes

| ID | Outcome |
|----|---------|
| O-1 | Content and pricing operations scale sub-linearly with storefront count (G-1, G-4) |
| O-2 | Security and platform risk transferred to SaaS vendors (G-2) |
| O-3 | The web tier becomes a well-behaved spoke of the hub — inventory truth holds end-to-end (G-3, G-7) |
| O-4 | Wholesale digital share grows without B2B disruption (G-6) |

---

## Conflicts & Tensions

| ID | Tension | Resolution approach |
|----|---------|---------------------|
| T-1 | Brand storefront count: brands want 5; ops wants 1 | CEO decision with brand-principal consultation; target ≤ 3 (G-4) |
| T-2 | One platform (B2B+B2C) vs two-platform split | Decided in ADR-005-001 after ARC-005-RSCH |
| T-3 | Trade portal change resistance vs Magento retirement | Parity-plus requirement (G-6); phased trade migration with pilot accounts |
| T-4 | Coupling with Project 004 (Shopify POS scenario) | Joint 004/005 checkpoint (mirrors ARC-004-RSCH R-2) |

## Regulatory Note (arckit-au overlay)

Australian Consumer Law (pricing display, refunds), Privacy Act/APPs and Spam
Act at the account/marketing boundary (Project 002 PIA extension), PCI DSS at
checkout (hosted fields/redirect preferred), WCAG 2.2 AA accessibility target
(SD-7). PSPF/ISM/DISP/SOCI: **not applicable**.
