# Stakeholder Drivers & Goals Analysis: Retail POS Consolidation

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:stakeholders`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-004-STKE-v1.0 |
| **Document Type** | Stakeholder Drivers & Goals Analysis |
| **Project** | Retail POS Consolidation (Project 004) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT — FICTIONAL DEMONSTRATION |
| **Version** | 1.0 |
| **Created Date** | 2026-07-06 |
| **Review Cycle** | Quarterly |
| **Owner** | Priya Nair, GM Retail — Project Sponsor |
| **Distribution** | Executive team, store managers, digital team, solution architecture advisor |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-06 | ArcKit AI | Initial creation from `/arckit:stakeholders` | [PENDING] | [PENDING] |

---

## Executive Summary

### Purpose

Identifies stakeholders and drivers for consolidating the 12-store Spoke & Rim
retail network from **three POS estates** (7× Retail Express legacy, 3× Square
from acquisition A, 2× unintegrated cash register + standalone EFTPOS from
acquisition B) onto **one** POS platform integrated with the inventory/order
hub (Project 001) and the CRM customer master (Project 002).

### Key Findings

Store managers are simultaneously the biggest beneficiaries and the biggest
delivery risk: three cohorts each defend their current muscle memory. The
hardest deadline in the portfolio sits here — the Retail Express contract
renews **June 2027** (ARC-000-PORT PR-4). Payments economics is a live CEO
driver: least-cost routing on eftpos and compliant card surcharging materially
affect margin at retail volumes. Workshop/servicing is the differentiating
workflow — a bike shop POS without job/service management fails the floor.

### Stakeholder Alignment Score

**Overall Alignment**: MEDIUM-HIGH — everyone wants one system; contention is
*which* cohort retrains, and whether workshop management lives in POS or a
separate tool.

---

## Stakeholder Identification

| Stakeholder | Role | Influence | Interest | Engagement Strategy |
|-------------|------|-----------|----------|---------------------|
| Priya Nair | GM Retail — Sponsor [STK-F1] | HIGH | HIGH | Manage Closely — owns rollout, store P&L |
| Nathan Dyke | CEO [STK-F2] | HIGH | MEDIUM | Manage Closely — payments economics, contract timing, spend |
| Kirralee Dyke | COO [STK-F3] | HIGH | MEDIUM | Manage Closely — hub integration integrity |
| Store managers ×12 (3 cohorts) [STK-F4] | Operations | MEDIUM | HIGH | Involve — pilot stores drawn from each cohort |
| Workshop leads (per store) [STK-F5] | Servicing | LOW | HIGH | Involve — job management workflows are make-or-break |
| Sam Whitford | Digital Lead [STK-F6] | MEDIUM | MEDIUM | Consult — click-and-collect, endless-aisle with Project 005 |
| Grace Liu | Finance [STK-F7] | MEDIUM | MEDIUM | Consult — reconciliation, surcharge configuration |
| Chris McKelt | Architecture advisor [STK-F8] | MEDIUM-HIGH | HIGH | Involve — hub-first design gate |
| Payments acquirer(s) | Banks / PSPs [STK-F9] | MEDIUM | MEDIUM | Negotiate — least-cost routing, terminal fleet |
| Customers (walk-in + loyalty) | Public [STK-F10] | LOW | MEDIUM | Beneficiary — faster checkout, cross-store returns |

---

## Drivers → Goals → Outcomes

### Drivers

| ID | Driver | Stakeholder | Type |
|----|--------|-------------|------|
| SD-1 | Three POS estates: no chain-wide stock view, no cross-store returns or transfers, triple training burden | GM Retail | Efficiency |
| SD-2 | Two stores fully unintegrated — sales keyed into MYOB weekly; shrinkage invisible | GM Retail, COO | Risk |
| SD-3 | Retail Express renewal Jun 2027 forces a decision window | CEO | Timing |
| SD-4 | Card acceptance costs: no least-cost routing; surcharging inconsistent across stores (RBA rules) | CEO, Finance | Cost/Compliance |
| SD-5 | Loyalty cannot run at the counter without CRM-integrated POS | GM Retail, Digital | Growth |
| SD-6 | Workshop jobs managed on paper cards in 9 of 12 stores | Workshop leads | Efficiency |
| SD-7 | PCI DSS posture unknown across the acquired estates | COO, Advisor | Compliance |

### Goals

| ID | Goal | Traces to | Measure |
|----|------|-----------|---------|
| G-1 | One POS platform live in all 12 stores before Jun 2027 | SD-1, SD-3 | Rollout complete; legacy contracts exited |
| G-2 | Real-time hub-integrated stock: chain-wide availability, transfers, cross-store returns | SD-1, SD-2 | Stock lookup any-store; zero weekly re-keying |
| G-3 | Least-cost routing enabled; compliant, consistent surcharging chain-wide | SD-4 | Blended card cost ↓ ≥ 15 bps; surcharge config audit clean |
| G-4 | Loyalty earn/burn at every counter against the CRM master | SD-5 | INT to Project 002 live; > 40% of retail transactions identified |
| G-5 | Workshop job management in-platform in all stores | SD-6 | Paper job cards retired |
| G-6 | PCI DSS SAQ scope minimised (P2PE/validated terminals); attestation current | SD-7 | SAQ completed; no cardholder data in POS environment |

### Outcomes

| ID | Outcome |
|----|---------|
| O-1 | Retail operates as one chain, not three acquisitions (G-1, G-2) |
| O-2 | Payments margin recovered and compliant (G-3, G-6) |
| O-3 | Loyalty becomes a counter-native behaviour feeding Project 002 outcomes (G-4) |
| O-4 | Servicing revenue visible and schedulable chain-wide (G-5) |

---

## Conflicts & Tensions

| ID | Tension | Resolution approach |
|----|---------|---------------------|
| T-1 | Which cohort's incumbent wins (Retail Express vs Square) vs a fresh platform | Open evaluation (ARC-004-RSCH); pilot includes one store from each cohort |
| T-2 | Workshop management: in-POS vs specialist tool | Scored requirement (FR-008); in-POS preferred unless scoring < 60% |
| T-3 | Rollout speed vs Christmas trading freeze | No store cutovers Nov 15 – Jan 15; sequencing in ARC-000-PORT phasing |

## Regulatory Note (arckit-au overlay)

PCI DSS v4.x (via acquirer obligations), RBA surcharging standards, and
Australian Consumer Law (receipts, refunds, warranties) are core. Privacy Act
applies at the loyalty boundary (handled under Project 002 PIA scope
extension). PSPF/ISM/DISP/SOCI: **not applicable**.
