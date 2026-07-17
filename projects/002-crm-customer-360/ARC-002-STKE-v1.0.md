# Stakeholder Drivers & Goals Analysis: CRM & Customer 360

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:stakeholders`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-STKE-v1.0 |
| **Document Type** | Stakeholder Drivers & Goals Analysis |
| **Project** | CRM & Customer 360 (Project 002) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT — FICTIONAL DEMONSTRATION |
| **Version** | 1.0 |
| **Created Date** | 2026-07-06 |
| **Last Modified** | 2026-07-06 |
| **Review Cycle** | Quarterly |
| **Next Review Date** | 2026-10-06 |
| **Owner** | Wilma Flintstone, COO — Operational Sponsor |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Executive team, wholesale team, retail management, digital team, solution architecture advisor |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-06 | ArcKit AI | Initial creation from `/arckit:stakeholders` using the demo scenario brief | [PENDING] | [PENDING] |

---

## Executive Summary

### Purpose

Identifies stakeholders in the CRM & Customer 360 programme, their drivers,
the measurable goals those drivers become, and the outcomes that prove success.
Spoke & Rim currently has **no CRM**: ~250 wholesale trade accounts live in
spreadsheets managed by the wholesale team, ~38,000 loyalty members live in a
separate spreadsheet, and marketing runs off a disconnected Mailchimp list with
no auditable consent trail.

### Key Findings

The dual-channel nature of the business creates the central tension: wholesale
(Barney Rubble) needs an account-based B2B pipeline and trade credit visibility,
while retail (Betty Rubble) and digital (George Jetson) need a high-volume B2C
customer and loyalty engine. A single platform serving both is the strategic
preference but risks over-fitting one channel. Privacy exposure is the sharpest
driver: consolidating 38k customer records without a consent audit and PIA
would convert a spreadsheet problem into a Privacy Act problem.

### Stakeholder Alignment Score

**Overall Alignment**: MEDIUM — strong agreement that "no CRM" is untenable;
unresolved B2B-first vs B2C-first sequencing tension, and latent concern from
store managers about being asked to capture customer data at the counter.

---

## Stakeholder Identification

### Internal Stakeholders

| Stakeholder | Role | Influence | Interest | Engagement Strategy |
|-------------|------|-----------|----------|---------------------|
| Wilma Flintstone | COO — Operational Sponsor [STK-D1] | HIGH | HIGH | Manage Closely — owns process design and cross-channel priorities |
| Fred Flintstone | CEO — Investment authority [STK-D2] | HIGH | MEDIUM | Manage Closely — approves platform decision and spend |
| Barney Rubble | Head of Wholesale [STK-D3] | HIGH | HIGH | Manage Closely — B2B pipeline, trade account and credit views |
| Betty Rubble | GM Retail [STK-D4] | HIGH | HIGH | Manage Closely — loyalty programme, in-store capture, clienteling |
| George Jetson | Digital & E-Commerce Lead [STK-D5] | MEDIUM | HIGH | Involve — marketing automation, consent, e-commerce identity (dep. Project 005) |
| Store managers ×12 | Retail operations [STK-D6] | LOW | MEDIUM | Keep Informed — counter workflows must stay under 10 seconds |
| Order & Supply Chain team | Operations [STK-D7] | LOW | MEDIUM | Keep Informed — order history views, service cases |

### External Stakeholders

| Stakeholder | Organisation | Relationship | Influence | Interest |
|-------------|--------------|--------------|-----------|----------|
| Velma Dinkley | Solution architecture advisory [STK-D8] | Trusted advisor | MEDIUM-HIGH | HIGH |
| Wholesale trade customers ×250 | Independent bike shops | Beneficiary | LOW | HIGH |
| Loyalty members ×38,000 | Riders Club | Data subjects / beneficiaries | LOW | MEDIUM |
| CRM vendor (TBD) | Shortlist per ARC-002-RSCH | Supplier | MEDIUM | HIGH |
| OAIC | Regulator | Privacy Act oversight | LOW (until incident) | LOW |

---

## Drivers → Goals → Outcomes

### Stakeholder Drivers

| ID | Driver | Stakeholder(s) | Type |
|----|--------|----------------|------|
| SD-1 | Wholesale account knowledge is trapped in one team's spreadsheets — key-person risk on 250 trade relationships | Barney Rubble, CEO | Risk |
| SD-2 | Loyalty programme cannot grow: no segmentation, no automation, manual point adjustments | Betty Rubble | Growth |
| SD-3 | Marketing consent is unauditable — Spam Act and Privacy Act exposure on the 38k-member list | George Jetson, COO | Compliance |
| SD-4 | No single customer view: a trade customer who also shops retail is two unrelated records | COO, Digital | Efficiency |
| SD-5 | Store staff have no visibility of customer history — servicing and warranty conversations start cold | Store managers, GM Retail | Experience |
| SD-6 | Every future project (004 POS loyalty, 005 e-commerce accounts) needs a customer master to build on | Advisor, COO | Architecture |

### Goals (measurable)

| ID | Goal | Traces to | Measure |
|----|------|-----------|---------|
| G-1 | All 250 trade accounts migrated with contacts, terms, and interaction history | SD-1 | 100% accounts in CRM; zero spreadsheet fallback after 60 days |
| G-2 | Loyalty operated in-platform with automated earn/burn | SD-2 | Manual point adjustments < 5/month (from ~200) |
| G-3 | Auditable consent for all marketing sends | SD-3 | 100% sends against a recorded consent event; Spam Act complaint rate ~0 |
| G-4 | Single customer identity across wholesale, retail, online | SD-4, SD-6 | Duplicate rate < 2% post-merge; match rules documented |
| G-5 | Customer context at the counter in < 10 seconds | SD-5 | Store lookup P90 < 10s; adoption > 70% of service interactions |
| G-6 | CRM exposes a customer-master API consumed by Projects 004 & 005 | SD-6 | Both projects integrate without a parallel customer store |

### Outcomes

| ID | Outcome | Proves |
|----|---------|--------|
| O-1 | Wholesale relationships survive staff turnover; pipeline reportable to the board | G-1 |
| O-2 | Loyalty drives measurable repeat purchase (baseline then +10% repeat rate in 12 months) | G-2, G-5 |
| O-3 | Privacy/marketing compliance demonstrable to OAIC standard (PIA complete, NDB playbook in place) | G-3, G-4 |
| O-4 | The portfolio's "customer truth" decision (ARC-000-PORT §2.3) is realised | G-4, G-6 |

---

## Conflicts & Tensions

| ID | Tension | Between | Resolution approach |
|----|---------|---------|---------------------|
| T-1 | B2B-first vs B2C-first rollout sequencing | Wholesale vs Retail | Phase by risk: wholesale first (smaller, higher key-person risk), loyalty second — decided in ADR-002-001 |
| T-2 | Single platform vs best-of-breed per channel | Advisor/COO vs channel leads | Evaluated in ARC-002-RSCH; decision in ADR-002-001 |
| T-3 | Counter data capture vs store throughput | GM Retail vs store managers | Hard NFR: capture flow < 10s or it doesn't ship (NFR-P-002) |

## Regulatory Note (arckit-au overlay)

Privacy Act 1988 / APPs and the Spam Act 2003 apply in full. A **Privacy Impact
Assessment** (`/arckit-au:pia`) is mandatory before customer data migration.
PSPF, ISM classification, DISP, and SOCI/CIRMP are **not applicable** (private
retailer, no critical infrastructure asset class).
