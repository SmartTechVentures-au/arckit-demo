# Vendor Profile: Microsoft (Teams + Stream on SharePoint)

> **Template Origin**: Official | **ArcKit Version**: 6.7.2 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-VEND-microsoft-v1.0 |
| **Document Type** | Vendor Profile |
| **Project** | Lecture Capture Platform Consolidation (Project 002) |
| **Classification** | OFFICIAL-SENSITIVE |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-27 |
| **Last Researched** | 2026-07-27 |
| **Review Date** | 2026-08-26 |
| **Owner** | Dr. Benny Moog, Director Learning Technologies |
| **Confidence** | **HIGH** — 8+ data points, all from official Microsoft Learn documentation |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Project Team, Procurement, Digital & IT |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-27 | ArcKit AI | Initial creation from `/arckit:research` | PENDING | PENDING |

---

## Overview

Microsoft is not a lecture capture vendor. It is a general-purpose collaboration and productivity platform vendor whose stack — **Microsoft Teams** for meetings and **Stream (on SharePoint)** for video — is already licensed at The University of Funk and is the CIO's preferred consolidation target [S-C1].

This profile exists because Principle 19 (*Realise Licensed Capability Before New Spend*) requires the university to evaluate configuring and adopting already-licensed capability before acquiring a new platform. That evaluation must be honest in both directions, and the honest finding is: **the Microsoft option is not "capability we already own, switched on". It is "capability we already own, plus a licence uplift, plus an integration build."** Whether that is still the best value is a cost question that cannot be answered until D-2 (the Microsoft entitlement position) is delivered.

Microsoft's strengths here are real and structural — identity, data residency and data portability are all best-in-class by construction. Its weakness is equally structural: it models a *meeting*, not a *capture schedule*.

## Products & Services (relevant scope)

- **Microsoft Teams** — meetings, recording, transcription; the live-delivery and recording surface
- **Microsoft Stream (on SharePoint)** — enterprise video management. Videos stored in SharePoint/OneDrive with "admin control of storage, management, compliance, governance, & life cycle capabilities" [M-C3]. Available to all Microsoft 365 customers with SharePoint and OneDrive, including **Education** plans [M-C3]
- **Microsoft Teams Rooms** (Basic / Pro) — room device licensing
- **Teams Premium** — required for assigned meeting templates [M-C2]
- **Microsoft 365 LTI app** — the current Blackboard integration path, registered as an LTI 1.3/Advantage tool [M-C5]
- **Microsoft Entra ID** — identity, with SCIM as the documented provisioning pattern [M-C8]

## Pricing Model

Mixed: entitlement (already held, extent unknown) plus published per-room and per-user list prices.

| Item | Published price | Status | Source |
|---|---|---|---|
| **Microsoft Teams Rooms Pro** | **US$40.00 per room per month, paid yearly** | ✅ **Published list price** — the only room-side cost in this whole procurement with a knowable public figure | [M-C4] |
| Microsoft Teams Rooms Basic | Not shown on the fetched page | Unavailable | [M-C4] |
| Teams Premium | Reported at US$10/user/month in secondary sources | ⚠️ **NOT VERIFIED against a Microsoft-published page.** Education pricing not located. **Do not use without verification** | — |
| Microsoft 365 A1 / A3 / A5 | Not established | The relevant question is **what UoF already holds** — this is dependency D-2 | — |

**No AUD conversion has been applied.** Applying an exchange rate to a US list price and presenting it as an Australian cost would manufacture false precision.

> **Cost-shape warning for BR-003 and Conflict C-2.** Teams Rooms Pro is a **recurring per-room opex** licence, indefinitely. Specialist platforms concentrate room-side cost in **periodic capital** (appliances). Over the five-year model these are not comparable line-for-line, and the Microsoft room licence must be modelled across the full five years in the **"decision-caused"** column, because it is entirely a consequence of the platform decision.

## Australian Higher Education Presence

- **Australian data residency**: ✅ **CONFIRMED — the strongest position of any candidate.** Australia is listed as a Microsoft 365 *Local Region Geography*, with data centre locations in **Sydney and Melbourne** [M-C1]. Exchange Online, SharePoint/OneDrive, Microsoft Teams and Copilot all carry **P-M-A** for Australia — Product Terms data residency, Multi-Geo, and Advanced Data Residency [M-C1]. Because Teams meeting recordings land in OneDrive/SharePoint [M-C3], the recordings themselves fall inside those commitments.
- **Sector purchasing**: Microsoft education agreements are typically negotiated institutionally or via aggregators; no Australian sector panel was researched.

## UK Government Presence

**Not applicable to this project.** The client is an Australian university.

## Government Award History

`{not applicable}` — no UK tender evidence gathered, and none is relevant to an Australian university procurement.

## Strengths

- ✅ **Best-in-class data residency, contractually backed.** Australia as a Local Region Geography with three separate durable-commitment mechanisms (Product Terms, Multi-Geo, ADR) [M-C1]. This is a *contractual* residency commitment, not a configuration setting — materially stronger than competitors whose position rests on a marketing page. Directly supports NFR-C-001, DR-006 and Principle 8.
- ✅ **Strongest identity and provisioning position by construction.** Entra ID native; SCIM is Microsoft's own documented provisioning standard [M-C8]. If REQ-025 / Principle 12 / risk R-022 were the only criteria, Microsoft would win outright — the CSV workaround for casual staff cannot survive in an Entra-driven model.
- ✅ **Strongest data portability position.** Recordings are ordinary files in SharePoint/OneDrive, in a tenant the university already administers, with admin control over storage, governance and lifecycle [M-C3] — not locked inside a video-platform silo. Against NFR-I-002 and Principle 9 this is the least lock-in of any candidate.
- ✅ **Zero incremental platform licence for the video layer.** Stream (on SharePoint) is available to all Microsoft 365 customers with SharePoint and OneDrive, explicitly including Education plans, with transcript generation for uploaded videos included [M-C3].
- ✅ **Current, documented Blackboard LTI 1.3 path.** The Microsoft 365 LTI app registers via Blackboard's "Register LTI 1.3/Advantage Tool" with a published Client ID [M-C5].
- ✅ **Reduces platform count.** Consolidating Learning Delivery and Learning Capture onto an already-licensed platform is the outcome Principle 2 and Principle 19 both point toward, and it removes an integration, a patching surface and a support queue.

## Weaknesses

- ❌ **No timetable-driven automatic capture — this is the decisive gap.** Microsoft's own documentation states that enabling the auto-recording policy "gives the organizer access to" the option, and that organizers **"must manually enable Record and transcribe automatically setting for each meeting they want recorded and transcribed automatically"** [M-C2]. There is no tenant-wide force-record control. **FR-001 requires capture to begin "automatically with no human action"; NFR-U-001 requires "zero academic actions".** On documented behaviour, Microsoft does not meet this natively.
- ❌ **The only automation path requires Teams Premium.** "Only organizers with a Teams Premium license can use assigned meeting templates" [M-C2]. Automating capture therefore carries a per-organizer licence uplift on top of the room licence.
- ❌ **Satisfying FR-001 requires a bespoke integration build the university would own.** A service must, for every timetabled session in a capture-equipped room, create a Teams meeting with the correct organizer, room resource and enforced auto-record template; reconcile it against Allocate+ changes within the INT-002 one-hour SLA; and suppress recordings for cancelled sessions (FR-001 acceptance criterion 3). Nothing in the Microsoft stack supplies this. **It should be scrutinised with the same rigour a full custom build would attract** — including Principle 13's requirement that two people can run it, and the risk of Microsoft changing the meeting API.
- ❌ **Recurring per-room licensing at US$40/room/month Pro** [M-C4] — the highest and most explicit *recurring* room-side cost of any option, scaling linearly with the estate (D-3).
- ❌ **Classic Teams LTI apps have been retired.** The classic Teams Classes and Teams Meetings app **sunset on 15 September 2025** [M-C6]. The replacement Meetings app displays only "the previous six months and upcoming six months of meetings scheduled" [M-C6] — a rolling twelve-month window that sits awkwardly against a multi-year recordings retention schedule (DR-005).
- ❌ **Identity-matching precondition.** The Microsoft 365 LTI app requires the Blackboard user's Email or Institutional Email field to be populated with the Entra UPN or primary email **for every course using the integration** [M-C5]. Real work, dependent on D-7.
- ❌ **Enterprise video management gaps.** Stream (on SharePoint) is documented for lightweight video sharing; the service description lists upload, management, screen/webcam recording, transcripts and transcript search — but no lecture-capture scheduling, no engagement analytics of the kind FR-011 describes, and no caption-correction workflow of the kind FR-007 describes [M-C3].
- ⚠️ **Product-level WCAG 2.2 AA conformance for the Stream/Teams playback experience was NOT VERIFIED.** The service description points to the Microsoft Trust Center for accessibility [M-C3] but no product-level 2.2 AA conformance statement was located. NFR-C-002 is a mandatory gate; this must be obtained.

## Assessment Against Mandatory Gates

| Gate | Position | Evidence status |
|------|----------|-----------------|
| NFR-SEC-001 (SSO+MFA, no local accounts) | **Structural pass** — Entra-native | Strongest candidate |
| NFR-C-002 (WCAG 2.2 AA + captioning) | **NOT VERIFIED** at product level | Must obtain conformance statement |
| NFR-I-002 (open-format bulk export, no fee, no vendor assistance) | **Structurally strongest** — files in the university's own tenant [M-C3] | Caveat: course-context association is time-bounded by the ±6-month LTI window [M-C6] |

## Assessment Against Requirements — Summary

| Requirement | Position |
|---|---|
| FR-001 (automatic scheduled capture) | ❌ Not native; requires build [M-C2] |
| FR-002 (4-hour publication to unit site) | ⚠️ Depends on the build |
| FR-008 (live delivery with recording) | ✅ Native strength |
| FR-016 (access derived from enrolment) | ✅ Strong via Entra + LTI [M-C5] |
| NFR-C-001 (AU residency) | ✅ Strongest of all candidates [M-C1] |
| NFR-I-001 (LTI 1.3) | ✅ Documented [M-C5] |
| NFR-I-002 (export) | ✅ Structurally strongest [M-C3] |
| REQ-025 (automated provisioning) | ✅ Strongest of all candidates [M-C8] |
| REQ-010 / FR-009 (performance capture) | ❌ Not addressed; requires the discipline exception regardless |

## Open Questions for Evaluation

1. **D-2: what capture/streaming capability does UoF's existing A-series entitlement actually include?** This is the single highest-leverage unknown in the project.
2. What is the verified Teams Premium price for education, and how many organizer identities would need it?
3. What is the estimated build effort for the timetable-to-Teams-meeting scheduling service, and who maintains it after go-live (Principle 13)?
4. Is there a product-level WCAG 2.2 AA conformance statement for the Stream/Teams playback experience?
5. How would FR-007 (caption correction with a persistent vocabulary list) and FR-011 (per-unit engagement analytics with cohort-size suppression) be delivered?
6. How many capture-equipped rooms would require Teams Rooms devices and licences (D-3)?

## Projects Referenced In

- `002-lecture-capture` — Lecture Capture Platform Consolidation (Principle 19 candidate; proposed for shortlist)

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RSCH | ARC-002-RSCH-v1.0.md | ArcKit artifact | `002-lecture-capture/research/` | Parent research findings document |
| REQ | ARC-002-REQ-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Requirements and mandatory gates |
| S | stakeholders.md | Engagement input | `002-lecture-capture/external/` | Stakeholder register (CIO platform position) |

### Citations

| Citation ID | Source | URL | Fetch status | Claim supported |
|-------------|--------|-----|--------------|-----------------|
| M-C1 | Microsoft Learn — Microsoft 365 data residency overview | https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview | Fetched (doc updated 2026-05-06) | Australia a Local Region Geography; Table 3 shows P-M-A for Exchange, SharePoint/OneDrive, Teams, Copilot; Table 4 data centre locations Melbourne, Sydney |
| M-C2 | Microsoft Learn — Manage Teams meeting auto recording | https://learn.microsoft.com/en-us/microsoftteams/manage-teams-auto-recording | Fetched (doc updated 2026-05-11) | "Organizers must manually enable Record and transcribe automatically setting for each meeting"; "Only organizers with a Teams Premium license can use assigned meeting templates"; PowerShell `-AutoRecording` parameter |
| M-C3 | Microsoft Learn — Microsoft Stream service description | https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-stream | Fetched | Stream on SharePoint; storage in SharePoint/OneDrive with "admin control of storage, management, compliance, governance, & life cycle capabilities"; feature table shows Education column; transcripts for uploaded videos |
| M-C4 | Microsoft — Teams Rooms Pro product page | https://www.microsoft.com/en-us/microsoft-teams/teamsroomspro | Fetched | "$40.00 room/month, paid yearly"; AI-powered audio/video, remote room management, AI-enhanced device management |
| M-C5 | Microsoft Learn — Deploy the Microsoft 365 LTI app in Blackboard by Anthology | https://learn.microsoft.com/en-us/microsoft-365/lti/microsoft-365-lti-blackboard | Fetched (doc updated 2026-06-02) | Registered via "Register LTI 1.3/Advantage Tool" with published Client ID; requires Blackboard Email/Institutional Email populated with Entra UPN or primary email |
| M-C6 | Microsoft Learn — same page, migration guidance | https://learn.microsoft.com/en-us/microsoft-365/lti/microsoft-365-lti-blackboard | Fetched | "The classic Teams Classes and Teams Meetings app has sunset as of September 15, 2025"; new Meetings app shows only previous and upcoming six months of meetings |
| M-C7 | Microsoft Community Hub — Automatic Teams meeting recording: why the policy alone is not enough | https://techcommunity.microsoft.com/blog/microsoftteamssupport/automatic-teams-meeting-recording-why-the-policy-alone-is-not-enough/4517517 | Search result | Corroborates that the auto-recording policy alone does not record every meeting; no org-wide setting to force auto-record |
| M-C8 | Microsoft Learn — SCIM provisioning for apps from Microsoft Entra ID | https://learn.microsoft.com/en-us/entra/identity/app-provisioning/use-scim-to-provision-users-and-groups | Search result | SCIM is Microsoft's documented provisioning pattern for Entra ID |

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
