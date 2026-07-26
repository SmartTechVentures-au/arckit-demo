# Project Requirements: Learning & Teaching Baseline Strategy

> **Template Origin**: Official | **ArcKit Version**: 6.4.0 | **Command**: `arckit.requirements`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-REQ-v1.0 |
| **Document Type** | Business and Technical Requirements |
| **Project** | Learning & Teaching Baseline Strategy (Project 001) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-26 |
| **Last Modified** | 2026-07-26 |
| **Review Date** | 2026-08-25 |
| **Owner** | Dr. Felix Marimba, Academic Lead (Digital Learning) — custodian of the survey requirements register |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Project Team, Steering Committee, Digital & IT, Education Committee |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-26 | ArcKit AI | Initial creation from `/arckit:requirements` command | [PENDING] | [PENDING] |

---

## Document Purpose

This document converts the consolidated academic survey requirements into typed, testable architecture requirements suitable for capability mapping (WP3), requirements mapping (WP7), future-state design (WP8), and vendor engagement.

**On requirement identifiers.** The source register uses a single flat sequence, `REQ-001` to `REQ-035` [RQ-C1]. This document assigns ArcKit typed identifiers (`BR-`, `FR-`, `NFR-*-`, `INT-`, `DR-`) because type-prefixed IDs are required for traceability, test mapping, and vendor response structuring. **Every requirement derived from the register carries a `Source Ref` naming its originating `REQ-xxx` ID**, and Appendix E holds a complete bidirectional cross-reference.

This preserves the chain back to the 412 survey respondents [RQ-C2] — an explicit need of the Academic Lead, whose credibility with colleagues and future consultation response rates depend on survey input visibly shaping the outcome (driver SD-8 in `ARC-001-STKE-v1.0`).

Requirements marked `Source Ref: Derived` do **not** originate in the survey. They are derived from the architecture principles, the privacy and security context, or the current-state integration assessment, and are labelled so that the survey's actual scope is never overstated.

---

## Executive Summary

### Business Context

The University of Funk's Learning & Teaching technology ecosystem has grown organically over roughly a decade to 20-plus tools spanning eight capability categories [RQ-C3]. The result is overlapping capability, fragile point-to-point integration, licensed functionality that was never configured, and an inconsistent student experience across schools.

An academic survey of 412 respondents has produced 35 consolidated requirements [RQ-C2]. This engagement applies those requirements architecturally rather than gathering them [RQ-C4]. The output feeds a rationalisation roadmap due 31 August 2026 and a September business case.

### Objectives

- Establish a deliberately bounded ecosystem where every capability category has a designated primary platform
- Replace fragile batch and manual integration with governed, near-real-time data flows
- Reach demonstrable privacy and security posture across a SaaS-heavy estate
- Deliver a consistent, accessible student experience regardless of school
- Hold or reduce licence spend while closing Must-priority capability gaps

### Expected Outcomes

Requirements in this document support the six outcomes defined in `ARC-001-STKE-v1.0`:

| Outcome | Summary | Primary requirements |
|---------|---------|----------------------|
| O-1 | Rationalised, deliberately bounded ecosystem | BR-001, BR-007 |
| O-2 | Reliable, governed integration | BR-004, INT-001 to INT-009 |
| O-3 | Licence spend contained while gaps close | BR-002 |
| O-4 | Demonstrable privacy and security posture | BR-005, NFR-SEC-*, NFR-C-* |
| O-5 | Consistent, accessible student experience | BR-006, NFR-U-001, NFR-U-002 |
| O-6 | Governance that prevents recurrence | BR-007 |

### Project Scope

**In Scope**:

- Architecture requirements for all eight L&T capability categories [RQ-C3]
- The seven known integrations, current and target state [RQ-C5]
- Canonical data model definition for student, course, enrolment and institutional role
- Privacy, security, accessibility and availability requirements across the L&T estate
- Requirements-to-capability mapping inputs for WP7

**Out of Scope**:

- **Delivery of the integrations themselves.** The architecture governing them is in scope; building them is not [RQ-C6].
- Administration of the academic survey or maintenance of the source register [RQ-C4]
- Non-L&T institutional systems except where they are an integration counterparty (student information system, timetabling)
- Procurement execution and contract negotiation
- Teaching-lab desktop fleet and lecture-theatre appliance estate, except where security maturity depends on them

---

## Stakeholders

| Stakeholder | Role | Organization | Involvement Level |
|-------------|------|--------------|-------------------|
| Prof. Otis Hammond | Deputy Vice-Chancellor (Education) | University Executive | Executive Sponsor — decision maker |
| A/Prof. Pearl Clavinet | Dean of L&T; Chair, Education Committee | Academic governance | Academic approval authority |
| Cassandra Rhodes | Chief Information Officer | Digital & IT | Technical decision maker; funds delivery |
| Vernon Ostinato | Chief Financial Officer | Finance | Business case scrutiny |
| Dr. Benny Moog | Director, Learning Technologies | Learning Technologies | Product owner; RIFF facilitation |
| Dr. Felix Marimba | Academic Lead, Digital Learning | Academic | Requirements custodian |
| Sam Okafor | Integration Architect | Digital & IT | Technical oversight; owns delivery |
| Rhonda Bell | Project Manager | Project team | Coordination |
| Tobias Ohm | Cybersecurity Lead | Digital & IT | Security review |
| Eleanor Frame | Privacy & Records Officer | Governance | Regulatory compliance; PIA sign-off |
| Grace Tanaka | Procurement & Vendor Manager | Procurement | Contract and licensing input |
| Prof. Desmond Key | Dean, Music & Performing Arts | Academic | Discipline requirements |
| Prof. Priya Anand | Dean, Health Sciences | Academic | Discipline requirements |
| Dr. Wynton Castle | Senior Lecturer | Academic | User acceptance — teaching staff |
| Jazmin Field | President, Student Guild | Students | User acceptance — students |

---

## Business Requirements

### BR-001: Deliberately bounded capability ecosystem

**Description**: Every capability category must have a designated primary platform, with any remaining overlap recorded as a declared, justified decision carrying either a defined boundary or a retirement path.

**Rationale**: Undeclared duplication is the root cause of the ecosystem's cost and complexity — the same function is licensed several times and staff receive inconsistent guidance [RQ-C7]. Duplication is not inherently wrong; undeclared duplication is.

**Success Criteria**:

- All 8 capability categories have a designated primary platform
- Every overlap classified as primary-with-boundary, transitional-with-retirement-date, or approved exception
- No platform retained solely because no decision was taken

**Priority**: MUST_HAVE

**Source Ref**: Derived (architecture principle 2; consultant brief WP9)

**Stakeholder**: Dr. Benny Moog (owner); Cassandra Rhodes, Vernon Ostinato (beneficiaries)

**Traces To**: Goal G-2, G-4 · Outcome O-1

---

### BR-002: Licence spend held flat or reduced while Must-priority gaps close

**Description**: Total ecosystem licence spend must reduce or hold flat across the roadmap horizon while Must-priority capability gaps identified by the survey are addressed.

**Rationale**: The university currently pays for functionality never configured or switched on, and for capability licensed more than once [RQ-C7]. This is the financial test the September business case must pass.

**Success Criteria**:

- Baseline total ecosystem licence spend established during WP3
- Modelled spend at roadmap end is flat or lower against that baseline
- Every Must-priority capability gap either addressed or explicitly deferred with rationale
- Savings tied to actual renewal dates and verified exit provisions, not notional

**Priority**: SHOULD_HAVE

**Source Ref**: REQ-035

**Stakeholder**: Vernon Ostinato (owner); Grace Tanaka (contract data)

**Traces To**: Goal G-7 · Outcome O-3

---

### BR-003: Baseline strategy and roadmap delivered to business case timing

**Description**: Prioritised recommendations and a sequenced roadmap must be delivered by 31 August 2026, structured to feed the September business case directly.

**Rationale**: The due date is fixed and the business case depends on it [RQ-C8]. A deliverable in the wrong format requires rework at the point of maximum time pressure.

**Success Criteria**:

- Roadmap delivered by 31 August 2026 and accepted by the Executive Sponsor
- Recommendations cover rationalisation, cost optimisation, capability gaps, integration uplift and risk
- Quick wins distinguished from strategic investments, with dependencies and phasing shown
- Every recommendation traceable to evidence from WP2 to WP7

**Priority**: MUST_HAVE

**Source Ref**: Derived (consultant brief WP9, due date)

**Stakeholder**: Prof. Otis Hammond (owner); Rhonda Bell (delivery)

**Traces To**: Goal G-6

---

### BR-004: Integration fragility and manual handling eliminated

**Description**: The integration estate must move from batch transfer and manual handling to governed, interface-mediated flows with no manual step in any production flow carrying personal information.

**Rationale**: Four of seven known integrations involve manual handling or flat-file transfer, producing role assignment failures, hierarchy drift, single-person dependencies and audit concerns [RQ-C5]. The same weaknesses are simultaneously privacy findings [RQ-C9].

**Success Criteria**:

- Zero manual steps in production flows carrying personal information
- Target architecture defined for all seven known integrations with current-to-target gaps identified
- No single-person dependency for any production process
- Integration failures detected by monitoring rather than user report

**Priority**: MUST_HAVE

**Source Ref**: REQ-023, REQ-025, REQ-026, REQ-028 (consolidated business-level statement)

**Stakeholder**: Cassandra Rhodes (owner); Sam Okafor (delivery)

**Traces To**: Goal G-3 · Outcome O-2

---

### BR-005: Demonstrable privacy and security posture

**Description**: The estate must hold an assessed privacy position for every personal information class, a documented pathway to the target security maturity, and no unremediated authentication exception.

**Rationale**: Four data classes involve offshore disclosure triggering APP 8 [RQ-C10], sensitive placement information moves by manual re-keying with exports circulating by email [RQ-C9], and two platforms permit local accounts in breach of the authentication requirement [RQ-C11].

**Success Criteria**:

- All 8 personal information classes formally assessed
- Cross-border disclosure position recorded and accepted for each offshore class
- Documented maturity pathway for all eight mitigation strategies
- Zero local accounts in production; existing exceptions carry dated remediation plans

**Priority**: MUST_HAVE

**Source Ref**: REQ-030, REQ-031, REQ-033

**Stakeholder**: Eleanor Frame (privacy); Tobias Ohm (security); Cassandra Rhodes (accountable)

**Traces To**: Goal G-8, G-9 · Outcome O-4

---

### BR-006: Consistent and accessible student experience

**Description**: Students must reach all unit materials, activities and grades through a single entry point, encountering consistent structure and verified accessibility regardless of the school delivering the unit.

**Rationale**: Students routinely study across schools. Structural inconsistency imposes a cumulative cognitive cost invisible to any single teaching team [RQ-C12]. Accessibility conformance carries legal and ethical weight [RQ-C13].

**Success Criteria**:

- All student-facing capability reachable from the primary entry point
- Baseline template available and default for new unit sites
- All student-facing platforms assessed for WCAG 2.2 AA with gaps owned
- Student representatives consulted on the navigation model

**Priority**: MUST_HAVE

**Source Ref**: REQ-001, REQ-007, REQ-029

**Stakeholder**: A/Prof. Pearl Clavinet (owner); Jazmin Field (beneficiary)

**Traces To**: Goal G-1, G-10 · Outcome O-5

---

### BR-007: Governance operating on architectural evidence

**Description**: The RIFF review must assess new and changed learning technology against a maintained capability map, the architecture principles, and integration, privacy and accessibility impact — before procurement or build commences.

**Rationale**: RIFF exists to prevent capability being acquired on functional merit while its integration, privacy and cost consequences go unexamined [RQ-C14]. Without a maintained evidence base it operates on opinion, and the duplication pattern recurs.

**Success Criteria**:

- 100% of solution requests assessed against the capability map and principles before commitment
- Duplication, integration, privacy, accessibility and whole-of-life cost recorded per request
- Decisions recorded with options and rationale, forming an auditable register
- Capability map current as at the most recent contract review

**Priority**: MUST_HAVE

**Source Ref**: Derived (RIFF governance process; architecture principles 18, 19)

**Stakeholder**: Dr. Benny Moog (owner); A/Prof. Pearl Clavinet (accountable)

**Traces To**: Goal G-4 · Outcome O-6

---

### BR-008: Survey requirements traceable to outcomes

**Description**: Every requirement in the source register must be mapped to a capability status — met, partially met, duplicated, or unmet — with the mapping visible in the final recommendations.

**Rationale**: This is what converts 412 survey responses into architectural decisions [RQ-C2]. Consultation fatigue is real: a survey that visibly changes nothing depresses future response rates and damages the credibility of the Academic Lead who owned it.

**Success Criteria**:

- 100% of the 35 source requirements mapped to a capability status
- Must-priority requirements with no current capability explicitly identified
- Requirements satisfied by more than one platform identified as duplication candidates
- Traceability from source `REQ-xxx` to recommendation visible in the WP9 deliverable

**Priority**: MUST_HAVE

**Source Ref**: Derived (stakeholder driver SD-8; consultant brief WP7)

**Stakeholder**: Dr. Felix Marimba (owner)

**Traces To**: Goal G-5

---

## Functional Requirements

### User Personas

#### Persona 1: Unit Coordinator

- **Role**: Academic responsible for design and delivery of one or more units
- **Goals**: Build a unit site quickly, reuse last year's structure, see which students are struggling, mark efficiently
- **Pain Points**: Rebuilding sites each teaching period; inconsistent tooling between units; no single view of cohort engagement; waiting for enrolment data to appear
- **Technical Proficiency**: Medium

#### Persona 2: Student

- **Role**: Enrolled student, frequently studying across multiple schools
- **Goals**: Find materials, submit work, see grades and feedback, collaborate with a group
- **Pain Points**: Different navigation in every unit; multiple logins; materials scattered across platforms; grades appearing late or not at all
- **Technical Proficiency**: Medium — but highly variable, and assistive technology users are disproportionately affected by inconsistency

#### Persona 3: Sessional / Casual Academic

- **Role**: Short-tenure teaching staff, often marking or tutoring
- **Goals**: Get access to the right units promptly, mark, provide feedback
- **Pain Points**: Manual account provisioning; access arriving late in the teaching period or persisting after it ends
- **Technical Proficiency**: Medium

#### Persona 4: Placement Supervisor (external)

- **Role**: Clinical or community-sector supervisor assessing students on placement
- **Goals**: Record assessment outcomes once, without university system training
- **Pain Points**: Outcomes re-keyed by university staff, introducing error and delay
- **Technical Proficiency**: Low

#### Persona 5: Learning Technologist

- **Role**: Central support for the L&T platform estate
- **Goals**: Support staff, configure platforms, run rollover, resolve integration failures
- **Pain Points**: Undocumented automation; discovering integration failures via user reports; manual CSV handling
- **Technical Proficiency**: High

---

### Use Cases

#### UC-1: Enrol and access a unit

**Actor**: Student

**Preconditions**:

- Student record exists in the student information system
- Student has an active enrolment in the unit
- Unit site exists and is published

**Main Flow**:

1. Student enrols in a unit through the student information system
2. System propagates the enrolment change to the learning platform
3. System grants the student the enrolled-student role for that unit
4. Student authenticates through institutional single sign-on with MFA
5. Student reaches the unit site from the single entry point
6. Student accesses materials, activities, submissions and grades from that entry point

**Postconditions**:

- Student holds access appropriate to their enrolment
- Access is attributable and logged

**Alternative Flows**:

- **Alt 2a**: If the student withdraws, the system revokes access within the defined deprovisioning window
- **Alt 5a**: If a capability is delivered by a supporting platform, the student launches it from the entry point with identity, unit and role context preserved

**Exception Flows**:

- **Ex 1**: Propagation failure is detected by monitoring, alerted to a named owner, and the affected record is recoverable — not silently discarded

**Business Rules**:

- Enrolment is authoritative in the student information system; the learning platform holds a derived copy
- No student is asked to re-authenticate when moving between platforms

**Priority**: CRITICAL

---

#### UC-2: Record a placement assessment outcome

**Actor**: Placement Supervisor (external)

**Preconditions**:

- Student has an active placement allocation
- Supervisor is authorised against that placement

**Main Flow**:

1. Supervisor records the assessment outcome in the placement management platform
2. System validates the outcome against the assessment schema
3. System synchronises the outcome to the LMS gradebook
4. System propagates the resulting grade to the student record
5. Unit coordinator sees the outcome without manual entry

**Postconditions**:

- Outcome recorded once and visible in the gradebook and student record
- Full audit trail of who recorded what and when

**Alternative Flows**:

- **Alt 3a**: If synchronisation fails, the record is queued and retried, and the failure is alerted

**Exception Flows**:

- **Ex 1**: Conflicting edits in placement platform and gradebook are resolved by the documented conflict rule, never silently overwritten

**Business Rules**:

- Placement records carry sensitive information and are handled under elevated controls
- No outcome is transferred by manual re-keying, screenshot, email or spreadsheet export

**Priority**: CRITICAL

---

#### UC-3: Roll a unit over to a new teaching period

**Actor**: Unit Coordinator, supported by Learning Technologist

**Preconditions**:

- Prior teaching period unit site exists
- New teaching period unit shell has been created from the student information system

**Main Flow**:

1. Coordinator requests rollover through a self-service interface
2. System copies structure, content and configuration to the new unit site
3. System excludes prior-period student data, submissions and grades
4. System logs the operation with actor, timestamp and scope
5. Coordinator reviews and adjusts the new site

**Postconditions**:

- New unit site conforms to the baseline template
- No prior-period student personal information carried forward

**Alternative Flows**:

- **Alt 2a**: If the source site predates the baseline template, the system reports which elements require manual adjustment

**Exception Flows**:

- **Ex 1**: Partial failure leaves the target site in a defined state with a documented recovery path

**Business Rules**:

- Rollover is executable by more than one person and is not dependent on undocumented scripts
- Student personal information is never carried into a new teaching period

**Priority**: HIGH

---

### Functional Requirements Detail

> Requirements are grouped by the eight capability categories of the institutional taxonomy [RQ-C3]. Each carries its originating `REQ-xxx` identifier.

#### Course Design

##### FR-001: Course template authoring and reuse

**Description**: Staff shall author and reuse course templates so that unit sites present a consistent structure and navigation to students across all schools.

**Source Ref**: REQ-001 · **Capability**: Course Design · **Relates To**: BR-006, UC-3

**Acceptance Criteria**:

- [ ] Given a baseline template exists, when a new unit site is created, then it is instantiated from that template by default
- [ ] Given a coordinator needs pedagogical variation, when they request it, then the variation is permitted and recorded against a documented justification
- [ ] Given a unit site is created, when a student navigates it, then top-level structure and terminology match every other unit site
- [ ] Edge case: a unit site predating the template reports which elements diverge

**Priority**: MUST_HAVE · **Complexity**: MEDIUM

**Rationale**: Structural inconsistency between units imposes a recurring cognitive cost on students studying across schools.

**Stakeholder**: Jazmin Field, Dr. Wynton Castle, A/Prof. Pearl Clavinet

---

##### FR-002: Interactive content authoring without specialist skills

**Description**: Staff shall build interactive learning content — quizzes, branching scenarios, embedded activities — without specialist development skills.

**Source Ref**: REQ-002 · **Capability**: Course Design · **Relates To**: BR-001

**Acceptance Criteria**:

- [ ] Given a coordinator with no development background, when they author an interactive activity, then they complete it without writing code
- [ ] Given interactive content is authored, when a student accesses it, then it meets WCAG 2.2 AA
- [ ] Given content is authored, when the unit rolls over, then the content transfers intact

**Priority**: SHOULD_HAVE · **Complexity**: MEDIUM

**Rationale**: Authoring capability currently spans several licensed platforms with unclear boundaries — a duplication candidate.

**Stakeholder**: Dr. Wynton Castle, Dr. Benny Moog

---

#### Learning Resources

##### FR-003: Centrally managed reading lists with copyright compliance

**Description**: Reading lists shall be managed centrally and linked to units, with copyright compliance handled automatically.

**Source Ref**: REQ-003 · **Capability**: Learning Resources · **Relates To**: BR-006

**Acceptance Criteria**:

- [ ] Given a reading list is linked to a unit, when the unit rolls over, then the list is carried forward and flagged for review
- [ ] Given an item is added, when copyright limits apply, then the system enforces or flags them without manual checking
- [ ] Given a student opens the list, when they select an item, then access is granted without a separate login

**Priority**: MUST_HAVE · **Complexity**: MEDIUM

**Rationale**: Copyright exposure is an institutional risk that manual processes do not reliably contain.

**Stakeholder**: Dr. Benny Moog, A/Prof. Pearl Clavinet

---

##### FR-004: Single supported video toolchain

**Description**: Staff shall record, edit and caption instructional video with a single supported toolchain.

**Source Ref**: REQ-004 · **Capability**: Learning Resources · **Relates To**: BR-001, BR-006

**Acceptance Criteria**:

- [ ] Given a staff member needs to produce instructional video, when they follow the supported path, then recording, editing and captioning are available without switching toolchain
- [ ] Given video is published, when a student accesses it, then captions are present and meet WCAG 2.2 AA
- [ ] Given the toolchain is designated, when an alternative tool is requested, then it is assessed at RIFF as a duplication candidate

**Priority**: MUST_HAVE · **Complexity**: MEDIUM

**Rationale**: Video production capability currently spans multiple licensed platforms — a named rationalisation candidate.

**Stakeholder**: Dr. Benny Moog, Cassandra Rhodes

---

##### FR-005: Music notation and audio-production materials

**Description**: Music & Performing Arts staff shall distribute interactive notation and audio-production project files as learning materials.

**Source Ref**: REQ-005 · **Capability**: Learning Resources (discipline-specific) · **Relates To**: BR-001

**Acceptance Criteria**:

- [ ] Given a lecturer distributes a notation or audio-production file, when a student opens it, then it renders or opens in the supported discipline toolchain
- [ ] Given discipline tooling is used, when a student authenticates, then institutional single sign-on applies
- [ ] Given the tool sits outside the core platform set, when it is reviewed, then it has a named support model and owner

**Priority**: SHOULD_HAVE · **Complexity**: MEDIUM

**Rationale**: Specialist need justifies a different tool, never a different architecture. Licensing and support models for these tools are currently unclear [RQ-C15].

**Stakeholder**: Prof. Desmond Key

---

##### FR-006: Clinical simulation with device integration

**Description**: Health Sciences staff shall deliver clinical simulation scenarios with device integration in simulation labs.

**Source Ref**: REQ-006 · **Capability**: Learning Resources (discipline-specific) · **Relates To**: BR-001

**Acceptance Criteria**:

- [ ] Given a simulation scenario is configured, when it runs in a lab, then connected devices integrate without manual data transfer
- [ ] Given simulation platforms are in use, when reviewed, then each has a defined internal support model
- [ ] Given student participation is recorded, when it is stored, then personal information handling meets the classification requirements

**Priority**: MUST_HAVE · **Complexity**: HIGH

**Rationale**: Simulation is core to Health Sciences teaching and cannot be met by general-purpose platforms. Support model clarity is an open question [RQ-C15].

**Stakeholder**: Prof. Priya Anand

---

#### Learning Delivery

##### FR-007: Single entry point for students

**Description**: Students shall access all unit materials, activities and grades through a single entry point.

**Source Ref**: REQ-007 · **Capability**: Learning Delivery · **Relates To**: BR-006, UC-1

**Acceptance Criteria**:

- [ ] Given a student is enrolled, when they authenticate, then every student-facing capability for their units is reachable from one entry point
- [ ] Given a capability is delivered by a supporting platform, when the student launches it, then identity, unit and role context are preserved
- [ ] Given a grade originates in a supporting platform, when it is finalised, then it is visible at the entry point
- [ ] Edge case: a capability that cannot be surfaced through the entry point requires a recorded exception

**Priority**: MUST_HAVE · **Complexity**: HIGH

**Rationale**: The survey's clearest and most strongly expressed signal. Fragmentation transfers navigational cost onto students.

**Stakeholder**: Jazmin Field, Dr. Felix Marimba

---

##### FR-008: Live online classes on one primary platform

**Description**: Live online classes shall support breakout rooms, polling and recording, using one primary platform.

**Source Ref**: REQ-008 · **Capability**: Learning Delivery · **Relates To**: BR-001

**Acceptance Criteria**:

- [ ] Given a live class is scheduled, when it runs, then breakout rooms, polling and recording are available in the designated primary platform
- [ ] Given a recording is made, when the class ends, then it is published to the relevant unit site
- [ ] Given an alternative platform is requested, when assessed at RIFF, then the request justifies why the primary platform is unsuitable

**Priority**: MUST_HAVE · **Complexity**: MEDIUM

**Rationale**: The register itself specifies "one primary platform", making this a consolidation requirement. Three platforms currently provide overlapping delivery and capture capability [RQ-C16]. See Conflict C-1.

**Stakeholder**: Dr. Benny Moog, Cassandra Rhodes

---

#### Learning Capture

##### FR-009: Automatic lecture capture and publication

**Description**: All timetabled lectures shall be captured automatically and published to the relevant unit site within 4 hours.

**Source Ref**: REQ-009 · **Capability**: Learning Capture · **Relates To**: BR-006, NFR-P-002

**Acceptance Criteria**:

- [ ] Given a lecture is timetabled, when it occurs, then capture starts automatically without staff intervention
- [ ] Given a capture completes, when 4 hours have elapsed, then the recording is published to the correct unit site
- [ ] Given capture or publication fails, when the failure occurs, then it is alerted to a named owner rather than discovered by student report
- [ ] Given a recording is published, when a student accesses it, then captions are available

**Priority**: MUST_HAVE · **Complexity**: HIGH

**Rationale**: Automatic capture is a Must-priority expectation. Capture appliance provisioning currently requires manual CSV handling for casual staff [RQ-C5].

**Stakeholder**: Jazmin Field, Dr. Benny Moog

---

##### FR-010: Multi-camera and high-fidelity performance capture

**Description**: Performance and ensemble sessions shall be capturable with multi-camera and high-fidelity audio options.

**Source Ref**: REQ-010 · **Capability**: Learning Capture (discipline-specific) · **Relates To**: BR-001

**Acceptance Criteria**:

- [ ] Given a performance session is scheduled, when captured, then multi-camera and high-fidelity audio options are available
- [ ] Given a performance recording is produced, when published, then it is reachable from the unit site
- [ ] Given this capability influences the capture platform decision, when that decision is taken, then this requirement is explicitly assessed

**Priority**: COULD_HAVE · **Complexity**: HIGH

**Rationale**: Could-priority in the register, but materially affects the lecture capture platform decision — a general-purpose platform may not meet it. Flagged so it is not silently dropped. See Conflict C-1.

**Stakeholder**: Prof. Desmond Key

---

#### Active Learning

##### FR-011: Peer review with anonymised marking

**Description**: Students shall engage in peer review of written and creative work with anonymised marking options.

**Source Ref**: REQ-013 · **Capability**: Active Learning · **Relates To**: BR-001

**Acceptance Criteria**:

- [ ] Given peer review is configured, when students participate, then anonymity is enforced where selected
- [ ] Given peer review outcomes exist, when marking completes, then results are visible in the gradebook
- [ ] Given more than one platform offers peer review, when assessed, then a primary is designated

**Priority**: SHOULD_HAVE · **Complexity**: MEDIUM

**Rationale**: Peer review capability appears in more than one licensed platform — a duplication candidate.

**Stakeholder**: Dr. Wynton Castle

---

##### FR-012: In-class polling and formative checks

**Description**: Staff shall run in-class polling and formative checks with results visible in the unit analytics view.

**Source Ref**: REQ-014 · **Capability**: Active Learning · **Relates To**: FR-019

**Acceptance Criteria**:

- [ ] Given a poll is run in class, when it completes, then results are available to the coordinator immediately
- [ ] Given poll results exist, when the coordinator opens the unit analytics view, then the results are visible there
- [ ] Given polling exists in multiple platforms, when assessed, then a primary is designated

**Priority**: SHOULD_HAVE · **Complexity**: MEDIUM

**Rationale**: Polling capability is currently spread across delivery and active-learning platforms.

**Stakeholder**: Dr. Wynton Castle

---

#### Collaboration

##### FR-013: Group collaboration linked to enrolment groups

**Description**: Students shall collaborate on shared documents, boards and group spaces linked to their unit enrolment groups.

**Source Ref**: REQ-011 · **Capability**: Collaboration · **Relates To**: BR-006, FR-014

**Acceptance Criteria**:

- [ ] Given a student belongs to an enrolment group, when they open collaboration tooling, then their group space exists and is populated
- [ ] Given group membership changes, when the change occurs, then the collaboration space reflects it without manual intervention
- [ ] Given collaboration content is created, when the teaching period ends, then retention rules apply

**Priority**: MUST_HAVE · **Complexity**: MEDIUM

**Rationale**: Collaboration capability overlaps across three or more platforms — a named rationalisation candidate [RQ-C16].

**Stakeholder**: Jazmin Field, Dr. Benny Moog

---

##### FR-014: Automatic group provisioning from timetable allocation

**Description**: Group membership in collaboration tools shall be provisioned automatically from timetable allocation data.

**Source Ref**: REQ-012 · **Capability**: Collaboration · **Relates To**: INT-006, BR-004

**Acceptance Criteria**:

- [ ] Given timetable allocation data changes, when the change occurs, then group membership updates without a batch cycle
- [ ] Given a student changes tutorial group, when the change is made, then their collaboration group access follows within the defined propagation window
- [ ] Edge case: allocation conflicts are surfaced rather than silently resolved

**Priority**: MUST_HAVE · **Complexity**: HIGH

**Rationale**: Current batch export means timetable changes are not reflected until the next run [RQ-C5].

**Stakeholder**: Sam Okafor, Dr. Benny Moog

---

#### Assessment & Progress Tracking

##### FR-015: Whole-of-program portfolio with export on graduation

**Description**: Students shall maintain a portfolio of evidence across their whole program, exportable on graduation.

**Source Ref**: REQ-015 · **Capability**: Assessment & Progress Tracking · **Relates To**: DR-008, NFR-I-002

**Acceptance Criteria**:

- [ ] Given a student progresses across units, when they add evidence, then it persists across teaching periods and programs
- [ ] Given a student graduates, when they request export, then they receive their portfolio in an open, documented format
- [ ] Given a student has left the university, when they request export, then the capability remains available for the defined period

**Priority**: MUST_HAVE · **Complexity**: MEDIUM

**Rationale**: Student-owned artifacts must remain portable beyond enrolment — an exit-rights requirement as much as a functional one.

**Stakeholder**: Jazmin Field, Prof. Priya Anand

---

##### FR-016: Similarity and AI-writing detection

**Description**: All text-based submissions shall pass through similarity and AI-writing detection before marking.

**Source Ref**: REQ-016 · **Capability**: Assessment & Progress Tracking · **Relates To**: NFR-C-002

**Acceptance Criteria**:

- [ ] Given a text-based submission is made, when it is received, then it passes through detection before it is available for marking
- [ ] Given detection produces a result, when the marker opens the submission, then the result is visible alongside it
- [ ] Given submissions are processed, when they are stored, then student intellectual property and hosting region requirements are met

**Priority**: MUST_HAVE · **Complexity**: MEDIUM

**Rationale**: A governance-sourced requirement supporting academic integrity. Submitted work is held offshore under the assessed hosting, triggering APP 8 [RQ-C10].

**Stakeholder**: A/Prof. Pearl Clavinet, Eleanor Frame

---

##### FR-017: Secure examination on-campus and remote

**Description**: High-stakes exams shall be deliverable in a secure, lockdown environment both on-campus and remotely.

**Source Ref**: REQ-017 · **Capability**: Assessment & Progress Tracking · **Relates To**: NFR-A-001, NFR-C-001

**Acceptance Criteria**:

- [ ] Given a high-stakes exam is scheduled, when it runs on-campus, then the lockdown environment is enforced
- [ ] Given the same exam runs remotely, when a student sits it, then equivalent integrity controls apply
- [ ] Given an exam is in progress, when the platform is under peak load, then availability targets are met
- [ ] Given proctoring artifacts are captured, when stored, then their classification and hosting position are recorded

**Priority**: MUST_HAVE · **Complexity**: HIGH

**Rationale**: Examination failure has immediate and severe academic consequence. Exam responses and proctoring artifacts are held offshore [RQ-C10].

**Stakeholder**: Prof. Priya Anand, Eleanor Frame

---

##### FR-018: Single-entry placement assessment

**Description**: Placement supervisors shall enter assessment outcomes once, flowing automatically to the student record.

**Source Ref**: REQ-018 · **Capability**: Assessment & Progress Tracking · **Relates To**: INT-005, UC-2, DR-004

**Acceptance Criteria**:

- [ ] Given a supervisor records an outcome, when they submit it, then it reaches the LMS gradebook without manual re-keying
- [ ] Given an outcome reaches the gradebook, when finalised, then it propagates to the student record
- [ ] Given placement data carries sensitive information, when it moves between systems, then it does so under elevated controls and never by email or spreadsheet export
- [ ] Edge case: synchronisation failure queues the record and alerts a named owner

**Priority**: MUST_HAVE · **Complexity**: HIGH

**Rationale**: The current flow runs on manual re-keying and is documented as error-prone with audit concerns [RQ-C5]. It carries the estate's only sensitive information [RQ-C17]. This is simultaneously an academic integrity, privacy and student-fairness defect — the clearest single remediation candidate in the estate.

**Stakeholder**: Prof. Priya Anand, Eleanor Frame, Sam Okafor

---

##### FR-019: Micro-credentials and badging

**Description**: Micro-credentials and badges shall be issuable against defined skill frameworks.

**Source Ref**: REQ-019 · **Capability**: Assessment & Progress Tracking · **Relates To**: BR-001

**Acceptance Criteria**:

- [ ] Given a skill framework is defined, when a student meets its criteria, then a credential can be issued against it
- [ ] Given a credential is issued, when the student wishes to share it, then it is portable in an open format
- [ ] Given no badging platform is currently in use, when one is selected, then it is assessed at RIFF against the capability map

**Priority**: COULD_HAVE · **Complexity**: MEDIUM

**Rationale**: No badging capability currently in the estate; options investigation is outstanding [RQ-C15]. A new-acquisition candidate requiring BR-007 assessment.

**Stakeholder**: Dr. Benny Moog

---

#### Evaluation & Analytics

##### FR-020: Cohort engagement and at-risk dashboard

**Description**: Unit coordinators shall view engagement, progress and at-risk indicators for their cohort in one dashboard.

**Source Ref**: REQ-020 · **Capability**: Evaluation & Analytics · **Relates To**: DR-006, FR-012

**Acceptance Criteria**:

- [ ] Given a coordinator opens the dashboard, when it loads, then engagement, progress and at-risk indicators for their cohort are present
- [ ] Given data originates in more than one platform, when displayed, then it is reconciled to a single cohort view
- [ ] Given the dashboard shows derived personal information, when accessed, then least-privilege access controls apply

**Priority**: SHOULD_HAVE · **Complexity**: HIGH

**Rationale**: Analytics capability is currently spread across four platforms with no consolidated cohort view.

**Stakeholder**: Dr. Wynton Castle, Dr. Benny Moog

---

##### FR-021: Single platform for teaching evaluation

**Description**: Student evaluation of teaching shall be administered, analysed and reported through one platform.

**Source Ref**: REQ-021 · **Capability**: Evaluation & Analytics · **Relates To**: BR-001

**Acceptance Criteria**:

- [ ] Given an evaluation round is administered, when it runs, then it uses the designated primary platform
- [ ] Given responses are collected, when reported, then reporting is de-identified
- [ ] Given two platforms currently provide this capability, when assessed, then one is designated primary with a retirement path for the other

**Priority**: MUST_HAVE · **Complexity**: MEDIUM

**Rationale**: A governance-sourced requirement. Two survey and evaluation platforms currently overlap — a clear duplication candidate with offshore hosting implications [RQ-C10].

**Stakeholder**: A/Prof. Pearl Clavinet, Eleanor Frame

---

##### FR-022: Learning analytics export to the institutional data platform

**Description**: Learning analytics data shall be exportable to the institutional data platform for cross-system analysis.

**Source Ref**: REQ-022 · **Capability**: Evaluation & Analytics · **Relates To**: INT-009, DR-006

**Acceptance Criteria**:

- [ ] Given analytics data exists, when export runs, then it reaches the institutional data platform without ad-hoc manual extracts
- [ ] Given data is exported, when it is transferred, then minimisation and de-identification rules are applied
- [ ] Given exported data is retained, when the retention period expires, then deletion occurs automatically

**Priority**: SHOULD_HAVE · **Complexity**: MEDIUM

**Rationale**: Analytics export currently runs on ad-hoc extracts with no defined retention or minimisation rules [RQ-C9].

**Stakeholder**: Cassandra Rhodes, Eleanor Frame

---

## Non-Functional Requirements (NFRs)

### Performance Requirements

#### NFR-P-001: Change propagation latency

**Requirement**: Student, course and enrolment changes shall propagate from the authoritative source to the learning platform within 15 minutes of the change, replacing the nightly batch cycle.

- Propagation latency: within 15 minutes of change (95th percentile)
- Deprovisioning on withdrawal: within the same window

**Source Ref**: REQ-023 · **Relates To**: INT-001, BR-004

**Acceptance Criteria**:

- [ ] Given an enrolment change occurs, when 15 minutes elapse, then the learning platform reflects it
- [ ] Given a withdrawal occurs, when 15 minutes elapse, then access is revoked
- [ ] Given propagation exceeds the target, when it does, then an alert is raised

**Priority**: MUST_HAVE

**Rationale**: Overnight batch means access and role state are wrong for up to a day — students unable to reach materials, and access persisting after entitlement ends [RQ-C9].

---

#### NFR-P-002: Lecture capture publication latency

**Requirement**: Captured lectures shall be published to the relevant unit site within 4 hours of the session ending.

**Source Ref**: REQ-009 · **Relates To**: FR-009

**Acceptance Criteria**:

- [ ] Given a lecture ends, when 4 hours elapse, then the recording is published to the correct unit site
- [ ] Given publication fails, when the deadline passes, then an alert is raised to a named owner

**Priority**: MUST_HAVE

**Rationale**: Students rely on timely capture availability, particularly those unable to attend in person.

---

### Availability and Resilience Requirements

#### NFR-A-001: Availability during teaching periods

**Requirement**: Core teaching platforms — LMS, lecture capture and video conferencing — shall meet 99.9% availability during teaching periods.

- Uptime target: 99.9% during teaching periods (approximately 43 minutes of downtime per month)
- Assessment and examination periods carry elevated protection

**Source Ref**: REQ-032 · **Relates To**: FR-007, FR-009, FR-017

**Acceptance Criteria**:

- [ ] Given a teaching period is active, when availability is measured over a month, then it meets or exceeds 99.9%
- [ ] Given vendor service levels are contracted, when compared to this target, then they meet or exceed it
- [ ] Given a platform depends on another, when aggregate availability is calculated, then the dependency chain is accounted for

**Priority**: MUST_HAVE

**Rationale**: Availability requirements are not uniform across the year — an outage during assessment week and the same outage in the inter-semester break are entirely different events.

---

#### NFR-A-002: Change control aligned to the academic calendar

**Requirement**: Change and maintenance for teaching-critical platforms shall be scheduled around the academic calendar, with defined change freeze windows during assessment and examination periods.

**Source Ref**: Derived (architecture principle 15)

**Acceptance Criteria**:

- [ ] Given assessment periods are defined, when change is planned, then freeze windows are enforced
- [ ] Given a change is required during a freeze, when requested, then it follows an exception path with named approval
- [ ] Given a teaching-critical platform degrades, when it does, then defined degraded-mode behaviour applies

**Priority**: MUST_HAVE

**Rationale**: Not present in the survey register, but a direct consequence of NFR-A-001 being period-differentiated.

---

### Scalability Requirements

#### NFR-S-001: Peak load capacity

**Requirement**: Core teaching platforms shall sustain the concurrency and throughput of institutional peak periods without degradation.

- Peak periods: teaching period commencement, assessment submission deadlines, examination windows
- Integration throughput: capable of processing full-cohort enrolment change volumes within NFR-P-001 latency

**Source Ref**: Derived (architecture principle 1; implied by REQ-023 and REQ-032)

**Acceptance Criteria**:

- [ ] Given a submission deadline, when the platform is under peak concurrent load, then response times remain within target
- [ ] Given a teaching period commences, when enrolment change volume peaks, then propagation still meets NFR-P-001
- [ ] Given capacity is assessed, when load testing is performed, then results are documented against measured peak

**Priority**: SHOULD_HAVE

**Rationale**: The survey did not raise scalability, but assessment-deadline load is the predictable failure mode for this class of platform.

---

### Security Requirements

#### NFR-SEC-001: Authentication via institutional single sign-on with MFA

**Requirement**: Authentication to all L&T platforms shall use university single sign-on with multi-factor authentication. Local accounts are prohibited.

**Source Ref**: REQ-031 · **Relates To**: BR-005, NFR-SEC-003

**Acceptance Criteria**:

- [ ] Given any L&T platform, when a user authenticates, then institutional single sign-on with MFA is enforced
- [ ] Given a platform currently permits local accounts, when assessed, then it carries a dated remediation plan
- [ ] Given a new platform is evaluated, when it cannot support institutional SSO, then it is not adopted
- [ ] Given administrative access is required, when granted, then it is individually attributable with no shared accounts

**Priority**: MUST_HAVE

**Rationale**: Two platforms currently permit local accounts, breaching this requirement directly [RQ-C11]. In a SaaS-heavy estate identity is the primary control surface. See Conflict C-3.

---

#### NFR-SEC-002: Essential Eight maturity alignment

**Requirement**: The L&T estate shall demonstrate alignment to the ASD Essential Eight maturity targets set by Digital & IT — Maturity Level 2 across the estate by end 2027.

**Source Ref**: REQ-033 · **Relates To**: BR-005

**Acceptance Criteria**:

- [ ] Given the eight mitigation strategies, when assessed, then each has a documented pathway from current to target maturity
- [ ] Given a gap exists, when identified, then it carries a named owner and target date
- [ ] Given backup and export coverage is claimed, when verified, then it is confirmed by test rather than vendor description

**Priority**: MUST_HAVE

**Rationale**: Current self-assessment sits largely at ML1 against an ML2 target, with export coverage unverified for four platforms [RQ-C11].

---

#### NFR-SEC-003: Automated identity lifecycle

**Requirement**: Account provisioning, role assignment and deprovisioning shall be automated and driven from the authoritative source. Manual account creation, manual role assignment and bulk user file loads are prohibited in production.

**Source Ref**: REQ-025, REQ-031 (extended by architecture principle 12)

**Acceptance Criteria**:

- [ ] Given a user's role changes, when the change occurs, then access is adjusted automatically
- [ ] Given a student withdraws or a staff contract ends, when it occurs, then deprovisioning happens within the defined window
- [ ] Given casual and sessional staff require access, when provisioned, then they follow the same automated path as continuing staff
- [ ] Given access review is required, when performed, then it is possible across platforms from a single view

**Priority**: MUST_HAVE

**Rationale**: Manual provisioning produces both access failures and access persistence. Casual academic provisioning is the documented source of manual CSV workaround [RQ-C5].

---

### Compliance and Regulatory Requirements

#### NFR-C-001: Privacy Act 1988 compliance

**Requirement**: All platforms holding personal information shall comply with the Privacy Act 1988 and the Australian Privacy Principles, with data residency in Australia preferred.

**Source Ref**: REQ-030 · **Relates To**: BR-005, DR-003, DR-005

**Acceptance Criteria**:

- [ ] Given a platform holds personal information, when assessed, then its APP compliance position is documented
- [ ] Given a new platform is evaluated, when assessed, then privacy review occurs before selection, not before release
- [ ] Given sensitive information is held, when handled, then elevated controls apply
- [ ] Given a data flow changes materially, when it does, then privacy assessment is repeated

**Priority**: MUST_HAVE

**Rationale**: Obligations attach to the design of a system, not to its documentation after the fact.

---

#### NFR-C-002: Cross-border disclosure assessment (APP 8)

**Requirement**: Where a platform discloses personal information offshore, that disclosure shall be assessed, contractually governed, and formally accepted before adoption or renewal.

**Source Ref**: REQ-030 · **Relates To**: DR-005, NFR-C-001

**Acceptance Criteria**:

- [ ] Given a platform holds personal information, when recorded, then its hosting region is a captured attribute
- [ ] Given offshore disclosure occurs, when identified, then a cross-border assessment is completed before adoption or renewal
- [ ] Given an offshore platform is retained, when assessed, then the practicability of an Australian-region alternative is documented, including where none exists
- [ ] Given a contract governs offshore disclosure, when reviewed, then accountability and breach notification obligations are present

**Priority**: MUST_HAVE

**Rationale**: Four data classes involve offshore disclosure under the assessed hosting arrangements [RQ-C10]. Accountability remains with the university regardless of where data sits.

---

#### NFR-C-003: Audit logging for academic and access records

**Requirement**: Changes to grades, assessment outcomes, institutional role assignment and access to sensitive information shall be logged with actor, timestamp and prior value, and retained for the period required by institutional records policy.

**Source Ref**: Derived (audit concerns raised in the integration landscape assessment)

**Acceptance Criteria**:

- [ ] Given a grade or assessment outcome changes, when it does, then actor, timestamp and prior value are logged
- [ ] Given institutional role assignment changes, when it does, then the change is attributable
- [ ] Given sensitive information is accessed, when accessed, then the event is logged
- [ ] Given an audit query is raised, when investigated, then the log supports reconstruction of the change sequence

**Priority**: MUST_HAVE

**Rationale**: Not in the survey register, but the placement grade flow is explicitly flagged for audit concerns [RQ-C5], and manual re-keying leaves no attributable trail.

---

### Usability Requirements

#### NFR-U-001: Navigation consistency

**Requirement**: Unit sites shall present consistent structure, navigation and terminology to students regardless of school, faculty or teaching team. Variation shall be justified by pedagogy and recorded.

**Source Ref**: REQ-001, REQ-007 · **Relates To**: FR-001, FR-007, BR-006

**Acceptance Criteria**:

- [ ] Given a student moves between units from different schools, when they navigate, then top-level structure and terminology are consistent
- [ ] Given common concepts are named, when displayed, then terminology is standardised institution-wide
- [ ] Given a teaching team requires variation, when requested, then pedagogical justification is recorded
- [ ] Given template conformance is measured, when reported, then it is measurable across the unit portfolio

**Priority**: MUST_HAVE

**Rationale**: Consistency requirements apply to the student-facing surface only; they do not dictate staff-side authoring workflow. See Conflict C-5.

---

#### NFR-U-002: Accessibility conformance

**Requirement**: All student-facing tools and materials shall conform to WCAG 2.2 Level AA.

**Source Ref**: REQ-029 · **Relates To**: BR-006

**Acceptance Criteria**:

- [ ] Given a student-facing platform, when assessed, then WCAG 2.2 AA conformance evidence is obtained and independently verified
- [ ] Given a vendor conformance claim is made, when received, then it is verified rather than accepted at face value
- [ ] Given recorded or live content is published, when accessed, then captioning is available
- [ ] Given a conformance gap exists, when identified, then it carries an owner and a remediation date
- [ ] Given a platform is being evaluated, when scored, then accessibility is a weighted criterion

**Priority**: MUST_HAVE

**Rationale**: A Must-priority requirement carrying legal and ethical weight. Retrofitting is materially more expensive than designing correctly, and a platform selected without assessment commits the university for the contract term.

---

### Maintainability and Supportability Requirements

#### NFR-M-001: Integration observability

**Requirement**: Integrations and teaching-critical services shall emit sufficient telemetry to detect failure, diagnose cause and confirm recovery without requiring a user to report the problem first.

**Source Ref**: Derived (architecture principle 17)

**Acceptance Criteria**:

- [ ] Given an integration runs, when it completes, then success, failure and volume are reported
- [ ] Given a failure occurs, when detected, then an alert reaches a named owner with an actionable runbook
- [ ] Given a record fails to propagate, when it does, then it is visible and recoverable rather than silently discarded
- [ ] Given a flow spans multiple systems, when monitored, then monitoring covers it end-to-end, not only endpoint availability

**Priority**: MUST_HAVE

**Rationale**: Several current integration failures are discovered by users — a role not assigned, a group that did not appear, a grade that did not arrive [RQ-C5]. Detection by user report means academic consequence has already occurred.

---

#### NFR-M-002: Reproducible and documented automation

**Requirement**: Operational automation shall be documented, version-controlled and executable by more than one person. Automation existing only as undocumented scripts held by an individual is prohibited.

**Source Ref**: REQ-026 (extended by architecture principle 13)

**Acceptance Criteria**:

- [ ] Given production automation exists, when reviewed, then it is held in version control with its configuration
- [ ] Given automation executes, when it runs, then execution is logged and attributable
- [ ] Given a process is production-critical, when assessed, then at least two people can execute and troubleshoot it
- [ ] Given automation modifies teaching-critical state, when it fails, then a defined rollback or recovery path exists

**Priority**: MUST_HAVE

**Rationale**: Course cloning currently runs on semi-manual, undocumented scripts with a single-person dependency [RQ-C5] — an availability risk at the busiest point in the academic calendar.

---

### Portability and Interoperability Requirements

#### NFR-I-001: Published, versioned interfaces

**Requirement**: Systems shall integrate through published, versioned interfaces. Direct database access across system boundaries, shared file locations as an integration mechanism, and manual transfer of data between systems are prohibited.

**Source Ref**: Derived (architecture principle 10)

**Acceptance Criteria**:

- [ ] Given an integration exists, when reviewed, then it uses a published, versioned interface
- [ ] Given systems exchange data, when assessed, then no direct cross-boundary database access occurs
- [ ] Given a target-state integration is designed, when specified, then it does not rely on shared-storage file exchange
- [ ] Given an interface changes, when versioned, then a backward-compatibility and deprecation policy applies
- [ ] Given an integration is in production, when reviewed, then it has a named owner

**Priority**: MUST_HAVE

**Rationale**: The most fragile current integrations are precisely those using flat files on shared storage, manual exports and undocumented scripts [RQ-C5].

---

#### NFR-I-002: Data portability and exit

**Requirement**: Vendor contracts shall permit export of all university data in open, documented formats, at any time and on termination, without additional fee.

**Source Ref**: REQ-034 · **Relates To**: DR-007, DR-008, BR-002

**Acceptance Criteria**:

- [ ] Given a platform holds university or student data, when export is requested, then it is available in an open, documented format
- [ ] Given export capability is claimed, when verified, then it is confirmed by test rather than by contract reading alone
- [ ] Given export is performed, when assessed, then scope covers content, configuration, user-generated work and assessment records
- [ ] Given a contract is negotiated or renewed, when reviewed, then termination-assistance obligations are present

**Priority**: SHOULD_HAVE

**Rationale**: Exit capability is what makes rationalisation executable — a platform that cannot be left cannot be rationalised, and its renewal is not a genuine decision. Export coverage is currently unverified for four platforms [RQ-C11].

---

## Integration Requirements

> Seven integrations exist in the current estate [RQ-C5]. Requirements below define target state. Delivery is out of scope; the architecture governing them is in scope [RQ-C6].

### External System Integrations

#### INT-001: Student information system to learning platform

**Purpose**: Propagate student, course and enrolment data to the learning platform in near-real-time, replacing the nightly batch flat-file transfer.

**Integration Type**: Event-driven

**Data Exchanged**:

- **From student information system to learning platform**: student identity, course, enrolment, on change
- **From learning platform to student information system**: none — the learning platform holds a derived copy

**Integration Pattern**: Publish/subscribe with change events

**Authentication**: Service-to-service, institutional standard

**Error Handling**: Retry with backoff; failed records queued and visible; alert to named owner

**SLA**: Propagation within 15 minutes of change (NFR-P-001); failure alerted within the same window

**Owner**: Sam Okafor, Integration Architect

**Source Ref**: REQ-023 · **Current state**: Nightly batch flat-file — fragile, no intra-day sync [RQ-C5]

**Priority**: CRITICAL

---

#### INT-002: Institutional role assignment

**Purpose**: Derive institutional role — coordinator, tutor, marker — from a single authoritative source and synchronise it to all L&T systems.

**Integration Type**: Event-driven

**Data Exchanged**:

- **From authoritative source to all L&T platforms**: role assignment per user per unit, on change

**Integration Pattern**: Publish/subscribe

**Authentication**: Service-to-service, institutional standard

**Error Handling**: Failed assignments surfaced and recoverable; no silent failure

**SLA**: Within 15 minutes of change

**Owner**: Sam Okafor, Integration Architect

**Source Ref**: REQ-024 · **Current state**: Role assignment failures documented [RQ-C5]

**Priority**: CRITICAL

---

#### INT-003: Automated platform provisioning

**Purpose**: Provision users automatically to lecture capture, portfolio and assessment platforms, eliminating manual CSV loads.

**Integration Type**: Event-driven

**Data Exchanged**:

- **From authoritative source to target platforms**: user identity and role, on change

**Integration Pattern**: Publish/subscribe

**Authentication**: Service-to-service, institutional standard

**Error Handling**: Retry with backoff; failures alerted

**SLA**: Within 15 minutes of change; casual and sessional staff on the same path as continuing staff

**Owner**: Sam Okafor, Integration Architect

**Source Ref**: REQ-025 · **Current state**: LTI plus manual CSV; manual workaround for casual academic staff [RQ-C5]

**Priority**: CRITICAL

---

#### INT-004: Course cloning and rollover

**Purpose**: Automate course cloning and rollover as a self-service, logged process.

**Integration Type**: Event-driven with self-service trigger

**Data Exchanged**:

- **Within the learning platform**: unit structure, content and configuration — explicitly excluding prior-period student data

**Integration Pattern**: Request/response with asynchronous completion

**Authentication**: Institutional single sign-on, coordinator role required

**Error Handling**: Partial failure leaves a defined state with a documented recovery path

**SLA**: Completion within the published rollover window; execution logged and attributable

**Owner**: Sam Okafor, Integration Architect

**Source Ref**: REQ-026 · **Current state**: Semi-manual scripts, undocumented, single-person dependency [RQ-C5]

**Priority**: HIGH

---

#### INT-005: Placement management to LMS gradebook

**Purpose**: Synchronise placement assessment outcomes bidirectionally with the LMS gradebook, eliminating manual re-keying.

**Integration Type**: Event-driven, bidirectional

**Data Exchanged**:

- **From placement platform to LMS**: assessment outcomes and grades, on submission
- **From LMS to placement platform**: enrolment and allocation context

**Integration Pattern**: Publish/subscribe with documented conflict-resolution rule

**Authentication**: Service-to-service, institutional standard

**Error Handling**: Failed records queued, visible and recoverable; alert to named owner. No fallback to manual transfer.

**SLA**: Within 15 minutes of submission

**Owner**: Sam Okafor, Integration Architect

**Source Ref**: REQ-028 · **Current state**: Manual re-keying — error-prone, audit concerns, sensitive information exposure [RQ-C5], [RQ-C17]

**Priority**: CRITICAL

**Note**: Bidirectional synchronisation is permitted here by explicit requirement, and therefore requires a conflict-resolution rule defined in advance — architecture principle 5 otherwise avoids bidirectional flows.

---

#### INT-006: Timetable allocation to collaboration groups

**Purpose**: Provision collaboration group membership automatically from timetable allocation data.

**Integration Type**: Event-driven

**Data Exchanged**:

- **From timetabling system to collaboration platform**: group allocation per student per unit, on change

**Integration Pattern**: Publish/subscribe

**Authentication**: Service-to-service, institutional standard

**Error Handling**: Allocation conflicts surfaced rather than silently resolved

**SLA**: Within 15 minutes of allocation change

**Owner**: Sam Okafor, Integration Architect

**Source Ref**: REQ-012 · **Current state**: Batch export/import — timetable changes not reflected until next run [RQ-C5]

**Priority**: HIGH

---

#### INT-007: Institutional hierarchy synchronisation

**Purpose**: Synchronise institutional hierarchy — faculty, school, department — from the authoritative source to the learning platform.

**Integration Type**: Event-driven

**Data Exchanged**:

- **From authoritative source to learning platform**: hierarchy structure, on change

**Integration Pattern**: Publish/subscribe

**Authentication**: Service-to-service, institutional standard

**Error Handling**: Drift detection with reconciliation reporting

**SLA**: Within one business day of change; drift reported automatically

**Owner**: Sam Okafor, Integration Architect

**Source Ref**: Derived (current-state integration 4) · **Current state**: Manual — drift between systems documented [RQ-C5]

**Priority**: MEDIUM

---

#### INT-008: Sandpit environment provisioning

**Purpose**: Provision non-production sandpit environments for staff experimentation and development.

**Integration Type**: Event-driven with self-service trigger

**Data Exchanged**:

- **From authoritative source to sandpit**: staff identity and role only — no student personal information

**Integration Pattern**: Request/response with asynchronous completion

**Authentication**: Institutional single sign-on

**Error Handling**: Provisioning failure alerted; partial environments cleaned up

**SLA**: To be defined during design

**Owner**: Sam Okafor, Integration Architect

**Source Ref**: Derived (consultant brief WP5) · **Current state**: Planned for 2027, not yet designed [RQ-C5]

**Priority**: LOW

**Note**: Student personal information must not be replicated into non-production environments.

---

#### INT-009: Learning analytics to institutional data platform

**Purpose**: Export learning analytics data to the institutional data platform for cross-system analysis.

**Integration Type**: Scheduled batch — an accepted exception to the event-driven default, as this is bulk analytical transfer rather than change propagation

**Data Exchanged**:

- **From L&T platforms to institutional data platform**: engagement and derived analytics data, minimised and de-identified where purpose permits

**Integration Pattern**: Scheduled extract with defined schema

**Authentication**: Service-to-service, institutional standard

**Error Handling**: Failed extracts alerted; no partial loads

**SLA**: Per agreed reporting cycle

**Owner**: Cassandra Rhodes (institutional data platform); Sam Okafor (extract)

**Source Ref**: REQ-022 · **Current state**: Ad-hoc extracts with no defined retention or minimisation rules [RQ-C9]

**Priority**: MEDIUM

---

## Data Requirements

### Data Entities

#### DR-001: Canonical data model for core academic entities

**Description**: A canonical data model shall be defined for student, course and enrolment entities, governing all integrations. Point-to-point transformations between proprietary formats are prohibited for these entities.

**Attributes** (indicative — full definition is a WP5 deliverable):

| Attribute | Type | Required | Description | Constraints |
|-----------|------|----------|-------------|-------------|
| student_id | String | Yes | Institutional student identifier | Authoritative in student information system |
| course_code | String | Yes | Unit or course identifier | Authoritative in student information system |
| enrolment_status | Enum | Yes | Enrolment state | active, withdrawn, completed, deferred |
| teaching_period | String | Yes | Period identifier | Governs rollover scope |
| institutional_role | Enum | Yes | Role held in the unit | student, coordinator, tutor, marker |

**Data Classification**: CONFIDENTIAL

**Data Retention**: Per institutional records policy; derived copies expire with the retention rule of their holding platform

**Source Ref**: REQ-027 · **Relates To**: INT-001, INT-002, DR-002

**Acceptance Criteria**:

- [ ] Given the canonical model is published, when an integration is built, then it maps to and from the canonical model rather than another system's internal representation
- [ ] Given identifiers are defined, when used across systems, then identity is preserved
- [ ] Given the model changes, when versioned, then a backward-compatible evolution path applies
- [ ] Given the model exists, when reviewed, then it has a named owner accountable for maintenance

**Priority**: MUST_HAVE

**Rationale**: A canonical model converts an N-times-N mapping problem into an N-times-one problem and makes platform substitution tractable — directly enabling the rationalisation objective.

---

#### DR-002: Institutional role as a governed entity

**Description**: Institutional role shall be derived from a single authoritative source and propagated. No platform shall independently maintain role assignment.

**Data Classification**: CONFIDENTIAL

**Data Retention**: Current state only; change history retained per NFR-C-003

**Source Ref**: REQ-024 · **Relates To**: INT-002, NFR-SEC-003

**Acceptance Criteria**:

- [ ] Given a role is assigned, when propagated, then it originates from the single authoritative source
- [ ] Given a platform holds role data, when reviewed, then it is a derived, read-oriented copy
- [ ] Given a role changes, when the change occurs, then all dependent platforms reflect it within the defined window

**Priority**: MUST_HAVE

**Rationale**: Role assignment failures trace directly to the absence of a declared authority for this entity [RQ-C5].

---

#### DR-003: Personal information classification and inventory

**Description**: All personal information held across the L&T estate shall be classified and inventoried, with sensitive information identified explicitly.

**Data Classification**: Varies by class — CONFIDENTIAL to RESTRICTED

**Data Retention**: Defined per class and enforced automatically

**Source Ref**: REQ-030 · **Relates To**: NFR-C-001, DR-004, DR-005

**Acceptance Criteria**:

- [ ] Given personal information is held, when inventoried, then its class, holding systems and sensitivity are recorded
- [ ] Given sensitive information exists, when identified, then it is separately flagged and handled under elevated controls
- [ ] Given a data flow is designed, when assessed, then it carries only the fields necessary for its stated purpose
- [ ] Given a retention period expires, when it does, then deletion occurs automatically rather than by convention

**Priority**: MUST_HAVE

**Rationale**: Eight personal information classes span the estate [RQ-C17]. Classification is the precondition for every other privacy control.

---

#### DR-004: Sensitive information handling — placement records

**Description**: Placement records containing clearance metadata and health-context notes are sensitive information and shall be handled under elevated controls, never transferred by manual re-keying, email, screenshot or spreadsheet export.

**Data Classification**: RESTRICTED

**Data Retention**: Per institutional records policy and placement provider agreements

**Source Ref**: Derived (privacy context §1, §2) · **Relates To**: FR-018, INT-005, UC-2

**Acceptance Criteria**:

- [ ] Given placement records are held, when classified, then they are identified as sensitive information
- [ ] Given placement outcomes move between systems, when transferred, then transfer occurs through the governed integration only
- [ ] Given access is granted, when reviewed, then it follows least privilege and is revoked promptly on role change
- [ ] Given an export is attempted outside the governed path, when detected, then it is prevented or alerted

**Priority**: MUST_HAVE

**Rationale**: This is the estate's only sensitive information class and its current handling — manual re-keying with exports circulating by email [RQ-C9] — is the clearest single defect in the estate. It is simultaneously an academic integrity, privacy and student-fairness problem.

---

#### DR-005: Data residency register

**Description**: Hosting region shall be a recorded attribute of every platform holding personal information, captured at procurement and reviewed at renewal.

**Data Classification**: INTERNAL

**Data Retention**: Maintained as a standing register

**Source Ref**: REQ-030 · **Relates To**: NFR-C-002

**Acceptance Criteria**:

- [ ] Given a platform holds personal information, when recorded, then its hosting region is captured
- [ ] Given hosting is offshore, when identified, then a cross-border assessment is triggered
- [ ] Given a contract is renewed, when reviewed, then residency posture is re-assessed rather than assumed unchanged

**Priority**: MUST_HAVE

**Rationale**: Cross-border disclosure must be a decided position, not an inherited one. Four data classes are affected under the assessed hosting [RQ-C10].

---

#### DR-006: Analytics minimisation and retention

**Description**: Derived engagement and learning analytics data shall be minimised, de-identified where purpose permits, and subject to defined retention rules enforced automatically.

**Data Classification**: CONFIDENTIAL

**Data Retention**: To be defined per analytics purpose; automatic deletion at expiry

**Source Ref**: REQ-022 · **Relates To**: FR-020, FR-022, INT-009

**Acceptance Criteria**:

- [ ] Given analytics data is exported, when transferred, then minimisation rules are applied
- [ ] Given reporting is produced, when purpose permits, then it is de-identified
- [ ] Given retention periods are defined, when they expire, then deletion is automatic
- [ ] Given ad-hoc extracts currently occur, when the target state is reached, then they are eliminated

**Priority**: SHOULD_HAVE

**Rationale**: Analytics export currently runs with no defined retention or minimisation rules [RQ-C9].

---

#### DR-007: Institutional data export on termination

**Description**: All university data held in a platform shall be exportable in open, documented formats on termination, covering content, configuration, user-generated work and assessment records.

**Data Classification**: Varies by content

**Data Retention**: N/A — export capability requirement

**Source Ref**: REQ-034 · **Relates To**: NFR-I-002, BR-002

**Acceptance Criteria**:

- [ ] Given a platform is to be retired, when export is performed, then all university data is retrievable in open formats
- [ ] Given export capability is claimed, when tested, then it is confirmed periodically, not only at exit
- [ ] Given proprietary formats requiring vendor tooling are offered, when assessed, then they do not satisfy this requirement

**Priority**: SHOULD_HAVE

**Rationale**: Rationalisation decisions are only executable where contracts and platforms permit exit.

---

#### DR-008: Student portfolio portability

**Description**: Students shall be able to export their portfolio of evidence in an open, documented format, including after their enrolment ends.

**Data Classification**: CONFIDENTIAL — student-owned

**Data Retention**: Available for a defined period post-graduation

**Source Ref**: REQ-015 · **Relates To**: FR-015, NFR-I-002

**Acceptance Criteria**:

- [ ] Given a student maintains a portfolio, when they request export, then they receive it in an open, documented format
- [ ] Given a student graduates, when the defined period applies, then export remains available
- [ ] Given portfolio content spans multiple teaching periods, when exported, then it is complete

**Priority**: MUST_HAVE

**Rationale**: Student-owned artifacts must remain portable beyond enrolment — the student's own evidence of learning should not be trapped by an institutional platform decision.

---

### Data Quality Requirements

**Data Accuracy**: Enrolment, role and grade data must reconcile between the authoritative source and derived copies with zero unexplained discrepancies. Reconciliation is automated and monitored, not periodic and manual.

**Data Completeness**: Required fields defined per canonical entity (DR-001). Records failing validation are surfaced and recoverable, never silently discarded.

**Data Consistency**: Cross-system reconciliation between the authoritative source and every derived copy, with discrepancies surfaced automatically. Hierarchy drift (INT-007) is a named current failure to be eliminated.

**Data Timeliness**: Change propagation within 15 minutes for identity, enrolment, role and grade (NFR-P-001). Hierarchy within one business day (INT-007).

**Data Lineage**: Source-to-target mapping documented for all flows carrying personal information. Transformation logic version-controlled and reviewable.

---

### Data Migration Requirements

**Migration Scope**: Determined by the rationalisation decisions taken in WP6 and WP8. Where a platform is retired, its content, configuration, user-generated work and assessment records must migrate or be archived.

**Migration Strategy**: Phased, aligned to contract renewal dates and the academic calendar. No migration of a teaching-critical platform during a teaching period.

**Data Transformation**: Through the canonical model (DR-001) where core entities are involved.

**Data Validation**: Record counts, completeness checks against the source, and sample verification by the owning academic area before decommissioning.

**Rollback Plan**: Source platform retained in read-only state until validation completes and the owning area confirms acceptance.

**Migration Timeline**: To be defined in the WP9 roadmap. Migration windows must fall outside teaching and assessment periods (NFR-A-002).

---

## Constraints and Assumptions

### Technical Constraints

**TC-1**: Platforms are predominantly vendor-hosted SaaS. Integration capability is bounded by what each vendor's interfaces support, and target patterns may require negotiation rather than design alone.

**TC-2**: All platforms must support institutional single sign-on with MFA (NFR-SEC-001). A platform that cannot is not adoptable, regardless of functional merit.

**TC-3**: The student information system is the authoritative source for student, course and enrolment. Its interface capability constrains INT-001 and INT-002.

**TC-4**: Teaching-lab desktop fleets and lecture-theatre capture appliances sit partly outside L&T project control but materially affect security maturity (NFR-SEC-002).

**TC-5**: Delivery of the integrations is out of scope for this engagement [RQ-C6]; requirements define target state for subsequent delivery by the internal Integration team.

### Business Constraints

**BC-1**: The 31 August 2026 deliverable date is fixed and drives the September business case [RQ-C8].

**BC-2**: Total ecosystem licence spend must hold flat or reduce (BR-002), constraining how capability gaps may be closed.

**BC-3**: Rationalisation is only executable at contract renewal points or where exit provisions permit — timing is commercially, not architecturally, determined.

**BC-4**: New or changed learning technology must pass RIFF review before procurement or build [RQ-C14].

**BC-5**: Academic approval through the Education Committee is required for principles and future state; this sets the governance calendar.

### Assumptions

**A-1**: The consolidated survey requirements are complete and authoritative. The engagement does not re-open requirements gathering [RQ-C4].

**A-2**: Foundation artifacts — taxonomy, system map, governance process — are accurate at commencement and require validation rather than reproduction [RQ-C18].

**A-3**: The Integration team is available to support WP4 and WP5 throughout [RQ-C18].

**A-4**: The project team facilitates vendor access for capability and roadmap data [RQ-C18].

**A-5**: A system prioritisation session is held in week one, bounding WP3 scope to what is achievable within the timeline [RQ-C18].

**A-6**: Hosting regions stated in the privacy context are working assumptions pending vendor confirmation, and cross-border positions must be confirmed before adoption decisions rely on them.

---

## Success Criteria and KPIs

### Business Success Metrics

| Metric | Baseline | Target | Measurement |
|--------|----------|--------|-------------|
| Capability categories with a designated primary platform | 0 of 8 | 8 of 8 | Capability map |
| Total ecosystem licence spend | To be established in WP3 | Flat or reduced | Contract register and finance system |
| Must-priority capability gaps addressed or explicitly deferred | Not assessed | 100% | Requirements-to-capability matrix |
| Source requirements mapped to capability status | 0 of 35 | 35 of 35 | Requirements-to-capability matrix |
| Roadmap delivered to business case timing | Not delivered | 31 August 2026 | Sponsor acceptance |

### Technical Success Metrics

| Metric | Baseline | Target | Measurement |
|--------|----------|--------|-------------|
| Production flows requiring a manual step | 4 of 7 known integrations | 0 carrying personal information | Integration register |
| Change propagation latency (identity, enrolment, role) | Up to 24 hours | Within 15 minutes | Integration telemetry |
| Platforms permitting local accounts | 2 | 0 | Security posture assessment |
| Mitigation strategies at target maturity | Largely ML1 against ML2 target | Documented pathway for all 8 | Essential Eight assessment |
| Personal information classes with an assessed privacy position | 0 of 8 | 8 of 8 | Privacy Impact Assessment |
| Integration failures detected by monitoring rather than user report | Not measured | 100% | Monitoring telemetry |
| Student-facing platforms with verified accessibility conformance | Not systematically assessed | All assessed | Conformance register |

### User Adoption Metrics

| Metric | Baseline | Target | Measurement |
|--------|----------|--------|-------------|
| New unit sites instantiated from the baseline template | No template in force | Majority, with justified exceptions | LMS reporting |
| Placement outcomes entered once by the supervisor | 0% — all re-keyed | 100% | Placement platform and gradebook reconciliation |
| Self-service course rollover completions | Request-driven, single-person dependency | Majority self-service | Rollover logs |

---

## Dependencies and Risks

### Dependencies

**D-1**: Architecture principles (`ARC-000-PRIN-v1.0`) must be endorsed by Education Committee before WP7 and WP8 proceed [RQ-C19].

**D-2**: WP3 capability mapping must be sufficiently progressed before requirements-to-capability mapping (BR-008) can complete.

**D-3**: Vendor capability, contract and roadmap data is required for BR-002 and the WP3 capability baseline.

**D-4**: The consolidation decision (Conflict C-1) must be resolved before target-state integration requirements can name specific platforms.

**D-5**: The Privacy Impact Assessment must run in parallel with capability mapping so that NFR-C-001 and NFR-C-002 findings shape platform decisions rather than invalidating them.

### Risks

| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|------------|
| Consolidation decision stalls, blocking future-state requirements | HIGH | HIGH | Publish decision criteria before scoring options; set a decision deadline protecting WP8 |
| Compliance findings arrive after platform decisions harden | MEDIUM | HIGH | Capture hosting region and SSO capability during WP3; run PIA in parallel |
| Timeline compression degrades requirements mapping, undermining BR-008 | MEDIUM | MEDIUM | Prioritise systems in week one; state coverage explicitly rather than implying completeness |
| Vendor interfaces cannot support event-driven propagation | MEDIUM | HIGH | Assess interface capability during WP3; record batch exceptions with review dates |
| Vendor unresponsiveness blocks capability and contract data | MEDIUM | MEDIUM | Procurement initiates engagement in week one; prioritise contracts due within the roadmap horizon |
| Academic resistance to consistency requirements prevents NFR-U-001 realisation | MEDIUM | MEDIUM | Make the compliant path the easiest path; deliver automation benefit before requesting conformance |

---

## Requirement Conflicts & Resolutions

> Conflicts below originate from the stakeholder conflict analysis in `ARC-001-STKE-v1.0`.

### Conflict C-1: Platform consolidation versus specialist capability

**Conflicting Requirements**:

- **Requirement A**: FR-008 — live online classes "using one primary platform"; and BR-001 requiring a designated primary per capability category
- **Requirement B**: FR-010 — multi-camera and high-fidelity performance capture; FR-005 — discipline notation and audio-production tooling

**Stakeholders Involved**:

- **Cassandra Rhodes (CIO)**: Wants consolidation onto a single vendor platform, reducing support surface, security surface and licence cost (driver SD-2)
- **Dr. Benny Moog (Director, Learning Technologies) and Prof. Desmond Key (Dean, Music)**: Defend best-of-breed pedagogical tooling that general-purpose platforms cannot replace (drivers SD-6, SD-13)

**Nature of Conflict**:

The register itself asks for "one primary platform" for live delivery, while separately requiring multi-camera and high-fidelity performance capture that a general-purpose collaboration platform is unlikely to provide. Three platforms currently deliver overlapping capture, delivery and collaboration capability [RQ-C16]. A platform cannot be both retired and retained.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Option 1**: Full consolidation onto one platform | Lowest support and security surface; clearest licence saving | Performance capture capability likely lost; discipline teaching quality reduced | Rhodes satisfied; Key and Moog opposed |
| **Option 2**: Retain best-of-breed across all categories | Pedagogical capability fully preserved | Duplication persists; licence and support cost unchanged; BR-002 unachievable | Moog and Key satisfied; Rhodes and Ostinato opposed |
| **Option 3**: Consolidate the general case, permit specialist tooling at the edge under common standards | Majority of duplication removed; discipline capability preserved; both positions partly met | Neither position fully satisfied; requires ongoing boundary governance | Both partly satisfied |
| **Option 4**: Defer the decision to the business case | Avoids conflict during the engagement | Future state ambiguous; WP8 blocked; decision taken without pedagogical input | Both dissatisfied; BR-003 at risk |

**Resolution Strategy**: COMPROMISE

**Decision**: Option 3 — consolidate the general case to a designated primary platform per capability category, while architecture principle 4 explicitly permits discipline-specific tooling at the edge, held to the same identity, integration, accessibility and privacy standards as core platforms.

**Rationale**: Option 3 is the only option that satisfies both BR-001 (bounded ecosystem) and FR-005 / FR-010 (discipline capability). Critically, it converts the disagreement from "which platform wins" into "where is the boundary" — a question that capability mapping can answer with evidence. The specific platform decision remains open and is routed to WP6 as a formal decision with criteria published *before* options are scored.

**Decision Authority**: Dr. Benny Moog facilitates through RIFF; A/Prof. Pearl Clavinet accountable via Education Committee. Escalates to Steering Committee (Hammond, Rhodes, Clavinet) if RIFF cannot converge. Per the RACI in `ARC-001-STKE-v1.0`.

**Impact on Requirements**:

- **Modified**: FR-008 retains "one primary platform" for the general case, with the specific platform to be determined at WP6
- **Retained with elevated visibility**: FR-010 remains COULD_HAVE by register priority, but is flagged as materially affecting the capture platform decision so it is not silently dropped
- **Added**: BR-001 success criterion requiring every overlap to be classified rather than merely identified

**Stakeholder Management**:

- **Rhodes (partial)**: Consolidation proceeds for the general case; the support and security surface reduces materially. Specialist exceptions are bounded and must meet SSO and privacy criteria.
- **Moog and Key (partial)**: Discipline capability is protected by architectural principle rather than case-by-case advocacy — a stronger position than they currently hold. The corresponding obligation is that specialist tools meet common standards.

**Future Consideration**: Boundary statements reviewed at each contract renewal via RIFF. If a general-purpose platform later meets the performance capture requirement, the exception is revisited.

---

### Conflict C-2: Cost containment versus integration investment

**Conflicting Requirements**:

- **Requirement A**: BR-002 — licence spend flat or reduced while Must-priority gaps close
- **Requirement B**: BR-004, INT-001 to INT-006 — near-real-time governed integration requiring capital investment

**Stakeholders Involved**:

- **Vernon Ostinato (CFO)**: Requires the financial test to be met (driver SD-3)
- **Cassandra Rhodes (CIO) and Sam Okafor (Integration Architect)**: Require funded integration uplift (drivers SD-2, SD-7)

**Nature of Conflict**:

Fixing the integration estate requires one-off investment that produces no licence saving. Presented as a single number, rationalisation appears to cost money rather than save it.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Option 1**: Fund integration fully upfront | Fastest remediation of fragility and privacy findings | Business case shows net cost; BR-002 fails | Rhodes satisfied; Ostinato opposed |
| **Option 2**: Defer integration until savings are realised | BR-002 met cleanly | Privacy and audit defects persist; FR-018 unresolved | Ostinato satisfied; Frame and Anand exposed |
| **Option 3**: Separate recurring licence spend from one-off investment; phase, funding uplift partly from rationalisation savings | Both tests met on their own terms; quick wins demonstrate value early | Slower full remediation; requires disciplined sequencing | Both satisfied |

**Resolution Strategy**: PHASE

**Decision**: Option 3 — the business case separates recurring licence spend from one-off integration investment, each with its own benefit case. Highest-risk flows are sequenced first.

**Rationale**: BR-002 is a test of *recurring licence spend*, not of total programme cost. Conflating them creates a false conflict. Sequencing the placement grade flow (INT-005) and provisioning automation (INT-003) first delivers demonstrable operational and privacy benefit before the larger canonical-model investment is requested.

**Decision Authority**: Vernon Ostinato accountable for the financial position; Prof. Otis Hammond accountable for roadmap sequencing.

**Impact on Requirements**:

- **Modified**: BR-002 success criteria explicitly scoped to licence spend, with integration investment stated separately
- **Sequenced**: INT-005 and INT-003 prioritised as early remediation; INT-007 and INT-008 deferred

**Stakeholder Management**:

- **Ostinato**: The financial test is met on its own terms and evidenced against contract data.
- **Rhodes and Okafor**: Uplift is funded, though phased rather than immediate. Highest-risk flows are addressed first.

**Future Consideration**: Re-test the licence spend model at each renewal point as actual savings are realised.

---

### Conflict C-3: Security and privacy criteria versus pedagogical tool retention

**Conflicting Requirements**:

- **Requirement A**: NFR-SEC-001 — institutional SSO with MFA, no local accounts; NFR-C-002 — cross-border disclosure assessed and accepted
- **Requirement B**: FR-005, FR-006, FR-010 — discipline tooling that academics value and that may not meet those criteria

**Stakeholders Involved**:

- **Tobias Ohm (Cybersecurity) and Eleanor Frame (Privacy)**: Require conformance (drivers SD-10, SD-11)
- **Dr. Benny Moog, Prof. Desmond Key, Prof. Priya Anand**: Require capability (drivers SD-6, SD-13, SD-14)

**Nature of Conflict**:

Two platforms already permit local accounts in breach of NFR-SEC-001 [RQ-C11], and four data classes are held offshore [RQ-C10]. The platforms concerned may be exactly those academics value most. Compliance stakeholders hold MEDIUM formal influence but effective veto — an objection raised late can stop a decision after the business case is written.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Option 1**: Enforce criteria strictly, retire non-conforming platforms | Clean security and privacy posture | Capability loss; academic resistance; possible teaching disruption | Ohm and Frame satisfied; Deans opposed |
| **Option 2**: Grant standing exemptions for pedagogically valued tools | Capability preserved | Posture indefensible; NFR-SEC-002 target unreachable | Deans satisfied; Ohm and Frame exposed |
| **Option 3**: Assess conformance during capability mapping; where a valued tool fails, present remediate / accept-with-dated-review / retire as an explicit decision at RIFF with the affected school present | Decision made with full information by the right forum; no late surprises | Requires compliance stakeholders engaged early; some decisions will be genuinely hard | Both engaged; outcome decided case by case |

**Resolution Strategy**: INNOVATE (process solution rather than requirement trade-off)

**Decision**: Option 3 — privacy and security conformance become attributes captured during WP3 capability mapping, not a gate applied afterwards. Where a valued tool fails a criterion, three options are presented explicitly and the decision is taken at RIFF with the affected school present.

**Rationale**: The conflict is largely one of *sequencing*, not of substance. Assessed early, a conformance gap shapes the platform decision. Assessed late, it invalidates one — and compliance stakeholders appear obstructive when they are simply arriving after the fact. Moving the assessment earlier dissolves most of the conflict without weakening either requirement.

**Decision Authority**: Tobias Ohm responsible for security exception acceptance, Eleanor Frame for privacy positions, both accountable to Cassandra Rhodes. Per the RACI in `ARC-001-STKE-v1.0`.

**Impact on Requirements**:

- **Modified**: NFR-SEC-001 acceptance criteria include dated remediation plans for existing exceptions rather than requiring immediate retirement
- **Modified**: NFR-C-002 requires the practicability of an Australian-region alternative to be documented, including where none exists
- **Added**: DR-005 residency register, so hosting region is captured at procurement rather than discovered at assessment

**Stakeholder Management**:

- **Ohm and Frame**: Gain early visibility and a structured decision path — a stronger position than a late veto.
- **Moog, Key and Anand**: Affected schools are present when a tool-affecting decision is taken, rather than informed afterwards.

**Future Consideration**: Time-bound exceptions reviewed at expiry, never automatically renewed.

---

### Conflict C-4: Delivery timeline versus requirements mapping depth

**Conflicting Requirements**:

- **Requirement A**: BR-003 — roadmap delivered by 31 August 2026
- **Requirement B**: BR-008 — all 35 source requirements mapped to capability status through workshop-based analysis

**Stakeholders Involved**:

- **Rhonda Bell (PM)**: Fixed deadline (driver SD-9)
- **Dr. Felix Marimba, Dr. Wynton Castle, Jazmin Field**: Consultative depth (drivers SD-8, SD-15, SD-16)

**Nature of Conflict**:

Requirements mapping is workshop-based and depends on WP3 progress. Under deadline pressure it degrades to desk analysis, and the survey's influence becomes nominal — the precise outcome BR-008 exists to prevent.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Option 1**: Full workshop mapping for all systems | Highest fidelity; BR-008 fully met | Deadline at serious risk | Marimba satisfied; Bell and Hammond exposed |
| **Option 2**: Desk analysis throughout | Deadline safe | Survey influence nominal; BR-008 met in form only | Bell satisfied; Marimba's credibility damaged |
| **Option 3**: Prioritise systems in week one; workshop depth for prioritised systems and all Must-priority requirements; desk review for the remainder, with coverage stated explicitly | Deadline met; depth where it matters; honest about what was not covered | Some systems receive lighter treatment | Both partly satisfied; nothing misrepresented |

**Resolution Strategy**: COMPROMISE

**Decision**: Option 3 — depth analysis for prioritised systems and all Must-priority requirements; desk review for the remainder, with the deliverable stating explicitly which received which.

**Rationale**: An honest coverage statement protects the engagement's credibility more than an implied completeness it did not achieve. Silently narrowing scope is the failure mode to avoid — it is also what would most damage Marimba's standing with the 412 respondents.

**Decision Authority**: Rhonda Bell responsible, Dr. Benny Moog accountable for system prioritisation. Per the RACI in `ARC-001-STKE-v1.0`.

**Impact on Requirements**:

- **Modified**: BR-008 success criteria retain 100% mapping coverage, but the deliverable must distinguish depth analysis from desk review
- **Added**: Any requirement left unmapped at depth is scheduled as a named post-engagement activity with an owner

**Stakeholder Management**:

- **Bell**: Deadline protected by bounded scope agreed in week one.
- **Marimba**: Must-priority requirements — the ones respondents care most about — receive full treatment, and the coverage statement is transparent rather than silent.

**Future Consideration**: Complete depth mapping for deferred systems in the first post-engagement quarter.

---

### Conflict C-5: Navigation consistency versus academic autonomy

**Conflicting Requirements**:

- **Requirement A**: FR-001, NFR-U-001 — consistent structure, navigation and terminology across all schools
- **Requirement B**: Academic autonomy over unit site design, and staff workload capacity

**Stakeholders Involved**:

- **Jazmin Field (Student Guild) and A/Prof. Pearl Clavinet**: Require consistency (drivers SD-16, SD-4)
- **Dr. Wynton Castle and teaching staff generally**: Resist mandated rework (driver SD-15)

**Nature of Conflict**:

Template conformance serves students but reads to teaching staff as an instruction to rebuild unit sites that currently work. Castle holds LOW formal power but high informal influence, and academic adoption ultimately determines whether consistency is achieved at all.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Option 1**: Mandate conformance with a deadline | Fastest consistency on paper | High resistance; likely non-adoption; relationship cost | Field satisfied nominally; Castle opposed; outcome not delivered |
| **Option 2**: Make conformance voluntary | No resistance | Consistency not achieved; NFR-U-001 fails | Castle satisfied; Field and students unserved |
| **Option 3**: Scope consistency to the student-facing surface; permit and record pedagogical variation; make the compliant path the easiest path through templates and automated rollover | Both served; adoption driven by benefit rather than mandate | Slower; depends on rollover automation landing first | Both satisfied if sequencing holds |

**Resolution Strategy**: INNOVATE

**Decision**: Option 3 — NFR-U-001 applies to the student-facing surface only. Pedagogical variation is permitted and recorded. FR-001 and INT-004 (automated self-service rollover) are sequenced so that staff experience effort *reduction* before conformance is requested.

**Rationale**: The apparent conflict dissolves under reframing. Automated rollover and a working baseline template reduce staff effort *and* deliver student consistency — the same intervention satisfies both drivers if presented as effort reduction rather than compliance. Mandating conformance without first delivering the automation is what converts an aligned interest into a contested one.

**Decision Authority**: A/Prof. Pearl Clavinet accountable via Education Committee, with Dr. Benny Moog responsible for template and rollover delivery.

**Impact on Requirements**:

- **Modified**: NFR-U-001 explicitly scoped to the student-facing surface, not staff authoring workflow
- **Sequenced**: INT-004 rollover automation delivered before template conformance is requested
- **Added**: FR-001 acceptance criterion permitting recorded pedagogical variation

**Stakeholder Management**:

- **Field**: The student-facing outcome is delivered, with student representation in validation.
- **Castle**: Involved in principles validation; receives automation benefit first. Convincing him is disproportionately valuable given his informal influence.

**Future Consideration**: Review conformance rate per teaching period with student representation; phase across teaching periods rather than setting a single deadline.

---

## Timeline and Milestones

### High-Level Milestones

| Milestone | Target | Depends On |
|-----------|--------|------------|
| Architecture principles endorsed by Education Committee | Mid-August 2026 | Stakeholder validation workshops |
| Current landscape and capability baseline validated | Mid-August 2026 | Week-one system prioritisation; vendor data |
| Requirements mapped to capability status | Late August 2026 | Capability baseline |
| Integration architecture and canonical model defined | Late August 2026 | Landscape assessment; principles endorsed |
| Contested platform decisions resolved at RIFF | Late August 2026 | Capability mapping evidence |
| Privacy Impact Assessment complete | Late August 2026 | Hosting region data from vendors |
| Recommendations and roadmap delivered | 31 August 2026 | All of the above |
| Business case submitted | September 2026 | Roadmap accepted |

**Note**: This timeline covers the *engagement*. Delivery of the requirements defined in this document extends across the roadmap horizon to end 2027 and beyond, and is out of scope for this engagement [RQ-C6].

---

## Budget

### Cost Estimate

Not established at this stage. The engagement's WP3 capability mapping establishes the licence spend baseline, and the WP9 roadmap produces the costed rationalisation position that feeds the September business case. Cost figures are therefore an output of this engagement rather than an input to these requirements.

Two cost categories must be modelled separately, per the resolution of Conflict C-2:

| Category | Basis | Owner |
|----------|-------|-------|
| Recurring licence spend | Contract register, renewal calendar, capability duplication analysis | Grace Tanaka, reporting to Vernon Ostinato |
| One-off integration investment | Target integration architecture scope, sequenced by risk | Sam Okafor, reporting to Cassandra Rhodes |

### Ongoing Operational Costs

To be established in WP9. Must include support model costs for discipline-specific tooling, where internal support arrangements are currently unclear [RQ-C15].

---

## Approval

### Requirements Review

| Reviewer | Role | Review Date | Status |
|----------|------|-------------|--------|
| Dr. Felix Marimba | Requirements custodian | [PENDING] | [PENDING] |
| Dr. Benny Moog | Product owner, L&T ecosystem | [PENDING] | [PENDING] |
| Sam Okafor | Integration Architect | [PENDING] | [PENDING] |
| Eleanor Frame | Privacy & Records Officer | [PENDING] | [PENDING] |
| Tobias Ohm | Cybersecurity Lead | [PENDING] | [PENDING] |
| Jazmin Field | Student Guild | [PENDING] | [PENDING] |

### Sign-Off

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Executive Sponsor | Prof. Otis Hammond, DVC (Education) | | |
| Academic Authority | A/Prof. Pearl Clavinet, Chair Education Committee | | |
| Technical Authority | Cassandra Rhodes, Chief Information Officer | | |

---

## Appendices

### Appendix A: Glossary

| Term | Definition |
|------|------------|
| APP | Australian Privacy Principle — the 13 principles under the Privacy Act 1988 |
| Capability category | One of the eight categories in the institutional L&T capability taxonomy |
| Canonical data model | A single agreed representation of core entities that all integrations map to and from |
| Essential Eight | The ASD's eight prioritised mitigation strategies, assessed at Maturity Levels 0 to 3 |
| LMS | Learning Management System — the primary learning platform |
| MoSCoW | Prioritisation method: Must have, Should have, Could have, Won't have |
| RIFF Review | Review of Innovation, Fit & Function — the institutional gate for L&T technology requests |
| Sensitive information | A defined subset of personal information under the Privacy Act attracting elevated protection |
| Unit | A single subject of study within a program |

### Appendix B: Reference Documents

| Document | Location |
|----------|----------|
| ARC-000-PRIN-v1.0 — Enterprise Architecture Principles | `projects/000-global/` |
| ARC-001-STKE-v1.0 — Stakeholder Drivers & Goals Analysis | `projects/001-lt-ecosystem/` |
| Consultant Engagement Brief | `projects/001-lt-ecosystem/external/` |
| Requirements Register — Academic Survey | `projects/001-lt-ecosystem/external/` |
| System Categorisation & Status | `projects/001-lt-ecosystem/external/` |
| Privacy & Security Context | `projects/001-lt-ecosystem/external/` |
| L&T Capability Taxonomy | `projects/000-global/external/` |
| L&T Technology Solution Governance Process (RIFF) | `projects/000-global/policies/` |

### Appendix C: Wireframes and Mockups

Not applicable. This engagement produces architecture requirements, not interface designs.

### Appendix D: Data Models

The canonical data model for student, course and enrolment (DR-001) is a WP5 deliverable. Run `/arckit:data-model` to produce the full entity model from the DR-xxx requirements in this document.

### Appendix E: Source Requirement Cross-Reference

> Bidirectional mapping between the source survey register [RQ-C1] and the ArcKit typed identifiers in this document. Preserves traceability to the 412 survey respondents.

#### E.1 — Source register to ArcKit requirements

| Source | Source Requirement (abbreviated) | Priority | ArcKit ID(s) |
|--------|----------------------------------|----------|--------------|
| REQ-001 | Course templates for consistent structure | Must | FR-001, NFR-U-001, BR-006 |
| REQ-002 | Interactive content without specialist skills | Should | FR-002 |
| REQ-003 | Central reading lists with copyright compliance | Must | FR-003 |
| REQ-004 | Single supported video toolchain | Must | FR-004 |
| REQ-005 | Music notation and audio-production materials | Should | FR-005 |
| REQ-006 | Clinical simulation with device integration | Must | FR-006 |
| REQ-007 | Single entry point for students | Must | FR-007, NFR-U-001, BR-006 |
| REQ-008 | Live online classes, one primary platform | Must | FR-008 |
| REQ-009 | Automatic lecture capture within 4 hours | Must | FR-009, NFR-P-002 |
| REQ-010 | Multi-camera performance capture | Could | FR-010 |
| REQ-011 | Group collaboration linked to enrolment | Must | FR-013 |
| REQ-012 | Automatic group provisioning from timetable | Must | FR-014, INT-006 |
| REQ-013 | Peer review with anonymised marking | Should | FR-011 |
| REQ-014 | In-class polling and formative checks | Should | FR-012 |
| REQ-015 | Whole-of-program portfolio, exportable | Must | FR-015, DR-008 |
| REQ-016 | Similarity and AI-writing detection | Must | FR-016 |
| REQ-017 | Secure examination, on-campus and remote | Must | FR-017 |
| REQ-018 | Single-entry placement assessment | Must | FR-018, INT-005 |
| REQ-019 | Micro-credentials and badging | Could | FR-019 |
| REQ-020 | Cohort engagement and at-risk dashboard | Should | FR-020 |
| REQ-021 | Single platform for teaching evaluation | Must | FR-021 |
| REQ-022 | Analytics export to institutional data platform | Should | FR-022, INT-009, DR-006 |
| REQ-023 | SIS to LMS within 15 minutes | Must | INT-001, NFR-P-001, BR-004 |
| REQ-024 | Institutional role from single source | Must | INT-002, DR-002 |
| REQ-025 | Automated provisioning, no manual CSV | Must | INT-003, NFR-SEC-003, BR-004 |
| REQ-026 | Automated self-service course cloning | Should | INT-004, NFR-M-002, BR-004 |
| REQ-027 | Canonical data model for core entities | Must | DR-001 |
| REQ-028 | Placement grades bidirectional with gradebook | Must | INT-005, FR-018, BR-004 |
| REQ-029 | WCAG 2.2 AA accessibility | Must | NFR-U-002, BR-006 |
| REQ-030 | Privacy Act 1988 / APP compliance, APP 8 | Must | NFR-C-001, NFR-C-002, DR-003, DR-005, BR-005 |
| REQ-031 | SSO with MFA, no local accounts | Must | NFR-SEC-001, NFR-SEC-003, BR-005 |
| REQ-032 | 99.9% availability during teaching periods | Must | NFR-A-001 |
| REQ-033 | Essential Eight maturity alignment | Must | NFR-SEC-002, BR-005 |
| REQ-034 | Data export in open formats on termination | Should | NFR-I-002, DR-007 |
| REQ-035 | Licence spend flat or reduced | Should | BR-002, BR-001 |

**Coverage**: 35 of 35 source requirements mapped. No source requirement is unrepresented.

#### E.2 — Derived requirements with no survey source

> These requirements originate from the architecture principles, the privacy and security context, or the current-state integration assessment — **not** from the academic survey. Listed separately so the survey's actual scope is never overstated.

| ArcKit ID | Requirement | Origin |
|-----------|-------------|--------|
| BR-001 | Deliberately bounded capability ecosystem | Architecture principle 2; consultant brief WP9 |
| BR-003 | Roadmap delivered to business case timing | Consultant brief, due date |
| BR-007 | Governance operating on architectural evidence | RIFF process; principles 18, 19 |
| BR-008 | Survey requirements traceable to outcomes | Stakeholder driver SD-8; brief WP7 |
| NFR-A-002 | Change control aligned to academic calendar | Architecture principle 15 |
| NFR-S-001 | Peak load capacity | Architecture principle 1 |
| NFR-C-003 | Audit logging for academic and access records | Integration landscape audit concerns |
| NFR-M-001 | Integration observability | Architecture principle 17 |
| NFR-I-001 | Published, versioned interfaces | Architecture principle 10 |
| INT-007 | Institutional hierarchy synchronisation | Current-state integration 4 |
| INT-008 | Sandpit environment provisioning | Consultant brief WP5 |
| DR-004 | Sensitive information handling — placement records | Privacy context §1, §2 |

---

## External References

> This section provides traceability from generated content back to source documents.

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RQ-D1 | requirements-register.md | Requirements input | `projects/001-lt-ecosystem/external/` | Consolidated academic survey requirements REQ-001 to REQ-035 |
| RQ-D2 | consultant-brief.md | Engagement brief | `projects/001-lt-ecosystem/external/` | Work packages WP1 to WP9, scope, assumptions, due date |
| RQ-D3 | system-landscape.md | Foundation artifact | `projects/001-lt-ecosystem/external/` | System categorisation map, usage status, known integrations |
| RQ-D4 | privacy-context.md | Compliance input | `projects/001-lt-ecosystem/external/` | Personal information inventory, data flows, Essential Eight self-assessment |
| RQ-D5 | stakeholders.md | Engagement input | `projects/001-lt-ecosystem/external/` | Engagement stakeholder register |
| RQ-D6 | capability-taxonomy.md | Enterprise standard | `projects/000-global/external/` | Eight-category L&T capability taxonomy |
| RQ-D7 | solution-governance-process.md | Global policy | `projects/000-global/policies/` | RIFF Review governance and approval process |
| RQ-D8 | ARC-000-PRIN-v1.0.md | ArcKit artifact | `projects/000-global/` | Enterprise Architecture Principles |
| RQ-D9 | ARC-001-STKE-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/` | Stakeholder Drivers & Goals Analysis |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| RQ-C1 | RQ-D1 | All tables | Requirements | Consolidated register of 35 requirements identified REQ-001 to REQ-035 across functional, integration and non-functional groupings |
| RQ-C2 | RQ-D1 | Header | Provenance | "Consolidated requirements from the 2026 academic survey (412 responses across all schools)." |
| RQ-C3 | RQ-D6 | Table | Taxonomy | Eight capability categories: Course Design, Learning Resources, Learning Delivery, Learning Capture, Active Learning, Collaboration, Assessment & Progress Tracking, Evaluation & Analytics |
| RQ-C4 | RQ-D2 | §1 | Scope | "The Solution Architect (SA) is not required to gather or manage requirements — they are applied architecturally." |
| RQ-C5 | RQ-D3 | Known integrations | Current state | "Fragile; role assignment failures; no intra-day sync"; "Manual workaround for casual academic staff"; "Undocumented; single-person dependency"; "Drift between PeopleSoft and Blackboard hierarchies"; "Timetable changes not reflected until next run"; "Error-prone; audit concerns" |
| RQ-C6 | RQ-D2 | §2, WP5 | Scope | "Delivery of these integrations is out of scope; the architecture governing them is in scope." |
| RQ-C7 | RQ-D2 | §2, WP3 | Scope | "Functionality paid for but not configured or in use"; "Standardised capability categories to enable cross-system comparison and duplication analysis" |
| RQ-C8 | RQ-D2 | Header, §2 | Constraint | "Due date: 31 August 2026"; "structured to feed directly into the September business case" |
| RQ-C9 | RQ-D4 | §2 | Privacy | "Flat-files at rest on shared storage; stale de-provisioning (access persists up to 24h after withdrawal)"; "Human error; screenshots/exports circulating via email"; "No defined retention or minimisation rules" |
| RQ-C10 | RQ-D4 | §1 | Privacy | "APP 8 triggers: classes 3, 4 (partial), 6 and 7 involve offshore disclosure under the assumed hosting — the PIA must assess cross-border disclosure accountability, contract clauses and the practicability of AU-region alternatives." |
| RQ-C11 | RQ-D4 | §3 | Security | Essential Eight self-assessment: target "ML2 across the SaaS-heavy L&T estate by end 2027"; MFA row notes two tools still allow local accounts breaching REQ-031; backups row notes "SaaS export coverage unverified for 4 tools" |
| RQ-C12 | RQ-D1 | REQ-001, REQ-007 | Requirement | Consistent structure and navigation across all schools; single entry point for materials, activities and grades |
| RQ-C13 | RQ-D1 | REQ-029 | Requirement | "All student-facing tools shall conform to WCAG 2.2 AA accessibility" |
| RQ-C14 | RQ-D7 | Rules | Governance | "Business case submissions include the RIFF review as supporting documentation"; "Solutions duplicating capability already licensed (per the system landscape map) must justify why the incumbent tool is unsuitable." |
| RQ-C15 | RQ-D3 | Notes | Context | Investigations outstanding for badging software options, Articulate 360 enterprise licensing, Kuracloud internal support model, MuseScore and Ableton Live usage and licensing, and OnExam extent of use |
| RQ-C16 | RQ-D3 | Notes | Context | "MS Teams — investigation planned for 2027 to establish a seamless platform experience across collaboration, learning delivery and lecture capture (overlaps with Zoom and Echo360 — key rationalisation candidate)." |
| RQ-C17 | RQ-D4 | §1 | Privacy | Personal information inventory of eight classes; row 5 "Placement records (incl. clearance metadata, health-context notes)" classified as sensitive information |
| RQ-C18 | RQ-D2 | §4 | Assumptions | Consolidated requirements provided to the SA; foundation artifacts provided at commencement; Integration team available for WP4 and WP5; project team facilitates vendor access; system prioritisation session held in week one |
| RQ-C19 | RQ-D2 | §2, WP1 | Dependency | "Start immediately. Must be agreed before WP7 and WP8 proceed." |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| ARC-000-PRIN-v1.0.md (RQ-D8) | `projects/000-global/` | Principles are referenced by number throughout as the origin of derived requirements; no verbatim passage is quoted |
| ARC-001-STKE-v1.0.md (RQ-D9) | `projects/001-lt-ecosystem/` | Stakeholder goals, drivers and conflicts are referenced by ID throughout; no verbatim passage is quoted |
| stakeholders.md (RQ-D5) | `projects/001-lt-ecosystem/external/` | Superseded for this document by the derived stakeholder analysis (RQ-D9) |

---

**Generated by**: ArcKit `/arckit:requirements` command
**Generated on**: 2026-07-26 GMT
**ArcKit Version**: 6.4.0
**Project**: Learning & Teaching Baseline Strategy (Project 001)
**AI Model**: Claude Opus 5 (1M context)
**Generation Context**: Derived from the consolidated academic survey register (REQ-001 to REQ-035), the consultant engagement brief, the system categorisation map, the privacy and security context, the RIFF governance process, the L&T capability taxonomy, and the project's own ARC-000-PRIN-v1.0 principles and ARC-001-STKE-v1.0 stakeholder analysis.

<!-- arckit-provenance:start -->

## Build Provenance

_Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix._

| Field | Value |
|-------|-------|
| Requested Effort | `max` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-07-26T10:40:37.529Z |

<!-- arckit-provenance:end -->
