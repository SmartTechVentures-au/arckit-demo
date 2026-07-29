# Project Requirements: LMS Ultra Migration & Integration Modernisation

> **Template Origin**: Official | **ArcKit Version**: 6.7.4 | **Command**: `/arckit:requirements`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-003-REQ-v1.0 |
| **Document Type** | Business and Technical Requirements |
| **Project** | 003-lms-ultra-migration — Blackboard Ultra Migration & Integration Modernisation |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-29 |
| **Last Modified** | 2026-07-29 |
| **Review Date** | 2026-08-28 |
| **Owner** | Sam Okafor, Integration Architect |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Project Team, Steering Committee, Digital & IT |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-29 | ArcKit AI | Initial creation from `/arckit:requirements` command | PENDING | PENDING |

---

## Document Purpose

This document defines the business, functional, non-functional, integration, and data requirements for the Blackboard Ultra Migration & Integration Modernisation project (Project 003). It operationalises the integration architecture defined in ARC-001-ADR-001-v1.0, the canonical data model defined in ARC-001-DATA-v1.0, and the stakeholder drivers and goals captured in ARC-003-STKE-v1.0.

Where Project 001 (ARC-001-REQ-v1.0) established the architecture requirements for the Learning & Teaching ecosystem at large, this document narrows focus to the concrete delivery: migrating Blackboard Learn Original to Ultra, re-engineering seven integrations through a canonical data model and event-driven architecture, and eliminating the manual handling of personal information that is simultaneously the estate's fragility finding and its privacy finding.

Every requirement carries a unique identifier, traces to stakeholder goals and architecture principles, and defines acceptance criteria against which delivery can be verified.

---

## Executive Summary

### Business Context

The University of Funk operates Blackboard Learn Original as its primary LMS, supported by seven integrations ranging from a nightly flat-file feed from PeopleSoft to manual re-keying of placement grades from Sonia. Four of these seven integrations involve manual handling or flat-file transfer of personal information. The architecture baseline established in Project 001 documented these as both integration defects and privacy findings under the Privacy Act 1988.

Anthology's end-of-support trajectory for Learn Original creates a forcing function: migration to Blackboard Ultra is required. This migration is simultaneously the opportunity to implement the integration mediation approach decided in ADR-001 — replacing fragile point-to-point flows with event-driven integration through a canonical data model and a central integration broker.

### Objectives

- Migrate all faculties from Blackboard Learn Original to Blackboard Ultra with zero disruption to assessment or examination periods
- Re-engineer the PeopleSoft-to-Blackboard integration from nightly flat-file to event-driven, near-real-time propagation through the canonical data model
- Eliminate all manual flows carrying personal information — CSV provisioning, flat-file transfers, manual re-keying of placement grades
- Enforce institutional SSO/MFA on Ultra from day one with no local accounts, and modernise integration credentials to OAuth 2.0 service accounts
- Deploy consistent, accessible Ultra unit site templates that make conformance the path of least resistance

### Expected Outcomes

| Outcome | Summary | Traces To (STKE) | Primary Requirements |
|---------|---------|-------------------|----------------------|
| O-1 | Sustainable integration estate — event-driven, canonical-model-mediated, no manual handling | ARC-003-STKE O-1 | BR-001, BR-003, INT-001 to INT-007 |
| O-2 | Academic community adopted Ultra without disruption — zero assessment-period incidents, templates adopted, discipline tools verified | ARC-003-STKE O-2 | BR-002, BR-005, FR-001 to FR-015 |
| O-3 | Privacy and security posture measurably improved — zero manual PI flows, zero local accounts, deprovisioning within minutes | ARC-003-STKE O-3 | BR-004, NFR-SEC-001 to NFR-SEC-004, NFR-C-001 to NFR-C-003 |

### Project Scope

**In Scope**:

- Migration of all Blackboard Learn Original unit sites, content, and configuration to Blackboard Ultra
- Re-engineering of all seven known integrations through the canonical data model and event broker (per ADR-001)
- Ultra template design, testing, and deployment across all faculties
- Academic training and change management for Ultra adoption
- Data migration with explicit privacy controls (minimisation, retention, access restriction)
- LTI 1.3 Advantage verification for all discipline-specific tool integrations
- Sandpit provisioning design (integration 7, planned 2027)

**Out of Scope**:

- Replacement of the Student Information System (PeopleSoft) — it remains the authoritative source for student, course, and enrolment data
- Non-L&T institutional integrations not connected to the LMS or its supporting platforms
- Procurement of a new integration broker — that is governed by ADR-001 Condition 1 (Principle 19 test)
- Resolution of ADR-002 (Authoritative Source for Institutional Role Assignment) — that is a prerequisite for this project, not a deliverable of it
- Lecture capture platform decision (Project 002)
- Teaching-lab desktop fleet and lecture-theatre appliance estate

---

## Stakeholders

| Stakeholder | Role | Organisation/Department | Involvement Level |
|-------------|------|------------------------|-------------------|
| Prof. Otis Hammond | Deputy Vice-Chancellor (Education) | University Executive | Executive Sponsor — decision maker |
| Cassandra Rhodes | Chief Information Officer | Digital & IT | Technical decision maker; funds integration uplift |
| A/Prof. Pearl Clavinet | Dean of L&T; Chair, Education Committee | Academic governance | Academic approval authority; migration timeline gate |
| Prof. Stella Groove | Vice-Chancellor | University Executive | Funding approval; exception escalation |
| Vernon Ostinato | Chief Financial Officer | Finance | Migration cost justification; contract terms |
| Rhonda Bell | Project Manager | Project Team | Day-to-day coordination; migration scheduling |
| Sam Okafor | Integration Architect | Digital & IT | Integration delivery; canonical model implementation |
| Dr. Benny Moog | Director, Learning Technologies | Learning Technologies | Ultra configuration; template design; RIFF |
| Dr. Felix Marimba | Academic Lead, Digital Learning | Academic | Academic change management; training |
| Grace Tanaka | Procurement & Vendor Manager | Procurement | Blackboard contract; Ultra licensing terms |
| Tobias Ohm | Cybersecurity Lead | Digital & IT | SSO/MFA enforcement; E8 alignment |
| Eleanor Frame | Privacy & Records Officer | Governance | Data migration privacy; manual flow remediation |
| Prof. Desmond Key | Dean, Music & Performing Arts | Academic | Discipline tool LTI verification |
| Prof. Priya Anand | Dean, Health Sciences | Academic | Placement integration priority |
| Dr. Wynton Castle | Senior Lecturer; LMS power user | Academic | Ultra interface change; template migration |
| Jazmin Field | President, Student Guild | Students | Student experience during transition |
| Student Administration | Representative TBD | Student Services | PeopleSoft integration; enrolment lifecycle |
| Human Resources | Representative TBD | HR | Staff role assignment source (ADR-002) |

> **Source**: ARC-003-STKE-v1.0 stakeholder register. Student Administration and Human Resources added to address the engagement gap identified in ADR-002.

---

## Business Requirements

### BR-001: Migration without assessment-period disruption

**Description**: The Blackboard Learn Original to Ultra migration must be completed across all faculties with zero disruption to assessment or examination periods, using a phased rollout aligned to the academic calendar.

**Rationale**: A migration that disrupts assessment directly harms students and permanently damages the programme's credibility with the academic community. CSF-1 in ARC-003-STKE requires that no teaching period experiences both a changed LMS interface and a changed integration simultaneously.

**Acceptance Criteria**:

- Zero assessment-period disruption incidents attributable to migration
- Migration phases scheduled exclusively in inter-semester windows, with change freezes enforced during assessment periods
- Rollback capability verified before each migration phase commences
- Pilot programme completed with willing academics before full rollout, achieving satisfaction rating above 80%
- Content migration success rate exceeds 95% (items migrated without manual intervention)

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE G-3, CSF-1; REQ-032

**Stakeholder**: Rhonda Bell (delivery), Prof. Otis Hammond (accountable)

**Traces To**: Goal G-3 · Outcome O-2 · Principles P1, P3

---

### BR-002: Integration estate re-engineered to event-driven architecture

**Description**: All seven known integrations must be re-engineered from their current batch, flat-file, and manual mechanisms to event-driven, near-real-time flows mediated through the canonical data model and the integration broker selected under ADR-001.

**Rationale**: The current integration estate is the engagement's primary fragility finding. Four of seven integrations involve manual handling or flat-file transfer. The nightly batch PeopleSoft integration means access and role state are wrong for up to 24 hours. ADR-001 selected a central integration broker specifically to enforce the canonical model at runtime rather than by convention.

**Acceptance Criteria**:

- All seven integrations operating through the canonical data model with events published and consumed via the integration broker
- Change propagation latency for identity, enrolment, and role changes within 15 minutes (per NFR-P-001)
- Zero manual steps in any production data flow
- Integration failures detected by monitoring and alerted to named owners, not discovered by user report
- Old integration mechanisms decommissioned after each new flow has run one full teaching period

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE G-1, CSF-2, CSF-3; ADR-001; REQ-023, REQ-024, REQ-027

**Stakeholder**: Sam Okafor (delivery), Cassandra Rhodes (accountable)

**Traces To**: Goal G-1, G-5 · Outcome O-1 · Principles P5, P6, P10, P11

---

### BR-003: Manual flows carrying personal information eliminated

**Description**: All manual re-keying, CSV file loads, flat-file transfers, and email-circulated exports carrying personal information must be eliminated as part of the migration — not deferred to a follow-on project.

**Rationale**: These are simultaneously the estate's privacy findings under the Privacy Act 1988 (APPs) and its integration defects. Migrating to Ultra without fixing them replicates the privacy exposure on a new platform. CSF-4 requires that manual flows are eliminated, not migrated.

**Acceptance Criteria**:

- Zero production data flows requiring a manual step involving personal information
- Zero flat files on shared storage carrying personal information
- Zero CSV-based user provisioning events per month
- Placement grades flowing bidirectionally between Sonia and Ultra without manual re-keying
- Echo360 user provisioning automated through LTI and the canonical model, with no manual CSV

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE G-2, CSF-4; REQ-025, REQ-028

**Stakeholder**: Eleanor Frame (sign-off), Sam Okafor (delivery)

**Traces To**: Goal G-2 · Outcome O-1, O-3 · Principles P7, P11, P12

---

### BR-004: Privacy and security posture improved through migration

**Description**: The Ultra migration must close the estate's most visible privacy and security gaps: manual re-keying of sensitive information, flat-file personal data on shared storage, local accounts, and 24-hour deprovisioning latency.

**Rationale**: The privacy context document identifies four data flows of concern and two tools permitting local accounts in breach of REQ-031. The Essential Eight self-assessment targets ML2 by end 2027. The migration is the natural moment to enforce SSO/MFA from day one and modernise integration credentials.

**Acceptance Criteria**:

- Zero local accounts on Ultra — SSO/MFA enforced from first day of operation
- All integration credentials using OAuth 2.0 service accounts with scoped permissions, replacing shared credentials in batch scripts
- Deprovisioning latency reduced from 24 hours (nightly batch) to within 15 minutes (event-driven)
- Data migration plan reviewed and approved by Eleanor Frame before execution
- Migration data deleted within 30 days of successful cutover per phase

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE G-1, G-2; REQ-030, REQ-031, REQ-033

**Stakeholder**: Tobias Ohm (security), Eleanor Frame (privacy), Cassandra Rhodes (accountable)

**Traces To**: Goal G-1, G-2 · Outcome O-3 · Principles P7, P12, P16

---

### BR-005: Academic adoption through templates and training

**Description**: The Ultra migration must be accompanied by consistent, accessible templates and a co-designed training programme that positions Ultra as a pedagogical improvement, not a vendor-mandated interface refresh.

**Rationale**: The migration is the one moment when every unit site is being rebuilt. If templates are not ready, academics will recreate their Learn Original structures ad hoc and the consistency outcome from Project 001 is lost. If Ultra is positioned as "the vendor made us" rather than "this improves teaching", academic resistance will be high and adoption grudging.

**Acceptance Criteria**:

- Baseline Ultra template deployed as default for all new and migrated unit sites
- Template adoption rate exceeds 80% in the first teaching period on Ultra
- Template design validated with academic representatives (Castle, Marimba, student representation) before deployment
- Training programme co-designed with academics, delivered through workshops (not solely self-service documentation)
- Academic satisfaction survey conducted post-migration with satisfaction exceeding 70%

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE G-4, CSF-5; REQ-001, REQ-007

**Stakeholder**: Dr. Benny Moog (owner), A/Prof. Pearl Clavinet (approval)

**Traces To**: Goal G-4 · Outcome O-2 · Principles P1, P3, P14

---

### BR-006: Licence cost management through migration

**Description**: Migration and integration re-engineering costs must be quantified and justified against the licence and operational savings the rationalisation roadmap promised, and Ultra licensing terms must be negotiated as part of the migration commitment.

**Rationale**: The September business case was approved on the basis that licence spend would hold flat or reduce while capability gaps were closed. Project 003 is the first major capital draw against that case. If migration costs escalate without corresponding savings materialising, the remainder of the roadmap loses funding credibility.

**Acceptance Criteria**:

- Migration costs separated from ongoing licence costs in the business case
- Ultra licensing terms negotiated as part of the migration commitment, not as a separate renewal
- Savings from eliminated manual effort quantified (placement re-keying, CSV provisioning, course cloning time)
- No unbudgeted premium licensing required for APIs essential to the integration architecture
- Migration plan available with firm timeline and scope before contract negotiation concludes

**Priority**: SHOULD_HAVE

**Source Ref**: ARC-003-STKE SD-9, SD-10; REQ-035

**Stakeholder**: Vernon Ostinato (approval), Grace Tanaka (negotiation)

**Traces To**: Goal G-5 · Outcome O-1 · Principle P19

---

### BR-007: Governance continuity through RIFF and Education Committee

**Description**: All migration and integration decisions must follow the established RIFF Review and Education Committee governance pathway, with architecture decisions recorded as ADRs and assessed against the maintained capability map and principles.

**Rationale**: Project 003 is the first concrete delivery from the L&T Baseline Strategy. Its governance rigour — or lack thereof — sets the precedent for Projects 004 onwards. Solutions duplicating capability already licensed must justify why the incumbent tool is unsuitable, per the RIFF duplication rule.

**Acceptance Criteria**:

- 100% of solution requests assessed against the capability map and principles before commitment
- Integration architecture decisions recorded as ADRs with options analysis and traceability
- Education Committee endorsement obtained for the migration timeline and any change affecting teaching periods
- Faculty sign-off obtained before each faculty's migration phase commences
- Migration exceptions recorded with rationale and time-bound remediation

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE CSF-3; ARC-000-PRIN P18, P19

**Stakeholder**: Dr. Benny Moog (RIFF), A/Prof. Pearl Clavinet (Education Committee)

**Traces To**: Goal G-3, G-4 · Outcome O-2 · Principles P18, P19

---

## Functional Requirements

### User Personas

#### Persona 1: Unit Coordinator (Migration Context)

- **Role**: Academic responsible for design and delivery of one or more units, now migrating from Learn Original to Ultra
- **Goals**: Migrate unit content cleanly; adopt the new Ultra template without excessive rework; clone units in Ultra for the next teaching period; see enrolment data appear promptly
- **Pain Points**: Fear that carefully built unit sites will break in migration; uncertainty about which Learn Original features are available in Ultra; effort to rebuild during teaching; waiting up to 24 hours for enrolment updates
- **Technical Proficiency**: Medium
- **Migration-specific concern**: Content migration fidelity — embedded content, rubric configurations, custom building blocks

#### Persona 2: Student (Migration Context)

- **Role**: Enrolled student, frequently studying across multiple schools, experiencing the Ultra transition
- **Goals**: Find materials, submit work, see grades and feedback without disruption; navigate a consistent interface regardless of which units have migrated
- **Pain Points**: Different navigation between migrated and non-migrated units during transition; broken links or missing content in newly migrated units; grades appearing late
- **Technical Proficiency**: Medium — highly variable; assistive technology users disproportionately affected by interface changes
- **Migration-specific concern**: Dual interface during phased rollout; accessibility of the new Ultra interface

#### Persona 3: Sessional / Casual Academic (Migration Context)

- **Role**: Short-tenure teaching staff, often marking or tutoring, whose provisioning is currently manual
- **Goals**: Get access to the right units promptly in Ultra; mark and provide feedback without learning two interfaces
- **Pain Points**: Manual CSV provisioning means access arrives late or persists after engagement ends; during migration, must learn Ultra while teaching
- **Technical Proficiency**: Medium
- **Migration-specific concern**: Automated provisioning must replace manual CSV as part of the migration, not after it

#### Persona 4: Placement Supervisor (Migration Context)

- **Role**: Clinical or community-sector supervisor assessing students on placement, interacting with the grades flow
- **Goals**: Record assessment outcomes once, without re-keying or university system training
- **Pain Points**: Outcomes currently re-keyed by university staff with errors and delays; sensitive placement information circulating via email exports
- **Technical Proficiency**: Low
- **Migration-specific concern**: The Sonia-to-Ultra grades integration must be automated; the supervisor's workflow should be unchanged or simplified

#### Persona 5: Learning Technologist (Migration Context)

- **Role**: Central support for the L&T platform estate, now managing the migration alongside day-to-day support
- **Goals**: Execute migration phases reliably; support academics through Ultra adoption; configure the new templates; resolve integration issues without firefighting
- **Pain Points**: Dual-running burden — supporting both Learn Original and Ultra simultaneously; undocumented course cloning scripts with single-person dependency; discovering integration failures via user reports
- **Technical Proficiency**: High
- **Migration-specific concern**: Team capacity during dual-running; documented, reproducible migration and cloning processes

---

### Use Cases

#### UC-001: Migrate a unit site from Learn Original to Ultra

**Actor**: Learning Technologist, Unit Coordinator

**Preconditions**:

- Unit site exists in Blackboard Learn Original with published content
- Ultra template has been designed, tested, and approved
- Migration phase window is within an inter-semester period (not during assessment)
- Rollback capability verified for this phase

**Main Flow**:

1. Learning Technologist initiates content migration for a cohort of unit sites using Anthology's migration tooling
2. System migrates content, structure, assessments, and rubrics to Ultra, mapping to the baseline template
3. System generates a migration report identifying items migrated successfully, items requiring manual review, and items that could not be migrated
4. Unit Coordinator reviews the migrated site in Ultra and verifies content integrity
5. Unit Coordinator adjusts content where needed and confirms readiness
6. Learning Technologist marks the unit as migrated and updates the migration register

**Postconditions**:

- Unit site is operational in Ultra with content verified by the coordinator
- Migration report archived for audit
- Learn Original unit site retained in read-only state until cutover confirmation

**Alternative Flows**:

- **Alt 3a**: If custom building blocks or embedded content cannot be migrated, the system flags these for manual remediation and the coordinator is notified with specific items listed
- **Alt 5a**: If the coordinator identifies unacceptable content loss, the migration is rolled back to Learn Original for that unit

**Priority**: CRITICAL

---

#### UC-002: Event-driven enrolment propagation to Ultra

**Actor**: Student (indirect — triggered by SIS enrolment change)

**Preconditions**:

- Student record exists in PeopleSoft
- Unit offering exists in Ultra via the course lifecycle integration
- Integration broker is operational with the canonical ENROLMENT entity registered

**Main Flow**:

1. Student enrols in a unit through the Student Information System
2. PeopleSoft publishes an ENROLMENT change event to the integration broker
3. Broker validates the event against the canonical schema and routes to Ultra
4. Ultra provisions the student with the enrolled-student role for that unit offering
5. Student authenticates through institutional SSO with MFA and accesses the unit within 15 minutes of the enrolment change

**Postconditions**:

- Student holds access appropriate to their enrolment
- Event is logged in the integration monitoring telemetry

**Alternative Flows**:

- **Alt 1a**: If the student withdraws, PeopleSoft publishes a withdrawal event; Ultra revokes access within 15 minutes
- **Alt 3a**: If schema validation fails, the event is routed to a dead-letter queue and an alert is raised to the integration team

**Priority**: CRITICAL

---

#### UC-003: Automated placement grade synchronisation

**Actor**: Placement Supervisor (external), Unit Coordinator

**Preconditions**:

- Student has an active placement allocation in Sonia
- Sonia-to-Ultra integration is operational via the integration broker
- Supervisor is authorised against the placement in Sonia

**Main Flow**:

1. Placement Supervisor records the assessment outcome in Sonia
2. Sonia publishes a grade change event to the integration broker carrying the canonical GRADE entity
3. Broker validates and routes the event to Ultra
4. Ultra updates the gradebook for the relevant unit and student
5. Unit Coordinator sees the outcome in the Ultra gradebook without manual entry
6. Grade propagates to the student record via the existing Ultra-to-PeopleSoft grades flow

**Postconditions**:

- Outcome recorded once and visible in the gradebook and student record
- Full audit trail of who recorded what and when
- No sensitive placement information transferred by email, spreadsheet, or manual re-keying

**Alternative Flows**:

- **Alt 2a**: If Sonia cannot publish events natively, a change-data-capture mechanism polls Sonia for grade changes and publishes to the broker on its behalf

**Priority**: CRITICAL

---

#### UC-004: Discipline tool verification in Ultra

**Actor**: Learning Technologist, Discipline Faculty Staff

**Preconditions**:

- Discipline tool (e.g., MuseScore, Ableton Live, iSimulate, Kuracloud, ExamSoft) is currently integrated with Learn Original via LTI
- Ultra test environment is available with representative discipline content

**Main Flow**:

1. Learning Technologist configures the discipline tool's LTI 1.3 Advantage connection in Ultra
2. System establishes the LTI launch, names-and-roles provisioning, and deep linking
3. Discipline faculty staff test representative workflows — content distribution, assessment submission, grade passback
4. Staff verify that discipline-specific features (interactive notation, audio project distribution, simulation launch) function correctly
5. Faculty Dean signs off on the discipline tool integration before their faculty's migration phase

**Postconditions**:

- Discipline tool verified as fully functional in Ultra
- LTI 1.3 Advantage compliance confirmed
- Faculty sign-off recorded in the migration register

**Alternative Flows**:

- **Alt 3a**: If a discipline tool's LTI implementation does not function correctly in Ultra, the issue is escalated to Anthology and the tool vendor jointly, and the faculty's migration is held until resolved

**Priority**: HIGH

---

#### UC-005: Course cloning in Ultra

**Actor**: Unit Coordinator, Learning Technologist

**Preconditions**:

- Prior teaching period unit site exists in Ultra
- New teaching period unit shell has been created from PeopleSoft via the course lifecycle integration
- Automated cloning process is documented with more than one person able to execute it

**Main Flow**:

1. Unit Coordinator requests rollover through a self-service interface in Ultra
2. System copies structure, content, and configuration to the new unit site, applying the baseline template
3. System excludes prior-period student data, submissions, and grades
4. System logs the operation with actor, timestamp, and scope
5. Coordinator reviews and adjusts the new site

**Postconditions**:

- New unit site conforms to the baseline template
- No prior-period student personal information carried forward
- Operation logged and attributable

**Alternative Flows**:

- **Alt 2a**: If the source site predates the baseline template, the system reports which elements require manual adjustment to conform

**Priority**: HIGH

---

### Functional Requirements Detail

#### Content Migration

##### FR-001: Content migration fidelity

**Description**: All content types present in Learn Original unit sites must be migrated to Ultra with documented fidelity, including text content, embedded media, file attachments, assessment configurations, rubrics, and grade centre settings.

**Rationale**: Content is the product of years of academic effort. Silent loss of content during migration damages trust and creates rework during teaching.

**Acceptance Criteria**:

- Content migration success rate exceeds 95% of items migrated without manual intervention
- Migration report generated per unit site identifying: items migrated successfully, items requiring manual review, items that cannot be migrated
- Custom building blocks and Learn Original-specific features mapped to Ultra equivalents or flagged as requiring manual remediation
- Embedded LTI content links updated to Ultra LTI 1.3 endpoints
- Grade centre configurations preserved or mapped to Ultra's gradebook structure

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE SD-6, G-3; REQ-007

**Stakeholder**: Dr. Wynton Castle (validation), Dr. Benny Moog (delivery)

**Traces To**: Goal G-3 · Outcome O-2 · Principle P1

---

##### FR-002: Migration rollback capability

**Description**: Each migration phase must have a verified rollback capability that restores the affected unit sites to their Learn Original state without data loss.

**Rationale**: A migration without rollback is a one-way bet. CSF-1 requires that no teaching period is disrupted; rollback is the safety net that makes phased migration safe.

**Acceptance Criteria**:

- Rollback procedure documented and tested before each phase commences
- Rollback executable within 4 hours of a go/no-go decision
- Learn Original unit sites retained in read-only state until cutover confirmation for that phase
- Rollback does not affect units already migrated and confirmed in prior phases
- Rollback test results recorded and reviewed at the phase go/no-go gate

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE G-3, R-1; REQ-032

**Stakeholder**: Rhonda Bell (delivery), Sam Okafor (integration rollback)

**Traces To**: Goal G-3 · Outcome O-2 · Principle P13

---

##### FR-003: Content migration testing on representative sites

**Description**: Content migration must be tested on representative unit sites from each faculty — including discipline-specific content — before the migration phase for that faculty commences.

**Rationale**: Generic testing does not catch discipline-specific content failures. Castle's carefully built unit sites, Key's interactive notation, and Anand's clinical simulation links all require verified migration paths.

**Acceptance Criteria**:

- At least two representative unit sites per faculty tested before that faculty's migration phase
- Music & Performing Arts sites tested for interactive notation and audio-production project files
- Health Sciences sites tested for clinical simulation scenario links and placement-related content
- Test results documented and reviewed with the relevant faculty Dean or academic lead
- Issues discovered in testing resolved before the faculty's migration phase proceeds

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE SD-6, SD-12, G-6; REQ-005, REQ-006

**Stakeholder**: Dr. Wynton Castle, Prof. Desmond Key, Prof. Priya Anand

**Traces To**: Goal G-3, G-6 · Outcome O-2 · Principles P1, P4

---

#### Template and Configuration

##### FR-004: Ultra baseline template design

**Description**: A baseline Ultra unit site template must be designed and deployed that delivers consistent structure, navigation, and accessibility across all schools, making template conformance the path of least resistance for academics.

**Rationale**: The migration is the one moment when every unit site is being rebuilt. Consistent templates reduce student cognitive load across units and ensure accessibility by default rather than by individual effort.

**Acceptance Criteria**:

- Baseline template provides consistent top-level structure and terminology across all unit sites
- Template meets WCAG 2.2 AA conformance (verified by accessibility audit before deployment)
- Template validated with academic representatives including Castle, Marimba, and student representation (Field)
- Template deployed as the default for all new and migrated unit sites
- Template permits pedagogical variation where justified, with variation recorded

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE G-4; REQ-001, REQ-029

**Stakeholder**: Dr. Benny Moog (owner), A/Prof. Pearl Clavinet (approval)

**Traces To**: Goal G-4 · Outcome O-2 · Principles P3, P14

---

##### FR-005: Ultra mobile responsiveness

**Description**: The Ultra configuration and baseline template must deliver a responsive experience on mobile devices, given Ultra's mobile-first design.

**Rationale**: Ultra is designed as a responsive platform. The template must leverage this rather than constrain it. Students increasingly access course materials from mobile devices.

**Acceptance Criteria**:

- Baseline template renders correctly and is fully navigable on screen widths from 320px upward
- All assessment submission and grade viewing functions accessible on mobile
- Template tested on iOS and Android devices with representative content before deployment

**Priority**: SHOULD_HAVE

**Source Ref**: ARC-003-STKE G-4; REQ-007

**Stakeholder**: Jazmin Field (student perspective), Dr. Benny Moog (configuration)

**Traces To**: Goal G-4 · Outcome O-2 · Principles P1, P14

---

##### FR-006: Ultra SSO/MFA configuration

**Description**: Ultra must be configured to require institutional single sign-on with multi-factor authentication for all user access, with no local account creation permitted.

**Rationale**: Two tools in the current estate still allow local accounts, breaching REQ-031. The migration to Ultra is the opportunity to enforce SSO/MFA from day one with no grandfather clause.

**Acceptance Criteria**:

- Ultra configured with institutional SSO as the sole authentication method
- MFA enforced for all user sessions — no bypass for admin or integration access
- Local account creation disabled in Ultra configuration
- Configuration verified by Tobias Ohm before Ultra go-live
- No user able to authenticate to Ultra without passing through institutional SSO/MFA

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE SD-8, G-1; REQ-031

**Stakeholder**: Tobias Ohm (verification), Sam Okafor (configuration)

**Traces To**: Goal G-1 · Outcome O-3 · Principles P12, P16

---

#### Integration Re-engineering

##### FR-007: Canonical data model implementation

**Description**: The canonical data model defined in ARC-001-DATA-v1.0 must be implemented as the integration contract for all seven integrations, with entities registered in the schema registry of the integration broker.

**Rationale**: ADR-001 selected a central integration broker specifically to enforce the canonical model at runtime. CSF-3 requires the model is implemented, not bypassed for expedience. The six canonical entities — PERSON, UNIT, TEACHING_PERIOD, UNIT_OFFERING, ENROLMENT, INSTITUTIONAL_ROLE_ASSIGNMENT — are the integration surface.

**Acceptance Criteria**:

- All six canonical entities registered in the integration broker's schema registry
- Every integration publishes and consumes against the canonical schema
- Schema validation rejects non-conformant events (they do not pass silently)
- Schema versioning process established for governed evolution of the canonical model
- No integration bypasses the canonical model through direct database coupling or bespoke point-to-point exchange

**Priority**: MUST_HAVE

**Source Ref**: ADR-001; ARC-001-DATA-v1.0; REQ-027

**Stakeholder**: Sam Okafor (owner)

**Traces To**: Goal G-1 · Outcome O-1 · Principles P5, P6, P10

---

##### FR-008: Event-driven identity and enrolment lifecycle

**Description**: The PeopleSoft-to-Ultra integration must be re-engineered to publish identity, enrolment, and course lifecycle changes as events to the integration broker, replacing the nightly flat-file with near-real-time propagation.

**Rationale**: This is the estate's most consequential data flow. Every other integration depends on users and courses being correct. The nightly batch means access and role state are wrong for up to 24 hours.

**Acceptance Criteria**:

- PeopleSoft publishes PERSON, UNIT, UNIT_OFFERING, and ENROLMENT change events to the broker
- Ultra consumes these events and provisions or deprovisions users within 15 minutes of the source change
- Nightly flat-file process decommissioned after the event-driven flow has run one full teaching period
- Event processing handles bulk operations (e.g., start-of-semester enrolment wave) within acceptable throughput (per NFR-P-002)
- Failed events routed to dead-letter queue with monitoring alerts

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE G-1, CSF-2; ADR-001 Phase 3; REQ-023

**Stakeholder**: Sam Okafor (delivery), Student Administration (PeopleSoft side)

**Traces To**: Goal G-1 · Outcome O-1 · Principles P5, P11, P12

---

##### FR-009: Automated user provisioning for supporting platforms

**Description**: User provisioning for Echo360, and other supporting platforms currently using manual CSV, must be automated through the canonical model and integration broker or through LTI 1.3 Advantage Names and Role Provisioning Services.

**Rationale**: Manual CSV provisioning is simultaneously a privacy exposure (CSV extracts of the student cohort handled manually) and an integration defect (access arriving late for casual staff). Principle 12 prohibits manual role assignment in production.

**Acceptance Criteria**:

- Echo360 user provisioning automated via LTI 1.3 Names and Role Provisioning Services or via canonical PERSON/ENROLMENT events from the broker
- Zero CSV-based provisioning events per month for any supporting platform
- Casual and sessional academic provisioning on the same automated path as permanent staff
- Provisioning latency within 15 minutes of the source enrolment or role change

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE G-2; REQ-025

**Stakeholder**: Sam Okafor (delivery), Dr. Benny Moog (platform configuration)

**Traces To**: Goal G-2 · Outcome O-1, O-3 · Principles P11, P12

---

##### FR-010: Automated course cloning and rollover

**Description**: Course cloning and rollover must be automated as a self-service, logged process in Ultra, executable by more than one person and not dependent on undocumented scripts.

**Rationale**: The current course cloning process has a single-person dependency (one of the estate's most documented fragility points). Principle 13 requires reproducible, documented automation. The migration to Ultra is the moment to replace the undocumented scripts.

**Acceptance Criteria**:

- Course cloning available as a self-service function in Ultra for unit coordinators
- Process documented with version-controlled runbook and at least two people trained to support it
- Cloning operation logged with actor, timestamp, scope, and outcome
- Prior-period student data, submissions, and grades excluded from cloned sites
- Cloned sites conform to the baseline template

**Priority**: SHOULD_HAVE

**Source Ref**: ARC-003-STKE G-3; REQ-026

**Stakeholder**: Dr. Wynton Castle (user), Dr. Benny Moog (configuration)

**Traces To**: Goal G-3, G-4 · Outcome O-2 · Principles P13, P3

---

#### Training and Adoption

##### FR-011: Academic training programme for Ultra

**Description**: A structured training programme must be delivered to all academic staff before their faculty migrates, covering Ultra navigation, template usage, content authoring, assessment configuration, and differences from Learn Original.

**Rationale**: Training available only as self-service documentation is a documented blocker for Castle. Academic resistance to Ultra will be highest where the interface change feels imposed without support.

**Acceptance Criteria**:

- Training delivered through workshops with hands-on Ultra sandbox access, not solely self-service documentation
- Training programme co-designed with Dr. Felix Marimba and Dr. Wynton Castle
- Training delivered to each faculty before their migration phase commences
- Training covers Ultra-specific workflows, template usage, assessment configuration, and automated course cloning
- Attendance and feedback recorded; feedback used to refine training for subsequent phases

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE SD-4, SD-6, CSF-5

**Stakeholder**: Dr. Felix Marimba (co-design), Dr. Benny Moog (delivery)

**Traces To**: Goal G-3, G-4 · Outcome O-2 · Principles P1, P3

---

##### FR-012: Pilot programme with willing academics

**Description**: A pilot programme must be conducted with willing academics before full rollout, testing content migration, Ultra usability, template design, and integration behaviour on representative unit sites.

**Rationale**: CSF-5 requires academics to experience the migration as effort reduction rather than mandated rework. The pilot validates this before the wider community is exposed.

**Acceptance Criteria**:

- Pilot cohort includes willing academics from at least three faculties, including representatives from Music & Performing Arts and Health Sciences
- Pilot includes Dr. Wynton Castle as a Learn Original power user
- Student Guild representative (or delegate) included in the pilot for student experience validation
- Pilot satisfaction rating exceeds 80%
- Pilot issues documented and remediated before full rollout commences

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE G-3, G-4, CSF-5

**Stakeholder**: A/Prof. Pearl Clavinet (approval), Dr. Benny Moog (delivery)

**Traces To**: Goal G-3, G-4 · Outcome O-2 · Principles P1, P3

---

##### FR-013: Student communication plan

**Description**: A student communication plan must be developed and executed for each migration phase, informing students of the transition timeline, what will change, and where to get support.

**Rationale**: Students routinely bear the consequences of technology change as broken links, inaccessible materials, and grade confusion. Field's advocacy is that students should not bear the cost of a migration they did not request.

**Acceptance Criteria**:

- Communication issued to affected students at least two weeks before each migration phase
- Communication explains what is changing, what is not, and where to get help
- Student Guild consulted on communication content and channels
- Support channels staffed during the first two weeks after each migration phase
- No migration occurs without prior student communication

**Priority**: SHOULD_HAVE

**Source Ref**: ARC-003-STKE SD-13

**Stakeholder**: Jazmin Field (consultation), Dr. Felix Marimba (communications)

**Traces To**: Goal G-3 · Outcome O-2 · Principle P1

---

##### FR-014: Discipline tool LTI verification

**Description**: All discipline-specific tools currently integrated via LTI must be verified as functional in Ultra before the faculties using them are migrated, with LTI 1.3 Advantage compliance confirmed.

**Rationale**: Principle 4 protects discipline specialisation at the edge, but the protection is only real if the integrations work in Ultra as they do in Learn Original. A broken LTI integration in Ultra will be perceived as the consolidation that Project 001's governance process was supposed to prevent.

**Acceptance Criteria**:

- MuseScore, Ableton Live, iSimulate, Kuracloud, and ExamSoft verified in Ultra test environment
- LTI 1.3 Advantage compliance confirmed for each tool: launch, Names and Role Provisioning, Assignment and Grade Services, Deep Linking
- Discipline faculty staff conduct representative workflow tests
- Faculty Dean signs off before their faculty's migration phase
- Issues escalated to Anthology and tool vendors jointly, with resolution tracked

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE G-6, SD-12; REQ-005, REQ-006

**Stakeholder**: Prof. Desmond Key (Music), Prof. Priya Anand (Health Sciences), Dr. Benny Moog (LTI configuration)

**Traces To**: Goal G-6 · Outcome O-2 · Principles P4, P10

---

##### FR-015: Institutional hierarchy synchronisation

**Description**: The institutional hierarchy in Ultra must be synchronised from PeopleSoft through the canonical data model, replacing the current manual update process.

**Rationale**: Manual hierarchy updates cause drift between PeopleSoft and Blackboard, affecting reporting, navigation, and role scoping. Event-driven synchronisation ensures the hierarchy is always current.

**Acceptance Criteria**:

- Institutional hierarchy changes in PeopleSoft published as events to the integration broker
- Ultra hierarchy updated within 15 minutes of a PeopleSoft change
- No manual hierarchy update required in production
- Hierarchy drift between PeopleSoft and Ultra eliminated — reconciliation confirms zero discrepancies per teaching period

**Priority**: SHOULD_HAVE

**Source Ref**: ARC-003-STKE G-2; system-landscape.md integration 4

**Stakeholder**: Sam Okafor (delivery), Student Administration (PeopleSoft side)

**Traces To**: Goal G-1, G-2 · Outcome O-1 · Principles P5, P11

---

## Non-Functional Requirements

### Performance

#### NFR-P-001: Change propagation latency

**Description**: Changes to identity, enrolment, role, and course lifecycle data in the source system must propagate to Ultra and all consuming platforms within 15 minutes.

**Rationale**: The nightly batch means access and role state are wrong for up to 24 hours. This is simultaneously an operational defect (students cannot access enrolled units) and a privacy defect (access persists up to 24 hours after withdrawal). The 15-minute target is set by ARC-001-DATA's governance matrix for E-006 freshness.

**Acceptance Criteria**:

- 95th percentile propagation latency from PeopleSoft change to Ultra effect is within 15 minutes
- Propagation latency measured end-to-end via integration monitoring telemetry
- Latency target applies to: PERSON changes, ENROLMENT changes, UNIT_OFFERING changes, INSTITUTIONAL_ROLE_ASSIGNMENT changes
- Deprovisioning (access revocation on withdrawal or role end) meets the same 15-minute target

**Priority**: MUST_HAVE

**Source Ref**: ARC-001-DATA governance matrix; ADR-001; REQ-023

**Stakeholder**: Sam Okafor (measurement), Tobias Ohm (deprovisioning)

**Traces To**: Goal G-1 · Outcome O-1, O-3 · Principles P11, P12

---

#### NFR-P-002: Content migration throughput

**Description**: The content migration process must be capable of migrating a full faculty's unit sites within a single inter-semester window.

**Rationale**: Migration phases are constrained to inter-semester windows (typically 3 to 4 weeks). If migration throughput cannot complete a faculty within that window, the migration timeline extends and dual-running burden increases.

**Acceptance Criteria**:

- Migration tooling benchmarked on representative content volumes before the first migration phase
- A full faculty's unit sites (estimated 200-400 units depending on faculty) completable within the inter-semester window
- Migration can be parallelised to handle multiple units simultaneously
- Throughput verified during pilot testing

**Priority**: SHOULD_HAVE

**Source Ref**: ARC-003-STKE G-3

**Stakeholder**: Rhonda Bell (scheduling), Dr. Benny Moog (tooling)

**Traces To**: Goal G-3 · Outcome O-2

---

#### NFR-P-003: Ultra page load performance

**Description**: Ultra unit site pages must load within acceptable performance thresholds for students and staff.

**Rationale**: A migration that improves the LMS interface but degrades performance will undermine academic adoption.

**Acceptance Criteria**:

- Ultra unit site pages load within 3 seconds on a standard institutional network connection
- Performance verified with representative content volumes (not empty test sites)
- Performance baseline established during pilot and monitored post-migration
- Performance degradation exceeding 20% from baseline triggers investigation

**Priority**: SHOULD_HAVE

**Source Ref**: REQ-007

**Stakeholder**: Dr. Benny Moog (monitoring)

**Traces To**: Goal G-3 · Outcome O-2 · Principle P1

---

### Availability

#### NFR-A-001: LMS availability during teaching periods

**Description**: Blackboard Ultra must meet 99.9% availability during teaching periods, consistent with the availability target for core teaching platforms.

**Rationale**: The LMS is the single entry point for all unit materials, activities, and grades. Unavailability during teaching directly affects every student and academic.

**Acceptance Criteria**:

- 99.9% availability during teaching periods (equates to a maximum of approximately 8.7 hours downtime per year during teaching)
- Availability measured against Anthology's SLA and verified through institutional monitoring
- Planned maintenance scheduled outside teaching periods wherever possible
- Availability incidents during teaching periods recorded, attributed, and reviewed at steering

**Priority**: MUST_HAVE

**Source Ref**: REQ-032

**Stakeholder**: Cassandra Rhodes (accountable), Dr. Benny Moog (monitoring)

**Traces To**: Goal G-3 · Outcome O-2 · Principle P1

---

#### NFR-A-002: Migration rollback availability

**Description**: Rollback capability must be maintained and verified for each migration phase until the migrated units have been confirmed operational in Ultra for at least one teaching period.

**Rationale**: Rollback is the safety mechanism that makes phased migration viable. If rollback is unavailable or untested, a migration failure during teaching has no recovery path.

**Acceptance Criteria**:

- Learn Original unit sites retained in read-only state throughout the rollback window
- Rollback procedure tested before each phase go/no-go gate
- Rollback executable within 4 hours
- Rollback window extends until the migrated units complete one full teaching period in Ultra

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE G-3, R-1

**Stakeholder**: Rhonda Bell (delivery), Sam Okafor (integration state)

**Traces To**: Goal G-3 · Outcome O-2 · Principle P13

---

#### NFR-A-003: Integration broker availability

**Description**: The integration broker must meet availability targets consistent with the estate's teaching-period requirements, with per-integration degradation rather than estate-wide failure.

**Rationale**: ADR-001 accepted a new shared runtime dependency. NFR-A-001 requires it not to become the estate's weakest point. Per-integration degradation means a failure in one integration does not cascade to all.

**Acceptance Criteria**:

- Broker availability meets or exceeds 99.9% during teaching periods
- Failure in one integration's processing does not block other integrations
- Broker outage does not cause data loss — events buffered at the edge and replayed on recovery
- Availability design completed and reviewed before the first integration cuts over (per ADR-001 Condition 2)

**Priority**: MUST_HAVE

**Source Ref**: ADR-001 Condition 2

**Stakeholder**: Sam Okafor (design and operation)

**Traces To**: Goal G-1 · Outcome O-1 · Principles P10, P17

---

### Security

#### NFR-SEC-001: SSO/MFA enforcement — no local accounts

**Description**: All user authentication to Ultra must use institutional single sign-on with multi-factor authentication. No local account creation is permitted.

**Rationale**: Two tools in the current estate still allow local accounts, breaching REQ-031 and the Essential Eight MFA mitigation strategy. The migration to Ultra closes this gap from day one.

**Acceptance Criteria**:

- Ultra configured with institutional SSO/MFA as the sole authentication method
- Local account creation disabled at the platform configuration level
- No admin, test, or integration user authenticated via a local account
- Configuration verified by Tobias Ohm before Ultra go-live
- Annual audit confirms zero local accounts

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE SD-8; REQ-031; privacy-context.md section 3

**Stakeholder**: Tobias Ohm (verification)

**Traces To**: Goal G-1 · Outcome O-3 · Principles P12, P16

---

#### NFR-SEC-002: OAuth 2.0 service credentials for integrations

**Description**: All service-to-service integration credentials must use OAuth 2.0 with scoped permissions, replacing shared credentials in batch scripts.

**Rationale**: Legacy integration scripts use shared credentials that work against the ML2 target for restricting administrative privileges. OAuth 2.0 service accounts provide scoped, auditable, rotatable credentials.

**Acceptance Criteria**:

- Every integration authenticates using OAuth 2.0 client credentials with scoped permissions
- No shared password or API key in any integration configuration
- Credentials rotatable without service interruption
- Credential usage logged and auditable
- Test environments use dedicated test credentials — never production credentials

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE SD-8; REQ-033; ADR-001

**Stakeholder**: Tobias Ohm (standards), Sam Okafor (implementation)

**Traces To**: Goal G-1 · Outcome O-3 · Principles P16, P17

---

#### NFR-SEC-003: Automated identity lifecycle — deprovisioning

**Description**: When a person's enrolment ends or their role is removed, their access must be revoked automatically within 15 minutes without manual intervention.

**Rationale**: The current nightly batch means access persists up to 24 hours after withdrawal — a standing APP 11 exposure. Event-driven deprovisioning makes revocation a direct consequence of the authoritative source change.

**Acceptance Criteria**:

- Access revoked within 15 minutes of the source change (enrolment withdrawal, role end, appointment end)
- Deprovisioning applies to Ultra and all integrated platforms receiving identity/role events
- Casual and sessional academic deprovisioning on the same automated path as permanent staff
- No manual CSV or flat-file step in the deprovisioning process
- Deprovisioning events logged with timestamp, actor (system), and prior state

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE G-1, G-2; REQ-031; privacy-context.md section 2

**Stakeholder**: Tobias Ohm (verification), Eleanor Frame (APP compliance)

**Traces To**: Goal G-1, G-2 · Outcome O-3 · Principles P7, P12, P16

---

#### NFR-SEC-004: Migration data access control

**Description**: Access to data during migration — bulk exports from Learn Original, transformation environments, and import staging — must be restricted to authorised migration team members with elevated controls for sensitive data classes.

**Rationale**: Bulk data migration creates temporary copies of personal information. Without explicit access restriction, the migration itself becomes a privacy and security exposure.

**Acceptance Criteria**:

- Migration environment access restricted to named individuals on the migration team
- Access logged and auditable
- Sensitive data classes (placement records including clearance metadata and health-context notes) handled under elevated controls with Frame's sign-off per batch
- Migration data not copied to non-restricted locations (personal devices, shared drives, email)
- Migration data deleted within 30 days of successful cutover for each phase

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE SD-7, R-6

**Stakeholder**: Eleanor Frame (sign-off), Tobias Ohm (controls)

**Traces To**: Goal G-2 · Outcome O-3 · Principles P7, P16

---

### Compliance

#### NFR-C-001: Privacy Act 1988 — Australian Privacy Principles

**Description**: All data handling during and after migration must comply with the Privacy Act 1988 and the Australian Privacy Principles, with particular attention to APP 6 (use and disclosure), APP 8 (cross-border disclosure), and APP 11 (security of personal information).

**Rationale**: Four data classes involve offshore disclosure triggering APP 8 assessment. Sensitive placement information requires elevated controls. The data migration creates new handling that must be assessed under the APPs.

**Acceptance Criteria**:

- Privacy Impact Assessment completed and approved by Eleanor Frame before migration commences
- All eight personal information classes assessed for APP compliance during and after migration
- Cross-border disclosure position confirmed for Ultra hosting — Australian region confirmed, or cross-border position formally assessed and accepted
- Data minimisation applied to migration — only data required for Ultra operation migrated, not historical data retained beyond defined retention periods
- Sensitive placement data (clearance metadata, health-context notes) handled under elevated controls throughout migration

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE SD-7; REQ-030; privacy-context.md

**Stakeholder**: Eleanor Frame (owner)

**Traces To**: Goal G-2 · Outcome O-3 · Principle P7

---

#### NFR-C-002: ASD Essential Eight — ML2 target

**Description**: The migration and integration re-engineering must advance the L&T estate toward the ML2 target set by Digital & IT for end 2027, particularly for multi-factor authentication, restricting administrative privileges, and patching applications.

**Rationale**: The Essential Eight self-assessment identifies MFA exceptions and local accounts as the L&T estate's most visible security gap. The migration directly addresses MFA enforcement and credential modernisation.

**Acceptance Criteria**:

- MFA enforcement on Ultra closes the local-account exception (advancing MFA from current state toward ML2)
- Integration credentials modernised to OAuth 2.0 service accounts (advancing Restrict Administrative Privileges toward ML2)
- Essential Eight posture re-assessed after migration completion, with improvement documented
- No new Essential Eight exceptions introduced by the migration

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE SD-8; REQ-033; privacy-context.md section 3

**Stakeholder**: Tobias Ohm (assessment), Cassandra Rhodes (target owner)

**Traces To**: Goal G-1 · Outcome O-3 · Principle P16

---

#### NFR-C-003: Data migration privacy controls

**Description**: The data migration from Learn Original to Ultra must be conducted under explicit privacy controls covering minimisation, retention, access restriction, and defined deletion timelines.

**Rationale**: Bulk export of student data from Learn Original, transformation, and import into Ultra creates temporary copies of personal information that must be governed under the Privacy Act.

**Acceptance Criteria**:

- Data migration plan reviewed and approved by Eleanor Frame before execution
- Migration data minimised — only data required for Ultra operation included
- Migration environment access-restricted to named individuals
- Migration data retained only for the duration required — deleted within 30 days of successful cutover per phase
- Sensitive data classes (placement records) handled under elevated controls with Frame's sign-off per batch
- Data migration audit log maintained showing what was migrated, by whom, and when

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE SD-7, R-6

**Stakeholder**: Eleanor Frame (approval), Sam Okafor (implementation)

**Traces To**: Goal G-2 · Outcome O-3 · Principle P7

---

### Usability

#### NFR-U-001: WCAG 2.2 AA conformance

**Description**: All student-facing and staff-facing Ultra content, templates, and integrated tools must conform to WCAG 2.2 Level AA.

**Rationale**: Accessibility conformance carries legal and ethical weight. Principle 14 requires accessibility by default, not as an afterthought. The migration must not introduce accessibility regressions.

**Acceptance Criteria**:

- Baseline Ultra template verified for WCAG 2.2 AA conformance before deployment
- Accessibility audit conducted on representative migrated content
- Accessibility regressions identified in migrated content flagged for remediation
- Integrated tools (via LTI) assessed for accessibility conformance, with gaps owned and tracked
- Accessibility testing includes assistive technology users where possible

**Priority**: MUST_HAVE

**Source Ref**: REQ-029; ARC-000-PRIN P14

**Stakeholder**: Dr. Benny Moog (template), Jazmin Field (student experience)

**Traces To**: Goal G-4 · Outcome O-2 · Principle P14

---

#### NFR-U-002: Ultra mobile responsiveness

**Description**: Ultra must deliver a responsive, functional experience on mobile devices for both students and staff.

**Rationale**: Ultra's mobile-first design is a potential improvement over Learn Original. The migration should leverage this capability, not constrain it through poor template or configuration choices.

**Acceptance Criteria**:

- All core student functions (access materials, submit work, view grades, participate in discussions) functional on mobile devices
- Staff functions (marking, feedback, gradebook) accessible on tablet and mobile
- Responsive behaviour tested across iOS and Android devices with representative content
- Performance on mobile networks within acceptable thresholds

**Priority**: SHOULD_HAVE

**Source Ref**: REQ-007

**Stakeholder**: Jazmin Field (student), Dr. Benny Moog (configuration)

**Traces To**: Goal G-4 · Outcome O-2 · Principles P1, P14

---

### Maintainability

#### NFR-M-001: Integration observability

**Description**: All integrations must be observable through a single monitoring plane, with failures detected by monitoring and alerted to named owners rather than discovered by user report.

**Rationale**: Currently there is no central view of integration health — failures surface as user complaints. ADR-001 selected a central integration broker partly to deliver single-plane observability.

**Acceptance Criteria**:

- Single dashboard showing the health, latency, throughput, and error rate of all seven integrations
- Failed events visible with source, timestamp, error class, and affected entities
- Alerts routed to named owners within 5 minutes of a detected failure
- Dead-letter queue visible and actionable — failed events can be inspected and replayed
- Integration health metrics available for steering committee reporting

**Priority**: MUST_HAVE

**Source Ref**: ADR-001; REQ-027; ARC-000-PRIN P17

**Stakeholder**: Sam Okafor (owner)

**Traces To**: Goal G-1, G-5 · Outcome O-1 · Principle P17

---

#### NFR-M-002: Integration documentation and runbooks

**Description**: Every integration must have a documented design, a version-controlled runbook, and at least two people able to operate and troubleshoot it.

**Rationale**: The current course cloning process has a single-person dependency and undocumented scripts — one of the estate's most documented fragility points. Principle 13 requires reproducible, documented automation. ADR-002 Condition 4 makes this a hard gate for the role authority service.

**Acceptance Criteria**:

- Every integration has a documented design in the project's architecture repository
- Every integration has a version-controlled runbook covering: normal operation, common failure modes, escalation, rollback
- At least two named individuals can operate and troubleshoot each integration
- No integration depends on undocumented scripts or single-person knowledge
- Documentation reviewed and updated at each integration change

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE G-5; ADR-002 Condition 4; ARC-000-PRIN P13

**Stakeholder**: Sam Okafor (owner), Cassandra Rhodes (capacity)

**Traces To**: Goal G-5 · Outcome O-1 · Principle P13

---

#### NFR-M-003: Integration change logging with prior value

**Description**: All integration change events must be logged with the prior value, the new value, the source, and the timestamp, creating an auditable history of every state change.

**Rationale**: Role change equals access change — this is the estate's highest-value audit target. ARC-001-DATA's governance matrix requires change logging with prior value for all entities, particularly E-006 (INSTITUTIONAL_ROLE_ASSIGNMENT).

**Acceptance Criteria**:

- Every change event processed through the integration broker logged with: entity, prior value, new value, source system, timestamp
- Logs retained for the period required by the university's records retention policy
- Logs queryable for subject access requests and breach investigation
- Conflicting assertions from different source systems logged and resolved per documented rules

**Priority**: MUST_HAVE

**Source Ref**: ARC-001-DATA governance matrix; ARC-000-PRIN P17

**Stakeholder**: Eleanor Frame (audit), Tobias Ohm (security)

**Traces To**: Goal G-1 · Outcome O-1, O-3 · Principles P7, P17

---

### Interoperability

#### NFR-I-001: Published, versioned API standards

**Description**: All integration interfaces must be published and versioned, with breaking changes governed through the schema change process.

**Rationale**: Point-to-point integrations rarely produce versioned contracts. The canonical model enforced by the broker is a runtime contract, and its evolution needs the same versioning discipline as any API.

**Acceptance Criteria**:

- Integration interfaces documented in a published API catalogue
- Schema versions tracked in the broker's schema registry
- Breaking changes to the canonical schema require RIFF approval before deployment
- Backward-compatible changes documented and communicated to all consumers before deployment
- Interface documentation maintained as part of the integration runbook (per NFR-M-002)

**Priority**: MUST_HAVE

**Source Ref**: ADR-001; ARC-000-PRIN P10

**Stakeholder**: Sam Okafor (owner)

**Traces To**: Goal G-1 · Outcome O-1 · Principles P10, P13

---

#### NFR-I-002: LTI 1.3 Advantage for tool integration

**Description**: All tool integrations with Ultra must use LTI 1.3 Advantage (including Names and Role Provisioning Services, Assignment and Grade Services, and Deep Linking) as the standard integration mechanism.

**Rationale**: LTI 1.3 Advantage is the industry standard for LMS tool integration. Ultra supports it natively. Using a standard integration mechanism reduces coupling to any single vendor and supports Principle 10 (Interface-Mediated Integration).

**Acceptance Criteria**:

- All discipline tools and supporting platforms integrated via LTI 1.3 Advantage where technically supported
- LTI 1.3 Advantage services verified for each tool: launch, Names and Role Provisioning, Assignment and Grade Services, Deep Linking
- Tools that cannot support LTI 1.3 Advantage documented with a migration path or justified exception
- No integration using LTI 1.1 in the target state unless the tool vendor has no LTI 1.3 capability and a dated upgrade commitment is obtained

**Priority**: SHOULD_HAVE

**Source Ref**: ARC-000-PRIN P10; REQ-005, REQ-006

**Stakeholder**: Dr. Benny Moog (configuration), Sam Okafor (standards)

**Traces To**: Goal G-6 · Outcome O-2 · Principles P4, P10

---

## Integration Requirements

### INT-001: PeopleSoft to Ultra — User and Course Lifecycle

| Field | Value |
|-------|-------|
| **ID** | INT-001 |
| **Priority** | MUST_HAVE |
| **Current State** | Nightly batch flat-file from PeopleSoft to Blackboard Learn Original. Fragile; role assignment failures; no intra-day sync. Flat files at rest on shared storage carrying personal information. Access persists up to 24 hours after withdrawal. |
| **Target State** | Event-driven, near-real-time propagation of PERSON, UNIT, TEACHING_PERIOD, UNIT_OFFERING, and ENROLMENT changes from PeopleSoft through the integration broker to Ultra. |
| **Data Exchanged** | Canonical entities: PERSON, UNIT, TEACHING_PERIOD, UNIT_OFFERING, ENROLMENT |
| **Direction** | PeopleSoft → Broker → Ultra (primarily); grade passback Ultra → PeopleSoft for assessment results |
| **Authentication** | OAuth 2.0 service accounts with scoped permissions for both PeopleSoft event publication and Ultra consumption |
| **Latency Target** | < 15 minutes from source change to platform effect |
| **Availability** | 99.9% during teaching periods; failed events buffered and replayed on recovery |
| **Source Ref** | REQ-023; ADR-001 Phase 3; ARC-003-STKE G-1 |
| **Stakeholder** | Sam Okafor (delivery), Student Administration (PeopleSoft side) |
| **Traces To** | Goal G-1 · Outcome O-1, O-3 · Principles P5, P6, P10, P11, P12 |
| **Dependencies** | ADR-002 resolved (authoritative source for role assignment confirmed); integration broker operational (ADR-001); PeopleSoft capable of emitting change events or change-data-capture mechanism available |
| **Acceptance Criteria** | Events published and consumed for all five canonical entities; propagation latency within 15 minutes; flat-file process decommissioned after one full teaching period on event-driven flow; zero manual intervention for standard lifecycle events |

---

### INT-002: Echo360 User Provisioning

| Field | Value |
|-------|-------|
| **ID** | INT-002 |
| **Priority** | MUST_HAVE |
| **Current State** | LTI launch plus manual CSV for casual academic staff. CSV extracts of the student cohort handled manually — a privacy exposure under APP 11. |
| **Target State** | Automated provisioning via LTI 1.3 Names and Role Provisioning Services from Ultra, or via canonical PERSON/ENROLMENT events from the integration broker. Zero CSV loads. |
| **Data Exchanged** | Canonical entities: PERSON, ENROLMENT, INSTITUTIONAL_ROLE_ASSIGNMENT |
| **Direction** | Ultra → Echo360 (LTI provisioning) or Broker → Echo360 (event-driven provisioning) |
| **Authentication** | OAuth 2.0 / LTI 1.3 security model (platform-tool key pair) |
| **Latency Target** | < 15 minutes from enrolment or role change to Echo360 access |
| **Availability** | Provisioning available during teaching periods; degraded provisioning (LTI launch-time) acceptable if broker is temporarily unavailable |
| **Source Ref** | REQ-025; ARC-003-STKE G-2 |
| **Stakeholder** | Sam Okafor (delivery), Dr. Benny Moog (Echo360 configuration) |
| **Traces To** | Goal G-2 · Outcome O-1, O-3 · Principles P11, P12 |
| **Dependencies** | INT-001 operational (provides the identity and enrolment events); Echo360 LTI 1.3 Advantage capability confirmed |
| **Acceptance Criteria** | Zero CSV-based provisioning events per month; casual and sessional academics provisioned on the same automated path; provisioning latency within 15 minutes |

---

### INT-003: Course Cloning Automation

| Field | Value |
|-------|-------|
| **ID** | INT-003 |
| **Priority** | SHOULD_HAVE |
| **Current State** | Semi-manual scripts with a single-person dependency. Undocumented. One of the estate's most documented fragility points. |
| **Target State** | Self-service course cloning in Ultra, automated and logged, with documented runbook and at least two trained operators. Cloned sites conform to the baseline template. |
| **Data Exchanged** | Course structure, content, configuration (internal to Ultra); triggered by UNIT_OFFERING creation from PeopleSoft |
| **Direction** | Internal to Ultra, triggered by events from the broker |
| **Authentication** | Ultra service account with scoped permissions for course operations |
| **Latency Target** | Cloning completed within 10 minutes of coordinator request; triggered by UNIT_OFFERING creation event within 15 minutes of PeopleSoft change |
| **Availability** | Available during the rollover window (inter-semester); not required during assessment periods |
| **Source Ref** | REQ-026; ARC-003-STKE G-3 |
| **Stakeholder** | Dr. Wynton Castle (user), Dr. Benny Moog (configuration), Sam Okafor (trigger integration) |
| **Traces To** | Goal G-3, G-4 · Outcome O-1, O-2 · Principles P13, P3 |
| **Dependencies** | INT-001 operational (provides UNIT_OFFERING creation events); Ultra self-service cloning capability confirmed |
| **Acceptance Criteria** | Cloning available as self-service; process documented with version-controlled runbook; at least two trained operators; no single-person dependency; prior-period student data excluded; operation logged |

---

### INT-004: Institutional Hierarchy Synchronisation

| Field | Value |
|-------|-------|
| **ID** | INT-004 |
| **Priority** | SHOULD_HAVE |
| **Current State** | Manual updates to the Blackboard hierarchy. Drift between PeopleSoft and Blackboard hierarchies is a known issue. |
| **Target State** | Event-driven synchronisation of institutional hierarchy from PeopleSoft through the integration broker to Ultra. |
| **Data Exchanged** | Institutional hierarchy structure (organisational units, faculties, schools) — mapped to canonical model or managed as a reference data flow |
| **Direction** | PeopleSoft → Broker → Ultra |
| **Authentication** | OAuth 2.0 service accounts |
| **Latency Target** | < 15 minutes from PeopleSoft change to Ultra effect |
| **Availability** | Hierarchy changes are infrequent; standard broker availability sufficient |
| **Source Ref** | system-landscape.md integration 4; ARC-003-STKE G-2 |
| **Stakeholder** | Sam Okafor (delivery), Student Administration (hierarchy source) |
| **Traces To** | Goal G-1, G-2 · Outcome O-1 · Principles P5, P11 |
| **Dependencies** | INT-001 operational (shares PeopleSoft event infrastructure); hierarchy structure defined in PeopleSoft |
| **Acceptance Criteria** | Zero manual hierarchy updates in production; hierarchy drift eliminated — reconciliation confirms zero discrepancies per teaching period |

---

### INT-005: Allocate+ to Ultra — Group Creation

| Field | Value |
|-------|-------|
| **ID** | INT-005 |
| **Priority** | SHOULD_HAVE |
| **Current State** | Batch export from Allocate+ timetabling system, imported into Blackboard. Timetable changes not reflected until the next batch run. |
| **Target State** | Event-driven or near-real-time propagation of timetable group allocation changes from Allocate+ through the integration broker to Ultra. |
| **Data Exchanged** | Group allocation data linked to UNIT_OFFERING — students assigned to tutorial/lab groups based on timetable allocation |
| **Direction** | Allocate+ → Broker → Ultra |
| **Authentication** | OAuth 2.0 service accounts |
| **Latency Target** | < 15 minutes from timetable change to Ultra group update |
| **Availability** | Critical during enrolment and the first two weeks of each teaching period when timetable changes are frequent |
| **Source Ref** | REQ-012; system-landscape.md integration 5 |
| **Stakeholder** | Sam Okafor (delivery) |
| **Traces To** | Goal G-1 · Outcome O-1 · Principles P5, P11 |
| **Dependencies** | INT-001 operational (provides UNIT_OFFERING context); Allocate+ capable of emitting change events or change-data-capture mechanism available |
| **Acceptance Criteria** | Timetable group changes reflected in Ultra within 15 minutes; batch export/import process decommissioned; group membership consistent with Allocate+ |

---

### INT-006: Sonia to Ultra — Placement Grades

| Field | Value |
|-------|-------|
| **ID** | INT-006 |
| **Priority** | MUST_HAVE |
| **Current State** | Manual re-keying of placement grades from Sonia to Blackboard. Error-prone; audit concerns. Sensitive placement information (clearance metadata, health-context notes) circulated via email exports. Simultaneously an academic integrity problem, a privacy problem, and a student-fairness problem. |
| **Target State** | Automated bidirectional grade synchronisation between Sonia and Ultra through the integration broker, using LTI 1.3 Assignment and Grade Services or canonical GRADE events. No manual re-keying, no email circulation of sensitive data. |
| **Data Exchanged** | Grades and assessment outcomes. Sensitive placement context (clearance metadata, health-context notes) handled under elevated controls and data-minimised in the integration payload. |
| **Direction** | Sonia → Broker → Ultra (grade submission); Ultra → Broker → Sonia (gradebook updates where applicable) |
| **Authentication** | OAuth 2.0 service accounts; elevated access controls for sensitive placement data |
| **Latency Target** | < 15 minutes from grade entry in Sonia to Ultra gradebook update |
| **Availability** | Required during placement assessment periods; standard broker availability |
| **Source Ref** | REQ-018, REQ-028; ARC-003-STKE G-2, SD-11 |
| **Stakeholder** | Prof. Priya Anand (priority), Eleanor Frame (sensitive data), Sam Okafor (delivery) |
| **Traces To** | Goal G-2 · Outcome O-1, O-3 · Principles P7, P11, P12 |
| **Dependencies** | Sonia API capability confirmed for bidirectional grade exchange; INT-001 operational (provides student and unit context); sensitive data classification agreed with Frame |
| **Acceptance Criteria** | Zero manual re-keying of placement grades; zero email circulation of placement data; grades synchronised bidirectionally within 15 minutes; sensitive placement context data-minimised in integration payloads; audit trail of all grade changes |

---

### INT-007: Sandpit Provisioning

| Field | Value |
|-------|-------|
| **ID** | INT-007 |
| **Priority** | COULD_HAVE |
| **Current State** | Not yet designed. Planned for 2027. |
| **Target State** | Automated provisioning of Ultra sandpit environments for academics, integrated through the canonical model and broker. Sandpit sites available for training, experimentation, and Ultra familiarisation. |
| **Data Exchanged** | Canonical entities: PERSON, INSTITUTIONAL_ROLE_ASSIGNMENT (to determine who receives a sandpit) |
| **Direction** | Broker → Ultra (sandpit provisioning based on role events) |
| **Authentication** | OAuth 2.0 service accounts |
| **Latency Target** | Sandpit provisioning within 24 hours of a role assignment (not time-critical) |
| **Availability** | Standard availability; not teaching-critical |
| **Source Ref** | system-landscape.md integration 7 |
| **Stakeholder** | Dr. Benny Moog (design), Sam Okafor (integration) |
| **Traces To** | Goal G-4 · Outcome O-2 · Principles P11, P13 |
| **Dependencies** | INT-001 and INT-004 operational; Ultra sandpit capability confirmed with Anthology |
| **Acceptance Criteria** | Sandpit provisioned automatically based on role assignment; no manual provisioning step; sandpit content isolated from production; sandpit deprovisioned when role ends |

---

## Data Requirements

### DR-001: Canonical data model implementation

**Description**: The canonical data model defined in ARC-001-DATA-v1.0 must be implemented as the runtime integration contract, with all six core entities registered in the integration broker's schema registry.

**Rationale**: ADR-001 selected a central integration broker specifically to enforce the canonical model at runtime rather than by convention. The model is already defined — PERSON, UNIT, TEACHING_PERIOD, UNIT_OFFERING, ENROLMENT, INSTITUTIONAL_ROLE_ASSIGNMENT — but implementation is what converts it from documentation into a governing contract.

**Acceptance Criteria**:

- All six canonical entities registered in the schema registry with published, versioned schemas
- Every integration publishes and consumes against the canonical schema
- Schema validation rejects non-conformant events at runtime
- Schema change process established and governed through RIFF
- No integration bypasses the canonical model

**Priority**: MUST_HAVE

**Source Ref**: ARC-001-DATA-v1.0; ADR-001; REQ-027

**Stakeholder**: Sam Okafor (owner)

**Traces To**: Goal G-1 · Outcome O-1 · Principles P5, P6, P10

---

### DR-002: Data migration scope and minimisation

**Description**: The data migration from Learn Original to Ultra must be scoped to include only the data required for Ultra operation, with data minimisation applied to exclude historical data beyond defined retention periods.

**Rationale**: Privacy Act 1988 APP 11 requires that personal information be protected from misuse, interference, and loss. Migrating more data than necessary increases the attack surface and the privacy exposure during migration.

**Acceptance Criteria**:

- Data migration scope documented and approved by Eleanor Frame
- Historical data beyond the defined retention period excluded from migration
- Student personal information minimised — only data required for current and upcoming teaching periods migrated
- Sensitive data classes (placement records) migrated under elevated controls
- Data not required for Ultra operation archived or deleted per the university's records retention policy

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE SD-7; REQ-030

**Stakeholder**: Eleanor Frame (approval), Sam Okafor (implementation)

**Traces To**: Goal G-2 · Outcome O-3 · Principle P7

---

### DR-003: Personal information classification for migration

**Description**: All personal information classes identified in the privacy context document must be classified and handled according to their sensitivity during migration, with elevated controls for sensitive information.

**Rationale**: The privacy context identifies eight personal information classes with varying sensitivity, from student identity (PI) to placement records including clearance metadata and health-context notes (sensitive information). Migration handling must match the classification.

**Acceptance Criteria**:

- All eight personal information classes from the privacy context document classified for migration handling
- Sensitive information (placement records) handled under elevated controls: restricted access, encrypted in transit and at rest, Frame sign-off per batch
- PI classes with offshore disclosure implications (classes 3, 4, 6, 7) assessed for APP 8 compliance in the Ultra hosting environment
- Classification documented in the data migration plan

**Priority**: MUST_HAVE

**Source Ref**: privacy-context.md section 1; REQ-030

**Stakeholder**: Eleanor Frame (classification), Tobias Ohm (controls)

**Traces To**: Goal G-2 · Outcome O-3 · Principle P7

---

### DR-004: Data retention and deletion post-migration

**Description**: Migration data (bulk exports, transformation intermediaries, staging copies) must be deleted within a defined period after successful cutover, with deletion confirmed and logged.

**Rationale**: Migration data retained after cutover is an unnecessary copy of personal information with no operational purpose. APP 11 requires that personal information no longer needed be destroyed or de-identified.

**Acceptance Criteria**:

- Migration data deleted within 30 days of successful cutover for each phase
- Deletion confirmed by two individuals (maker-checker)
- Deletion logged with timestamp, scope, and confirming parties
- Learn Original data retained only in the read-only rollback state until the rollback window closes
- After the rollback window closes, Learn Original data archived per the university's records retention policy or deleted

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE SD-7, R-6; REQ-030

**Stakeholder**: Eleanor Frame (policy), Sam Okafor (execution)

**Traces To**: Goal G-2 · Outcome O-3 · Principle P7

---

### DR-005: Migration data audit trail

**Description**: The data migration must produce a complete audit trail documenting what data was migrated, when, by whom, and the outcome of each migration operation.

**Rationale**: An auditable migration history supports subject access requests, breach investigation, and governance reporting. It also provides the evidence base for the post-migration data deletion process.

**Acceptance Criteria**:

- Migration audit log maintained for each phase, recording: unit sites migrated, data volumes, timestamps, executing personnel, outcomes
- Failed migration items documented with reason and remediation action
- Audit log retained per the university's records retention policy
- Audit log available for review by Eleanor Frame and the steering committee

**Priority**: MUST_HAVE

**Source Ref**: ARC-003-STKE R-6; ARC-000-PRIN P17

**Stakeholder**: Eleanor Frame (review), Rhonda Bell (governance reporting)

**Traces To**: Goal G-3 · Outcome O-3 · Principle P17

---

## Constraints and Assumptions

### Constraints

| ID | Constraint | Source | Impact |
|----|-----------|--------|--------|
| CON-1 | Migration phases must be scheduled in inter-semester windows — no migration during assessment or examination periods | ARC-003-STKE CSF-1 | Limits migration throughput to 2-3 windows per year; extends total timeline |
| CON-2 | Principle 19 requires licensed capability to be evaluated before new spend — integration broker selection governed by ADR-001 Condition 1 | ARC-000-PRIN P19 | Broker procurement cannot begin until the Principle 19 test is complete |
| CON-3 | ADR-002 (Authoritative Source for Institutional Role Assignment) is a prerequisite and remains Proposed — role assignment integration design blocked until resolved | ADR-002 | INT-001 role assignment component cannot be finalised until ADR-002 is accepted |
| CON-4 | Integration team capacity is finite — dual-running burden (maintaining old integrations while building new) must be explicitly planned | ARC-003-STKE SD-3, G-5 | Integration re-engineering must be sequenced by risk and dependency, not attempted simultaneously |
| CON-5 | The university's governance pathway is RIFF Review, Education Committee, Operations Committee — not UK Government frameworks | ARC-003-STKE governance section | All governance references use the institutional pathway; no GDS, TCoP, or NCSC references apply |
| CON-6 | Privacy Act 1988 and Australian Privacy Principles apply — not GDPR, not UK Data Protection Act | Australian regulatory context | Compliance requirements reference APPs, OAIC, and the Notifiable Data Breach scheme |

### Assumptions

| ID | Assumption | If Invalid |
|----|-----------|-----------|
| A-1 | PeopleSoft can emit change events or a change-data-capture mechanism can be deployed against it | INT-001 Phase 3 extends; custom CDC build required; timeline risk increases |
| A-2 | Anthology's migration tooling handles the majority of Learn Original content types, achieving the 95% success target | Migration effort and manual remediation increase significantly; additional Anthology professional services required |
| A-3 | Ultra's REST API and webhook capabilities are available within the current licensing tier (not gated behind premium licensing) | Unbudgeted licensing cost; Tanaka negotiates API access as part of migration commitment (per R-5) |
| A-4 | Sonia has or will develop API capability for bidirectional grade exchange | INT-006 requires a CDC or polling mechanism on the integration team's side; Sonia vendor engagement critical |
| A-5 | Ultra hosting region is Australia, or Anthology can confirm the hosting position for APP 8 assessment | Cross-border disclosure assessment required; contract clause negotiation with Anthology |
| A-6 | ADR-002 will be resolved within the first 8 weeks of the project, unblocking the role assignment component of INT-001 | Role assignment implemented with the current PeopleSoft-as-source assumption and retrofitted if ADR-002 concludes differently |
| A-7 | Academic calendar provides inter-semester windows of at least 3 weeks sufficient for faculty-level migration | Migration phases span two inter-semester windows per faculty, extending the overall timeline |
| A-8 | The integration team receives capacity augmentation (vendor professional services or additional staff) for the dual-running period | Dual-running degrades both existing and new integrations; integration re-engineering sequenced more conservatively |

---

## Success Criteria and KPIs

| KPI | Target | Baseline | Measurement Method | Frequency | Owner |
|-----|--------|----------|-------------------|-----------|-------|
| Assessment-period disruption incidents attributable to migration | Zero | No migration attempted | Incident log | Per migration phase | Rhonda Bell |
| Content migration success rate | > 95% items migrated without manual intervention | No baseline | Migration report per unit site | Per migration phase | Dr. Benny Moog |
| Pilot satisfaction rating | > 80% | No baseline | Pilot survey | After pilot completion | Dr. Benny Moog |
| Academic satisfaction post-migration | > 70% | No baseline | Post-migration survey | Per faculty phase | Dr. Felix Marimba |
| Template adoption rate | > 80% in first teaching period on Ultra | 0% (no baseline template exists) | LMS reporting | Per teaching period | Dr. Benny Moog |
| Change propagation latency (identity/enrolment/role) | < 15 minutes (95th percentile) | Up to 24 hours (nightly batch) | Integration monitoring telemetry | Continuous | Sam Okafor |
| Manual PI flows in production | Zero | 4 of 7 integrations involve manual handling | Integration register audit | Quarterly | Eleanor Frame |
| Flat files carrying PI on shared storage | Zero | Multiple (PeopleSoft flat-file, CSV exports) | Storage audit | Quarterly | Eleanor Frame |
| Local accounts on Ultra | Zero | 2 tools allow local accounts | Configuration audit | Annually | Tobias Ohm |
| Integration incidents per teaching period | < 2 requiring intervention | Weekly manual interventions | Incident log | Per teaching period | Sam Okafor |
| Discipline tool integration pass rate in Ultra | 100% | Not yet tested | Integration test results | Before each faculty migration | Dr. Benny Moog |
| Deprovisioning latency | < 15 minutes | Up to 24 hours | Integration telemetry | Continuous | Tobias Ohm |

---

## Dependencies and Risks

### Dependencies

| ID | Dependency | Type | Status | Impact if Unresolved |
|----|-----------|------|--------|---------------------|
| DEP-1 | ADR-001 accepted and integration broker selected/confirmed | Architecture decision | Proposed | All integration re-engineering blocked; cannot implement canonical model at runtime |
| DEP-2 | ADR-002 resolved — authoritative source for institutional role assignment confirmed | Architecture decision | Proposed | Role assignment component of INT-001 cannot be finalised; assumption A-6 applies as fallback |
| DEP-3 | Anthology migration tooling tested and capable of handling UoF content types | Vendor capability | Not yet tested | Content migration success rate at risk; additional manual remediation required |
| DEP-4 | Ultra REST API and webhook access available within current licensing | Vendor commercial | Not yet confirmed | Integration architecture constrained; unbudgeted licensing cost |
| DEP-5 | Sonia API capability for bidirectional grade exchange | Vendor capability | Not yet confirmed | INT-006 requires alternative mechanism (CDC/polling); manual re-keying persists longer |
| DEP-6 | Student Administration and HR engagement confirmed | Organisational | Representatives TBD | ADR-002 resolution blocked; role assignment integration delayed |
| DEP-7 | Integration team capacity augmented for dual-running period | Resource | Not yet approved | Risk R-2 materialises; integration re-engineering sequenced more conservatively |

### Risks

Risks below reference ARC-003-STKE-v1.0 risk register (R-1 to R-6).

| ID | Risk | Likelihood | Impact | Mitigation | Contingency | Owner | Traces To |
|----|------|-----------|--------|------------|-------------|-------|-----------|
| R-1 | Academic resistance to Ultra interface change — content migration imperfect, timing conflicts with teaching preparation | HIGH | MEDIUM | Pilot programme; content migration tested on representative units; Ultra positioned as pedagogical improvement; training workshops | Extend pilot; address content migration issues before broadening; accept lower initial template adoption with voluntary rather than mandated approach | Dr. Benny Moog | G-3, G-4 |
| R-2 | Integration team overwhelmed by dual-running — cannot maintain existing integrations while building new ones | HIGH | HIGH | Capacity plan approved before migration; vendor professional services for PeopleSoft integration; progressive decommission of old flows | Narrow Phase 1 to PeopleSoft integration only; delay remaining integrations with explicit resourcing decision | Sam Okafor | G-1, G-5 |
| R-3 | ADR-002 unresolved — role assignment source undefined, blocking INT-001 role component | MEDIUM | HIGH | Escalate ADR-002 resolution as prerequisite; include Student Admin and HR as named stakeholders; set decision deadline | Implement with PeopleSoft-as-source assumption; retrofit if ADR-002 concludes differently | Sam Okafor | G-1, G-2 |
| R-4 | Content migration breaks discipline-specific content — embedded notation, simulation links, clinical scenarios | MEDIUM | MEDIUM | Discipline faculty unit sites in pilot testing; LTI integrations tested in Ultra sandbox; faculty sign-off before migration | Manual remediation with Learning Technologies support; extend discipline faculty migration window | Dr. Benny Moog | G-3, G-6 |
| R-5 | Anthology gates critical API access behind premium licensing — REST API or webhook capabilities require premium tier | MEDIUM | HIGH | API access requirements documented and submitted before contract negotiation; Tanaka negotiates API access as part of migration commitment | Evaluate alternative integration approaches (LTI Advantage, SIS framework); escalate to steering | Grace Tanaka | G-1, G-2 |
| R-6 | Data migration exposes personal information without adequate controls — bulk exports without access restriction or defined deletion | LOW | HIGH | Data migration plan reviewed by Frame; migration environment access-restricted; data deleted within 30 days of cutover; sensitive data under elevated controls | Segment data migration — non-sensitive first, then sensitive with Frame sign-off per batch | Eleanor Frame | G-2 |

---

## Requirement Conflicts and Resolutions

### Conflict 1: Migration pace versus academic disruption

**Competing Requirements**: BR-002 (integration re-engineering) and NFR-P-001 (propagation latency < 15 minutes) push for rapid delivery. BR-001 (zero assessment disruption) and FR-012 (pilot programme) demand a slower, phased rollout.

**Source**: ARC-003-STKE Conflict 1 — SD-2/SD-3 versus SD-6/SD-13

**Affected Stakeholders**: Rhodes and Okafor (want prompt integration delivery) versus Castle and Field (want migration sequenced to minimise teaching disruption)

**Resolution**: Phase the migration around inter-semester windows. Deliver the PeopleSoft integration first (purely backend — invisible to academics), then migrate faculties in cohorts during breaks. This gives Rhodes and Okafor early integration wins while protecting Castle and Field from in-semester disruption. The backend integration re-engineering and the front-end LMS migration are sequenced so that no teaching period experiences both changes simultaneously.

**Residual Impact**: Longer overall timeline; extended dual-running period; increased capacity requirement during dual-running.

---

### Conflict 2: Integration scope versus team capacity

**Competing Requirements**: BR-002 (all seven integrations re-engineered) creates a large delivery scope. NFR-M-002 (documentation and runbooks for every integration) increases per-integration effort. BR-006 (licence cost management) constrains the capacity investment.

**Source**: ARC-003-STKE Conflict 2 — SD-2 versus SD-3/SD-9

**Affected Stakeholders**: Rhodes (wants all seven integrations re-engineered) versus Okafor (cannot build seven while maintaining seven) versus Ostinato (will not fund unlimited capacity)

**Resolution**: Sequence by risk and dependency. Phase 1: PeopleSoft lifecycle (unblocks everything). Phase 2: provisioning automation and placement grades (highest privacy/operational impact). Phase 3: remaining integrations. This is achievable within team capacity plus targeted vendor professional services for Phase 1. Each phase decommissions old flows, progressively freeing capacity.

**Residual Impact**: Phase 3 integrations (Allocate+ groups, hierarchy, sandpit) delivered later; team capacity remains tight until Phase 1 decommissions the flat-file.

---

### Conflict 3: Principle 19 versus middleware need

**Competing Requirements**: BR-002 requires integration through a central broker (per ADR-001). BR-006 and Principle 19 require that existing licensed capability be evaluated before new spend.

**Source**: ARC-003-STKE Conflict 3 — SD-2 versus SD-9

**Affected Stakeholders**: Rhodes (needs the broker to enforce the canonical model) versus Ostinato (needs costs justified)

**Resolution**: ADR-001 already navigated this by attaching Condition 1: Digital & IT must confirm in writing whether existing licensed platforms — including the Microsoft agreement — already provide adequate integration or event-brokering capability. If they do, Option B is delivered using that capability rather than a new purchase. The Principle 19 test is a precondition for procurement, not an objection to the architecture.

**Residual Impact**: Broker selection delayed by the Principle 19 test (estimated 2 weeks); if existing capability is adequate, the operating model may differ from the originally envisaged broker.

---

### Conflict 4: Anthology commercial interest versus Principle 19

**Competing Requirements**: Anthology wants to sell Ultra premium features and professional services (SD-14). Principle 19 and BR-006 require exhausting licensed capability before new spend. NFR-I-002 (LTI 1.3 Advantage) and FR-007 (canonical model) require API access that may be behind a premium tier.

**Source**: ARC-003-STKE Conflict 4 — SD-14 versus SD-9

**Affected Stakeholders**: Anthology (wants premium feature revenue) versus Tanaka (negotiating leverage) versus Ostinato (costs justified)

**Resolution**: Complete capability mapping of the Ultra licence before engaging on premium features. Negotiate professional services scope as part of the contract renewal rather than as a separate purchase. Tanaka leads with Principle 19 as a procurement position: API access required for the integration architecture is a core capability expectation, not a premium add-on.

**Residual Impact**: If critical APIs are genuinely premium-only, an unbudgeted cost materialises; escalation to steering required.

---

## Timeline and Milestones

### Phase 1: Foundation (Months 1-4)

| Milestone | Target | Dependencies |
|-----------|--------|-------------|
| ADR-002 resolved | Month 2 | Student Admin and HR engagement (DEP-6) |
| Principle 19 test complete (ADR-001 Condition 1) | Month 1 | Digital & IT assessment |
| Integration broker selected/confirmed | Month 2 | Principle 19 test result |
| Canonical schema registered in broker | Month 3 | Broker operational |
| PeopleSoft event-driven integration live (INT-001) | Month 4 | Broker, PeopleSoft event capability, ADR-002 |
| Ultra SSO/MFA configured and verified | Month 2 | Anthology Ultra instance available |
| Ultra baseline template designed and accessibility-audited | Month 3 | Academic consultation complete |
| Pilot programme commenced with willing academics | Month 3 | Template ready; Ultra sandbox available |

### Phase 2: Migration and Priority Integrations (Months 4-8)

| Milestone | Target | Dependencies |
|-----------|--------|-------------|
| Pilot programme completed; satisfaction > 80% | Month 5 | Pilot cohort available |
| First faculty cohort migrated to Ultra (inter-semester window) | Month 6 | Pilot success; Education Committee approval |
| Echo360 provisioning automated (INT-002) | Month 5 | INT-001 operational |
| Sonia placement grades automated (INT-006) | Month 6 | Sonia API capability confirmed |
| Course cloning automated in Ultra (INT-003) | Month 6 | Ultra cloning capability confirmed |
| Flat-file process decommissioned (after one teaching period) | Month 8 | INT-001 proven |

### Phase 3: Completion and Sustainment (Months 8-12)

| Milestone | Target | Dependencies |
|-----------|--------|-------------|
| Remaining faculties migrated to Ultra | Month 10 | Phase 2 lessons applied; inter-semester windows available |
| Institutional hierarchy automated (INT-004) | Month 9 | PeopleSoft hierarchy events |
| Allocate+ group creation automated (INT-005) | Month 10 | Allocate+ event capability |
| Sandpit provisioning designed (INT-007) | Month 10 | Ultra sandpit capability confirmed |
| Learn Original decommissioned | Month 12 | All faculties migrated and confirmed; rollback window closed |
| All old integration mechanisms decommissioned | Month 12 | All new integrations proven through one teaching period |
| Essential Eight posture re-assessed | Month 12 | All security improvements in place |
| Post-migration privacy review completed | Month 12 | All migration data deleted; manual flows eliminated |

---

## Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Executive Sponsor | Prof. Otis Hammond, DVC (Education) | | |
| Business Owner | Dr. Benny Moog, Director Learning Technologies | | |
| Integration Architect | Sam Okafor | | |
| Privacy & Records Officer | Eleanor Frame | | |
| Cybersecurity Lead | Tobias Ohm | | |
| Project Manager | Rhonda Bell | | |

---

## Appendices

### Appendix A: Glossary

| Term | Definition |
|------|-----------|
| APPs | Australian Privacy Principles — the 13 principles in Schedule 1 of the Privacy Act 1988 governing the handling of personal information |
| ADR | Architecture Decision Record — a structured record of an architecture decision, its options, rationale, and consequences |
| ASD Essential Eight | The Australian Signals Directorate's Essential Eight Mitigation Strategies — a prioritised list of security controls for organisations |
| Canonical Data Model | A standardised data model defining the authoritative shape of core entities across the integration estate — PERSON, UNIT, TEACHING_PERIOD, UNIT_OFFERING, ENROLMENT, INSTITUTIONAL_ROLE_ASSIGNMENT |
| CDC | Change Data Capture — a pattern for detecting and publishing data changes from a source system that does not natively emit events |
| Dead-letter queue | A queue where messages that cannot be processed are held for inspection and replay |
| Integration Broker | The central mediating layer selected under ADR-001 through which all integrations publish and subscribe, enforcing the canonical schema at runtime |
| Learn Original | The current version of Blackboard Learn, distinct from the Ultra experience |
| LTI | Learning Tools Interoperability — an industry standard (by 1EdTech) for integrating tools with learning management systems |
| LTI 1.3 Advantage | The current LTI standard including Names and Role Provisioning Services, Assignment and Grade Services, and Deep Linking |
| ML2 | Maturity Level 2 — the target maturity level for the ASD Essential Eight mitigation strategies |
| MoSCoW | Prioritisation method: Must Have, Should Have, Could Have, Won't Have (this time) |
| OAIC | Office of the Australian Information Commissioner — the regulator responsible for the Privacy Act 1988 |
| PI | Personal Information as defined by the Privacy Act 1988 |
| RIFF | Request for Information/Functionality — the university's governance process for assessing new and changed learning technology |
| Schema Registry | A component of the integration broker that holds the canonical entity definitions and validates events at runtime |
| SCIM | System for Cross-domain Identity Management — a standard for automating user provisioning and deprovisioning |
| SIS | Student Information System — PeopleSoft at the University of Funk |
| SSO/MFA | Single Sign-On with Multi-Factor Authentication |
| TEQSA | Tertiary Education Quality and Standards Agency — Australia's higher education regulator |
| Ultra | Blackboard Ultra — the current-generation Blackboard LMS experience, replacing Learn Original |
| WCAG 2.2 AA | Web Content Accessibility Guidelines version 2.2 at Level AA conformance |

### Appendix B: Cross-reference to ARC-001-REQ-v1.0

This document (ARC-003-REQ) operationalises the architecture requirements established in ARC-001-REQ for the specific delivery context of the Ultra migration and integration re-engineering. The table below maps Project 003 requirements to their Project 001 ancestors where applicable.

| ARC-003-REQ ID | ARC-001-REQ ID | Relationship |
|---------------|---------------|-------------|
| BR-001 | BR-006 | Migration-specific instantiation of the consistent student experience requirement |
| BR-002 | BR-004 | Delivery of the integration fragility and manual handling elimination requirement |
| BR-003 | BR-004, BR-005 | Migration-specific instantiation of privacy and manual flow requirements |
| BR-004 | BR-005 | Delivery of the demonstrable privacy and security posture requirement |
| BR-005 | BR-006 | Migration-specific instantiation of the consistent and accessible experience requirement |
| BR-006 | BR-002 | Delivery against the licence spend constraint |
| BR-007 | BR-007 | Continuity of the governance operating on evidence requirement |
| FR-007 | INT-001 to INT-009 | Canonical model implementation across all integrations |
| FR-008 | INT-001 | PeopleSoft lifecycle integration |
| INT-001 | INT-001 | Direct delivery of the SIS lifecycle integration requirement |
| INT-006 | INT-005 | Direct delivery of the placement grades integration requirement |
| NFR-P-001 | NFR-P-001 | Same propagation latency target |
| NFR-SEC-001 | NFR-SEC-001 | Same SSO/MFA enforcement requirement |
| NFR-C-001 | NFR-C-001 | Same Privacy Act compliance requirement |
| DR-001 | DR-001 | Same canonical data model requirement |

### Appendix C: Principle Alignment Matrix

| Principle | ID | Relevant Requirements | Alignment |
|-----------|----|-----------------------|-----------|
| Single Learning Entry Point | P1 | BR-001, BR-005, FR-001, FR-004, NFR-U-001, NFR-A-001 | Ultra as the single entry point; consistent templates; availability during teaching |
| Deliberate Capability Boundaries | P2 | BR-007 | RIFF governance applies to all migration decisions |
| Consistent Experience Across Schools | P3 | BR-005, FR-004, FR-010, FR-011, FR-012 | Templates, training, and cloning deliver consistency |
| Discipline Specialisation at the Edge | P4 | FR-003, FR-014, NFR-I-002 | LTI 1.3 verification for discipline tools; discipline content migration tested |
| Single Source of Truth for Core Entities | P5 | BR-002, FR-007, FR-008, INT-001, DR-001 | Canonical model enforced at runtime; PeopleSoft authoritative for student/course/enrolment |
| Canonical Data Model | P6 | BR-002, FR-007, INT-001 to INT-007, DR-001 | All integrations through the canonical model |
| Privacy by Design and Data Minimisation | P7 | BR-003, BR-004, NFR-SEC-003, NFR-SEC-004, NFR-C-001, NFR-C-003, DR-002, DR-003, DR-004 | Manual PI flows eliminated; migration data minimised; sensitive data under elevated controls |
| Interface-Mediated Integration | P10 | BR-002, FR-007, NFR-I-001, NFR-I-002, NFR-A-003 | All integrations through the broker and canonical model; LTI 1.3 for tool integration |
| Event-Driven and Near-Real-Time by Default | P11 | BR-002, FR-008, FR-009, FR-015, NFR-P-001, INT-001 to INT-007 | Nightly batch replaced with event-driven; < 15 minutes propagation |
| Automated Identity Lifecycle | P12 | BR-003, BR-004, FR-006, FR-008, FR-009, NFR-SEC-001, NFR-SEC-003 | SSO/MFA only; automated provisioning and deprovisioning; no CSV |
| Reproducible, Documented Automation | P13 | FR-002, FR-010, NFR-M-002, INT-003 | Documented runbooks; version-controlled processes; no single-person dependency |
| Accessibility by Default | P14 | BR-005, FR-004, FR-005, NFR-U-001, NFR-U-002 | WCAG 2.2 AA; templates accessibility-audited; mobile responsiveness |
| Layered Security Posture | P16 | BR-004, FR-006, NFR-SEC-001, NFR-SEC-002, NFR-SEC-004 | SSO/MFA only; OAuth 2.0 service credentials; migration data access control |
| Observable Integrations and Services | P17 | NFR-M-001, NFR-M-003, NFR-I-001, DR-005 | Single observability plane; change logging with prior value; audit trails |
| Evidence-Based Capability Investment | P18 | BR-007 | RIFF governance with architectural evidence |
| Realise Licensed Capability Before New Spend | P19 | BR-006, BR-007 | Principle 19 test prerequisite for broker procurement; Ultra capability mapping before premium features |

---

## External References

> This section provides traceability from generated content back to source documents.

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| SL | system-landscape.md | Foundation artifact | `projects/003-lms-ultra-migration/external/` | System categorisation map with usage status and known integrations |
| PC | privacy-context.md | Compliance input | `projects/003-lms-ultra-migration/external/` | Personal information inventory, data flows, Essential Eight self-assessment |
| PP | ARC-000-PRIN-v1.1 | ArcKit artifact | `projects/000-global/` | Enterprise Architecture Principles (19 principles) |
| RR | requirements-register.md | Requirements input | `projects/003-lms-ultra-migration/external/` | Consolidated academic survey requirements (REQ-001 to REQ-035) |
| SGP | solution-governance-process.md | Foundation artifact | `projects/000-global/policies/` | RIFF Review governance and approval process |
| STKE3 | ARC-003-STKE-v1.0.md | ArcKit artifact | `projects/003-lms-ultra-migration/` | Stakeholder Drivers & Goals Analysis (Project 003) |
| REQ1 | ARC-001-REQ-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/` | Requirements (Project 001) — ancestor requirements |
| ADR1 | ARC-001-ADR-001-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/decisions/` | Integration Mediation Approach |
| ADR2 | ARC-001-ADR-002-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/decisions/` | Authoritative Source for Institutional Role Assignment |
| DATA1 | ARC-001-DATA-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/` | Canonical data model and privacy-relevant flows |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Referenced Content |
|-------------|--------|--------------|----------|--------------------|
| SL-C1 | SL | Known integrations | Risk Factor | Seven integration descriptions including: nightly batch flat-file, manual CSV, undocumented single-person dependency, manual re-keying |
| PC-C1 | PC | Section 2 | Compliance Constraint | Data flows of PIA interest: flat files at rest on shared storage; stale deprovisioning; manual re-keying of placement grades; CSV cohort extracts |
| PC-C2 | PC | Section 3 | Security Requirement | Essential Eight self-assessment: MFA at ML2 with exception for two tools allowing local accounts |
| PP-C1 | PP | Principle 19 | Design Decision | Licensed capability must be evaluated before new spend |
| SGP-C1 | SGP | Rules | Governance | RIFF duplication rule: solutions duplicating licensed capability must justify why the incumbent is unsuitable |
| STKE-C1 | STKE3 | CSF-1 to CSF-5 | Success Factors | Critical success factors governing migration sequencing, integration re-engineering, and academic adoption |
| ADR1-C1 | ADR1 | Decision Outcome | Architecture Decision | Central integration broker with canonical schema enforcement; phased adoption starting with SIS lifecycle and placement grades |
| ADR2-C1 | ADR2 | Status | Dependency | Proposed (unresolved) — authoritative source for institutional role assignment not yet confirmed |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| consultant-brief.md | `projects/003-lms-ultra-migration/external/` | Read for context; scope documented in STKE and ADR artifacts already cited |
| stakeholders.md | `projects/003-lms-ultra-migration/external/` | Full stakeholder register used via ARC-003-STKE-v1.0, which supersedes it |

---

**Generated by**: ArcKit `/arckit:requirements` command
**Generated on**: 2026-07-29
**ArcKit Version**: 6.7.4
**Project**: LMS Ultra Migration & Integration Modernisation (Project 003)
**Model**: Claude Opus 4.6 (1M context)
