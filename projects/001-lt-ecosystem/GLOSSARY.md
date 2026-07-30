# Glossary: Learning & Teaching Baseline Strategy (L&T Technology Ecosystem)

> **Template Origin**: Official | **ArcKit Version**: 6.7.5 | **Command**: `/arckit:glossary`
>
> **Filename note**: this document's canonical Document ID is `ARC-001-GLOS-v1.0`. It is
> stored as `GLOSSARY.md` because the `validate-arc-filename.mjs` hook registry
> (`config/doc-types.mjs` in arckit 6.7.5) does not yet include the `GLOS` document-type
> code, and therefore rejects `ARC-001-GLOS-v1.0.md`. Rename to
> `ARC-001-GLOS-v1.0.md` once `GLOS` is registered.

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-GLOS-v1.0 |
| **Document Type** | Project Glossary |
| **Project** | Learning & Teaching Baseline Strategy (Project 001) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-29 |
| **Last Modified** | 2026-07-29 |
| **Review Date** | 2026-08-28 |
| **Review Cycle** | Quarterly |
| **Owner** | Solution Architect (Digital & IT) |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Project Team, Architecture Team |

> **Note**: The University of Funk (UoF) is a fictional Australian higher-education
> institution used for demonstration. This glossary defines terminology only; it makes
> no factual claim about any real institution or vendor.

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-29 | ArcKit AI | Initial creation from `/arckit:glossary` command | [PENDING] | [PENDING] |

---

## Purpose

This glossary provides a single, authoritative reference for all terminology, acronyms, and abbreviations used within the Learning & Teaching Baseline Strategy project. It ensures consistent understanding across academic, Digital & IT, privacy and governance stakeholders, reduces ambiguity in architecture artefacts, and supports onboarding.

**Scope**: All terms, acronyms and abbreviations referenced in project architecture documents, requirements, data model, decisions and foundation inputs.

**Authority**: Architecture team, with contributions from Learning Innovation, Digital & IT, and Privacy & Records.

**Usage**: All project documentation SHOULD reference this glossary for canonical definitions. Where a term has a project-specific meaning that differs from common usage, the glossary definition takes precedence.

---

## Conventions

- Terms are listed in **alphabetical order** within each section
- **Bold** terms within definitions indicate cross-references to other glossary entries
- The **Source Artifact** column references the document where the term is defined or most used
- The **Category** column classifies terms to aid filtering (Business, Technical, Governance, Financial, Data, Security, Platform)
- Acronyms and abbreviations are listed separately for quick lookup
- Definitions not stated verbatim in a source are marked *(Inferred from context)*

---

## Glossary

### A–C

| Term | Definition | Source Artifact | Category |
|------|------------|-----------------|----------|
| Academic requestor | The academic staff member who identifies a learning & teaching technology need and submits the solution request that enters the **RIFF governance process**. | solution-governance-process.md [GOV-C1] | Governance |
| Active Learning | Capability category 5 of the taxonomy: systems enabling students to engage in their learning (thinking, discussing, investigating, creating) across engagement with content, other students and teachers. | capability-taxonomy.md [CT-C1] | Business |
| Allocate+ | Timetabling and student allocation platform; source of timetable and group allocation data feeding group creation in the **LMS**. | system-landscape.md | Platform |
| APP 8 | Australian Privacy Principle 8 (cross-border disclosure): before disclosing personal information to an overseas recipient, an entity must take reasonable steps to ensure the recipient does not breach the **APPs**, and generally remains accountable for the recipient's acts. Triggered by offshore-hosted platforms in this project. | privacy-context.md [PC-C1]; ARC-001-DATA-v1.0 | Security |
| Assessment & Progress Tracking | Capability category 7: systems enabling educators to evaluate, measure and document academic readiness, learning progress, skill acquisition and educational needs, including feedback and milestone tracking against learning outcomes. | capability-taxonomy.md | Business |
| Australian Privacy Principles (APPs) | The 13 principles in Schedule 1 of the **Privacy Act 1988** governing collection, use, disclosure, quality, security, access and correction of personal information by covered entities. | privacy-context.md; ARC-001-DATA-v1.0 | Security |
| Blackboard | The institution's incumbent **LMS** and single learning entry point for students. | system-landscape.md | Platform |
| Canonical data model | An institution-agreed, platform-neutral definition of core entities and their attributes (e.g. PERSON, UNIT, ENROLMENT), used as the shared contract for integration so each system maps once to the canonical form rather than point-to-point to every peer. | ARC-000-PRIN-v1.1 (Principle 6); ARC-001-DATA-v1.0 | Data |
| Capability category | One of the eight categories of the **capability taxonomy** against which every current and proposed tool is classified to enable duplication analysis and rationalisation. | capability-taxonomy.md | Business |
| Collaboration | Capability category 6: systems enabling groups to work together to solve problems, complete tasks and learn new concepts. | capability-taxonomy.md | Business |
| Core (tool designation) | A tool supported and offered institution-wide across all schools, as distinct from a **discipline-specific** tool. *(Inferred from context)* | system-landscape.md | Business |
| Course Design | Capability category 1: systems enabling course design — learning objectives, user interface and experience, look & feel, site aesthetics and instructional strategies. | capability-taxonomy.md | Business |
| Course cloning | Automated copying of a prior unit site into a new **teaching period** offering; currently semi-manual scripted with a single-person dependency. | system-landscape.md | Technical |

### D–H

| Term | Definition | Source Artifact | Category |
|------|------------|-----------------|----------|
| Data residency | The geographic region in which data is stored and processed; material to **APP 8** accountability and to the assumed AU / US / EU hosting of platforms in the estate. | ARC-000-PRIN-v1.1 (Principle 8); privacy-context.md | Security |
| De-provisioning | Removal of access when a person's enrolment or employment ends; currently stale by up to 24 hours because of the nightly batch feed. | privacy-context.md [PC-C2] | Security |
| Digital & IT | The institution's technology function; performs high-level analysis, technical feasibility and integration-impact assessment in the **RIFF governance process**, and owns the **Essential Eight** target. | solution-governance-process.md | Governance |
| Discipline-specific | A tool supported for a particular school or discipline rather than institution-wide (e.g. music notation, clinical simulation), consistent with specialisation at the edge. | system-landscape.md; ARC-000-PRIN-v1.1 (Principle 4) | Business |
| Echo360 | Lecture capture and video platform used for **Learning Capture** and delivery; provisioned via **LTI** plus manual CSV. | system-landscape.md | Platform |
| Education Committee | Academic governance body granting academic approval of L&T technology solution requests; the first approval step after solution analysis and design. | solution-governance-process.md | Governance |
| Eligible data breach | Under the **NDB scheme**, unauthorised access, disclosure or loss of personal information that is likely to result in serious harm to any affected individual — the test that triggers **OAIC** and individual notification. | privacy-context.md | Security |
| Essential Eight | The Australian Signals Directorate's eight prioritised mitigation strategies (application control; patch applications; configure Microsoft Office macro settings; user application hardening; restrict administrative privileges; patch operating systems; multi-factor authentication; regular backups), assessed at maturity levels **ML0–ML3**. | privacy-context.md; ARC-001-REQ-v1.0 | Security |
| Evaluation & Analytics | Capability category 8: systems enabling data access and analysis for monitoring and evaluation to inform course design. | capability-taxonomy.md | Business |
| Evasys | Course and teaching evaluation survey platform. | system-landscape.md | Platform |
| ExamSoft | Secure/lockdown examination and remote-proctoring platform. | system-landscape.md | Platform |
| H5P | Open interactive-content authoring format and toolset used for quizzes and embedded activities. | system-landscape.md | Platform |

### I–M

| Term | Definition | Source Artifact | Category |
|------|------------|-----------------|----------|
| Institutional hierarchy | The organisational structure (school, discipline, program) mastered in **PeopleSoft** and mirrored into the **LMS**; currently subject to drift. | system-landscape.md | Data |
| Institutional role assignment | The assignment of a person to a role (e.g. unit coordinator, tutor, student) in a given offering; subject of ADR-002 on the authoritative source. | ARC-001-DATA-v1.0 (E-006); ADR-002 | Data |
| Integration broker | A mediating integration component (message/API broker) that decouples systems by receiving, transforming and routing data between them using the **canonical data model**, replacing point-to-point flat-file exchange. | ADR-001; ARC-001-REQ-v1.0 | Technical |
| Integration plane | The set of environments and runtime components hosting the **integration broker** and related services; deployment topology defined in ADR-005. | ADR-005 | Technical |
| iSimulate | Clinical simulation tooling used in Health Sciences simulation labs. | system-landscape.md | Platform |
| Kuracloud | Discipline-specific interactive practical/lab authoring and delivery platform; internal support model to be confirmed. | system-landscape.md | Platform |
| Leganto | Reading list and course-resource management platform. | system-landscape.md | Platform |
| Learning Capture | Capability category 4: systems enabling capture of course delivery (lectures, performances, labs) for streaming or later consumption. | capability-taxonomy.md | Business |
| Learning Delivery | Capability category 3: systems enabling delivery of course resources to students. | capability-taxonomy.md | Business |
| Learning Innovation | The function providing information, guidance and pedagogical-fit advice to requestors and facilitating the **RIFF Review**. | solution-governance-process.md | Governance |
| Learning Management System (LMS) | The core platform through which students access unit materials, activities and grades — the single learning entry point. At UoF this is **Blackboard**. | ARC-001-REQ-v1.0 (REQ-007); ARC-000-PRIN-v1.1 (Principle 1) | Platform |
| Learning Resources | Capability category 2: systems enabling creation, management, publication, curation and editing of learning resources in a variety of digital formats. | capability-taxonomy.md | Business |
| LinkedIn Learning | Third-party on-demand professional learning content library. | system-landscape.md | Platform |
| LTI 1.3 Advantage | The 1EdTech (formerly IMS Global) Learning Tools Interoperability 1.3 standard together with its Advantage services — **Deep Linking**, **NRPS** (Names and Role Provisioning Services) and **AGS** (Assignment and Grade Services) — providing OAuth2/OIDC-secured tool launch, roster retrieval and grade return between the **LMS** and external tools. | ARC-001-REQ-v1.0; ADR-002 | Technical |
| Maturity level (ML0–ML3) | The **Essential Eight** maturity scale: ML0 (not aligned), ML1, ML2, ML3 (increasing resistance to increasingly capable adversaries). The project target is ML2 across the SaaS-heavy L&T estate. | privacy-context.md | Security |
| Miro | Online whiteboard/visual collaboration tool; under investigation, not currently in use. | system-landscape.md | Platform |
| MoSCoW | Requirement prioritisation scheme: **Must** have, **Should** have, **Could** have, **Won't** have (this time). Priorities in the requirements register were assigned by the project team with the **Education Committee**. | requirements-register.md [RR-C1] | Business |
| MS Teams | Microsoft collaboration, meeting and delivery platform; a 2027 investigation candidate for consolidating collaboration, delivery and capture. | system-landscape.md | Platform |
| MuseScore / Ableton Live | Music notation and digital audio production tools used by the School of Music & Performing Arts as **discipline-specific** learning resources. | system-landscape.md | Platform |

### N–R

| Term | Definition | Source Artifact | Category |
|------|------------|-----------------|----------|
| Notifiable Data Breach (NDB) scheme | The scheme under Part IIIC of the **Privacy Act 1988** requiring assessment of a suspected breach (with an investigation clock of up to 30 days) and, where an **eligible data breach** is confirmed, notification to the **OAIC** and to affected individuals. | privacy-context.md | Security |
| OAIC | Office of the Australian Information Commissioner — the regulator for the **Privacy Act 1988** and the **NDB scheme**. | privacy-context.md | Governance |
| OnExam | Online examination platform under investigation; extent of use at UoF to be determined. | system-landscape.md | Platform |
| OneRoster | 1EdTech roster and gradebook exchange standard referenced as an option for course, enrolment and grade interchange. | ARC-001-REQ-v1.0 | Technical |
| Operations Committee | Governance body providing operational and financial approval where thresholds are exceeded, after **Education Committee** approval and alongside or before **University Executive** review. | solution-governance-process.md | Governance |
| Padlet | Lightweight collaborative board tool for active learning. | system-landscape.md | Platform |
| PebblePad | Portfolio and workplace-learning platform holding student portfolio evidence. | system-landscape.md | Platform |
| PeopleSoft | The student information system of record for person, enrolment, offering and institutional hierarchy data. | system-landscape.md; ARC-001-DATA-v1.0 | Platform |
| Personal information (PI) | Information or an opinion about an identified individual, or an individual who is reasonably identifiable, as defined in the **Privacy Act 1988**. | privacy-context.md; ARC-001-DATA-v1.0 (E-019) | Data |
| Placement allocation | The assignment of a student to a professional placement host and supervisor, recorded in **Sonia**; associated records include **sensitive information**. | ARC-001-DATA-v1.0 (E-014) | Data |
| Privacy Act 1988 | The Commonwealth Act (Cth) regulating handling of **personal information** in Australia, containing the **APPs** and the **NDB scheme**, administered by the **OAIC**. | privacy-context.md; ARC-001-DATA-v1.0 | Governance |
| Qualtrics | Survey and experience-management platform used for evaluation and analytics. | system-landscape.md | Platform |
| Rationalisation | Deliberate reduction or consolidation of overlapping tools within a **capability category** to remove duplication and realise already-licensed capability before new spend. | system-landscape.md; ARC-000-PRIN-v1.1 (Principle 19) | Business |
| Remark | Scanned/optical response marking tool used for paper-based assessment processing. | system-landscape.md | Platform |
| RIFF Review | *Review of Innovation, Fit & Function* — the central gate of the L&T technology governance process, assessing a solution request for architectural fit, capability duplication, integration impact and total cost before any procurement or build proceeds. Its output is supporting documentation for business cases. | solution-governance-process.md [GOV-C2] | Governance |
| RIFF governance process | The end-to-end approval flow for new or changed L&T technology: need identified → academic request → Digital & IT analysis → Learning Innovation guidance → **RIFF Review** → solution analysis & design → **Education Committee** → (where required) **Operations Committee** and/or **University Executive** → decision finalised. | solution-governance-process.md | Governance |

### S–Z

| Term | Definition | Source Artifact | Category |
|------|------------|-----------------|----------|
| Sandpit | A non-production teaching/experimentation environment for staff; provisioning planned for 2027 and not yet designed. | system-landscape.md | Technical |
| Sensitive information | A subset of **personal information** attracting higher protection under the **APPs** (including health information); in this project, placement clearance metadata and health-context notes held in **Sonia**. | privacy-context.md; ARC-001-DATA-v1.0 | Security |
| Single source of truth | The principle that each core entity has exactly one authoritative mastering system, from which all others derive. | ARC-000-PRIN-v1.1 (Principle 5) | Data |
| Sonia | Placement management platform holding placement allocations, supervisors and assessments, including **sensitive information**. | system-landscape.md | Platform |
| Turnitin | Text-similarity and AI-writing detection platform, including **PeerMark** peer-review capability. | system-landscape.md | Platform |
| Unit | A single taught subject of study; the primary academic container to which sites, assessments and enrolments attach. | ARC-001-DATA-v1.0 (E-002) | Data |
| Unit offering | A specific delivery of a **unit** in a given **teaching period** and mode. | ARC-001-DATA-v1.0 (E-004) | Data |
| Unit site | The **LMS** course space for a **unit offering**, presenting materials, activities and grades to students. | ARC-001-DATA-v1.0 (E-007) | Data |
| University Executive | The most senior institutional decision-making body; provides strategic and financial approval for solution requests above defined thresholds. | solution-governance-process.md | Governance |
| University of Funk (UoF) | The fictional Australian higher-education institution that is the subject of this demonstration project. | project foundation inputs | Business |
| WCAG 2.2 AA | Web Content Accessibility Guidelines version 2.2, conformance level AA — the accessibility target applied to student-facing L&T platforms and content. | ARC-001-REQ-v1.0; ARC-000-PRIN-v1.1 (Principle 14) | Governance |
| Zoom | Live online class and meeting platform, including breakout rooms, polling and recording. | system-landscape.md | Platform |

---

## Requirement and Artefact Identifier Prefixes

| Prefix | Meaning |
|--------|---------|
| BR-nnn | Business Requirement |
| FR-nnn | Functional Requirement |
| NFR-P-nnn | Non-Functional Requirement — Performance |
| NFR-A-nnn | Non-Functional Requirement — Availability and Resilience |
| NFR-S-nnn | Non-Functional Requirement — Scalability |
| NFR-SEC-nnn | Non-Functional Requirement — Security |
| NFR-C-nnn | Non-Functional Requirement — Compliance and Regulatory |
| NFR-U-nnn | Non-Functional Requirement — Usability and Accessibility |
| NFR-M-nnn | Non-Functional Requirement — Maintainability and Supportability |
| NFR-I-nnn | Non-Functional Requirement — Portability and Interoperability |
| INT-nnn | Integration Requirement |
| DR-nnn | Data Requirement |
| REQ-nnn | Consolidated survey requirement from the external requirements register |
| E-nnn | Data model entity identifier |
| C-n | Requirement conflict and resolution identifier |

### ArcKit artefact type codes in use on this project

| Code | Artefact |
|------|----------|
| PRIN | Architecture Principles (global, project 000) |
| REQ | Requirements Specification |
| STKE | Stakeholder Analysis |
| RISK | Risk Register |
| SOBC | Strategic Outline Business Case |
| DATA | Data Model and Data Governance Specification |
| TRAC | Requirements Traceability Matrix |
| ADR | Architecture Decision Record |
| DIAG | Architecture Diagram set |
| WARD | Wardley Map |
| STRAT | Architecture Strategy |
| PLAN | Project Plan |
| FINOPS | FinOps / Cloud Cost Management Strategy |
| RSCH | Research Report |
| GLOS | Project Glossary (this document) |

---

## Acronyms & Abbreviations

| Acronym | Expansion | Context |
|---------|-----------|---------|
| ADR | Architecture Decision Record | Governance |
| AGS | Assignment and Grade Services | **LTI 1.3 Advantage** service for grade return |
| APP | Australian Privacy Principle | Privacy Act 1988, Schedule 1 |
| ASD | Australian Signals Directorate | Publisher of the **Essential Eight** |
| CIO | Chief Information Officer | Approver of the data model |
| CRUD | Create, Read, Update, Delete | Data governance matrix |
| CSV | Comma-Separated Values | Manual provisioning extracts |
| E8 | Essential Eight | Security maturity assessment |
| ERD | Entity-Relationship Diagram | Data model |
| iPaaS | Integration Platform as a Service | Integration mediation option |
| IP | Intellectual Property | Student-submitted creative work |
| KPI | Key Performance Indicator | Success criteria |
| L&T | Learning & Teaching | Project domain |
| LMS | Learning Management System | Core platform |
| LTI | Learning Tools Interoperability | 1EdTech integration standard |
| MDM | Master Data Management | Data model |
| MFA | Multi-Factor Authentication | Essential Eight mitigation |
| ML0–ML3 | Maturity Level 0 to 3 | Essential Eight maturity scale |
| MoSCoW | Must / Should / Could / Won't have | Requirement prioritisation |
| NDB | Notifiable Data Breach | Privacy Act 1988, Part IIIC |
| NFR | Non-Functional Requirement | Requirements |
| NRPS | Names and Role Provisioning Services | **LTI 1.3 Advantage** roster service |
| OAIC | Office of the Australian Information Commissioner | Privacy regulator |
| OIDC | OpenID Connect | Authentication for LTI 1.3 launch |
| PI | Personal Information | Privacy |
| PIA | Privacy Impact Assessment | Privacy compliance thread |
| SA | Solution Architect | Engagement role |
| SaaS | Software as a Service | Delivery model of most L&T tools |
| SoR | System of Record | Authoritative mastering system |
| SSO | Single Sign-On | Identity and access |
| TCO | Total Cost of Ownership | Investment analysis |
| UoF | The University of Funk | Fictional institution |
| WCAG | Web Content Accessibility Guidelines | Accessibility standard |
| WP | Work Package | Engagement structure (WP2–WP7) |

---

## Standards Reference Table

| Standard | Version | Relevance | URL |
|----------|---------|-----------|-----|
| Privacy Act 1988 (Cth) | Current, incl. Tranche 1 reforms | Governs handling of personal and sensitive information; source of the **APPs** and **NDB scheme** | https://www.legislation.gov.au/C2004A03712 |
| Australian Privacy Principles | 13 APPs (Schedule 1) | APP 8 cross-border disclosure is the key constraint on offshore-hosted platforms | https://www.oaic.gov.au/privacy/australian-privacy-principles |
| Notifiable Data Breach scheme | Privacy Act Part IIIC | Breach assessment and OAIC/individual notification obligations | https://www.oaic.gov.au/privacy/notifiable-data-breaches |
| ASD Essential Eight Maturity Model | ML0–ML3 | Security maturity target (ML2) for the L&T estate | https://www.cyber.gov.au/resources-business-and-government/essential-cyber-security/essential-eight |
| WCAG | 2.2 (Level AA) | Accessibility conformance target for student-facing platforms and content | https://www.w3.org/TR/WCAG22/ |
| 1EdTech LTI Advantage | LTI 1.3 (Deep Linking, NRPS, AGS) | Preferred interface-mediated integration standard between LMS and tools | https://www.1edtech.org/standards/lti |
| 1EdTech OneRoster | 1.2 | Option for roster and gradebook interchange | https://www.1edtech.org/standards/oneroster |

---

## Traceability

| Document | Document ID | Terms Contributed |
|----------|-------------|-------------------|
| Requirements Specification | ARC-001-REQ-v1.0 | 12 terms |
| Data Model & Data Governance | ARC-001-DATA-v1.0 | 14 terms |
| Architecture Principles | ARC-000-PRIN-v1.1 | 8 terms |
| Architecture Decision Records | ARC-001-ADR-001..006-v1.0 | 4 terms |
| Capability Taxonomy (external) | capability-taxonomy.md | 9 terms |
| Solution Governance Process (external) | solution-governance-process.md | 8 terms |
| System Landscape (external) | system-landscape.md | 24 terms |
| Privacy & Security Context (external) | privacy-context.md | 12 terms |
| Requirements Register (external) | requirements-register.md | 2 terms |

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| CT | capability-taxonomy.md | Foundation input | projects/000-global/external/ | Eight L&T capability categories |
| GOV | solution-governance-process.md | Policy | projects/000-global/policies/ | RIFF Review governance process |
| SL | system-landscape.md | Foundation input | projects/001-lt-ecosystem/external/ | Tool categorisation, status and known integrations |
| PC | privacy-context.md | Foundation input | projects/001-lt-ecosystem/external/ | PI inventory, APP 8 triggers, Essential Eight self-assessment |
| RR | requirements-register.md | Foundation input | projects/001-lt-ecosystem/external/ | Consolidated survey requirements with MoSCoW priorities |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| CT-C1 | CT | Category 5 | Capability | "systems and tools that enable students to engage in their learning (thinking, discussing, investigating, creating)" |
| GOV-C1 | GOV | Roles | Governance | "Identifies the need; submits the solution request" |
| GOV-C2 | GOV | Introduction | Governance | "the RIFF Review — Review of Innovation, Fit & Function — which assesses solution requests for architectural fit, capability duplication, integration impact and total cost" |
| PC-C1 | PC | Section 1 | Privacy | "the PIA must assess cross-border disclosure accountability, contract clauses and the practicability of AU-region alternatives" |
| PC-C2 | PC | Section 2 | Privacy | "stale de-provisioning (access persists up to 24h after withdrawal)" |
| RR-C1 | RR | Introduction | Requirements | "MoSCoW priorities were assigned by the project team with the Education Committee" |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| — | — | All supplied inputs were referenced |

---

## Maintenance

This is a living document. It SHOULD be updated whenever a new artefact introduces terminology, and reviewed quarterly. New versions (v2.0, v3.0) are created rather than overwriting, so terminology evolution remains traceable.

**Known gaps and flags**

- Badging software is referenced generically (Badgr, Credly, Milestone under investigation); no product decision has been made, so no term is defined for a selected platform.
- Adobe Creative Suite appears in the landscape but is not elaborated elsewhere in project artefacts.
- Hosting regions, contract terms and Essential Eight maturity levels are stated in the inputs as invented scenario assumptions and must not be read as factual.

---

**Generated by**: ArcKit `/arckit:glossary` command
**Generated on**: 2026-07-29
**ArcKit Version**: 6.7.5
**Project**: Learning & Teaching Baseline Strategy (Project 001)
**AI Model**: Claude Opus 5
**Generation Context**: Compiled from ARC-001-REQ-v1.0, ARC-001-DATA-v1.0, ARC-000-PRIN-v1.1, ARC-001-ADR-001..006, and five external foundation inputs (capability taxonomy, solution governance process, system landscape, privacy context, requirements register).
