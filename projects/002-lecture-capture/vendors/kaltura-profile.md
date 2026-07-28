# Vendor Profile: Kaltura

> **Template Origin**: Official | **ArcKit Version**: 6.7.2 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-VEND-kaltura-v1.0 |
| **Document Type** | Vendor Profile |
| **Project** | Lecture Capture Platform Consolidation (Project 002) |
| **Classification** | OFFICIAL-SENSITIVE |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-27 |
| **Last Researched** | 2026-07-27 |
| **Review Date** | 2026-08-26 |
| **Owner** | Dr. Benny Moog, Director Learning Technologies |
| **Confidence** | **MEDIUM** — 7 sourced data points; product capability researched at lower depth than Echo360 / Panopto / Microsoft |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Project Team, Procurement, Digital & IT |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-27 | ArcKit AI | Initial creation from `/arckit:research` | PENDING | PENDING |

---

## Overview

Kaltura is a publicly listed (NASDAQ: KLTR) video platform vendor headquartered in New York [K-C2], operating across enterprise, education and technology markets. It is the broadest of the candidates in scope — a general video platform with open APIs and custom workflows that extends well beyond lecture capture — and it maintains a distinct Lecture Capture product line.

**Kaltura is included in this profile for completeness of the market view, not because the evidence favours it.** The single most directly relevant Australian data point is a university *leaving* Kaltura: the University of Queensland decommissioned Kaltura and transitioned to Echo360, switching Kaltura to read-only on 3 June 2024 and decommissioning it on 31 December 2024 [K-C4].

## Products & Services

- **Kaltura Video Portal / MediaSpace** — video content management
- **Kaltura Lecture Capture** — actively maintained; a release was issued **14 December 2025** addressing Microsoft PowerPoint and Windows 11 issues [K-C5]
- **Kaltura Capture** — desktop recorder; version **5.2.3 released 4 December 2025** [K-C6]
- **KAF (Kaltura Application Framework)** — LMS integration layer
- **REACH** — captioning and enrichment services (*not verified in this research*)
- **Agentic AI suite** — Agentic Avatars, AI Genie, Content Lab, REACH AI enrichment [K-C1]

## Pricing Model

**Not published.** No list pricing located. Quote-based, consistent with the segment.

Kaltura holds a US MEEC consortium master agreement under RFP #0004-2023, term 1 July 2023 – 30 June 2029, multi-award; pricing not published [K-C2].

**Financial position (relevant to vendor viability, R-012)** — from published FY2025 results [K-C3]:

| Metric | FY2025 | Movement |
|---|---|---|
| Total revenue | US$180.9m | +1% YoY |
| Subscription revenue | US$171.9m | +3% |
| Enterprise, Education & Technology segment | US$134.4m | +4% |
| Annualised Recurring Revenue | US$168.2m | **−3%** |
| Net Dollar Retention | **97%** | — |
| Adjusted EBITDA | US$18.6m | up from US$7.3m |
| 2026 guidance | US$181.2–184.2m | — |

> **Interpretation, stated carefully.** Profitability improved materially. But ARR declined 3% and net dollar retention of 97% means the existing customer base is contracting slightly rather than expanding. This is a **neutral, structural input to vendor-viability scoring** — a supplier under revenue pressure. It is not a prediction and must not be presented as one.

## Australian Higher Education Presence

- **Australian data residency**: ✅ **CONFIRMED.** Kaltura announced expansion of its platform capabilities to three new regions including **Asia-Pacific (Sydney)**, with dedicated regional infrastructure "designed to meet data residency and performance requirements" and storing data within each geography, explicitly citing education among regulated sectors [K-C1].
- **Australian deployments evidenced**: University of Queensland — **decommissioned**, 31 December 2024 [K-C4].
- **Sector purchasing**: no Australian sector agreement located.

## UK Government Presence

**Not applicable to this project.** The client is an Australian university.

## Government Award History

`{not applicable}` — no UK tender evidence gathered, and none is relevant to an Australian university procurement.

## Strengths

- ✅ **Confirmed Australian data residency** with dedicated Sydney regional infrastructure, explicitly framed around data residency requirements for regulated sectors including education [K-C1].
- ✅ **Actively maintained lecture capture products.** Both Lecture Capture and the Capture desktop recorder had releases in December 2025 [K-C5] [K-C6] — this is a live product line, not a legacy one.
- ✅ **LTI Advantage certified** [K-C8].
- ✅ **Published VPAT** [K-C7] — though the conformance level was not verified in this research.
- ✅ **Financial transparency.** As a listed company, Kaltura's financial position is verifiable from filings rather than inferred [K-C3]. For vendor-viability assessment this is a genuine advantage over privately held competitors.
- ✅ **Breadth and open APIs.** The broadest platform of the candidates, extending beyond lecture capture into live streaming and custom video workflows — relevant if the university has video needs outside teaching.
- ✅ **Migration at institutional scale is demonstrated.** UQ's exit was executed as a vendor migration with content re-linked into Blackboard [K-C4]. Read as an *exit* data point this is reassuring: leaving Kaltura was practically achievable.

## Weaknesses

- ❌ **The one directly comparable Australian institution moved off it.** UQ's stated rationale — "Rationalising our video systems will simplify the environment for teaching staff, and students, reduce support complexity, and save money" [K-C4] — is almost word-for-word this project's own objective. That does not make Kaltura unsuitable, but it is the single most relevant piece of Australian evidence available and it is unfavourable.
- ❌ **ARR declining 3% with net dollar retention at 97%** [K-C3] — a base contracting slightly. Relevant to a five-year whole-of-life commitment (BR-003) and to R-012.
- ⚠️ **Blackboard Ultra integration depth NOT RESEARCHED.** No assessment of KAF against Blackboard Ultra, LTI 1.3 behaviour, or roster/role handling was made.
- ⚠️ **Provisioning API capability NOT ESTABLISHED.** Nothing found on event-driven provisioning granularity (REQ-025, R-022).
- ⚠️ **Accessibility conformance level NOT VERIFIED.** A VPAT is published [K-C7] but the WCAG version and level were not confirmed. NFR-C-002 is a mandatory gate at 2.2 AA.
- ⚠️ **Bulk export terms NOT ESTABLISHED.** A competitor publishes a Kaltura migration checklist for requesting a data extract [K-C9], which implies a vendor-assisted rather than self-service process — the same pattern seen across the market — but Kaltura's own terms were not located.
- ⚠️ **Multi-track / high-fidelity audio capability NOT ESTABLISHED** (FR-009).

## Assessment Against Mandatory Gates

| Gate | Position | Evidence status |
|------|----------|-----------------|
| NFR-SEC-001 (SSO+MFA, no local accounts) | Not researched | Unknown |
| NFR-C-002 (WCAG 2.2 AA) | VPAT published, level unverified [K-C7] | Must obtain |
| NFR-I-002 (open-format bulk export, no fee, no vendor assistance) | Vendor-assisted extract implied [K-C9] | Must obtain |

## Recommendation on Inclusion

The competitive market-test route is now settled (Conflict C-5), so inclusion turns solely on evaluation capacity. On present evidence Kaltura is unlikely to displace the three primary candidates, and including it consumes capacity against a compressed timeline (BC-1) — **recommend excluding unless the panel wants a fourth comparator.** If included, the three questions that matter most are: current WCAG level, Blackboard Ultra LTI 1.3 depth, and bulk export terms.

## Projects Referenced In

- `002-lecture-capture` — Lecture Capture Platform Consolidation (market completeness candidate)

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RSCH | ARC-002-RSCH-v1.0.md | ArcKit artifact | `002-lecture-capture/research/` | Parent research findings document |
| REQ | ARC-002-REQ-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Requirements and mandatory gates |

### Citations

| Citation ID | Source | URL | Fetch status | Claim supported |
|-------------|--------|-----|--------------|-----------------|
| K-C1 | IT Business Net — Kaltura Expands AI-Powered Agentic Experiences to Europe, Asia-Pacific, and Canada | https://itbusinessnet.com/2026/04/kaltura-expands-ai-powered-agentic-experiences-to-europe-asia-pacific-and-canada-with-dedicated-regional-infrastructure-for-enterprise-data-residency-and-performance/ | Search result | Asia-Pacific (Sydney) among three new regions; dedicated regional infrastructure for data residency; data stored within each geography; education named among regulated sectors; Agentic Avatars, AI Genie, Content Lab, REACH AI |
| K-C2 | MEEC — Lecture Capture Systems | https://www.meec-edu.org/lecture-capture-solutions-2/ | Fetched | Kaltura Inc, New York NY; RFP #0004-2023; 7/1/2023–6/30/2029; pricing not published |
| K-C3 | Kaltura — Q4 and Full-Year 2025 Financial Results | https://investors.kaltura.com/news-releases/news-release-details/kaltura-announces-fourth-quarter-and-full-year-2025-financial/ | Search result | FY2025 revenue US$180.9m (+1%); subscription US$171.9m (+3%); EE&T US$134.4m (+4%); ARR US$168.2m (−3%); NDR 97%; Adj EBITDA US$18.6m from US$7.3m; 2026 guidance US$181.2–184.2m |
| K-C4 | University of Queensland eLearning — Kaltura decommission and transition to Echo360 | https://elearning.uq.edu.au/project/kaltura-decommission-and-transition-echo360 | Fetched | Kaltura read-only 3 Jun 2024; vendor migration complete by 1 Jul 2024; supplementary migration Nov–Dec 2024; decommissioned 31 Dec 2024; rationale quoted; no information on bulk export capability or costs |
| K-C5 | Kaltura Knowledge Center — Lecture Capture release notes | https://knowledge.kaltura.com/help/kaltura-lecture-capture---release-notes | Search result | Release 14 December 2025 addressing PowerPoint and Windows 11 issues |
| K-C6 | Kaltura Knowledge Center — Kaltura Capture release notes | https://knowledge.kaltura.com/help/kaltura-capture-release-notes | Search result | Version 5.2.3 released 4 December 2025 |
| K-C7 | Kaltura — Official VPAT | https://corp.kaltura.com/kaltura-official-vpat/ | Search result | Accessibility Conformance Report / VPAT published. **Level not verified** |
| K-C8 | 1EdTech — LTI Advantage certification | https://www.imsglobal.org/ltiadvantage | Search result | Kaltura among LTI Advantage certified organisations |
| K-C9 | YuJa Help Center — Kaltura Migration Checklist for Requesting Data Extract | https://support.yuja.com/hc/en-us/articles/20649221953687-Kaltura-Migration-Checklist-for-Requesting-Data-Extract | Search result | Competitor-published checklist for requesting a Kaltura data extract — implies vendor-assisted export |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| — | — | — |

---

**Generated by**: ArcKit `/arckit:research` agent
**Generated on**: 2026-07-27
**ArcKit Version**: 6.7.2
**Project**: Lecture Capture Platform Consolidation (Project 002)
**Model**: Claude Opus 5 (1M context)
