# Project Requirements: CRM & Customer 360

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:requirements`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-REQ-v1.0 |
| **Document Type** | Business and Technical Requirements |
| **Project** | CRM & Customer 360 (Project 002) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT — FICTIONAL DEMONSTRATION |
| **Version** | 1.0 |
| **Created Date** | 2026-07-06 |
| **Last Modified** | 2026-07-06 |
| **Review Date** | 2026-08-06 |
| **Owner** | Wilma Flintstone (COO) — Operational Sponsor |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Executive team, channel leads, shortlisted vendors, solution architecture advisor |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-06 | ArcKit AI | Initial creation from `/arckit:requirements` | [PENDING] | [PENDING] |

## Document Purpose

Defines business and technical requirements for the CRM & Customer 360
programme. Drives vendor selection (ARC-002-RSCH shortlist), the single-vs-dual
platform decision (ARC-002-ADR-001), data migration planning, and acceptance
testing. Traces to ARC-002-STKE-v1.0, ARC-000-PRIN-v1.0, and ARC-000-PORT-v1.0.

---

## Executive Summary

Spoke & Rim operates dual-channel — ~250 wholesale trade accounts and ~38,000
retail/loyalty customers — with no CRM. This project establishes a single
customer master serving both channels, an auditable consent model, a loyalty
engine, and a customer-master API on which Projects 004 (POS) and 005
(E-Commerce) depend. Buy, not build (per ARC-000-PRIN); phased rollout,
wholesale first.

---

## 1. Business Requirements

| ID | Requirement | Priority | Traces to |
|----|-------------|----------|-----------|
| BR-001 | Establish one customer master covering wholesale accounts, retail customers, and loyalty members | MUST | G-4, O-4 |
| BR-002 | Migrate all ~250 trade accounts (contacts, terms, credit status, interaction notes) from spreadsheets | MUST | G-1 |
| BR-003 | Operate the Riders Club loyalty programme in-platform: enrolment, earn/burn, tiers, expiry | MUST | G-2 |
| BR-004 | All marketing communications sent against a recorded, auditable consent event | MUST | G-3 |
| BR-005 | Wholesale pipeline management: opportunities, quotes, activity tracking, account plans | MUST | G-1, O-1 |
| BR-006 | Buy a proven SaaS product; no custom CRM build | MUST | PRIN (buy-over-build) |
| BR-007 | Wholesale rollout before retail/loyalty rollout | SHOULD | T-1 |
| BR-008 | Total 3-year TCO within small-business envelope (≤ A$350k incl. implementation) | MUST | CEO constraint |
| BR-009 | Service/warranty case management for workshop and returns | SHOULD | SD-5 |

## 2. Functional Requirements

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-001 | B2B account hierarchy: parent trade account → stores → contacts | MUST |
| FR-002 | B2C individual profiles with loyalty membership object (points balance, tier, history) | MUST |
| FR-003 | Deduplication and merge with configurable match rules (email, phone, name+postcode); survivorship rules documented | MUST |
| FR-004 | Consent objects per channel (email, SMS) with timestamp, source, and proof; unsubscribe honoured within 5 business days (Spam Act s18) | MUST |
| FR-005 | Segmentation and automated journeys (welcome, win-back, service reminder) | MUST |
| FR-006 | Store-counter lookup view: identity, loyalty balance, purchase and service history — P90 < 10 seconds end-to-end | MUST |
| FR-007 | Quote-to-order handoff for wholesale: opportunity → order pushed to the inventory/order hub (Project 001) | MUST |
| FR-008 | Case management with SLA timers for warranty/service | SHOULD |
| FR-009 | Role-based views: wholesale reps see trade data; store staff see retail data only | MUST |
| FR-010 | Reporting: pipeline by rep, loyalty cohort behaviour, campaign attribution | SHOULD |

## 3. Non-Functional Requirements

| ID | Category | Requirement | Priority |
|----|----------|-------------|----------|
| NFR-P-001 | Performance | Customer lookup API P95 < 500 ms | MUST |
| NFR-P-002 | Usability | Counter capture flow ≤ 3 fields, ≤ 10 seconds | MUST |
| NFR-A-001 | Availability | 99.9% during retail trading hours (incl. weekends, AWST–AEST span) | MUST |
| NFR-S-001 | Security | SSO (Entra ID); MFA for all users; RBAC per FR-009 | MUST |
| NFR-S-002 | Security | Alignment with ASD Essential Eight Maturity Level 1 for admin practices | SHOULD |
| NFR-D-001 | Data residency | Customer PII stored in Australian regions, or documented adequacy assessment (APP 8 cross-border disclosure) | MUST |
| NFR-C-001 | Compliance | PIA completed and actions closed before migration go-live (`/arckit-au:pia`) | MUST |
| NFR-C-002 | Compliance | OAIC NDB response playbook in place at go-live (`/arckit-au:ndb-playbook`) | MUST |
| NFR-I-001 | Integrability | Documented REST/GraphQL API + webhooks for customer master consumption | MUST |

## 4. Integration Requirements

| ID | Integration | Direction | Notes |
|----|-------------|-----------|-------|
| INT-001 | Inventory/Order hub (Project 001) | Bidirectional | Orders and order history against customer records; hub-first principle (ARC-000-PORT §2) |
| INT-002 | POS (Project 004) | CRM → POS, POS → CRM | Loyalty identity, earn/burn events at the counter |
| INT-003 | E-Commerce (Project 005) | Bidirectional | Web accounts authenticate against / sync to the customer master |
| INT-004 | MYOB AccountRight (via hub) | CRM → hub → MYOB | Trade credit terms and account status; no direct MYOB integration |
| INT-005 | Mailchimp (decommission) | One-time export | Consent audit and selective import only; the list is not migrated wholesale |

## 5. Data Requirements

| ID | Requirement |
|----|-------------|
| DAT-001 | Data migration plan with consent audit: any Mailchimp contact without provable consent is excluded from marketing and flagged for re-permission |
| DAT-002 | Retention: inactive B2C profiles anonymised after 7 years of inactivity, subject to warranty-record retention needs (ACL) |
| DAT-003 | Data quality gates: migration rejects records failing mandatory-field and format validation; exceptions reported, not silently loaded |
| DAT-004 | Customer master ownership: CRM is the system of record for customer identity (ARC-000-PORT §2.3); downstream copies are read-only caches |

## 6. Out of Scope

- Field-service scheduling; ERP financials (Project 003); e-commerce checkout identity flows (defined in Project 005 against INT-003).

## 7. Australian Regulatory Overlay Applicability

| Overlay command | Applicable | Rationale |
|---|---|---|
| `/arckit-au:pia` (Privacy Act PIA) | **YES — mandatory** | 38k+ individual records consolidated and migrated |
| `/arckit-au:ndb-playbook` (OAIC NDB) | **YES** | Eligible data breach readiness at go-live |
| `/arckit-au:essential-eight` | YES (baseline) | Admin and SaaS-tenancy hygiene |
| `/arckit-au:ism`, PSPF, DISP | No | Not a government entity; no classified data |
| `/arckit-au:soci-cirmp` | No | Retail is not a SOCI critical infrastructure asset class |

## 8. Acceptance Summary

Go-live acceptance requires: G-1..G-6 measures instrumented; PIA actions
closed; consent model demonstrated end-to-end (capture → send → unsubscribe →
audit trail); counter lookup P90 < 10s witnessed in a pilot store.
