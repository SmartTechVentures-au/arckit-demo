# Technology and Service Research: Lecture Capture Platform Consolidation

> **Template Origin**: Official | **ArcKit Version**: 6.7.2 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-RSCH-v1.0 |
| **Document Type** | Technology and Service Research Findings |
| **Project** | Lecture Capture Platform Consolidation (Project 002) |
| **Classification** | OFFICIAL-SENSITIVE |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-27 |
| **Last Modified** | 2026-07-27 |
| **Review Date** | 2026-08-26 |
| **Owner** | Dr. Benny Moog, Director Learning Technologies — capability evidence owner |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Project Team, Steering Committee, Procurement, Digital & IT, Education Committee |

> **Classification rationale**: This document assesses named suppliers against criteria that will become a competitive evaluation. Sections 3 to 10 identify specific platform weaknesses against the mandatory gates; disclosure to any prospective supplier before criteria are issued would allow that supplier to prepare against the finding rather than be tested on it. It is OFFICIAL-SENSITIVE until the evaluation framework is signed under BR-004. Market landscape material (Section 2) may be published to Education Committee without restriction.

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-27 | ArcKit AI | Initial creation from `/arckit:research` command | [PENDING] | [PENDING] |

---

## Document Purpose and Standing

This document is **market evidence, not a recommendation of supplier**. Its three uses, in order:

1. **Input to the evaluation framework (BR-004).** The findings below identify which requirements actually discriminate between platforms and which do not. A criterion on which every candidate scores identically wastes weighting; a criterion where candidates genuinely differ is where the weighting belongs.
2. **Input to the whole-of-life cost model (BR-003).** This document establishes what *can* be costed from published sources and what cannot. Section 7 states plainly which parts of the TCO are unobtainable until the August baselines land.
3. **Evidence for the RIFF duplication test (BC-5, Conflict C-5).** The RIFF rule requires a written justification of why an incumbent or already-licensed tool is unsuitable [SGP-C2]. Section 5 provides the capability evidence that justification would draw on, in both directions.

**What this document does not do**: it does not select a platform, does not score options, and does not model The University of Funk's costs. Scoring happens under the signed framework (BR-004); cost modelling happens once D-1, D-2 and D-3 are delivered (see Section 7.1).

---

## 1. Executive Summary

### 1.1 Research Scope

**Requirements analysed**: 8 business requirements (BR-001 to BR-008), 18 functional (FR-001 to FR-018), 21 non-functional (NFR-P, A, S, SEC, C, U, M, I series), 7 integration (INT-001 to INT-007) and 7 data (DR-001 to DR-007) requirements from `ARC-002-REQ-v1.0.md`, together with the survey register subset named in the research brief (REQ-004, 008, 009, 010, 025, 029, 030, 031, 032, 033, 034, 035).

**Research categories identified**: 6, derived from requirement content rather than a standard list —

| # | Category | Requirements driving it |
|---|----------|-------------------------|
| 1 | Lecture capture and video management platforms | REQ-004, 008, 009; FR-001 to FR-012, FR-018; NFR-P-001, A-001 |
| 2 | Australian data residency and sector procurement context | REQ-030; NFR-C-001; DR-006; Principle 8 |
| 3 | Captioning and ASR accuracy | REQ-029; FR-006, FR-007; NFR-C-002, NFR-U-003 |
| 4 | Provisioning and integration standards (LTI 1.3, SCIM) | REQ-025, 031; NFR-I-001; INT-001, INT-003; Principle 12 |
| 5 | Data portability, export and exit | REQ-034; NFR-I-002; FR-017; INT-007; Principle 9 |
| 6 | Multi-camera / high-fidelity performance capture | REQ-010; FR-009; BR-005; Principle 4 |
| (7) | Capture hardware and appliance dependency — treated as a cross-cutting concern within categories 1 and 6 | TC-4; NFR-SEC-004; INT-006; BR-008 |

**Research approach**: vendor documentation and support knowledge bases, vendor and third-party press releases, published public-sector contract award notices, peer-reviewed and industry ASR research, official Microsoft product documentation, and Australian sector bodies (AARNet, CAUDIT). No UK Digital Marketplace, G-Cloud, Crown Commercial Service or DOS material has been used — those frameworks have no application to an Australian university. UK contract award notices appear **only** as published price evidence for the same products, and are labelled as such.

**Candidates assessed**: Echo360 (EchoVideo), Panopto, Kaltura, YuJa, Microsoft (Teams + Stream on SharePoint), Zoom. Enghouse Mediasite is noted as a fifth commercial player evidenced through a US consortium award but was not researched in depth. Open-source options are covered in Section 6.5.

### 1.2 The Finding That Matters Most

**The contested question — Echo360 versus Microsoft — is answerable from published documentation on one specific point, and the answer is unfavourable to a pure Microsoft consolidation for *scheduled room capture*.**

Microsoft's own documentation states that enabling the auto-recording policy "gives the organizer access to the meeting option" and that organizers "must manually enable **Record and transcribe automatically** setting for each meeting they want recorded and transcribed automatically" [MSAR-C1]. Automation without per-meeting user action requires a Teams Premium meeting template, and "only organizers with a Teams Premium license can use assigned meeting templates" [MSAR-C2]. There is no tenant-wide force-record control.

FR-001 requires capture to begin "automatically with no human action", and NFR-U-001 requires scheduled capture to need "zero academic actions". On the documented behaviour, a Teams-based scheduled capture service for every timetabled lecture requires, at minimum: a Teams meeting created per timetabled session with a room resource, an organizer identity, a Teams Premium licence on that organizer, an enforced meeting template, and an integration that reconciles all of it against Allocate+ changes within the INT-002 SLA. That is a build, and it should be costed as one.

This does **not** decide the question. It reframes it: the Microsoft option is not "capability we already own, switched on". It is "capability we already own, plus a licence uplift, plus an integration build". Whether that is still cheaper than a purpose-built platform is exactly what the BR-003 cost model must answer — and it cannot be answered until D-2 (the Microsoft entitlement position) is delivered.

### 1.3 Key Findings

- **Accessibility now discriminates between vendors, and it discriminates against Panopto.** Echo360 announced on 29 April 2026 that all five Echosystem products are compliant with **WCAG 2.2 AA**, with ongoing auditing by Level Access, and has completed VPATs for each [E360A-C1] [E360A-C2]. Panopto's own accessibility page states its platform is "regularly evaluated against **WCAG 2.1 AA** and Section 508 standards" and that its conformance report is "available on request" rather than published [PANA-C1] [PANA-C2]. NFR-C-002 is a **mandatory pass/fail gate at WCAG 2.2 AA**. On published evidence today, Echo360 clears it and Panopto does not — but this is a claim about published documentation, not about tested conformance, and NFR-C-002 requires conformance "assessed during evaluation against the platform as it will be configured, not against a vendor conformance claim". Both statements must be tested.

- **Echo360's Blackboard integration is documented at LTI 1.1, not LTI 1.3.** Echo360's Blackboard Integration Overview states: "NOTE that while migrating to LTI 1.3 may appear to be an option within Blackboard, it has not been fully tested by us. We are only supporting migrating to LTI 1.1." [E360BB-C1]. Echo360 is separately LTI Advantage certified through 1EdTech and documents LTI 1.3 deep linking with Blackboard [E360LTI-C1] [E360BB2-C1]. NFR-I-001 makes LTI 1.3 a CRITICAL requirement. Panopto by contrast holds an LTI Advantage **Complete** certification [PANLTI-C1] and documents LTI 1.3 for Blackboard Ultra specifically [PANBB-C1]. This is the sharpest documented integration difference found, and it runs the opposite way to the accessibility finding.

- **Australian data residency is achievable on every commercial candidate, and is therefore a weak discriminator.** Panopto has operated an AU cloud in AWS Asia-Pacific (Sydney) since November 2020 for ANZ customers [PANAU-C1]. Kaltura announced dedicated regional infrastructure including Asia-Pacific (Sydney) for data residency [KALAU-C1]. Zoom permits administrators to set Australia as the storage region for cloud recordings, activated for AARNet customers from 1 February 2021 [ZOOMAU-C1]. Microsoft 365 lists Australia as a *Local Region Geography* with Product Terms, Multi-Geo and Advanced Data Residency commitments available for Exchange, SharePoint/OneDrive and Teams, with data centres in Sydney and Melbourne [MSDR-C1] [MSDR-C2]. Echo360's and YuJa's Australian residency positions could **not** be confirmed from published sources (Section 4.2) and must be obtained in writing.

- **Caption accuracy cannot be evaluated from vendor claims, and the independent evidence says so explicitly.** Peer-reviewed work measuring eleven ASR services against Higher Education lecture recordings found that "accuracy ranges widely between vendors and for the individual audio samples" and that "despite the recent improvements of ASR, common services lack reliability in accuracy" [ASR-C1] [ASR-C2]. 3Play Media's 2025 industry study, across 205 hours and over 1.7 million words, reported that "error rates across all engines still fall short of meeting accessibility requirements" and that human-in-the-loop workflows remain critical [3PLAY-C1] [3PLAY-C2]. Echo360's own support documentation concedes that ASR "is unlikely to meet the accuracy levels required for closed captions for hearing-impaired individuals" [E360ASR-C1]. NFR-U-003's insistence on a fixed discipline-vocabulary test set is vindicated by the literature. **D-8 is not optional; without it there is nothing to score.**

- **The appliance estate is a genuine cost driver and vendor hardware strategies now diverge.** Panopto has certified the Epiphan Pearl family for classroom capture, with Pearl Nexus recording and streaming up to three channels of 1080p with SDI/HDMI/USB/SRT/NDI inputs and XLR audio [PANEPI-C1] [EPIPN-C1]. Echo360 runs Universal Capture as software on Windows 10+ and macOS 10.14+ as well as on its Pro and Pod appliances [E360UC-C1] [E360UC2-C1], and its earlier SCHD appliance reached end of software support on 1 April 2020 and end of life on 30 December 2020 [E360SCHD-C1]. A Microsoft-based room capture path depends on Teams Rooms devices, and Teams Rooms Pro is published at **US$40 per room per month, paid yearly** [MSTRP-C1]. This is the one option whose room-side licence cost is a published, knowable number today — and it is a *new recurring* cost, not an existing entitlement.

- **Exit is the weakest-evidenced area across the whole market, which is itself the finding.** No vendor publishes bulk export of media plus captions plus metadata as a self-service, no-fee, standing capability. The most specific public evidence found is from a competitor's migration documentation, indicating that a Panopto data extract is requested rather than self-served, takes 3–4 weeks, and is delivered as access to an AWS S3 bucket [PANEXP-C1]. Echo360 documents that caption and transcript files use the WEBVTT standard [E360ASR-C2], which satisfies the *format* half of NFR-I-002 but says nothing about bulk retrieval. NFR-I-002's requirement that export be "tested during evaluation, not accepted as a contractual assurance" is the correct control, and R-020 is correctly rated.

### 1.4 Build vs Buy Summary

Currency note: figures below are in the currency in which they were published (US$ for Microsoft list pricing; £ for UK public contract award notices used as sector price evidence). **No conversion to AUD has been applied**, because applying an exchange rate to a foreign list price and presenting the result as an Australian cost would create exactly the false precision this document is trying to avoid.

| Approach | Categories | 3-Year TCO | Basis | Rationale |
|----------|-----------|------------|-------|-----------|
| **BUILD** (custom capture platform) | 0 of 6 | Not modelled — rejected at screening | n/a | A mature product market with five-plus credible suppliers; building would breach Principle 19 in spirit and cannot meet the July 2027 window (BC-2) |
| **BUY** (commercial capture SaaS) | 1, 3, 5 | **UNAVAILABLE** — see §7.1 | Vendor list pricing is quote-only across all four capture vendors | The only route that meets FR-001 to FR-012 without an integration build |
| **CONFIGURE** (realise licensed Microsoft capability) | 1 (partial), 3 (partial) | **PARTIALLY AVAILABLE** — Teams Rooms Pro US$40/room/month published [MSTRP-C1]; Teams Premium and A-series entitlement position unavailable pending D-2 | Principle 19's preferred route, but requires an integration build to reach FR-001 |
| **ADOPT** (open source) | 0 of 6 recommended | Not modelled | Opencast assessed and not shortlisted — §6.5 | Operational burden lands on the same AV/support teams already identified as capacity-constrained (R-008) |
| **HYBRID BUILD** (discipline exception) | 6 | **UNAVAILABLE** — hardware is specifiable, venue count is not | Epiphan/Dante components have published specifications; venue count and existing AV inventory outstanding (D-3) | Principle 4 route for FR-009 |
| **TOTAL** | 6 | **Cannot be stated** | | See §7.1 for the four specific blockers |

### 1.5 Shortlist Proposed for Evaluation

Proposed for the evaluation under BR-004 — **not** a preference order:

1. **Echo360 (EchoVideo)** — incumbent. Strongest published accessibility position (WCAG 2.2 AA, Level Access audited, VPATs complete) [E360A-C1]; purpose-built scheduled capture; must be tested hard on LTI 1.3 with Blackboard [E360BB-C1] and on AU residency, neither of which is resolved by published material.
2. **Panopto** — strongest published integration standards position (LTI Advantage Complete [PANLTI-C1], documented Blackboard Ultra LTI 1.3 [PANBB-C1]), confirmed AU region since 2020 [PANAU-C1], certified hardware path via Epiphan Pearl [PANEPI-C1]. Must be tested on WCAG 2.2 (published position is 2.1 AA [PANA-C1]) and on provisioning API granularity.
3. **Microsoft (Teams + Stream on SharePoint)** — the Principle 19 candidate and the CIO's position. Must be assessed as *platform plus build*, with the auto-record constraint [MSAR-C1] and Teams Rooms Pro cost [MSTRP-C1] costed explicitly rather than assumed away.
4. **YuJa** — credible fourth on market presence and consortium standing [MEEC-C1], with an aggressively positioned migration practice [YUJAMIG-C1]. Published accessibility position is *partial* WCAG 2.2 A/AA per an independent university statement [YUJA-C1], and no data-centre region is named on its own trust page [YUJAT-C1]. The market test route is settled (Conflict C-5), so inclusion turns on evaluation capacity and on the threshold questions in the vendor profile being answered first.
5. **Kaltura** — include for completeness; AU region confirmed [KALAU-C1], but the one directly comparable Australian data point is a university *leaving* Kaltura for Echo360 [UQ-C1]. Financially the most transparent supplier (listed; 2025 revenue US$180.9m, ARR down 3%, net dollar retention 97% [KLTR-C1]).

**Explicitly out of shortlist**: Zoom as the *capture* platform. Zoom is retained in scope only as a Learning Delivery candidate under FR-008 and as an AU-residency-capable recording source [ZOOMAU-C1]; nothing found supports it as a timetable-driven room capture platform.

### 1.6 Requirements Coverage

Coverage is stated against the capture requirement subset in the research brief.

- ✅ **9 of 12 subset requirements (75%)** have at least one identified solution with published supporting evidence — REQ-004, 008, 009, 025, 029, 030, 031, 032, 034.
- ⚠️ **1 requirement (8%)** requires a hardware/integration build under every option — REQ-010 (multi-camera performance capture, §10).
- 🔍 **2 requirements (17%)** cannot be assessed from market research at all because they are properties of *this university's* position, not of any product — REQ-033 (Essential Eight maturity of the estate) and REQ-035 (spend flat or reduced). Both depend on D-1/D-2/D-3.

---

## 2. Market Landscape

### 2.1 Structure of the Market

The lecture capture segment is a consolidated, mature product market with a small number of specialist suppliers and one large adjacent generalist (Microsoft). It has the characteristics of a **Product** on the Wardley evolution axis — off-the-shelf, stabilising, differentiated on integration and service rather than on core function. That positioning is the single strongest argument against building (§6.1).

Corporate structure matters here more than usual, because three of the five specialists have changed hands or merged recently:

| Vendor | Corporate position | Evidence |
|--------|-------------------|----------|
| **Echo360** | Merged with Turning (announced January 2022) with investment from Centre Lane Partners; combined company operates under the Echo360 brand; acquired Inkling in May 2024. Private-equity backed. Listed on the MEEC consortium agreement as "Echo360 / Turning Tech Intermediate, Inc." | [E360M-C1] [E360M-C2] [MEEC-C1] |
| **Panopto** | Headquartered Pittsburgh, PA per MEEC listing. Certification and partnership activity with Epiphan for classroom hardware. | [MEEC-C1] [PANEPI-C1] |
| **Kaltura** | Publicly listed (NASDAQ: KLTR). FY2025 total revenue US$180.9m (+1% YoY); subscription revenue US$171.9m (+3%); Enterprise, Education & Technology segment US$134.4m (+4%); ARR US$168.2m (−3%); net dollar retention 97%. 2026 guidance US$181.2–184.2m. | [KLTR-C1] |
| **YuJa** | San Jose, CA per MEEC listing. Positions on multi-tenant SaaS and migration-from-incumbent. | [MEEC-C1] [YUJAMIG-C1] |
| **Enghouse Mediasite** | Paramus, NJ per MEEC listing. Not researched in depth. | [MEEC-C1] |

> **Procurement relevance**: Echo360's private-equity ownership and acquisition cadence is a legitimate, *neutral* factor for R-012 (renewal step-change) — PE-backed vendors have a structural interest in ARR growth at renewal. It is not evidence of intent and must not be presented as such. Kaltura's declining ARR and 97% net dollar retention [KLTR-C1] is the mirror-image concern: a supplier under revenue pressure. Both belong in the vendor-viability section of the evaluation, weighted low, evidenced from filings not inference.

### 2.2 Comparison Table

Every cell below is either sourced or explicitly marked **NOT CONFIRMED**. A blank is not an assessment.

| Dimension | Echo360 (EchoVideo) | Panopto | Kaltura | YuJa | Microsoft (Teams + Stream) | Zoom |
|---|---|---|---|---|---|---|
| **Purpose-built scheduled room capture** | Yes — capture schedules linked to LMS courses [E360API-C1] | Yes — remote recorder + scheduling with certified hardware [PANEPI-C1] | Yes — Lecture Capture product, actively maintained (release 14 Dec 2025) [KALLC-C1] | NOT CONFIRMED in depth | **No** — requires per-meeting organizer action or Teams Premium template [MSAR-C1] [MSAR-C2] | Not evidenced as timetable-driven room capture |
| **AU data residency** | NOT CONFIRMED — no published statement found [E360SEC-C1] | Yes — AWS Asia-Pacific (Sydney) AU cloud since Nov 2020 [PANAU-C1] | Yes — dedicated Asia-Pacific (Sydney) regional infrastructure [KALAU-C1] | NOT CONFIRMED — no region named on trust page [YUJAT-C1] | Yes — Australia is a Local Region Geography (Sydney, Melbourne); Product Terms + Multi-Geo + ADR for Teams/SharePoint/OneDrive [MSDR-C1] [MSDR-C2] | Yes — admin-selectable Australia storage region [ZOOMAU-C1] |
| **Published WCAG position** | **2.2 AA** across five products, Level Access audited, VPATs complete (29 Apr 2026) [E360A-C1] [E360A-C2] | **2.1 AA**; conformance report on request, not published [PANA-C1] [PANA-C2] | VPAT published [KALVPAT-C1] — level NOT VERIFIED in this research | **Partial** 2.2 A and AA per independent university accessibility statement [YUJA-C1] | Microsoft accessibility programme referenced in service description [MSSTR-C1] — product-level WCAG 2.2 conformance NOT VERIFIED | NOT RESEARCHED |
| **LTI 1.3 / Advantage** | LTI Advantage certified via 1EdTech (Deep Linking, NRPS, AGS) [E360LTI-C1] | **LTI Advantage Complete** certification [PANLTI-C1] | LTI Advantage certified [1EDT-C1] | NOT CONFIRMED [1EDT-C1] | Microsoft 365 LTI registers as an LTI 1.3/Advantage tool in Blackboard [MSLTI-C1] | NOT RESEARCHED |
| **Blackboard Ultra specifics** | LTI 1.1 + LTI 1.3 deep linking + REST API (course linking, roster sync, analytics); vendor supports migrating **to LTI 1.1 only** [E360BB-C1] [E360BB2-C1] [E360BB3-C1] | LTI 1.3 for Blackboard Ultra documented; inherits Blackboard course roles and permissions [PANBB-C1] [PANBB2-C1] | NOT RESEARCHED in depth | NOT RESEARCHED in depth | Microsoft 365 LTI app; classic Teams Classes/Meetings LTI **sunset 15 Sep 2025** [MSLTI-C2] | NOT RESEARCHED |
| **Provisioning path (REQ-025, Principle 12)** | REST APIs and SDKs published; roster sync via REST API integration [E360API-C1] [E360BB3-C1] | Community evidence of SOAP `CreateUser`/`SyncExternalUser` and requests for SCIM [PANSCIM-C1] — current REST provisioning capability NOT CONFIRMED | NOT CONFIRMED | API documented [YUJAAPI-C1] — granularity NOT CONFIRMED | Entra ID native — strongest position by construction; SCIM is Microsoft's own pattern [MSSCIM-C1] | NOT RESEARCHED |
| **Captioning engine** | AWS Transcribe; custom dictionaries **configured by Echo360 Support on the institution's behalf**, not self-service [E360ASR-C1] | Site-level custom ASR/OCR dictionaries; ASR stated 90–95% accurate depending on audio, human 99%+ [PANCAP-C1] [PANCAP2-C1] | REACH service (not verified in this research) | Auto-captions with download; accuracy claim NOT FOUND [YUJA-C1] | Transcripts for uploaded video included across plans incl. Education [MSSTR-C1] | Live transcription ~90% accuracy dependent on audio and accent, per AARNet [ZOOMAU-C1] |
| **Multi-track audio** | NOT CONFIRMED | **Not available** — vendor community evidence [PANMC-C1] | NOT CONFIRMED | NOT CONFIRMED | Not applicable | Not applicable |
| **Room hardware dependency** | Universal Capture software (Win 10+, macOS 10.14+) or Pro/Pod appliances; SCHD appliance EOL 30 Dec 2020 [E360UC-C1] [E360UC2-C1] [E360SCHD-C1] | Certified Epiphan Pearl family (Nexus, Mini, Nano) [PANEPI-C1] [EPIPN-C1] | Kaltura Lecture Capture / Capture desktop recorder actively maintained [KALLC-C1] [KALCAP-C1] | NOT CONFIRMED | Teams Rooms devices; Teams Rooms Pro **US$40/room/month paid yearly** [MSTRP-C1] | NOT RESEARCHED |
| **Public review position** | G2 4.3/5, 56 reviews | G2 4.3/5, 246+ reviews | G2 4.3/5, 118 reviews | G2 4.5/5, review count not captured | n/a | n/a |
| — *review caveat* | All four figures derive from a single aggregated search result, not from individually fetched G2 pages, and are reported here as **low-confidence**. Review volume differs by a factor of four; the scores are not comparable at that spread. | | | | | |

### 2.3 Australian and Sector Context

**AARNet** is the Australian academic and research network and is described as "a leading Zoom APAC Reseller for education in Australia", delivering licensing and support across Zoom products, hosting Zoom servers on its network, and providing local support and cloud recording integration with its CloudStor storage application [AARN-C1]. AARNet also acts as an advocate for feature development with Zoom on behalf of Australian education customers [ZOOMAU-C1]. For Project 002 this matters in one concrete way: **if Zoom is retained for Learning Delivery under FR-008, the AARNet channel is the relevant commercial route, not a direct Zoom agreement.** Grace Tanaka should confirm the university's current Zoom contracting path as part of D-1.

**CAUDIT** (Council of Australasian University Directors of Information Technology) operates an IT Procurement Community of Practice and a strategic partner programme, and has an established MoU with AARNet since October 2017 [CAUD-C1]. No evidence was found of a CAUDIT panel or aggregated agreement specifically covering lecture capture platforms. **This is a gap in this research, not a finding of absence** — CAUDIT agreements are member-facing and would not necessarily be visible publicly. Recommended action: Grace Tanaka to query CAUDIT directly before criteria are issued to suppliers (2026-08-31). The route is settled as a competitive tender (Conflict C-5), so an existing sector arrangement would not change the route — but it could change the supplier set, the terms available, and the baseline against which pricing is judged.

**Comparator sector arrangement (US)**: MEEC (a US higher-education purchasing consortium) awarded master agreements for lecture capture systems under RFP #0004-2023 covering **1 July 2023 to 30 June 2029** to five suppliers — Echo360/Turning Tech Intermediate, Kaltura, Panopto, Enghouse Mediasite and YuJa — as a multi-award allowing member institutions to select their preferred vendor [MEEC-C1]. Pricing is not published; members request agreement copies from the MEEC office [MEEC-C1]. This is included as **evidence of market structure**, not as a procurement route available to UoF. Its useful signal is that a competitive sector process in this market produced *five* viable awardees, which supports the contestability position in Conflict C-5.

**Australian institutional movement observed** (directional evidence only, small sample):

- **University of Queensland** decommissioned Kaltura and transitioned to Echo360 as its primary video platform. Kaltura was switched to read-only on 3 June 2024, vendor migration completed by 1 July 2024, a supplementary higher-quality migration ran November–December 2024, and Kaltura was decommissioned on 31 December 2024. Stated rationale: "Rationalising our video systems will simplify the environment for teaching staff, and students, reduce support complexity, and save money." [UQ-C1]
- **University of South Australia** moved from a customised on-premises Echo360 lecture capture system to Panopto's video cloud [PANUNISA-C1]. *(Source is a Panopto-published blog — vendor material, treated as a claim of fact about the customer, not as an endorsement.)*

> These two movements point in opposite directions. That is the honest reading: **there is no sector consensus to defer to.** The evaluation must be decided on UoF's own criteria, which is precisely what BR-004 requires.

### 2.4 Published Price Evidence (Sector Comparators Only)

There is **no published list price for any of the four specialist capture platforms.** Panopto's own pricing page states: "Panopto is an enterprise platform. Your deployment—the number of users, integrations, add-ons, and deployment model—is unique. So is your price." No tiers, storage figures, user counts or prices are disclosed [PANPRICE-C1]. YuJa likewise does not publish pricing. This is the norm for the segment and it is why §7.1 concludes the TCO cannot be completed from public sources.

The only genuine published price points located are **UK public-sector contract award notices for the same products**. They are reproduced here as *order-of-magnitude sector comparators for institutions of broadly comparable scale*, and for no other purpose:

| Buyer | Supplier | Published value | Term | Confidence | Source |
|---|---|---|---|---|---|
| University of Derby | Panopto | **£393,572** | 1 Sep 2024 – 31 Aug 2027 (3 years) | Medium — value and dates from search result summary; **the Contracts Finder notice itself returned HTTP 403 and could not be fetched directly** | [UKC-C1] |
| University of Sheffield | Echo360 | **£195,000** (reported as £195K) | Not captured | Low — award value from an aggregator summary; notice not fetched | [UKC-C2] |
| Royal Holloway, University of London | Panopto | **£172,000** (reported as £172K) | Not captured | Low — award value from an aggregator summary; notice not fetched | [UKC-C2] |
| University of Southampton | Panopto EDU platform licences | Value not captured | 4 Jun 2021 – 3 Jun 2024 | Low — dates only | [UKC-C1] |

**How these figures must and must not be used:**

- ✅ They establish that an institution-wide capture platform licence in this market is a **six-figure annual-order commitment**, not a marginal add-on. That is a legitimate input to the order-of-magnitude sanity check on any quote UoF receives.
- ❌ They must **not** be converted to AUD and presented as a UoF cost estimate. Different jurisdiction, different FTE, different scope, different bundled modules, different negotiation, different year.
- ❌ They must **not** be used to compare Echo360 against Panopto. Sheffield's £195K and Royal Holloway's £172K are different institutions of different size with different scope. Reading a vendor price difference out of them would be a category error.
- ⚠️ The 403 on the primary Contracts Finder notice means the Derby figure is second-hand. It should be re-verified before it appears in any paper going to Operations Committee.

### 2.5 Microsoft Published Pricing (The One Costable Component)

| Item | Published price | Notes | Source |
|---|---|---|---|
| Microsoft Teams Rooms Pro | **US$40.00 per room per month, paid yearly** | Microsoft's own product page. Includes AI-powered audio/video, remote room management, AI-enhanced device management. No education-specific price shown on the page. | [MSTRP-C1] |
| Microsoft Teams Rooms Basic | Not shown on the fetched page | Referenced via a "See plans and pricing" link not retrieved | [MSTRP-C1] |
| Teams Premium | Reported at US$10 per user per month in secondary sources | **LOW CONFIDENCE — not verified against a Microsoft-published page.** Education pricing for Teams Premium was not located. Do not use this figure without verification. | — |
| Microsoft 365 A1/A3/A5 | Not established | The relevant question is not list price but **what UoF already holds** — this is D-2 and it is outstanding | — |

> **The single most consequential unknown in this whole document is D-2.** If UoF's A-series entitlement already includes the necessary Teams and Stream capability, the Microsoft option's marginal licence cost is confined to Teams Rooms Pro (or Basic) and any Teams Premium uplift for organizer identities. If it does not, the picture changes completely. Neither this document nor any evaluation can resolve that from the outside.

---

## 3. Category 1 — Lecture Capture and Video Management Platforms

**Requirements addressed**: REQ-004, REQ-008, REQ-009; BR-001; FR-001 to FR-006, FR-008, FR-010 to FR-013, FR-018; NFR-P-001, NFR-P-002, NFR-A-001, NFR-A-002, NFR-A-003, NFR-U-001, NFR-U-002, NFR-M-001; INT-002, INT-003, INT-006.

**Why this category**: FR-001 (automatic scheduled capture from timetable data) and FR-002 (publication to the unit site within 4 hours) are together the definitional capability of the project. BR-001 requires exactly one primary platform for it.

### 3.1 The Discriminating Capability: Timetable-Driven Automatic Capture

This is where the candidates genuinely separate, and it is worth being precise about *why*.

A purpose-built lecture capture platform models a **capture schedule** as a first-class object: a room, a time, a unit, a device, recurring across a teaching period, reconciled against timetable change. Echo360 documents "linking a section and capture schedule to an LMS course" and a REST API integration that "automates course linking and scheduling" [E360API-C1] [E360BB3-C1]. Panopto documents scheduled recording against certified room hardware [PANEPI-C1] [EPIPN-C1]. Kaltura maintains a distinct Lecture Capture product line with active releases [KALLC-C1].

A meeting platform models a **meeting**: an organizer, invitees, a start time. Recording is a property of the meeting, controlled by the organizer. Microsoft's documentation is unambiguous that the auto-recording policy "gives the organizer access to" the option and that organizers "must manually enable" it per meeting; the only automation path is a meeting template requiring Teams Premium [MSAR-C1] [MSAR-C2].

**Architectural consequence for Option C (Microsoft)**: to satisfy FR-001, the university would have to build a service that, for every timetabled session in a capture-equipped room, creates a Teams meeting with the correct organizer, room resource and enforced auto-record template; keeps it reconciled with Allocate+ within the INT-002 one-hour SLA; and handles cancellation without generating spurious recordings (FR-001 acceptance criterion 3). Nothing in the Microsoft stack supplies this. It is an integration build of non-trivial scope, and it must appear as a line item in the BR-003 model — not be treated as configuration.

This is the substance of Dr. Moog's stated position that "a general-purpose meeting-recording tool and a purpose-built lecture capture platform are not the same product class" [STKE-C9]. The published documentation supports the *distinction*. It does not by itself decide whether the distinction is worth the price difference — that is a cost question, and the cost inputs are missing.

### 3.2 Live Delivery Overlap (FR-008, REQ-008)

FR-008 requires breakout rooms, polling and recording on the designated live-delivery platform, with recordings following the same publication path as room capture. A-7 explicitly permits this to be one platform or two bounded platforms.

- **Zoom** is the incumbent for live delivery and can store cloud recordings in Australia by administrator setting [ZOOMAU-C1]. It is procured for Australian education through AARNet [AARN-C1].
- **Teams** is already licensed and provides meeting recording with transcripts into Stream on SharePoint [MSSTR-C1].
- Retaining Zoom *and* selecting a separate capture platform is legitimate under Principle 2 provided the boundary is declared — Principle 2 requires the architecture to "state which is primary and why the others persist" [PRIN-C1], not that only one platform exist.

**Finding**: FR-008 does **not** by itself force the capture decision. Treating it as if it does would import a Learning Delivery argument into a Learning Capture decision. The evaluation should score FR-008 separately and allow a two-platform-with-declared-boundary outcome, consistent with Conflict C-1 Option 4 being retained as a genuine outcome rather than a strawman.

### 3.3 Availability, Performance and Observability (NFR-A-001, NFR-P-001, NFR-M-001)

**Not assessable from published sources.** No vendor publishes a contractual SLA at the granularity NFR-A-001 requires — 99.9% during teaching periods, measured *separately* for capture, processing and playback, with zero planned downtime in teaching periods. This is a **negotiation item, not a research finding**, and it should be drafted into the contract terms milestone (2026-12-11) rather than scored from documentation.

The same applies to NFR-M-001 (room status dashboard, queue depth, integration health, alert routing by failure class). Every vendor markets monitoring; none publishes the specific telemetry surface. This must be demonstrated live in evaluation, not read.

> **Recommendation for the evaluation framework**: NFR-A-001 and NFR-M-001 should be **demonstration criteria with a written contractual follow-through**, not documentation-scored criteria. Documentation-scoring them will produce four identical high scores and waste the weighting.

---

## 4. Category 2 — Australian Data Residency and Sector Context

**Requirements addressed**: REQ-030; NFR-C-001; DR-006; Principle 8; risk R-013.

### 4.1 Confirmed Australian Residency Positions

| Platform | Position | Detail | Source |
|---|---|---|---|
| **Panopto** | **Confirmed** | Data centre in Sydney, Australia launched for ANZ customers; AU Cloud in AWS Asia-Pacific (Sydney) Region; "all video recordings and content stored on the customer's Panopto platform to be stored locally"; encrypted at rest and in transit; announced November 2020 | [PANAU-C1] |
| **Kaltura** | **Confirmed** | Dedicated regional infrastructure for Asia-Pacific (Sydney) among three new regions, explicitly "designed to meet data residency and performance requirements", storing data within each geography | [KALAU-C1] |
| **Microsoft 365** | **Confirmed, strongest** | Australia listed as a *Local Region Geography*; data centre locations Sydney and Melbourne; Exchange Online, SharePoint/OneDrive, Teams and Copilot all carry **P-M-A** (Product Terms + Multi-Geo + Advanced Data Residency) for Australia | [MSDR-C1] [MSDR-C2] |
| **Zoom** | **Confirmed, customer-configured** | Administrators select the region for cloud recordings; Australia activated for AARNet customers 1 February 2021; setting under Account Management → Account Settings → General ensures storage *and post-meeting processing including transcription* occur in Australia | [ZOOMAU-C1] |

### 4.2 Unconfirmed Positions — Action Required

| Platform | Status | What was and was not found |
|---|---|---|
| **Echo360** | ⚠️ **NOT CONFIRMED** | The Echo360 secure-solutions page carries US federal-sector references (Section 508, Air Force AFNIC, Marine Corps DADMS, Defense Health Agency, FEMA licences) but **no data residency, hosting region, cloud provider, or ISO 27001 / SOC 2 / IRAP statement** [E360SEC-C1]. Echo360's ASR runs on AWS Transcribe [E360ASR-C1], which implies AWS but does not establish the region. **This is a material gap for the incumbent** and directly affects R-013 and the PIA. |
| **YuJa** | ⚠️ **NOT CONFIRMED** | YuJa's own trust page references "multiple physical data center zones" and "industry-leading cloud infrastructure" but **names no region, does not name the cloud provider, and states no data residency guarantee**. It does list AES-256 at rest, TLS 1.2 minimum (1.3 default), SOC 2 Type II, GDPR, HECVAT, TX-RAMP, CSA Cyber Essentials — and **no ISO 27001** [YUJAT-C1]. A separate search result indicates YuJa hosts in AWS, but this was not confirmed on a YuJa-published page. |

> **Recommended mandatory-information request**: Before shortlisting, Procurement should require from every candidate, in writing: (a) the specific region(s) in which recordings, transcripts, captions, thumbnails and derived analytics are stored at rest; (b) the region(s) in which ASR/transcription *processing* occurs — Zoom's documentation shows this can differ from storage [ZOOMAU-C1]; (c) any sub-processor with access, and its jurisdiction; (d) whether the residency position is contractual or configurational. DR-006 requires a cross-border disclosure register per data class; that register cannot be built from vendor marketing pages.

### 4.3 The Processing-Location Trap

The Zoom evidence exposes a distinction the requirements should sharpen. AARNet's guidance is explicit that setting the Australian region "ensures that both the storage of recordings **and any post-meeting processing such as transcriptions or AI-generated summaries** all happen in Australia" [ZOOMAU-C1] — implying that without that setting, processing may occur elsewhere even where storage does not.

NFR-C-001 currently requires "Australian data residency for recordings and derived assets". DR-006 requires storage location per data class. **Neither explicitly covers transient processing location.** With every vendor now adding AI enrichment (Kaltura's REACH/AI Genie [KALAU-C1], Panopto's AI add-ons [PANPRICE-C1], Echo360's AWS-based ASR [E360ASR-C1]), the transcription and summarisation path is a genuine APP 8 surface.

> **Recommendation**: Eleanor Frame to consider a clarifying amendment to DR-006 at the next revision, extending the register to cover *processing* jurisdiction as well as storage jurisdiction. This is a requirements refinement arising from research, flagged rather than made unilaterally.

---

## 5. Category 3 — Captioning and ASR Accuracy

**Requirements addressed**: REQ-029; FR-006, FR-007; NFR-C-002 (mandatory gate); NFR-U-003 (scored); D-8; risk R-018.

### 5.1 Independent Measured Evidence

This section deliberately separates **measured evidence** from **vendor claims**, because NFR-U-003 states that "vendor accuracy claims are not accepted as evidence".

**Peer-reviewed, higher-education-specific** — Kuhn, Kersken, Reuter, Egger and Zimmermann (2024), *Measuring the Accuracy of Automatic Speech Recognition Solutions*, ACM Transactions on Accessible Computing [ASR-C3]:

- Eleven common ASR services evaluated against recordings of **Higher Education lectures**, chosen because "there is high demand for affordable and scalable transcription of lectures, with institutions required to offer equal access to all students" [ASR-C2].
- Motivated by the gap between industry accuracy claims and accessibility problems reported by Deaf and hard-of-hearing users [ASR-C1].
- Key results: "accuracy ranges widely between vendors and for the individual audio samples"; "despite the recent improvements of ASR, common services lack reliability in accuracy"; and **significantly lower quality for streaming ASR used for live events** [ASR-C1].
- Crucially for evaluation design: "even providers that achieve a relatively low average WER can show a high error rate for an individual audio sample", and "no vendor consistently reach[ed] the lowest WER across all samples" — performance depended heavily on individual speaker and acoustic environment even without strong accents [ASR-C2].
- State-of-the-art average for English is reported around **5% WER**, with the caveat that results differ for spontaneous, conversational and colloquial speech [ASR-C2].

**Industry benchmark** — 3Play Media, *2025 State of ASR* (published 20 May 2025) [3PLAY-C1]:

- 205 hours of diverse audio, over 1.7 million words, eight ASR engines plus Gemini as a multimodal LLM.
- "Error rates across all engines still fall short of meeting accessibility requirements."
- Accuracy improvement for English pre-recorded content is **plateauing**; the gap between leading engines and the rest has widened.
- Industry variation is large — sports content shows error rates **3× higher** than the best-performing verticals, attributed to noise, unscripted speech, proper nouns and unusual numerical phrasing [3PLAY-C1].
- "Human-in-the-loop workflows remain critical for captioning and transcription use cases" [3PLAY-C1].
- The prior-year (2024) study concluded "ASR alone is still insufficient for the captioning use case, especially regarding formatting and hallucinations", and flagged hallucination as a persistent problem particularly in Whisper [3PLAY-C2].

**Domain-specific evidence**: research into ASR for specialised terminology reports word error rates "from 0.087 in controlled dictation settings to over 50% in conversational or multi-speaker scenarios", with medical communication scenarios between **0.122 and 0.228 WER** [ASRMED-C1]. Commercial ASR tools "exhibited high word error rates particularly with specialized academic terminology" [ASRMED-C1].

### 5.2 Why This Directly Validates NFR-U-003 and D-8

The three findings that matter for evaluation design:

1. **The sports-content finding is the Music & Performing Arts finding.** 3Play attributes 3× error rates to unscripted speech, proper nouns and unusual phrasing conventions [3PLAY-C1]. A conservatoire teaching session — composer names, foreign-language terms, instrument and technique vocabulary, sung or played passages interleaved with speech — has precisely that profile. The generalisation is directional, not measured for music specifically, and is flagged as such. But it means a platform's *general* caption score is a poor predictor of its performance where Prof. Key's students depend on it.

2. **The individual-sample variance finding destroys single-number scoring.** Because "even providers that achieve a relatively low average WER can show a high error rate for an individual audio sample" [ASR-C2], a test set of two or three recordings will produce a *random* ranking. D-8's test set must be large enough and drawn from enough speakers and rooms to be stable. This is a design constraint on D-8 that the requirement does not currently state.

3. **The streaming-ASR finding affects FR-008.** Measured quality is significantly lower for streaming ASR used for live events [ASR-C1], and AARNet reports Zoom live transcription at approximately 90% accuracy dependent on audio quality and speaker accent [ZOOMAU-C1]. Live-delivered classes captioned in real time will not reach the standard that post-processed recordings do. Whether NFR-U-003 applies to live captions or only to published recordings should be clarified before the criteria are signed.

> **Recommendation to Dr. Moog on D-8**: the test set should span **at least 20 recordings** across both Health Sciences and Music & Performing Arts, multiple speakers, and both a large lecture theatre and a smaller room, with a human reference transcript. Fewer than that and the literature says the result will not be reproducible. This is offered as a research-derived design input; the sizing figure is a professional judgement drawn from the variance finding, not a number published in the cited studies.

### 5.3 Vendor Positions — Recorded as Claims

| Vendor | Claim / documented capability | Status |
|---|---|---|
| **Echo360** | Uses **AWS Transcribe**. Institutions set a **confidence-score threshold**; transcripts meeting or exceeding it auto-apply to the closed caption track. Supports **custom transcription dictionaries** for organisation-specific terminology, acronyms and proper nouns in AWS Transcribe format — but these "must be configured by Echo360 Support on behalf of institutions". Caption and transcript files use the **WEBVTT** standard. Documentation concedes ASR "is unlikely to meet the accuracy levels required for closed captions for hearing-impaired individuals". | [E360ASR-C1] [E360ASR-C2] — vendor documentation, and notably candid |
| **Panopto** | ASR captions "typically 90–95% accurate depending on the audio quality", human captions "at least 99% accurate". **Custom site-level dictionaries for ASR and OCR** for specialised terms and proper nouns. Notes automatic captioning is less reliable for non-native speakers, dialects and accents, and "can also struggle to accurately represent technical, disciplinary language". Integrations with 3Play Media, Rev.com and Verbit.ai for human captioning. | [PANCAP-C1] [PANCAP2-C1] [PANA-C1] — vendor claim; the 90–95% figure is unverified and is a range, not a measurement |
| **YuJa** | Auto-captions generated and downloadable; documentation notes auto-generated captions "may contain errors and must be reviewed and edited". **No accuracy percentage claim found.** | [YUJA-C1] |
| **Microsoft** | Transcript generation for uploaded videos available across plans including Education. | [MSSTR-C1] |
| **Zoom** | Live transcription "approximately 90% accuracy depending on audio quality and speaker accents"; not available in breakout rooms; transcripts saveable alongside recordings. | [ZOOMAU-C1] — reported by AARNet, a reseller, so treat as vendor-adjacent |

**Operational difference worth weighting**: Echo360's custom dictionary requires a **support ticket to the vendor** [E360ASR-C1]; Panopto's is described as a **site-level dictionary** the institution maintains [PANCAP-C1]. FR-007's acceptance criterion — that a recurring mis-transcribed discipline term can be added to a vocabulary list for future recordings — is a *self-service* expectation. A vendor-mediated dictionary satisfies the letter and fails the operational intent, and creates a standing dependency for Nina Kalimba's team (D-6). This is a small, concrete, testable difference and it belongs in the criteria.

### 5.4 Accessibility Conformance (NFR-C-002 — Mandatory Gate)

| Vendor | Published position | Assessment against the gate |
|---|---|---|
| **Echo360** | 29 April 2026: all five Echosystem solutions (EchoVideo, EchoInk, EchoEngage, EchoExam, GoReact) "compliant with the Web Content Accessibility Guidelines (WCAG) **2.2 AA** standards"; ongoing auditing and validation by **Level Access**; VPATs completed for each solution; also aligns to EN 301 549 and Section 508 [E360A-C1] [E360A-C2] | **Meets the published standard.** Strongest position found. Named third-party auditor is a meaningful quality signal. |
| **Panopto** | "regularly evaluated against **WCAG 2.1 AA** and Section 508 standards"; conformance report "available on request" [PANA-C1] [PANA-C2] | **Below the gate on published evidence.** 2.1 AA ≠ 2.2 AA. Panopto must be asked directly for a current WCAG 2.2 AA VPAT. |
| **YuJa** | "partially compliant with WCAG **2.2** Level A and AA" per an independent university accessibility statement; vendor self-evaluated using automated tools, manual testing and multi-browser validation [YUJA-C1] | **"Partially compliant" is a fail against a mandatory gate** unless the specific non-conformances are known and remediated with dates. |
| **Kaltura** | VPAT published [KALVPAT-C1] | **Level not verified in this research.** Must be obtained. |
| **Microsoft** | Accessibility commitment referenced in the Stream service description with pointers to the Trust Center [MSSTR-C1] | **Product-level WCAG 2.2 AA conformance for Stream/Teams playback not verified.** Must be obtained. |

> **Critical caveat, and it cuts both ways.** NFR-C-002 requires conformance "assessed during evaluation against the platform as it will be configured, not against a vendor conformance claim", and Principle 14 requires vendor claims to be verified rather than accepted [PRIN-C5]. Echo360's 2.2 AA announcement is a *claim* — a well-supported one with a named auditor, but a claim. Panopto's 2.1 AA page may simply lag its actual conformance. **The correct action is identical for both: obtain the current VPAT and test the student journey.** This document's finding is that the *published* positions differ materially, which is enough to justify making this a hard information request before shortlisting — not enough to disqualify anyone.

---

## 6. Category 4 — Provisioning and Integration Standards

**Requirements addressed**: REQ-025, REQ-031; NFR-I-001 (CRITICAL), NFR-SEC-001 (mandatory gate); INT-001, INT-003, INT-004; FR-016; TC-5; Principle 12; risk R-022.

**Why this category**: this is the project's highest-value platform-neutral outcome. The current state runs Echo360 provisioning on "LTI + manual CSV" with a standing manual workaround for casual academic staff [SL-C4]. R-022 rates the risk of carrying that failure into the new estate as Major in impact.

### 6.1 LTI 1.3 and LTI Advantage

| Vendor | Certification | Detail |
|---|---|---|
| **Panopto** | **LTI Advantage Complete** certification from 1EdTech [PANLTI-C1] | "LTI Advantage Complete" is awarded for certifying LTI 1.3 Core **and all three** Advantage services [1EDT-C1]. Highest published standing found. |
| **Echo360** | LTI Advantage certified through 1EdTech [E360LTI-C1] | Documents support for Deep Linking, Names and Role Provisioning Services, and Assignments and Grades Services [E360LTI-C1]. Listed in the 1EdTech directory [1EDT-C1]. |
| **Kaltura** | LTI Advantage certified [1EDT-C1] | Not researched in depth. |
| **YuJa** | **Not found** in the search of the 1EdTech directory [1EDT-C1] | YuJa's trust page states products "conform to the latest Learning Tool Interoperability (LTI) and Single Sign On (SSO) standards" [YUJAT-C1] — a vendor claim without a certification reference. **Must be verified in the 1EdTech directory directly.** |
| **Microsoft** | Microsoft 365 LTI registers in Blackboard via **Register LTI 1.3/Advantage Tool** with a published Client ID [MSLTI-C1] | Confirms LTI 1.3 registration path. |

### 6.2 Blackboard Ultra Integration Depth (INT-003, TC-2)

This is where documented capability diverges most sharply, and the finding is **adverse to the incumbent**.

**Echo360** documents three integration modes with Blackboard — LTI 1.1, LTI 1.3, and REST API [E360BB-C1]. The REST API integration for Blackboard "automates course linking and scheduling between Blackboard and Echo", "synchronizes roster data", and "delivers consolidated analytics" [E360BB-C1] [E360BB3-C1] — functionally rich. However, the same overview page carries this verbatim caveat:

> "NOTE that while migrating to LTI 1.3 may appear to be an option within Blackboard, it has not been fully tested by us. We are only supporting migrating to LTI 1.1." [E360BB-C1]

A separate Echo360 page documents creating an LTI 1.3 integration with Blackboard for Deep Linking, configuring an Analytics tool and a Deep Linking content tool, with no stated limitation [E360BB2-C1]. Echo360 also documents a deep-link tool specifically for **Blackboard Ultra** and embedding content in Ultra-enabled courses [E360BB4-C1]. And its general LTI 1.3 page notes two further limitations: "LTI 1.3 does not currently support linking to EchoVideo Course sections themselves", and there is **no automatic migration path from LTI 1.1 links to LTI 1.3** [E360LTI-C1].

**Reading of the conflict**: Echo360 *has* LTI 1.3 with Blackboard, but its own guidance steers existing customers to LTI 1.1 on migration, and section-level linking — which is how capture schedules attach to courses — is not supported over LTI 1.3. For UoF, whose current provisioning already runs on LTI plus CSV [SL-C4], this is the specific mechanism by which the CSV workaround could survive the transition. **R-022 is live for the incumbent, not only for hypothetical new vendors.**

**Panopto** documents LTI 1.3 for Blackboard Ultra directly, states that LTI 1.3 support is available for the Blackboard Ultra, Canvas, D2L and Moodle integrations, supports both Ultra and Original course views, and — significantly for FR-016 — "inherits Blackboard course roles and permissions automatically, so access control stays aligned with institutional policies without separate configuration in Panopto" [PANBB-C1] [PANBB2-C1]. It also documents batch course provisioning in Blackboard [PANBB3-C1]. Context: Blackboard announced it would no longer support Building Block (B2) integrations from June 2024, moving to LTI and REST APIs [PANBB2-C1] — so the whole market has been forced onto LTI, and Panopto appears further through that transition for Ultra.

**Microsoft**: the Microsoft 365 LTI app is the current path. Critically, "the classic Teams Classes and Teams Meetings app has sunset as of September 15, 2025" [MSLTI-C2]. The new Meetings app displays only "the previous six months and upcoming six months of meetings scheduled" [MSLTI-C2] — a rolling twelve-month window that sits awkwardly against a recordings archive with a multi-year retention schedule (DR-005). Integration also requires that the Blackboard user's Email or Institutional Email field be populated with the Entra UPN or primary email for **every course using the integration** [MSLTI-C1] — an identity-matching precondition that is real work and depends on D-7.

> **Evaluation design recommendation**: NFR-I-001 should be tested as a **hands-on gate on the university's own Blackboard Ultra instance**, specifically: (i) LTI 1.3 launch with correct role mapping for coordinator, tutor and marker; (ii) capture schedule attached to a unit at section granularity; (iii) a casual-staff appointment event producing access within 15 minutes with **no file transfer of any kind**. R-022's control is described as "tested not assumed" — these three tests are what that means concretely.

### 6.3 Provisioning APIs (REQ-025, Principle 12, TC-5)

| Vendor | Evidence found | Confidence |
|---|---|---|
| **Echo360** | "modern, stateful" REST APIs with SDKs; documented API set includes Reporting API, Capture Intake API, Capture API; REST integration performs roster sync for Blackboard [E360API-C1] [E360BB3-C1] | Medium — API existence well evidenced; **role granularity for coordinator/tutor/marker not confirmed** |
| **Panopto** | Community evidence indicates SOAP `CreateUser` and `SyncExternalUser` as the pre-population route, with users requesting "SCIM compatibility, or at least some REST API endpoints that could be called upon user provisioning" [PANSCIM-C1]. Course roles inherited from Blackboard via the LMS integration [PANBB2-C1] | **Low — this is community forum evidence of uncertain date.** Panopto has published REST APIs; whether current provisioning is REST or SOAP was not established. **Must be verified directly with the vendor.** Do not carry this into a paper as a finding. |
| **Microsoft** | Entra ID native; SCIM is Microsoft's own documented provisioning pattern [MSSCIM-C1] | High — structurally the strongest. If identity lifecycle were the only criterion, Microsoft would win it outright. |
| **Kaltura / YuJa** | Not established. YuJa publishes an API [YUJAAPI-C1] | Low |

> **Honest statement of a research limit**: I was unable to establish current, authoritative provisioning-API capability for Panopto, Kaltura or YuJa. Vendor API reference documentation is largely behind support-portal authentication, and one fetch attempt against Panopto's support site failed on a TLS certificate error. **Section 6.3 is the thinnest evidence in this document.** Given that R-022's control is a mandatory gate tested in evaluation, the practical consequence is small — the gate does the work that this research could not. But no shortlisting decision should rest on Section 6.3.

### 6.4 SSO and MFA (NFR-SEC-001 — Mandatory Gate)

No candidate was found that lacks SAML 2.0 / OIDC SSO. YuJa states conformance to "the latest ... Single Sign On (SSO) standards" [YUJAT-C1]; Panopto lists SSO among enterprise security features [PANPRICE-C1]; Microsoft is Entra-native by construction. **This gate is unlikely to eliminate anyone**, which is a useful finding in itself.

The real risk NFR-SEC-001 addresses is not "can the platform do SSO" but "**does a local account path exist at all**". The requirement is explicit: "Authentication failure must not fall back to any local credential path — no such path may exist" (INT-004). Most video platforms retain a local administrator account for break-glass and for service integrations. **The evaluation must ask specifically: can every local and service account be eliminated or federated, and if not, exactly which ones remain and why.** Two tools in the wider estate already breach REQ-031 [PC-C5]; the requirement's own warning that "this procurement shall not add a third" is the point.

Similarly for NFR-SEC-002 and INT-006: per-device identity for room appliances, explicitly not shared administrative credentials. Given that legacy shared admin accounts in the AV/capture estate are precisely what holds "restrict administrative privileges" at ML1 [PC-C1], **the appliance authentication model should be a documented information request to every vendor.** No published vendor material addressing this was found for any candidate.

### 6.5 Open Source — Assessed and Not Shortlisted

**Opencast** is the established open-source lecture capture platform in higher education, with a European university consortium behind it. It is named here for completeness of the build/buy/adopt analysis.

**Recommendation: do not shortlist.** Reasoning, stated plainly:

- The operational burden lands on the AV and Digital Learning Support teams that R-008 already identifies as capacity-constrained for the single July 2027 window, and that D-6 identifies as unresourced for caption correction.
- Principle 13 requires automation to be documented, version-controlled and executable by more than one person — the current estate already fails this on course cloning [PP-C7]. Adding a self-hosted platform to that operating model would compound a known weakness.
- BC-2 permits one cutover window. A self-hosted deployment reaching production-grade for 100% of timetabled lectures by July 2027 is not a credible schedule alongside the pilot requirement in BR-006.
- NFR-C-002 and NFR-U-003 would place the university itself in the position of evidencing WCAG 2.2 AA conformance and caption accuracy, rather than requiring it of a supplier.

> **Honesty note**: I did **not** conduct primary research into Opencast's current release, community health, LTI 1.3 support or Australian deployments in this pass. The recommendation above is a reasoned screening judgement on operating-model grounds, not an evidenced capability assessment. If the steering committee wants open source genuinely evaluated rather than screened out, that is a separate piece of work and should be commissioned as such.

---

## 7. Build vs Buy and Total Cost of Ownership

### 7.1 Why the 3-Year TCO Cannot Be Completed — Stated Plainly

**This document does not contain a completed TCO, and producing one would be misleading.** There are four specific blockers, all known and all owned:

| Blocker | What is missing | Owner | Due | Consequence |
|---|---|---|---|---|
| **D-1** | Echo360 and Zoom contract values, terms, renewal dates | Grace Tanaka | 2026-08-14 | No baseline to compare against; BR-003's "flat or reduced" test has no denominator |
| **D-2** | Microsoft entitlement position — what capture/streaming capability is already licensed | Cassandra Rhodes | 2026-08-14 | The Principle 19 argument is untestable. This is the **single highest-leverage missing input in the project** |
| **D-3** | Appliance inventory — models, age, patch status, telemetry capability | Marcus Fairlight | 2026-08-21 | The largest variable cost is unquantified; R-007 and R-011 unassessable; TC-4 cannot be applied |
| **NFR-S-001 / Entity 1** | Archive volume and growth rate | Eleanor Frame | 2026-08-28 | Storage cost, migration cost and export throughput all unmodellable |

Additionally, and independently of UoF's own data: **no specialist capture vendor publishes list pricing.** Panopto states directly that price depends on users, integrations, add-ons and deployment model and is quoted per customer [PANPRICE-C1]; YuJa is likewise quote-only. So even with perfect internal baselines, the "buy" columns require **actual quotes**, obtained through Procurement under BC-4.

> **Recorded position**: any 3-year TCO produced before 2026-08-28 would be an invented number wearing a table. ARC-002-REQ deliberately left the budget section unpopulated for exactly this reason — "values are deliberately not estimated in advance of sourced data, because an invented baseline would propagate into the business case". **This document holds that line.** R-006 is the highest-inherent-score risk in the register precisely because five other assessments depend on it.

### 7.2 What the Cost Model Must Contain (Structure, Not Values)

Delivered here so that the model can be built the moment the baselines land, and so that every option is costed identically (Conflict C-2, Option 3).

| Cost line | Buy (specialist SaaS) | Configure (Microsoft) | Hybrid (discipline exception) | Source status |
|---|---|---|---|---|
| Platform licence, Y1–Y3 | Quote required | Marginal uplift on existing entitlement — **requires D-2** | n/a | Unavailable |
| Teams Rooms licensing | n/a | **US$40/room/month Pro, paid yearly — PUBLISHED LIST** [MSTRP-C1] × room count (D-3) | n/a | **Published list price; room count unavailable** |
| Teams Premium for organizer identities | n/a | Required for enforced auto-record templates [MSAR-C2]; unit price **NOT VERIFIED** | n/a | Unavailable |
| Capture appliance — required regardless | Estate age driven | Estate age driven | n/a | Unavailable (D-3) |
| Capture appliance — decision-caused | Vendor-certified hardware where estate incompatible | Teams Rooms devices where rooms lack them | Multi-camera + audio (§10) | Unavailable (D-3) |
| Integration build | INT-001 to INT-006 against a platform with native scheduling | INT-001 to INT-006 **plus** a timetable-to-Teams-meeting scheduling service (§3.1) | Publish path to unit site | Estimable after selection |
| Archive migration | INT-007 | INT-007 | n/a | Unavailable (volume) |
| Storage and processing growth | Rises with coverage to 100%, falls with retention applied (NFR-S-001) | SharePoint/OneDrive storage model | Large files — multi-camera, high-bitrate audio | Unavailable |
| Caption correction capacity | FR-007 workload; self-service vs vendor-ticket dictionary (§5.3) | FR-007 workload | Highest per-minute correction burden (discipline vocabulary) | Unavailable (D-6) |
| Dual-running contingency | R-020 fallback if incumbent export terms restrictive | Same | n/a | Unavailable (D-1) |
| Training and transition | Nina Kalimba | Nina Kalimba | Specialist AV training | Unavailable |

### 7.3 Sensitivity Analysis — The Variables That Actually Decide It

Since values are unavailable, the useful analysis is **which variable dominates**. Three do:

1. **Room count requiring physical intervention (D-3).** This is the dominant swing variable across every option. At US$40/room/month list [MSTRP-C1], the Microsoft room-side licence alone scales linearly with the estate — 100 rooms is a materially different proposition from 30. And under any option, if the estate needs replacing, "it needs replacing under every option" (R-007). Conflict C-2's required split between "required regardless" and "decision-caused" is the only way to stop this variable distorting the comparison.

2. **Microsoft entitlement (D-2).** Binary in effect. If capture-relevant capability is already held, Option C's licence delta is small and Principle 19 bites hard. If not, Option C is a new purchase competing on price with purpose-built platforms while carrying an integration build they do not need.

3. **Archive volume (NFR-S-001).** Drives migration effort, export throughput feasibility against the July window, storage cost, and the value of applying the retention schedule first (R-014's control on R-020). The retention schedule is the one lever that *reduces* this variable, and D-5 controls it.

**Risk-adjusted contingency guidance** — offered as method, not as a costed figure:

| Option class | Suggested contingency | Reasoning |
|---|---|---|
| Buy (specialist SaaS) | +10% on licence, +20% on integration | Licence is quoted and contractible; integration effort is the historically underestimated element |
| Configure (Microsoft) | +30% on integration | The scheduling service (§3.1) is a build with no vendor-supplied reference implementation, and the auto-record constraint was discovered in documentation rather than disclosed in a product datasheet |
| Appliance refresh | +20% | Physical works in a fixed window with a capacity-constrained team (R-008) |
| Discipline exception | +25% | Venue-specific AV design; no standard product (§10) |

These percentages are **professional judgement, not sourced figures.** They are offered so Finance has a starting point to argue with, and should be replaced by Vernon Ostinato's own contingency policy if one exists.

### 7.4 Build — Rejected at Screening

**Recommendation: do not build a custom lecture capture platform.** Not modelled in detail, because the screening test fails on four independent grounds:

- **Market maturity.** Five suppliers held a competitively awarded US consortium master agreement for this exact capability [MEEC-C1]. This is a Product-stage commodity, not novel capability.
- **Principle 19 and Principle 18.** Building where a mature market exists inverts the governance intent.
- **Schedule.** BC-2 permits one cutover window (July 2027), preceded by a Semester 1 2027 pilot (BR-006). A custom build cannot credibly reach 100% coverage, WCAG 2.2 AA, 99.9% availability and a captioning pipeline on that timeline.
- **Whole-of-life.** BR-003 requires cost flat or reduced over five years. A custom build front-loads capital and creates a permanent maintenance obligation against a capability the market supplies.

> **The one nuance**: the Microsoft option is **partially** a build. The scheduling service in §3.1 is bespoke integration the university would own, maintain and depend on for FR-001. It should be evaluated with the same scepticism a full build would attract — including who maintains it, whether two people can run it (Principle 13), and what happens when Microsoft changes the meeting API.

---

## 8. Hardware and Appliance Requirements

**Requirements addressed**: TC-4; INT-006; NFR-SEC-004; NFR-A-002; BR-008; risks R-007, R-008, R-011, R-016.

**Why this section exists**: lecture capture is the only L&T capability with a significant physical estate behind it [STKE-C3]. A licence-only comparison structurally omits the largest variable cost — this is the substance of Conflict C-2.

### 8.1 Vendor Hardware Dependency by Option

| Option | Room-side model | Hardware dependency | Cost character | Source |
|---|---|---|---|---|
| **Echo360** | **Universal Capture** software on Windows 10+ / macOS 10.14+, *or* on Pro and Pod appliances via the UC:Device interface — a deliberately consistent interface across hardware and software | **Lowest hardware lock-in of the specialists.** Software capture can run on a room PC. Legacy **SCHD appliance reached End of Software Support 1 Apr 2020 and End of Life 30 Dec 2020** | Potentially low marginal hardware cost if rooms have PCs; **any SCHD units still in the estate are unsupported and must be replaced or removed** (NFR-SEC-004 prohibits retaining unpatchable appliances as exceptions) | [E360UC-C1] [E360UC2-C1] [E360UC3-C1] [E360SCHD-C1] |
| **Panopto** | Remote recorder software plus **certified Epiphan Pearl family** (Nexus, Mini, Nano). Pearl Nexus records and streams up to 3 channels of 1080p with SDI, HDMI, USB, SRT and NDI video inputs and XLR, USB and 3.5mm audio inputs, with cloud management | Certified-hardware path is a strength for reliability and a cost if the estate lacks compatible devices | Capital per room where Pearl units are required; Panopto certification means the integration is tested rather than improvised | [PANEPI-C1] [PANEPI2-C1] [EPIPN-C1] |
| **Kaltura** | Kaltura Lecture Capture product plus Kaltura Capture desktop recorder; both actively maintained (Lecture Capture release 14 Dec 2025; Capture 5.2.3 on 4 Dec 2025) | Not established in this research | Unknown | [KALLC-C1] [KALCAP-C1] |
| **YuJa** | Not established | Not established | Unknown | — |
| **Microsoft** | **Teams Rooms devices**, licensed per room | **Highest and most explicit recurring room-side cost** — Teams Rooms Pro at US$40/room/month paid yearly | **The only room-side cost with a published list price.** Recurring opex per room, not one-off capex — a structurally different cost shape from appliance capital | [MSTRP-C1] |

### 8.2 The Finding for R-011

The cost shapes are **not comparable line for line**, and presenting them as if they were will mislead Operations Committee:

- Specialist platforms concentrate room-side cost in **capital** (appliances, refreshed on a multi-year cycle), with the licence covering the platform.
- The Microsoft option concentrates room-side cost in **recurring opex** (Teams Rooms licences per room per month, indefinitely), on top of device capital.

Over five years, a per-room recurring licence compounds in a way an appliance refresh does not. **BR-003's five-year model must express both on the same basis** — which means the Microsoft option's room licensing must be modelled across the full five years and included in the "decision-caused" column, because it is entirely a consequence of the platform decision.

> **This is a concrete, sourced contribution to Conflict C-2.** Vernon Ostinato's exposure is not only "will appliances need replacing" but "does this option convert a periodic capital cost into a permanent per-room subscription". Both belong in the split.

### 8.3 Essential Eight Implications (BR-008, NFR-SEC-004)

Three research findings bear directly on the E8 workstream:

1. **The SCHD end-of-life date is a hard finding.** End of software support 1 April 2020, end of life 30 December 2020 [E360SCHD-C1]. If the D-3 inventory finds SCHD units in service, they are more than six years past software support. NFR-SEC-004 states appliances that cannot be patched "shall be identified in the inventory and either replaced or removed from service — not retained as exceptions". **This is likely to be the single most actionable output of the D-3 inventory, and it is independent of the platform decision.**

2. **Software capture changes the patching problem rather than solving it.** Echo360's Universal Capture running on a room PC [E360UC2-C1] moves the OS patching obligation onto the standard managed Windows/macOS estate — which is *better*, because that estate presumably already has a patching regime. It does not remove the obligation, and NFR-SEC-004's 48-hour critical remediation SLA still applies to the room PC.

3. **Per-device identity is unevidenced across the board.** INT-006 requires per-device identity, "explicitly **not** shared administrative credentials". No published vendor documentation was found addressing appliance authentication for any candidate. Given that shared admin accounts in the AV/capture estate are the specific reason "restrict administrative privileges" sits at ML1 [PC-C1], this must be a written information request, not an assumption.

### 8.4 What Cannot Be Concluded

- Whether UoF's existing appliances are compatible with any candidate — **requires D-3**.
- The proportion of refresh that is "required regardless" versus "decision-caused" — **requires D-3**.
- Whether A-3 (appliances can report health telemetry centrally) holds — **requires D-3**. If it fails for older appliances, it "would then become a replacement driver", per the assumption's own validation note.
- Peak concurrent capture load (NFR-P-001) — requires the timetable extract and appliance inventory.

---

## 9. Category 5 — Data Portability and Exit

**Requirements addressed**: REQ-034; NFR-I-002 (mandatory gate, elevated to MUST_HAVE on the authority of Principle 9); FR-017; FR-015; INT-007; DR-007; A-10; risks R-020, R-012.

### 9.1 The Market-Wide Finding

**No vendor researched publishes bulk export of media plus captions plus metadata as a self-service, standing, no-fee capability.** This is not a gap in the research; it is the state of the market, and it is the most important finding in this section.

NFR-I-002 requires export "at any time and on termination, without additional fee and without vendor assistance being required". FR-017's acceptance criteria include "no additional fee **or vendor assistance** is required". On the published evidence, **no candidate clearly meets that standard today.**

### 9.2 Evidence by Vendor

| Vendor | Export evidence | Assessment against NFR-I-002 |
|---|---|---|
| **Panopto** | Individual caption download in WebVTT/text from the viewer and settings [PANEXP2-C1]. For full migration, a **data extract is requested from Panopto**, takes **3–4 weeks**, and is delivered as **access to an AWS S3 bucket** [PANEXP-C1]. Community discussion indicates bulk download capturing all streams and source files is not currently available in a single self-service action [PANEXP3-C1] | **Vendor-assisted, not self-service.** Meets the *format* expectation for captions; the 3–4 week lead time and request-based process are material to the July 2027 window (INT-007). **Fails the "without vendor assistance" test on published evidence.** |
| **Echo360** | Caption and transcript files use the **WEBVTT** standard [E360ASR-C2] — an open, documented format satisfying the caption half of NFR-I-002. Published REST APIs and SDKs exist for data transfer [E360API-C1]. **No published bulk export or termination-assistance documentation found** | **Format: satisfied for captions. Bulk export: UNKNOWN.** This is exactly the uncertainty A-10 records and R-020 rates. **D-1's contract review is the only way to resolve it.** |
| **Kaltura** | YuJa publishes a Kaltura migration checklist for requesting a data extract [YUJAMIG-C1]. UQ's Kaltura-to-Echo360 migration was executed as a **vendor migration** with media re-linked to Blackboard, but the UQ page provides no information about bulk export capability or costs [UQ-C1] | **Vendor-assisted.** The UQ case demonstrates migration *is* achievable at institutional scale, which is a meaningful practical reassurance even without published terms. |
| **YuJa** | Users can download auto-captions for their own media [YUJA-C1]; custom metadata managed via the Admin Panel [YUJAMETA-C1]; an API is published [YUJAAPI-C1]. YuJa publishes migration checklists for **Panopto, Kaltura and Mediasite** requesting data extracts from those vendors, with a Mediasite extract quoted at **2–3 weeks** to transfer to a YuJa S3 bucket [YUJAMIG-C1] | **Inbound migration is a well-developed YuJa capability. Outbound export from YuJa was not evidenced** — a notable asymmetry. |
| **Microsoft** | Videos stored in SharePoint/OneDrive with "admin control of storage, management, compliance, governance, & life cycle capabilities" [MSSTR-C1]. Files are standard objects in the tenant | **Structurally the strongest position.** Content sits in a general-purpose file platform the university already administers, rather than in a video-platform silo. Caveat: the LTI Meetings app displays only a rolling ±6-month window of meetings [MSLTI-C2], so *course-context* association is time-bounded even though the *files* are not. |

### 9.3 The Asymmetry That Should Shape the Negotiation

Every specialist vendor invests in **inbound** migration tooling — YuJa publishes step-by-step checklists for extracting from three named competitors [YUJAMIG-C1]; Kaltura migrated UQ's content into Echo360 as a vendor exercise [UQ-C1]. None publishes equivalent **outbound** tooling.

This is rational commercial behaviour and it is not a scandal. But it is exactly the dynamic R-012 describes: "a supplier's pricing power at renewal is a function of how expensive leaving has become". The practical implication for Grace Tanaka:

- The *counterparty* has a documented, industrialised process for helping UoF leave its **current** vendor. That is leverage available **now**, during selection.
- Once migrated, UoF becomes the customer whose exit is undocumented.
- **The moment of maximum leverage on exit terms is before signature. It never returns.**

### 9.4 Recommended Contractual Positions

Derived from the evidence above, for Grace Tanaka's contract terms milestone (2026-12-11):

1. **Termination assistance as a priced, scoped, time-bound obligation** — not "reasonable assistance". Specify: full media in a widely supported open container, captions in WebVTT or SRT, transcripts, and metadata sufficient to associate each recording to unit, session and date **without proprietary tooling** (FR-017 acceptance criterion 2).
2. **A maximum elapsed time for a full export**, benchmarked against the 3–4 weeks evidenced for a Panopto extract [PANEXP-C1] and 2–3 weeks for Mediasite [YUJAMIG-C1]. INT-007 must complete inside the July 2027 inter-semester break; a 4-week vendor-side lead time consumes it entirely.
3. **Explicit no-fee language covering egress**, including any cloud storage egress the vendor passes through.
4. **A contractual right to test export annually**, not only at termination — Principle 9 requires export capability to be "tested periodically, not only at the point of exit" [PRIN-C4 context].
5. **A practical export test during evaluation** on a real sample producing media, captions and metadata together — R-020's control, and NFR-I-002's own validation requirement.

### 9.5 On the Incumbent (A-10, R-020)

**A-10 remains unvalidated and this research cannot validate it.** Echo360's contractual export terms are not public. The WEBVTT finding [E360ASR-C2] confirms the caption format is open; it says nothing about bulk retrieval rights, throughput or fees.

R-020's trigger list includes "export technically available but excluding captions or metadata". **The specific test that resolves this**: can Echo360 produce, in one operation, the media *and* its WEBVTT captions *and* the unit/session/date association, for the full in-retention archive, without a fee? Anything less strands part of the archive.

> **This is the highest-value single question in the entire D-1 contract review.** It determines whether BR-007 is executable, whether the retention schedule can be applied at the natural point (Conflict C-4), and whether the university's ability to rationalise anything survives (R-020's fourth consequence). It should not wait behind the platform argument.

---

## 10. Category 6 — Multi-Camera and High-Fidelity Performance Capture

**Requirements addressed**: REQ-010; FR-009 (COULD_HAVE, institutionally); BR-005 (SHOULD_HAVE, with the *decision* MUST_HAVE); UC-5; Principle 4; Conflict C-6; risk R-006 (funding).

### 10.1 The Core Finding

**The mainstream lecture capture market does not serve this requirement, and the gap is specific and identifiable.**

The clearest single piece of evidence: Panopto community documentation indicates **multi-track audio is not currently available in Panopto**, with users reporting an inability to run multiple audio tracks [PANMC-C1]. Panopto does support multiple cameras — additional cameras plugged into the recording device are recognised and recorded automatically synced [PANMC2-C1] — but for distributed recording "at least one device needs to record a primary audio stream, as secondary-only recordings will not include audio" [PANMC-C1].

For a music performance this is the wrong shape. Multi-camera video is the *easy* half. The hard half is a **multi-channel, high-fidelity, low-noise audio path** — spot mics, section mics, a stereo pair, a discrete mix — captured as separate tracks so it can be mixed after the fact. A single primary audio stream from a lecture-capture appliance is not a performance recording.

Equivalent multi-track audio capability for Echo360, Kaltura and YuJa was **not established** in this research. The absence of evidence is not evidence of absence — but given Panopto's position and the product category's design intent, the working assumption that the mainstream platforms treat audio as one channel should be **tested rather than presumed either way** during evaluation.

### 10.2 Specialist Options Identified

| Option | Capability | Fit for FR-009 | Source |
|---|---|---|---|
| **Epiphan Pearl Nexus** | Records and streams **up to 3 channels of 1080p** with SDI, HDMI, USB, SRT and NDI video inputs and **XLR, USB and 3.5mm audio inputs**; cloud management tools | Strong. XLR inputs mean professional microphones connect directly. **Already Panopto-certified** [PANEPI-C1], so the publish-to-unit-site path (FR-009 criterion 2) is a supported route rather than an improvisation | [EPIPN-C1] [PANEPI-C1] |
| **Epiphan Pearl (family)** | Can capture **perfectly synchronized video at 1080p30 from up to six sources**; Pearl Mini offers the same production functionality in a portable chassis; Pearl Nano for small-scale events | Strong for multi-angle. Six synchronised sources exceeds the likely need for a recital venue | [EPIP2-C1] [PANEPI-C1] |
| **Epiphan EC20 PTZ camera** | 4K, AI tracking; supports **Dante**, HDMI, SDI and USB; integrates with Q-SYS and Crestron | Useful where automated tracking of a performer or ensemble is wanted without an operator | [EPIPEC-C1] |
| **Dante networked audio** | "one of the easiest methods of capturing live recordings with a large number of audio channels" | **This is the component that actually answers the high-fidelity half of FR-009.** Precedent: the University of North Texas College of Music moved recording and streaming to a Dante network, handling roughly **1,000 events annually** including multi-camera video shoots, live streaming, classical recitals and jazz performances | [DANTE-C1] [DANTE2-C1] |

### 10.3 Recommended Architecture for the Exception

A **hybrid**: specialist capture hardware at the venue, publishing through the core platform.

```
Named venue (Music & Performing Arts)
  ├─ Multi-camera video ──────┐
  ├─ Dante multi-channel audio ├─→ Epiphan Pearl (or equivalent)
  └─ Operator / AI tracking ───┘         │
                                          ├─→ Edit across sources where required (UC-5 Alt 3a)
                                          │
                                          └─→ Core capture platform
                                                    │
                                                    └─→ Unit site in Blackboard Ultra
                                                        (same identity, same enrolment,
                                                         same route as core capture)
```

**Why this satisfies Principle 4**: specialist need justifies a different *tool*, never a different *architecture* [PRIN-C2]. The specialist hardware sits at the edge; identity, enrolment, access and publication all flow through the core platform. FR-009's third acceptance criterion — access derives from the same identity and enrolment model — is satisfied by construction. There is no separate portal, no separate identity store, no separate privacy posture.

**Practical consequence for the core platform decision**: whichever core platform is selected must be able to **ingest an externally produced, edited media file and associate it to a unit and session**. This is a modest, common capability — but it should be an explicit criterion, because it is the hinge on which BR-005's architectural compliance turns.

### 10.4 What Cannot Be Costed

- **Venue count and current AV inventory** — the named venues have not been enumerated. BR-005 requires named venues, a capability standard and a cost, approved alongside the core recommendation. Prof. Desmond Key owns the scope, due before options analysis.
- **Per-venue capital** — Epiphan and Dante components have published specifications but no published prices were located, and any figure would depend heavily on camera count, microphone count and existing infrastructure.
- **Operating model** — UC-5's main flow has a technician configuring camera positions and audio inputs. That is **staffed** capture, not automated capture. The recurring staff cost may exceed the capital cost, and BR-005's success criterion requiring an agreed support model "including specialist equipment maintenance" is where that lands.

### 10.5 On Conflict C-6

The research supports the requirement document's framing. REQ-010 is a **genuine capability gap** in the mainstream market, not a preference — the multi-track audio evidence [PANMC-C1] and the entirely separate specialist ecosystem (Epiphan, Dante) [EPIPN-C1] [DANTE-C1] demonstrate that the two capabilities are served by different technology, not by different tiers of the same technology.

This strengthens the Option 3 resolution in Conflict C-6 without disturbing it: the capability genuinely cannot be obtained by choosing a better core platform, so the exception route under Principle 4 is the architecturally correct answer regardless of the funding decision. **What it does not do is make the exception affordable.** The refusal path in BR-005 remains real, and Prof. Key was told plainly that he gets an explicit decision, not a guarantee.

---

## 11. Requirements Traceability

### 11.1 Coverage Against the Capture Requirement Subset

| REQ | Requirement (abbreviated) | Category | Solution position | Status |
|-----|---------------------------|----------|-------------------|--------|
| REQ-004 | Staff record and publish teaching content with a single supported toolchain | 1 | All four specialists purpose-built for this; Microsoft requires per-meeting action [MSAR-C1] | ✅ Solutions identified |
| REQ-008 | Live class delivery with recording | 1 | Zoom (AU residency confirmed [ZOOMAU-C1], AARNet channel [AARN-C1]) or Teams; may be a bounded second platform under A-7 | ✅ Solutions identified |
| REQ-009 | Universal automatic capture, 4-hour publication | 1 | Specialists: native scheduling. Microsoft: requires a build (§3.1) | ✅ Solutions identified; ⚠️ cost differs materially by option |
| REQ-010 | Multi-camera, high-fidelity performance capture | 6 | Not served by mainstream platforms; hybrid specialist hardware + core platform (§10.3) | ⚠️ Requires hardware build |
| REQ-025 | Automated provisioning, no manual CSV | 4 | Microsoft strongest structurally [MSSCIM-C1]; Echo360 REST + roster sync [E360BB3-C1]; Panopto uncertain [PANSCIM-C1] | 🔍 Must be gate-tested (R-022) |
| REQ-029 | WCAG 2.2 AA | 3 | Echo360 published at 2.2 AA [E360A-C1]; Panopto at 2.1 AA [PANA-C1]; YuJa partial [YUJA-C1] | ⚠️ Published positions differ; all must be tested |
| REQ-030 | Privacy Act 1988, AU residency preferred, APP 8 assessed | 2 | Confirmed: Panopto [PANAU-C1], Kaltura [KALAU-C1], Microsoft [MSDR-C1], Zoom [ZOOMAU-C1]. **Not confirmed: Echo360 [E360SEC-C1], YuJa [YUJAT-C1]** | 🔍 Two gaps requiring written confirmation |
| REQ-031 | SSO with MFA, no local accounts | 4 | Universally supported; the real test is elimination of local/service account paths (§6.4) | ✅ Unlikely to discriminate; ⚠️ must be tested specifically |
| REQ-032 | 99.9% availability during teaching periods | 1 | No vendor publishes an SLA at this granularity (§3.3) | 🔍 Contract negotiation item, not a research finding |
| REQ-033 | Essential Eight alignment | — | Property of the estate, not of any product. SCHD EOL finding is directly actionable [E360SCHD-C1] | 🔍 Not assessable from market research; requires D-3 |
| REQ-034 | Export in open formats on termination | 5 | **No vendor meets the "no vendor assistance" standard on published evidence** (§9.1) | ⚠️ Market-wide gap; contractual mitigation required |
| REQ-035 | Total licence spend reduce or hold flat | — | Requires D-1 and D-2 | 🔍 Not assessable; §7.1 |

### 11.2 Mandatory Gate Assessment

| Gate | Requirement | Echo360 | Panopto | Kaltura | YuJa | Microsoft |
|---|---|---|---|---|---|---|
| **NFR-SEC-001** SSO+MFA, no local accounts | Pass/fail | Likely pass — verify local account elimination | Likely pass — verify | Likely pass — verify | Likely pass — verify [YUJAT-C1] | Structural pass |
| **NFR-C-002** WCAG 2.2 AA + captioning | Pass/fail | **Published 2.2 AA, Level Access audited** [E360A-C1] | **Published 2.1 AA** [PANA-C1] — obtain 2.2 VPAT | Level unverified [KALVPAT-C1] | **Partial 2.2 A/AA** [YUJA-C1] | Unverified [MSSTR-C1] |
| **NFR-I-002** Open-format bulk export, no fee, no vendor assistance | Pass/fail | Captions WEBVTT [E360ASR-C2]; bulk export **unknown** | Vendor-assisted, 3–4 weeks [PANEXP-C1] | Vendor-assisted [YUJAMIG-C1] | Outbound unevidenced | Structurally strongest [MSSTR-C1] |

> **Read this table carefully.** On published evidence **no candidate clears all three gates cleanly.** That is a finding about the state of the market and about the strictness of the gates — both of which are legitimate. The gates were set deliberately (NFR-I-002 was elevated to MUST_HAVE on Principle 9's authority, flagged for Education Committee visibility). If, after testing, no candidate passes all three, that is a **governance decision for Education Committee**, not a licence for the project to quietly relax a gate. The RIFF pause provision exists for exactly this situation [SGP-C3].

### 11.3 Gaps

**GAP-1: No vendor demonstrably meets NFR-I-002 as written.**
- *Impact*: The mandatory export gate may eliminate every candidate, or be applied inconsistently under time pressure.
- *Options*: (a) Test all candidates practically and accept the best demonstrated; (b) convert the gate to a contractual obligation with a tested acceptance criterion; (c) relax the "without vendor assistance" clause with Education Committee visibility.
- *Recommendation*: **(b)**. Keep the gate, satisfy it through a contractual termination-assistance obligation with a demonstrated export during evaluation and an annual test right (§9.4). This preserves Principle 9's substance — a platform that can be left — without disqualifying the entire market on a clause no supplier currently meets.

**GAP-2: Echo360 and YuJa Australian residency unconfirmed.**
- *Impact*: NFR-C-001 is CRITICAL and DR-006 requires a register per data class. The PIA cannot complete without this (R-013).
- *Recommendation*: Written information request before shortlisting, covering storage *and* processing location (§4.2).

**GAP-3: Provisioning API capability unverified for three of five candidates.**
- *Impact*: R-022's residual rating of 4 (Low) assumes the mandatory gate is applied and tested. It is sound only if the gate is genuinely enforced.
- *Recommendation*: The gate is the mitigation. No further research needed — but the gate must not be softened into a scored criterion.

**GAP-4: No SLA evidence at NFR-A-001 granularity.**
- *Recommendation*: Move to contract negotiation; do not score from documentation (§3.3).

**GAP-5: CAUDIT sector arrangements not established.**
- *Impact*: With the competitive tender route settled (Conflict C-5), a pre-existing sector agreement would not change the route, but could change the supplier set, the terms available and the pricing baseline.
- *Recommendation*: Grace Tanaka to query CAUDIT directly before criteria are issued on 2026-08-31.

---

## 12. Recommendation

### 12.1 What This Research Recommends

**1. Shortlist three, not two.** Echo360, Panopto and Microsoft. The framing of the dispute as "Echo360 versus Microsoft" [S-C1] omits the candidate that, on published evidence, holds the strongest position on the integration standards the requirements make CRITICAL — Panopto, with LTI Advantage Complete [PANLTI-C1], documented Blackboard Ultra LTI 1.3 [PANBB-C1], confirmed AU region since 2020 [PANAU-C1] and a certified room hardware path [PANEPI-C1]. Including it also converts a two-party executive dispute into a three-way evaluation, which is a structurally healthier shape for Conflict C-1's Option 3.

**2. Cost the Microsoft option as platform plus build.** The auto-record constraint [MSAR-C1] [MSAR-C2] and the Teams Rooms Pro recurring room licence [MSTRP-C1] are both sourced and both material. Neither invalidates the Principle 19 argument — but the argument must be made against the real cost, not the assumed one.

**3. Make the three mandatory gates hands-on tests, not documentation reviews.** Every gate in §11.2 resolved to "verify" or "unknown" from published sources. Documentation-scoring them will produce false confidence.

**4. Escalate the incumbent export question ahead of the platform argument.** §9.5. It is the only question whose answer determines whether BR-007 is executable at all, and it is answerable by 2026-08-14 from the contract file.

**5. Treat REQ-010 as a hardware programme, not a platform feature.** §10. The exception should be scoped as Epiphan-class capture hardware plus networked audio at named venues, publishing through whichever core platform is selected — with the core platform's ability to ingest and associate an external media file made an explicit criterion.

**6. Size D-8 for statistical stability.** §5.2. The literature shows small test sets produce unstable rankings.

### 12.2 What This Research Explicitly Does Not Conclude

Stated so that nothing here is over-read:

- ❌ **It does not recommend a platform.** That is the evaluation's job under signed criteria (BR-004).
- ❌ **It does not state a TCO.** Four named blockers, all owned, all dated (§7.1).
- ❌ **It does not establish that Echo360 fails LTI 1.3.** It establishes that Echo360's own guidance steers Blackboard migrations to LTI 1.1 and that section-level linking is unsupported over 1.3 [E360BB-C1] [E360LTI-C1]. That is a question to put to the vendor, not a conclusion.
- ❌ **It does not establish that Panopto fails WCAG 2.2 AA.** It establishes that Panopto's published claim is 2.1 AA and its VPAT is not public [PANA-C1] [PANA-C2].
- ❌ **It does not establish Panopto's current provisioning API.** §6.3 is the weakest evidence here and is flagged as such.
- ❌ **It does not assess Kaltura, YuJa, Zoom or Mediasite to the same depth** as Echo360, Panopto and Microsoft.
- ❌ **It does not evaluate Opencast or any open-source option on capability.** §6.5 is a screening judgement on operating-model grounds.
- ❌ **It does not confirm any Australian sector purchasing arrangement.** §2.3.

### 12.3 Immediate Actions

| # | Action | Owner | By |
|---|--------|-------|-----|
| 1 | Contract review: incumbent bulk export terms — media + captions + metadata, fees, throughput (§9.5) | Grace Tanaka | 2026-08-14 |
| 2 | Written residency statements from Echo360 and YuJa: storage **and** processing (§4.2) | Grace Tanaka | 2026-08-21 |
| 3 | Request current WCAG 2.2 AA VPATs from all shortlisted vendors (§5.4) | Dr. Benny Moog | 2026-08-21 |
| 4 | Query CAUDIT on any sector agreement covering this capability (§2.3) | Grace Tanaka | 2026-08-31 |
| 5 | Add to evaluation criteria: LTI 1.3 hands-on test on UoF's Blackboard Ultra at section granularity (§6.2) | Sam Okafor | 2026-08-28 |
| 6 | Add to evaluation criteria: room-side cost shape — capital vs recurring per-room licence (§8.2) | Vernon Ostinato | 2026-08-28 |
| 7 | Size and build the D-8 caption test set per §5.2 | Dr. Benny Moog | Before evaluation |
| 8 | Scope named performance venues and capability standard (§10.4) | Prof. Desmond Key | Before options analysis |
| 9 | Re-verify the University of Derby Panopto contract value from the primary notice (§2.4) | Rhonda Bell | Before any Ops Committee paper |

---

## 13. Research Methodology and Limitations

**Sources used**: vendor product and support documentation; vendor and third-party press releases; official Microsoft Learn documentation; peer-reviewed research (ACM TACCESS / arXiv); industry benchmarking (3Play Media); published public-sector contract award notices; Australian sector bodies (AARNet, CAUDIT); a US higher-education purchasing consortium (MEEC); and university-published project and accessibility pages.

**Deliberate exclusions**: UK Digital Marketplace, G-Cloud, Crown Commercial Service and DOS frameworks were excluded as inapplicable to an Australian university, per the research brief. UK contract award notices appear solely as published price evidence for the same products and are labelled as sector comparators.

**Limitations — stated so the reader can calibrate**:

1. **No vendor pricing was obtained.** The segment is quote-only [PANPRICE-C1]. Every cost statement is either a published list price (Microsoft) or a foreign public-sector award value used as an order-of-magnitude comparator.
2. **Vendor support portals are largely authenticated.** Several fetches returned 403 or TLS errors, including the primary UK Contracts Finder notice, the ACM paper, a YuJa support article and a Panopto support article. Where a fetch failed, the finding is either sourced to an alternative page or marked lower confidence.
3. **Kaltura, YuJa, Zoom and Mediasite are covered at lower depth** than Echo360, Panopto and Microsoft.
4. **G2 ratings in §2.2 come from a single aggregated search result**, not individually fetched review pages, and are marked low-confidence.
5. **Section 6.3 (provisioning APIs) is the weakest section.** Panopto's position rests on a community forum post of uncertain date.
6. **No Australian-specific vendor pricing or contract data was located.** Australian universities are not Commonwealth agencies and do not publish awards to AusTender.
7. **Currency**: no AUD conversion has been applied anywhere. Applying an exchange rate to a foreign list price would manufacture false precision.
8. **Market currency**: this research reflects the market as at July 2026 and should be treated as valid for approximately six months.
9. **No external analyst reports were available.** `projects/002-lecture-capture/external/` contains engagement inputs only; no Gartner, Forrester or equivalent market research was supplied. If the university holds analyst subscriptions, that material would materially strengthen §2.

---

## 14. Spawned Knowledge

The following standalone knowledge files were created from this research and are reusable beyond Project 002. Each carries its own citations back to the sources fetched on 2026-07-27.

### Vendor Profiles

| File | Status | Confidence | Note |
|------|--------|-----------|------|
| `vendors/echo360-profile.md` | Created | HIGH (10+ sourced data points) | Incumbent. Strongest published accessibility position; open questions on AU residency, Blackboard LTI 1.3 and bulk export |
| `vendors/panopto-profile.md` | Created | HIGH (12+ sourced data points) | Strongest published integration-standards and AU residency position; open questions on WCAG 2.2 and provisioning API |
| `vendors/microsoft-profile.md` | Created | HIGH (8+ data points, all official Microsoft Learn documentation) | Principle 19 candidate. Strongest on identity, residency and portability; no native timetable-driven capture |
| `vendors/kaltura-profile.md` | Created | MEDIUM (7 sourced data points) | Included for market completeness; capability researched at lower depth |
| `vendors/yuja-profile.md` | Created | MEDIUM-LOW (6 sourced data points) | Two CRITICAL positions — AU residency and LTI 1.3 certification — could not be established from published sources |

> **No profile was created for Zoom or Enghouse Mediasite.** Neither reached the three-verified-data-point threshold as a *capture* platform in this research pass. Zoom's evidence is confined to AU recording residency and the AARNet channel; Mediasite appears only in the MEEC consortium listing.

### Tech Notes

| File | Status | Reusable beyond this project? |
|------|--------|-------------------------------|
| `tech-notes/asr-caption-accuracy.md` | Created | **Yes** — the finding that vendor accuracy claims are not evidence, and that a locally built test set must be sized for statistical stability, applies to any procurement involving captioning, transcription or accessibility conformance |
| `tech-notes/lti-1-3-advantage.md` | Created | **Yes** — the LTI certification ladder, the "certification does not guarantee depth on your LMS" finding, and the separation of LTI from identity provisioning apply to any LMS tool integration |
| `tech-notes/australian-data-residency-saas.md` | Created | **Yes** — the residency mechanism taxonomy (contractual / infrastructure / configurational), the processing-location trap, and the standing information request apply to any Australian SaaS procurement holding personal information |

**Deduplication check performed**: `projects/002-lecture-capture/vendors/` and `projects/002-lecture-capture/tech-notes/` were both empty before this run. All eight files are new; no merge was required.

---

## External References

> This section provides traceability from generated content back to source documents and to web sources fetched during research.

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| REQ | ARC-002-REQ-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Requirements specification — BR/FR/NFR/INT/DR set and mandatory gates |
| STKE | ARC-002-STKE-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Stakeholder drivers, goals, conflicts, RACI |
| RISK | ARC-002-RISK-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Risk register — R-006, R-007, R-011, R-012, R-020, R-022 referenced |
| PRIN | ARC-000-PRIN-v1.0.md | ArcKit artifact | `000-global/` | Enterprise Architecture Principles |
| SL | system-landscape.md | Foundation artifact | `002-lecture-capture/external/` | System categorisation map and known integrations |
| PC | privacy-context.md | Compliance input | `002-lecture-capture/external/` | PI inventory, data flows, Essential Eight self-assessment |
| SGP | solution-governance-process.md | Foundation artifact | `000-global/policies/` | RIFF Review governance process |
| S | stakeholders.md | Engagement input | `002-lecture-capture/external/` | Stakeholder register |

### Citations — Project Documents

| Citation ID | Doc ID | Section | Category | Quoted Passage |
|-------------|--------|---------|----------|----------------|
| S-C1 | S | Engagement notes | Risk Factor | "Known tension: Rhodes (CIO) favours Microsoft-platform consolidation (Teams/Stream); Moog and Key defend best-of-breed pedagogy tools (Echo360, discipline software)." |
| SL-C4 | SL | Known integrations, #2 | Integration Requirement | "Echo360 user provisioning / LTI + manual CSV / Manual workaround for casual academic staff" |
| PC-C1 | PC | §3 | Security Requirement | "Restrict administrative privileges / ML1 / ML2 / Legacy shared admin accounts in AV/capture estate"; "Patch operating systems / ML1 / ML2 / Lecture-theatre capture appliances behind" |
| PC-C5 | PC | §3 | Security Requirement | "Multi-factor authentication ... exception: two tools still allow local accounts (breaches REQ-031)" |
| PP-C7 | SL | Known integrations | Context | "Undocumented; single-person dependency" (course cloning automation) |
| PRIN-C1 | PRIN | Principle 2 | Design Decision | "Each capability category MUST have a designated primary platform. Where more than one platform provides the same capability, the architecture MUST state which is primary and why the others persist, with a defined boundary or a retirement path." |
| PRIN-C2 | PRIN | Principle 4 | Design Decision | "Discipline-specific tooling MAY sit outside the core platform set where a genuine specialist need exists, but it MUST integrate through the same standard interfaces, identity model, and data contracts as core platforms. Specialist need justifies a different tool — never a different architecture." |
| PRIN-C4 | PRIN | Principle 9 | Procurement Constraint | "Every platform holding university or student data MUST permit export of that data in open, documented formats, at any time and on termination, without dependence on vendor goodwill or additional fee." |
| PRIN-C5 | PRIN | Principle 14 | Compliance Constraint | "All student-facing platforms and materials MUST meet WCAG 2.2 Level AA. Accessibility is assessed during evaluation and before release — never remediated after deployment." |
| SGP-C2 | SGP | Rules | Procurement Constraint | "Solutions duplicating capability already licensed (per the system landscape map) must justify why the incumbent tool is unsuitable." |
| SGP-C3 | SGP | Rules | Procurement Constraint | "A request may be paused or closed without progressing further, with the agreement of key consulting stakeholders, if it is deemed not to be required." |
| STKE-C3 | STKE | SD-3 | Business Requirement | "A platform change that requires appliance replacement converts an opex saving into a capex request, and he will not learn that at business case stage without consequence." |
| STKE-C9 | STKE | SD-6 | Design Decision | "a general-purpose meeting-recording tool and a purpose-built lecture capture platform are not the same product class, and he expects the difference to be dismissed in a cost comparison" |

### Citations — Web Sources

> All URLs below were fetched or returned as search results during this research on 2026-07-27. Fetch failures are recorded explicitly.

| Citation ID | Source | URL | Fetch status | Claim supported |
|-------------|--------|-----|--------------|-----------------|
| MSAR-C1 | Microsoft Learn — Manage Teams meeting auto recording | https://learn.microsoft.com/en-us/microsoftteams/manage-teams-auto-recording | Fetched (doc updated 2026-05-11) | "Organizers must manually enable **Record and transcribe automatically** setting for each meeting they want recorded and transcribed automatically." |
| MSAR-C2 | Microsoft Learn — Manage Teams meeting auto recording | https://learn.microsoft.com/en-us/microsoftteams/manage-teams-auto-recording | Fetched | "Only organizers with a Teams Premium license can use assigned meeting templates." |
| MSDR-C1 | Microsoft Learn — M365 data residency overview | https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview | Fetched | Australia is a *Local Region Geography*; Table 3 shows P-M-A for Exchange, SharePoint/OneDrive, Teams, Copilot |
| MSDR-C2 | Microsoft Learn — M365 data residency overview, Table 4 | https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview | Fetched | Australia data centre locations: Melbourne, Sydney |
| MSSTR-C1 | Microsoft Learn — Microsoft Stream service description | https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-stream | Fetched | Stream on SharePoint; transcripts for uploaded videos across plans incl. Education; SharePoint/OneDrive storage with admin control of lifecycle and governance |
| MSLTI-C1 | Microsoft Learn — Deploy the Microsoft 365 LTI app in Blackboard | https://learn.microsoft.com/en-us/microsoft-365/lti/microsoft-365-lti-blackboard | Fetched | Registered via "Register LTI 1.3/Advantage Tool"; requires Blackboard Email/Institutional Email populated with Entra UPN |
| MSLTI-C2 | Microsoft Learn — same page, migration guidance | https://learn.microsoft.com/en-us/microsoft-365/lti/microsoft-365-lti-blackboard | Fetched | "The classic Teams Classes and Teams Meetings app has sunset as of September 15, 2025"; new Meetings app shows only previous and upcoming six months |
| MSTRP-C1 | Microsoft — Teams Rooms Pro product page | https://www.microsoft.com/en-us/microsoft-teams/teamsroomspro | Fetched | "$40.00 room/month, paid yearly" |
| MSSCIM-C1 | Microsoft Learn — SCIM provisioning tutorial | https://learn.microsoft.com/en-us/entra/identity/app-provisioning/use-scim-to-provision-users-and-groups | Search result | SCIM is Microsoft's documented provisioning pattern for Entra ID |
| E360A-C1 | PR Newswire — Echo360 Achieves WCAG 2.2 AA Compliance Across the Echosystem | https://www.prnewswire.com/news-releases/echo360-achieves-wcag-2-2-aa-compliance-across-the-echosystem-302756675.html | Fetched | 29 April 2026; "all five solutions in the Echosystem™ are compliant with the Web Content Accessibility Guidelines (WCAG) 2.2 AA standards"; covers EchoVideo, EchoInk, EchoEngage, EchoExam, GoReact |
| E360A-C2 | PR Newswire — same release | https://www.prnewswire.com/news-releases/echo360-achieves-wcag-2-2-aa-compliance-across-the-echosystem-302756675.html | Fetched | Level Access named as auditing partner; VPATs completed for each solution; aligns to EN 301 549 and Section 508 |
| E360BB-C1 | Echo360 Support — Blackboard Integration Overview | https://support.echo360.com/hc/en-us/articles/11074515169421-EchoVideo-Blackboard-Integration-Overview | Fetched | "NOTE that while migrating to LTI 1.3 may appear to be an option within Blackboard, it has not been fully tested by us. We are only supporting migrating to LTI 1.1." Also: REST API automates course linking/scheduling, synchronises roster data, delivers consolidated analytics |
| E360BB2-C1 | Echo360 Support — Creating an LTI 1.3 Integration with Blackboard | https://support.echo360.com/hc/en-us/articles/13786298949901-EchoVideo-Creating-an-LTI-1-3-Integration-with-Blackboard | Fetched | LTI 1.3 Deep Linking between Blackboard and EchoVideo; Analytics tool and Deep Linking content tool placements |
| E360BB3-C1 | Echo360 Support — Adding a REST API Integration with Blackboard | https://support.echo360.com/hc/en-us/articles/11074881768973-EchoVideo-Adding-a-REST-API-Integration-with-Blackboard | Search result | REST API integration with Blackboard as LMS type |
| E360BB4-C1 | Echo360 Support — Deep Link Placement for Blackboard Ultra / Embedding in Ultra-enabled courses | https://support.echo360.com/hc/en-us/articles/11075080326541-EchoVideo-Adding-a-Deep-Link-Tool-for-Embedding-EchoVideo-Media-into-Blackboard-Ultra | Search result | Deep link tool for Blackboard Ultra |
| E360LTI-C1 | Echo360 Support — LTI Advantage and LTI 1.3 Support | https://support.echo360.com/hc/en-us/articles/11074490900621-EchoVideo-LTI-Advantage-and-LTI-1-3-Support | Fetched | LTI Advantage certified through 1EdTech; Deep Linking, Names and Role Provisioning Services, Assignments and Grades Services; Moodle/Canvas/Brightspace/Blackboard; "LTI 1.3 does not currently support linking to EchoVideo Course sections themselves"; no automatic LTI 1.1 → 1.3 migration |
| E360ASR-C1 | Echo360 Support — ASR Service for Media Transcription | https://support.echo360.com/hc/en-us/articles/360035406171-EchoVideo-Automatic-Speech-Recognition-ASR-Service-for-Media-Transcription | Fetched | Partnership with AWS for transcription; confidence-score threshold for auto-applying captions; custom dictionaries in AWS Transcribe format "must be configured by Echo360 Support on behalf of institutions"; ASR "is unlikely to meet the accuracy levels required for closed captions for hearing-impaired individuals" |
| E360ASR-C2 | Echo360 Support — same page | https://support.echo360.com/hc/en-us/articles/360035406171-EchoVideo-Automatic-Speech-Recognition-ASR-Service-for-Media-Transcription | Fetched | "closed caption files and transcription files use the WEBVTT standard" |
| E360API-C1 | Echo360 Support — API section | https://support.echo360.com/hc/en-us/sections/10967188719245-API | Search result | "modern, stateful" REST APIs with SDKs; API and SDK documentation, Reporting API, Capture Intake API, Capture API |
| E360SEC-C1 | Echo360 — Government Secure Solutions | https://echo360.com/government/secure-solutions/ | Fetched | Page contains **no** data residency, hosting region, cloud provider, SOC 2, ISO 27001, FedRAMP or IRAP statement; references US federal approvals only |
| E360UC-C1 | Echo360 Support — Universal Capture Overview | https://support.echo360.com/hc/en-us/articles/11077013986061-EchoVideo-Universal-Capture-Overview | Search result | Cross-platform capture interface across hardware and software |
| E360UC2-C1 | Echo360 Support — Universal Capture Specifications / Supported Devices | https://support.echo360.com/hc/en-us/articles/360035035332-EchoVideo-Universal-Capture-Specifications | Search result | Supported on macOS 10.14+ and Windows 10+ |
| E360UC3-C1 | Echo360 Support — Universal Capture on the Pro and Pod | https://support.echo360.com/hc/en-us/articles/360035406231-Universal-Capture-on-the-Pro-and-Pod | Search result | UC interface accessible on Pro and Pod appliances via UC:Device and UC:Online |
| E360SCHD-C1 | Echo360 Support — Working with Managed Capture Devices | https://support.echo360.com/hc/en-us/articles/360035034472-Working-with-Capture-Appliances | Search result | SCHD appliance End of Software Support 1 April 2020; End of Life 30 December 2020 |
| E360M-C1 | PR Newswire — Echo360 and Turning Merge | https://www.prnewswire.com/news-releases/echo360-and-turning-merge-to-support-higher-educations-shift-to-video-and-hybrid-learning-301457993.html | Search result | January 2022 merger; combined company operates under the Echo360 brand; Centre Lane Partners investment |
| E360M-C2 | Centre Lane Partners — Echo360 Acquires Inkling | https://www.centrelanepartners.com/2024/05/21/echo360-acquires-inkling-to-form-premier-global-education-and-corporate-learning-saas-enterprise/ | Search result | Echo360 acquired Inkling, May 2024 |
| PANA-C1 | Panopto — Video Accessibility & Captioning Platform | https://www.panopto.com/capabilities/accessibility/ | Fetched | "regularly evaluated against WCAG 2.1 AA and Section 508 standards"; integrations with 3Play Media, Rev.com, Verbit.ai |
| PANA-C2 | Panopto — same page | https://www.panopto.com/capabilities/accessibility/ | Fetched | "Panopto's Accessibility Conformance Report documentation is available on request" — not published |
| PANAU-C1 | Panopto — Expands Global Video Cloud, Launches New Data Center in Australia | https://www.panopto.com/company/news/panopto-expands-global-video-cloud-launches-new-data-center-in-australia/ | Search result (news index fetched; article body not retrieved) | Sydney data centre for ANZ; AU Cloud in AWS Asia-Pacific (Sydney) Region; content stored locally; encrypted at rest and in transit; announced November 2020 |
| PANLTI-C1 | Panopto — Achieves LTI Advantage Complete Certification from 1EdTech | https://www.panopto.com/company/news/panopto-achieves-lti-advantage-certification-1edtech/ | Search result | LTI 1.3 Advantage Complete certification |
| PANBB-C1 | Panopto Support — How to Set Up a Blackboard Integration with LTI 1.3 | https://support.panopto.com/s/article/How-to-Set-Up-a-Blackboard-Ultra-Integration-with-LTI-1-3 | Search result | LTI 1.3 setup for Blackboard Ultra |
| PANBB2-C1 | Panopto — Blackboard integration page / community LTI 1.3 announcements | https://www.panopto.com/integrations/blackboard/ | Search result | LTI 1.3 available for Blackboard Ultra, Canvas, D2L, Moodle; supports Ultra and Original course views; "inherits Blackboard course roles and permissions automatically"; Blackboard B2 support ended June 2024 |
| PANBB3-C1 | Panopto Support — How to Batch Provision Courses in Blackboard | https://support.panopto.com/s/article/provision-courses-blackboard-1 | Search result | Batch course provisioning documented |
| PANCAP-C1 | Aalto University OPIT blog — Boost ASR accuracy on Panopto with a Custom Dictionary | https://blogs.aalto.fi/opit/2024/08/12/boost-asr-accuracy-on-panopto-with-a-custom-dictionary-tailored-to-aalto-university/ | Search result | Site-level custom dictionaries for ASR and OCR; institution-specific terms, acronyms, proper nouns |
| PANCAP2-C1 | Panopto — FAQs About Video Captioning | https://www.panopto.com/blog/frequently-asked-questions-faqs-about-video-captioning-answered/ | Search result | ASR captions "typically 90-95% accurate depending on the audio quality"; human captions "at least 99% accurate"; ASR struggles with non-native speakers, accents, and "technical, disciplinary language" |
| PANEPI-C1 | Panopto — Certifies Epiphan Pearl Devices for Superior Classroom Capture | https://www.panopto.com/company/news/panopto-certifies-epiphan-pearl-devices-for-superior-classroom-capture/ | Search result | Epiphan Pearl family Panopto Certified after testing for compatibility and integration |
| PANEPI2-C1 | Panopto — Certification of Pearl Nexus | https://www.panopto.com/company/news/panopto-elevates-with-certification-of-pearl-nexus/ | Search result | Pearl Nexus certification |
| PANMC-C1 | Panopto Community — Audio Stream | https://community.panopto.com/discussion/1773/audio-stream | Search result | "Multi-track audio is not currently available in Panopto"; for distributed recording "at least one device needs to record a primary audio stream, as secondary-only recordings will not include audio" |
| PANMC2-C1 | Panopto — Record Video Presentations From Different Viewpoints With Multiple Cameras | https://www.panopto.com/blog/engage-multi-cam-2/ | Search result | Second, third, fourth camera recognised and recorded automatically synced |
| PANEXP-C1 | YuJa Help Center — Panopto Migration Checklist for Requesting Data Extract | https://support.yuja.com/hc/en-us/articles/19402197922071-Panopto-Migration-Checklist-for-Requesting-Data-Extract | **Fetch returned HTTP 403**; detail from search result summary | Panopto data extract: allow 3–4 weeks; delivered as access to an AWS S3 bucket |
| PANEXP2-C1 | Panopto Support — How to Download Captions | https://support.panopto.com/s/article/How-to-Download-Captions | Search result | Individual caption download |
| PANEXP3-C1 | Panopto Community — bulk download videos | https://community.panopto.com/discussion/1174/bulk-download-videos | Search result | Bulk download capturing all streams and source files not currently available in one action |
| PANPRICE-C1 | Panopto — Pricing | https://www.panopto.com/pricing/ | Fetched | "Panopto is an enterprise platform. Your deployment—the number of users, integrations, add-ons, and deployment model—is unique. So is your price." No tiers or figures published. SSO, SOC 2, GDPR, FERPA listed; AI add-ons priced separately |
| PANSCIM-C1 | Panopto Community — Automating user provisioning through the APIs | https://community.panopto.com/discussion/554/automating-user-provisioning-through-the-api-s | Search result | Community request for "SCIM compatibility, or at least some REST API endpoints"; SOAP `CreateUser` and `SyncExternalUser` referenced. **Date uncertain — low confidence** |
| PANUNISA-C1 | Panopto — Switching From An On-Premises Solution To The Panopto Video Cloud | https://www.panopto.com/blog/switching-from-an-on-premises-solution-to-the-panopto-video-cloud/ | Search result | University of South Australia moved from customised on-premises Echo360 to Panopto cloud. **Vendor-published** |
| KALAU-C1 | IT Business Net — Kaltura Expands AI-Powered Agentic Experiences to Europe, Asia-Pacific, and Canada | https://itbusinessnet.com/2026/04/kaltura-expands-ai-powered-agentic-experiences-to-europe-asia-pacific-and-canada-with-dedicated-regional-infrastructure-for-enterprise-data-residency-and-performance/ | Search result | Asia-Pacific (Sydney) among three new regions with dedicated regional infrastructure for data residency; stores data within each geography |
| KALLC-C1 | Kaltura Knowledge Center — Lecture Capture release notes | https://knowledge.kaltura.com/help/kaltura-lecture-capture---release-notes | Search result | Lecture Capture release 14 December 2025 |
| KALCAP-C1 | Kaltura Knowledge Center — Kaltura Capture release notes | https://knowledge.kaltura.com/help/kaltura-capture-release-notes | Search result | Kaltura Capture 5.2.3 released 4 December 2025 |
| KALVPAT-C1 | Kaltura — Official VPAT | https://corp.kaltura.com/kaltura-official-vpat/ | Search result | Kaltura Accessibility Conformance Report / VPAT published. **Conformance level not verified** |
| KLTR-C1 | Kaltura — Q4 and Full-Year 2025 Financial Results | https://investors.kaltura.com/news-releases/news-release-details/kaltura-announces-fourth-quarter-and-full-year-2025-financial/ | Search result | FY2025 revenue US$180.9m (+1%); subscription US$171.9m (+3%); EE&T segment US$134.4m (+4%); ARR US$168.2m (−3%); NDR 97%; 2026 guidance US$181.2–184.2m |
| YUJAT-C1 | YuJa — Security and Trust | https://www.yuja.com/trust-center/security/ | Fetched | "multiple physical data center zones"; **no region or cloud provider named; no data residency guarantee**; AES-256 at rest; TLS 1.2 min / 1.3 default; SOC 2 Type II, GDPR, HECVAT, TX-RAMP, CSA Cyber Essentials; **no ISO 27001**; conformance to "latest LTI and SSO standards" |
| YUJA-C1 | University College Dublin IT Services — YuJa Accessibility Statement | https://www.ucd.ie/itservices/ourservices/educationaltechnologies/accessibilitystatements/yujaaccessibilitystatement/ | Search result | "YuJa EVCM is partially compliant with the Web Content Accessibility Guidelines (WCAG) 2.2 Level A and AA"; vendor-evaluated using automated tools, manual testing, multi-browser validation. Auto-captions "may contain errors and must be reviewed and edited" |
| YUJAMIG-C1 | YuJa Help Center — Mediasite / Panopto / Kaltura Migration Checklists | https://support.yuja.com/hc/en-us/articles/20502658067863--Mediasite-Migration-Checklist-for-Requesting-Data-Extract | Search result | YuJa publishes migration checklists for Mediasite, Panopto and Kaltura; Mediasite extract "allow 2-3 weeks to fully transfer all data to the YuJa S3 bucket" |
| YUJAAPI-C1 | YuJa Help Center — YuJa API | https://support.yuja.com/hc/en-us/articles/360049580714-YuJa-API | Search result | YuJa API documented |
| YUJAMETA-C1 | YuJa Help Center — Setting Metadata Schemes and Managing Metadata | https://support.yuja.com/hc/en-us/articles/360047436573-Setting-Metadata-Schemes-and-Managing-Metadata | Search result | Custom metadata management via Admin Panel |
| ZOOMAU-C1 | AARNet — Zoom introduces Live Transcription, and Cloud Recording storage in Australia for education | https://www.aarnet.edu.au/zoom-introduces-live-transcription-and-cloud-recording-storage-in-australia-for-education | Fetched | Australian cloud recording storage activated for AARNet customers 1 February 2021; admin sets Data & Storage region to Australia, ensuring storage **and post-meeting processing such as transcription** occur in Australia; live transcription ~90% accuracy dependent on audio quality and accents; not available in breakout rooms |
| AARN-C1 | AARNet — Zoom Video Communications for Research & Education | https://www.aarnet.edu.au/zoom | Search result | AARNet is "a leading Zoom APAC Reseller for education in Australia"; delivers licensing and support; hosts Zoom servers on its network; Zoom cloud recording integration with CloudStor |
| CAUD-C1 | CAUDIT — IT Procurement Community of Practice / Strategic Partner Program | https://www.caudit.edu.au/it-procurement-cop/ | Search result | CAUDIT IT Procurement CoP; MoU with AARNet since October 2017. **No lecture capture panel evidenced** |
| MEEC-C1 | MEEC — Lecture Capture Systems | https://www.meec-edu.org/lecture-capture-solutions-2/ | Fetched | Five master agreement holders: Echo360/Turning Tech Intermediate Inc (Youngstown OH), Kaltura Inc (New York NY), Panopto Inc (Pittsburgh PA), Enghouse Mediasite (Paramus NJ), YuJa Inc (San Jose CA); RFP #0004-2023; term 7/1/2023–6/30/2029; multi-award; pricing not published |
| UQ-C1 | University of Queensland eLearning — Kaltura decommission and transition to Echo360 | https://elearning.uq.edu.au/project/kaltura-decommission-and-transition-echo360 | Fetched | Kaltura read-only 3 June 2024; vendor migration complete by 1 July 2024; supplementary migration Nov–Dec 2024; Kaltura decommissioned 31 December 2024; "Rationalising our video systems will simplify the environment for teaching staff, and students, reduce support complexity, and save money"; no information on bulk export capability or costs |
| UKC-C1 | UK Contracts Finder / search summary — University of Derby and University of Southampton Panopto contracts | https://www.contractsfinder.service.gov.uk/notice/4e6f2ce8-5bda-4b50-afcc-dbfdc1d003aa | **Fetch returned HTTP 403** — figures from search result summary only | Derby: Panopto £393,572, 1 Sep 2024 – 31 Aug 2027, integrated with Blackboard Learn. Southampton: Panopto EDU platform licences, 4 Jun 2021 – 3 Jun 2024. **Medium/low confidence — re-verify** |
| UKC-C2 | bidstats.uk — Lecture Capture System [Award] / Lecture Capture Software Solution (Panopto) [Award] | https://bidstats.uk/tenders/2024/W30/827327063 | **Fetch returned HTTP 403** — figures from search result summary only | University of Sheffield → Echo360, £195K. Royal Holloway → Panopto, £172K. **Low confidence** |
| ASR-C1 | arXiv — Measuring the Accuracy of Automatic Speech Recognition Solutions (Kuhn, Kersken, Reuter, Egger, Zimmermann, 2024) | https://arxiv.org/abs/2408.16287 | Fetched | Eleven common ASR services evaluated; "accuracy ranges widely between vendors and for the individual audio samples"; "despite the recent improvements of ASR, common services lack reliability in accuracy"; "significant lower quality for streaming ASR, which is used for live events" |
| ASR-C2 | Same study — search result detail | https://arxiv.org/pdf/2408.16287 | Search result | Higher Education lectures used as the use case; "even providers that achieve a relatively low average WER can show a high error rate for an individual audio sample"; no vendor consistently lowest across all samples; state-of-the-art English average around 5% WER |
| ASR-C3 | ACM Transactions on Accessible Computing — same paper | https://dl.acm.org/doi/10.1145/3636513 | **Fetch returned HTTP 403** — cited via arXiv version | Published venue reference |
| ASRMED-C1 | Search-aggregated research findings on ASR and specialised terminology | https://dl.acm.org/doi/10.1145/3636513 (and related medical ASR literature) | Search result aggregate | WER "from 0.087 in controlled dictation settings to over 50% in conversational or multi-speaker scenarios"; medical communication scenarios 0.122–0.228 WER; commercial ASR "exhibited high word error rates particularly with specialized academic terminology". **Aggregated from multiple sources; individual papers not fetched — medium confidence** |
| 3PLAY-C1 | 3Play Media — 2025 State of ASR Report press release | https://www.3playmedia.com/news/2025-asr-report-release/ | Fetched | Published 20 May 2025; 205 hours, 1.7m+ words, eight ASR engines plus Gemini; "error rates across all engines still fall short of meeting accessibility requirements"; sports error rates 3× higher than best-performing industries; "human-in-the-loop workflows remain critical" |
| 3PLAY-C2 | 3Play Media — annual State of ASR study (2024) | https://www.3playmedia.com/blog/annual-state-of-asr-study/ | Fetched | "ASR alone is still insufficient for the captioning use case, especially regarding formatting and hallucinations"; hallucinations problematic particularly in Whisper |
| EPIPN-C1 | Epiphan Video — Pearl Nexus | https://www.epiphan.com/products/pearl-nexus/ | Search result | Records and streams up to 3 channels of 1080p; SDI, HDMI, USB, SRT, NDI video inputs; XLR, USB, 3.5mm audio inputs; cloud management |
| EPIP2-C1 | Epiphan Video — Pearl multi-source recording | https://www.epiphan.com/userguides/pearl-2/Content/UserGuides/Streaming/record/recordBasics.htm | Search result | Pearl can capture synchronised video at 1080p30 from up to six sources |
| EPIPEC-C1 | Epiphan Video — EC20 PTZ Camera | https://www.epiphan.com/products/ec20/ | Search result | 4K, AI tracking; Dante, HDMI, SDI, USB; integrates with Q-SYS and Crestron |
| DANTE-C1 | Medium (Blair Liikala) — Case Study: Recording with Networked Audio | https://skippybla.medium.com/dante-audio-upgrade-80b86e5bb30a | Search result | University of North Texas College of Music moved recording and streaming to a Dante network; ~1,000 events annually including multi-camera shoots, live streaming, classical recitals, jazz |
| DANTE2-C1 | Yamaha — Live recording guide (Dante) | https://hu.yamaha.com/files/download/other_assets/2/1203362/live_recording_guide_dante_en.pdf | Search result | Dante "one of the easiest methods of capturing live recordings with a large number of audio channels" |
| 1EDT-C1 | 1EdTech — LTI Advantage certification and product directory | https://www.imsglobal.org/ltiadvantage | Search result | "LTI Advantage Complete" awarded for LTI 1.3 Core plus all three Advantage services; Kaltura among certified organisations; **YuJa not found in the searched results** |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| README.md | `002-lecture-capture/external/` | ArcKit scaffold guidance; no project content |
| consultant-brief.md | `002-lecture-capture/external/` | Read for engagement context; WP3/WP6 scope already carried into ARC-002-REQ and not re-cited here to avoid second-hand traceability |
| requirements-register.md | `002-lecture-capture/external/` | Survey requirements consumed via ARC-002-REQ, which decomposes them into the testable IDs this research is scoped against |
| capability-taxonomy.md | `000-global/external/` | Taxonomy definitions inherited via ARC-002-REQ Appendix A |
| DEMO.md | Repository root | Read to confirm the fictional-client framing and Australian scope; contains no technical content bearing on vendor assessment |

---

**Generated by**: ArcKit `/arckit:research` command
**Generated on**: 2026-07-27
**ArcKit Version**: 6.7.2
**Project**: Lecture Capture Platform Consolidation (Project 002)
**Model**: Claude Opus 5 (1M context)
**Generation Context**: Derived from ARC-002-REQ-v1.0 (requirement subset and mandatory gates), ARC-002-STKE-v1.0 (conflicts and drivers), ARC-002-RISK-v1.0 (R-006, R-007, R-011, R-012, R-020, R-022) and ARC-000-PRIN-v1.0 (Principles 2, 4, 8, 9, 12, 13, 14, 18, 19), with primary market research conducted via web search and fetch on 2026-07-27. UK Digital Marketplace, G-Cloud, CCS and DOS frameworks deliberately excluded as inapplicable to an Australian university.

<!-- arckit-provenance:start -->

## Build Provenance

_Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix._

| Field | Value |
|-------|-------|
| Requested Effort | `max` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-07-28T04:27:49.595Z |

<!-- arckit-provenance:end -->
