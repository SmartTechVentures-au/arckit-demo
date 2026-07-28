# Vendor Profile: YuJa

> **Template Origin**: Official | **ArcKit Version**: 6.7.2 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-VEND-yuja-v1.0 |
| **Document Type** | Vendor Profile |
| **Project** | Lecture Capture Platform Consolidation (Project 002) |
| **Classification** | OFFICIAL-SENSITIVE |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-27 |
| **Last Researched** | 2026-07-27 |
| **Review Date** | 2026-08-26 |
| **Owner** | Dr. Benny Moog, Director Learning Technologies |
| **Confidence** | **MEDIUM-LOW** — 6 sourced data points; several material positions could not be established from published sources |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Project Team, Procurement, Digital & IT |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-27 | ArcKit AI | Initial creation from `/arckit:research` | PENDING | PENDING |

---

## Overview

YuJa is a video platform vendor headquartered in San Jose, California [Y-C2], positioned on multi-tenant SaaS architecture and on displacing incumbents. It is a credible fourth player on market presence — it holds a US MEEC consortium master agreement alongside Echo360, Kaltura, Panopto and Mediasite [Y-C2] — and it runs the most developed **inbound migration practice** of any vendor researched, publishing step-by-step data-extract checklists for Panopto, Kaltura and Mediasite customers [Y-C4].

**This profile carries the lowest confidence of the five.** Two positions that are CRITICAL to this project — Australian data residency and LTI 1.3 certification — could not be established from any published source, and the one independent accessibility assessment located reports only *partial* conformance against a mandatory gate.

## Products & Services

- **YuJa Enterprise Video Platform** (also referenced as Lumina Video Platform / EVCM in institutional documentation)
- **Auto-captioning** with user caption download [Y-C3]
- **Custom metadata schemas** managed through the Admin Panel [Y-C6]
- **YuJa API** [Y-C5]
- **Migration services** — published extract checklists for Panopto, Kaltura and Mediasite [Y-C4]
- **AutoRedact.AI** — automated privacy tool blurring faces and removing screen-captured personal data before institutional release (*reported in market analysis; not verified against a YuJa-published page*)

## Pricing Model

**Not published.** No list pricing, tiers or rate card located. Quote-based.

Holds a US MEEC consortium master agreement under RFP #0004-2023, term 1 July 2023 – 30 June 2029, multi-award; pricing not published [Y-C2].

Market analysis characterises YuJa as anchoring its market position through aggressive SaaS pricing and multi-tenant architecture. **This is a market-commentary characterisation, not a verified price position**, and should not be relied on.

## Australian Higher Education Presence

- **Australian data residency**: ⚠️ **NOT CONFIRMED.** YuJa's own Security and Trust page references "multiple physical data center zones" and "industry-leading cloud infrastructure" but **names no region, does not name the cloud provider, and states no data residency guarantee** [Y-C1]. A secondary search result indicates YuJa hosts in AWS, but this was not confirmed on a YuJa-published page. **This is a material gap against NFR-C-001 (CRITICAL), DR-006 and Principle 8.**
- **Australian deployments evidenced**: none located. TAFE South Australia publishes YuJa guidance, indicating some Australian vocational-sector presence, but no Australian university deployment was confirmed.
- **Sector purchasing**: no Australian sector agreement located.

## UK Government Presence

**Not applicable to this project.** The client is an Australian university.

## Government Award History

`{not applicable}` — no UK tender evidence gathered, and none is relevant to an Australian university procurement.

## Strengths

- ✅ **Well-documented security baseline.** AES-256 or higher at rest; TLS 1.2 minimum with TLS 1.3 by default; SOC 2 Type II (independently audited); GDPR; HECVAT; TX-RAMP; CSA Cyber Essentials; database replication across multiple physical data centre zones [Y-C1].
- ✅ **Consortium standing.** One of five awardees on the MEEC lecture capture master agreement following a competitive RFP [Y-C2] — independent evidence of market credibility.
- ✅ **Strongest migration-in practice of any vendor researched.** Publishes detailed data-extract checklists for three named competitors, with realistic lead times stated (a Mediasite extract quoted at 2–3 weeks to transfer to a YuJa S3 bucket) [Y-C4]. If UoF needed to leave a restrictive incumbent, this is practical, transferable knowledge — and it is publicly available whether or not YuJa is selected.
- ✅ **Custom metadata schema support** [Y-C6] — relevant to DR-007 (migration provenance) and to FR-018 reporting.
- ✅ **Highest headline review score** — G2 4.5/5 (*low confidence: from an aggregated search result, not an individually fetched G2 page; review volume not captured and is materially smaller than Panopto's*).
- ✅ **HECVAT and TX-RAMP** [Y-C1] indicate the vendor is accustomed to higher-education security assessment processes.

## Weaknesses

- ❌ **Accessibility conformance is only *partial* against a mandatory gate.** An independent university accessibility statement records that "YuJa EVCM is **partially compliant** with the Web Content Accessibility Guidelines (WCAG) 2.2 Level A and AA", evaluated **by the vendor** using automated tools, manual testing and multi-browser validation [Y-C3]. **NFR-C-002 is a pass/fail gate.** "Partially compliant" is a fail unless the specific non-conformances are enumerated and carry dated remediation commitments.
- ❌ **No named data centre region and no data residency guarantee on the vendor's own trust page** [Y-C1]. For a CRITICAL requirement, silence on a published trust page is a significant weakness relative to competitors who name Sydney explicitly.
- ❌ **No ISO 27001 listed** among certifications on the trust page [Y-C1], where SOC 2 Type II, HECVAT, TX-RAMP and CSA Cyber Essentials are. Not disqualifying — SOC 2 Type II is a substantive control attestation — but it is an absence worth noting where competitors and the Australian public sector commonly reference ISO 27001.
- ❌ **LTI 1.3 / LTI Advantage certification NOT CONFIRMED.** YuJa was not found in the searched 1EdTech certification results [Y-C7]. YuJa's own claim is that products "conform to the latest Learning Tool Interoperability (LTI) and Single Sign On (SSO) standards" [Y-C1] — a vendor claim without a certification reference. **Must be verified directly in the 1EdTech product directory.** NFR-I-001 is CRITICAL.
- ❌ **Outbound export is unevidenced — a notable asymmetry.** YuJa documents in detail how to extract data *from* three competitors [Y-C4], but no equivalent documentation of exporting *from YuJa* was located. Individual caption download is documented [Y-C3]; bulk export of media plus captions plus metadata is not. Against NFR-I-002 and Principle 9 this asymmetry is exactly the lock-in pattern risk R-012 describes.
- ⚠️ **Blackboard Ultra integration depth NOT RESEARCHED.**
- ⚠️ **Provisioning API granularity NOT ESTABLISHED.** An API is published [Y-C5]; whether it supports event-driven role assignment at coordinator/tutor/marker granularity within 15 minutes (INT-001, R-022) is unknown.
- ⚠️ **Caption accuracy claim NOT FOUND.** Documentation acknowledges auto-generated captions "may contain errors and must be reviewed and edited" [Y-C3] — honest, but provides nothing to assess against NFR-U-003.
- ⚠️ **No Australian university deployment confirmed** — no reference site available in-jurisdiction.

## Assessment Against Mandatory Gates

| Gate | Position | Evidence status |
|------|----------|-----------------|
| NFR-SEC-001 (SSO+MFA, no local accounts) | Claims conformance to "latest ... SSO standards" [Y-C1] | Vendor claim; must verify local account elimination |
| NFR-C-002 (WCAG 2.2 AA) | **"Partially compliant" — fails as written** [Y-C3] | Requires enumerated non-conformances and remediation dates |
| NFR-I-002 (open-format bulk export, no fee, no vendor assistance) | **Outbound export unevidenced** | Must obtain |

## Recommendation on Inclusion

The competitive market-test route is now settled (Conflict C-5). Include **only after three threshold questions are answered in writing**, before evaluation capacity is committed:

1. In which region(s) are recordings, transcripts, captions and derived analytics **stored and processed**? Is the position contractual?
2. Is the platform LTI 1.3 / LTI Advantage certified, verifiable in the 1EdTech product directory?
3. What are the specific WCAG 2.2 AA non-conformances behind "partially compliant", and what are the remediation dates?

Two of these three are mandatory gates. If the answers are unsatisfactory, YuJa should not consume evaluation capacity against the compressed BC-1 timeline.

> **Regardless of selection**, YuJa's published migration checklists [Y-C4] are useful reference material for INT-007 planning and for calibrating realistic vendor-side export lead times against the July 2027 window.

## Projects Referenced In

- `002-lecture-capture` — Lecture Capture Platform Consolidation (conditional market-test candidate)

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RSCH | ARC-002-RSCH-v1.0.md | ArcKit artifact | `002-lecture-capture/research/` | Parent research findings document |
| REQ | ARC-002-REQ-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Requirements and mandatory gates |

### Citations

| Citation ID | Source | URL | Fetch status | Claim supported |
|-------------|--------|-----|--------------|-----------------|
| Y-C1 | YuJa — Security and Trust | https://www.yuja.com/trust-center/security/ | Fetched | "multiple physical data center zones"; **no region or cloud provider named; no data residency guarantee**; AES-256 or higher at rest; TLS 1.2 minimum, TLS 1.3 by default; SOC 2 Type II, GDPR, HECVAT, TX-RAMP, CSA Cyber Essentials; **no ISO 27001**; "All our products conform to the latest Learning Tool Interoperability (LTI) and Single Sign On (SSO) standards" |
| Y-C2 | MEEC — Lecture Capture Systems | https://www.meec-edu.org/lecture-capture-solutions-2/ | Fetched | YuJa Inc, San Jose CA; RFP #0004-2023; term 7/1/2023–6/30/2029; multi-award; pricing not published |
| Y-C3 | University College Dublin IT Services — YuJa Accessibility Statement | https://www.ucd.ie/itservices/ourservices/educationaltechnologies/accessibilitystatements/yujaaccessibilitystatement/ | Search result | "YuJa EVCM is partially compliant with the Web Content Accessibility Guidelines (WCAG) 2.2 Level A and AA"; vendor-evaluated using automated tools, manual testing, multi-browser validation; auto-captions "may contain errors and must be reviewed and edited"; caption download available |
| Y-C4 | YuJa Help Center — Mediasite / Panopto / Kaltura Migration Checklists for Requesting Data Extract | https://support.yuja.com/hc/en-us/articles/20502658067863--Mediasite-Migration-Checklist-for-Requesting-Data-Extract | Search result | Checklists published for three named competitors; Mediasite extract "allow 2-3 weeks to fully transfer all data to the YuJa S3 bucket"; Panopto extract 3–4 weeks |
| Y-C5 | YuJa Help Center — YuJa API | https://support.yuja.com/hc/en-us/articles/360049580714-YuJa-API | Search result | YuJa API documented |
| Y-C6 | YuJa Help Center — Setting Metadata Schemes and Managing Metadata | https://support.yuja.com/hc/en-us/articles/360047436573-Setting-Metadata-Schemes-and-Managing-Metadata | Search result | Custom metadata schemas managed via the Admin Panel |
| Y-C7 | 1EdTech — LTI Advantage certification and product directory | https://www.imsglobal.org/ltiadvantage | Search result | **YuJa not found** in searched certification results. Absence of evidence, not confirmed absence — verify in the directory directly |

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
