# The University of Funk — Enterprise Architecture Principles

> **Template Origin**: Official | **ArcKit Version**: 6.4.0 | **Command**: `/arckit:principles`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-000-PRIN-v1.0 |
| **Document Type** | Enterprise Architecture Principles |
| **Project** | Global / Cross-Project (The University of Funk) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-26 |
| **Last Modified** | 2026-07-26 |
| **Review Cycle** | Annual |
| **Next Review Date** | 2027-07-26 |
| **Owner** | Cassandra "Cas" Rhodes, Chief Information Officer |
| **Reviewed By** | Dr. Benny Moog, Director Learning Technologies; Sam Okafor, Integration Architect |
| **Approved By** | PENDING — Education Committee (A/Prof. Pearl Clavinet, Chair) |
| **Distribution** | University Executive; Education Committee; Operations Committee; Digital & IT; Learning Innovation; School and Faculty leadership |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-26 | ArcKit AI | Initial creation from `/arckit:principles` command — WP1 Architecture Principles | PENDING | PENDING |

---

## Executive Summary

This document establishes the principles governing all technology architecture decisions at The University of Funk. It is the WP1 deliverable of the Learning & Teaching Baseline Strategy engagement [PP-C1], and it is deliberately written as an **organisation-wide** artifact: every project initialised after this document inherits these principles.

**Scope**: All technology projects, systems, and initiatives — with immediate application to the Learning & Teaching technology ecosystem.

**Authority**: Education Committee, on advice from Digital & IT and Learning Innovation.

**Compliance**: Mandatory unless an exception is approved through the RIFF Review process (Section VI) [PP-C2].

**Philosophy**: These principles are **technology-agnostic**. They describe WHAT qualities the architecture must have, not HOW to implement them with specific products. No principle in this document names a vendor, product, or platform. Technology selection happens during research, decision (ADR) and design phases, guided by these principles.

**Why these principles, now**: The L&T ecosystem has grown to 20+ tools with overlapping capability, fragile point-to-point integrations, and licensed functionality that was never switched on [PP-C3]. Principles 2, 11 and 19 exist specifically to stop that pattern recurring.

### Principle Index

| # | Principle | Category | Criticality |
|---|-----------|----------|-------------|
| 1 | Single Learning Entry Point | Business | HIGH |
| 2 | Deliberate Capability Boundaries | Business | CRITICAL |
| 3 | Consistent Experience Across Schools | Business | HIGH |
| 4 | Discipline Specialisation at the Edge | Business | MEDIUM |
| 5 | Single Source of Truth for Core Entities | Data | CRITICAL |
| 6 | Canonical Data Model | Data | HIGH |
| 7 | Privacy by Design and Data Minimisation | Data | CRITICAL |
| 8 | Data Residency and Cross-Border Accountability | Data | CRITICAL |
| 9 | Data Portability and Exit | Data | HIGH |
| 10 | Interface-Mediated Integration | Application | CRITICAL |
| 11 | Event-Driven and Near-Real-Time by Default | Application | HIGH |
| 12 | Automated Identity Lifecycle | Application | CRITICAL |
| 13 | Reproducible, Documented Automation | Application | HIGH |
| 14 | Accessibility by Default | Quality | CRITICAL |
| 15 | Availability Aligned to the Teaching Calendar | Quality | HIGH |
| 16 | Layered Security Posture | Technology | CRITICAL |
| 17 | Observable Integrations and Services | Technology | HIGH |
| 18 | Evidence-Based Capability Investment | Governance | CRITICAL |
| 19 | Realise Licensed Capability Before New Spend | Governance | HIGH |

---

## I. Business and Strategic Principles

### 1. Single Learning Entry Point

**Principle Statement**:
Students MUST be able to reach all unit materials, activities, submissions and grades through a single, consistent entry point. Supporting platforms MAY hold the underlying capability, but they MUST be reachable from that entry point rather than requiring students to navigate to them independently.

**Rationale**:
Fragmentation across many tools transfers navigational cost onto students, disproportionately affecting those with the least time, confidence, or assistive-technology tolerance for inconsistency. A single entry point is the architectural expression of the survey's most strongly held requirement [PP-C4].

**Implications**:

- The learning management layer acts as the integration surface for the student journey, not as the sole container of capability
- Specialist platforms surface through embedded, launched, or linked experiences that preserve session and identity context
- Deep links into supporting platforms carry enrolment and role context; students are not asked to re-authenticate or re-identify themselves
- Grades and progress indicators originating in specialist platforms flow back to the single entry point rather than remaining stranded
- A capability that cannot be surfaced through the entry point requires an approved exception

**Validation Gates**:

- [ ] Every student-facing capability is reachable from the primary entry point
- [ ] No student-facing platform requires a separate credential or manual account request
- [ ] Grade and progress data originating externally is visible at the entry point
- [ ] Launch context (identity, unit, role) is preserved on transition between platforms
- [ ] Student representatives have validated the navigation model

---

### 2. Deliberate Capability Boundaries

**Principle Statement**:
Each capability category MUST have a designated primary platform. Where more than one platform provides the same capability, the architecture MUST state which is primary and why the others persist, with a defined boundary or a retirement path.

**Rationale**:
Overlapping capability is the root cause of the ecosystem's current cost and complexity — the same function is licensed several times, staff receive inconsistent guidance, and students encounter different tools for the same task between units [PP-C3]. Duplication is not inherently wrong; *undeclared* duplication is.

**Implications**:

- Capability categories are the unit of architectural analysis, and every platform is mapped to them [PP-C5]
- Where overlap exists, one of three outcomes is recorded: designated primary with defined boundary, transitional state with retirement date, or approved permanent exception
- New platform requests that duplicate licensed capability must justify why the incumbent is unsuitable [PP-C2]
- Boundary statements are architectural artifacts, reviewed when contracts renew
- "Best of breed" and "single platform" are both legitimate strategies — but the choice must be explicit per capability category, not left implicit

**Validation Gates**:

- [ ] Every capability category has a designated primary platform
- [ ] Every overlap is classified as primary/boundary, transitional, or approved exception
- [ ] Transitional overlaps carry a retirement date and an owner
- [ ] No platform is retained solely because no one decided to retire it
- [ ] Capability map is current as at the most recent contract review

---

### 3. Consistent Experience Across Schools

**Principle Statement**:
Unit sites MUST present a consistent structure, navigation, and terminology to students regardless of school, faculty, or teaching team. Variation MUST be justified by pedagogy, not by local preference or historical accident.

**Rationale**:
Students routinely study across schools. Structural inconsistency between units imposes a recurring cognitive tax that is invisible to any single teaching team but cumulative for the student [PP-C4].

**Implications**:

- Templates define baseline structure and navigation; teaching teams customise content within that structure
- Template conformance is designed to be the path of least resistance, not an additional compliance step
- Terminology for common concepts (assessment, submission, feedback, reading list) is standardised institution-wide
- Variation is permitted where a discipline's pedagogy genuinely requires it, and is recorded
- Consistency requirements apply to the student-facing surface; they do not dictate staff-side authoring workflow

**Validation Gates**:

- [ ] Baseline template exists and is the default for new unit sites
- [ ] Common terminology defined and applied across student-facing surfaces
- [ ] Template conformance measurable across the unit portfolio
- [ ] Documented pedagogical justification exists for each approved structural variation
- [ ] Student representatives consulted on structure and terminology

---

### 4. Discipline Specialisation at the Edge

**Principle Statement**:
Discipline-specific tooling MAY sit outside the core platform set where a genuine specialist need exists, but it MUST integrate through the same standard interfaces, identity model, and data contracts as core platforms. Specialist need justifies a different tool — never a different architecture.

**Rationale**:
Music and performing arts, health simulation, and clinical placement each have legitimate requirements that general-purpose platforms cannot meet [PP-C6]. Accommodating them at the edge preserves both disciplinary quality and architectural coherence. The failure mode this principle prevents is a specialist tool arriving with its own identity store, its own manual data flows, and its own privacy posture.

**Implications**:

- Specialist tools are held to the same identity, integration, accessibility and privacy principles as core platforms
- A specialist tool that cannot meet those principles is an exception decision, taken with the affected school and recorded
- Support models for specialist tools are defined explicitly, including where support sits when it is not central
- Discipline tooling is reviewed on the same contract and capability cycle as core platforms
- Specialist status is not a permanent exemption from architectural review

**Validation Gates**:

- [ ] Each specialist tool has a named support model and owner
- [ ] Specialist tools authenticate through institutional identity
- [ ] Specialist tools integrate through published interfaces, not manual transfer
- [ ] Specialist tool inventory reviewed at least annually
- [ ] Exceptions recorded where a specialist tool cannot meet a principle

---

## II. Data Principles

### 5. Single Source of Truth for Core Entities

**Principle Statement**:
Student, course, enrolment, and institutional role MUST each have exactly one authoritative source system. All other systems hold derived, read-oriented copies that are clearly identified as such.

**Rationale**:
Role assignment failures and hierarchy drift between systems trace directly to the absence of a declared authority for these entities [PP-C7]. Where two systems both believe they are authoritative, reconciliation becomes manual and errors become permanent.

**Implications**:

- The authoritative source for each core entity is declared and published
- Derived copies are read-oriented; writes are directed to the authoritative source
- Bidirectional synchronisation is avoided; where genuinely required, a conflict-resolution rule is defined in advance
- Institutional role is derived from one source and propagated, never independently maintained per platform [PP-C8]
- Reconciliation between authoritative source and derived copies is automated and monitored, not periodic and manual

**Validation Gates**:

- [ ] Authoritative source declared for student, course, enrolment, and role
- [ ] Derived copies documented with synchronisation frequency and direction
- [ ] No bidirectional synchronisation without a documented conflict-resolution rule
- [ ] Reconciliation discrepancies surfaced automatically
- [ ] No platform maintains an independent role assignment

---

### 6. Canonical Data Model

**Principle Statement**:
A canonical data model MUST be defined for core academic entities and MUST govern all integrations. Point-to-point transformations between proprietary formats are prohibited for these entities.

**Rationale**:
Each new point-to-point integration adds a bespoke mapping that must be understood, tested, and maintained. A canonical model converts an N-times-N mapping problem into an N-times-one problem, and makes platform substitution tractable [PP-C9].

**Implications**:

- Entity definitions, identifiers, and permitted values are published and version-controlled
- Integrations map to and from the canonical model, not directly to another system's internal representation
- Model changes follow a versioned, backward-compatible evolution path
- Identifier strategy is defined explicitly, including how identity is preserved across systems
- The canonical model is an institutional asset, owned and maintained beyond any single project

**Validation Gates**:

- [ ] Canonical definitions published for student, course, enrolment, and role
- [ ] Identifier strategy documented for each entity
- [ ] All new integrations map through the canonical model
- [ ] Model versioned with a backward-compatibility policy
- [ ] Named owner accountable for model maintenance

---

### 7. Privacy by Design and Data Minimisation

**Principle Statement**:
Systems and integrations MUST collect, transmit, and retain the minimum personal information necessary for their purpose. Privacy assessment MUST occur at design time, before implementation, and MUST be repeated when data flows materially change.

**Rationale**:
Obligations under the Privacy Act 1988 and the Australian Privacy Principles attach to the design of a system, not to its documentation after the fact [PP-C10]. The ecosystem's current manual flows — re-keyed grades, circulating cohort extracts, ad-hoc analytics exports — are privacy findings as much as they are integration weaknesses [PP-C11].

**Implications**:

- Personal information is classified at design time, with sensitive information identified explicitly and handled under elevated controls
- Bulk extracts, manual re-keying, and email transfer of personal information are treated as architectural defects requiring remediation
- Retention periods are defined per data class and enforced automatically rather than by convention
- Derived and analytics data is minimised and de-identified wherever the purpose permits
- Privacy assessment is a design input, not a pre-release gate discovered late
- Access to personal information follows least privilege and is revoked promptly when a role ends

**Validation Gates**:

- [ ] Personal information classified, with sensitive information separately identified
- [ ] Each flow justified against a defined purpose, carrying only necessary fields
- [ ] Retention periods defined and automatically enforced per data class
- [ ] No manual re-keying or ad-hoc extract in any production flow carrying personal information
- [ ] Privacy assessment completed before build commences
- [ ] De-identification applied to analytics and reporting where purpose permits

---

### 8. Data Residency and Cross-Border Accountability

**Principle Statement**:
Personal information SHOULD be held in Australian jurisdiction. Where a platform discloses personal information offshore, that disclosure MUST be assessed, contractually governed, and formally accepted before the platform is adopted or renewed.

**Rationale**:
Cross-border disclosure carries accountability that remains with the university regardless of where the data physically sits [PP-C12]. Several current platforms hold student work, recordings, exam artifacts, and survey responses offshore under the assessed hosting arrangements — this must be a decided position, not an inherited one.

**Implications**:

- Hosting region is a required attribute of every platform record, captured at procurement
- Offshore disclosure triggers a documented cross-border assessment before adoption or renewal
- The practicability of an Australian-region alternative is assessed and recorded, including when the answer is that none exists
- Contracts governing offshore disclosure specify accountability, breach notification, and data handling obligations
- Residency posture is re-assessed at each contract renewal, not fixed at first adoption

**Validation Gates**:

- [ ] Hosting region recorded for every platform holding personal information
- [ ] Cross-border assessment completed for each offshore disclosure
- [ ] Australian-region alternative considered and outcome documented
- [ ] Contractual accountability and breach notification clauses verified
- [ ] Residency posture reviewed at contract renewal

---

### 9. Data Portability and Exit

**Principle Statement**:
Every platform holding university or student data MUST permit export of that data in open, documented formats, at any time and on termination, without dependence on vendor goodwill or additional fee.

**Rationale**:
Exit capability is what makes the rationalisation decisions in this ecosystem executable. A platform that cannot be left cannot be rationalised, and its renewal is not a genuine decision [PP-C13]. Portability also underpins the student's ability to retain evidence of their own learning beyond graduation.

**Implications**:

- Export capability is verified during evaluation, not assumed from contract language
- Export formats are open and documented; proprietary formats requiring vendor tooling do not satisfy this principle
- Export coverage includes content, configuration, user-generated work, and assessment records
- Student-owned artifacts remain exportable by the student, including after their enrolment ends
- Export capability is tested periodically, not only at the point of exit

**Validation Gates**:

- [ ] Export capability verified by test, not by contract reading alone
- [ ] Export formats open and documented
- [ ] Export scope covers content, configuration, and user-generated work
- [ ] Student-facing export available for portfolio and evidence artifacts
- [ ] Termination-assistance obligations present in contract

---

## III. Integration and Application Principles

### 10. Interface-Mediated Integration

**Principle Statement**:
Systems MUST integrate through published, versioned interfaces. Direct database access across system boundaries, shared file locations as an integration mechanism, and manual transfer of data between systems are prohibited.

**Rationale**:
The ecosystem's most fragile integrations are precisely those using flat files on shared storage, manual exports, and undocumented scripts [PP-C7]. These mechanisms create silent failure, unclear ownership, and — where personal information is involved — direct privacy exposure [PP-C11].

**Implications**:

- Integration contracts are published, versioned, and independently testable
- Flat-file exchange over shared storage is not an acceptable target-state mechanism
- Manual transfer steps in a production flow are architectural defects with remediation plans
- Interface changes are versioned with a backward-compatibility and deprecation policy
- Each integration has a named owner accountable for its operation

**Validation Gates**:

- [ ] Every integration uses a published, versioned interface
- [ ] No direct cross-boundary database access
- [ ] No shared-storage file exchange in target state
- [ ] No manual step in any production data flow
- [ ] Named owner recorded per integration

---

### 11. Event-Driven and Near-Real-Time by Default

**Principle Statement**:
Integrations conveying changes to identity, enrolment, role, or grade MUST propagate those changes in near-real-time. Scheduled batch transfer is permitted only where a documented constraint prevents event-driven exchange, and requires a recorded exception.

**Rationale**:
Overnight batch cycles mean access and role state are wrong for up to a day. That has direct consequences: students unable to reach materials, staff without marking access, and — for withdrawals — access persisting after entitlement ends [PP-C11]. The requirement is explicit and rated Must [PP-C14].

**Implications**:

- Change events are published by the authoritative source and consumed by dependent systems
- Delivery guarantees, ordering, and replay behaviour are defined per event type
- Failed propagation is detected and alerted, not discovered by user report
- Batch remains acceptable for bulk reconciliation and genuine periodic processes, not for change propagation
- Where a platform cannot consume events, the limitation is recorded as an exception with a review date

**Validation Gates**:

- [ ] Change propagation for identity, enrolment, role, and grade meets the defined latency target
- [ ] Event schemas published and versioned
- [ ] Delivery guarantees and replay behaviour defined
- [ ] Propagation failures alerted automatically
- [ ] Each remaining batch flow carries a documented exception and review date

---

### 12. Automated Identity Lifecycle

**Principle Statement**:
Account provisioning, role assignment, and deprovisioning MUST be automated and driven from the authoritative source. Manual account creation, manual role assignment, and bulk user file loads are prohibited in production.

**Rationale**:
Manual provisioning produces two failures that compound: people who cannot access what they need, and people who retain access they should have lost. Manual cohort file handling additionally creates unnecessary copies of personal information [PP-C11]. The requirement to eliminate manual loads is rated Must [PP-C15].

**Implications**:

- Access derives from authoritative role data; it is not granted per platform by request
- Deprovisioning is automatic and prompt on withdrawal, completion, or role change
- Casual, sessional, and short-tenure staff are provisioned through the same automated path as continuing staff — the common source of manual workaround
- Access review is possible centrally, across platforms, without per-platform inspection
- Shared and generic accounts are prohibited; every action is attributable to an individual

**Validation Gates**:

- [ ] All provisioning automated from the authoritative source
- [ ] Deprovisioning occurs automatically within the defined window
- [ ] No manual file-based user loads in production
- [ ] Casual and sessional staff covered by the automated path
- [ ] No shared or generic accounts in production
- [ ] Cross-platform access review possible from a single view

---

### 13. Reproducible, Documented Automation

**Principle Statement**:
Operational automation MUST be documented, version-controlled, and executable by more than one person. Automation that exists only as undocumented scripts held by an individual is prohibited.

**Rationale**:
Course cloning currently runs on semi-manual, undocumented scripts with a single-person dependency [PP-C7]. This is an availability risk at the busiest point in the academic calendar, and it is a knowledge risk that grows silently until the individual is unavailable.

**Implications**:

- Automation is held in version control with its configuration
- Execution is logged, auditable, and attributable
- At least two people can execute and troubleshoot any production automation
- Self-service is preferred over request-driven execution where the process is well understood
- Rollback or recovery behaviour is defined for automation that modifies teaching-critical state

**Validation Gates**:

- [ ] All production automation version-controlled
- [ ] Execution logged and attributable
- [ ] No single-person dependency for any production process
- [ ] Runbook exists and has been followed by a second person
- [ ] Rollback or recovery path defined and tested

---

## IV. Quality Attribute Principles

### 14. Accessibility by Default

**Principle Statement**:
All student-facing platforms and materials MUST meet WCAG 2.2 Level AA. Accessibility is assessed during evaluation and before release — never remediated after deployment.

**Rationale**:
Accessibility is a Must-priority requirement carrying legal and ethical weight [PP-C16]. Retrofitting is materially more expensive than designing correctly, and a platform selected without accessibility assessment commits the university to that cost for the life of the contract.

**Implications**:

- Accessibility conformance evidence is a mandatory evaluation criterion for student-facing platforms
- Vendor conformance claims are verified, not accepted at face value
- Captioning, keyboard navigation, and assistive-technology compatibility are baseline expectations
- Authoring tools support staff in producing accessible content by default
- Known conformance gaps are recorded with remediation commitments and dates

**Validation Gates**:

- [ ] WCAG 2.2 AA conformance evidence obtained and independently verified
- [ ] Accessibility included as a weighted evaluation criterion
- [ ] Captioning available for recorded and live content
- [ ] Keyboard and assistive-technology navigation tested
- [ ] Outstanding gaps recorded with owner and remediation date

---

### 15. Availability Aligned to the Teaching Calendar

**Principle Statement**:
Core teaching platforms MUST meet defined availability targets during teaching periods, with change and maintenance scheduled around the academic calendar rather than the operational one.

**Rationale**:
Availability requirements for teaching platforms are not uniform across the year. An outage during assessment week and the same outage in the inter-semester break are entirely different events. The 99.9% target during teaching periods is a Must-priority requirement [PP-C17].

**Implications**:

- Availability targets are stated per platform and differentiated by academic period
- Assessment and examination periods carry elevated protection, including change freezes
- Vendor service levels are verified against these targets at contract negotiation, not assumed
- Degraded-mode behaviour is defined for teaching-critical platforms
- Dependency chains are understood — a platform is only as available as what it depends on

**Validation Gates**:

- [ ] Availability targets defined per platform and academic period
- [ ] Change freeze windows defined for assessment periods
- [ ] Vendor service levels verified against stated targets
- [ ] Degraded-mode behaviour documented for teaching-critical platforms
- [ ] Dependency chain mapped and its aggregate availability understood

---

### 16. Layered Security Posture

**Principle Statement**:
Access to all platforms MUST use institutional single sign-on with multi-factor authentication. Local accounts are prohibited. The estate MUST demonstrably progress toward the institution's stated security maturity targets.

**Rationale**:
Single sign-on with multi-factor authentication is a Must-priority requirement, and demonstrable alignment to the Essential Eight maturity targets is a separate Must [PP-C18]. Two platforms currently permit local accounts, which breaches the first of these directly [PP-C19]. In a heavily SaaS-based estate, identity is the primary control surface — a local account is a hole in it.

**Implications**:

- Institutional single sign-on with multi-factor authentication is a mandatory selection criterion; a platform that cannot support it is not adopted
- Existing local-account exceptions carry remediation plans with dates, and are not renewed indefinitely
- Administrative privilege is minimised, individually attributable, and time-boxed where practical
- Backup and recovery capability is verified per platform rather than assumed from vendor description
- Security maturity is assessed against the stated target, with gaps tracked as accountable items rather than noted and left
- Security posture is re-assessed at contract renewal

**Validation Gates**:

- [ ] Institutional single sign-on with multi-factor authentication enforced on all platforms
- [ ] No local accounts in production; existing exceptions carry dated remediation plans
- [ ] Administrative privilege individually attributable, with no shared administrative accounts
- [ ] Backup and export coverage verified by test per platform
- [ ] Security maturity assessed against target with gaps owned and tracked
- [ ] Security assessment repeated at contract renewal

---

### 17. Observable Integrations and Services

**Principle Statement**:
Integrations and teaching-critical services MUST emit sufficient telemetry to detect failure, diagnose cause, and confirm recovery — without requiring a user to report the problem first.

**Rationale**:
Several current integration failures are discovered by users: a role that was not assigned, a group that did not appear, a grade that did not arrive [PP-C7]. Detection by user report means the failure has already had academic consequence by the time it is known.

**Implications**:

- Every integration reports success, failure, and volume per run or per event stream
- Alerting is directed to a named owner with an actionable runbook
- Records that fail to propagate are visible and recoverable, not silently discarded
- Telemetry is retained long enough to investigate patterns, not merely the current incident
- Monitoring covers the flow end-to-end, not only the availability of the endpoints it connects

**Validation Gates**:

- [ ] Success, failure, and volume telemetry emitted per integration
- [ ] Alerts routed to a named owner with a runbook
- [ ] Failed records visible and recoverable
- [ ] End-to-end flow monitored, not only endpoint availability
- [ ] Telemetry retention sufficient for pattern analysis

---

## V. Governance and Lifecycle Principles

### 18. Evidence-Based Capability Investment

**Principle Statement**:
New or changed learning technology MUST pass architectural review before procurement or build commences. Review assesses capability duplication, integration impact, privacy posture, accessibility, and total cost — not functional fit alone.

**Rationale**:
The RIFF Review exists precisely to prevent capability being acquired on functional merit while its integration, privacy, and cost consequences go unexamined [PP-C2]. Reviewing after selection is reviewing after the decision has effectively been made.

**Implications**:

- Architectural review precedes commitment, not deployment
- Review scope explicitly covers duplication against the current capability map, integration impact, privacy posture, accessibility conformance, and whole-of-life cost
- Review outcomes are recorded as decisions with rationale, forming an auditable decision register
- Business case submissions include the review as supporting evidence
- A request may be paused or closed without progressing, with the agreement of key stakeholders

**Validation Gates**:

- [ ] Architectural review completed before procurement or build commitment
- [ ] Duplication assessed against the current capability map
- [ ] Integration, privacy, accessibility, and cost impacts assessed and recorded
- [ ] Decision recorded with rationale and options considered
- [ ] Business case references the completed review

---

### 19. Realise Licensed Capability Before New Spend

**Principle Statement**:
Where a required capability already exists within a licensed platform, the university MUST evaluate configuring and adopting it before acquiring a new platform. Acquiring new capability that duplicates unrealised licensed capability requires an approved exception.

**Rationale**:
The ecosystem currently pays for functionality that was never configured or switched on [PP-C3]. Total licence spend is expected to reduce or hold flat while Must-priority capability gaps are closed [PP-C20] — an outcome that is only achievable by realising what is already owned.

**Implications**:

- Licensed-but-unconfigured capability is inventoried and visible during capability assessment
- The cost of configuring existing capability is compared against acquisition on a whole-of-life basis, including change and support effort
- Genuine unsuitability of an incumbent platform is a valid reason to acquire — undiscovered capability is not
- Vendor roadmap capability arriving within the contract term is considered before external acquisition
- Contract renewal is treated as a decision point, with unrealised capability explicitly reviewed

**Validation Gates**:

- [ ] Licensed-but-unconfigured capability inventoried per platform
- [ ] Configuration option costed before acquisition is approved
- [ ] Incumbent unsuitability documented where new acquisition proceeds
- [ ] In-term vendor roadmap capability considered
- [ ] Unrealised capability reviewed at each contract renewal

---

## VI. Exception Process

Principles are mandatory unless a documented exception is approved through the RIFF Review process [PP-C2].

**Valid Exception Reasons**:

- Technical constraints that genuinely prevent compliance
- Regulatory, contractual, or legal requirements
- Transitional state during migration or rationalisation
- Pilot or proof-of-concept with a defined end date

**Not Valid Exception Reasons**:

- Local preference or familiarity
- Delivery convenience or schedule pressure alone
- "The vendor does not support it" — without evidence that no compliant alternative exists

**Exception Request Requirements**:

- [ ] Principle identified and nature of the deviation stated
- [ ] Business or technical justification provided
- [ ] Alternative approach and compensating controls described
- [ ] Risk assessment with mitigation plan
- [ ] Expiry date — exceptions are time-bound without exception
- [ ] Remediation plan to reach compliance

**Approval Path**:

1. Exception request submitted with the solution request
2. Digital & IT high-level analysis and Learning Innovation guidance
3. RIFF Review assessment
4. Education Committee approval
5. Operations Committee or University Executive where financial or strategic thresholds are exceeded
6. Exception recorded, with review at expiry

---

## VII. Governance and Compliance

### Architecture Review Gates

**Discovery**:

- [ ] Principles understood by the project team
- [ ] High-level approach aligns with principles
- [ ] Capability duplication assessed against the current map
- [ ] No obvious principle violations

**Design**:

- [ ] Detailed architecture documented
- [ ] Compliance validated principle by principle
- [ ] Exceptions requested and approved
- [ ] Data, privacy, accessibility, and security principles specifically validated

**Pre-Deployment**:

- [ ] Implementation matches approved architecture
- [ ] All validation gates passed
- [ ] Operational ownership and runbooks in place
- [ ] Outstanding exceptions carry current expiry dates

### Enforcement

- Architectural review is mandatory for all new and changed learning technology
- Principle violations are remediated before deployment or carry an approved, time-bound exception
- Exceptions are reviewed at expiry, not automatically renewed
- Compliance of live systems is reviewed at contract renewal

---

## VIII. Appendix

### Principle to Requirement Traceability

Principles are institution-wide and outlive any single project. This table records where each principle is reinforced by a Must or Should priority requirement from the academic survey register [PP-C21], which supports WP7 requirements mapping.

| Principle | Reinforcing Requirements |
|-----------|--------------------------|
| 1. Single Learning Entry Point | REQ-007 |
| 2. Deliberate Capability Boundaries | REQ-035 |
| 3. Consistent Experience Across Schools | REQ-001 |
| 4. Discipline Specialisation at the Edge | REQ-005, REQ-006 |
| 5. Single Source of Truth for Core Entities | REQ-024 |
| 6. Canonical Data Model | REQ-027 |
| 7. Privacy by Design and Data Minimisation | REQ-030 |
| 8. Data Residency and Cross-Border Accountability | REQ-030 |
| 9. Data Portability and Exit | REQ-015, REQ-034 |
| 10. Interface-Mediated Integration | REQ-025, REQ-028 |
| 11. Event-Driven and Near-Real-Time by Default | REQ-012, REQ-023 |
| 12. Automated Identity Lifecycle | REQ-025, REQ-031 |
| 13. Reproducible, Documented Automation | REQ-026 |
| 14. Accessibility by Default | REQ-029 |
| 15. Availability Aligned to the Teaching Calendar | REQ-032 |
| 16. Layered Security Posture | REQ-031, REQ-033 |
| 17. Observable Integrations and Services | REQ-023, REQ-028 |
| 18. Evidence-Based Capability Investment | REQ-035 |
| 19. Realise Licensed Capability Before New Spend | REQ-035 |

### Consistency Note

Principles 2 and 4 are read together: Principle 2 requires declared capability boundaries and Principle 4 permits discipline-specific tooling outside the core set. These are not in tension — a specialist tool adopted under Principle 4 is recorded as a declared boundary under Principle 2, not as an undeclared overlap.

Principles 10 and 11 are likewise complementary: Principle 10 governs the *mechanism* of integration (published interfaces), Principle 11 governs its *timeliness* (near-real-time propagation). A compliant integration satisfies both.

---

## External References

> This section provides traceability from generated content back to source documents.

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| PP-D1 | consultant-brief.md | Engagement brief | `demo-inputs/` | Consultant Engagement Brief — L&T Baseline Strategy, WP1–WP9 |
| PP-D2 | capability-taxonomy.md | Foundation artifact | `demo-inputs/` | Eight-category L&T capability taxonomy |
| PP-D3 | system-landscape.md | Foundation artifact | `demo-inputs/` | System categorisation map with usage status and known integrations |
| PP-D4 | solution-governance-process.md | Foundation artifact | `demo-inputs/` | RIFF Review governance and approval process |
| PP-D5 | requirements-register.md | Requirements input | `demo-inputs/` | Consolidated academic survey requirements (REQ-001 to REQ-035) |
| PP-D6 | privacy-context.md | Compliance input | `demo-inputs/` | Personal information inventory, data flows, Essential Eight self-assessment |
| PP-D7 | stakeholders.md | Engagement input | `demo-inputs/` | Engagement stakeholder register |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| PP-C1 | PP-D1 | §2, WP1 | Scope | "Establish principles covering: LMS role and boundaries, integration approach, platform governance, student experience consistency" |
| PP-C2 | PP-D4 | Rules | Governance | "Solutions duplicating capability already licensed (per the system landscape map) must justify why the incumbent tool is unsuitable." |
| PP-C3 | PP-D3 | Notes | Context | "MS Teams — investigation planned for 2027 to establish a seamless platform experience across collaboration, learning delivery and lecture capture (overlaps with Zoom and Echo360 — key rationalisation candidate)." |
| PP-C4 | PP-D5 | REQ-007 | Requirement | "Students shall access all unit materials, activities and grades through a single entry point (the LMS)" |
| PP-C5 | PP-D2 | Table | Taxonomy | "Every current and proposed tool is categorised against this taxonomy to enable cross-system comparison, duplication analysis and rationalisation decisions." |
| PP-C6 | PP-D5 | REQ-005, REQ-006 | Requirement | "Music & Performing Arts staff shall distribute interactive notation and audio-production project files as learning materials"; "Health Sciences staff shall deliver clinical simulation scenarios with device integration in simulation labs" |
| PP-C7 | PP-D3 | Known integrations | Context | "Fragile; role assignment failures; no intra-day sync"; "Undocumented; single-person dependency"; "Drift between PeopleSoft and Blackboard hierarchies" |
| PP-C8 | PP-D5 | REQ-024 | Requirement | "Institutional role assignment (coordinator, tutor, marker) shall be derived from a single authoritative source and synchronised to all L&T systems" |
| PP-C9 | PP-D1 | §2, WP5 | Scope | "Define a canonical data model for key entities: student, course, enrolment" |
| PP-C10 | PP-D5 | REQ-030 | Requirement | "All platforms holding personal information shall comply with the Privacy Act 1988 (APPs), with data residency in Australia preferred and APP 8 assessed for any offshore disclosure" |
| PP-C11 | PP-D6 | §2 | Privacy | "Flat-files at rest on shared storage; stale de-provisioning (access persists up to 24h after withdrawal)"; "Human error; screenshots/exports circulating via email"; "No defined retention or minimisation rules" |
| PP-C12 | PP-D6 | §1 | Privacy | "APP 8 triggers: classes 3, 4 (partial), 6 and 7 involve offshore disclosure under the assumed hosting — the PIA must assess cross-border disclosure accountability, contract clauses and the practicability of AU-region alternatives." |
| PP-C13 | PP-D5 | REQ-034 | Requirement | "Vendor contracts shall permit export of all university data in open formats on termination" |
| PP-C14 | PP-D5 | REQ-023 | Requirement | "Student, course and enrolment data shall flow from the student information system to the LMS within 15 minutes of change (near-real-time, replacing nightly batch)" |
| PP-C15 | PP-D5 | REQ-025 | Requirement | "User provisioning for lecture capture, portfolio and assessment platforms shall be automated — no manual CSV loads" |
| PP-C16 | PP-D5 | REQ-029 | Requirement | "All student-facing tools shall conform to WCAG 2.2 AA accessibility" |
| PP-C17 | PP-D5 | REQ-032 | Requirement | "Core teaching platforms (LMS, capture, video conferencing) shall meet 99.9% availability during teaching periods" |
| PP-C18 | PP-D5 | REQ-031, REQ-033 | Requirement | "Authentication to all L&T platforms shall use university single sign-on with MFA; no local accounts"; "The ecosystem shall demonstrate alignment to the ASD Essential Eight maturity targets set by Digital & IT" |
| PP-C19 | PP-D6 | §3 | Security | Multi-factor authentication row, current ML2 / target ML2: "SSO+MFA enforced; **exception:** two tools still allow local accounts (breaches REQ-031)" |
| PP-C20 | PP-D5 | REQ-035 | Requirement | "Total ecosystem licence spend shall reduce or hold flat while closing Must-priority capability gaps" |
| PP-C21 | PP-D5 | Header | Provenance | "Consolidated requirements from the 2026 academic survey (412 responses across all schools)." |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| stakeholders.md (PP-D7) | `demo-inputs/` | Read for document ownership and approval path; stakeholder analysis is produced separately by `/arckit:stakeholders` |

---

**Generated by**: ArcKit `/arckit:principles` command
**Generated on**: 2026-07-26
**ArcKit Version**: 6.4.0
**Project**: The University of Funk — Global / Cross-Project (Project 000)
**Model**: Claude Opus 5 (1M context)

<!-- arckit-provenance:start -->

## Build Provenance

_Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix._

| Field | Value |
|-------|-------|
| Requested Effort | `high` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-07-26T09:33:13.109Z |

<!-- arckit-provenance:end -->
