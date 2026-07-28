# Vendor Profile: Echo360 (EchoVideo)

> **Template Origin**: Official | **ArcKit Version**: 6.7.2 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-VEND-echo360-v1.0 |
| **Document Type** | Vendor Profile |
| **Project** | Lecture Capture Platform Consolidation (Project 002) |
| **Classification** | OFFICIAL-SENSITIVE |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-27 |
| **Last Researched** | 2026-07-27 |
| **Review Date** | 2026-08-26 |
| **Owner** | Dr. Benny Moog, Director Learning Technologies |
| **Confidence** | **HIGH** — 10+ independently sourced data points |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Project Team, Procurement, Digital & IT |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-27 | ArcKit AI | Initial creation from `/arckit:research` | PENDING | PENDING |

---

## Overview

Echo360 is a purpose-built lecture capture and video learning platform vendor, and **the incumbent capture platform at The University of Funk**. The company merged with Turning (learning engagement / student response) in January 2022 with investment from Centre Lane Partners, operating the combined business under the Echo360 brand [E-C7], and acquired Inkling in May 2024 [E-C8]. It is privately held and private-equity backed. Its principal product for this project is **EchoVideo**; the wider "Echosystem" also includes EchoInk, EchoEngage, EchoExam and GoReact [E-C1].

Echo360 is widely deployed in Australian higher education. The University of Queensland consolidated onto Echo360, decommissioning Kaltura on 31 December 2024, citing simplification of the environment, reduced support complexity and cost saving [E-C9]. Counter-directionally, the University of South Australia moved from an on-premises Echo360 deployment to Panopto (vendor-published claim) and UCL replaced Lecturecast (Echo360) with Panopto in September 2025 — so institutional movement in this market runs both ways.

## Products & Services

- **EchoVideo** — video management, scheduled lecture capture, publication to LMS, analytics
- **Universal Capture** — cross-platform capture interface running as software on Windows 10+ and macOS 10.14+, and on Pro and Pod appliances via the UC:Device and UC:Online interfaces, deliberately presenting a consistent interface across hardware and software [E-C4] [E-C5]
- **Capture appliances** — Pro and Pod. The legacy **SCHD appliance reached End of Software Support on 1 April 2020 and End of Life on 30 December 2020** [E-C6]
- **APIs** — published REST APIs and SDKs, including Reporting API, Capture Intake API and Capture API [E-C10]
- **Echosystem adjacent products** — EchoInk, EchoEngage, EchoExam, GoReact [E-C1]

## Pricing Model

**Not published.** No list pricing is available for Echo360 in any public source located. Pricing is quote-based, consistent with the segment norm.

**Sector price comparators only** (published UK public-sector award notices for the same product; **not** applicable as a UoF cost estimate — different jurisdiction, scale, scope and year):

- University of Sheffield → Echo360, reported at **£195K** [E-C11] — *low confidence; aggregator summary, primary notice returned HTTP 403*

Echo360 also holds a US consortium master agreement with MEEC (as "Echo360 / Turning Tech Intermediate, Inc.", Youngstown OH) under RFP #0004-2023, term 1 July 2023 – 30 June 2029, multi-award. Consortium pricing is not published [E-C2].

## Australian Higher Education Presence

- **Australian data residency**: ⚠️ **NOT CONFIRMED.** The Echo360 government/secure-solutions page contains no data residency, hosting region, cloud provider, SOC 2, ISO 27001, FedRAMP or IRAP statement — only US federal-sector approvals (Section 508, Air Force AFNIC, Marine Corps DADMS, Defense Health Agency, FEMA licences) [E-C3]. ASR runs on AWS Transcribe [E-C12], implying AWS but not establishing region. **This is a material open question for NFR-C-001, DR-006 and the PIA (risk R-013).**
- **Australian deployments evidenced**: University of Queensland (consolidated onto Echo360, 2024) [E-C9]; widely referenced across the Australian sector.
- **Sector purchasing**: no CAUDIT or other Australian sector agreement covering Echo360 was located. Absence of evidence, not evidence of absence — CAUDIT agreements are member-facing.

## UK Government Presence

**Not applicable to this project.** The client is an Australian university; UK Digital Marketplace, G-Cloud, DOS and Crown Commercial Service frameworks have no bearing on its procurement. UK contract notices are cited in this profile solely as published price evidence for the same product.

## Government Award History

`{not applicable}` — no UK tender evidence gathered, and none is relevant to an Australian university procurement.

## Strengths

- ✅ **Strongest published accessibility position in the market.** Announced 29 April 2026 that all five Echosystem solutions are compliant with **WCAG 2.2 AA**, with ongoing auditing and validation by **Level Access** (a named independent auditor), VPATs completed for each solution, and alignment to EN 301 549 and Section 508 [E-C1]. NFR-C-002 is a mandatory pass/fail gate at WCAG 2.2 AA — this is the only candidate with a published claim at that level.
- ✅ **Purpose-built scheduled capture.** Capture schedules are first-class objects linked to LMS courses; REST API integration automates course linking and scheduling and synchronises roster data [E-C13] [E-C10].
- ✅ **Low hardware lock-in.** Universal Capture runs as software on standard Windows/macOS room machines as well as on appliances [E-C4] [E-C5] — potentially the lowest marginal room-side cost of the specialists, and it moves OS patching onto the managed desktop estate (relevant to NFR-SEC-004 and BR-008).
- ✅ **Open caption format.** Closed caption and transcript files use the **WEBVTT** standard [E-C14] — satisfies the format half of NFR-I-002.
- ✅ **Candid documentation.** Echo360's own support material states that ASR "is unlikely to meet the accuracy levels required for closed captions for hearing-impaired individuals" [E-C12]. Unusually honest for vendor documentation, and a positive signal for evaluation dialogue.
- ✅ **Incumbency.** Lowest transition risk on the platform axis; staff familiarity; no archive migration required if retained (materially de-risks BR-007, INT-007 and R-020/R-021).

## Weaknesses

- ❌ **Blackboard LTI 1.3 position is equivocal, and this is the sharpest documented concern.** Echo360's own Blackboard Integration Overview states verbatim: *"NOTE that while migrating to LTI 1.3 may appear to be an option within Blackboard, it has not been fully tested by us. We are only supporting migrating to LTI 1.1."* [E-C15]. Separately, "LTI 1.3 does not currently support linking to EchoVideo Course sections themselves", and there is no automatic migration path from LTI 1.1 links to LTI 1.3 [E-C16]. NFR-I-001 makes LTI 1.3 CRITICAL. Section-level linking is how capture schedules attach to courses.
- ❌ **Australian data residency unconfirmed in any published source** [E-C3]. For the incumbent, on a CRITICAL requirement, this is a notable documentation gap.
- ❌ **Custom ASR dictionary is vendor-mediated, not self-service.** Custom transcription dictionaries "must be configured by Echo360 Support on behalf of institutions" [E-C12]. FR-007's acceptance criterion expects the institution to add recurring mis-transcribed discipline terms to a vocabulary list — a support-ticket dependency satisfies the letter and fails the operational intent, and creates a standing load on Digital Learning Support (D-6).
- ❌ **Bulk export terms unknown.** No published bulk export or termination-assistance documentation was found. Assumption A-10 (bulk export permitted without additional fee) remains unvalidated — this is exactly risk **R-020**, and it is the highest-value question in the D-1 contract review.
- ❌ **Legacy appliance EOL exposure.** SCHD units are more than six years past end of software support [E-C6]. If the D-3 inventory finds them in service, NFR-SEC-004 requires replacement or removal — they cannot be retained as exceptions.
- ⚠️ **Private-equity ownership with acquisition cadence** [E-C7] [E-C8]. A neutral, structural factor for risk R-012 (renewal price step-change): PE-backed vendors have an interest in ARR growth at renewal. **This is not evidence of intent and must not be presented as such** — it belongs in vendor viability, weighted low, evidenced from structure not inference.

## Assessment Against Mandatory Gates

| Gate | Position | Evidence status |
|------|----------|-----------------|
| NFR-SEC-001 (SSO+MFA, no local accounts) | Likely pass — must verify elimination of local and service account paths | Not researched to conclusion |
| NFR-C-002 (WCAG 2.2 AA) | **Published claim meets the standard** [E-C1] | Claim, third-party audited. Must still be tested per Principle 14 |
| NFR-I-002 (open-format bulk export, no fee, no vendor assistance) | Captions WEBVTT ✅; **bulk export UNKNOWN** | Requires D-1 contract review + practical export test |

## Open Questions for Evaluation

1. Where are recordings, transcripts, captions and derived analytics stored **and processed**? Is the position contractual or configurational?
2. Is LTI 1.3 with Blackboard Ultra production-supported, including section-level linking — or is LTI 1.1 the practical path?
3. Can a full archive export produce media **plus** WEBVTT captions **plus** unit/session/date association in one operation, without fee?
4. Can the institution maintain its own ASR custom dictionary without raising a support ticket?
5. What is the appliance authentication model — per-device identity, or shared administrative credentials (INT-006, NFR-SEC-002)?

## Projects Referenced In

- `002-lecture-capture` — Lecture Capture Platform Consolidation (incumbent; shortlist candidate)

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RSCH | ARC-002-RSCH-v1.0.md | ArcKit artifact | `002-lecture-capture/research/` | Parent research findings document |
| REQ | ARC-002-REQ-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Requirements and mandatory gates |
| RISK | ARC-002-RISK-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Risks R-012, R-020, R-022 |

### Citations

| Citation ID | Source | URL | Fetch status | Claim supported |
|-------------|--------|-----|--------------|-----------------|
| E-C1 | PR Newswire — Echo360 Achieves WCAG 2.2 AA Compliance Across the Echosystem | https://www.prnewswire.com/news-releases/echo360-achieves-wcag-2-2-aa-compliance-across-the-echosystem-302756675.html | Fetched | 29 Apr 2026; all five Echosystem solutions WCAG 2.2 AA; Level Access auditor; VPATs complete; EN 301 549 and Section 508 |
| E-C2 | MEEC — Lecture Capture Systems | https://www.meec-edu.org/lecture-capture-solutions-2/ | Fetched | "Echo360 / Turning Tech Intermediate, Inc." (Youngstown OH); RFP #0004-2023; 7/1/2023–6/30/2029; pricing not published |
| E-C3 | Echo360 — Government Secure Solutions | https://echo360.com/government/secure-solutions/ | Fetched | No data residency, hosting region, cloud provider or certification statement; US federal approvals only |
| E-C4 | Echo360 Support — Universal Capture Specifications / Supported Devices | https://support.echo360.com/hc/en-us/articles/360035035332-EchoVideo-Universal-Capture-Specifications | Search result | Supported on macOS 10.14+ and Windows 10+ |
| E-C5 | Echo360 Support — Universal Capture on the Pro and Pod | https://support.echo360.com/hc/en-us/articles/360035406231-Universal-Capture-on-the-Pro-and-Pod | Search result | UC accessible on Pro and Pod via UC:Device and UC:Online |
| E-C6 | Echo360 Support — Working with Managed Capture Devices | https://support.echo360.com/hc/en-us/articles/360035034472-Working-with-Capture-Appliances | Search result | SCHD End of Software Support 1 Apr 2020; End of Life 30 Dec 2020 |
| E-C7 | PR Newswire — Echo360 and Turning Merge | https://www.prnewswire.com/news-releases/echo360-and-turning-merge-to-support-higher-educations-shift-to-video-and-hybrid-learning-301457993.html | Search result | Jan 2022 merger; Centre Lane Partners investment; combined company under Echo360 brand |
| E-C8 | Centre Lane Partners — Echo360 Acquires Inkling | https://www.centrelanepartners.com/2024/05/21/echo360-acquires-inkling-to-form-premier-global-education-and-corporate-learning-saas-enterprise/ | Search result | Inkling acquisition, May 2024 |
| E-C9 | University of Queensland eLearning — Kaltura decommission and transition to Echo360 | https://elearning.uq.edu.au/project/kaltura-decommission-and-transition-echo360 | Fetched | Kaltura read-only 3 Jun 2024; decommissioned 31 Dec 2024; rationale quoted |
| E-C10 | Echo360 Support — API section | https://support.echo360.com/hc/en-us/sections/10967188719245-API | Search result | "modern, stateful" REST APIs with SDKs; Reporting, Capture Intake, Capture APIs |
| E-C11 | bidstats.uk — Lecture Capture System [Award] | https://bidstats.uk/tenders/2024/W30/827327063 | **HTTP 403** — search summary only | University of Sheffield → Echo360, £195K. **Low confidence** |
| E-C12 | Echo360 Support — ASR Service for Media Transcription | https://support.echo360.com/hc/en-us/articles/360035406171-EchoVideo-Automatic-Speech-Recognition-ASR-Service-for-Media-Transcription | Fetched | AWS Transcribe; confidence-score threshold; custom dictionaries "must be configured by Echo360 Support on behalf of institutions"; ASR "unlikely to meet the accuracy levels required for closed captions for hearing-impaired individuals" |
| E-C13 | Echo360 Support — Linking a Section and Capture Schedule to an LMS Course | https://support.echo360.com/hc/en-us/articles/11074882531597-EchoVideo-Linking-a-Section-and-Capture-Schedule-to-an-LMS-Course | Search result | Capture schedules linked to LMS courses |
| E-C14 | Echo360 Support — ASR Service page | https://support.echo360.com/hc/en-us/articles/360035406171-EchoVideo-Automatic-Speech-Recognition-ASR-Service-for-Media-Transcription | Fetched | "closed caption files and transcription files use the WEBVTT standard" |
| E-C15 | Echo360 Support — Blackboard Integration Overview | https://support.echo360.com/hc/en-us/articles/11074515169421-EchoVideo-Blackboard-Integration-Overview | Fetched | Verbatim LTI 1.3 caveat; REST API automates course linking/scheduling, roster sync, consolidated analytics |
| E-C16 | Echo360 Support — LTI Advantage and LTI 1.3 Support | https://support.echo360.com/hc/en-us/articles/11074490900621-EchoVideo-LTI-Advantage-and-LTI-1-3-Support | Fetched | LTI Advantage certified via 1EdTech (Deep Linking, NRPS, AGS); "LTI 1.3 does not currently support linking to EchoVideo Course sections themselves"; no automatic 1.1→1.3 migration |

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
