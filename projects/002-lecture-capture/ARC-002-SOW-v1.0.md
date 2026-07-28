# Statement of Work (SOW): Lecture Capture Platform Consolidation

> **Template Origin**: Official | **ArcKit Version**: 6.7.2 | **Command**: `/arckit:sow`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-SOW-v1.0 |
| **Document Type** | Statement of Work / Request for Proposal |
| **Project** | Lecture Capture Platform Consolidation (Project 002) |
| **Classification** | OFFICIAL-SENSITIVE — pre-issue; becomes PUBLIC on release to suppliers |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-28 |
| **Last Modified** | 2026-07-28 |
| **Review Date** | 2026-08-27 |
| **Owner** | Grace Tanaka, Procurement & Vendor Manager |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Evaluation Panel; Steering Committee; Procurement; Legal. Released to suppliers on issue. |

> **Procurement route.** The University has determined that this requirement will be met through a **competitive tender**, tested against the market, rather than by varying an existing agreement. That determination resolves Conflict C-5 in ARC-002-REQ and is recorded in the decision file; the written value-for-money rationale required by the RIFF duplication rule [SGP-C2] accompanies it.
>
> **Do not issue this document to any supplier before** the evaluation criteria at ARC-002-EVAL-v1.0 are signed under BR-004. Criteria must be fixed before suppliers are engaged; issuing scope without settled criteria voids that control.

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-28 | ArcKit AI | Initial creation from `/arckit:sow` command | [PENDING] | [PENDING] |

## Document Purpose

This Statement of Work defines the scope, requirements, deliverables and commercial terms for the supply and implementation of a consolidated lecture capture platform for The University of Funk, for the 2027 academic year.

It is the scope-side companion to **ARC-002-EVAL-v1.0**, which defines how proposals will be assessed. The two are read together: this document states *what is required*; the evaluation framework states *how compliance will be measured and scored*. Suppliers receive both.

---

## 1. Executive Summary

### 1.1 Purpose of This SOW

The University of Funk invites proposals for a single primary platform serving the **Learning Capture** capability category, with defined interfaces to Learning Delivery, for deployment before Semester 2, 2027.

### 1.2 Background

The University's learning and teaching technology ecosystem currently carries three platforms with overlapping capture and delivery capability [SL-C1]. This overlap creates duplicated licensing, three integration surfaces to secure and support, and inconsistent student experience between units and schools.

A Learning & Teaching Baseline Strategy engagement identified the consolidation of this category as a decision that must be resolved before the target-state architecture can be finalised [CB-C1]. This procurement implements that decision.

Two features of the University's context materially shape this requirement and suppliers should understand them before responding:

1. **The University operates under Australian privacy law.** Recordings capturing students are personal information with a biometric-adjacent character. Data residency and cross-border disclosure are assessed requirements, not preferences (Section 3.4).
2. **The University has an existing recordings archive that must survive the transition.** Exit capability — of the incumbent platform and of the platform selected here — is a first-order requirement, not a contractual afterthought (Section 3.5).

### 1.3 Project Overview

| Attribute | Detail |
|-----------|--------|
| **Capability sought** | Automatic capture, processing, captioning, publication and lifecycle management of recorded teaching |
| **Scale** | All capture-equipped teaching spaces across the University; all enrolled students and teaching staff. **Room count and archive volume to be confirmed in the Supplier Information Pack at issue** |
| **Deployment target** | Pilot Semester 1 2027; full production before Semester 2 2027 |
| **Cutover window** | July 2027 inter-semester break. **No cutover activity in a teaching period will be accepted** |
| **Contract shape** | Hybrid — fixed subscription, fixed-price implementation, time-and-materials for agreed change (Section 9.1) |
| **Term** | Initial term with at least one renewal modelled; five-year whole-of-life basis |

### 1.4 Success Criteria

The engagement succeeds if, at the start of Semester 2 2027:

- Every timetabled lecture in a capture-equipped room is captured automatically and published to the unit site within 4 hours, with no academic intervention
- No manual account provisioning occurs, and no local accounts exist on the platform
- Every published recording carries captions meeting the University's measured accuracy standard within 24 hours
- The retained recordings archive is accessible, with existing links resolving
- Availability during teaching periods meets 99.9%
- No recordings were lost in transition

---

## 2. Scope of Work

### 2.1 In Scope

| # | Item | Requirement refs |
|---|------|------------------|
| S-1 | Supply of a lecture capture and video management platform under subscription | BR-001 |
| S-2 | Automatic, timetable-driven capture in capture-equipped teaching spaces | FR-001, REQ-009 |
| S-3 | Processing, captioning and publication to Blackboard Ultra unit sites | FR-002, FR-006, INT-003 |
| S-4 | Live class delivery with recording, where the proposed platform serves that capability | FR-008, REQ-008 |
| S-5 | Automated, event-driven user provisioning integrated with University identity and student systems | FR-016, INT-001, INT-004 |
| S-6 | Timetable feed integration for capture scheduling | INT-002 |
| S-7 | Room device integration, management, health telemetry and patching | INT-006, NFR-SEC-004 |
| S-8 | Migration of the retained recordings archive with captions and metadata intact | FR-015, INT-007, BR-007 |
| S-9 | Retention schedule configuration, disposal and legal hold | FR-014, DR-005 |
| S-10 | Analytics export to the institutional data platform | FR-011, INT-005 |
| S-11 | Implementation services: configuration, integration build support, migration execution support | BR-006 |
| S-12 | Training for academic staff, support staff and AV technicians | NFR-M-002 |
| S-13 | Operational documentation and runbooks, delivered before cutover | NFR-M-002 |
| S-14 | Support and maintenance for the contract term, Australian business hours minimum | NFR-A-001 |

### 2.2 Out of Scope

| # | Item | Why excluded |
|---|------|--------------|
| X-1 | Replacement of the Learning Management System | Blackboard Ultra is retained; the platform integrates with it |
| X-2 | Replacement of the student information system or timetabling system | The platform consumes their data; it does not replace them |
| X-3 | Delivery of the University's canonical data model and role-assignment source | Delivered under project 001; consumed here (REQ-027, REQ-024) |
| X-4 | Clinical simulation capture within iSimulate and Kuracloud | Assessed for interface only; those products are retained |
| X-5 | Non-teaching meeting and collaboration use of video conferencing | This procurement addresses teaching use only |
| X-6 | Multi-camera performance capture hardware for Music venues | Procured separately as a bounded discipline exception (Section 2.4) |
| X-7 | Capture appliance replacement where required by estate age | Assessed separately; suppliers must state hardware compatibility (Section 3.6) but do not tender for estate refresh |
| X-8 | Assessment, portfolio, plagiarism and examination platforms | Different capability categories |

### 2.3 Client Responsibilities

The University will provide:

| # | Responsibility | Owner | By |
|---|---------------|-------|-----|
| C-1 | Access to a Blackboard Ultra test instance for integration demonstration | Dr. Benny Moog | At evaluation |
| C-2 | Test identity feed and role model for provisioning demonstration | Sam Okafor | At evaluation |
| C-3 | Discipline-vocabulary test set for caption accuracy measurement | Dr. Benny Moog | 2026-09-04 |
| C-4 | Room inventory, models and network conditions | Marcus Fairlight | At issue |
| C-5 | Archive volume, format and metadata schema | Eleanor Frame | At issue |
| C-6 | Approved retention schedule for configuration | Eleanor Frame | 2027-04-30 |
| C-7 | Timetable data feed specification | Ivy Sequence | At contract |
| C-8 | Room access for installation and configuration in non-teaching periods | Marcus Fairlight | July 2027 |
| C-9 | Single point of supplier contact throughout | Grace Tanaka | Throughout |

### 2.4 Related but Separately Procured

Multi-camera, high-fidelity performance capture for named Music & Performing Arts venues (REQ-010, FR-009) is a bounded discipline exception under the University's architecture principles. It is decided in the same governance cycle as this procurement but procured separately.

**Suppliers must nonetheless state**, in response to Section 7.1(f), how their platform ingests and associates an externally produced media file, so that specialist recordings publish through the same route and identity model as core capture. This is a scored criterion.

### 2.5 Assumptions

| # | Assumption | If invalid |
|---|-----------|-----------|
| A-1 | Timetable data is authoritative for room, time and unit, and available for the full teaching period | Automatic scheduling scope reduces; FR-001 renegotiated |
| A-2 | Blackboard Ultra unit sites exist with provisioned cohorts before teaching begins | Publication target changes |
| A-3 | Room appliances can report health telemetry to a central point | Estate refresh scope increases; supplier not liable |
| A-4 | Project 001 delivers the canonical model and role-assignment source before integration build | Integration timeline extends; change control applies |
| A-5 | The incumbent platform permits bulk export of media, captions and metadata | Migration scope and cost change materially — see Section 9.7 |
| A-6 | Rights and consent for recorded performance are addressed under University policy | Out of supplier scope |

> **A-5 is unconfirmed at the date of this document.** Contract review is due 2026-08-14. Suppliers should price migration on the assumption that the University supplies an export in a documented open format, and should state separately any charge that would apply if source content requires format conversion.

---

## 3. Requirements

The full requirement set is **ARC-002-REQ-v1.0**, which is incorporated into this SOW by reference and supplied to suppliers with it. Requirements below are stated in summary; the referenced document governs in the event of any inconsistency.

**Priority convention**: MUST requirements are mandatory. A proposal that cannot meet a MUST requirement, or that meets it only through a workaround the University has not accepted in writing, may be disqualified. SHOULD requirements are scored. COULD requirements are scored at low weight.

### 3.1 Mandatory Compliance Gates — Pass/Fail

Three requirements are assessed pass/fail before scoring begins. **Failure of any one eliminates the proposal**, regardless of merit elsewhere. Assessment method is defined in ARC-002-EVAL-v1.0 §3.

| Gate | Requirement | Evidence the University requires |
|------|-------------|----------------------------------|
| **MQ-1** | University SSO with MFA enforced. **No local accounts, no platform-native passwords**, including for room devices and service identities (NFR-SEC-001, REQ-031) | Hands-on demonstration against the University identity provider in a trial tenant. Written attestation alone is insufficient |
| **MQ-2** | WCAG 2.2 Level AA conformance for the platform as configured (NFR-C-002, REQ-029) | Current VPAT or independent audit report, **or** a dated, contractually-committed remediation plan reaching 2.2 AA before cutover with 2.1 AA evidenced now |
| **MQ-3** | Bulk export of recordings **with captions and metadata** in open, documented formats, at any time and on termination, **without additional fee** (NFR-I-002, REQ-034) | Practical export executed on a sample during evaluation, plus the contractual term in writing |
| **MQ-4** | Australian data residency for recordings, transcripts and derived analytics — or a written statement of storage **and processing** locations sufficient for the University to complete a cross-border disclosure assessment (NFR-C-001, REQ-030) | Written statement addressing storage and processing separately |

### 3.2 Business Requirements

| ID | Requirement | Priority |
|----|-------------|----------|
| BR-001 | One primary platform for Learning Capture with a declared boundary | MUST |
| BR-003 | Whole-of-life cost held flat or reduced over five years | SHOULD |
| BR-006 | Transition completed without teaching disruption; pilot S1 2027, cutover July 2027 | MUST |
| BR-007 | Retained recordings accessible; exit rights proven before contract signature | MUST |
| BR-008 | Capture estate brought within managed patching; no shared administrative accounts | MUST |

### 3.3 Functional Requirements

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-001 | Automatic scheduled capture from timetable data, no human action | MUST |
| FR-002 | Publication to the unit site within 4 hours of session end | MUST |
| FR-003 | Ad-hoc capture initiated by teaching staff in no more than two actions | MUST |
| FR-004 | Capture failure detection, alerting and recovery | MUST |
| FR-005 | Recording review, trim and segment removal by teaching staff | MUST |
| FR-006 | Automatic captioning and searchable transcript within 24 hours | MUST |
| FR-007 | Caption correction workflow with vocabulary list support | SHOULD |
| FR-008 | Live class delivery with breakout rooms, polling and recording | MUST |
| FR-009 | Multi-camera, high-fidelity performance capture (separately procured — Section 2.4) | COULD |
| FR-010 | Student playback: search, speed, transcript navigation, mobile, resume | MUST |
| FR-011 | Engagement analytics per unit with small-cohort suppression | SHOULD |
| FR-012 | Unit-level capture policy with approval-referenced exceptions | MUST |
| FR-013 | Student notification of recording, in-platform and in-room | MUST |
| FR-014 | Retention schedule application, pre-disposal notification, legal hold, archive-on-request | MUST |
| FR-015 | Archive migration with metadata and captions intact; link preservation | MUST |
| FR-016 | Role-based access derived from enrolment; no locally maintained access lists | MUST |
| FR-017 | Bulk export of recordings, captions, transcripts and metadata | MUST |
| FR-018 | Operational and compliance reporting without manual collation | MUST |

### 3.4 Non-Functional Requirements

**Security and privacy**

| ID | Requirement | Priority |
|----|-------------|----------|
| NFR-SEC-001 | SSO with MFA; no local accounts (gate MQ-1) | MUST |
| NFR-SEC-002 | RBAC with least privilege; no shared administrative accounts anywhere, including room devices | MUST |
| NFR-SEC-003 | TLS 1.3 in transit; AES-256 at rest including appliance local buffers, archive tier, backups and exports | MUST |
| NFR-SEC-004 | Room appliances within a managed patching regime; published vulnerability disclosure process; remediation SLAs — critical 48 hours, high 14 days, medium 30 days | MUST |
| NFR-C-001 | Privacy Act 1988 compliance; Australian residency; cross-border assessment where applicable (gate MQ-4) | MUST |
| NFR-C-003 | Tamper-evident audit logging of view, download, edit, publish, export and disposal | SHOULD |
| NFR-C-004 | Reporting sufficient to evidence Essential Eight maturity for the capture estate | SHOULD |
| NFR-C-005 | **Contractual commitment to notify the University of any actual or suspected breach within 24 hours** of becoming aware | MUST |

> **NFR-C-005 is not negotiable to a longer period.** The University carries a 30-day statutory assessment clock on eligible data breaches [PC-C1]. A notification obligation measured in days consumes that window before the University knows an incident has occurred.

**Availability, performance and operability**

| ID | Requirement | Priority |
|----|-------------|----------|
| NFR-A-001 | 99.9% availability during teaching periods, measured separately for capture, processing and playback. Maintenance scheduled outside teaching periods | MUST |
| NFR-A-002 | **RPO zero for recorded content** — no lecture lost to network or platform failure. Local buffering with a full teaching day's capacity | MUST |
| NFR-A-003 | Graceful degradation: room-level failure isolation; audio-only fallback | SHOULD |
| NFR-P-001 | Median publication latency under 1 hour; 99th percentile under 4 hours | MUST |
| NFR-P-002 | Playback start under 3 seconds at 95th percentile; adaptive bitrate | SHOULD |
| NFR-S-001 | Five-year volume growth accommodated without architectural change; defined storage tiering | SHOULD |
| NFR-M-001 | Central observability: room status, processing metrics, integration health, alert routing | SHOULD |
| NFR-M-002 | Runbooks and user documentation published **before** cutover | MUST |

**Accessibility and usability**

| ID | Requirement | Priority |
|----|-------------|----------|
| NFR-C-002 | WCAG 2.2 Level AA (gate MQ-2) | MUST |
| NFR-U-001 | Zero academic actions for scheduled capture; no more than two for ad-hoc | SHOULD |
| NFR-U-002 | Identical student experience across all schools and units | SHOULD |
| NFR-U-003 | Caption accuracy validated against the University's discipline-vocabulary test set. **Vendor accuracy claims are not accepted as evidence** | SHOULD |

**Integration and portability**

| ID | Requirement | Priority |
|----|-------------|----------|
| NFR-I-001 | Documented standard interfaces: LTI 1.3, SAML 2.0 or OIDC, SCIM or equivalent documented provisioning API, REST/JSON | MUST |
| NFR-I-002 | Open-format export at any time and on termination, without fee (gate MQ-3) | MUST |

### 3.5 Integration Requirements

| ID | Integration | Priority |
|----|-------------|----------|
| INT-001 | Student information system → platform: identity, enrolment, institutional roles, event-driven, 15-minute latency | MUST |
| INT-002 | Timetabling (Allocate+) → platform: session scheduling, reconciliation within 1 hour of change | MUST |
| INT-003 | Platform ↔ Blackboard Ultra: **LTI 1.3 with deep linking and names-and-roles**. Suppliers must state support at **section-level** granularity | MUST |
| INT-004 | Identity provider: SAML 2.0 or OIDC with MFA enforced at the IdP; no local credential fallback path may exist | MUST |
| INT-005 | Platform → institutional data platform: scheduled analytics export in a documented open format | SHOULD |
| INT-006 | Platform ↔ room appliances: schedule, capture, telemetry, patching, **per-device identity** | MUST |
| INT-007 | Incumbent → platform: one-time bulk archive migration with per-batch reconciliation | MUST |

> **INT-003 requires a specific answer.** Suppliers must state, without ambiguity: (a) whether LTI 1.3 is supported for Blackboard Ultra in production, (b) whether linking is supported at course-section granularity, and (c) whether the supplier's own guidance recommends LTI 1.1 for Blackboard migrations. This will be verified hands-on against the University's Blackboard Ultra instance.

### 3.6 Data Requirements

| ID | Requirement | Priority |
|----|-------------|----------|
| DR-001 | Recordings and derived assets handled as personal information throughout | MUST |
| DR-002 | Conformance to the University canonical model for student, course and enrolment | MUST |
| DR-003 | Engagement analytics minimisation; pseudonymised export; small-cohort suppression | MUST |
| DR-004 | Minimal identity projection — no passwords, no demographics; deprovisioned records removed within 90 days | MUST |
| DR-005 | Configurable retention schedule covering recordings, transcripts, captions and analytics identifiers | MUST |
| DR-006 | Documented storage and processing location per data class | MUST |
| DR-007 | Migration reconciliation by count and association, with provenance retained | MUST |

### 3.7 Technical Constraints

| ID | Constraint |
|----|-----------|
| TC-1 | Must integrate with the existing University identity provider; no local account path may exist |
| TC-2 | Must publish into Blackboard Ultra as the student entry point; a separate student portal is not acceptable as the primary route |
| TC-3 | Integrations must use the canonical entity model; point-to-point mappings against platform-specific schemas will not be accepted |
| TC-4 | The solution operates within the existing lecture-theatre estate. Options requiring appliance replacement must declare it, itemised and costed separately |
| TC-5 | Bulk user file loads are prohibited in production |

---

## 4. Deliverables

Deliverables are framed for a **SaaS subscription plus implementation services** engagement. The University is not commissioning bespoke software development; deliverables therefore concern configuration, integration, migration, enablement and evidence rather than source code and unit tests.

### 4.1 Design and Mobilisation Phase

| ID | Deliverable | Acceptance criteria | Due |
|----|-------------|--------------------|-----|
| D-1 | Solution Configuration Design — how the platform is configured to meet Sections 3.2–3.7 | Approved by Dr. Benny Moog and Sam Okafor; traces every MUST requirement to a configuration or interface | Contract + 4 weeks |
| D-2 | Integration Design — INT-001 to INT-006, including provisioning event model, timetable feed, LTI 1.3 placement | Approved by Sam Okafor; conforms to the canonical model; no bulk-import provisioning path | Contract + 6 weeks |
| D-3 | Migration Plan — INT-007, staged batches, reconciliation method, rollback, link preservation | Approved by Eleanor Frame and Rhonda Bell; reconciliation criteria explicit | Contract + 6 weeks |
| D-4 | Security and Privacy Design — authentication, RBAC, encryption, audit logging, residency statement | Approved by Tobias Ohm and Eleanor Frame; supports completion of the University's privacy impact assessment | Contract + 4 weeks |
| D-5 | Room Deployment Plan — per-room configuration, device identity, patching regime, works schedule | Approved by Marcus Fairlight; all works scheduled in non-teaching periods | Contract + 8 weeks |
| D-6 | Test Plan — including the pilot acceptance criteria at Section 5.2 | Approved by Rhonda Bell | Contract + 8 weeks |

### 4.2 Implementation Phase

| ID | Deliverable | Acceptance criteria | Due |
|----|-------------|--------------------|-----|
| D-7 | Configured production and non-production tenants | Meets D-1; accessible via University SSO with MFA; zero local accounts verified | Pre-pilot |
| D-8 | Integrations delivered and tested | Provisioning within 15 minutes verified; LTI 1.3 placement verified at section granularity on the University's Blackboard Ultra; timetable feed reconciling | Pre-pilot |
| D-9 | Room deployment completed | All prioritised rooms capturing; telemetry reporting; per-device identity; zero shared administrative accounts | Pre-cutover |
| D-10 | Archive migrated | 100% of in-retention recordings with metadata and captions; reconciliation signed off; link-check sweep clean | July 2027 |
| D-11 | Retention schedule configured | Disposal, notification, hold and archive-on-request all demonstrated | Pre-cutover |

### 4.3 Enablement and Handover

| ID | Deliverable | Acceptance criteria | Due |
|----|-------------|--------------------|-----|
| D-12 | Operational runbooks — one per failure class in FR-004 | Approved by Nina Kalimba; **published before cutover, not after** | Pre-cutover |
| D-13 | Academic quick reference and student help content | Approved by Dr. Benny Moog; accessible per WCAG 2.2 AA | Pre-cutover |
| D-14 | Training delivery — academics, casual staff, support team, AV technicians | Delivered before each cohort's first teaching week on the platform | Pre-cutover |
| D-15 | Accessibility conformance evidence — current VPAT or audit for the configured platform | Reviewed by Dr. Benny Moog with Student Guild input | At contract, refreshed annually |
| D-16 | Export demonstration — full export of media, captions and metadata in open formats | Executed on a sample, verified by Eleanor Frame | **Before contract signature**, repeated annually |

> **D-16 is a pre-signature deliverable.** Export capability asserted contractually but never tested is the failure mode this requirement exists to prevent.

### 4.4 Ongoing Service Deliverables

| ID | Deliverable | Frequency |
|----|-------------|-----------|
| D-17 | Availability and performance reporting against NFR-A-001 and NFR-P-001 | Monthly |
| D-18 | Capture coverage, publication latency and failure reporting (FR-018) | Monthly |
| D-19 | Captioning coverage report; support for University accuracy sampling | Each teaching period |
| D-20 | Patch status and administrative account inventory for the room estate | Monthly / quarterly |
| D-21 | Provisioning audit log extract | On request |
| D-22 | Roadmap briefing at current contract cost | Annually |

---

## 5. Project Timeline and Milestones

### 5.1 High-Level Timeline

| Phase | Duration | Period |
|-------|----------|--------|
| Procurement and award | 6 weeks | 2026-08-31 to 2026-10-09 |
| Contract and mobilisation | 9 weeks | 2026-10-12 to 2026-12-11 |
| Design | 8 weeks | 2026-12-14 to 2027-02-12 |
| Build and integration | 6 weeks | 2027-02-15 to 2027-02-26 (overlapping) |
| **Pilot — Semester 1 2027** | 17 weeks | 2027-03-01 to 2027-06-25 |
| Migration and cutover | 4 weeks | 2027-06-28 to 2027-07-24 |
| **Production — Semester 2 2027** | — | From 2027-07-27 |
| Incumbent decommissioning | — | 2027-12-11 |
| Essential Eight evidence complete | — | 2027-12-11 |

**Total: approximately 60 weeks from issue to production.**

### 5.2 Key Milestones and Gates

| # | Milestone | Gate criteria | Date |
|---|-----------|---------------|------|
| M-1 | SOW and criteria issued | ARC-002-EVAL signed under BR-004 | 2026-08-31 |
| M-2 | Proposals received | Complete, on time, cost envelope separate | 2026-09-07 |
| M-3 | Mandatory gates assessed | MQ-1 to MQ-4 evidenced hands-on | 2026-09-04 |
| M-4 | Evaluation complete | Scoring moderated per ARC-002-EVAL §6 | 2026-09-09 |
| M-5 | **RIFF review** | Recommendation endorsed; dissent recorded | 2026-09-11 |
| M-6 | **Education Committee approval** | Academic endorsement | 2026-09-25 |
| M-7 | **Operations Committee approval** | Financial and strategic approval | 2026-10-09 |
| M-8 | **Privacy impact assessment signed off** | No unmitigated high findings | 2026-12-04 |
| M-9 | **Contract executed** | M-8 complete; D-16 export demonstrated | 2026-12-11 |
| M-10 | Design approved | D-1 to D-6 accepted | 2027-02-12 |
| M-11 | Pilot entry | D-7, D-8 accepted; pilot acceptance criteria agreed | 2027-03-01 |
| M-12 | Pilot exit | No Must-priority capability regression; failure modes documented | 2027-06-25 |
| M-13 | **Migration reconciliation signed off** | Source-to-target reconciled; every difference explained | 2027-07-20 |
| M-14 | **Cutover go/no-go** | M-13 complete; D-12 to D-14 delivered; rooms ready | 2027-07-24 |
| M-15 | Incumbent decommissioned | Reconciliation signed; retention applied | 2027-12-11 |

> **M-8 and M-9 are sequenced deliberately.** The privacy impact assessment must be signed off before contract execution, not after. Suppliers should expect residency and processing-location questions during that period and should ensure the necessary statements are available.
>
> **M-13 gates M-15.** The incumbent platform is retained read-only until reconciliation is signed off. No supplier should assume decommissioning at cutover.

### 5.3 Proposal Timeline

| Event | Date |
|-------|------|
| SOW and evaluation criteria issued | 2026-08-31 |
| Supplier clarification questions due | 2026-09-02, 17:00 AEST |
| University responses issued to all suppliers | 2026-09-03 |
| **Proposals due** | **2026-09-07, 17:00 AEST** |
| Hands-on assessment sessions | 2026-09-01 to 2026-09-08 |
| Clarification interviews (if required) | 2026-09-08 |
| Evaluation moderation | 2026-09-09 |
| Suppliers notified of outcome | 2026-10-12 |

---

## 6. Supplier Qualifications

### 6.1 Mandatory Qualifications

Assessed pass/fail. These are in addition to the compliance gates at Section 3.1.

| # | Qualification | Evidence required |
|---|--------------|-------------------|
| Q-1 | Platform in production at a minimum of three higher-education institutions | Named institutions; at least two contactable references |
| Q-2 | At least one deployment at comparable scale in Australia or New Zealand, **or** a substantiated statement of Australian service capability | Reference or written capability statement |
| Q-3 | Documented support model covering Australian business hours | Support policy document |
| Q-4 | Evidence of financial standing sufficient to sustain a five-year term | Audited accounts or equivalent |
| Q-5 | Willingness to accept the mandatory contract terms at Section 9.7 | Written confirmation with the proposal |
| Q-6 | Proposal complete, on time, and with the cost envelope submitted separately | Procurement check |

> **Q-5 is assessed at proposal stage, not at negotiation.** Suppliers unwilling to commit to 24-hour breach notification, open-format export without fee, or a stated residency position should not tender. Late discovery of these positions wastes both parties' time.

### 6.2 Preferred Qualifications

Scored, not gated: prior Blackboard Ultra integration at section granularity; demonstrable caption accuracy in clinical or musical vocabulary; Australian data centre presence for both storage and processing; published accessibility conformance for the current release; experience migrating an archive from a competing platform.

### 6.3 Team Requirements

The University expects a named implementation lead, a named integration engineer, and a named migration lead, each available for the duration of their phase. **CVs for platform engineering staff are not required** — this is a subscription procurement, not a staff augmentation engagement. What the University requires is continuity of named accountable individuals and a stated escalation path.

---

## 7. Proposal Requirements

### 7.1 Proposal Format

Proposals must be submitted as **two separate PDF documents**: a Technical Proposal and a Cost Proposal. Cost information must not appear in the Technical Proposal.

**Technical Proposal — maximum 40 pages excluding appendices**, addressing in order:

| § | Content |
|---|---------|
| (a) | Compliance statement against Section 3.1 gates MQ-1 to MQ-4, with the evidence offered for each |
| (b) | Requirement compliance matrix — every requirement in Sections 3.2 to 3.7 marked Comply / Comply with qualification / Does not comply, with an explanation for anything other than Comply |
| (c) | Capture and publication approach — how FR-001 and FR-002 are achieved, including whether any user action, additional licence tier or university-built component is required |
| (d) | Integration approach — INT-001 to INT-006, with an explicit and unambiguous answer to the three INT-003 questions |
| (e) | Migration approach — INT-007, reconciliation, link preservation, and throughput against the July 2027 window |
| (f) | External media ingestion — how a media file produced outside the platform is ingested and associated (Section 2.4) |
| (g) | Accessibility and captioning — conformance evidence, accuracy methodology, correction workflow |
| (h) | Security, privacy and residency — including storage and processing locations stated separately |
| (i) | Service, support and availability — SLA offered, measurement method, exclusions |
| (j) | Implementation plan, resourcing and named leads |
| (k) | Assumptions, dependencies and risks the supplier carries |
| (l) | References — three, with contact details |

**Appendices permitted and not counted**: VPAT or accessibility audit, security certifications, SLA document, standard terms, roadmap.

### 7.2 Cost Proposal Format

The Cost Proposal must present a **five-year whole-of-life view** using the structure below. Suppliers must not aggregate lines.

| Line | Basis |
|------|-------|
| Platform subscription, years 1–5 | Fixed for the initial term; state uplift mechanism and cap for any renewal period |
| Per-room or per-device licensing, if applicable | State the unit and whether recurring or one-off |
| Implementation services | **Fixed price**, itemised by deliverable D-1 to D-14 |
| Migration services | **Fixed price**; state separately any charge arising if source content requires format conversion (Assumption A-5) |
| Training | Fixed price |
| Support and maintenance | Annual, stating what is included |
| Storage and processing beyond any included allowance | Unit rate and the included allowance |
| Egress, export or exit charges | **State explicitly, including nil** |
| Change requests | Time-and-materials day rates by role |
| Optional items | Priced separately and clearly marked optional |

All prices in **Australian dollars, exclusive of GST**, with GST shown separately.

> **Suppliers who cannot provide a five-year view should say so and explain why**, rather than providing a shorter term without comment. The University is assessing whole-of-life cost including at least one renewal, because renewal-point pricing exposure is a recorded project risk.

### 7.3 Submission Instructions

Submissions to **Grace Tanaka, Procurement & Vendor Manager**, by the deadline at Section 5.3, by the method stated in the issue letter.

**Probity — read carefully.** From the date this SOW is issued, all contact regarding this procurement must be through Grace Tanaka. Contact with any other University staff member regarding this procurement, including with individuals with whom a supplier holds an existing account relationship, may result in disqualification. Contact on existing contractual matters unrelated to this procurement remains permitted and will be logged.

Clarification questions and the University's responses are issued to **all** suppliers.

---

## 8. Evaluation

### 8.1 Governing Document

Proposals are evaluated **strictly in accordance with ARC-002-EVAL-v1.0**, issued with this SOW. That document defines the criteria, weightings, evidence rules, scoring scale and thresholds, and is signed by the University before issue. **It will not be amended after issue.**

This SOW does **not** restate the weightings, and no weighting stated or implied elsewhere in this document overrides the evaluation framework. Where any apparent inconsistency arises, ARC-002-EVAL-v1.0 governs.

### 8.2 Summary of the Approach

For supplier information:

- **Mandatory gates** (Section 3.1) are assessed first, pass/fail. Failure eliminates the proposal.
- **Scored categories** cover capability, accessibility, integration, security and privacy, portability and exit, operability, commercial, and supplier service. Weightings derive from the priority ratings in the University's requirement set, not from negotiation.
- **Evidence tier caps score.** Claims evidenced only by sales material cannot score above 50%. Ten specified sub-criteria cannot score above 50% without hands-on demonstration.
- **Technical scoring is locked before the cost envelope is opened.**
- **Thresholds**: a proposal must exceed an overall minimum, must not fall below a floor in any category, and must exceed a raised floor in security and privacy.
- **"Retain existing arrangements"** is evaluated as a comparator option. Suppliers should understand that a proposal must demonstrate benefit over the status quo, not merely over other proposals.

### 8.3 Hands-On Assessment

Suppliers reaching assessment must provide a **trial tenant** sufficient to demonstrate: SSO with MFA against the University identity provider; provisioning from a test identity feed; LTI 1.3 placement on the University's Blackboard Ultra instance at section granularity; caption generation against a University-supplied test set; export of a sample including captions and metadata; and capture continuity under network interruption.

**Inability or unwillingness to provide a trial tenant is itself assessed**, and caps the scores available on the affected criteria.

---

## 9. Contract Terms and Conditions

### 9.1 Contract Type — Hybrid

| Component | Basis |
|-----------|-------|
| Platform subscription | **Fixed** for the initial term, with a capped and indexed uplift mechanism for renewal |
| Implementation services | **Fixed price** against deliverables D-1 to D-14 |
| Migration services | **Fixed price**, with a stated rate for format conversion if Assumption A-5 fails |
| Change requests | **Time and materials** at tendered day rates, under the change process at Section 9.4 |
| Ongoing support | **Fixed annual**, included in subscription or stated separately |

This allocation places delivery risk on the supplier where scope is defined, and shares it where scope depends on inputs the University has not yet confirmed.

### 9.2 Payment Terms

Payment on acceptance of deliverables, not on elapsed time.

| Milestone | % of implementation fee |
|-----------|------------------------|
| Design accepted (D-1 to D-6) | 20% |
| Integrations delivered and tested (D-8) | 25% |
| Rooms deployed (D-9) | 15% |
| Migration reconciled and signed off (D-10, M-13) | 25% |
| Cutover complete and documentation delivered (D-12 to D-14) | 15% |

Subscription commences on the earlier of pilot entry (M-11) or production cutover, **not on contract signature**. Payment terms 30 days from valid invoice and acceptance.

### 9.3 Acceptance Criteria

A deliverable is accepted when it meets the criteria at Section 4 and the University confirms acceptance in writing within 15 business days. Where acceptance is withheld, the University states the deficiency; the supplier has 10 business days to remedy. Repeated failure to achieve acceptance on the same deliverable is a material breach.

**Pilot acceptance** (M-12) requires no regression against the incumbent baseline on any Must-priority requirement. The University may terminate at pilot exit without further liability beyond fees for accepted deliverables where pilot acceptance criteria are not met.

### 9.4 Change Management

All changes in writing, assessed for cost, schedule and requirement impact, approved by the University's Project Manager before work commences. Changes materially affecting a MUST requirement, the residency position, or the export terms require Steering Committee approval.

### 9.5 Data Ownership and Intellectual Property

Framed for SaaS. The University is **not** acquiring platform source code and does not seek to own it.

| Item | Position |
|------|----------|
| University data — recordings, transcripts, captions, metadata, analytics | **Owned by the University at all times.** The supplier holds it as a service provider with no rights of use beyond providing the service |
| Use of University data for model training or product improvement | **Prohibited without separate written consent.** This includes captioning and speech-recognition model training on University recordings |
| Configuration and integration artefacts produced under this engagement | Owned by the University |
| Platform software and supplier pre-existing IP | Retained by the supplier |
| University marks, content and course material | Retained by the University |

**Source code escrow is not required.** The University's continuity protection is the export capability at gate MQ-3 and the exit provisions at Section 9.7, which are more useful for a SaaS service than access to source code the University could not operate.

### 9.6 Warranties and Service Levels

| Item | Requirement |
|------|-------------|
| Availability | 99.9% during teaching periods, measured separately for capture, processing and playback |
| Service credits | Applicable for breach of the availability commitment; suppliers to propose a regime |
| Recording durability | **No recorded session may be lost due to platform or network failure.** Loss is a service failure, not a service credit event |
| Implementation warranty | 90 days from acceptance of each deliverable |
| Accessibility warranty | Conformance maintained across releases; regression is a defect |
| Security | Vulnerability remediation to the SLAs at NFR-SEC-004 |

### 9.7 Mandatory Terms

The following are **not negotiable**. Suppliers unable to accept them should not tender (Q-5).

1. **Breach notification within 24 hours** of the supplier becoming aware of any actual or suspected breach affecting University data, with sufficient detail to support the University's statutory assessment.
2. **Export at any time and on termination**, of recordings, captions, transcripts and metadata in open documented formats, **without additional fee** and without requiring supplier assistance as a precondition.
3. **Stated data residency**, covering storage and processing separately, with written notice before any change to processing location.
4. **No use of University data for model training** without separate written consent.
5. **Read-only access to University data for 90 days after termination**, to permit orderly transition.
6. **No local accounts.** Authentication exclusively via University SSO with MFA.
7. **Renewal price protection** — a capped, indexed uplift mechanism for at least the first renewal.

### 9.8 Termination

The University may terminate: for convenience on 90 days' notice, with fees payable for accepted deliverables only; for material breach not remedied within 30 days; at pilot exit where acceptance criteria are not met (Section 9.3); or where the supplier changes processing location in breach of term 3 above.

On termination for any reason, the export and 90-day read-only obligations at Section 9.7 survive.

---

## 10. Appendices

### Appendix A: Reference Documents Supplied to Suppliers

| Document | Supplied |
|----------|----------|
| ARC-002-REQ-v1.0 — Requirements | Yes, in full |
| ARC-002-EVAL-v1.0 — Evaluation criteria (Sections 3–5 only) | Yes, on issue |
| Supplier Information Pack — room counts, archive volume, cohort sizes, network conditions | Yes, at issue |
| Blackboard Ultra environment specification | On request |
| ARC-002-STKE, ARC-002-RISK, ARC-002-RSCH | **No — internal only** |

### Appendix B: Glossary

| Term | Definition |
|------|------------|
| **APP** | Australian Privacy Principle under the Privacy Act 1988 |
| **Capture-equipped room** | A teaching space with installed capture appliance capability |
| **Essential Eight** | ASD cyber mitigation strategies with maturity levels ML0–ML3 |
| **LTI 1.3 / LTI Advantage** | Learning Tools Interoperability standard for LMS integration |
| **RIFF Review** | Review of Innovation, Fit & Function — the University's solution governance gate |
| **Teaching period** | Weeks in which timetabled teaching occurs, excluding inter-semester breaks |
| **Unit** | A single subject of study; the Blackboard Ultra unit site is the student entry point |
| **WCAG 2.2 AA** | Web Content Accessibility Guidelines, conformance level AA |

### Appendix C: Architecture Principles Applied

Suppliers should understand that the following University principles shape the requirements and will be applied in assessment. The full principles document is available on request.

| # | Principle | Effect on this procurement |
|---|-----------|---------------------------|
| 1 | Single Learning Entry Point | Recordings reach students through the LMS unit site, not a separate portal |
| 2 | Deliberate Capability Boundaries | One primary platform per capability category, with any overlap declared |
| 3 | Consistent Experience Across Schools | Identical student experience regardless of school |
| 4 | Discipline Specialisation at the Edge | Specialist tooling integrates through the same interfaces and identity model |
| 7 | Privacy by Design and Data Minimisation | Minimal identity projection; analytics minimisation; retention enforced |
| 8 | Data Residency and Cross-Border Accountability | Residency stated; cross-border disclosure assessed |
| 9 | Data Portability and Exit | Export without fee or vendor goodwill — gate MQ-3 |
| 12 | Automated Identity Lifecycle | No manual provisioning; no bulk file loads |
| 14 | Accessibility by Default | Assessed during evaluation, never remediated after deployment |
| 15 | Availability Aligned to the Teaching Calendar | Maintenance outside teaching periods |
| 16 | Layered Security Posture | No shared administrative accounts; managed patching |
| 19 | Realise Licensed Capability Before New Spend | Existing licensed capability is evaluated alongside new purchases |

---

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| REQ | ARC-002-REQ-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Requirements incorporated by reference |
| EVAL | ARC-002-EVAL-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Governing evaluation framework |
| RSCH | ARC-002-RSCH-v1.0.md | ArcKit artifact | `002-lecture-capture/research/` | Market research informing scope and terms |
| RISK | ARC-002-RISK-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Risk register informing mandatory terms |
| PRIN | ARC-000-PRIN-v1.0.md | ArcKit artifact | `000-global/` | Architecture principles at Appendix C |
| CB | consultant-brief.md | Engagement input | `002-lecture-capture/external/` | Engagement background |
| SL | system-landscape.md | Foundation artifact | `002-lecture-capture/external/` | Current platform overlap |
| PC | privacy-context.md | Compliance input | `002-lecture-capture/external/` | Privacy and NDB context |
| SGP | solution-governance-process.md | Foundation artifact | `000-global/policies/` | RIFF governance and approval route |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| SL-C1 | SL | Categorisation map | Design Decision | "Learning Capture / Echo360 ✅ · MS Teams ✅¹ · Zoom ✅" |
| CB-C1 | CB | §2, WP6 | Design Decision | "Examples: Echo360 vs Microsoft Stream; Teams scope and provisioning model; integration pattern standards" |
| PC-C1 | PC | §4 | Compliance Constraint | "Assess eligible-data-breach criteria, the 30-day investigation clock, and the notification workflow across UoF, the placement providers and affected students." |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| stakeholders.md | `002-lecture-capture/external/` | Stakeholder positions are internal; deliberately excluded from a supplier-facing document |
| requirements-register.md | `002-lecture-capture/external/` | Superseded by ARC-002-REQ, which is the document incorporated by reference |
| capability-taxonomy.md | `000-global/external/` | Category structure conveyed through the requirement set |

---

**Generated by**: ArcKit `/arckit:sow` command
**Generated on**: 2026-07-28
**ArcKit Version**: 6.7.2
**Project**: Lecture Capture Platform Consolidation (Project 002)
**Model**: Claude Opus 5 (1M context)
**Generation Context**: Requirements incorporated from ARC-002-REQ-v1.0. Evaluation deliberately delegated to ARC-002-EVAL-v1.0 rather than restated, preserving the BR-004 signed-criteria control. Mandatory contract terms derive from ARC-002-RISK-v1.0 (R-012 renewal pricing, R-013 privacy assessment sequencing, R-018 breach notification, R-020 export terms) and ARC-002-RSCH-v1.0 market findings. Deliverables reframed from the template's build-procurement default to SaaS subscription plus implementation services, per user direction.

<!-- arckit-provenance:start -->

## Build Provenance

_Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix._

| Field | Value |
|-------|-------|
| Requested Effort | `high` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-07-28T04:26:26.403Z |

<!-- arckit-provenance:end -->
