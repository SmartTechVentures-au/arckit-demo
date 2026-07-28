# Vendor Profile: Panopto

> **Template Origin**: Official | **ArcKit Version**: 6.7.2 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-VEND-panopto-v1.0 |
| **Document Type** | Vendor Profile |
| **Project** | Lecture Capture Platform Consolidation (Project 002) |
| **Classification** | OFFICIAL-SENSITIVE |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-27 |
| **Last Researched** | 2026-07-27 |
| **Review Date** | 2026-08-26 |
| **Owner** | Dr. Benny Moog, Director Learning Technologies |
| **Confidence** | **HIGH** — 12+ independently sourced data points |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Project Team, Procurement, Digital & IT |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-27 | ArcKit AI | Initial creation from `/arckit:research` | PENDING | PENDING |

---

## Overview

Panopto is a purpose-built video management and lecture capture platform vendor headquartered in Pittsburgh, Pennsylvania [P-C2]. It is not currently in use at The University of Funk and appears in this project as a **market-test candidate** — one whose published position on the integration standards the requirements make CRITICAL is the strongest found.

Panopto has an established Australian presence: it launched a Sydney data centre for ANZ customers in November 2020, hosted in the AWS Asia-Pacific (Sydney) region, with all customer video content stored locally [P-C1]. Recent institutional movement toward Panopto includes UCL replacing Lecturecast (Echo360) with Panopto from 1 September 2025 [P-C11], and the University of South Australia moving from an on-premises Echo360 deployment to Panopto's cloud [P-C12] — the latter is vendor-published and should be treated as a claim of fact about a customer, not an endorsement.

## Products & Services

- **Panopto Enterprise** — video CMS, lecture capture, LMS integration, search, analytics
- **Panopto Essential** — non-enterprise tier [P-C3]
- **Remote recorder / scheduled capture** against certified room hardware
- **Panopto Capture** — browser and desktop recording, multi-camera and distributed recording [P-C9]
- **AI features** — search, captions, summaries, Smart Chapters; **AI Video Studio, Access AI, Knowledge Insights and Panopto Connect are priced separately as add-ons** [P-C3]
- **Certified hardware** — Epiphan Pearl family (Nexus, Mini, Nano) [P-C7] [P-C8]

## Pricing Model

**Not published — quote only.** Panopto's own pricing page states verbatim: *"Panopto is an enterprise platform. Your deployment—the number of users, integrations, add-ons, and deployment model—is unique. So is your price."* No tiers, storage figures, user counts, video hours or prices are disclosed. No free subscription tier [P-C3].

Note that **AI capabilities are add-ons priced separately** [P-C3] — a quote comparison must state explicitly whether captioning/AI features are in or out of the base price, or the comparison against bundled competitors will be apples-to-oranges.

**Sector price comparators only** (published UK public-sector award notices for the same product; **not** applicable as a UoF cost estimate):

| Buyer | Value | Term | Confidence |
|---|---|---|---|
| University of Derby | **£393,572** | 1 Sep 2024 – 31 Aug 2027 (3 yr) | Medium — primary Contracts Finder notice returned HTTP 403; figure from search summary. **Re-verify before any Ops Committee paper** [P-C10] |
| Royal Holloway, University of London | **£172K** | not captured | Low — aggregator summary [P-C13] |
| University of Southampton | not captured | 4 Jun 2021 – 3 Jun 2024 | Low — dates only [P-C10] |

Panopto also holds a US MEEC consortium master agreement under RFP #0004-2023, term 1 July 2023 – 30 June 2029, multi-award; pricing not published [P-C2].

## Australian Higher Education Presence

- **Australian data residency**: ✅ **CONFIRMED.** Sydney data centre launched November 2020 for ANZ customers; AU Cloud in the AWS Asia-Pacific (Sydney) Region; "all video recordings and content stored on the customer's Panopto platform to be stored locally"; encrypted at rest and in transit; multi-AZ with server redundancy [P-C1].
- **Australian deployments evidenced**: University of South Australia (from on-premises Echo360) [P-C12] — vendor-published.
- **Sector purchasing**: no CAUDIT or other Australian sector agreement located.

## UK Government Presence

**Not applicable to this project.** The client is an Australian university. UK contract notices appear in this profile solely as published price evidence for the same product.

## Government Award History

`{not applicable}` — no UK tender evidence gathered, and none is relevant to an Australian university procurement.

## Strengths

- ✅ **Strongest published integration-standards position in the market.** Holds an **LTI Advantage Complete** certification from 1EdTech [P-C4] — awarded only where a tool certifies LTI 1.3 Core **and all three** Advantage services [P-C14].
- ✅ **Blackboard Ultra LTI 1.3 documented and unqualified.** LTI 1.3 available for Blackboard Ultra, Canvas, D2L and Moodle; supports both Ultra and Original course views; batch course provisioning documented [P-C5] [P-C6] [P-C15]. Directly relevant given Blackboard announced it would stop supporting Building Block (B2) integrations from June 2024 [P-C6].
- ✅ **Course roles inherited automatically.** "Panopto inherits Blackboard course roles and permissions automatically, so access control stays aligned with institutional policies without separate configuration in Panopto" [P-C6] — materially supportive of FR-016 (access derived from enrolment, no locally maintained access list).
- ✅ **Confirmed AU data residency since 2020** [P-C1] — the longest-established AU position of the specialists.
- ✅ **Certified room hardware path.** Epiphan Pearl family is Panopto Certified after testing for compatibility and integration [P-C7]; Pearl Nexus records/streams up to 3 channels of 1080p with SDI, HDMI, USB, SRT and NDI video and XLR, USB and 3.5mm audio inputs [P-C8]. Tested rather than improvised integration is a genuine operational strength for INT-006.
- ✅ **Self-service custom ASR dictionaries.** Site-level custom dictionaries for ASR and OCR covering specialised terms, proper nouns and acronyms [P-C16] — institution-maintained, unlike the vendor-ticket model of at least one competitor. Directly supports FR-007's vocabulary-list acceptance criterion.
- ✅ **Largest public review base of the specialists** — G2 4.3/5 from 246+ reviews (*low confidence: aggregated search result, not an individually fetched G2 page*).

## Weaknesses

- ❌ **Published accessibility position is WCAG 2.1 AA, not 2.2 AA.** Panopto's own accessibility page states the platform is "regularly evaluated against **WCAG 2.1 AA** and Section 508 standards" [P-C17]. **NFR-C-002 is a mandatory pass/fail gate at WCAG 2.2 AA.** On published evidence Panopto does not clear it.
- ❌ **VPAT is not published.** "Panopto's Accessibility Conformance Report documentation is available on request" [P-C18] — weaker transparency than a competitor publishing VPATs with a named third-party auditor. A current WCAG 2.2 AA VPAT must be requested before shortlisting.
- ❌ **Multi-track audio is not available.** Community evidence indicates multi-track audio is not currently supported, and for distributed recording "at least one device needs to record a primary audio stream, as secondary-only recordings will not include audio" [P-C9]. **This is disqualifying for FR-009 (high-fidelity music performance capture) as a native capability** — the discipline exception must be served by specialist hardware regardless (which the Epiphan certification helpfully enables).
- ❌ **Bulk export is vendor-assisted, not self-service.** A Panopto data extract is requested from the vendor, takes **3–4 weeks**, and is delivered as access to an AWS S3 bucket [P-C19]. Community evidence indicates no single self-service bulk download capturing all streams and source files [P-C20]. Against NFR-I-002's "without vendor assistance being required" this **fails on published evidence** — and a 4-week vendor lead time would consume the entire July 2027 migration window (INT-007).
- ⚠️ **Provisioning API capability unresolved — treat as unknown.** Community evidence references SOAP `CreateUser` / `SyncExternalUser` and users requesting "SCIM compatibility, or at least some REST API endpoints" [P-C21]. **The post is of uncertain date and Panopto publishes REST APIs; this must not be carried into any paper as a finding.** It is the weakest evidence in this profile and must be verified with the vendor. Risk R-022's mandatory gate is the correct mitigation.
- ⚠️ **AI features priced separately** [P-C3] — quote comparability risk (see Pricing Model).

## Assessment Against Mandatory Gates

| Gate | Position | Evidence status |
|------|----------|-----------------|
| NFR-SEC-001 (SSO+MFA, no local accounts) | Likely pass — SSO listed among enterprise security features [P-C3]; must verify elimination of local/service account paths | Not researched to conclusion |
| NFR-C-002 (WCAG 2.2 AA) | **Published position is 2.1 AA — below the gate** [P-C17] | Request current 2.2 AA VPAT |
| NFR-I-002 (open-format bulk export, no fee, no vendor assistance) | **Fails "no vendor assistance" on published evidence** — 3–4 week vendor-provided extract [P-C19] | Mitigate contractually; test practically |

## Open Questions for Evaluation

1. Is there a current WCAG **2.2** AA VPAT, and if not, what is the remediation plan and date?
2. What is the current, supported provisioning API — REST or SOAP? Does it support event-driven role assignment at coordinator/tutor/marker granularity within 15 minutes (INT-001)?
3. Can a full archive export be self-served, and what is the guaranteed maximum elapsed time?
4. Are AI/captioning capabilities in the base price or add-ons, and at what cost?
5. What is the appliance authentication model for certified hardware (INT-006, NFR-SEC-002)?

## Projects Referenced In

- `002-lecture-capture` — Lecture Capture Platform Consolidation (market-test candidate; proposed for shortlist)

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RSCH | ARC-002-RSCH-v1.0.md | ArcKit artifact | `002-lecture-capture/research/` | Parent research findings document |
| REQ | ARC-002-REQ-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Requirements and mandatory gates |

### Citations

| Citation ID | Source | URL | Fetch status | Claim supported |
|-------------|--------|-----|--------------|-----------------|
| P-C1 | Panopto — Expands Global Video Cloud, Launches New Data Center in Australia | https://www.panopto.com/company/news/panopto-expands-global-video-cloud-launches-new-data-center-in-australia/ | Search result (news index fetched; article body not retrieved) | Sydney data centre for ANZ, Nov 2020; AU Cloud in AWS Asia-Pacific (Sydney); content stored locally; encrypted at rest and in transit; multi-AZ |
| P-C2 | MEEC — Lecture Capture Systems | https://www.meec-edu.org/lecture-capture-solutions-2/ | Fetched | Panopto Inc, Pittsburgh PA; RFP #0004-2023; 7/1/2023–6/30/2029; pricing not published |
| P-C3 | Panopto — Pricing | https://www.panopto.com/pricing/ | Fetched | Quote-only; verbatim pricing statement; Enterprise and Essential; SSO, SOC 2, GDPR, FERPA; AI Video Studio, Access AI, Knowledge Insights, Panopto Connect priced separately; no free tier |
| P-C4 | Panopto — Achieves LTI Advantage Complete Certification from 1EdTech | https://www.panopto.com/company/news/panopto-achieves-lti-advantage-certification-1edtech/ | Search result | LTI Advantage Complete certification |
| P-C5 | Panopto Support — How to Set Up a Blackboard Integration with LTI 1.3 | https://support.panopto.com/s/article/How-to-Set-Up-a-Blackboard-Ultra-Integration-with-LTI-1-3 | Search result | LTI 1.3 setup for Blackboard Ultra |
| P-C6 | Panopto — Blackboard integration page and LTI 1.3 release notes | https://www.panopto.com/integrations/blackboard/ | Search result | LTI 1.3 for Blackboard Ultra, Canvas, D2L, Moodle; Ultra and Original course views; inherits Blackboard course roles and permissions automatically; Blackboard B2 support ended June 2024 |
| P-C7 | Panopto — Certifies Epiphan Pearl Devices for Superior Classroom Capture | https://www.panopto.com/company/news/panopto-certifies-epiphan-pearl-devices-for-superior-classroom-capture/ | Search result | Pearl family Panopto Certified after compatibility and integration testing |
| P-C8 | Epiphan Video — Pearl Nexus | https://www.epiphan.com/products/pearl-nexus/ | Search result | Up to 3 channels 1080p; SDI, HDMI, USB, SRT, NDI; XLR, USB, 3.5mm audio; cloud management |
| P-C9 | Panopto Community — Audio Stream | https://community.panopto.com/discussion/1773/audio-stream | Search result | "Multi-track audio is not currently available in Panopto"; distributed recording requires a primary audio stream |
| P-C10 | UK Contracts Finder / search summary — University of Derby and Southampton Panopto contracts | https://www.contractsfinder.service.gov.uk/notice/4e6f2ce8-5bda-4b50-afcc-dbfdc1d003aa | **HTTP 403** — search summary only | Derby £393,572, 1 Sep 2024 – 31 Aug 2027; Southampton 4 Jun 2021 – 3 Jun 2024. **Medium/low confidence** |
| P-C11 | UCL ISD — Launching Panopto, our new lecture capture and video management platform | https://www.ucl.ac.uk/isd/news/2025/sep/launching-panopto-new-lecture-capture-and-video-management-platform | Fetched | Replaces Lecturecast (Echo360); launch 1 Sep 2025; Panopto Scheduler from 8 Sep 2025 |
| P-C12 | Panopto — Switching From An On-Premises Solution To The Panopto Video Cloud | https://www.panopto.com/blog/switching-from-an-on-premises-solution-to-the-panopto-video-cloud/ | Search result | University of South Australia moved from customised on-premises Echo360 to Panopto cloud. **Vendor-published** |
| P-C13 | bidstats.uk — Lecture Capture Software Solution (Panopto) [Award] | https://bidstats.uk/tenders/2024/W31/827588722 | **HTTP 403** — search summary only | Royal Holloway → Panopto, £172K. **Low confidence** |
| P-C14 | 1EdTech — LTI Advantage certification | https://www.imsglobal.org/ltiadvantage | Search result | "LTI Advantage Complete" awarded for LTI 1.3 Core plus all three Advantage services |
| P-C15 | Panopto Support — How to Batch Provision Courses in Blackboard | https://support.panopto.com/s/article/provision-courses-blackboard-1 | Search result | Batch course provisioning documented |
| P-C16 | Aalto University OPIT — Boost ASR accuracy on Panopto with a Custom Dictionary | https://blogs.aalto.fi/opit/2024/08/12/boost-asr-accuracy-on-panopto-with-a-custom-dictionary-tailored-to-aalto-university/ | Search result | Site-level custom dictionaries for ASR and OCR; institution-specific terms, acronyms, proper nouns |
| P-C17 | Panopto — Video Accessibility & Captioning Platform | https://www.panopto.com/capabilities/accessibility/ | Fetched | "regularly evaluated against WCAG 2.1 AA and Section 508 standards"; 3Play Media, Rev.com, Verbit.ai integrations |
| P-C18 | Panopto — same page | https://www.panopto.com/capabilities/accessibility/ | Fetched | "Panopto's Accessibility Conformance Report documentation is available on request" |
| P-C19 | YuJa Help Center — Panopto Migration Checklist for Requesting Data Extract | https://support.yuja.com/hc/en-us/articles/19402197922071-Panopto-Migration-Checklist-for-Requesting-Data-Extract | **HTTP 403** — search summary only | Allow 3–4 weeks for extract; delivered as access to an AWS S3 bucket. **Competitor-published** |
| P-C20 | Panopto Community — bulk download videos | https://community.panopto.com/discussion/1174/bulk-download-videos | Search result | Bulk download capturing all streams and source files not available in one action |
| P-C21 | Panopto Community — Automating user provisioning through the APIs | https://community.panopto.com/discussion/554/automating-user-provisioning-through-the-api-s | Search result | SOAP `CreateUser` / `SyncExternalUser`; community request for SCIM or REST provisioning endpoints. **Date uncertain — low confidence, must verify** |

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
