# Requirements Register — Academic Survey (Consolidated)

**The University of Funk** | Input to WP7 Requirements Mapping | v1.0 | *fictional demonstration document*

Consolidated requirements from the 2026 academic survey (412 responses across all
schools). Provided as an **input** to the Solution Architecture engagement — the SA
applies these architecturally (WP7) against the WP3 capability data. MoSCoW priorities
were assigned by the project team with the Education Committee.

Sources: `SURVEY` = academic survey · `IT` = Digital & IT · `GOV` = governance/compliance.

## Functional requirements

| ID | Requirement | Category | Priority | Source |
|----|-------------|----------|----------|--------|
| REQ-001 | Staff shall author and reuse course templates so unit sites present a consistent structure and navigation to students across all schools | Course Design | Must | SURVEY |
| REQ-002 | Staff shall build interactive learning content (quizzes, branching scenarios, embedded activities) without specialist development skills | Course Design | Should | SURVEY |
| REQ-003 | Reading lists shall be managed centrally and linked to units, with copyright compliance handled automatically | Learning Resources | Must | SURVEY |
| REQ-004 | Staff shall record, edit and caption instructional video with a single supported toolchain | Learning Resources | Must | SURVEY |
| REQ-005 | Music & Performing Arts staff shall distribute interactive notation and audio-production project files as learning materials | Learning Resources | Should | SURVEY |
| REQ-006 | Health Sciences staff shall deliver clinical simulation scenarios with device integration in simulation labs | Learning Resources | Must | SURVEY |
| REQ-007 | Students shall access all unit materials, activities and grades through a single entry point (the LMS) | Learning Delivery | Must | SURVEY |
| REQ-008 | Live online classes shall support breakout rooms, polling and recording, using one primary platform | Learning Delivery | Must | SURVEY |
| REQ-009 | All timetabled lectures shall be captured automatically and published to the relevant unit site within 4 hours | Learning Capture | Must | SURVEY |
| REQ-010 | Performance and ensemble sessions shall be capturable with multi-camera and high-fidelity audio options | Learning Capture | Could | SURVEY |
| REQ-011 | Students shall collaborate on shared documents, boards and group spaces linked to their unit enrolment groups | Collaboration | Must | SURVEY |
| REQ-012 | Group membership in collaboration tools shall be provisioned automatically from timetable allocation data | Collaboration | Must | SURVEY |
| REQ-013 | Students shall engage in peer review of written and creative work with anonymised marking options | Active Learning | Should | SURVEY |
| REQ-014 | Staff shall run in-class polling and formative checks with results visible in the unit analytics view | Active Learning | Should | SURVEY |
| REQ-015 | Students shall maintain a portfolio of evidence across their whole program, exportable on graduation | Assessment & Progress Tracking | Must | SURVEY |
| REQ-016 | All text-based submissions shall pass through similarity and AI-writing detection before marking | Assessment & Progress Tracking | Must | GOV |
| REQ-017 | High-stakes exams shall be deliverable in a secure, lockdown environment both on-campus and remotely | Assessment & Progress Tracking | Must | SURVEY |
| REQ-018 | Placement supervisors shall enter assessment outcomes once, flowing automatically to the student record | Assessment & Progress Tracking | Must | SURVEY |
| REQ-019 | Micro-credentials and badges shall be issuable against defined skill frameworks | Assessment & Progress Tracking | Could | SURVEY |
| REQ-020 | Unit coordinators shall view engagement, progress and at-risk indicators for their cohort in one dashboard | Evaluation & Analytics | Should | SURVEY |
| REQ-021 | Student evaluation of teaching shall be administered, analysed and reported through one platform | Evaluation & Analytics | Must | GOV |
| REQ-022 | Learning analytics data shall be exportable to the institutional data platform for cross-system analysis | Evaluation & Analytics | Should | IT |

## Integration requirements

| ID | Requirement | Priority | Source |
|----|-------------|----------|--------|
| REQ-023 | Student, course and enrolment data shall flow from the student information system to the LMS within 15 minutes of change (near-real-time, replacing nightly batch) | Must | IT |
| REQ-024 | Institutional role assignment (coordinator, tutor, marker) shall be derived from a single authoritative source and synchronised to all L&T systems | Must | IT |
| REQ-025 | User provisioning for lecture capture, portfolio and assessment platforms shall be automated — no manual CSV loads | Must | IT |
| REQ-026 | Course cloning and rollover shall be an automated, self-service, logged process | Should | IT |
| REQ-027 | A canonical data model shall be defined for student, course and enrolment entities, governing all integrations | Must | IT |
| REQ-028 | Grades captured in placement management shall synchronise bidirectionally with the LMS gradebook | Must | IT |

## Non-functional requirements

| ID | Requirement | Priority | Source |
|----|-------------|----------|--------|
| REQ-029 | All student-facing tools shall conform to WCAG 2.2 AA accessibility | Must | GOV |
| REQ-030 | All platforms holding personal information shall comply with the Privacy Act 1988 (APPs), with data residency in Australia preferred and APP 8 assessed for any offshore disclosure | Must | GOV |
| REQ-031 | Authentication to all L&T platforms shall use university single sign-on with MFA; no local accounts | Must | IT |
| REQ-032 | Core teaching platforms (LMS, capture, video conferencing) shall meet 99.9% availability during teaching periods | Must | IT |
| REQ-033 | The ecosystem shall demonstrate alignment to the ASD Essential Eight maturity targets set by Digital & IT | Must | GOV |
| REQ-034 | Vendor contracts shall permit export of all university data in open formats on termination | Should | GOV |
| REQ-035 | Total ecosystem licence spend shall reduce or hold flat while closing Must-priority capability gaps | Should | GOV |
