# Project Requirements: Lecture Capture Platform Consolidation

> **Template Origin**: Official | **ArcKit Version**: 6.7.2 | **Command**: `/arckit:requirements`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-REQ-v1.0 |
| **Document Type** | Business and Technical Requirements |
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

> **Classification rationale**: This document becomes the evaluation criteria for a competitive procurement. Until criteria are formally issued, it is OFFICIAL-SENSITIVE and must not reach any prospective supplier — the weightings, mandatory gates and Section 12 conflict resolutions would each confer advantage. On issue, Sections 4 to 9 may be published to suppliers as the requirement schedule of the SOW; Sections 12 and 13 remain internal.

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-27 | ArcKit AI | Initial creation from `/arckit:requirements` command | [PENDING] | [PENDING] |

## Document Purpose

This document defines the requirements for consolidating the Learning Capture and Learning Delivery tooling of The University of Funk onto a single primary platform for the 2027 academic year, with a bounded discipline exception for performance capture.

It has three uses, in this order:

1. **Evaluation criteria.** Requirements here become the scored criteria and mandatory pass/fail gates of the platform evaluation. Goal G-2 of the stakeholder analysis requires those criteria to be agreed and signed before any vendor engagement [STKE-C1] — this document is the input to that signature.
2. **Statement of Work.** The requirement schedule of the SOW is drawn from Sections 4 to 9.
3. **Architecture review baseline.** The HLD review, the ADR recording the platform decision, and the traceability matrix all trace to the IDs defined here.

Requirements are **derived, not gathered**. The academic survey has already been run (412 responses) and consolidated into the requirements register supplied as an engagement input [RR-C1]. This document applies the subset of that register relevant to lecture capture, decomposes it into testable requirements, and adds the procurement, transition, privacy and security requirements that the register does not carry because it was written before this project existed.

---

## Executive Summary

### Business Context

The Learning Capture capability at The University of Funk is currently served by three platforms simultaneously — Echo360, Microsoft Teams and Zoom — with Learning Delivery overlapping across the same three [SL-C1]. A Teams investigation was already planned for 2027 to establish a seamless platform experience across collaboration, learning delivery and lecture capture, and the system landscape names this as a key rationalisation candidate [SL-C2]. Project 001 surfaced the decision; the WP6 decisions register names "Echo360 vs Microsoft Stream" explicitly as a decision that must be resolved before the future state can be finalised [CB-C1].

The cost of the overlap is not only licensing. Capture provisioning currently runs on LTI plus manual CSV loads, with a standing manual workaround for casual academic staff [SL-C4] — a direct breach of the register's REQ-025 and an uncomfortable fit with REQ-031's prohibition on local accounts. The lecture-theatre capture appliances are behind on operating system patching, and the AV estate still carries legacy shared administrative accounts; both hold back the Essential Eight ML2 target set for end 2027 [PC-C1]. And the recordings themselves are personal information with a biometric-adjacent character, held under assumed AU and US hosting, with no defined retention or minimisation rules applied to the derived analytics [PC-C2] [PC-C3].

The stakeholder analysis found that the contested platform question occupies most of the attention while two uncontested constraints — the recordings archive and the appliance estate — bind every option equally [STKE-C2]. This requirements set is written to reflect that finding: the platform-neutral requirements are specified to the same depth as the contested ones, so that work on them can start before the decision is made.

### Objectives

- Designate one primary platform for Learning Capture with a declared boundary, and one bounded, funded discipline exception for performance capture
- Eliminate manual provisioning and enforce SSO with MFA across the capture estate
- Meet the survey's Must-priority capture requirements — universal automatic capture, 4-hour publication, single supported video toolchain
- Establish a defensible privacy, retention and residency position for recordings before contract signature
- Transition without teaching disruption, and close the Essential Eight gaps on the capture estate in the same programme

### Expected Outcomes

- Platforms in the Learning Capture category reduced from 3 to 1 primary plus 1 bounded discipline exception
- 100% of timetabled lectures in capture-equipped rooms captured automatically and published within 4 hours, from a current state that is neither universal nor measured
- Zero manual CSV provisioning events and zero local accounts on the capture platform
- 100% of published recordings captioned within 24 hours at a validated accuracy against discipline vocabulary
- Whole-of-life cost held flat or reduced across five years, with appliance refresh attributed correctly
- Essential Eight ML2 reached on "restrict administrative privileges" and "patch operating systems" for the capture estate by end 2027

### Project Scope

**In Scope**:

- Lecture capture platform selection, procurement and transition for the 2027 academic year
- Learning Delivery consolidation where it overlaps capture (live class recording, REQ-008)
- Automated user provisioning and SSO/MFA enforcement for the capture platform
- Lecture-theatre capture appliance assessment, patching regime and shared-account remediation
- Recordings archive retention decision, migration and exit-rights verification
- Captioning capability and accessibility conformance for recorded teaching
- Bounded performance-capture exception for named Music & Performing Arts venues
- Capture policy: publication defaults, unit-level exceptions, student notification

**Out of Scope**:

- The wider Learning Capture-adjacent categories not overlapping capture — Course Design, Learning Resources authoring (Articulate 360, Camtasia licensing), Assessment platforms
- The PeopleSoft → Blackboard core integration rebuild — governed by project 001's WP5 integration architecture; this project consumes it, does not deliver it
- Clinical simulation capture inside iSimulate and Kuracloud as products — assessed for interface only (see INT-006 and A-4)
- Zoom's non-teaching use (professional services meetings) — this project addresses teaching use only
- The canonical data model itself (REQ-027) — defined in project 001, applied here
- Delivery of the integration platform; this project specifies integration requirements against it

---

## Stakeholders

| Stakeholder | Role | Organization | Involvement Level |
|-------------|------|--------------|-------------------|
| Prof. Otis Hammond | Deputy Vice-Chancellor (Education), Executive Sponsor | University Executive | Decision maker |
| Cassandra "Cas" Rhodes | Chief Information Officer | Digital & IT | Decision maker — funding and platform position |
| Dr. Benny Moog | Director, Learning Technologies | Learning Innovation | Requirements owner, capability evidence |
| Grace Tanaka | Procurement & Vendor Manager | Procurement | Evaluation process authority |
| A/Prof. Pearl Clavinet | Dean L&T, Chair Education Committee | Academic | Academic approval gate |
| Vernon Ostinato | Chief Financial Officer | Finance | Whole-of-life cost approval |
| Sam Okafor | Integration Architect | Digital & IT | Integration requirements definition |
| Marcus Fairlight | Manager, AV & Learning Spaces | Digital & IT | Room and appliance requirements |
| Tobias Ohm | Cybersecurity Lead | Digital & IT | Security review |
| Eleanor Frame | Privacy & Records Officer | Governance | Privacy and records compliance |
| Prof. Desmond Key | Dean, Music & Performing Arts | Academic | Discipline exception requirements |
| Prof. Priya Anand | Dean, Health Sciences | Academic | Cohort impact, simulation capture |
| Dr. Wynton Castle | Senior Lecturer | Academic | User acceptance — academic workflow |
| Jazmin Field | President, Student Guild | Students | User acceptance — student experience |
| Nina Kalimba | Manager, Digital Learning Support | Learning Innovation | Supportability and training |
| Ivy Sequence | Manager, Timetabling & Student Allocation | Student Administration | Scheduling data provider |
| Rhonda Bell | Project Manager | Engagement | Requirements coordination |

Full driver, goal and outcome analysis for each stakeholder is in `ARC-002-STKE-v1.0.md`. Requirements below trace to the goals (G-1 to G-10) and outcomes (O-1 to O-6) defined there.

---

## Business Requirements

### BR-001: Single primary platform for Learning Capture with a declared boundary

**Description**: The university shall designate one primary platform for the Learning Capture capability category, with any other platform retaining capture capability either bounded by a documented boundary or given a retirement path.

**Rationale**: Three platforms currently provide overlapping capture capability [SL-C1]. Principle 2 requires that each capability category has a designated primary platform, and that where more than one platform provides the same capability, the architecture states which is primary and why the others persist [PRIN-C1]. Undeclared duplication — not duplication itself — is the failure this addresses.

**Success Criteria**:

- Primary platform designated and recorded in an ADR under project 001's decisions register
- Boundary or retirement path documented for each remaining platform with capture capability
- System categorisation map updated to reflect the designation

**Priority**: MUST_HAVE

**Stakeholder**: Cassandra Rhodes (CIO) and Dr. Benny Moog (Learning Technologies) — jointly, and in dispute; see Conflict C-1

**Traces To**: STKE G-1, O-1 · Principle 2

---

### BR-002: Decision endorsed through governance by 9 October 2026

**Description**: The platform recommendation shall pass RIFF review by 11 September 2026, Education Committee by 25 September 2026, and Operations Committee by 9 October 2026, with formal dissent recorded rather than suppressed.

**Rationale**: The September business case depends on this decision being closed [CB-C2]. The RIFF Review is the mandated gate for architectural fit, capability duplication, integration impact and total cost before any procurement or build proceeds [SGP-C1]. A decision taken outside that process, or imposed without academic endorsement, will be reopened at renewal.

**Success Criteria**:

- Three governance gates cleared on schedule
- Dissent recorded in RIFF minutes with a written response
- ADR published within 4 weeks of Operations Committee

**Priority**: MUST_HAVE

**Stakeholder**: Prof. Otis Hammond (Executive Sponsor)

**Traces To**: STKE G-1, O-6

---

### BR-003: Whole-of-life cost held flat or reduced over five years

**Description**: The consolidated capture capability shall be delivered at a five-year whole-of-life cost — licensing, appliance refresh, migration, support and the discipline exception — at or below the current five-year run-rate, with appliance refresh separated into "required regardless of this decision" and "caused by this decision".

**Rationale**: REQ-035 requires total ecosystem licence spend to reduce or hold flat while closing Must-priority capability gaps [RR-C2]. Lecture capture is the one L&T capability with a significant physical estate behind it; a licence-only comparison satisfies the letter of REQ-035 while producing a worse financial outcome [STKE-C3].

**Success Criteria**:

- Five-year model covering all five cost categories produced at options stage, not preferred-option stage
- Appliance refresh cost attributed between the two categories with stated reasoning
- Renewal price protection secured in contract terms
- Discipline exception costed as a named line item

**Priority**: SHOULD_HAVE (inherited from REQ-035's Should priority; the *transparency* of the cost model is MUST_HAVE — see BR-004)

**Stakeholder**: Vernon Ostinato (CFO)

**Traces To**: STKE G-7, O-3 · REQ-035 · Principle 19

---

### BR-004: Evaluation conducted on published weighted criteria, unchanged after issue

**Description**: An evaluation framework with weightings totalling 100% and defined mandatory pass/fail gates shall be signed by Rhodes, Moog and Tanaka before any vendor engagement, and applied without amendment through to recommendation.

**Rationale**: Two senior stakeholders hold publicly stated opposing positions before any evaluation has occurred [S-C1]. This is the pattern that produces a challengeable outcome. Fixing criteria first converts an executive disagreement into a decidable question, and is the only mechanism that makes an adverse result acceptable to the party that loses.

**Success Criteria**:

- Framework signed by all three parties before first vendor engagement
- 100% of scored criteria traceable to a requirement ID in this document
- Zero criteria or weighting changes after issue
- All vendor contact logged through a single point (Grace Tanaka)

**Priority**: MUST_HAVE

**Stakeholder**: Grace Tanaka (Procurement)

**Traces To**: STKE G-2, O-6

---

### BR-005: Bounded and funded discipline exception for performance capture

**Description**: A performance-capture capability for named Music & Performing Arts venues shall be scoped, costed and decided in the same governance cycle as the core platform, integrating through the same identity model, interfaces and data contracts as the core.

**Rationale**: Principle 4 permits discipline-specific tooling outside the core platform set where a genuine specialist need exists, provided it integrates through standard interfaces, identity model and data contracts — specialist need justifies a different tool, never a different architecture [PRIN-C2]. REQ-010's Could priority reflects institutional breadth rather than disciplinary criticality [RR-C3]; without an explicit exception route, the requirement is structurally guaranteed to lose every prioritisation exercise.

**Success Criteria**:

- Named venues, capability standard and cost approved alongside the core recommendation — or refusal recorded with the REQ-010 consequence stated
- Exception integrates via the core identity model and publishes to the unit site (Principle 1)
- Support model agreed, including specialist equipment maintenance

**Priority**: SHOULD_HAVE (the *decision* is MUST_HAVE; the *capability* inherits REQ-010's Could priority)

**Stakeholder**: Prof. Desmond Key (Dean, Music & Performing Arts)

**Traces To**: STKE G-9, O-1 · REQ-010 · Principle 4

---

### BR-006: Transition completed without teaching disruption

**Description**: The platform shall be piloted in Semester 1 2027 and cut over during the mid-year inter-semester break, with no cutover activity inside a teaching period under any circumstance.

**Rationale**: REQ-032 sets 99.9% availability for core teaching platforms during teaching periods [RR-C4], and Principle 15 requires change and maintenance to be scheduled around the academic calendar rather than the operational one [PRIN-C3]. Every operational stakeholder's worst case is the same event — a cutover that fails in week three of semester [STKE-C4].

**Success Criteria**:

- Pilot completed in Semester 1 2027 with documented failure modes
- Cutover executed in the July 2027 inter-semester break
- Runbooks and known-issues documentation published before cutover
- Zero recordings lost in transition

**Priority**: MUST_HAVE

**Stakeholder**: Rhonda Bell (PM), Marcus Fairlight (AV), Nina Kalimba (Support)

**Traces To**: STKE G-8, O-2 · REQ-032 · Principle 15

---

### BR-007: Retained recordings remain accessible, with exit rights proven before signature

**Description**: An approved retention schedule shall be applied to the recordings archive, all in-retention recordings migrated with metadata and captions intact, existing unit-site links preserved or redirected, and open-format export demonstrated from the target platform before contract signature.

**Rationale**: Principle 9 requires every platform holding university or student data to permit export in open, documented formats at any time and on termination, without dependence on vendor goodwill or additional fee — a platform that cannot be left cannot be rationalised [PRIN-C4]. Migration is also the only operationally natural point at which a retention schedule can be applied; after cutover, everything migrated becomes permanent by default [STKE-C5].

**Success Criteria**:

- Retention schedule approved by Education Committee before migration planning completes
- 100% of in-retention recordings migrated with metadata and captions intact
- Export tested practically during evaluation, not accepted as a contractual assurance
- Link-check sweep across unit sites shows no broken recording links post-cutover

**Priority**: MUST_HAVE

**Stakeholder**: Eleanor Frame (Privacy & Records Officer)

**Traces To**: STKE G-6, O-4 · REQ-034 · Principle 9

---

### BR-008: Essential Eight gaps on the capture estate closed

**Description**: Shared administrative accounts shall be removed from the AV and capture estate and capture appliances brought into the managed patching regime, reaching ML2 for "restrict administrative privileges" and "patch operating systems" across this estate by end 2027.

**Rationale**: Both mitigation strategies sit at ML1 specifically because of this estate — legacy shared admin accounts in the AV/capture estate, and lecture-theatre capture appliances behind on OS patching [PC-C1]. The Digital & IT target is ML2 by end 2027 [PC-C4], and REQ-033 requires demonstrable Essential Eight alignment [RR-C5]. A platform transition touches every capture-equipped room; doing this work separately means touching them twice.

**Success Criteria**:

- Zero shared administrative accounts in the AV/capture estate at cutover
- 100% of retained capture appliances within the managed patching regime
- ML2 assessed and evidenced for both strategies for this estate

**Priority**: MUST_HAVE

**Stakeholder**: Tobias Ohm (Cybersecurity Lead), Marcus Fairlight (AV)

**Traces To**: STKE G-10, O-4 · REQ-033 · Principle 16

---

## Functional Requirements

### User Personas

#### Persona 1: Unit Coordinator (continuing academic)

- **Role**: Designs and delivers a unit; typically 2–4 units per year; represented by Dr. Wynton Castle
- **Goals**: Teach without thinking about the technology; have recordings appear where students already look; reuse material across offerings
- **Pain Points**: Recordings that silently fail to start; publication delays that miss the tutorial; being asked to relearn a workflow mid-semester; uncertainty about who can view recordings of their teaching
- **Technical Proficiency**: Medium

#### Persona 2: Casual Academic (sessional tutor)

- **Role**: Appointed per teaching period, often days before semester; delivers tutorials and occasional lectures
- **Goals**: Have working access on day one; record a session without an administrative request
- **Pain Points**: Access depends on a manual CSV load being run [SL-C4]; frequently starts teaching without capture access; no institutional visibility of the gap
- **Technical Proficiency**: Medium — but with near-zero tolerance for setup overhead given short engagements

#### Persona 3: Student (including placement and shift-working cohorts)

- **Role**: Enrolled student; in Health Sciences frequently combining study with clinical placement [STKE-C6]
- **Goals**: Find the recording of a session they could not attend; search it; read accurate captions; watch on a phone between shifts
- **Pain Points**: Publication inconsistency between units and schools; captions that mangle clinical or musical vocabulary; not knowing whether a session was recorded at all
- **Technical Proficiency**: High for consumer tooling, low tolerance for institutional friction

#### Persona 4: AV Technician

- **Role**: Maintains capture appliances in teaching spaces; reports to Marcus Fairlight
- **Goals**: Know a room has failed before the academic does; patch and manage devices centrally; stop using shared credentials
- **Pain Points**: Appliances outside the managed patching regime; shared administrative accounts [PC-C1]; room-by-room manual intervention
- **Technical Proficiency**: High

#### Persona 5: Learning Technologist / Support Analyst

- **Role**: First and second line support for L&T platforms; Nina Kalimba's team
- **Goals**: Documented workflows, a health dashboard, and fewer access tickets in week one
- **Pain Points**: Absorbs every failure mode; no runbooks for a platform they did not choose; provisioning failures presenting as user error
- **Technical Proficiency**: High

#### Persona 6: Privacy & Records Officer

- **Role**: Assesses privacy compliance and owns the records schedule; Eleanor Frame
- **Goals**: Know where recordings are hosted, who can access them, and when they are destroyed
- **Pain Points**: No retention rule applied to recordings or their derived analytics [PC-C3]; assumed offshore hosting for part of the estate [PC-C2]; leverage that evaporates after contract signature
- **Technical Proficiency**: Medium

---

### Use Cases

#### UC-1: Timetabled lecture captured and published automatically

**Actor**: Unit Coordinator (passive); system-initiated

**Preconditions**:

- Session exists in the timetable with a room, unit, time and scheduled presenter
- Room is capture-equipped and healthy
- Unit site exists in the LMS with the enrolled cohort provisioned

**Main Flow**:

1. System receives the timetable schedule for the teaching period from Allocate+
2. System creates a capture schedule entry for each timetabled session in a capture-equipped room
3. At session start time, the room appliance begins capture automatically
4. At session end time, capture stops and the recording uploads
5. System processes the recording, generates captions, and publishes it to the unit site
6. System records publication time against the 4-hour target

**Postconditions**:

- Recording is available in the unit site to the enrolled cohort
- Captions are attached or queued within the captioning SLA
- Capture event, timings and outcome are logged

**Alternative Flows**:

- **Alt 3a**: If the unit's capture policy is set to "not published by default" (FR-012), the recording is captured and held unpublished pending coordinator action
- **Alt 4a**: If network connectivity to the room is lost, the appliance buffers locally and uploads on restoration (NFR-A-002)

**Exception Flows**:

- **Ex 1**: Room appliance offline at session start — system raises an alert to AV before the session, and to the coordinator if unresolved (FR-004)
- **Ex 2**: Timetable change after schedule creation — system reconciles and adjusts the capture schedule (INT-002)

**Business Rules**:

- Every timetabled lecture in a capture-equipped room is captured unless an approved unit-level exception exists
- Publication is to the unit site, not to a separate portal (Principle 1)

**Priority**: CRITICAL

---

#### UC-2: Casual academic gains capture access on appointment

**Actor**: Casual Academic

**Preconditions**:

- Appointment recorded in the authoritative source with a teaching role against a unit

**Main Flow**:

1. Appointment or role change is recorded in the authoritative HR/SIS source
2. Change is published as an event to the integration layer
3. Capture platform receives the identity and role assignment via the canonical model
4. Account is provisioned or updated with the correct unit-level role
5. User authenticates via university SSO with MFA; no separate credential is created
6. User can start, edit and publish recordings for their assigned units

**Postconditions**:

- Access granted within 15 minutes of the source change
- No CSV file created, transmitted or stored at any point
- Provisioning event logged for audit

**Alternative Flows**:

- **Alt 4a**: Appointment ends — access is removed within the same 15-minute window (deprovisioning is the same flow)

**Exception Flows**:

- **Ex 1**: Role cannot be mapped to a platform role — provisioning fails loudly with an alert to support, never silently

**Business Rules**:

- Manual account creation and bulk user file loads are prohibited in production (Principle 12)
- Institutional role assignment derives from a single authoritative source (REQ-024)

**Priority**: CRITICAL

---

#### UC-3: Student finds and watches a captioned recording

**Actor**: Student

**Preconditions**:

- Student is enrolled in the unit; recording is published

**Main Flow**:

1. Student opens the unit site in the LMS
2. Student selects the recordings area — the same location in every unit (Principle 3)
3. Student sees sessions listed with date, topic and duration
4. Student opens a recording; playback begins
5. Student enables captions, searches the transcript for a term, and jumps to that point
6. Student adjusts playback speed and continues on a mobile device

**Postconditions**:

- Viewing event recorded in engagement analytics under the retention and minimisation rules of DR-003

**Alternative Flows**:

- **Alt 4a**: Student is on a low-bandwidth connection — adaptive bitrate degrades video quality rather than stalling (NFR-P-002)

**Exception Flows**:

- **Ex 1**: Session was not recorded — the unit site states this explicitly rather than showing an empty list

**Business Rules**:

- Access is derived from enrolment; no separate enrolment in the capture platform
- Presentation and location are consistent across all schools

**Priority**: CRITICAL

---

#### UC-4: Academic starts an unscheduled capture

**Actor**: Unit Coordinator or Casual Academic

**Preconditions**:

- User is authenticated and holds a teaching role for the unit
- Room is capture-equipped, or the user is capturing from a personal device

**Main Flow**:

1. User selects the unit and session context
2. User starts capture with a single action
3. System captures, processes and offers the recording for review
4. User trims start and end, then publishes to the unit site

**Postconditions**:

- Recording is published against the correct unit and session

**Alternative Flows**:

- **Alt 2a**: User is in a capture-equipped room — capture uses room equipment; otherwise it uses the personal device

**Exception Flows**:

- **Ex 1**: Another capture is already running in the room — system informs the user rather than creating a conflicting recording

**Business Rules**:

- Ad-hoc capture must not require a support request or an administrative action

**Priority**: HIGH

---

#### UC-5: Multi-camera performance capture in a Music venue

**Actor**: AV Technician, with academic direction

**Preconditions**:

- Session booked in a named performance venue
- Multi-camera and audio capture equipment available and configured

**Main Flow**:

1. Technician configures camera positions and audio inputs for the performance
2. Capture runs across multiple video sources and a high-fidelity audio path
3. Recording is processed and associated with the relevant unit
4. Recording is published to the unit site through the same route as core capture

**Postconditions**:

- Performance recording accessible via the unit site alongside standard recordings
- Rights and consent position for the performance recorded (see DR-006 and A-6)

**Alternative Flows**:

- **Alt 3a**: Recording requires editing across sources before publication — edit occurs before the publication step

**Exception Flows**:

- **Ex 1**: Third-party performance rights prevent publication — recording is retained unpublished with the restriction recorded

**Business Rules**:

- Specialist capture integrates through the same identity model and interfaces as the core platform (Principle 4)

**Priority**: MEDIUM (institutional) / CRITICAL (School of Music & Performing Arts)

---

#### UC-6: Recording reaches end of retention and is disposed of

**Actor**: System, under the approved retention schedule; overseen by the Privacy & Records Officer

**Preconditions**:

- Approved retention schedule is configured
- Recording has reached the end of its retention period and carries no hold

**Main Flow**:

1. System identifies recordings reaching end of retention
2. System notifies the unit coordinator ahead of disposal, offering an archive-on-request path
3. Where no hold or archive request exists, system destroys the recording and its derived assets
4. System records the disposal event in the immutable audit log

**Postconditions**:

- Recording, transcript, captions and derived analytics identifiers destroyed
- Disposal evidenced for records compliance

**Alternative Flows**:

- **Alt 3a**: Coordinator requests archival for genuinely reusable teaching material — recording is moved to an archive tier with a new retention date

**Exception Flows**:

- **Ex 1**: Legal or investigative hold present — disposal is suppressed and the hold recorded

**Business Rules**:

- Disposal is the default at end of retention; retention beyond schedule requires an active decision

**Priority**: HIGH

---

### Functional Requirements Detail

#### FR-001: Automatic scheduled capture from timetable data

**Description**: The platform shall automatically schedule and execute capture for every timetabled session in a capture-equipped teaching space, driven by the timetabling system, without academic or administrator intervention.

**Relates To**: BR-001, UC-1, REQ-009, INT-002

**Acceptance Criteria**:

- [ ] Given a timetabled session in a capture-equipped room, when the session start time is reached, then capture begins automatically with no human action
- [ ] Given a timetable change published after the schedule was created, when the change is received, then the capture schedule reconciles within 1 hour
- [ ] Given a session cancelled in the timetable, when cancellation is received, then no recording is produced and no failure alert is raised
- [ ] Edge case: given two sessions scheduled back-to-back in the same room, when the first ends, then two discrete recordings are produced with correct unit association

**Data Requirements**:

- **Inputs**: Timetable session records (unit, room, start, end, presenter), room capability register
- **Outputs**: Capture schedule entries, capture events
- **Validations**: Room must exist in the capability register; unit must resolve to an LMS unit site

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

**Dependencies**: INT-002 (timetable feed), INT-006 (room appliances), FR-016 (unit association)

**Assumptions**: A-1 (timetable data is authoritative for room and time)

---

#### FR-002: Publication to the unit site within 4 hours

**Description**: The platform shall publish each completed recording to the relevant LMS unit site within 4 hours of session end, visible to the enrolled cohort without further action.

**Relates To**: BR-001, UC-1, UC-3, REQ-009, REQ-007

**Acceptance Criteria**:

- [ ] Given a completed capture, when processing finishes, then the recording appears in the unit site with correct title, date and duration
- [ ] Given a completed capture, when 4 hours have elapsed from session end, then the recording is published in at least 99% of cases measured monthly
- [ ] Given a unit with a "hold for review" policy (FR-012), when capture completes, then the recording is held unpublished and the coordinator is notified
- [ ] Edge case: given a recording that fails processing, when the failure is detected, then the coordinator and support are alerted within 1 hour rather than the recording silently not appearing

**Data Requirements**:

- **Inputs**: Recording media, session metadata, unit site identifier
- **Outputs**: Published recording entry in the LMS, publication timestamp
- **Validations**: Unit site must exist and the cohort must be provisioned before publication

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

**Dependencies**: INT-003 (LMS integration), FR-001, FR-006

**Assumptions**: A-2 (LMS unit sites exist before the teaching period begins)

---

#### FR-003: Ad-hoc capture initiated by teaching staff

**Description**: The platform shall allow a user holding a teaching role to start and stop an unscheduled capture for a unit, from a capture-equipped room or a personal device, without a support request.

**Relates To**: UC-4, REQ-004

**Acceptance Criteria**:

- [ ] Given an authenticated user with a teaching role, when they start an ad-hoc capture, then capture begins in no more than two actions from the unit context
- [ ] Given an ad-hoc capture in progress, when the user stops it, then the recording follows the same processing, captioning and publication path as scheduled capture
- [ ] Edge case: given a scheduled capture already running in the room, when a user attempts an ad-hoc capture, then the system reports the conflict rather than producing overlapping recordings

**Data Requirements**:

- **Inputs**: User identity and role, unit context, capture source
- **Outputs**: Recording with unit association
- **Validations**: User must hold a teaching role for the selected unit

**Priority**: MUST_HAVE

**Complexity**: LOW

**Dependencies**: FR-016, INT-004

**Assumptions**: None

---

#### FR-004: Capture failure detection, alerting and recovery

**Description**: The platform shall detect capture failures — appliance offline, capture not started, upload failed, processing failed — and alert AV and support before or as the failure affects teaching, with a defined recovery path.

**Relates To**: UC-1 (Ex 1), BR-006, NFR-M-001

**Acceptance Criteria**:

- [ ] Given a room appliance offline, when a session is scheduled in that room within the next 24 hours, then AV receives an alert with room, time and affected unit
- [ ] Given a capture that failed to start, when the session start time passes without a capture event, then an alert is raised within 10 minutes
- [ ] Given an upload failure, when retry attempts are exhausted, then support is alerted and the locally buffered recording is preserved for manual recovery
- [ ] Edge case: given a session where the presenter did not attend, when no audio or video signal is detected for the full session, then the event is classified separately from a technical failure

**Data Requirements**:

- **Inputs**: Appliance health telemetry, capture event stream, processing status
- **Outputs**: Alerts with routing by failure class, failure log
- **Validations**: Alert must identify room, unit, session and failure class

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

**Dependencies**: INT-006, NFR-M-001

**Assumptions**: A-3 (room appliances can report health telemetry to a central point)

---

#### FR-005: Recording review, trim and edit by teaching staff

**Description**: The platform shall allow teaching staff to review a recording, trim its start and end, remove a segment, and republish, without specialist video skills or a separate application.

**Relates To**: UC-4, REQ-004

**Acceptance Criteria**:

- [ ] Given a published or held recording, when the coordinator trims the start and end, then the trimmed version replaces the published one and captions re-align
- [ ] Given a segment containing content that must be removed, when the coordinator removes it, then the segment is destroyed rather than hidden
- [ ] Edge case: given a recording already viewed by students, when it is edited, then the previous version is not retained beyond the retention rule for superseded content

**Data Requirements**:

- **Inputs**: Recording, edit instructions
- **Outputs**: Edited recording, realigned captions, edit audit entry
- **Validations**: Only users with a teaching role for that unit may edit

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

**Dependencies**: FR-006 (caption realignment)

**Assumptions**: None

---

#### FR-006: Automatic captioning within 24 hours

**Description**: The platform shall generate captions and a searchable transcript for every published recording within 24 hours of publication, meeting the accuracy standard defined in NFR-U-003.

**Relates To**: BR-001, UC-3, REQ-029, NFR-C-002

**Acceptance Criteria**:

- [ ] Given a published recording, when 24 hours have elapsed, then captions and a transcript are available in 100% of cases measured monthly
- [ ] Given captions are generated, when a student enables them, then they are synchronised to within 1 second of the audio
- [ ] Given a transcript, when a student searches a term, then playback can jump to each occurrence
- [ ] Edge case: given a recording with two speakers in dialogue, when captions are generated, then speaker changes are indicated

**Data Requirements**:

- **Inputs**: Recording audio
- **Outputs**: Caption file (open format), transcript, accuracy metadata
- **Validations**: Caption file must be exportable independently of the media (see NFR-I-002)

**Priority**: MUST_HAVE

**Complexity**: LOW (platform capability) / MEDIUM (accuracy validation)

**Dependencies**: NFR-U-003

**Assumptions**: A-5 (automatic captioning is the primary mechanism; human captioning is exception-only)

---

#### FR-007: Caption correction workflow

**Description**: The platform shall provide a workflow for correcting captions, available to teaching staff and to a central support role, with corrections applied to the transcript and the caption file together.

**Relates To**: FR-006, REQ-029, NFR-U-003

**Acceptance Criteria**:

- [ ] Given inaccurate captions, when a coordinator corrects a segment, then both the caption file and the transcript update
- [ ] Given a student reports a caption problem, when the report is submitted, then it routes to a defined owner with the timestamp and unit
- [ ] Edge case: given a recurring discipline term consistently mis-transcribed, when it is corrected, then the platform supports adding it to a vocabulary list for future recordings

**Data Requirements**:

- **Inputs**: Caption correction, vocabulary additions
- **Outputs**: Corrected caption file and transcript, correction audit entry
- **Validations**: Corrections must not alter the recording media

**Priority**: SHOULD_HAVE

**Complexity**: LOW

**Dependencies**: FR-006

**Assumptions**: Correction effort is resourced within Digital Learning Support (see D-6)

---

#### FR-008: Live class delivery with recording on one primary platform

**Description**: The platform designated for live online classes shall support breakout rooms, polling and recording, with recordings following the same processing, captioning and publication path as room capture.

**Relates To**: BR-001, REQ-008, UC-1

**Acceptance Criteria**:

- [ ] Given a live online class, when the session is recorded, then the recording publishes to the unit site within 4 hours by the same route as room capture
- [ ] Given a live class, when the presenter uses breakout rooms and polling, then both function without a secondary platform
- [ ] Edge case: given a hybrid session with in-room and online participants, when it is captured, then a single recording is produced rather than two

**Data Requirements**:

- **Inputs**: Live session, participant roles, poll results
- **Outputs**: Recording, poll results available to the coordinator
- **Validations**: Session must be associated with a unit

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

**Dependencies**: FR-002, BR-001 (designation resolves whether this is the same platform as capture)

**Assumptions**: A-7 (live delivery and capture may be the same platform or two bounded platforms; this requirement is neutral on that)

---

#### FR-009: Multi-camera, high-fidelity performance capture

**Description**: The capability serving named Music & Performing Arts venues shall capture multiple synchronised video sources with a high-fidelity audio path suitable for musical performance, publishing through the core platform's unit site route.

**Relates To**: BR-005, UC-5, REQ-010, Principle 4

**Acceptance Criteria**:

- [ ] Given a performance session in a named venue, when captured, then multiple synchronised camera angles and a high-fidelity audio path are recorded
- [ ] Given a completed performance recording, when published, then it appears in the unit site by the same route as core capture
- [ ] Given a performance recording, when accessed, then access derives from the same identity and enrolment model as core capture (Principle 4)
- [ ] Edge case: given third-party performance rights restricting publication, when the restriction is recorded, then the recording is retained unpublished

**Data Requirements**:

- **Inputs**: Multiple video sources, multi-channel audio, venue and session metadata
- **Outputs**: Published or restricted performance recording
- **Validations**: Venue must be one of the named venues in the approved exception scope

**Priority**: COULD_HAVE (institutional priority inherited from REQ-010) — see Conflict C-6 for why this priority understates the disciplinary need

**Complexity**: HIGH

**Dependencies**: BR-005 (exception approved and funded), INT-006

**Assumptions**: A-6 (rights and consent for recorded performance are addressed under a separate university policy)

---

#### FR-010: Student playback experience

**Description**: The platform shall provide students with search, variable playback speed, transcript-linked navigation, mobile playback and resumption from last position, consistently across all units and schools.

**Relates To**: UC-3, REQ-007, Principle 3

**Acceptance Criteria**:

- [ ] Given a published recording, when a student opens it on a mobile device, then playback works without installing an application
- [ ] Given a recording, when a student changes playback speed, then captions remain synchronised
- [ ] Given a student who stopped watching partway, when they return, then playback resumes from that position
- [ ] Edge case: given a student enrolled in units across two schools, when they access recordings in each, then the location and presentation are identical

**Data Requirements**:

- **Inputs**: Recording, transcript, viewing position
- **Outputs**: Playback session, viewing position (see DR-003 for retention)
- **Validations**: Access derives from enrolment

**Priority**: MUST_HAVE

**Complexity**: LOW

**Dependencies**: FR-002, FR-006, FR-016

**Assumptions**: None

---

#### FR-011: Engagement analytics for unit coordinators

**Description**: The platform shall provide unit coordinators with engagement data for their cohort — views, coverage, drop-off — and shall make that data exportable to the institutional data platform.

**Relates To**: REQ-020, REQ-022, DR-003, INT-005

**Acceptance Criteria**:

- [ ] Given a unit, when the coordinator opens the analytics view, then per-session engagement is shown for their cohort only
- [ ] Given the institutional data platform, when the scheduled export runs, then engagement data transfers in a documented open format
- [ ] Edge case: given a cohort small enough that individual students could be identified from aggregate views, when analytics are displayed, then a minimum cohort threshold suppresses the view

**Data Requirements**:

- **Inputs**: Viewing events
- **Outputs**: Aggregate engagement views, export dataset
- **Validations**: Minimum cohort threshold applied; retention rules of DR-003 enforced

**Priority**: SHOULD_HAVE

**Complexity**: MEDIUM

**Dependencies**: INT-005, DR-003

**Assumptions**: The institutional data platform can consume the export format

---

#### FR-012: Unit-level capture policy configuration

**Description**: The platform shall support a configured default of automatic capture and publication for all units, with unit-level exceptions applied only where formally approved, and the exception recorded and visible.

**Relates To**: BR-001, UC-1 (Alt 3a), Conflict C-3, Principle 3

**Acceptance Criteria**:

- [ ] Given no exception, when a session is captured, then it publishes automatically (the institutional default)
- [ ] Given an approved unit-level exception, when a session is captured, then the recording is held for coordinator review before publication
- [ ] Given an exception is configured, when it is set, then the approval reference and approver are recorded against it
- [ ] Edge case: given an exception applied without an approval reference, when configuration is attempted, then the platform rejects it

**Data Requirements**:

- **Inputs**: Unit policy setting, approval reference
- **Outputs**: Policy state per unit, exception register
- **Validations**: Exceptions require an approval reference

**Priority**: MUST_HAVE

**Complexity**: LOW

**Dependencies**: Capture policy approved by Education Committee (D-4)

**Assumptions**: A-8 (Education Committee approves the exception route; the platform enforces it rather than defining it)

---

#### FR-013: Student notification of recording

**Description**: The platform shall support clear notification to students that a session is being recorded, both in advance through the unit site and at the point of capture in the teaching space.

**Relates To**: REQ-030, DR-001, Conflict C-3, Principle 7

**Acceptance Criteria**:

- [ ] Given a unit where sessions are recorded, when a student views the unit site, then the recording practice is stated in plain language
- [ ] Given a capture in progress in a teaching space, when a student is present, then an in-room indication of active recording is visible
- [ ] Edge case: given a session where students are individually visible and audible (seminar or performance), when captured, then the heightened notification standard set by the capture policy applies

**Data Requirements**:

- **Inputs**: Unit capture policy, session context
- **Outputs**: Notification displayed, in-room indication
- **Validations**: Notification text is centrally maintained, not per-unit authored

**Priority**: MUST_HAVE

**Complexity**: LOW

**Dependencies**: FR-012, capture policy (D-4)

**Assumptions**: In-room indication may be delivered by room signage where the appliance cannot display it

---

#### FR-014: Retention schedule application and defensible disposal

**Description**: The platform shall apply the approved retention schedule to recordings and derived assets, notify before disposal, support archive-on-request, support legal hold, and log every disposal.

**Relates To**: BR-007, UC-6, DR-005, REQ-030, Principle 7

**Acceptance Criteria**:

- [ ] Given a recording reaching end of retention with no hold, when the disposal job runs, then the recording, transcript, captions and derived analytics identifiers are destroyed
- [ ] Given a recording approaching end of retention, when 30 days remain, then the unit coordinator is notified with an archive-on-request option
- [ ] Given a legal or investigative hold, when disposal would otherwise occur, then disposal is suppressed and the suppression logged
- [ ] Edge case: given a recording referenced from an active unit site, when it reaches end of retention, then the reference is resolved or the recording archived rather than leaving a broken link

**Data Requirements**:

- **Inputs**: Retention schedule, hold register, recording metadata
- **Outputs**: Disposal events, archive events, immutable audit entries
- **Validations**: Disposal must be irreversible and evidenced

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

**Dependencies**: DR-005 (approved schedule), NFR-C-003 (audit logging)

**Assumptions**: A-9 (Education Committee approves the retention schedule before migration)

---

#### FR-015: Archive migration with link preservation

**Description**: The platform shall ingest the migrated recordings archive with metadata and captions intact, and existing unit-site references to recordings shall resolve after cutover through preservation or redirection.

**Relates To**: BR-007, INT-007, NFR-I-002

**Acceptance Criteria**:

- [ ] Given the in-retention archive, when migration completes, then the target recording count reconciles to the source count with a documented explanation for every difference
- [ ] Given an existing recording link in a unit site, when a student follows it after cutover, then it resolves to the migrated recording
- [ ] Given migrated recordings, when opened, then captions and metadata are present and correctly associated
- [ ] Edge case: given a recording out of retention at migration time, when migration runs, then it is disposed of under FR-014 rather than migrated

**Data Requirements**:

- **Inputs**: Exported archive (media, captions, metadata), link inventory
- **Outputs**: Migrated archive, reconciliation report, redirect map
- **Validations**: Reconciliation must be complete before decommissioning the source

**Priority**: MUST_HAVE

**Complexity**: HIGH

**Dependencies**: INT-007, FR-014, BR-007

**Assumptions**: A-10 (incumbent contract permits bulk export without additional fee — to be confirmed, see R-3)

---

#### FR-016: Role-based access to recordings derived from enrolment

**Description**: Access to a recording shall derive from the enrolment and role data held in the authoritative source, with no separate enrolment, group or access list maintained inside the capture platform.

**Relates To**: UC-2, UC-3, REQ-024, INT-001, Principle 5, Principle 12

**Acceptance Criteria**:

- [ ] Given an enrolled student, when they access the unit site, then they see recordings for that unit and no others
- [ ] Given a student who withdraws, when the withdrawal is published, then access is removed within 15 minutes
- [ ] Given a marker or tutor role, when assigned in the authoritative source, then the corresponding platform permissions apply without manual configuration
- [ ] Edge case: given a student with a special enrolment arrangement, when their record is updated, then access follows the record rather than requiring an exception

**Data Requirements**:

- **Inputs**: Enrolment records, institutional role assignments
- **Outputs**: Effective permissions per user per unit
- **Validations**: No locally maintained access list may override the authoritative source

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

**Dependencies**: INT-001, REQ-027 canonical model from project 001

**Assumptions**: A-11 (project 001 delivers institutional role assignment from a single authoritative source, REQ-024)

---

#### FR-017: Bulk export of recordings, captions and metadata

**Description**: The platform shall permit bulk export of all recordings, captions, transcripts and metadata in open, documented formats, at any time and on termination, without additional fee.

**Relates To**: BR-007, REQ-034, NFR-I-002, Principle 9

**Acceptance Criteria**:

- [ ] Given a request for full export, when executed, then media, captions, transcripts and metadata export in documented open formats
- [ ] Given an export, when inspected, then recordings can be associated to unit, session and date without proprietary tooling
- [ ] Given the contract, when export is invoked, then no additional fee or vendor assistance is required
- [ ] Edge case: given an export during a live teaching period, when it runs, then it does not degrade capture or playback below NFR-A-001

**Data Requirements**:

- **Inputs**: Export scope
- **Outputs**: Export package with manifest
- **Validations**: Export must be tested during evaluation, not accepted as a contractual assurance

**Priority**: MUST_HAVE

**Complexity**: LOW

**Dependencies**: NFR-I-002 (mandatory gate)

**Assumptions**: None

---

#### FR-018: Operational and compliance reporting

**Description**: The platform shall report capture coverage, publication latency, failure counts by class, captioning coverage and accuracy sampling, provisioning events, and access audit — sufficient to evidence the success criteria of BR-001 to BR-008 without manual collation.

**Relates To**: All BRs; STKE G-3, G-4, G-5, G-8, G-10

**Acceptance Criteria**:

- [ ] Given a teaching period, when the monthly report is produced, then coverage, latency and failure metrics are available without manual data assembly
- [ ] Given a request for provisioning audit, when produced, then every account creation, role change and removal is attributable to a source event
- [ ] Given the steering committee reporting cycle, when the report is generated, then it maps to the goal measures defined in the stakeholder analysis
- [ ] Edge case: given a room out of service for part of a period, when coverage is calculated, then it is excluded from the denominator with the exclusion stated

**Data Requirements**:

- **Inputs**: Capture events, publication events, provisioning events, access logs
- **Outputs**: Operational report, compliance evidence pack
- **Validations**: Metric definitions fixed before baseline measurement

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

**Dependencies**: NFR-M-001

**Assumptions**: Baseline measurement begins before cutover so that improvement is demonstrable

---

## Non-Functional Requirements (NFRs)

### Performance Requirements

#### NFR-P-001: Processing and publication latency

**Requirement**:

- Median publication latency: < 1 hour from session end
- 99th percentile publication latency: < 4 hours from session end (REQ-009 compliance)
- Caption availability: < 24 hours from publication

**Measurement Method**: Platform reporting reconciled against the timetable extract; monthly report per FR-018

**Load Conditions**:

- Peak concurrent captures: to be sourced from the timetable extract and appliance inventory ⚠️ (Marcus Fairlight / Dr. Benny Moog, due 2026-08-21). The peak is structural — mid-morning weekdays in weeks 1–12 of each semester — and the platform must sustain simultaneous capture across every equipped room without queueing beyond the 4-hour target.
- Processing backlog must clear within the publication window even when peak capture and archive migration overlap

**Priority**: CRITICAL

---

#### NFR-P-002: Playback performance

**Requirement**:

- Playback start time: < 3 seconds (95th percentile) on campus network
- Adaptive bitrate delivery so that constrained connections degrade video quality rather than stalling
- Caption rendering must not delay playback start

**Measurement Method**: Synthetic monitoring from campus and off-campus vantage points; student-reported issues via support

**Load Conditions**: Peak concurrent playback occurs in the 48 hours before an assessment deadline, not during teaching hours; the platform must sustain peak playback concurrently with peak capture

**Priority**: HIGH

---

### Availability and Resilience Requirements

#### NFR-A-001: Availability target

**Requirement**: The platform shall achieve 99.9% availability during teaching periods (REQ-032) [RR-C4].

- Maximum planned downtime during teaching periods: zero
- Planned maintenance is scheduled into inter-semester or non-teaching weeks (Principle 15) [PRIN-C3]
- Availability is measured separately for capture, processing and playback — a platform that records but cannot publish is not available

**Maintenance Windows**: Inter-semester breaks (July, December–February) and, where unavoidable, weekends outside teaching weeks with 10 working days' notice

**Priority**: CRITICAL

---

#### NFR-A-002: Capture continuity and recording durability

**Requirement**: A recording, once started, shall survive network or platform interruption.

- **RPO**: Zero for recorded content — no lecture may be lost due to network or platform failure
- **RTO**: Capture capability restored within 4 hours during teaching periods
- Room appliances buffer locally and upload on restoration
- Local buffer capacity sufficient for a full teaching day
- Backups retained per DR-005 with restore tested annually

**Failover Requirements**:

- Automatic failover for the publication and playback tiers: YES
- Failover time: < 15 minutes

**Priority**: CRITICAL

---

#### NFR-A-003: Graceful degradation

**Requirement**: The platform shall degrade in defined steps rather than failing whole.

**Resilience Patterns Required**:

- [ ] Room-level failure isolation — one appliance failure cannot affect capture in other rooms
- [ ] Audio-only capture as an accepted fallback when video capture fails mid-session
- [ ] Retry with backoff on upload and processing
- [ ] Timeouts on all integration calls, with provisioning failures raised loudly rather than silently skipped (FR-004)
- [ ] Playback available when capture is degraded, and vice versa

**Priority**: HIGH

---

### Scalability Requirements

#### NFR-S-001: Storage and volume growth

**Requirement**: The platform shall accommodate recording volume growth for five years without architectural change, with a defined storage tiering approach for content past active use.

**Growth Projections**: Baseline archive volume and annual growth rate to be sourced ⚠️ (Eleanor Frame, due 2026-08-28). Projection is bounded by two known factors: coverage rising from partial to 100% of timetabled lectures in equipped rooms (which increases annual volume), and the first application of a retention schedule (which reduces the retained total). Both must be modelled before the cost position in BR-003 is finalised.

**Data Archival Strategy**: Active tier for the current and prior teaching period; archive tier thereafter until end of retention; disposal per FR-014

**Priority**: HIGH

---

### Security Requirements

#### NFR-SEC-001: Authentication — MANDATORY GATE

**Requirement**: All access shall use university single sign-on with MFA. No local accounts, no shared accounts, no platform-native passwords (REQ-031) [RR-C6].

**Multi-Factor Authentication**:

- Required for: all users, all access — this is a university-wide position, not a privileged-access-only control
- MFA is enforced by the identity provider, not by the platform

**Session Management**:

- Session timeout: 8 hours of inactivity for staff, aligned to the university standard
- Re-authentication required for: administrative configuration changes and bulk export

> **Evaluation treatment**: This is a mandatory pass/fail gate, not a scored criterion. A platform that cannot enforce SSO with MFA and eliminate local accounts is non-compliant regardless of its other capabilities. Two tools in the wider estate still permit local accounts in breach of REQ-031 [PC-C5]; this procurement shall not add a third.

**Priority**: CRITICAL

---

#### NFR-SEC-002: Authorization and administrative access

**Requirement**: Role-based access control with least privilege, and no shared administrative accounts anywhere in the platform or its room appliances.

**Roles and Permissions**: Derived from the authoritative source per FR-016; administrative roles assigned to named individuals only

**Privilege Elevation**: Time-bound elevation with logging; no standing administrative access on room appliances

**Rationale**: Legacy shared administrative accounts in the AV/capture estate hold the "restrict administrative privileges" strategy at ML1 [PC-C1]. This requirement closes that gap for the new estate and prevents its recurrence.

**Priority**: CRITICAL

---

#### NFR-SEC-003: Encryption

**Requirement**:

- Data in transit: TLS 1.3 for all client, integration and appliance-to-platform traffic
- Data at rest: AES-256 for recordings, transcripts, captions and metadata, including local appliance buffers
- Key management: university-approved key management service

**Encryption Scope**:

- [ ] Recording media at rest, including archive tier
- [ ] Local appliance buffer storage
- [ ] Backups and export packages
- [ ] Transcripts and caption files

**Priority**: CRITICAL

---

#### NFR-SEC-004: Vulnerability and patch management for the capture estate

**Requirement**: Room capture appliances shall be within the managed patching regime, with operating system and firmware patching evidenced.

**Remediation SLA**:

- Critical vulnerabilities: 48 hours (extended from 24 to reflect the physical estate and teaching-hours access constraint; deviations from the university standard are recorded here deliberately)
- High vulnerabilities: 14 days
- Medium vulnerabilities: 30 days

**Additional Requirements**:

- Vendor shall provide a published vulnerability disclosure process and security advisories
- Appliances that cannot be patched shall be identified in the inventory and either replaced or removed from service — not retained as exceptions

**Rationale**: Lecture-theatre capture appliances are behind on OS patching, holding "patch operating systems" at ML1 against an ML2 target [PC-C1] [PC-C4].

**Priority**: CRITICAL

---

### Compliance and Regulatory Requirements

#### NFR-C-001: Privacy Act 1988 compliance and data residency

**Applicable Regulations**: Privacy Act 1988 (Australian Privacy Principles), including APP 8 (cross-border disclosure) and the Notifiable Data Breach scheme

**Compliance Requirements**:

- [ ] Australian data residency for recordings and derived assets, preferred and stated (REQ-030) [RR-C7]
- [ ] Where any component is hosted offshore, APP 8 assessment completed covering accountability, contract clauses and the practicability of AU-region alternatives [PC-C6]
- [ ] Privacy Impact Assessment completed on the preferred option **before contract signature**
- [ ] Collection notification to students (FR-013)
- [ ] Data minimisation applied to derived analytics (DR-003)

**Data Residency**: Recordings, transcripts, captions and derived analytics held in Australia. Any exception requires a documented APP 8 assessment and Privacy & Records Officer sign-off.

**Data Retention**: Per the approved schedule (DR-005), enforced by FR-014

**Rationale**: Video and audio recordings capturing students are classified as personal information with a biometric-adjacent character, currently under assumed AU/US hosting, and are flagged as a partial APP 8 trigger [PC-C2] [PC-C6].

**Priority**: CRITICAL

---

#### NFR-C-002: Accessibility — MANDATORY GATE

**Requirement**: WCAG 2.2 Level AA conformance for all student-facing and staff-facing interfaces, and for the captioning of recorded content (REQ-029) [RR-C8].

**Accessibility Features**:

- [ ] Keyboard navigation for all playback and authoring functions
- [ ] Screen reader compatibility for the recording list and player
- [ ] Captions for all published recordings (FR-006)
- [ ] Transcript available as text
- [ ] Playback controls operable without a mouse
- [ ] Contrast and text sizing meeting AA

**Testing**: Conformance assessed during evaluation against the platform as it will be configured, not against a vendor conformance claim. Principle 14 requires accessibility to be assessed during evaluation and before release, never remediated after deployment [PRIN-C5].

> **Evaluation treatment**: Mandatory pass/fail gate.

**Priority**: CRITICAL

---

#### NFR-C-003: Audit logging

**Requirement**: Comprehensive, tamper-evident audit trail for access to and lifecycle of recordings.

**Audit Log Contents**:

- Who: authenticated identity
- What: view, download, edit, publish, unpublish, export, dispose
- When: timestamp, UTC, millisecond precision
- Where: platform component or room appliance
- Why: session or request context
- Result: success or failure with reason

**Log Retention**: 7 years for disposal and export events; 2 years for access events, subject to the approved records schedule

**Log Integrity**: Immutable storage for disposal and export events

**Priority**: HIGH

---

#### NFR-C-004: Essential Eight evidence

**Requirement**: The platform and its estate shall produce evidence sufficient to assess Essential Eight maturity for this estate, specifically for application control, patch applications, patch operating systems, restrict administrative privileges, MFA and regular backups (REQ-033) [RR-C5].

**Report Types**:

- Patch status by appliance: monthly, to Cybersecurity Lead
- Administrative account inventory: quarterly, to Cybersecurity Lead
- Backup and restore test evidence: annually, to Cybersecurity Lead

**Priority**: HIGH

---

#### NFR-C-005: Breach notification support

**Requirement**: The vendor shall notify the university of any actual or suspected data breach affecting university data within 24 hours of becoming aware, with sufficient detail to support an eligible-data-breach assessment.

**Rationale**: The Notifiable Data Breach scheme imposes a 30-day assessment clock on the university [PC-C7]. A vendor notification obligation measured in days rather than hours consumes the assessment window before the university knows a breach occurred.

**Priority**: HIGH

---

### Usability Requirements

#### NFR-U-001: Academic workflow effort

**Requirement**: Scheduled capture shall require zero academic actions. Ad-hoc capture shall require no more than two actions from the unit context. Publication shall require zero actions where the unit uses the institutional default.

**UX Standards**: Consistent with the LMS entry point (Principle 1); no separate portal as the primary student route

**User Onboarding**: Contextual help and a one-page quick reference; training delivered before the user's first teaching week on the platform (BR-006)

**Priority**: HIGH

---

#### NFR-U-002: Cross-school consistency

**Requirement**: The student-facing experience — location of recordings, presentation, captions, playback controls — shall be identical across all schools and units.

**Rationale**: Principle 3 (Consistent Experience Across Schools) and the survey's single-entry-point requirement (REQ-007). Variation between schools is currently the sharpest edge of the student experience concern raised by the Student Guild [STKE-C7].

**Priority**: HIGH

---

#### NFR-U-003: Caption accuracy

**Requirement**: Automatic captions shall achieve a word error rate low enough to support WCAG 2.2 AA conformance, validated against a discipline-vocabulary test set drawn from Health Sciences and Music & Performing Arts teaching.

**Measurement Method**: Accuracy sampled against a fixed test set built before evaluation and reused each semester. Vendor accuracy claims are not accepted as evidence.

**Rationale**: Auto-captioning quality varies most where it matters most — clinical and musical terminology — so a platform that captions general speech well and discipline vocabulary poorly delivers a materially worse service to the students who most depend on captions [STKE-C8].

**Priority**: HIGH

---

### Maintainability and Supportability Requirements

#### NFR-M-001: Observability

**Requirement**: Capture health, processing status and integration health shall be observable centrally, in real time, with alerting routed by failure class.

**Telemetry Requirements**:

- **Room status dashboard**: appliance health, last successful capture, scheduled next capture
- **Processing and publication metrics**: queue depth, latency distribution, failure counts by class
- **Integration health**: provisioning event throughput and failure, timetable feed freshness
- **Alerts**: routed to AV for room failures, to support for user-affecting failures, to integration for provisioning failures — with runbook links

**Rationale**: Principle 17 (Observable Integrations and Services). FR-004's alerting depends on this being present rather than assembled after go-live.

**Priority**: HIGH

---

#### NFR-M-002: Documentation and runbooks

**Requirement**: Runbooks and user documentation shall be published before cutover, not after.

**Documentation Types**:

- [ ] Support runbooks for each failure class in FR-004
- [ ] Room appliance provisioning and patching procedure
- [ ] Academic quick reference for scheduled, ad-hoc and edit workflows
- [ ] Student help content for playback, captions and access
- [ ] Migration reconciliation and rollback procedure
- [ ] Retention and disposal operating procedure

**Documentation Currency**: Reviewed each teaching period

**Priority**: MUST_HAVE

---

### Portability and Interoperability Requirements

#### NFR-I-001: Integration standards

**Requirement**: Integrations shall use documented, standard interfaces — LTI 1.3 for LMS integration, SAML 2.0 or OIDC for authentication, SCIM or an equivalent documented API for provisioning, and REST with JSON for data exchange.

**Rationale**: Principle 10 (Interface-Mediated Integration) prohibits direct database coupling; Principle 11 favours event-driven and near-real-time integration over batch. A platform whose only provisioning path is bulk file import fails REQ-025 by construction.

**Priority**: CRITICAL

---

#### NFR-I-002: Data portability and exit — MANDATORY GATE

**Requirement**: All university data — recordings, captions, transcripts, metadata and engagement analytics — shall be exportable in open, documented formats at any time and on termination, without additional fee and without vendor assistance being required.

**Export Formats**: Media in a widely supported open container; captions in an open caption format; metadata and analytics in a documented structured format

**Import Capability**: Bulk import of the migrated archive with metadata and captions preserved (FR-015)

> **Priority deviation, recorded deliberately**: REQ-034 carries a **Should** priority in the survey register [RR-C9], but Principle 9 states that every platform holding university or student data **MUST** permit export in open documented formats without dependence on vendor goodwill or additional fee [PRIN-C4]. This requirement is elevated to MUST_HAVE on the authority of Principle 9. The rationale is specific to this project: the archive migration in BR-007 is only executable if the *incumbent* honours the same standard, and selecting a new platform without it would repeat the trap. Elevation is flagged for Education Committee visibility rather than applied silently.

**Priority**: CRITICAL — mandatory pass/fail gate

---

## Integration Requirements

### External System Integrations

#### INT-001: Student information system → capture platform (identity, enrolment, roles)

**Purpose**: Provide the capture platform with authoritative identity, enrolment and institutional role data so that access derives from the record rather than from local configuration (FR-016, UC-2)

**Integration Type**: Event-driven, near-real-time

**Data Exchanged**:

- **From SIS to capture platform**: person identity, unit enrolment, institutional role assignment — on change
- **From capture platform to SIS**: none

**Integration Pattern**: Publish/subscribe against the canonical entity model defined in project 001 (REQ-027)

**Authentication**: Service identity with least privilege; no shared credentials

**Error Handling**: Failed provisioning raises an alert and retries with backoff; failures are never silently dropped

**SLA**: 15 minutes from source change to effective access (aligned to REQ-023)

**Owner**: Sam Okafor (Integration Architect)

**Priority**: CRITICAL

---

#### INT-002: Timetabling (Allocate+) → capture platform (session scheduling)

**Purpose**: Drive automatic capture scheduling from the authoritative timetable (FR-001, UC-1)

**Integration Type**: Scheduled feed with change events

**Data Exchanged**:

- **From timetabling to capture platform**: session records — unit, room, start, end, presenter — for the teaching period, plus subsequent changes
- **From capture platform to timetabling**: none

**Integration Pattern**: Bulk load at period start; change events thereafter

**Authentication**: Service identity

**Error Handling**: Reconciliation report on each run; unmatched rooms or units flagged rather than skipped

**SLA**: Schedule reconciled within 1 hour of a timetable change

**Owner**: Ivy Sequence (Timetabling) with Sam Okafor

**Priority**: CRITICAL

---

#### INT-003: Capture platform ↔ LMS (Blackboard Ultra)

**Purpose**: Place recordings in the unit site as the single student entry point, and derive unit context (FR-002, FR-010, REQ-007)

**Integration Type**: LTI 1.3 with deep linking and names/roles provisioning service

**Data Exchanged**:

- **From capture platform to LMS**: recording listings and playback surfaces within the unit site
- **From LMS to capture platform**: unit context and, where used, roster context

**Integration Pattern**: Standards-based LTI; no custom database coupling

**Authentication**: LTI 1.3 security profile

**Error Handling**: Where placement fails, the recording remains accessible and support is alerted; students never encounter an empty unit site without explanation

**SLA**: Placement within the 4-hour publication window

**Owner**: Dr. Benny Moog with Sam Okafor

**Priority**: CRITICAL

---

#### INT-004: Identity provider (SSO with MFA)

**Purpose**: Enforce NFR-SEC-001 — university SSO with MFA, no local accounts

**Integration Type**: Federated authentication

**Data Exchanged**:

- **From IdP to capture platform**: authenticated identity and assertions
- **From capture platform to IdP**: authentication requests

**Integration Pattern**: SAML 2.0 or OIDC

**Authentication**: Federation trust; MFA enforced at the IdP

**Error Handling**: Authentication failure must not fall back to any local credential path — no such path may exist

**SLA**: Aligned to the university IdP availability standard

**Owner**: Tobias Ohm (Cybersecurity Lead)

**Priority**: CRITICAL

---

#### INT-005: Capture platform → institutional data platform (analytics export)

**Purpose**: Make engagement data available for cross-system analysis (REQ-022, FR-011)

**Integration Type**: Scheduled export

**Data Exchanged**:

- **From capture platform to data platform**: engagement and viewing data at the minimisation level defined in DR-003

**Integration Pattern**: Scheduled extract in a documented open format

**Authentication**: Service identity

**Error Handling**: Failed export alerts; no partial loads without a marker

**SLA**: Daily, with data no more than 24 hours stale

**Owner**: Sam Okafor

**Priority**: SHOULD_HAVE

---

#### INT-006: Capture platform ↔ room appliances and specialist AV

**Purpose**: Schedule, execute, monitor and manage capture in teaching spaces and named performance venues (FR-001, FR-004, FR-009, BR-008)

**Integration Type**: Device management and telemetry

**Data Exchanged**:

- **From platform to appliance**: capture schedule, configuration, patches
- **From appliance to platform**: recordings, health telemetry, capture events

**Integration Pattern**: Managed device channel with local buffering (NFR-A-002)

**Authentication**: Per-device identity — explicitly **not** shared administrative credentials (NFR-SEC-002)

**Error Handling**: Health telemetry drives the alerting in FR-004; loss of contact is itself an alertable event

**SLA**: Health telemetry at least every 15 minutes per appliance

**Owner**: Marcus Fairlight (AV & Learning Spaces)

**Priority**: CRITICAL

---

#### INT-007: Incumbent platform → target platform (archive migration)

**Purpose**: Move the in-retention recordings archive with metadata and captions (BR-007, FR-015)

**Integration Type**: One-time bulk export and import, executed in stages

**Data Exchanged**:

- **From incumbent to target**: recording media, captions, transcripts, metadata, unit and session association

**Integration Pattern**: Export package with manifest; staged import with reconciliation

**Authentication**: Administrative service identity on both sides, time-bound to the migration window

**Error Handling**: Per-batch reconciliation; no source decommissioning until reconciliation is complete and signed off

**SLA**: Migration completed within the July 2027 inter-semester break

**Owner**: Rhonda Bell with Dr. Benny Moog

**Priority**: CRITICAL

---

## Data Requirements

### Data Entities

#### Entity 1: Recording

**Description**: A captured session — media plus derived assets

**Attributes**:

| Attribute | Type | Required | Description | Constraints |
|-----------|------|----------|-------------|-------------|
| recording_id | UUID | Yes | Unique identifier | Primary key |
| session_id | UUID | Yes | Timetabled or ad-hoc session | Indexed, FK to Session |
| unit_code | String(20) | Yes | Unit the recording belongs to | Indexed, must resolve to LMS unit site |
| captured_at | Timestamp | Yes | Session start, UTC | Indexed |
| duration_seconds | Integer | Yes | Recording length | > 0 |
| media_uri | String | Yes | Storage location of media | Encrypted at rest |
| caption_uri | String | No | Caption file location | Open format |
| transcript_uri | String | No | Transcript location | Open format |
| publication_state | Enum | Yes | Publication status | ['captured', 'processing', 'published', 'held', 'restricted', 'archived', 'disposed'] |
| published_at | Timestamp | No | Publication time | Used for the 4-hour measure |
| retention_until | Date | Yes | End of retention | Derived from DR-005 schedule |
| hold_flag | Boolean | Yes | Legal or investigative hold | Suppresses disposal |

**Relationships**:

- Many-to-one with Session
- Many-to-one with Unit
- One-to-many with Viewing Event

**Data Volume**: Baseline and growth to be sourced ⚠️ (Eleanor Frame, due 2026-08-28) — see NFR-S-001

**Access Patterns**: By unit and teaching period (student and coordinator views); by retention date (disposal job); by capture date (operational reporting)

**Data Classification**: CONFIDENTIAL — personal information, biometric-adjacent [PC-C2]

**Data Retention**: Per approved schedule (DR-005); disposal enforced by FR-014

---

#### Entity 2: Session

**Description**: A scheduled or ad-hoc teaching event that may be captured

**Attributes**:

| Attribute | Type | Required | Description | Constraints |
|-----------|------|----------|-------------|-------------|
| session_id | UUID | Yes | Unique identifier | Primary key |
| unit_code | String(20) | Yes | Unit reference | Indexed |
| room_id | String(50) | No | Teaching space; null for ad-hoc remote | FK to Room |
| scheduled_start | Timestamp | Yes | Session start | Indexed |
| scheduled_end | Timestamp | Yes | Session end | > scheduled_start |
| presenter_id | String(50) | No | Scheduled presenter | FK to Person |
| source | Enum | Yes | Origin of the session record | ['timetable', 'ad_hoc'] |
| capture_policy | Enum | Yes | Effective capture behaviour | ['auto_publish', 'hold_for_review', 'no_capture'] |

**Relationships**:

- One-to-many with Recording
- Many-to-one with Room, Unit

**Data Volume**: Bounded by timetabled sessions per teaching period plus ad-hoc

**Access Patterns**: By period for schedule generation; by room for AV operations

**Data Classification**: INTERNAL

**Data Retention**: Retained while any associated recording is retained; then disposed

---

#### Entity 3: Person (identity projection)

**Description**: The minimal identity projection the capture platform holds — not a master record

**Attributes**:

| Attribute | Type | Required | Description | Constraints |
|-----------|------|----------|-------------|-------------|
| person_id | String(50) | Yes | Institutional identifier | Primary key, from authoritative source |
| display_name | String(255) | Yes | Name for display | From authoritative source |
| institutional_role | Enum | Yes | Role in context | ['student', 'coordinator', 'tutor', 'marker', 'av_operator', 'admin'] |
| unit_associations | Array | Yes | Units and role per unit | Derived, never locally edited |
| account_state | Enum | Yes | Provisioning state | ['active', 'suspended', 'deprovisioned'] |

**Relationships**:

- Many-to-many with Unit via unit_associations

**Data Volume**: Bounded by enrolled students plus teaching staff per period

**Access Patterns**: By person for authorisation; by unit for cohort resolution

**Data Classification**: CONFIDENTIAL — personal information

**Data Retention**: Deprovisioned records removed within 90 days of the person having no active association, subject to audit log retention

> **Minimisation note**: The platform holds no password, no contact detail beyond what SSO requires, and no demographic data. Principle 7 (Privacy by Design and Data Minimisation) applies: this is a projection for authorisation, not a copy of the student record.

---

#### Entity 4: Viewing Event (engagement analytics)

**Description**: Record that a person viewed part of a recording — the basis of engagement analytics

**Attributes**:

| Attribute | Type | Required | Description | Constraints |
|-----------|------|----------|-------------|-------------|
| event_id | UUID | Yes | Unique identifier | Primary key |
| recording_id | UUID | Yes | Recording viewed | FK to Recording |
| person_id | String(50) | Yes | Viewer | FK to Person; pseudonymised on export |
| viewed_at | Timestamp | Yes | Event time | Indexed |
| watched_seconds | Integer | Yes | Duration watched | ≥ 0 |
| resume_position | Integer | No | Last position | Supports FR-010 |

**Relationships**:

- Many-to-one with Recording and Person

**Data Volume**: The highest-volume entity; grows with coverage and cohort size

**Access Patterns**: Aggregated by unit and session (FR-011); exported to the data platform (INT-005)

**Data Classification**: CONFIDENTIAL — derived personal information [PC-C8]

**Data Retention**: **This is a gap being closed.** Analytics derived from this estate currently have no defined retention or minimisation rules [PC-C3]. This project shall set: identifiable viewing events retained for the teaching period plus 12 months, then aggregated and the identifiers destroyed; exports to the institutional data platform pseudonymised at source.

---

### Data Requirements Detail

The entities above describe *what is held*. The requirements below state *what must be true of it*, and carry the IDs referenced elsewhere in this document.

#### DR-001: Recording classification and handling

**Description**: Recordings and their derived assets (transcript, captions, thumbnails) shall be classified as personal information with a biometric-adjacent character, and handled under that classification throughout capture, storage, playback, export and disposal.

**Rationale**: The personal information inventory classifies video and audio recordings capturing students as PI (biometric-adjacent) [PC-C2]. Classification drives the encryption, access, residency and retention requirements that follow; treating recordings as ordinary content is the failure this prevents.

**Acceptance Criteria**:

- [ ] Given any recording, when its handling is assessed, then encryption (NFR-SEC-003), access control (FR-016) and residency (NFR-C-001) all apply without exception
- [ ] Given a derived asset such as a transcript, when handled, then it carries the same classification as the recording it derives from

**Priority**: MUST_HAVE

**Relates To**: Entity 1 (Recording), NFR-C-001, NFR-SEC-003, FR-013

---

#### DR-002: Canonical entity alignment

**Description**: Unit, session, person and enrolment data used by the capture platform shall conform to the canonical data model for student, course and enrolment defined in project 001 (REQ-027); the platform shall hold no divergent local definition of these entities.

**Rationale**: Principle 6 (Canonical Data Model) and REQ-027. A platform-specific schema mapped point-to-point is what produced the current integration fragility.

**Acceptance Criteria**:

- [ ] Given an integration payload, when validated, then it conforms to the canonical model rather than a platform-specific schema
- [ ] Given a divergence between platform and canonical definitions, when detected by reconciliation, then it is reported rather than silently reconciled

**Priority**: MUST_HAVE

**Relates To**: Entity 2 (Session), Entity 3 (Person), INT-001, INT-002, TC-3

---

#### DR-003: Engagement analytics minimisation and retention

**Description**: Identifiable viewing events shall be retained for the teaching period plus 12 months, then aggregated with identifiers destroyed. Exports to the institutional data platform shall be pseudonymised at source. Aggregate views shall suppress cohorts below a minimum size threshold.

**Rationale**: Analytics derived from this estate currently have no defined retention or minimisation rules [PC-C3] — this requirement closes that gap. Principle 7 (Privacy by Design and Data Minimisation) applies to derived data as much as to collected data.

**Acceptance Criteria**:

- [ ] Given viewing events older than the teaching period plus 12 months, when the retention job runs, then identifiers are destroyed and only aggregates remain
- [ ] Given an export to the institutional data platform, when produced, then it is pseudonymised at source rather than after transfer
- [ ] Given a cohort below the minimum threshold, when analytics are displayed, then the view is suppressed

**Priority**: MUST_HAVE

**Relates To**: Entity 4 (Viewing Event), FR-011, INT-005, NFR-C-001

---

#### DR-004: Identity projection minimisation

**Description**: The capture platform shall hold the minimum identity attributes required for authorisation and display — no password, no contact detail beyond what SSO requires, no demographic data — and shall remove deprovisioned records within 90 days of the person having no active association.

**Rationale**: Principle 7 and Principle 5 (Single Source of Truth for Core Entities). The platform is a consumer of identity, not a master; every additional attribute it holds is an additional copy of personal information to secure and dispose of.

**Acceptance Criteria**:

- [ ] Given a provisioned person record, when inspected, then it contains only identifier, display name, role and unit associations
- [ ] Given a person with no active association for 90 days, when the retention job runs, then the record is removed subject to audit log retention

**Priority**: MUST_HAVE

**Relates To**: Entity 3 (Person), INT-001, FR-016, NFR-SEC-001

---

#### DR-005: Recordings retention and disposal schedule

**Description**: An approved retention schedule shall define retention periods for recordings by category, the disposal trigger, the hold mechanism and the archive-on-request path, covering recordings, transcripts, captions and derived analytics identifiers.

**Rationale**: No retention rule is currently applied to recordings [PC-C3]. Migration is the only operationally natural point at which a schedule can be applied [STKE-C5], which makes approval of the schedule a blocking dependency on migration planning (D-5), not a parallel activity.

**Acceptance Criteria**:

- [ ] Given the schedule, when approved by Education Committee, then every recording category has a defined retention period and disposal trigger
- [ ] Given the schedule, when applied, then disposal is the default at end of retention and continued retention requires an active decision
- [ ] Given migration planning, when it completes, then the approved schedule exists — planning cannot complete without it

**Priority**: MUST_HAVE

**Relates To**: Entity 1 (Recording), FR-014, BR-007, D-5, Conflict C-4

---

#### DR-006: Residency and cross-border disclosure register

**Description**: The storage location of recordings, transcripts, captions and derived analytics shall be documented per data class, with any offshore hosting recorded in a cross-border disclosure register and assessed under APP 8.

**Rationale**: Recordings are currently held under assumed AU and US hosting and are flagged as a partial APP 8 trigger [PC-C2] [PC-C6]. REQ-030 prefers Australian residency and requires APP 8 assessment for any offshore disclosure [RR-C7]. Without a register, the position is reassessed from scratch at every audit.

**Acceptance Criteria**:

- [ ] Given each data class, when the register is inspected, then its storage location and legal jurisdiction are stated
- [ ] Given any offshore component, when identified, then an APP 8 assessment exists covering accountability, contract clauses and the practicability of AU-region alternatives
- [ ] Given a vendor change to hosting location, when notified, then the register is updated and the assessment revisited

**Priority**: MUST_HAVE

**Relates To**: NFR-C-001, Entity 1, contract terms under BR-007

---

#### DR-007: Migration data integrity

**Description**: The migrated archive shall reconcile to source by count and by association, with every difference explained, and provenance retained so that a migrated recording's origin remains evident after cutover.

**Rationale**: BR-007 and FR-015 depend on reconciliation being evidential rather than assumed. The incumbent platform is not decommissioned until reconciliation is signed off, which makes the reconciliation record the rollback safety net.

**Acceptance Criteria**:

- [ ] Given a migration batch, when it completes, then target count reconciles to source count with every difference explained
- [ ] Given a migrated recording, when inspected, then captions, metadata and unit association are intact and provenance is recorded
- [ ] Given incomplete reconciliation, when decommissioning is proposed, then it is blocked

**Priority**: MUST_HAVE

**Relates To**: FR-015, INT-007, BR-007, A-10

---

### Data Quality Requirements

**Data Accuracy**: Unit and session association must be correct in 100% of published recordings — a recording in the wrong unit site is a privacy incident, not a data quality defect. Caption accuracy per NFR-U-003.

**Data Completeness**: Every recording must carry unit, session, capture time and retention date. Recordings that cannot be associated to a unit are quarantined rather than published.

**Data Consistency**: Person and enrolment data must reconcile to the authoritative source; a scheduled reconciliation shall report divergence rather than silently correcting it.

**Data Timeliness**: Identity and enrolment within 15 minutes of source change (INT-001); timetable within 1 hour (INT-002); analytics within 24 hours (INT-005).

**Data Lineage**: Every recording traces to a session, a room and a source system event. Migration provenance is retained for migrated recordings so that origin remains evident after cutover.

---

### Data Migration Requirements

**Migration Scope**: All in-retention recordings with metadata and captions. Out-of-retention content is disposed of under FR-014 rather than migrated — migration is the disposal trigger.

**Migration Strategy**: Phased by teaching period, oldest first, with the current and prior period migrated last to minimise the window during which content is in flight.

**Data Transformation**: Metadata mapped to the target schema; unit and session association re-resolved against the canonical model; caption formats normalised to the target open format.

**Data Validation**: Per-batch reconciliation of source count to target count, with every difference explained; sample-based playback verification; caption presence check; link-check sweep across unit sites.

**Rollback Plan**: The incumbent platform remains available read-only until reconciliation is signed off. No source content is deleted until sign-off. Rollback is therefore a redirect reversal, not a data restore.

**Migration Timeline**: July 2027 inter-semester break, with staged batches beginning after the Semester 1 pilot concludes.

---

## Constraints and Assumptions

### Technical Constraints

**TC-1**: The platform must integrate with the existing university identity provider using SSO with MFA; no local account path may exist (REQ-031) [RR-C6].

**TC-2**: The platform must publish into Blackboard Ultra as the student entry point (REQ-007, Principle 1) — a separate student portal is not an acceptable primary route.

**TC-3**: Integrations must use the canonical entity model for student, course and enrolment defined in project 001 (REQ-027); point-to-point mappings against a platform-specific schema are not acceptable.

**TC-4**: The solution operates within the existing lecture-theatre estate. Any option requiring appliance replacement must declare it at options stage, costed (BR-003).

**TC-5**: Bulk user file loads are prohibited in production (Principle 12) — this constrains platform selection, not just configuration.

---

### Business Constraints

**BC-1**: The decision must clear Operations Committee by 9 October 2026 to feed the September–October business case cycle (BR-002) [CB-C2].

**BC-2**: Cutover must occur in a non-teaching period; the July 2027 inter-semester break is the target window and the only viable one before Semester 2 2027 (BR-006).

**BC-3**: Whole-of-life cost must hold flat or reduce (BR-003, REQ-035) [RR-C2].

**BC-4**: All vendor contact routes through Procurement from the point criteria drafting begins (BR-004) — this constrains how requirements may be validated with suppliers.

**BC-5**: Any solution duplicating capability already licensed must justify why the incumbent tool is unsuitable [SGP-C2]. This applies in both directions and is a governance gate, not a preference.

---

### Assumptions

**A-1**: Timetable data is authoritative for room, time and unit, and is available to the capture platform for the full teaching period. **Validation**: confirm feed availability with Ivy Sequence by 2026-08-21.

**A-2**: LMS unit sites exist and cohorts are provisioned before the teaching period begins, so publication has a destination. **Validation**: confirm with Learning Technologies during evaluation.

**A-3**: Room appliances can report health telemetry to a central management point. **Validation**: appliance inventory, Marcus Fairlight, due 2026-08-21 — this assumption may fail for older appliances and would then become a replacement driver.

**A-4**: Clinical simulation capture inside iSimulate and Kuracloud remains within those products; this project assesses interface only, not replacement. **Validation**: confirm with Prof. Priya Anand before options analysis.

**A-5**: Automatic captioning is the primary mechanism; human captioning is exception-only and does not carry the volume. **Validation**: accuracy test set results during evaluation.

**A-6**: Rights and consent for recorded musical performance are addressed under existing university copyright and performance policy, not created by this project. **Validation**: confirm with the University Copyright Officer before performance capture is scoped.

**A-7**: Live delivery (REQ-008) and lecture capture (REQ-009) may be served by one platform or two bounded platforms; the requirements are written to be neutral, and BR-001 resolves it.

**A-8**: Education Committee approves the capture policy and its exception route; the platform enforces policy rather than defining it.

**A-9**: Education Committee approves the recordings retention schedule before migration planning completes. **Validation**: schedule drafted by Eleanor Frame, committee date to be confirmed.

**A-10**: The incumbent contract permits bulk export of recordings, captions and metadata without additional fee. **Validation**: Grace Tanaka, contract review due 2026-08-14. **If this fails, BR-007 and FR-015 are materially affected — see R-3.**

**A-11**: Project 001 delivers institutional role assignment from a single authoritative source (REQ-024) and the canonical model (REQ-027) in time for INT-001. **Validation**: dependency tracked with Sam Okafor.

---

## Success Criteria and KPIs

### Business Success Metrics

| Metric | Baseline | Target | Timeline | Measurement Method |
|--------|----------|--------|----------|-------------------|
| Platforms with overlapping capture capability | 3 [SL-C1] | 1 primary + 1 bounded exception | Oct 2026 (decision), Jul 2027 (effective) | System categorisation map |
| Five-year whole-of-life cost | ⚠️ To be sourced (Grace Tanaka / Cassandra Rhodes, 2026-08-14) | At or below baseline | Sep 2026 (model), annually thereafter | Cost model reviewed by Finance |
| Governance gates cleared on schedule | No decision | 3 of 3 | Oct 2026 | Committee minutes |
| Decision reopenings | Not applicable | Zero within 24 months | Oct 2028 | RIFF register |

### Technical Success Metrics

| Metric | Target | Measurement Method |
|--------|--------|-------------------|
| Capture coverage in equipped rooms | 100% of timetabled lectures | Platform reporting vs timetable extract (FR-018) |
| Publication within 4 hours | ≥ 99% | Platform reporting |
| Median publication latency | < 1 hour | Platform reporting |
| Availability during teaching periods | ≥ 99.9% | Availability monitoring |
| Manual provisioning events | Zero | Provisioning audit log |
| Local accounts on the capture platform | Zero | Identity platform audit |
| Recordings captioned within 24 hours | 100% | Captioning report |
| Caption accuracy on discipline test set | Meets the threshold set at evaluation | Semester sample against fixed test set |
| Shared administrative accounts in the estate | Zero | Account inventory |
| Appliances within managed patching regime | 100% of retained appliances | AV asset register |
| Recordings lost in transition | Zero | Migration reconciliation |

### User Adoption Metrics

| Metric | Target | Timeline | Measurement Method |
|--------|--------|----------|-------------------|
| Units using the institutional default capture policy | ≥ 90% | End Semester 2 2027 | Policy configuration report |
| Capture-related support tickets, first 4 weeks post-cutover | Within pilot-derived forecast | Aug 2027 | Service desk data |
| Staff trained before their first teaching week on the platform | 100% of coordinators, 100% of casuals with capture roles | Jul 2027 | Training records |
| Student-reported access or caption issues | Declining trend across two semesters | End 2027 | Guild feedback and support data |

---

## Dependencies and Risks

### Dependencies

| Dependency | Description | Owner | Target Date | Status | Impact if Delayed |
|------------|-------------|-------|-------------|--------|-------------------|
| D-1 | Contract values, terms and renewal dates for incumbent platforms | Grace Tanaka | 2026-08-14 | At Risk | HIGH — BR-003 cannot be modelled |
| D-2 | Microsoft entitlement position — what capture capability is already licensed | Cassandra Rhodes | 2026-08-14 | At Risk | HIGH — the consolidation argument is untestable without it |
| D-3 | Appliance inventory: models, age, patch status, management capability | Marcus Fairlight | 2026-08-21 | At Risk | HIGH — A-3 unvalidated; TC-4 unassessable |
| D-4 | Capture policy approved (publication default, exceptions, notification) | Education Committee | Before cutover | On Track | MEDIUM — FR-012 and FR-013 lack an authority to enforce |
| D-5 | Recordings retention schedule approved | Education Committee / Eleanor Frame | Before migration planning completes | On Track | HIGH — migration defaults to lift-everything |
| D-6 | Caption correction capacity resourced in Digital Learning Support | Nina Kalimba | Before cutover | On Track | MEDIUM — FR-007 exists without an owner |
| D-7 | Canonical entity model and authoritative role assignment from project 001 | Sam Okafor | Before INT-001 build | On Track | HIGH — INT-001 and FR-016 blocked |
| D-8 | Discipline-vocabulary caption test set built | Dr. Benny Moog with Health Sciences and Music | Before evaluation | At Risk | MEDIUM — NFR-U-003 becomes unmeasurable, defaults to vendor claims |

### Risks

| Risk ID | Description | Probability | Impact | Mitigation Strategy | Owner |
|---------|-------------|-------------|--------|---------------------|-------|
| R-1 | Evaluation criteria negotiation deadlocks between the opposing platform positions | HIGH | HIGH | Independent facilitation; anchor weights to register MoSCoW priority; set mandatory gates first; two-session cap with escalation | Rhonda Bell |
| R-2 | Baseline data (D-1, D-2, D-3) not delivered, forcing evaluation on assumptions | MEDIUM | HIGH | Due dates tracked as hard milestones with named owners; escalate to steering at first slip | Rhonda Bell |
| R-3 | Incumbent export terms restrictive or fee-bearing, stranding the archive (A-10 fails) | MEDIUM | HIGH | Contract review before criteria finalised; practical export test during evaluation; retention schedule applied first to minimise volume | Grace Tanaka |
| R-4 | Appliance estate incompatible or unpatchable, converting the decision into a capital programme | MEDIUM | HIGH | Inventory before decision; room compatibility as a scored criterion; refresh split into required-regardless and decision-caused | Marcus Fairlight |
| R-5 | Decision slips past October, compressing transition toward a teaching period | MEDIUM | HIGH | Committee dates confirmed and papers scheduled backwards; platform-neutral work progressed in parallel; **cutover in a teaching period is prohibited, not merely discouraged** | Prof. Otis Hammond |
| R-6 | Discipline exception endorsed in principle but unfunded | MEDIUM | MEDIUM | Costed line item in the same governance paper as the core recommendation | Prof. Desmond Key |
| R-7 | Selected platform supports only bulk-import provisioning, breaching REQ-025 and Principle 12 | LOW | HIGH | Provisioning API made a mandatory pass/fail gate (NFR-I-001), tested not assumed | Sam Okafor |
| R-8 | Caption accuracy assessed on vendor claims because the test set was not built (D-8 fails) | MEDIUM | MEDIUM | Test set is an evaluation deliverable with a named owner and date, not a post-selection activity | Dr. Benny Moog |

**Risk Scoring**: Probability × Impact = Risk Level

- High Risk (Red): Requires executive escalation — R-1, R-2, R-3, R-4, R-5
- Medium Risk (Yellow): Active monitoring and mitigation — R-6, R-8
- Low Risk (Green): Accepted with control — R-7

---

## Requirement Conflicts & Resolutions

> Conflicts below derive from the stakeholder conflict analysis in `ARC-002-STKE-v1.0.md` and are expressed here at requirement level. Decision authority references the RACI in that document.

### Conflict C-1: Consolidation onto licensed capability vs purpose-built capture depth

**Conflicting Requirements**:

- **Requirement A**: BR-003 (whole-of-life cost flat or reduced) read together with Principle 19 (realise licensed capability before new spend) — favours consolidating onto capability already held
- **Requirement B**: FR-001 to FR-011 collectively (scheduled capture, publication SLA, editing, captioning, analytics, LMS depth) — favours a purpose-built capture platform

**Stakeholders Involved**:

- **Cassandra Rhodes (CIO)**: Wants A because the university is paying twice for capability inside an agreement it already signed, and every extra platform is another integration, patching surface and support queue [S-C1]
- **Dr. Benny Moog (Learning Technologies)**: Wants B because lecture capture and meeting recording are different product classes, and the difference will be dismissed in a cost comparison [STKE-C9]

**Nature of Conflict**:

Both parties can cite institutional principle — Principle 19 for consolidation, Principle 4 and the capability requirements for specialisation. The conflict is not resolvable by more product analysis, because the parties disagree about what is being compared, not about the facts of either product.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Option 1**: Consolidate onto already-licensed platform | ✅ Direct licence saving<br>✅ Fewer integrations and platforms to secure | ❌ Capture-specific requirements may be met shallowly<br>❌ Analytics and LMS depth at risk | Rhodes satisfied<br>Moog, Key, Clavinet opposed |
| **Option 2**: Retain purpose-built capture platform | ✅ Capture requirements met at depth<br>✅ No academic disruption | ❌ Duplication persists against Principle 19<br>❌ REQ-035 position weakened | Moog satisfied<br>Rhodes, Ostinato opposed |
| **Option 3**: Decide by weighted criteria agreed before evaluation, with mandatory gates | ✅ Converts the dispute into a decidable question<br>✅ Both parties bound by criteria they signed | ❌ Requires both to accept an adverse result<br>❌ Costs time up front | Both bound; neither guaranteed |
| **Option 4**: Retain both with a declared boundary (Principle 2) | ✅ Legitimate under the pause provision [SGP-C3]<br>✅ Least disruption | ❌ Cost position unimproved<br>❌ Defers rather than resolves | Ostinato and Rhodes dissatisfied |

**Resolution Strategy**: PRIORITIZE (the process, not either position)

**Decision**: Option 3. The evaluation criteria and weightings are agreed and signed by Rhodes, Moog and Tanaka before any vendor engagement (BR-004), with mandatory pass/fail gates for security (NFR-SEC-001), accessibility (NFR-C-002) and export (NFR-I-002) removed from the trading space entirely. Option 4 is retained as a genuine outcome of the evaluation, not as a strawman — the pause provision explicitly permits it.

**Rationale**: Neither party's position can be adjudicated on its merits without agreed criteria, and any decision taken without them will be reopened at renewal. Anchoring the weights to the register's MoSCoW priorities means the weighting is derived from a prioritisation both parties already accepted through Education Committee [RR-C10], rather than negotiated fresh under adversarial conditions.

**Decision Authority**: Grace Tanaka is accountable for the criteria; Prof. Otis Hammond arbitrates if the weighting workshop deadlocks (STKE RACI).

**Impact on Requirements**:

- **Added**: BR-004 (criteria signed before engagement) as a MUST_HAVE
- **Modified**: NFR-SEC-001, NFR-C-002, NFR-I-002 changed from scored criteria to mandatory pass/fail gates
- **Unchanged**: FR-001 to FR-011 remain as written — they describe required capability, not a required product

**Stakeholder Management**:

- **Rhodes**: Her security, integration and provisioning outcomes (BR-008, FR-016, INT-001, INT-004) are delivered under every option and are proceeding now, independent of the platform decision
- **Moog**: He co-signs the criteria and owns the capability evidence; RIFF chairing for this decision passes to Hammond so his stated position is not a governance problem (STKE RACI)

**Future Consideration**: Whichever platform is not selected is reassessed at the boundary review in the RIFF register, not before.

---

### Conflict C-2: Licence saving vs appliance estate reality

**Conflicting Requirements**:

- **Requirement A**: BR-003 (whole-of-life cost flat or reduced)
- **Requirement B**: NFR-SEC-004 and BR-008 (appliances in the managed patching regime, shared accounts removed) with TC-4 (operate within the existing estate)

**Stakeholders Involved**:

- **Vernon Ostinato (CFO)**: Wants A — a licence saving he can attest to, without a hidden capital programme
- **Marcus Fairlight (AV)**: Wants B — the estate is behind on patching and carries shared administrative accounts regardless of which platform wins [PC-C1]

**Nature of Conflict**: A licence-only comparison makes the appliance constraint invisible until it is too late to fund. But the appliance work is partly *independent* of this decision — some of it is required regardless — so charging all of it to this project would equally distort the comparison.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Option 1**: Compare on licence cost only | ✅ Simple, fast | ❌ Capex surprise at business case<br>❌ Fails REQ-035 in substance | Ostinato exposed later |
| **Option 2**: Charge all appliance cost to this project | ✅ Complete visibility | ❌ Distorts the comparison<br>❌ May kill an otherwise sound option | Fairlight funded, decision skewed |
| **Option 3**: Whole-of-life with refresh split into required-regardless and decision-caused | ✅ Honest comparison<br>✅ Estate cost surfaced and owned | ❌ Requires the inventory before the decision (D-3) | Both satisfied if D-3 lands |

**Resolution Strategy**: INNOVATE (change what is measured rather than who wins)

**Decision**: Option 3, with the appliance inventory (D-3) scheduled to complete before evaluation rather than after.

**Rationale**: The disagreement is about accounting boundaries, not about facts. Splitting the refresh cost gives Ostinato the true marginal cost of each option and gives Fairlight a funded, visible estate programme.

**Decision Authority**: Vernon Ostinato accountable for the cost model; Cassandra Rhodes accountable for the appliance assessment (STKE RACI).

**Impact on Requirements**:

- **Modified**: BR-003 success criteria now require the two-way split explicitly
- **Added**: D-3 elevated to a hard milestone preceding evaluation

**Stakeholder Management**:

- **Ostinato**: Sees the capital consequence at options stage rather than at business case
- **Fairlight**: The estate programme is named and costed rather than absorbed into his team's summer

**Future Consideration**: If the inventory shows the estate requires refresh under every option, that is a finding to surface immediately, not a project failure.

---

### Conflict C-3: Universal publication vs academic discretion

**Conflicting Requirements**:

- **Requirement A**: FR-002 and NFR-U-002 (recordings published consistently across all schools) with FR-013 (student notification)
- **Requirement B**: FR-012 (unit-level capture policy permitting exceptions)

**Stakeholders Involved**:

- **Jazmin Field (Student Guild)**: Wants A — equal access regardless of who teaches a unit; publication inconsistency is the sharpest edge of the student experience concern [STKE-C7]
- **A minority of academic staff**, represented in the analysis via Dr. Wynton Castle: Want B — discretion over recording on attendance and performance-observation grounds, and clarity about who can view recordings of their teaching

**Nature of Conflict**: A platform default settles this question by configuration if the institution does not settle it by policy. Neither pure position is tenable: universal mandatory publication ignores legitimate pedagogical cases (small-group seminars, sensitive clinical discussion), while unrestricted discretion reproduces exactly the inconsistency Principle 3 exists to prevent.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Option 1**: Universal mandatory publication | ✅ Maximum consistency and access | ❌ Ignores legitimate exceptions<br>❌ Guaranteed academic resistance | Field satisfied, academics opposed |
| **Option 2**: Full academic discretion | ✅ No resistance | ❌ Reproduces current inconsistency<br>❌ Fails Principle 3 | Academics satisfied, students disadvantaged |
| **Option 3**: Publish by default, exceptions approved and recorded | ✅ Consistency is the default<br>✅ Legitimate cases have a route | ❌ Requires a policy and an approval process | Both partly satisfied |

**Resolution Strategy**: COMPROMISE

**Decision**: Option 3. The institutional default is automatic capture and publication (FR-002). Unit-level exceptions exist (FR-012) but require a recorded approval reference — the platform rejects an exception configured without one. Student notification (FR-013) applies in all cases.

**Rationale**: This is a policy question that must not be settled by default through a technical configuration. Principle 3 sets the default; exceptions become approved, documented and visible rather than exercised silently. The capture policy goes to Education Committee separately from the platform decision (D-4) so that it is decided on its own merits.

**Decision Authority**: Education Committee, accountable; Dr. Benny Moog responsible for drafting the policy; Field, Frame, Castle and the Deans consulted (STKE RACI).

**Impact on Requirements**:

- **Modified**: FR-012 now requires an approval reference as a validation rule, not merely a configuration field
- **Added**: FR-013 (student notification) as MUST_HAVE, applying regardless of the exception state
- **Added**: D-4 (capture policy approval) as a dependency of cutover

**Stakeholder Management**:

- **Field (partial win)**: Gains a default and a measurable consistency standard, not a guarantee of universality
- **Academic minority (partial win)**: Retains a legitimate route, loses the ability to exercise it silently

**Future Consideration**: Exception volume reported to Education Committee annually — a high or rising rate indicates the policy is not working.

---

### Conflict C-4: Retention and disposal vs keeping everything

**Conflicting Requirements**:

- **Requirement A**: FR-014 and DR-005 (retention schedule with defensible disposal), NFR-C-001 (Privacy Act compliance)
- **Requirement B**: Academic expectation that recordings remain available indefinitely, expressed through BR-007's link-preservation criteria and the archive-on-request path

**Stakeholders Involved**:

- **Eleanor Frame (Privacy & Records)**: Wants A — recordings are personal information with no retention rule currently applied [PC-C3]
- **Academic staff and Deans**: Want B — teaching material represents years of work and is reused across offerings

**Nature of Conflict**: Indefinite retention of personal information is not defensible under the APPs, but bulk disposal destroys genuinely reusable teaching material. Migration forces the question because everything migrated becomes permanent by default.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Option 1**: Migrate everything, decide retention later | ✅ No academic disruption | ❌ "Later" never arrives<br>❌ Larger migration, higher cost | Frame's position lost permanently |
| **Option 2**: Apply schedule strictly at migration | ✅ Clean compliance position<br>✅ Smallest migration | ❌ Destroys reusable material<br>❌ Strong academic reaction | Frame satisfied, academics alienated |
| **Option 3**: Schedule with pre-disposal notification and archive-on-request | ✅ Compliance with a real answer for academics<br>✅ Disposal is the default, retention is a decision | ❌ Requires notification workflow and academic action | Both largely satisfied |

**Resolution Strategy**: PHASE

**Decision**: Option 3. The retention schedule is approved before migration planning completes (D-5). Recordings approaching end of retention trigger a 30-day notification with an archive-on-request path (FR-014). Disposal is the default at end of retention; retention beyond schedule requires an active decision and a new retention date.

**Rationale**: Migration is the only operationally natural disposal point, and the archive-on-request path converts a refusal into a choice. Making disposal the default rather than the exception is what makes the schedule real.

**Decision Authority**: Education Committee accountable for the schedule, on Eleanor Frame's advice (STKE RACI).

**Impact on Requirements**:

- **Modified**: FR-014 requires pre-disposal notification and an archive path, not just a disposal job
- **Modified**: DR-005 retention scope now explicitly covers derived analytics identifiers, closing the gap identified in the privacy context [PC-C3]
- **Added**: D-5 as a blocking dependency on migration planning

**Stakeholder Management**:

- **Frame (win)**: A schedule that actually disposes, applied at the point of maximum leverage
- **Academics (partial)**: Archive-on-request preserves what is genuinely reusable; the default changes

**Future Consideration**: Archive-tier volume reviewed annually — if most content is archived on request, the schedule's retention period was set wrong.

---

### Conflict C-5: Procurement speed vs contestability

**Conflicting Requirements**:

- **Requirement A**: BC-1 (decision by 9 October 2026) and BR-006's transition window — both favour the fastest route, which is varying the existing agreement
- **Requirement B**: BR-004 (published unchanged criteria) and BC-5 (RIFF duplication rule) — both favour testing the market

**Stakeholders Involved**:

- **Cassandra Rhodes (CIO)**: The existing-agreement route is faster and cheaper to execute
- **Grace Tanaka (Procurement)**: Needs a value-for-money record and a process that survives challenge, particularly given publicly stated executive positions [S-C1]

**Nature of Conflict**: The timeline is genuinely tight — the October gate is driven by the business case cycle and the July 2027 cutover window, neither of which is arbitrary. But speed achieved by skipping the market test is exactly what makes the outcome challengeable, and the RIFF duplication rule requires justification either way [SGP-C2].

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Option 1**: Vary the existing agreement | ✅ Fastest<br>✅ Lowest process cost | ❌ No value-for-money record<br>❌ Challengeable given stated positions | Rhodes satisfied, Tanaka exposed |
| **Option 2**: Full competitive process | ✅ Maximum defensibility | ❌ Timeline risk against the October gate | Tanaka satisfied, BC-1 at risk |
| **Option 3**: Route decided explicitly at RIFF with its own options analysis and written justification | ✅ Either route becomes defensible<br>✅ Decision is recorded, not defaulted | ❌ Adds a governance step before evaluation | Both satisfied procedurally |

**Resolution Strategy**: PRIORITIZE (contestability over speed)

**Decision**: **Option 2 — full competitive process.** The requirement is tested against the market rather than met by varying the existing agreement. The written value-for-money rationale required by the RIFF duplication rule [SGP-C2] is recorded in the decision file, and the single-point-of-contact probity control applies throughout.

**Rationale**: Given that positions were stated publicly before any evaluation existed, a route that skips the market test would leave the outcome open to challenge from the party that loses — which is the specific failure this project cannot afford. Testing the market costs schedule but buys defensibility, and the timeline in Section 13 absorbs it. The decision is taken now rather than deferred to a governance step mid-procurement, so that scope, criteria and route are settled together before any supplier is approached.

**Decision Authority**: Grace Tanaka responsible, Prof. Otis Hammond accountable (STKE RACI).

**Impact on Requirements**:

- **Added**: BC-4 (vendor contact via Procurement) as a business constraint on requirements validation
- **Modified**: BR-004 success criteria include the contact log

**Stakeholder Management**:

- **Rhodes (partial)**: The fast route remains available, but must be justified rather than assumed
- **Tanaka (win)**: A defensible record either way

**Future Consideration**: Route rationale is retained in the decision file for audit.

---

### Conflict C-6: Discipline capability vs institutional prioritisation

**Conflicting Requirements**:

- **Requirement A**: BR-003 (cost flat or reduced) and the register's MoSCoW prioritisation, under which REQ-010 is **Could** [RR-C3]
- **Requirement B**: BR-005 and FR-009 (multi-camera, high-fidelity performance capture for named venues)

**Stakeholders Involved**:

- **Prof. Desmond Key (Dean, Music & Performing Arts)**: The capability is existential to his school and nationally recognised; he expects it to be endorsed and then defunded [STKE-C10]
- **Vernon Ostinato (CFO)** and the prioritisation process itself: A requirement affecting one school will always score below one affecting all schools

**Nature of Conflict**: This is a defect in how prioritisation interacts with disciplinary need, not a disagreement about facts. MoSCoW priority measures institutional breadth; it cannot express "critical to one school, irrelevant to the rest". Left unaddressed, REQ-010 loses every prioritisation exercise it enters, permanently.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Option 1**: Apply the Could priority literally | ✅ Consistent with the register | ❌ Capability lost<br>❌ Confirms the pattern Key expects | Cost contained, school damaged |
| **Option 2**: Elevate REQ-010 to Must | ✅ Protects the capability | ❌ Overrides an Education Committee prioritisation<br>❌ Sets a precedent for any school | Key satisfied, process undermined |
| **Option 3**: Retain the Could priority, decide the exception explicitly and concurrently under Principle 4 | ✅ Prioritisation integrity preserved<br>✅ Decision is explicit either way | ❌ Exception may still be refused | Honest; outcome not guaranteed |

**Resolution Strategy**: PHASE (decide concurrently, fund explicitly)

**Decision**: Option 3. FR-009 retains COULD_HAVE, faithful to the register. BR-005 requires the exception to be scoped, costed and decided **in the same governance paper as the core recommendation**, so that approval means approving the cost and refusal means recording the REQ-010 consequence explicitly.

**Rationale**: Elevating the priority unilaterally would override a prioritisation the Education Committee owns. Concurrent decision with a costed line achieves the same protection through the correct route: the exception cannot be quietly dropped, because dropping it requires an explicit refusal on the record.

**Decision Authority**: Education Committee accountable for the exception; Prof. Desmond Key responsible for the scope and standard (STKE RACI).

**Impact on Requirements**:

- **Unchanged**: FR-009 priority remains COULD_HAVE, with the tension documented rather than resolved by relabelling
- **Modified**: BR-005 success criteria require concurrent decision and an explicit refusal path
- **Added**: R-6 tracks the defunding risk

**Stakeholder Management**:

- **Key (procedural win, substantive uncertainty)**: He gets an explicit decision on the record; he does not get a guarantee of funding. This is stated to him plainly rather than softened.
- **Ostinato**: The exception is costed and visible rather than arriving later as a variation

**Future Consideration**: If the exception is refused, the REQ-010 gap is recorded in the risk register as a governed choice and revisited at the next capability review.

---

## Timeline and Milestones

### High-Level Milestones

| Milestone | Description | Target Date | Dependencies |
|-----------|-------------|-------------|--------------|
| Baselines sourced | Contract, licensing and appliance data available | 2026-08-21 | D-1, D-2, D-3 |
| Requirements approved | This document signed off by steering | 2026-08-26 | This document |
| Evaluation criteria signed | Weightings and mandatory gates agreed by Rhodes, Moog, Tanaka | 2026-08-28 | BR-004, D-8 |
| Evaluation complete | Options scored against signed criteria | 2026-09-09 | Criteria, vendor engagement |
| RIFF review | Recommendation reviewed, dissent recorded | 2026-09-11 | Evaluation |
| Education Committee | Academic approval of the solution request | 2026-09-25 | RIFF endorsement |
| Operations Committee | Financial and strategic approval | 2026-10-09 | Business case, EC approval |
| Contract executed | Terms including residency, export, breach notification | 2026-12-11 | Approval, PIA complete |
| Build and configure | Integrations, provisioning, room configuration | 2027-02-26 | Contract, D-7 |
| Pilot — Semester 1 2027 | Live pilot with volunteer cohort | 2027-03-01 to 2027-06-25 | Build complete |
| Retention schedule approved | Applied before migration | 2027-04-30 | D-5 |
| Archive migration | Staged migration in the inter-semester break | 2027-07-24 | Pilot outcomes, FR-015, INT-007 |
| Cutover — Semester 2 2027 | Full production cutover before teaching begins | 2027-07-24 | Migration reconciled, training complete |
| Incumbent decommissioned | Source platform closed after reconciliation sign-off | 2027-12-11 | Cutover stable, reconciliation signed |
| Essential Eight ML2 evidenced | Appliance patching and account remediation complete | 2027-12-11 | BR-008 |

---

## Budget

### Cost Estimate

All figures are pending the baseline data in D-1, D-2 and D-3. Cost categories are fixed here so that every option is costed on the same basis; values are deliberately not estimated in advance of sourced data, because an invented baseline would propagate into the business case.

| Category | Estimated Cost | Notes |
|----------|----------------|-------|
| Platform licensing (5 years) | ⚠️ To be sourced — Grace Tanaka / Cassandra Rhodes, 2026-08-14 | Must include the entitlement position for capability already licensed |
| Appliance refresh — required regardless | ⚠️ To be sourced — Marcus Fairlight, 2026-08-21 | Attributable to estate age and patching, not to this decision |
| Appliance refresh — decision-caused | ⚠️ To be sourced — Marcus Fairlight, 2026-08-21 | Attributable to platform compatibility |
| Integration build | ⚠️ To be estimated after platform selection | INT-001 to INT-006 |
| Archive migration | ⚠️ To be estimated — depends on archive volume (Eleanor Frame, 2026-08-28) | Includes reconciliation and link remediation |
| Discipline exception (performance capture) | ⚠️ To be scoped and costed — Prof. Desmond Key, before options analysis | Named venues and capability standard (BR-005) |
| Training and transition support | ⚠️ To be estimated — Nina Kalimba | Includes documentation and pilot support |
| **Total** | **Pending D-1, D-2, D-3** | Required at options stage, not preferred-option stage |

### Ongoing Operational Costs

| Category | Annual Cost | Notes |
|----------|-------------|-------|
| Platform licensing | ⚠️ To be sourced — D-1, D-2 | Compared against current combined run-rate |
| Storage and processing | ⚠️ To be modelled — depends on NFR-S-001 projections | Rises with coverage, falls with retention applied |
| Support and captioning correction | ⚠️ To be estimated — Nina Kalimba, D-6 | FR-007 workload |
| Appliance maintenance and patching | ⚠️ To be sourced — Marcus Fairlight, D-3 | Ongoing regime per NFR-SEC-004 |
| **Total** | **Pending baselines** | Feeds the BR-003 five-year position |

---

## Approval

### Requirements Review

| Reviewer | Role | Status | Date | Comments |
|----------|------|--------|------|----------|
| Prof. Otis Hammond | Business Sponsor | [ ] Approved | Scheduled 2026-08-14 | Pending |
| Dr. Benny Moog | Product Owner / Requirements Owner | [ ] Approved | Scheduled 2026-08-07 | Pending |
| Sam Okafor | Integration Architect | [ ] Approved | Scheduled 2026-08-07 | Pending |
| Tobias Ohm | Security | [ ] Approved | Scheduled 2026-08-12 | Pending |
| Eleanor Frame | Privacy & Records | [ ] Approved | Scheduled 2026-08-12 | Pending |
| Grace Tanaka | Procurement | [ ] Approved | Scheduled 2026-08-14 | Pending — criteria derivation |
| A/Prof. Pearl Clavinet | Academic Approval | [ ] Approved | Scheduled 2026-08-19 | Pending |

### Sign-Off

By signing below, stakeholders confirm that requirements are complete, understood, and approved to proceed to evaluation and design.

| Stakeholder | Signature | Date |
|-------------|-----------|------|
| Prof. Otis Hammond, DVC (Education) | _________ | Pending |
| Cassandra Rhodes, CIO | _________ | Pending |
| Dr. Benny Moog, Director Learning Technologies | _________ | Pending |
| Grace Tanaka, Procurement & Vendor Manager | _________ | Pending |

---

## Appendices

### Appendix A: Glossary

| Term | Definition |
|------|------------|
| **APP** | Australian Privacy Principle — the 13 principles of the Privacy Act 1988; APP 8 governs cross-border disclosure |
| **Capture-equipped room** | A teaching space with installed capture appliance capability |
| **Essential Eight (E8)** | ASD mitigation strategies with maturity levels ML0 to ML3; the university targets ML2 by end 2027 |
| **Learning Capture** | Category 4 of the capability taxonomy — systems enabling capture of course delivery for streaming or later consumption [CT-C1] |
| **Learning Delivery** | Category 3 of the capability taxonomy — systems enabling delivery of course resources to students |
| **LTI** | Learning Tools Interoperability — the standard for integrating tools with an LMS |
| **MoSCoW** | Must / Should / Could / Won't prioritisation, assigned to register requirements by the project team with Education Committee [RR-C10] |
| **NDB** | Notifiable Data Breach scheme under the Privacy Act 1988 |
| **RIFF Review** | Review of Innovation, Fit & Function — the university's solution governance gate [SGP-C1] |
| **Unit** | A single subject of study; the LMS unit site is the student entry point |
| **WCAG 2.2 AA** | Web Content Accessibility Guidelines conformance level required by REQ-029 |

### Appendix B: Reference Documents

- `projects/000-global/ARC-000-PRIN-v1.0.md` — Enterprise Architecture Principles (1, 2, 3, 4, 5, 7, 9, 10, 11, 12, 14, 15, 16, 17, 19 referenced)
- `projects/002-lecture-capture/ARC-002-STKE-v1.0.md` — Stakeholder Drivers & Goals Analysis (goals G-1 to G-10, outcomes O-1 to O-6, RACI)
- `projects/001-lt-ecosystem/ARC-001-REQ-v1.0.md` — Ecosystem-wide requirements for the parent engagement
- `projects/001-lt-ecosystem/ARC-001-DATA-v1.0.md` — Data model including the canonical entity definitions applied here
- `projects/001-lt-ecosystem/ARC-001-RISK-v1.0.md` — Parent engagement risk register
- `projects/000-global/policies/solution-governance-process.md` — RIFF Review process
- `projects/002-lecture-capture/external/` — Engagement inputs (brief, register, landscape, privacy context, stakeholders)

### Appendix C: Wireframes and Mockups

Not applicable. This is a platform procurement, not a bespoke build; the user experience is a property of the platforms evaluated. Evaluation includes hands-on assessment of the academic and student journeys described in UC-1 to UC-6 against the personas in Section 4.

### Appendix D: Data Models

Entity definitions are in Section 9. The canonical model for student, course and enrolment (REQ-027) is defined in `ARC-001-DATA-v1.0.md` and consumed here rather than redefined — this project holds an identity *projection* (Entity 3), not a master record.

---

## External References

> This section provides traceability from generated content back to source documents.

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| S | stakeholders.md | Engagement input | `002-lecture-capture/external/` | Stakeholder register with influence, interest and engagement notes |
| CB | consultant-brief.md | Engagement brief | `002-lecture-capture/external/` | Consultant Engagement Brief — WP1–WP9, scope, due date |
| RR | requirements-register.md | Requirements input | `002-lecture-capture/external/` | Consolidated academic survey requirements (REQ-001 to REQ-035) |
| PC | privacy-context.md | Compliance input | `002-lecture-capture/external/` | Personal information inventory, data flows, Essential Eight self-assessment |
| SL | system-landscape.md | Foundation artifact | `002-lecture-capture/external/` | System categorisation map, usage status, known integrations |
| SGP | solution-governance-process.md | Foundation artifact | `000-global/policies/` | RIFF Review governance and approval process |
| CT | capability-taxonomy.md | Foundation artifact | `000-global/external/` | Eight-category L&T capability taxonomy |
| PRIN | ARC-000-PRIN-v1.0.md | ArcKit artifact | `000-global/` | Enterprise Architecture Principles |
| STKE | ARC-002-STKE-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Stakeholder Drivers & Goals Analysis for this project |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| S-C1 | S | Engagement notes | Risk Factor | "Known tension: Rhodes (CIO) favours Microsoft-platform consolidation (Teams/Stream); Moog and Key defend best-of-breed pedagogy tools (Echo360, discipline software)." |
| CB-C1 | CB | §2, WP6 | Design Decision | "Examples: Echo360 vs Microsoft Stream; Teams scope and provisioning model; integration pattern standards" |
| CB-C2 | CB | §2, WP9 | Business Requirement | "Synthesises all findings into prioritised recommendations and a sequenced delivery roadmap, structured to feed directly into the September business case." |
| RR-C1 | RR | Header | Business Requirement | "Consolidated requirements from the 2026 academic survey (412 responses across all schools)." |
| RR-C2 | RR | Non-functional | Business Requirement | "REQ-035 — Total ecosystem licence spend shall reduce or hold flat while closing Must-priority capability gaps" |
| RR-C3 | RR | Functional | Functional Requirement | "REQ-010 — Performance and ensemble sessions shall be capturable with multi-camera and high-fidelity audio options ... Could" |
| RR-C4 | RR | Non-functional | Non-Functional Requirement | "REQ-032 — Core teaching platforms (LMS, capture, video conferencing) shall meet 99.9% availability during teaching periods" |
| RR-C5 | RR | Non-functional | Security Requirement | "REQ-033 — The ecosystem shall demonstrate alignment to the ASD Essential Eight maturity targets set by Digital & IT" |
| RR-C6 | RR | Non-functional | Security Requirement | "REQ-031 — Authentication to all L&T platforms shall use university single sign-on with MFA; no local accounts" |
| RR-C7 | RR | Non-functional | Compliance Constraint | "REQ-030 — All platforms holding personal information shall comply with the Privacy Act 1988 (APPs), with data residency in Australia preferred and APP 8 assessed for any offshore disclosure" |
| RR-C8 | RR | Non-functional | Compliance Constraint | "REQ-029 — All student-facing tools shall conform to WCAG 2.2 AA accessibility" |
| RR-C9 | RR | Non-functional | Procurement Constraint | "REQ-034 — Vendor contracts shall permit export of all university data in open formats on termination ... Should" |
| RR-C10 | RR | Header | Procurement Constraint | "MoSCoW priorities were assigned by the project team with the Education Committee." |
| PC-C1 | PC | §3 | Security Requirement | "Restrict administrative privileges / ML1 / ML2 / Legacy shared admin accounts in AV/capture estate"; "Patch operating systems / ML1 / ML2 / Lecture-theatre capture appliances behind" |
| PC-C2 | PC | §1, class 4 | Data Requirement | "Video/audio recordings capturing students / PI (biometric-adjacent) / Echo360, Zoom, MS Teams / AU / US" |
| PC-C3 | PC | §2 | Data Requirement | "Analytics export / Derived engagement data / Ad-hoc extracts / No defined retention or minimisation rules" |
| PC-C4 | PC | §3 | Security Requirement | "Target set by Digital & IT: ML2 across the SaaS-heavy L&T estate by end 2027." |
| PC-C5 | PC | §3 | Security Requirement | "Multi-factor authentication ... exception: two tools still allow local accounts (breaches REQ-031)" |
| PC-C6 | PC | §1, APP 8 note | Compliance Constraint | "APP 8 triggers: classes 3, 4 (partial), 6 and 7 involve offshore disclosure under the assumed hosting — the PIA must assess cross-border disclosure accountability, contract clauses and the practicability of AU-region alternatives." |
| PC-C7 | PC | §4 | Compliance Constraint | "Assess eligible-data-breach criteria, the 30-day investigation clock, and the notification workflow across UoF, the placement providers and affected students." |
| PC-C8 | PC | §1, class 8 | Data Requirement | "Engagement & learning analytics / PI (derived) / Blackboard, Echo360, institutional data platform / AU" |
| SL-C1 | SL | Categorisation map | Design Decision | "Learning Capture / Echo360 ✅ · MS Teams ✅¹ · Zoom ✅ / —" |
| SL-C2 | SL | Notes, item 1 | Design Decision | "MS Teams — investigation planned for 2027 to establish a seamless platform experience across collaboration, learning delivery and lecture capture (overlaps with Zoom and Echo360 — key rationalisation candidate)." |
| SL-C4 | SL | Known integrations, #2 | Integration Requirement | "Echo360 user provisioning / LTI + manual CSV / Manual workaround for casual academic staff" |
| SGP-C1 | SGP | Header | Compliance Constraint | "The central gate is the RIFF Review — Review of Innovation, Fit & Function — which assesses solution requests for architectural fit, capability duplication, integration impact and total cost before any procurement or build proceeds." |
| SGP-C2 | SGP | Rules | Procurement Constraint | "Solutions duplicating capability already licensed (per the system landscape map) must justify why the incumbent tool is unsuitable." |
| SGP-C3 | SGP | Rules | Procurement Constraint | "A request may be paused or closed without progressing further, with the agreement of key consulting stakeholders, if it is deemed not to be required." |
| CT-C1 | CT | Taxonomy table | Design Decision | "Learning Capture — Systems and tools that enable the capture of course delivery (lectures, performances, labs) for streaming or future consumption." |
| PRIN-C1 | PRIN | Principle 2 | Design Decision | "Each capability category MUST have a designated primary platform. Where more than one platform provides the same capability, the architecture MUST state which is primary and why the others persist, with a defined boundary or a retirement path." |
| PRIN-C2 | PRIN | Principle 4 | Design Decision | "Discipline-specific tooling MAY sit outside the core platform set where a genuine specialist need exists, but it MUST integrate through the same standard interfaces, identity model, and data contracts as core platforms. Specialist need justifies a different tool — never a different architecture." |
| PRIN-C3 | PRIN | Principle 15 | Non-Functional Requirement | "Core teaching platforms MUST meet defined availability targets during teaching periods, with change and maintenance scheduled around the academic calendar rather than the operational one." |
| PRIN-C4 | PRIN | Principle 9 | Procurement Constraint | "Every platform holding university or student data MUST permit export of that data in open, documented formats, at any time and on termination, without dependence on vendor goodwill or additional fee." |
| PRIN-C5 | PRIN | Principle 14 | Compliance Constraint | "All student-facing platforms and materials MUST meet WCAG 2.2 Level AA. Accessibility is assessed during evaluation and before release — never remediated after deployment." |
| STKE-C1 | STKE | Goal G-2 | Procurement Constraint | "Issue an evaluation framework with weightings totalling 100% and mandatory pass/fail gates, agreed by all three signatories before any vendor engagement, and apply it without amendment through to recommendation." |
| STKE-C2 | STKE | Key Findings | Risk Factor | "Whichever platform wins, the project is bound by two things almost nobody is currently arguing about: the retained recordings archive ... and the lecture-theatre capture appliance estate" |
| STKE-C3 | STKE | SD-3 | Business Requirement | "A platform change that requires appliance replacement converts an opex saving into a capex request, and he will not learn that at business case stage without consequence." |
| STKE-C4 | STKE | Goal G-8 | Non-Functional Requirement | "Every operational stakeholder's worst case is the same event — a cutover that fails in week three of semester" |
| STKE-C5 | STKE | Goal G-6 | Data Requirement | "Migration is also the only natural point at which a retention schedule can be applied — after cutover, everything migrated becomes permanent by default" |
| STKE-C6 | STKE | SD-13 | Stakeholder Need | "placement rosters and clinical shifts make live attendance genuinely impossible for parts of the cohort" |
| STKE-C7 | STKE | SD-14 | Stakeholder Need | "Every student gets the same access to recorded teaching, captioned to a usable standard" |
| STKE-C8 | STKE | SD-14 | Non-Functional Requirement | "a platform that captions clinical or musical terminology poorly delivers a materially worse service to the students who most need captions" |
| STKE-C9 | STKE | SD-6 | Design Decision | "a general-purpose meeting-recording tool and a purpose-built lecture capture platform are not the same product class, and he expects the difference to be dismissed in a cost comparison" |
| STKE-C10 | STKE | SD-9 | Risk Factor | "MoSCoW priority reflects institutional breadth, not disciplinary criticality: a requirement affecting one school will always score below one affecting all schools" |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| README.md | `002-lecture-capture/external/` | ArcKit scaffold guidance for the external documents directory; contains no project content |
| ARC-001-REQ-v1.0.md | `001-lt-ecosystem/` | Ecosystem-wide requirements listed as a reference document; this project derives from the source register directly rather than from the parent artifact, to avoid second-hand traceability |

---

**Generated by**: ArcKit `/arckit:requirements` command
**Generated on**: 2026-07-27
**ArcKit Version**: 6.7.2
**Project**: Lecture Capture Platform Consolidation (Project 002)
**Model**: Claude Opus 5 (1M context)
**Generation Context**: Derived from ARC-002-STKE-v1.0 (goals, outcomes, conflicts, RACI), ARC-000-PRIN-v1.0 (principles), the survey requirements register, system landscape, privacy context and RIFF governance process.

<!-- arckit-provenance:start -->

## Build Provenance

_Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix._

| Field | Value |
|-------|-------|
| Requested Effort | `max` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-07-28T04:26:40.644Z |

<!-- arckit-provenance:end -->
