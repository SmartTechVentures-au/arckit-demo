# Stakeholder Drivers & Goals Analysis: LMS Ultra Migration & Integration Modernisation

> **Template Origin**: Official | **ArcKit Version**: 6.7.4 | **Command**: `/arckit:stakeholders`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-003-STKE-v1.0 |
| **Document Type** | Stakeholder Drivers & Goals Analysis |
| **Project** | 003-lms-ultra-migration — Blackboard Ultra Migration & Integration Modernisation |
| **Classification** | OFFICIAL-SENSITIVE |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-29 |
| **Last Modified** | 2026-07-29 |
| **Review Cycle** | Fortnightly during project |
| **Next Review Date** | 2026-08-12 |
| **Owner** | Rhonda Bell, Project Manager — L&T Baseline Strategy |
| **Reviewed By** | Sam Okafor, Integration Architect |
| **Approved By** | PENDING — Prof. Otis Hammond, Executive Sponsor |
| **Distribution** | Steering Committee; Project Team; Digital & IT leadership. Not for general circulation. |

> **Classification rationale**: This document names individuals and assesses their influence, resistance, and personal motivations. It is classified OFFICIAL-SENSITIVE and restricted to the steering and project group. The derived engagement plan may be shared more widely; this analysis should not be.

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-29 | ArcKit AI | Initial creation from `/arckit:stakeholders` command | PENDING | PENDING |

---

## Executive Summary

### Purpose

This document identifies the stakeholders of the Blackboard Ultra Migration & Integration Modernisation project (Project 003), their underlying drivers, how those drivers convert into measurable goals, and the outcomes that will demonstrate satisfaction. Project 003 executes the integration architecture defined in `001-lt-ecosystem` ADR-001 and directly re-engineers the PeopleSoft → Blackboard integration — the estate's most fragile and most consequential data flow.

### Key Findings

This project inherits all sixteen named stakeholders from the L&T Baseline Strategy engagement (ARC-001-STKE-v1.0) but refocuses their drivers on a concrete delivery: migrating Blackboard from Learn Original to Ultra, re-engineering seven integrations through a canonical data model, and eliminating the manual handling that is simultaneously the estate's fragility findings and its privacy findings [SL-C1] [PC-C1].

The critical tension has shifted. In Project 001, the fault line was consolidation-versus-best-of-breed — a platform selection question. In Project 003, the platform is decided: Blackboard Ultra is the LMS. The new tensions are:

1. **Migration pace versus academic disruption**: Rhodes (CIO) and Okafor (Integration Architect) want the integration uplift delivered promptly; Castle (Senior Lecturer) and the broader academic community fear simultaneous LMS interface change and integration re-engineering will disrupt teaching.
2. **Integration scope versus team capacity**: ADR-001 specifies a lightweight event broker mediating all nine integrations through a canonical data model. Okafor's team must deliver this while maintaining the current fragile estate — a dual-running burden that Principle 19 constrains from being solved by simply buying middleware [PP-C1].
3. **Privacy remediation as a migration dependency**: Frame's (Privacy Officer) APP findings on manual re-keying and flat-file transfers [PC-C1] are not merely compliance items — they are integration defects that must be remediated as part of the migration, not after it.

### Critical Success Factors

- **CSF-1** — The Ultra migration and integration re-engineering are sequenced so that no teaching period experiences both a changed LMS interface and a changed integration simultaneously.
- **CSF-2** — The PeopleSoft → Blackboard integration moves from nightly flat-file to near-real-time event-driven within the first delivery phase, as this unblocks all other integration work.
- **CSF-3** — The canonical data model defined in ARC-001-DATA-v1.0 is implemented as the integration surface, not bypassed for expedience.
- **CSF-4** — Manual flows carrying personal information — placement grades, CSV provisioning, hierarchy updates — are eliminated, not migrated to the new platform in their current form.
- **CSF-5** — Academic staff experience the migration as effort reduction (automated cloning, better provisioning) rather than mandated rework.

### Stakeholder Alignment Score

**Overall Alignment**: MEDIUM-HIGH

Alignment is materially stronger than in Project 001 because the platform decision is settled and the integration architecture is defined. The remaining disagreement is about pace, sequencing, and the willingness to accept short-term dual-running complexity for long-term architectural coherence. No stakeholder opposes the migration itself — the question is how much disruption they will tolerate in pursuit of it.

---

## Stakeholder Identification

### Internal Stakeholders

| Stakeholder | Role/Department | Influence | Interest | Engagement Strategy |
|-------------|----------------|-----------|----------|---------------------|
| Prof. Otis Hammond | Deputy Vice-Chancellor (Education) — Executive Sponsor | HIGH | HIGH | Manage Closely — chairs steering, owns L&T strategy |
| Cassandra "Cas" Rhodes | Chief Information Officer | HIGH | HIGH | Manage Closely — funds integration uplift, owns E8 targets |
| A/Prof. Pearl Clavinet | Dean of Learning & Teaching; Chair, Education Committee | HIGH | HIGH | Manage Closely — academic approval, change impact on teaching |
| Prof. Stella Groove | Vice-Chancellor | HIGH | LOW | Keep Satisfied — approves funding, no surprises |
| Vernon Ostinato | Chief Financial Officer | HIGH | MEDIUM | Keep Satisfied — migration costs, Blackboard contract terms |
| Rhonda Bell | Project Manager, L&T Baseline Strategy | MEDIUM | HIGH | Manage Closely — day-to-day coordination, migration scheduling |
| Sam Okafor | Integration Architect, Digital & IT | HIGH | HIGH | Manage Closely — owns integration delivery, canonical model implementation |
| Dr. Benny Moog | Director, Learning Technologies | MEDIUM | HIGH | Manage Closely — Ultra configuration, template design, RIFF |
| Dr. Felix Marimba | Academic Lead, Digital Learning | MEDIUM | HIGH | Keep Informed — academic change management, training |
| Grace Tanaka | Procurement & Vendor Manager | MEDIUM | HIGH | Keep Informed — Blackboard contract, Ultra licensing terms |
| Tobias Ohm | Cybersecurity Lead | MEDIUM | HIGH | Keep Satisfied — SSO/MFA enforcement in Ultra, E8 alignment |
| Eleanor Frame | Privacy & Records Officer | MEDIUM | HIGH | Keep Satisfied — manual flow remediation, data migration privacy |
| Prof. Desmond Key | Dean, School of Music & Performing Arts | LOW | HIGH | Keep Informed — LTI integration for discipline tools |
| Prof. Priya Anand | Dean, Faculty of Health Sciences | MEDIUM | HIGH | Keep Informed — placement integration, Sonia grades flow |
| Dr. Wynton Castle | Senior Lecturer; LMS power user | LOW | HIGH | Keep Informed — Ultra interface change, template migration |
| Jazmin Field | President, Student Guild | LOW | HIGH | Keep Informed — student experience during transition |
| Student Administration | (Representative TBD) | MEDIUM | HIGH | Keep Informed — PeopleSoft integration, enrolment lifecycle |
| Human Resources | (Representative TBD) | MEDIUM | MEDIUM | Keep Informed — staff role assignment source (ADR-002) |

> **Stakeholder gap addressed**: ADR-002 identified that Student Administration and Human Resources were absent from the Project 001 stakeholder register despite being joint business owners of E-006 (Institutional Role Assignment). Project 003 includes both as named stakeholders. Representatives should be confirmed in week one.

### External Stakeholders

| Stakeholder | Organization | Relationship | Influence | Interest |
|-------------|--------------|--------------|-----------|----------|
| Anthology (Blackboard) | LMS vendor | Supplier — Ultra migration support, API access, roadmap | HIGH | HIGH |
| Office of the Australian Information Commissioner | OAIC | Privacy regulator — APP compliance during data migration | HIGH | LOW |
| Tertiary Education Quality and Standards Agency | TEQSA | Higher education regulator — assessment integrity during transition | HIGH | LOW |
| Remaining platform vendors (Echo360, PebblePad, Turnitin, etc.) | Various | Integration partners — must re-integrate with Ultra APIs | MEDIUM | HIGH |

### Governance Framework Applicability

The template's UK Government roles (GovS 005, GovS 007) are **not applicable** — The University of Funk is an Australian university. Governance follows the RIFF Review → Education Committee → Operations Committee → University Executive pathway [SGP-C1]. The applicable regulatory overlay is the Privacy Act 1988 and the ASD Essential Eight.

### Stakeholder Power-Interest Grid

```text
                              INTEREST
              Low                              High
        ┌──────────────────────────┬──────────────────────────┐
        │                          │                          │
        │     KEEP SATISFIED       │     MANAGE CLOSELY       │
        │                          │                          │
   High │  • Groove (VC)           │  • Hammond (DVC-E)       │
        │  • OAIC (regulator)      │  • Rhodes (CIO)          │
        │  • TEQSA (regulator)     │  • Clavinet (Dean L&T)   │
        │                          │  • Okafor (Integration)  │
        │                          │  • Anthology (Blackboard)│
 P      │                          │                          │
 O      ├──────────────────────────┼──────────────────────────┤
 W      │                          │                          │
 E      │        MONITOR           │      KEEP INFORMED       │
 R      │                          │                          │
        │                          │  • Bell (PM)             │
   Low  │                          │  • Moog (Learning Tech)  │
        │                          │  • Marimba (Acad Lead)   │
        │                          │  • Tanaka (Procurement)  │
        │                          │  • Castle (Lecturer)     │
        │                          │  • Field (Student Guild) │
        │                          │  • Key (Dean Music)      │
        │                          │  • Anand (Dean Health)   │
        │                          │  • Platform vendors      │
        │                          │  • Student Admin         │
        │                          │  • HR                    │
        └──────────────────────────┴──────────────────────────┘

   MEDIUM-power stakeholders: Ohm and Frame (compliance) lean Keep
   Satisfied; Ostinato has elevated interest compared to Project 001
   because the Blackboard contract is now a direct line item.
```

| Stakeholder | Power | Interest | Quadrant | Engagement Strategy |
|-------------|-------|----------|----------|---------------------|
| Prof. Otis Hammond | HIGH | HIGH | Manage Closely | Fortnightly steering; migration readiness gates |
| Cassandra Rhodes | HIGH | HIGH | Manage Closely | Fortnightly steering; integration funding decisions |
| A/Prof. Pearl Clavinet | HIGH | HIGH | Manage Closely | Education Committee; academic change approval |
| Sam Okafor | HIGH | HIGH | Manage Closely | Weekly working sessions; canonical model delivery |
| Anthology (Blackboard) | HIGH | HIGH | Manage Closely | Migration support engagement; API documentation |
| Prof. Stella Groove | HIGH | LOW | Keep Satisfied | Business case briefing; exception escalation only |
| Vernon Ostinato | HIGH | MEDIUM | Keep Satisfied | Migration cost checkpoints; contract terms |
| OAIC | HIGH | LOW | Keep Satisfied | No direct engagement; compliance evidenced via PIA |
| TEQSA | HIGH | LOW | Keep Satisfied | Assessment integrity evidenced during transition |
| Tobias Ohm | MEDIUM | HIGH | Keep Satisfied | Security architecture review; Ultra SSO/MFA config |
| Eleanor Frame | MEDIUM | HIGH | Keep Satisfied | Data migration privacy assessment; manual flow remediation |
| Rhonda Bell | MEDIUM | HIGH | Manage Closely | Daily/weekly working cadence; migration scheduling |
| Dr. Benny Moog | MEDIUM | HIGH | Manage Closely | Ultra configuration; template design; training plan |
| Dr. Felix Marimba | MEDIUM | HIGH | Keep Informed | Academic change management and communications |
| Grace Tanaka | MEDIUM | HIGH | Keep Informed | Blackboard contract negotiation; Ultra licensing |
| Prof. Priya Anand | MEDIUM | HIGH | Keep Informed | Sonia placement integration priority |
| Student Administration | MEDIUM | HIGH | Keep Informed | PeopleSoft integration requirements; enrolment lifecycle |
| Human Resources | MEDIUM | MEDIUM | Keep Informed | Staff role assignment; ADR-002 implementation |
| Prof. Desmond Key | LOW | HIGH | Keep Informed | LTI integration for discipline tools in Ultra |
| Dr. Wynton Castle | LOW | HIGH | Keep Informed | Ultra interface training; template migration |
| Jazmin Field | LOW | HIGH | Keep Informed | Student experience during transition |
| Platform vendors | MEDIUM | HIGH | Keep Informed | API integration with Ultra |

**Quadrant Interpretation:**

- **Manage Closely** (High Power, High Interest): Key decision-makers requiring active engagement
- **Keep Satisfied** (High Power, Low Interest): Influential stakeholders needing periodic updates
- **Keep Informed** (Low Power, High Interest): Engaged stakeholders needing regular communication
- **Monitor** (Low Power, Low Interest): Minimal engagement required

---

## Stakeholder Drivers Analysis

### SD-1: Prof. Otis Hammond (DVC Education) — A migration that strengthens teaching

**Stakeholder**: Prof. Otis Hammond, Deputy Vice-Chancellor (Education); Executive Sponsor

**Driver Category**: STRATEGIC

**Driver Statement**: Needs the Ultra migration to demonstrably improve the teaching platform while the integration uplift eliminates the fragility that the 001 engagement documented — without disrupting active teaching periods.

**Context & Background**: Hammond championed the L&T Baseline Strategy and approved the integration architecture (ADR-001). Project 003 is the first concrete delivery from that strategy. Its success or failure defines whether the September business case was credible, and whether subsequent projects (004 onwards) get funded. A migration that disrupts teaching undermines the entire programme.

**Driver Intensity**: CRITICAL

**Enablers**:

- Migration sequenced around the academic calendar with change freezes during assessment
- Integration uplift delivering visible early wins — particularly the placement grade flow
- Ultra's pedagogical features positioned as improvements, not just a vendor upgrade

**Blockers**:

- Simultaneous LMS interface change and integration re-engineering in a teaching period
- Integration failures during migration attributed to the strategy rather than the transition
- Academic community perceiving the migration as IT-driven rather than educationally motivated

**Related Stakeholders**: Groove (approves funding), Clavinet (academic gate), Rhodes (funds delivery), Castle (frontline impact)

---

### SD-2: Cassandra Rhodes (CIO) — Deliver the integration architecture

**Stakeholder**: Cassandra "Cas" Rhodes, Chief Information Officer

**Driver Category**: OPERATIONAL / STRATEGIC

**Driver Statement**: Wants ADR-001's lightweight event broker and canonical data model implemented through this migration, replacing the nightly flat-file and manual handling that define the current estate's fragility.

**Context & Background**: Rhodes funded the 001 engagement specifically to get a defensible target state for integration. Project 003 is where that target state becomes real. The PeopleSoft → Blackboard integration is the estate's most consequential data flow — user and course lifecycle, institutional role assignment — and its current nightly-batch implementation is the root cause of most integration complaints [SL-C1]. Ultra's REST APIs and LTI Advantage support make this migration the natural moment to re-engineer.

**Driver Intensity**: CRITICAL

**Enablers**:

- Ultra's REST API and webhook capabilities replacing the flat-file interface
- Canonical data model implemented as the integration contract, not bypassed
- Integration team capacity ring-fenced for the re-engineering work

**Blockers**:

- Migration team treating integration as "lift and shift" — replicating the flat-file in a new format
- Okafor's team split between maintaining current integrations and building new ones
- Principle 19 preventing middleware purchase even where it would accelerate delivery [PP-C1]

**Related Stakeholders**: Okafor (delivers it), Ohm (security posture), Ostinato (funds it), Moog (platform configuration)

---

### SD-3: Sam Okafor (Integration Architect) — Build it right this time

**Stakeholder**: Sam Okafor, Integration Architect, Digital & IT

**Driver Category**: OPERATIONAL / PERSONAL

**Driver Statement**: Needs the migration to be the opportunity to replace the integration estate he has been maintaining with something he designed — and needs it sequenced so his team can deliver without collapsing under dual-running.

**Context & Background**: Okafor co-designed the target integration architecture in WP5 and owns delivery post-engagement. He knows the current estate's failures intimately — the role assignment failures, the single-person course-cloning dependency, the manual CSV provisioning [SL-C1]. This is his project more than anyone's. But he also knows his team's capacity: implementing a canonical data model and event broker while maintaining seven existing integrations during migration is a staffing problem disguised as an architecture one.

**Driver Intensity**: CRITICAL

**Enablers**:

- Integration re-engineering sequenced by risk: PeopleSoft lifecycle first, then provisioning, then the rest
- Dual-running period minimised through parallel development with clear cutover gates
- Team augmentation or vendor professional services for the highest-risk integration

**Blockers**:

- All seven integrations expected to migrate simultaneously
- No additional capacity for the dual-running period
- Target architecture compromised for speed ("just replicate the flat-file for now")

**Related Stakeholders**: Rhodes (his CIO), Moog (platform configuration), Anthology (API access), Student Admin and HR (ADR-002)

---

### SD-4: Dr. Benny Moog (Director, Learning Technologies) — Ultra as a better platform

**Stakeholder**: Dr. Benny Moog, Director, Learning Technologies

**Driver Category**: OPERATIONAL / STRATEGIC

**Driver Statement**: Wants the Ultra migration to deliver genuine pedagogical improvement — better templates, improved mobile experience, modern content authoring — not merely a vendor-mandated interface refresh.

**Context & Background**: In Project 001, Moog defended best-of-breed tooling against consolidation. That tension is resolved for the LMS — Blackboard remains. In Project 003, Moog's role shifts from defender to designer: he owns Ultra configuration, template architecture, and the pedagogical narrative that justifies the migration to academics. If Ultra is positioned as "the vendor made us" rather than "this improves teaching", academic resistance will be high and adoption will be grudging.

**Driver Intensity**: HIGH

**Enablers**:

- Ultra's native features positioned against the current Learn Original limitations
- Template design that makes consistency the path of least resistance (Principle 3)
- Training programme co-designed with Marimba and Castle

**Blockers**:

- Migration framed as a technical upgrade rather than a pedagogical improvement
- Template design imposed without academic input
- Ultra feature gaps relative to Learn Original not acknowledged or mitigated

**Related Stakeholders**: Marimba (training), Castle (frontline adoption), Clavinet (academic endorsement), Key (discipline tool integration)

---

### SD-5: A/Prof. Pearl Clavinet (Dean L&T) — Academic community carries the change

**Stakeholder**: A/Prof. Pearl Clavinet, Dean of Learning & Teaching; Chair, Education Committee

**Driver Category**: STRATEGIC / PERSONAL

**Driver Statement**: Needs the Education Committee to endorse the migration plan with confidence that the academic community has been consulted, that disruption is managed, and that the pedagogical case is genuine.

**Context & Background**: Clavinet's committee endorsed the architecture principles in Project 001. Now it must approve the first major change those principles produce. If academics report that the migration was imposed without consultation, Clavinet's committee loses credibility — and future change requests (Projects 004+) face a harder approval path.

**Driver Intensity**: HIGH

**Enablers**:

- Pilot programme with willing academics before full rollout
- Migration timeline aligned to inter-semester windows
- Pedagogical benefits articulated in academic language, endorsed by Marimba and Castle

**Blockers**:

- Migration timeline set by IT without Education Committee input
- No pilot — direct cutover for all units
- Academic concerns about Ultra limitations dismissed as resistance to change

**Related Stakeholders**: Hammond (sponsor), Moog (Ultra design), Castle (academic voice), Marimba (survey linkage)

---

### SD-6: Dr. Wynton Castle (Senior Lecturer) — Do not break my units

**Stakeholder**: Dr. Wynton Castle, Senior Lecturer; LMS power user

**Driver Category**: PERSONAL / OPERATIONAL

**Driver Statement**: Needs assurance that existing unit content will migrate cleanly, that the interface change is learnable without excessive effort, and that the things that currently work will not stop working during migration.

**Context & Background**: Castle is a Blackboard power user and the frontline academic voice. He validated the principles in Project 001. Now he faces the concrete consequence: his carefully built unit sites will migrate to a different interface. His concern is not opposition to Ultra — it is fear that content will break, workarounds he has built will stop functioning, and the effort to rebuild will land during teaching.

**Driver Intensity**: HIGH

**Enablers**:

- Content migration testing on his actual unit sites before the teaching period
- Ultra training that addresses his specific workflows, not generic demonstrations
- Automated course cloning in Ultra (Principle 13) reducing his current manual effort

**Blockers**:

- Content migration that silently drops formatting, embedded content, or rubric configurations
- Training available only as self-service documentation
- Migration scheduled during teaching with no rollback option

**Related Stakeholders**: Marimba (training), Moog (template design), Clavinet (academic governance), Field (student impact)

---

### SD-7: Eleanor Frame (Privacy & Records Officer) — Migration must not migrate the privacy defects

**Stakeholder**: Eleanor Frame, Privacy & Records Officer

**Driver Category**: COMPLIANCE / RISK

**Driver Statement**: Needs the data migration to comply with Privacy Act 1988 requirements and — critically — needs the manual re-keying and flat-file transfers that are privacy findings in Project 001 to be eliminated by the new architecture, not replicated in it.

**Context & Background**: The privacy context document identifies flat files on shared storage, stale deprovisioning, manual re-keying of placement grades, and email circulation of exports as privacy concerns [PC-C1]. These are not just integration weaknesses — they are APP findings. The data migration itself creates additional privacy exposure: bulk export of student data from Learn Original, transformation, and import into Ultra must be governed, minimised, and time-limited.

**Driver Intensity**: HIGH

**Enablers**:

- Data migration plan with explicit privacy controls: minimisation, retention, access restriction during migration
- Integration re-engineering eliminating manual flows as an integral part of the migration, not a follow-on
- Hosting region for Ultra confirmed as Australian (or cross-border position formally assessed)

**Blockers**:

- Data migration treated as a bulk dump without privacy controls
- Manual flows replicated "temporarily" and never remediated
- Migration data retained after cutover without a defined deletion date

**Related Stakeholders**: Ohm (security controls), Okafor (integration remediation), Anand (placement data), Tanaka (contract clauses)

---

### SD-8: Tobias Ohm (Cybersecurity Lead) — Ultra closes the security gap

**Stakeholder**: Tobias Ohm, Cybersecurity Lead

**Driver Category**: COMPLIANCE / RISK

**Driver Statement**: Needs Ultra to enforce institutional SSO/MFA with no local accounts, and the integration re-engineering to eliminate shared service credentials and flat-file credential exposure.

**Context & Background**: The Essential Eight self-assessment identifies MFA exceptions and local accounts as the L&T estate's most visible security gap [PC-C2]. The migration to Ultra is an opportunity to enforce SSO/MFA from day one with no grandfather clause. The integration re-engineering similarly replaces shared credentials in batch scripts with service-to-service authentication aligned to the ML2 target.

**Driver Intensity**: HIGH

**Enablers**:

- Ultra configured with SSO/MFA only — no local account creation enabled
- Integration credentials using OAuth 2.0 / service accounts with scoped permissions
- Deprovisioning latency reduced from 24 hours (nightly batch) to minutes (event-driven)

**Blockers**:

- Ultra requiring local accounts for admin or integration purposes
- Legacy integration scripts migrated with their existing credential model
- Test environments using production credentials

**Related Stakeholders**: Rhodes (owns E8 target), Okafor (integration security), Frame (overlapping controls), Anthology (SSO configuration)

---

### SD-9: Vernon Ostinato (CFO) — Migration costs justified by the roadmap savings

**Stakeholder**: Vernon Ostinato, Chief Financial Officer

**Driver Category**: FINANCIAL

**Driver Statement**: Needs the migration and integration re-engineering costs quantified and justified against the licence and operational savings the rationalisation roadmap promised.

**Context & Background**: Ostinato approved the September business case on the basis that licence spend would hold flat or reduce while capability gaps were closed [RR-C1]. Project 003 is the first major capital draw against that case. If migration costs escalate without corresponding savings materialising, the remainder of the roadmap loses funding credibility.

**Driver Intensity**: HIGH

**Enablers**:

- Migration costs separated from ongoing licence costs in the business case
- Ultra licensing terms negotiated as part of the migration (not a separate renewal)
- Savings from eliminated manual effort quantified (placement re-keying, CSV provisioning, course cloning)

**Blockers**:

- Migration requiring additional Blackboard licence costs (Ultra premium features)
- Integration uplift costs escalating beyond the business case provision
- Savings dependent on later projects (004+) that have not yet been approved

**Related Stakeholders**: Tanaka (contract negotiation), Rhodes (competing capital claim), Hammond (programme credibility)

---

### SD-10: Grace Tanaka (Procurement & Vendor Manager) — Negotiate Ultra from strength

**Stakeholder**: Grace Tanaka, Procurement & Vendor Manager

**Driver Category**: FINANCIAL / OPERATIONAL

**Driver Statement**: Needs the migration plan to provide negotiating leverage with Anthology — migration commitment in exchange for favourable Ultra licensing, API access, and professional services support.

**Context & Background**: The Blackboard contract renewal is the commercial moment. If the university commits to Ultra migration, Anthology gains retention certainty. Tanaka can leverage that commitment for pricing, migration support, and API access terms — but only if the migration plan is credible and the timeline is firm before renewal negotiations conclude.

**Driver Intensity**: MEDIUM

**Enablers**:

- Migration plan with firm timeline and scope available before contract negotiation
- Data export requirements tested and verified (Principle 9) as a credible exit alternative
- Ultra licensing terms benchmarked against comparable institutions

**Blockers**:

- Contract auto-renewal triggering before migration terms are agreed
- Migration commitment made before negotiating leverage is exercised
- Anthology bundling migration support with premium licensing at additional cost

**Related Stakeholders**: Ostinato (approval), Rhodes (strategy), Anthology (counterparty)

---

### SD-11: Prof. Priya Anand (Dean, Health Sciences) — Fix the placement grades flow

**Stakeholder**: Prof. Priya Anand, Dean, Faculty of Health Sciences

**Driver Category**: OPERATIONAL / COMPLIANCE

**Driver Statement**: Needs the Sonia ↔ Blackboard placement grades integration automated as part of this migration — not deferred to a later project.

**Context & Background**: The placement grade flow is the estate's clearest single defect: sensitive information (placement records including clearance metadata and health-context notes) moved by manual re-keying, with exports circulating via email [PC-C1]. It is simultaneously an academic integrity problem, a privacy problem, and a student-fairness problem. In Project 001 it was identified as a priority remediation. In Project 003 it must be delivered.

**Driver Intensity**: HIGH

**Enablers**:

- Sonia ↔ Ultra integration designed using the canonical data model and LTI Advantage
- Placement data classified as sensitive information with elevated integration controls
- Bidirectional grade synchronisation replacing manual re-keying

**Blockers**:

- Sonia vendor unresponsive on API capability for Ultra integration
- Placement integration deprioritised as affecting one faculty only
- Sensitive information handling deferred to a separate privacy workstream

**Related Stakeholders**: Frame (sensitive data), Okafor (integration build), Moog (gradebook configuration)

---

### SD-12: Prof. Desmond Key (Dean, Music & Performing Arts) — Discipline tools still work in Ultra

**Stakeholder**: Prof. Desmond Key, Dean, School of Music & Performing Arts

**Driver Category**: OPERATIONAL

**Driver Statement**: Needs assurance that MuseScore, Ableton Live, and other discipline-specific tools currently integrated via LTI or embedded content will continue to function in Ultra without degradation.

**Context & Background**: Principle 4 (Discipline Specialisation at the Edge) protects specialist tooling, but the protection is only real if the LTI integrations work in Ultra as they do in Learn Original. Key's school depends on interactive notation distribution and high-fidelity performance capture — capabilities that general-purpose platforms cannot provide [RR-C2]. A migration that breaks these integrations will be perceived as exactly the consolidation Key feared in Project 001.

**Driver Intensity**: MEDIUM

**Enablers**:

- LTI 1.3 Advantage verified for all discipline tools in Ultra before migration
- Music & Performing Arts unit sites included in the pilot programme
- Key consulted on any integration changes affecting discipline tools

**Blockers**:

- Ultra's LTI implementation differing from Learn Original in ways that break discipline tool behaviour
- Discipline tools not tested until after the migration window opens
- LTI issues dismissed as edge cases

**Related Stakeholders**: Moog (LTI configuration), Okafor (integration), Anthology (Ultra LTI support)

---

### SD-13: Jazmin Field (President, Student Guild) — Students are not the experiment

**Stakeholder**: Jazmin Field, President, Student Guild

**Driver Category**: CUSTOMER

**Driver Statement**: Needs assurance that the student experience during migration is managed — clear communication, working content access, and no assessment disruption.

**Context & Background**: Students routinely encounter the consequences of technology change as broken links, inaccessible materials, and grade confusion. Field's advocacy is that students should not bear the cost of a migration they did not request. The single entry point principle (Principle 1) and accessibility requirement (WCAG 2.2 AA) apply during migration, not merely before and after.

**Driver Intensity**: MEDIUM

**Enablers**:

- Student communication plan for each migration phase
- No migration during assessment periods
- Student Guild representative in the pilot programme

**Blockers**:

- Migration during teaching without student notice
- Content broken by migration discovered by students before staff
- Accessibility regression in Ultra not caught before rollout

**Related Stakeholders**: Castle (staff side), Clavinet (academic governance), Marimba (communications)

---

### SD-14: Anthology (Blackboard vendor) — Retain the customer on Ultra

**Stakeholder**: Anthology, Inc. (Blackboard vendor)

**Driver Category**: STRATEGIC / FINANCIAL

**Driver Statement**: Needs UoF's migration to succeed as a reference case, and wants to deepen the relationship through Ultra premium features and professional services.

**Context & Background**: Anthology's business model depends on migrating Learn Original customers to Ultra. A successful UoF migration — particularly one that also demonstrates integration modernisation — is commercially valuable to them. This gives UoF leverage for support, API access, and pricing. But Anthology's interest in selling premium features may conflict with Principle 19 (Realise Licensed Capability Before New Spend).

**Driver Intensity**: MEDIUM

**Enablers**:

- Clear migration requirements communicated early
- Professional services engagement with defined scope and deliverables
- API documentation and sandbox access provided without premium gating

**Blockers**:

- Critical APIs behind a premium licensing tier
- Professional services scope creeping beyond migration support
- Ultra roadmap features promised but not delivered within the migration window

**Related Stakeholders**: Tanaka (contract), Rhodes (strategy), Moog (feature requirements), Okafor (API access)

---

## Driver-to-Goal Mapping

### Goal G-1: PeopleSoft → Ultra integration re-engineered to event-driven

**Derived From Drivers**: SD-2, SD-3, SD-7, SD-8

**Goal Owner**: Sam Okafor, Integration Architect

**Goal Statement**: Replace the nightly flat-file PeopleSoft → Blackboard integration with event-driven, near-real-time propagation of user lifecycle, course lifecycle, and institutional role assignment through the canonical data model, before the first teaching period on Ultra.

**Why This Matters**: This integration is the estate's most consequential data flow. Every other integration depends on users and courses being correct. The nightly batch means access and role state are wrong for up to 24 hours — a direct consequence for students and a privacy finding for deprovisioning [PC-C1].

**Success Metrics**:

- **Primary Metric**: Change propagation latency for identity, enrolment, and role changes
- **Secondary Metrics**:
  - Role assignment failure rate (current baseline vs post-migration)
  - Manual intervention incidents per teaching period

**Baseline**: Nightly batch; up to 24 hours latency; role assignment failures requiring manual correction weekly

**Target**: < 15 minutes propagation latency (per NFR-P-001); zero manual intervention for standard lifecycle events

**Measurement Method**: Integration monitoring telemetry; incident log

**Dependencies**:

- ADR-002 resolved — authoritative source for institutional role assignment confirmed
- Ultra REST API and webhook access from Anthology
- Canonical data model implementation for PERSON, UNIT, ENROLMENT, INSTITUTIONAL_ROLE_ASSIGNMENT

**Risks to Achievement**:

- PeopleSoft event publication capability limited or requiring custom development
- ADR-002 unresolved, blocking the role assignment flow
- Ultra API rate limits constraining near-real-time throughput

---

### Goal G-2: Manual flows carrying personal information eliminated

**Derived From Drivers**: SD-7, SD-11, SD-3, SD-8

**Goal Owner**: Eleanor Frame (sign-off), Sam Okafor (delivery)

**Goal Statement**: Eliminate all manual re-keying, CSV file loads, and email-circulated exports from the L&T integration estate as part of the Ultra migration — specifically the Sonia placement grades, Echo360 provisioning, and institutional hierarchy updates.

**Why This Matters**: These are simultaneously the estate's privacy findings and its integration defects. Migrating to Ultra without fixing them replicates the privacy exposure on a new platform.

**Success Metrics**:

- **Primary Metric**: Number of production data flows requiring a manual step
- **Secondary Metrics**:
  - Flat files on shared storage carrying personal information
  - CSV-based user provisioning events per month

**Baseline**: 4 of 7 integrations involve manual handling or flat-file transfer [SL-C1]

**Target**: Zero manual steps in production flows carrying personal information

**Measurement Method**: Integration register audit; privacy assessment

**Dependencies**:

- G-1 (PeopleSoft integration) provides the identity and enrolment events that provisioning depends on
- Sonia API capability confirmed for bidirectional grade exchange
- Echo360 LTI Advantage provisioning verified in Ultra

**Risks to Achievement**:

- Sonia lacking API capability for automated grade exchange
- "Temporary" manual workarounds becoming permanent
- Echo360 provisioning requiring manual CSV for casual staff edge cases

---

### Goal G-3: Ultra migration completed with zero assessment-period disruption

**Derived From Drivers**: SD-1, SD-5, SD-6, SD-13

**Goal Owner**: Rhonda Bell (delivery), Prof. Otis Hammond (accountable)

**Goal Statement**: Complete the Blackboard Learn Original to Ultra migration across all faculties with no disruption to assessment or examination periods, using a phased rollout with pilot validation.

**Why This Matters**: A migration that disrupts assessment directly harms students and permanently damages the programme's credibility with the academic community.

**Success Metrics**:

- **Primary Metric**: Assessment-period disruption incidents attributable to migration
- **Secondary Metrics**:
  - Pilot programme completion rate and satisfaction
  - Content migration success rate (items migrated without manual intervention)

**Baseline**: No migration attempted; Learn Original in stable operation

**Target**: Zero assessment disruption; > 95% content migration success; pilot satisfaction > 80%

**Measurement Method**: Incident log; content migration audit report; pilot survey

**Dependencies**:

- Academic calendar windows confirmed for migration phases
- Anthology migration tooling tested on representative unit sites
- Rollback capability verified before each phase

**Risks to Achievement**:

- Content types not supported by Anthology's migration tooling (custom building blocks, embedded content)
- Academic calendar leaving insufficient inter-semester window
- Rollback capability not genuinely tested before cutover

---

### Goal G-4: Ultra configured with consistent, accessible templates

**Derived From Drivers**: SD-4, SD-5, SD-6, SD-13

**Goal Owner**: Dr. Benny Moog

**Goal Statement**: Design and deploy Ultra unit site templates that deliver consistent structure and navigation (Principle 3), meet WCAG 2.2 AA (Principle 14), and make template conformance the path of least resistance for academics.

**Why This Matters**: The migration is the one moment when every unit site is being rebuilt. If templates are not ready, academics will recreate their Learn Original structures ad hoc, and the consistency outcome from Project 001 is lost.

**Success Metrics**:

- **Primary Metric**: Template adoption rate for migrated unit sites
- **Secondary Metrics**:
  - WCAG 2.2 AA conformance verified for the baseline template
  - Academic satisfaction with template usability

**Baseline**: No baseline template; unit structure varies by academic preference

**Target**: Baseline template deployed as default; > 80% adoption in first teaching period on Ultra

**Measurement Method**: LMS reporting; accessibility audit; academic feedback survey

**Dependencies**:

- Template design validated with Castle, Marimba, and student representation
- Ultra's template capabilities verified as sufficient for the design
- Training programme co-ordinated with migration rollout

**Risks to Achievement**:

- Ultra template capabilities more limited than Learn Original
- Template designed without academic input, producing resistance
- Training not reaching academics before they need to use Ultra

---

### Goal G-5: Integration team capacity sustained through dual-running

**Derived From Drivers**: SD-3, SD-2, SD-1

**Goal Owner**: Cassandra Rhodes (funding), Sam Okafor (delivery)

**Goal Statement**: Ensure the integration team has sufficient capacity to build the new event-driven integrations while maintaining the existing estate during the migration period, without degradation of either.

**Why This Matters**: Dual-running is the migration's most predictable risk. The team that maintains the fragile current integrations is the same team building the replacements. Without explicit capacity planning, one or both will fail.

**Success Metrics**:

- **Primary Metric**: Integration incidents during migration versus baseline
- **Secondary Metrics**:
  - New integration delivery against plan
  - Team overtime and attrition indicators

**Baseline**: Integration team maintaining 7 integrations with known fragility

**Target**: No increase in integration incidents during migration; new integrations delivered to plan

**Measurement Method**: Incident trending; delivery milestones; team health check

**Dependencies**:

- Capacity plan approved and funded before migration commences
- Vendor professional services available for highest-risk integrations
- Integration sequencing allowing progressive decommission of old flows

**Risks to Achievement**:

- No additional capacity approved; team expected to absorb dual-running
- Vendor professional services unavailable or prohibitively expensive
- Old integrations requiring emergency maintenance during new development

---

### Goal G-6: Discipline tool integrations verified in Ultra

**Derived From Drivers**: SD-12, SD-4

**Goal Owner**: Dr. Benny Moog, with Prof. Desmond Key

**Goal Statement**: Verify that all discipline-specific tools currently integrated via LTI (MuseScore, Ableton Live, iSimulate, Kuracloud, ExamSoft) function correctly in Ultra before the faculties using them are migrated.

**Why This Matters**: Principle 4 protects discipline specialisation at the edge, but the protection is only real if the integrations work. A broken LTI integration in Ultra will be perceived as the consolidation that Project 001's governance process was supposed to prevent.

**Success Metrics**:

- **Primary Metric**: Discipline tool integration pass rate in Ultra testing
- **Secondary Metrics**:
  - LTI 1.3 Advantage compliance verified per tool
  - Discipline faculty sign-off before their migration phase

**Baseline**: Discipline tools integrated with Learn Original via LTI 1.1/1.3

**Target**: 100% of discipline tools verified in Ultra; faculty sign-off obtained

**Measurement Method**: Integration test results; faculty acceptance

**Dependencies**:

- Ultra LTI 1.3 Advantage configuration documented by Anthology
- Discipline tool vendors responsive on Ultra compatibility
- Test environments with representative discipline content

**Risks to Achievement**:

- Ultra's LTI implementation breaking edge-case discipline tool behaviour
- Discipline tool vendors slow to verify Ultra compatibility
- Test environment not representative of production content

---

## Goal-to-Outcome Mapping

### Outcome O-1: The integration estate is sustainable

**Supported Goals**: G-1, G-2, G-5

**Outcome Statement**: The L&T integration estate operates on event-driven, canonical-model-mediated flows with no manual handling, no flat-file transfer, and no single-person dependency — and Sam Okafor's team can maintain it.

**Measurement Details**:

- **KPI**: Production integration incidents per teaching period
- **Current Value**: Weekly manual interventions; role assignment failures; placement grade errors
- **Target Value**: Zero manual steps; < 2 incidents per teaching period requiring intervention
- **Measurement Frequency**: Monthly during delivery; per teaching period in sustainment
- **Data Source**: Integration monitoring telemetry; incident log
- **Report Owner**: Sam Okafor

**Business Value**:

- **Financial Impact**: Manual effort eliminated — re-keying, CSV handling, script maintenance
- **Strategic Impact**: ADR-001's architecture proven in production; template for Projects 004+
- **Operational Impact**: Single-person dependency on course cloning eliminated; deprovisioning latency reduced from 24 hours to minutes
- **Customer Impact**: Students gain access when enrolled, lose it when withdrawn, see grades without delay

**Timeline**:

- **Phase 1 (Months 1-3)**: PeopleSoft → Ultra event-driven integration live; provisioning automated
- **Phase 2 (Months 4-6)**: Placement grades, hierarchy updates, course cloning automated
- **Phase 3 (Months 7-12)**: All seven integrations on the canonical model; old flows decommissioned
- **Sustainment (Year 2+)**: New integrations conform to the architecture by default

**Stakeholder Benefits**:

- **Rhodes**: The integration architecture she funded is operational
- **Okafor**: He runs a sustainable estate rather than firefighting a fragile one
- **Frame**: Privacy findings on manual flows resolved at source
- **Anand**: Placement grades flow automatically

**Leading Indicators**:

- Manual steps eliminated per phase
- Event-driven integrations passing end-to-end testing

**Lagging Indicators**:

- Integration incident rate per teaching period
- Deprovisioning latency (target: < 15 minutes)

---

### Outcome O-2: Academic community adopted Ultra without disruption

**Supported Goals**: G-3, G-4, G-6

**Outcome Statement**: All faculties are operating on Blackboard Ultra with consistent templates, verified discipline tool integrations, and no assessment-period disruption recorded during the migration.

**Measurement Details**:

- **KPI**: Assessment-period incidents; template adoption rate; academic satisfaction
- **Current Value**: Learn Original in stable use; no baseline template; unit structures vary
- **Target Value**: Zero assessment disruption; > 80% template adoption; academic satisfaction > 70%
- **Measurement Frequency**: Per teaching period during rollout; annually in sustainment
- **Data Source**: Incident log; LMS reporting; academic feedback survey
- **Report Owner**: Dr. Benny Moog

**Business Value**:

- **Financial Impact**: Template-based authoring reduces per-unit setup effort
- **Strategic Impact**: Migration proves that governed change works — builds credibility for Projects 004+
- **Operational Impact**: Consistent unit structure reduces student support load
- **Customer Impact**: Students experience consistency regardless of school; accessibility verified

**Timeline**:

- **Phase 1 (Months 1-3)**: Pilot with willing academics; templates designed and tested
- **Phase 2 (Months 4-6)**: First faculty cohort migrated in inter-semester window
- **Phase 3 (Months 7-12)**: Remaining faculties migrated; Learn Original decommissioned
- **Sustainment (Year 2+)**: Templates maintained; Ultra updates governed through RIFF

**Stakeholder Benefits**:

- **Hammond**: Strategy delivered without teaching disruption
- **Clavinet**: Education Committee endorsed a successful change
- **Castle**: Unit sites work in Ultra; cloning is automated; templates save time
- **Field**: Students experience consistent, accessible content

**Leading Indicators**:

- Pilot completion and satisfaction rating
- Content migration success rate in each phase

**Lagging Indicators**:

- Assessment-period disruption incidents (target: zero)
- Template adoption rate at 12 months

---

### Outcome O-3: Privacy and security posture measurably improved

**Supported Goals**: G-1, G-2

**Outcome Statement**: The migration closes the estate's most visible privacy and security gaps: manual re-keying of sensitive information, flat-file personal data on shared storage, local accounts, and 24-hour deprovisioning latency.

**Measurement Details**:

- **KPI**: Privacy findings remediated; E8 mitigation strategies at target maturity
- **Current Value**: 4 manual flows carrying PI; 2 local-account exceptions; mostly ML1 against ML2 target
- **Target Value**: Zero manual flows; zero local accounts; ML2 pathway delivered for integration-affecting strategies
- **Measurement Frequency**: Quarterly
- **Data Source**: PIA review; Essential Eight posture assessment
- **Report Owner**: Eleanor Frame (privacy), Tobias Ohm (security)

**Business Value**:

- **Financial Impact**: Regulatory penalty exposure reduced
- **Strategic Impact**: Compliance is proven through the architecture, not claimed alongside it
- **Operational Impact**: Breach response surface reduced
- **Customer Impact**: Student personal information handled under governed controls

**Timeline**:

- **Phase 1 (Months 1-3)**: Ultra SSO/MFA enforced; PeopleSoft integration eliminates flat-file PI
- **Phase 2 (Months 4-6)**: Placement grades automated; CSV provisioning eliminated
- **Phase 3 (Months 7-12)**: All manual PI flows remediated; E8 posture re-assessed
- **Sustainment (Year 2+)**: Posture reviewed at each contract renewal

**Stakeholder Benefits**:

- **Frame**: APP findings resolved architecturally
- **Ohm**: E8 local-account exception closed; service credentials modernised
- **Groove**: Business case approved with compliance risks addressed
- **Anand**: Sensitive placement information handled appropriately

**Leading Indicators**:

- Manual PI flows eliminated per phase
- SSO/MFA enforcement confirmed at Ultra go-live

**Lagging Indicators**:

- Essential Eight maturity assessment
- Notifiable data breaches (target: zero)

---

## Complete Traceability Matrix

### Stakeholder → Driver → Goal → Outcome

| Stakeholder | Driver ID | Driver Summary | Goal ID | Goal Summary | Outcome ID | Outcome Summary |
|-------------|-----------|----------------|---------|--------------|------------|-----------------|
| Hammond (DVC-E) | SD-1 | Migration strengthens teaching | G-3 | Zero assessment disruption | O-2 | Adopted without disruption |
| Hammond (DVC-E) | SD-1 | Migration strengthens teaching | G-5 | Team capacity sustained | O-1 | Sustainable integration |
| Rhodes (CIO) | SD-2 | Deliver integration architecture | G-1 | PeopleSoft event-driven | O-1 | Sustainable integration |
| Rhodes (CIO) | SD-2 | Deliver integration architecture | G-5 | Team capacity sustained | O-1 | Sustainable integration |
| Okafor (Integration) | SD-3 | Build it right this time | G-1 | PeopleSoft event-driven | O-1 | Sustainable integration |
| Okafor (Integration) | SD-3 | Build it right this time | G-2 | Manual flows eliminated | O-1 | Sustainable integration |
| Okafor (Integration) | SD-3 | Build it right this time | G-5 | Team capacity sustained | O-1 | Sustainable integration |
| Moog (Learning Tech) | SD-4 | Ultra as a better platform | G-4 | Consistent templates | O-2 | Adopted without disruption |
| Moog (Learning Tech) | SD-4 | Ultra as a better platform | G-6 | Discipline tools verified | O-2 | Adopted without disruption |
| Clavinet (Dean L&T) | SD-5 | Academic community carries change | G-3 | Zero assessment disruption | O-2 | Adopted without disruption |
| Clavinet (Dean L&T) | SD-5 | Academic community carries change | G-4 | Consistent templates | O-2 | Adopted without disruption |
| Castle (Lecturer) | SD-6 | Do not break my units | G-3 | Zero assessment disruption | O-2 | Adopted without disruption |
| Castle (Lecturer) | SD-6 | Do not break my units | G-4 | Consistent templates | O-2 | Adopted without disruption |
| Frame (Privacy) | SD-7 | No migrated privacy defects | G-2 | Manual flows eliminated | O-3 | Privacy/security improved |
| Frame (Privacy) | SD-7 | No migrated privacy defects | G-1 | PeopleSoft event-driven | O-3 | Privacy/security improved |
| Ohm (Cybersecurity) | SD-8 | Ultra closes security gap | G-1 | PeopleSoft event-driven | O-3 | Privacy/security improved |
| Ohm (Cybersecurity) | SD-8 | Ultra closes security gap | G-2 | Manual flows eliminated | O-3 | Privacy/security improved |
| Ostinato (CFO) | SD-9 | Costs justified by savings | G-5 | Team capacity sustained | O-1 | Sustainable integration |
| Tanaka (Procurement) | SD-10 | Negotiate from strength | G-3 | Migration completed | O-2 | Adopted without disruption |
| Anand (Dean Health) | SD-11 | Fix placement grades | G-2 | Manual flows eliminated | O-1 | Sustainable integration |
| Anand (Dean Health) | SD-11 | Fix placement grades | G-2 | Manual flows eliminated | O-3 | Privacy/security improved |
| Key (Dean Music) | SD-12 | Discipline tools work | G-6 | Discipline tools verified | O-2 | Adopted without disruption |
| Field (Student Guild) | SD-13 | Students not the experiment | G-3 | Zero assessment disruption | O-2 | Adopted without disruption |
| Anthology | SD-14 | Retain customer on Ultra | G-3 | Migration completed | O-2 | Adopted without disruption |

### Conflict Analysis

**Competing Drivers**:

- **Conflict 1 — Migration pace versus academic disruption** (SD-2/SD-3 versus SD-6/SD-13). Rhodes and Okafor want the integration re-engineering delivered promptly to eliminate fragility and free team capacity. Castle and Field want migration sequenced to minimise teaching disruption — which means slower rollout and longer dual-running.
  - **Resolution Strategy**: Phase the migration around inter-semester windows. Deliver PeopleSoft integration first (purely backend — invisible to academics), then migrate faculties in cohorts during breaks. This gives Rhodes and Okafor early integration wins while protecting Castle and Field from in-semester disruption.

- **Conflict 2 — Integration scope versus team capacity** (SD-2 versus SD-3/SD-9). Rhodes wants all seven integrations re-engineered. Okafor's team cannot build seven new integrations while maintaining seven old ones. Ostinato will not fund unlimited additional capacity.
  - **Resolution Strategy**: Sequence by risk and dependency. Phase 1: PeopleSoft lifecycle (unblocks everything). Phase 2: provisioning automation and placement grades (highest privacy/operational impact). Phase 3: remaining integrations. This is achievable within team capacity plus targeted vendor professional services for Phase 1.

- **Conflict 3 — Principle 19 versus middleware need** (SD-2 versus SD-9). ADR-001 specifies a lightweight event broker, but Principle 19 (Realise Licensed Capability Before New Spend) requires showing that existing licensed capability cannot serve before purchasing middleware [PP-C1].
  - **Resolution Strategy**: ADR-001 already navigated this: the recommendation is a lightweight, institution-managed broker (e.g., open-source message queue) rather than enterprise middleware. Verify whether Blackboard Ultra's webhook/event capabilities and PeopleSoft's Integration Broker provide sufficient mediation before introducing additional components.

- **Conflict 4 — Anthology commercial interest versus Principle 19** (SD-14 versus SD-9). Anthology wants to sell Ultra premium features and professional services. Principle 19 requires exhausting licensed capability first.
  - **Resolution Strategy**: Complete capability mapping of the Ultra licence before engaging on premium features. Negotiate professional services scope as part of the contract renewal rather than as a separate purchase. Tanaka leads with Principle 19 as a procurement position.

**Synergies**:

- **Synergy 1**: Okafor (SD-3) and Frame (SD-7) are solving the same problem. The manual re-keying and flat-file transfers are simultaneously integration defects and privacy findings — one remediation satisfies both. This is the strongest cross-cutting argument for the project.
- **Synergy 2**: Moog (SD-4) and Castle (SD-6) align on templates. Ultra's migration is the moment to deploy consistent templates. If templates reduce Castle's unit-building effort (automated cloning, sensible defaults), consistency becomes effort reduction rather than compliance burden.
- **Synergy 3**: Ohm (SD-8) and Rhodes (SD-2) both benefit from the migration to Ultra's modern authentication. SSO/MFA enforcement from day one on Ultra closes the local-account exception without requiring a separate remediation project.
- **Synergy 4**: Anand (SD-11) and Frame (SD-7) converge on the placement grade flow — the estate's clearest single defect involving sensitive information, manual handling, and academic integrity risk. Fixing it early demonstrates the project's value to multiple stakeholders simultaneously.

---

## Communication & Engagement Plan

### Stakeholder-Specific Messaging

#### Prof. Otis Hammond (DVC Education) — Executive Sponsor

**Primary Message**: Project 003 delivers the first concrete outcome from the strategy you championed — a modernised LMS with sustainable integration, sequenced to protect teaching.

**Key Talking Points**:

- Migration phased around the academic calendar with assessment-period change freezes
- Integration re-engineering delivers the placement grade fix and deprovisioning improvement visible to academics
- Pilot programme validates the approach before full rollout

**Communication Frequency**: Fortnightly (steering committee)

**Preferred Channel**: Steering meeting with one-page migration status summary

**Success Story**: Ultra rollout completes with zero assessment disruption and academics reporting reduced effort through templates and automated cloning.

---

#### Cassandra Rhodes (CIO)

**Primary Message**: The integration architecture you funded is being built. PeopleSoft event-driven first, then cascading through the estate.

**Key Talking Points**:

- Canonical data model implemented as the integration contract — not bypassed for speed
- SSO/MFA enforced from Ultra day one — closes the E8 local-account exception
- Integration team capacity plan ensures dual-running does not degrade service

**Communication Frequency**: Fortnightly (steering); ad hoc on integration decisions

**Preferred Channel**: Steering meeting; technical deep-dives on integration milestones

**Success Story**: All seven integrations operating on the canonical model; no manual steps; incident rate halved.

---

#### Sam Okafor (Integration Architect)

**Primary Message**: This is your architecture, built to your capacity, with the sequencing you need.

**Key Talking Points**:

- PeopleSoft first — the foundation everything else depends on
- Dual-running period explicitly planned and resourced
- You retain technical authority on integration design decisions

**Communication Frequency**: Weekly (working sessions)

**Preferred Channel**: Technical working sessions; architecture review gates

**Success Story**: The integration estate is something he designed, not something he inherited.

---

#### Dr. Benny Moog (Director, Learning Technologies)

**Primary Message**: Ultra is the better teaching platform — and you are designing what it looks like for academics.

**Key Talking Points**:

- Template design is your deliverable, validated with academics before rollout
- Ultra's native capabilities solve Learn Original limitations you have been working around
- Training programme co-designed with Marimba and Castle

**Communication Frequency**: Weekly (working cadence)

**Preferred Channel**: Working sessions; direct involvement in template design

**Success Story**: Academics adopt Ultra templates because they are easier, not because they are mandated.

---

#### Dr. Wynton Castle (Senior Lecturer) and academic community

**Primary Message**: Your units will migrate cleanly, and the things that work today will work in Ultra. The migration saves you time — automated cloning, better templates, fewer tools to navigate.

**Key Talking Points**:

- Content migration tested on representative unit sites before your teaching period
- Templates designed with academic input — consistency makes the easy path the default path
- Training available in workshops, not just documentation

**Communication Frequency**: Pilot programme; pre-migration workshops per faculty

**Preferred Channel**: Faculty workshops; hands-on Ultra sandpit sessions

**Success Story**: Castle reports that Ultra is a genuine improvement and his cloning takes one click.

---

#### Tobias Ohm and Eleanor Frame (Compliance)

**Primary Message**: The migration eliminates the privacy and security defects — not by documenting them, but by replacing the architecture that creates them.

**Key Talking Points**:

- SSO/MFA only from Ultra day one — no local accounts
- Manual PI flows replaced by governed integration in the migration, not after it
- Data migration plan includes explicit privacy controls

**Communication Frequency**: Security/privacy gates at each migration phase

**Preferred Channel**: Gate reviews; written assessment with remediation tracking

**Success Story**: No privacy finding or security exception remains that existed before the migration.

---

## Change Impact Assessment

### Impact on Stakeholders

| Stakeholder | Current State | Future State | Change Magnitude | Resistance Risk | Mitigation Strategy |
|-------------|---------------|--------------|------------------|-----------------|---------------------|
| Sam Okafor | Maintains 7 fragile point-to-point integrations | Operates event-driven canonical-model architecture | HIGH | LOW | Co-designer; sequenced to capacity; he wants this |
| Dr. Benny Moog | Manages Learn Original configuration | Owns Ultra configuration and template architecture | HIGH | LOW | Positions him as designer, not recipient of change |
| Dr. Wynton Castle | Builds units in Learn Original to personal preference | Rebuilds in Ultra with baseline templates | HIGH | HIGH | Pilot; tested content migration; training; effort reduction |
| Academic staff (general) | Familiar Learn Original interface | New Ultra interface with consistent templates | HIGH | HIGH | Phased rollout; inter-semester migration; sandpit access |
| Students | Navigate Learn Original | Navigate Ultra (consistent, accessible) | MEDIUM | LOW | Beneficiary; student comms plan; Guild involvement |
| Grace Tanaka | Contract renewal as routine | Contract renewal as strategic negotiation moment | MEDIUM | LOW | Gives her leverage she currently lacks |
| Prof. Priya Anand | Manual placement grade re-keying | Automated bidirectional grade flow | HIGH | LOW | Clear benefit; early-phase delivery |
| Anthology | Maintaining Learn Original customer | Migrating customer to Ultra | MEDIUM | LOW | Commercially motivated to support |

### Change Readiness

**Champions** (Enthusiastic supporters):

- **Sam Okafor** — the architecture he designed, replacing the estate he has been firefighting
- **Eleanor Frame** — privacy defects resolved architecturally rather than documented and left
- **Prof. Priya Anand** — placement grade automation is a long-standing pain point with a clear fix
- **Cassandra Rhodes** — integration modernisation is her stated objective
- **Tobias Ohm** — Ultra enforces SSO/MFA; integration credentials modernised

**Fence-sitters** (Neutral, need convincing):

- **Vernon Ostinato** — will support if migration costs are justified against business case savings
- **Grace Tanaka** — supportive if migration timeline provides contract negotiation leverage
- **Prof. Desmond Key** — supportive if discipline tools are verified before his faculty migrates
- **Anthology** — commercially motivated but will push premium features; needs managed expectations

**Resisters** (Opposed or skeptical):

- **Dr. Wynton Castle** — not opposed to Ultra, but deeply concerned about content migration, effort, and timing. *Strategy*: include him in the pilot; test migration on his actual units; demonstrate automated cloning and template benefits concretely. His endorsement carries disproportionate weight with colleagues.
- **Academic staff (general)** — interface change fatigue; fear of broken content. *Strategy*: phase around inter-semester windows; never migrate during assessment; provide sandpit access weeks before cutover; communicate what Ultra does better, not just that it is different.

---

## Risk Register (Stakeholder-Related)

### Risk R-1: Academic resistance to Ultra interface change

**Related Stakeholders**: Castle, academic staff, Clavinet, Marimba

**Risk Description**: Academics resist the Ultra migration because the interface change feels imposed, content migration is imperfect, or the timing conflicts with teaching preparation.

**Impact on Goals**: G-3 (zero disruption), G-4 (template adoption)

**Probability**: HIGH

**Impact**: MEDIUM

**Mitigation Strategy**: Pilot programme with willing academics; content migration tested on representative units; Ultra positioned as pedagogical improvement; training workshops not just documentation.

**Contingency Plan**: Extend pilot; address specific content migration issues before broadening rollout; accept lower initial template adoption with voluntary migration rather than mandate.

---

### Risk R-2: Integration team overwhelmed by dual-running

**Related Stakeholders**: Okafor, Rhodes, Bell

**Risk Description**: Okafor's team cannot simultaneously maintain the existing fragile integrations and build the new event-driven replacements, leading to degradation of both.

**Impact on Goals**: G-1 (PeopleSoft re-engineering), G-5 (team capacity)

**Probability**: HIGH

**Impact**: HIGH

**Mitigation Strategy**: Capacity plan approved before migration starts; vendor professional services for PeopleSoft integration (highest-risk, highest-value); progressive decommission of old flows as new ones go live.

**Contingency Plan**: Narrow Phase 1 to PeopleSoft integration only; delay remaining integrations to Phase 2 with explicit resourcing decision.

---

### Risk R-3: ADR-002 unresolved — role assignment source undefined

**Related Stakeholders**: Okafor, Rhodes, Student Admin, HR, Ohm

**Risk Description**: ADR-002 (Authoritative Source for Institutional Role Assignment) remains unresolved because Student Administration and HR cannot agree composition rules, blocking the role assignment integration in G-1.

**Impact on Goals**: G-1 directly; G-2 indirectly (provisioning depends on role)

**Probability**: MEDIUM

**Impact**: HIGH

**Mitigation Strategy**: Escalate ADR-002 resolution as a prerequisite for Project 003 commencement; include Student Admin and HR as named stakeholders (done in this document); set a decision deadline that protects the integration timeline.

**Contingency Plan**: Implement with the current PeopleSoft-as-source assumption and retrofit if ADR-002 concludes differently; document the assumption explicitly.

---

### Risk R-4: Content migration breaks discipline-specific content

**Related Stakeholders**: Key, Anand, Moog, Anthology

**Risk Description**: Anthology's migration tooling does not handle discipline-specific content types — embedded interactive notation, simulation links, clinical scenario configurations — resulting in broken or degraded discipline unit sites.

**Impact on Goals**: G-3 (disruption), G-6 (discipline tools)

**Probability**: MEDIUM

**Impact**: MEDIUM

**Mitigation Strategy**: Include Music & Performing Arts and Health Sciences unit sites in pilot testing; test discipline-specific LTI integrations in Ultra sandpit before migration; Key and Anand sign off before their faculty migrates.

**Contingency Plan**: Manual remediation of discipline content post-migration with Learning Technologies support; extend discipline faculty migration window if issues are discovered.

---

### Risk R-5: Anthology gates critical API access behind premium licensing

**Related Stakeholders**: Tanaka, Ostinato, Okafor, Anthology

**Risk Description**: REST API endpoints or webhook capabilities required for event-driven integration are only available in Ultra's premium licensing tier, creating an unbudgeted cost.

**Impact on Goals**: G-1 (PeopleSoft integration), G-2 (automated flows)

**Probability**: MEDIUM

**Impact**: HIGH

**Mitigation Strategy**: API access requirements documented and submitted to Anthology before contract negotiation; Tanaka negotiates API access as part of migration commitment, not as an add-on.

**Contingency Plan**: Evaluate alternative integration approaches (LTI Advantage, SIS framework) that do not require premium API access; escalate to steering if integration architecture is constrained by licensing.

---

### Risk R-6: Data migration exposes personal information without adequate controls

**Related Stakeholders**: Frame, Ohm, Okafor

**Risk Description**: Bulk data migration from Learn Original to Ultra creates temporary copies of personal information without adequate access restriction, minimisation, or defined deletion timelines.

**Impact on Goals**: G-2 (manual flow elimination — if the migration itself becomes a privacy defect)

**Probability**: LOW

**Impact**: HIGH

**Mitigation Strategy**: Data migration plan reviewed by Frame before execution; migration environment access-restricted; migration data deleted within 30 days of successful cutover; sensitive data classes (placement records) handled under elevated controls.

**Contingency Plan**: Segment data migration — migrate non-sensitive content first, then sensitive classes with Frame's sign-off per batch.

---

## Governance & Decision Rights

### Decision Authority Matrix (RACI)

| Decision Type | Responsible | Accountable | Consulted | Informed |
|---------------|-------------|-------------|-----------|----------|
| Migration timeline and phasing | Bell | Hammond | Rhodes, Clavinet, Moog, Okafor | All stakeholders |
| Integration architecture decisions | Okafor | Rhodes | Moog, Anthology, Student Admin | Hammond, Bell |
| Ultra template design | Moog | Clavinet | Castle, Marimba, Field | Hammond |
| Faculty migration readiness | Bell | Clavinet | Faculty Deans, Moog | Hammond, Rhodes |
| Contract and licensing terms | Tanaka | Ostinato | Rhodes, Bell | Hammond |
| Privacy controls for data migration | Frame | Rhodes | Ohm, Okafor | Hammond |
| Security configuration (SSO/MFA) | Ohm | Rhodes | Okafor, Anthology | Hammond |
| Discipline tool integration acceptance | Moog | Key / Anand (per faculty) | Okafor, Anthology | Clavinet |
| Go/No-go for each migration phase | Hammond | Groove (if escalated) | All Manage Closely stakeholders | All |
| Rollback decision | Bell | Hammond | Okafor, Moog | All |
| ADR-002 resolution (role assignment) | Okafor | Rhodes | Student Admin, HR, Ohm, Frame | Hammond, Clavinet |

### Escalation Path

Aligned to the RIFF governance process:

1. **Level 1 — Project working group**: Bell with Okafor, Moog, and Marimba. Day-to-day migration scope, sequencing, and issue resolution.
2. **Level 2 — RIFF Review**: Integration design decisions, discipline tool exceptions, template exceptions.
3. **Level 3 — Steering Committee**: Hammond (chair), Rhodes, Clavinet — fortnightly. Migration pace, scope changes, resource conflicts, go/no-go gates.
4. **Level 4 — Education Committee**: Chaired by Clavinet. Academic approval of migration timeline and any change affecting teaching periods.
5. **Level 5 — University Executive**: Where financial thresholds are exceeded (migration cost escalation) or where ADR-002 requires institutional data ownership resolution.

---

## Validation & Sign-off

### Stakeholder Review

| Stakeholder | Review Date | Comments | Status |
|-------------|-------------|----------|--------|
| Prof. Otis Hammond | Scheduled 2026-08-12 | Pending — migration sequencing and CSF validation | PENDING |
| Sam Okafor | Scheduled 2026-08-05 | Pending — integration capacity and dual-running assessment | PENDING |
| Dr. Benny Moog | Scheduled 2026-08-05 | Pending — Ultra template and training approach | PENDING |
| A/Prof. Pearl Clavinet | Scheduled 2026-08-12 | Pending — academic change impact and Education Committee timing | PENDING |

> **Note**: SD-3, SD-4, and SD-6 characterise stakeholder positions candidly, including personal dimensions. These should be validated with the Executive Sponsor before the analysis is shared beyond the steering group.

### Document Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Project Sponsor | Prof. Otis Hammond, DVC (Education) | | |
| Business Owner | Dr. Benny Moog, Director Learning Technologies | | |
| Integration Architect | Sam Okafor | | |

---

## Appendices

### Appendix A: Stakeholder Interview Summaries

No stakeholder interviews have been conducted as at 2026-07-29. This analysis is derived from the Project 001 stakeholder analysis (ARC-001-STKE-v1.0), the architecture decisions (ADR-001, ADR-002), the privacy context, and the system landscape.

Drivers marked with a PERSONAL category — SD-3, SD-4, SD-6 — are inferred from role and documented position rather than stated by the individual. They should be tested in validation conversations before being treated as established.

**Planned validation conversations**:

| Stakeholder | Purpose | Target |
|-------------|---------|--------|
| Sam Okafor | Validate SD-3; capacity planning for dual-running | Week 1 |
| Dr. Benny Moog | Validate SD-4; Ultra configuration approach | Week 1 |
| Dr. Wynton Castle | Validate SD-6; pilot programme design | Week 2 |
| Prof. Desmond Key | Validate SD-12; discipline tool LTI verification plan | Week 2 |
| Student Administration | Confirm representative; ADR-002 engagement | Week 1 |
| Human Resources | Confirm representative; ADR-002 engagement | Week 1 |

### Appendix B: Cross-Project Traceability

This stakeholder analysis inherits from and references:

| Source Artifact | Project | Relevance to Project 003 |
|-----------------|---------|--------------------------|
| ARC-001-STKE-v1.0 | 001-lt-ecosystem | Baseline stakeholder register; drivers SD-1 to SD-16 |
| ARC-000-PRIN-v1.1 | 000-global | Governing principles — especially 1, 3, 4, 10, 11, 12, 13, 14, 19 |
| ARC-001-ADR-001-v1.0 | 001-lt-ecosystem | Integration Mediation Approach — this project executes it |
| ARC-001-ADR-002-v1.0 | 001-lt-ecosystem | Authoritative Source for Institutional Role Assignment — prerequisite |
| ARC-001-DATA-v1.0 | 001-lt-ecosystem | Canonical data model — integration contract for this project |
| ARC-001-RISK-v1.0 | 001-lt-ecosystem | Integration fragility risks inherited by this project |

### Appendix C: References

- ARC-000-PRIN-v1.1 — Enterprise Architecture Principles
- ARC-001-ADR-001-v1.0 — Integration Mediation Approach
- ARC-001-ADR-002-v1.0 — Authoritative Source for Institutional Role Assignment
- ARC-001-DATA-v1.0 — Data Model and Privacy-Relevant Flows
- ARC-001-STKE-v1.0 — Stakeholder Drivers & Goals Analysis (Project 001)
- ARC-001-REQ-v1.0 — Requirements (Project 001)

---

## External References

> This section provides traceability from generated content back to source documents.

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| SL | system-landscape.md | Foundation artifact | `projects/003-lms-ultra-migration/external/` | System categorisation map with usage status and known integrations |
| PC | privacy-context.md | Compliance input | `projects/003-lms-ultra-migration/external/` | Personal information inventory, data flows, Essential Eight self-assessment |
| SGP | solution-governance-process.md | Foundation artifact | `projects/000-global/policies/` | RIFF Review governance and approval process |
| PP | ARC-000-PRIN-v1.1.md | ArcKit artifact | `projects/000-global/` | Enterprise Architecture Principles |
| RR | requirements-register.md | Requirements input | `projects/003-lms-ultra-migration/external/` | Consolidated academic survey requirements (REQ-001 to REQ-035) |
| STK1 | ARC-001-STKE-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/` | Stakeholder Drivers & Goals Analysis (Project 001) |
| ADR1 | ARC-001-ADR-001-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/decisions/` | Integration Mediation Approach |
| ADR2 | ARC-001-ADR-002-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/decisions/` | Authoritative Source for Institutional Role Assignment |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| SL-C1 | SL | Known integrations | Risk Factor | "Fragile; role assignment failures; no intra-day sync"; "Manual CSV"; "Undocumented; single-person dependency"; "Manual re-keying; error-prone; audit concerns" |
| PC-C1 | PC | §2 | Compliance Constraint | "Flat-files at rest on shared storage; stale de-provisioning (access persists up to 24h after withdrawal)"; "Human error; screenshots/exports circulating via email"; "No defined retention or minimisation rules" |
| PC-C2 | PC | §3 | Compliance Constraint | "SSO+MFA enforced; **exception:** two tools still allow local accounts (breaches REQ-031)" |
| PP-C1 | PP | Principle 19 | Design Decision | "Where a required capability already exists within a licensed platform, the university MUST evaluate configuring and adopting it before acquiring a new platform." |
| SGP-C1 | SGP | Rules | Governance | "Solutions duplicating capability already licensed (per the system landscape map) must justify why the incumbent tool is unsuitable." |
| RR-C1 | RR | REQ-035 | Business Requirement | "Total ecosystem licence spend shall reduce or hold flat while closing Must-priority capability gaps" |
| RR-C2 | RR | REQ-005, REQ-006 | Functional Requirement | "Music & Performing Arts staff shall distribute interactive notation and audio-production project files as learning materials"; "Health Sciences staff shall deliver clinical simulation scenarios with device integration in simulation labs" |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| consultant-brief.md | `projects/003-lms-ultra-migration/external/` | Read for context; scope and WP structure documented in Project 001 artifacts already cited |
| capability-taxonomy.md | `projects/000-global/external/` | Eight-category taxonomy informs capability goals structurally but no specific passage is cited in this stakeholder analysis |
| stakeholders.md | `projects/003-lms-ultra-migration/external/` | Full stakeholder register used via ARC-001-STKE-v1.0 (STK1), which already cites this source |

---

**Generated by**: ArcKit `/arckit:stakeholders` command
**Generated on**: 2026-07-29
**ArcKit Version**: 6.7.4
**Project**: LMS Ultra Migration & Integration Modernisation (Project 003)
**Model**: Claude Opus 4.6 (1M context)
