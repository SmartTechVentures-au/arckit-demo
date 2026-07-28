# Stakeholder Drivers & Goals Analysis: Lecture Capture Platform Consolidation

> **Template Origin**: Official | **ArcKit Version**: 6.7.2 | **Command**: `/arckit:stakeholders`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-STKE-v1.0 |
| **Document Type** | Stakeholder Drivers & Goals Analysis |
| **Project** | 002-lecture-capture — Lecture Capture Platform Consolidation |
| **Classification** | OFFICIAL-SENSITIVE |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-27 |
| **Last Modified** | 2026-07-27 |
| **Review Cycle** | Monthly during procurement; fortnightly during transition |
| **Next Review Date** | 2026-08-27 |
| **Owner** | Rhonda Bell, Project Manager — L&T Baseline Strategy |
| **Reviewed By** | Grace Tanaka, Procurement & Vendor Manager; Dr. Benny Moog, Director Learning Technologies |
| **Approved By** | PENDING — Prof. Otis Hammond, Deputy Vice-Chancellor (Education), Executive Sponsor |
| **Distribution** | Steering Committee; Project Team; Procurement; Digital & IT leadership. **Not for vendor disclosure.** |

> **Classification rationale**: This document names individuals, assesses their influence and resistance, and records internal positioning ahead of a competitive procurement. Disclosure to any prospective supplier — including the incumbent — would compromise probity. It is classified OFFICIAL-SENSITIVE and restricted to the steering and project group. The derived communication plan (Section 8) may be shared more widely; this analysis must not be.

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-27 | ArcKit AI | Initial creation from `/arckit:stakeholders` command — project 002 procurement and transition | PENDING | PENDING |

---

## Executive Summary

### Purpose

This document identifies the stakeholders of the Lecture Capture Platform Consolidation project, their underlying drivers, how those drivers convert into measurable goals, and the outcomes that will prove those goals achieved. Project 002 exists because of a decision surfaced but not resolved in project 001: the Learning Capture and Learning Delivery categories carry three overlapping platforms — Echo360, Microsoft Teams and Zoom [SL-C1] — and the WP6 decisions register requires that overlap to be resolved before the future state can be finalised [CB-C1].

This analysis covers the **procurement and transition**, not the baseline strategy. It inherits the architecture principles set in `000-global` [PRIN-C1] and the stakeholder register compiled for the parent engagement [S-C1], but it deliberately re-scopes both: the cast is narrower, procurement and AV roles carry far more weight than they do in project 001, and the drivers are about money, capability loss and disruption rather than about strategy.

### Key Findings

The platform choice is **openly contested at executive level**: the CIO favours consolidation onto the Microsoft platform, while the Director of Learning Technologies and the Dean of Music & Performing Arts defend best-of-breed pedagogical tooling [S-C2]. That conflict is real, it is between people who both have legitimate mandates, and it will not be resolved by further analysis of the two products alone.

The more consequential finding is that **the two loudest drivers are not the binding constraints**. Whichever platform wins, the project is bound by two things almost nobody is currently arguing about: the retained recordings archive (Principle 9 — Data Portability and Exit) and the lecture-theatre capture appliance estate, which is behind on operating-system patching and still carries shared administrative accounts [PC-C1]. Both bind every option, both carry cost, and neither is a function of vendor choice. If the steering committee spends its attention on the Echo360-versus-Teams argument and delegates the archive and the appliance estate, the project will select a platform it cannot transition to within the 2027 target.

Third: **a genuine capability gap exists at the discipline edge**. Multi-camera, high-fidelity performance capture (REQ-010) is a Music & Performing Arts need that the mainstream lecture capture market addresses poorly [RR-C1]. Principle 4 — Discipline Specialisation at the Edge — already provides the architectural answer, but only if the core decision is not allowed to become a referendum on the discipline exception.

### Critical Success Factors

- **The platform decision is made once, through governance, and holds.** A recommendation that Rhodes, Moog and Key can each live with — reached through published weighted criteria agreed *before* vendor engagement — is worth more than a technically superior recommendation that is relitigated at every contract renewal.
- **Whole-of-life costing, not licence costing.** Every option is costed including capture appliance refresh, archive migration and support effort. An option that wins on licence price and loses on appliance capex is not a saving.
- **The recordings archive has a defined destination before contract signature.** Export format, volume, retention schedule and access path are settled in the evaluation, not discovered during migration.
- **Transition lands outside teaching weeks.** Cutover in a teaching period fails REQ-032 [RR-C2] regardless of how good the platform is.
- **The discipline exception is bounded and named.** Music performance capture is scoped, costed and approved as an exception under Principle 4 — not left as an unresolved objection to the core decision.

### Stakeholder Alignment Score

**Overall Alignment**: MEDIUM

Alignment is bimodal, and reporting a single figure would mislead. On the *platform choice* alignment is **LOW** — two senior stakeholders hold publicly opposed positions with institutional backing on both sides. On *everything else* alignment is **HIGH**: automated provisioning, SSO/MFA enforcement, captioning, publication reliability, cost containment and archive portability attract no meaningful opposition from any stakeholder. Roughly 80% of this project's scope is uncontested; the contested 20% has been allowed to define the conversation.

The practical implication is that work on the uncontested scope should not wait for the contested decision. Provisioning automation, the captioning baseline, the retention schedule and the appliance patching uplift can all proceed on their own timeline and are the same work under either outcome.

### Baseline Data Status

This analysis sets targets against baselines that are **not yet sourced**. The engagement inputs provide requirements, integrations, privacy context and stakeholder positions, but no contract values, no capture coverage telemetry and no appliance inventory. Every figure below marked ⚠️ is an indicative planning assumption and **must be replaced with sourced data before the business case**:

| Baseline required | Source | Owner | Needed by |
|-------------------|--------|-------|-----------|
| Echo360 and Zoom contract values, terms, renewal dates | Contract register | Grace Tanaka | 2026-08-14 |
| Microsoft licensing position — what capture/streaming entitlement is already held | M365 agreement | Cassandra Rhodes | 2026-08-14 |
| Capture-equipped room count, appliance models, age, support status | AV asset register | Marcus Fairlight | 2026-08-21 |
| Current auto-capture coverage and publication latency | Echo360 reporting | Dr. Benny Moog | 2026-08-21 |
| Retained recording volume, storage footprint, retention rules applied | Echo360 + Records | Eleanor Frame | 2026-08-28 |
| Capture-related service desk ticket volume and causes | Service desk data | Nina Kalimba | 2026-08-21 |

---

## Stakeholder Identification

### Internal Stakeholders

| Stakeholder | Role/Department | Influence | Interest | Engagement Strategy |
|-------------|----------------|-----------|----------|---------------------|
| Prof. Otis Hammond | Deputy Vice-Chancellor (Education) — Executive Sponsor | HIGH | MEDIUM | Steering chair; brought in to arbitrate, not to run the project |
| Cassandra "Cas" Rhodes | Chief Information Officer | HIGH | HIGH | Active involvement; holds the platform position and the funding |
| A/Prof. Pearl Clavinet | Dean of Learning & Teaching; Chair, Education Committee | HIGH | MEDIUM | Academic approval gate; must be walked through the evidence early |
| Vernon Ostinato | Chief Financial Officer | HIGH | MEDIUM | Whole-of-life cost scrutiny; business case gate |
| Grace Tanaka | Procurement & Vendor Manager | HIGH | HIGH | Owns process probity; co-designs evaluation criteria |
| Dr. Benny Moog | Director, Learning Technologies | MEDIUM | HIGH | Product owner; runs RIFF; holds the opposing platform position |
| Marcus Fairlight | Manager, AV & Learning Spaces | MEDIUM | HIGH | Owns the appliance estate and the physical transition |
| Sam Okafor | Integration Architect, Digital & IT | MEDIUM | HIGH | Provisioning design; kills the CSV workaround |
| Prof. Desmond Key | Dean, School of Music & Performing Arts | MEDIUM | HIGH | Performance capture requirement; discipline exception case |
| Tobias Ohm | Cybersecurity Lead | MEDIUM | HIGH | Appliance patching, shared admin accounts, SSO/MFA enforcement |
| Eleanor Frame | Privacy & Records Officer | MEDIUM | HIGH | Recordings of students; APP 8 position; retention and disposal |
| Rhonda Bell | Project Manager | MEDIUM | HIGH | Day-to-day coordination; owns the transition plan |
| Prof. Priya Anand | Dean, Faculty of Health Sciences | MEDIUM | MEDIUM | Large cohorts depend on recordings; simulation lab capture |
| Nina Kalimba | Manager, Digital Learning Support | LOW | HIGH | Absorbs the training and support load of any change |
| Ivy Sequence | Manager, Timetabling & Student Allocation | LOW | MEDIUM | Timetable data drives automatic capture scheduling |
| Dr. Wynton Castle | Senior Lecturer; Blackboard power user | LOW | HIGH | Voice of frontline academics; must re-learn whatever is chosen |
| Jazmin Field | President, Student Guild | LOW | HIGH | Access to recordings, captioning, consent to being recorded |
| Prof. Stella Groove | Vice-Chancellor | HIGH | LOW | Final approver of the business case; no involvement before then |

### External Stakeholders

| Stakeholder | Organization | Relationship | Influence | Interest |
|-------------|--------------|--------------|-----------|----------|
| Account team | Echo360 (incumbent) | Supplier — current capture platform | MEDIUM | HIGH |
| Licensing partner | Microsoft (via existing agreement) | Supplier — incumbent productivity platform | MEDIUM | HIGH |
| Account team | Zoom | Supplier — current live delivery platform | LOW | MEDIUM |
| Students (recorded parties) | The University of Funk | Beneficiary and data subject | LOW | HIGH |
| Rights licensing bodies | APRA AMCOS / Copyright Agency | Compliance — recorded performance and third-party content | MEDIUM | LOW |
| Office of the Australian Information Commissioner | OAIC | Regulator — Privacy Act 1988, NDB scheme | HIGH | LOW |

Students are listed at LOW influence and HIGH interest, which understates them in one specific respect: they are the parties whose image and voice are recorded [PC-C2]. Their influence over the *platform* choice is minimal; their standing in the *privacy* position is not, and Eleanor Frame carries it into the project on their behalf.

### Governance Framework Applicability

The template's UK Government role sets (GovS 005 digital, GovS 007 security) are **not applicable** — The University of Funk is an Australian university, not a UK public body. The governing structure is institutional: the RIFF Review (Review of Innovation, Fit & Function), then Education Committee, then Operations Committee and/or University Executive where financial thresholds are exceeded [SGP-C1].

Two features of that process bear directly on this project:

1. **The duplication rule.** Solutions duplicating capability already licensed must justify why the incumbent tool is unsuitable [SGP-C2]. This cuts *both ways* here and is frequently misquoted in favour of one side. Microsoft Teams is already licensed and already sits in three capability categories; Echo360 is the incumbent in Learning Capture. Whichever direction the recommendation goes, it must clear this rule against the other.
2. **The pause provision.** A request may be paused or closed with the agreement of key consulting stakeholders if deemed not required [SGP-C3]. "Retain both, bounded" remains a legitimate outcome of this project and must be carried as a genuine option, not a strawman.

The Australian regulatory overlay that applies is the Privacy Act 1988 (Australian Privacy Principles, including APP 8 cross-border disclosure) and the ASD Essential Eight [PC-C3], carried by Eleanor Frame and Tobias Ohm respectively.

### Stakeholder Power-Interest Grid

```text
                          INTEREST
              Low                         High
        ┌─────────────────────┬─────────────────────┐
        │                     │                     │
        │   KEEP SATISFIED    │   MANAGE CLOSELY    │
   High │                     │                     │
        │  • VC (Groove)      │  • CIO (Rhodes)     │
        │  • CFO (Ostinato)   │  • Procurement      │
        │  • Dean L&T         │    (Tanaka)         │
 P      │    (Clavinet)       │  • DVC Education    │
 O      │  • OAIC             │    (Hammond)        │
 W      ├─────────────────────┼─────────────────────┤
 E      │                     │                     │
 R      │      MONITOR        │    KEEP INFORMED    │
        │                     │                     │
   Low  │  • Rights bodies    │  • Learning Tech    │
        │  • Zoom             │    (Moog)           │
        │                     │  • AV (Fairlight)   │
        │                     │  • Integration      │
        │                     │    (Okafor)         │
        │                     │  • Security (Ohm)   │
        │                     │  • Privacy (Frame)  │
        │                     │  • Deans (Key,      │
        │                     │    Anand)           │
        │                     │  • Academics, Guild │
        │                     │  • Vendors          │
        └─────────────────────┴─────────────────────┘
```

| Stakeholder | Power | Interest | Quadrant | Engagement Strategy |
|-------------|-------|----------|----------|---------------------|
| Cassandra Rhodes (CIO) | HIGH | HIGH | Manage Closely | Weekly; co-owner of the recommendation |
| Grace Tanaka (Procurement) | HIGH | HIGH | Manage Closely | Weekly; gate on process and probity |
| Prof. Otis Hammond (DVC Education) | HIGH | MEDIUM | Manage Closely | Fortnightly steering; arbitration on request |
| A/Prof. Pearl Clavinet (Dean L&T) | HIGH | MEDIUM | Keep Satisfied | Pre-briefed before each Education Committee paper |
| Vernon Ostinato (CFO) | HIGH | MEDIUM | Keep Satisfied | Cost model reviews at options and preferred-option stages |
| Prof. Stella Groove (VC) | HIGH | LOW | Keep Satisfied | Business case only; no surprises |
| OAIC | HIGH | LOW | Keep Satisfied | No direct engagement; compliance evidenced through PIA |
| Dr. Benny Moog (Learning Tech) | MEDIUM | HIGH | Keep Informed | Weekly; capability evidence owner |
| Marcus Fairlight (AV) | MEDIUM | HIGH | Keep Informed | Weekly during appliance assessment and transition |
| Sam Okafor (Integration) | MEDIUM | HIGH | Keep Informed | Weekly; provisioning design |
| Tobias Ohm (Security) | MEDIUM | HIGH | Keep Informed | Fortnightly; security requirements into evaluation |
| Eleanor Frame (Privacy) | MEDIUM | HIGH | Keep Informed | Fortnightly; PIA and retention schedule |
| Prof. Desmond Key (Music) | MEDIUM | HIGH | Keep Informed | Monthly; discipline exception case |
| Prof. Priya Anand (Health Sciences) | MEDIUM | MEDIUM | Keep Informed | Monthly; cohort impact |
| Rhonda Bell (PM) | MEDIUM | HIGH | Keep Informed | Daily; delivery |
| Nina Kalimba (Support) | LOW | HIGH | Keep Informed | Monthly, then weekly during transition |
| Dr. Wynton Castle (Academic) | LOW | HIGH | Keep Informed | Reference group; pilot participant |
| Jazmin Field (Student Guild) | LOW | HIGH | Keep Informed | Monthly; consent and accessibility positions |
| Ivy Sequence (Timetabling) | LOW | MEDIUM | Monitor | Consulted on scheduling data feed |
| Echo360 / Microsoft / Zoom | MEDIUM–LOW | HIGH | Monitor (managed via Procurement) | All contact through Tanaka; no direct approaches |

**Quadrant Interpretation:**

- **Manage Closely** (High Power, High Interest): Key decision-makers requiring active engagement
- **Keep Satisfied** (High Power, Low Interest): Influential stakeholders needing periodic updates
- **Keep Informed** (Low Power, High Interest): Engaged stakeholders needing regular communication
- **Monitor** (Low Power, Low Interest): Minimal engagement required

> **Probity note**: Vendor contact is routed exclusively through Grace Tanaka from the point evaluation criteria are drafted. Rhodes and Moog both have pre-existing account relationships; those relationships are an asset for information-gathering *before* criteria are issued and a liability after.

---

## Stakeholder Drivers Analysis

### SD-1: Cassandra Rhodes (CIO) — Consolidate onto capability already paid for

**Stakeholder**: Cassandra "Cas" Rhodes, Chief Information Officer

**Driver Category**: FINANCIAL / STRATEGIC

**Driver Statement**: Stop paying a specialist vendor for capability the university already licenses inside its Microsoft agreement, and reduce the number of platforms her team must integrate, secure and support.

**Context & Background**: Rhodes owns Digital & IT, funds the integration uplift, and carries the Essential Eight targets [S-C3]. She inherited an ecosystem of 20+ tools with overlapping capability and fragile point-to-point integrations. Three platforms currently sit in Learning Capture and Learning Delivery simultaneously, and a Teams investigation was already planned for 2027 to establish a seamless platform experience [SL-C2]. From her seat, every additional platform is another identity integration, another patching surface, another contract and another support queue. Principle 19 — Realise Licensed Capability Before New Spend — reads as institutional endorsement of her position.

**Driver Intensity**: HIGH

**Enablers** (What would help):

- Evidence that the already-licensed platform meets the Must-priority capture requirements (REQ-004, REQ-008, REQ-009)
- A whole-of-life cost model that makes the duplication visible in dollars
- The RIFF duplication rule applied consistently [SGP-C2]

**Blockers** (What would hinder):

- Discipline-specific capability the mainstream platform genuinely cannot meet (REQ-010)
- Appliance replacement capex that erases the licence saving
- Academic perception that IT is choosing on cost and calling it strategy

**Related Stakeholders**:

- Aligned: Ostinato (cost), Ohm (fewer platforms to secure), Okafor (fewer integrations)
- Opposed: Moog (SD-6), Key (SD-9)

---

### SD-2: Grace Tanaka (Procurement & Vendor Manager) — A defensible process

**Stakeholder**: Grace Tanaka, Procurement & Vendor Manager

**Driver Category**: COMPLIANCE / RISK

**Driver Statement**: Run a process that would survive scrutiny — criteria published before evaluation, weightings unchanged after issue, vendor contact controlled, and a written justification for whichever route is taken.

**Context & Background**: Tanaka holds contract status data and manages vendor roadmap sessions [S-C4]. In this project her role changes character: in project 001 she was a data source, here she is a process gate. She is acutely aware that two executives have publicly stated positions before any evaluation has occurred, which is precisely the pattern that produces a challengeable outcome. If the university varies its existing Microsoft agreement rather than testing the market, that decision needs a value-for-money record; if it runs a competitive process, the incumbent's account team must not receive informal signals.

**Driver Intensity**: HIGH

**Enablers** (What would help):

- Evaluation criteria and weightings agreed and signed off before any vendor engagement
- Single point of vendor contact
- The RIFF review as the documented decision forum [SGP-C1]

**Blockers** (What would hinder):

- Executives briefing vendors directly
- Criteria adjusted after proposals are received
- Timeline pressure used to justify skipping the market test

**Related Stakeholders**:

- Aligned: Ostinato (value for money), Hammond (defensible decision)
- Tension: Rhodes (SD-1) where speed favours the existing agreement

---

### SD-3: Vernon Ostinato (CFO) — No surprise capital, and a real saving

**Stakeholder**: Vernon Ostinato, Chief Financial Officer

**Driver Category**: FINANCIAL

**Driver Statement**: Deliver the licence saving that the rationalisation case promises, without discovering a multi-year AV capital programme hidden underneath it.

**Context & Background**: Ostinato scrutinises the business case and has licence spend optimisation as a standing objective [S-C5], reflected in REQ-035 — total ecosystem licence spend must reduce or hold flat while closing Must-priority gaps [RR-C3]. His exposure in this project is specific: lecture capture is the one L&T capability with a significant physical estate behind it. A platform change that requires appliance replacement converts an opex saving into a capex request, and he will not learn that at business case stage without consequence.

**Driver Intensity**: HIGH

**Enablers** (What would help):

- Whole-of-life cost model covering licence, appliances, migration and support for every option
- Appliance refresh profile separated into "required regardless" and "caused by this decision"
- Contract terms that avoid step-change pricing at renewal

**Blockers** (What would hinder):

- Options costed on licence price alone
- Archive migration effort discovered after contract signature
- An exception for Music that is approved without being costed

**Related Stakeholders**:

- Aligned: Rhodes (SD-1), Tanaka (SD-2)
- Tension: Fairlight (SD-7), Key (SD-9) — both bring cost he would rather not see

---

### SD-4: Prof. Otis Hammond (DVC Education) — A decision that does not come back

**Stakeholder**: Prof. Otis Hammond, Deputy Vice-Chancellor (Education), Executive Sponsor

**Driver Category**: STRATEGIC / PERSONAL

**Driver Statement**: Resolve a contested platform question once, with academic and technical legitimacy, so that it stays resolved through the September business case and beyond.

**Context & Background**: Hammond owns the L&T strategy and chairs the steering committee [S-C6]. He is sponsor of the parent engagement, whose entire value proposition is a rationalisation roadmap feeding a business case. A lecture capture decision that is reopened at every renewal — or worse, one that fractures along the academic/IT line and requires him to overrule a Dean — undermines the strategy he is sponsoring. He wants the recommendation to arrive with its opposition already addressed, not with the argument delegated upward to him.

**Driver Intensity**: HIGH

**Enablers** (What would help):

- Agreed evaluation criteria that both camps signed before evaluation
- A bounded, principled treatment of the discipline exception
- Education Committee endorsement rather than executive imposition

**Blockers** (What would hinder):

- Being asked to arbitrate between his CIO and a Dean in an open meeting
- A recommendation whose evidence base either camp disputes
- Slippage past the September business case window

**Related Stakeholders**:

- Aligned: Clavinet (academic legitimacy), Tanaka (defensibility)
- Manages: Rhodes (SD-1) and Moog (SD-6) conflict

---

### SD-5: A/Prof. Pearl Clavinet (Dean L&T, Chair Education Committee) — Pedagogy must be seen to lead

**Stakeholder**: A/Prof. Pearl Clavinet, Dean of Learning & Teaching

**Driver Category**: STRATEGIC / PERSONAL

**Driver Statement**: Ensure the committee she chairs is making an educational decision informed by technology, not ratifying a technology decision dressed in educational language.

**Context & Background**: Clavinet is the academic approval gate and validated the WP1 principles [S-C7]. Her committee must formally approve the solution request before it proceeds to Operations Committee [SGP-C4]. She is not opposed to consolidation, and she is not the Music school's advocate — but if the paper that reaches her committee reads as a cost exercise, she will send it back, and the timeline absorbs a full committee cycle.

**Driver Intensity**: MEDIUM

**Enablers** (What would help):

- Teaching-quality criteria weighted visibly in the evaluation
- Academic reference group input documented in the recommendation
- Early pre-briefing rather than first sight at committee

**Blockers** (What would hinder):

- A paper dominated by licence economics
- Deans discovering the recommendation at committee
- No evidence of frontline academic involvement

**Related Stakeholders**:

- Aligned: Hammond (SD-4), Moog (SD-6), Castle (SD-12)
- Gate for: the entire project

---

### SD-6: Dr. Benny Moog (Director, Learning Technologies) — Do not trade capability for tidiness

**Stakeholder**: Dr. Benny Moog, Director, Learning Technologies

**Driver Category**: OPERATIONAL / PERSONAL

**Driver Statement**: Protect the capture and pedagogical capability that academics actually use, and avoid being the person who presided over a downgrade sold as consolidation.

**Context & Background**: Moog is product owner of the L&T ecosystem, holds the deepest tool knowledge, and runs the RIFF reviews [S-C8]. He defends best-of-breed pedagogy tooling against Microsoft-platform consolidation [S-C2]. His concern is concrete rather than sentimental: the capture platform is integrated with the LMS through LTI, publishes to unit sites, and carries engagement analytics that feed the Evaluation & Analytics category [SL-C3]. A general-purpose meeting-recording tool and a purpose-built lecture capture platform are not the same product class, and he expects the difference to be dismissed in a cost comparison.

There is a personal dimension worth stating plainly: he chairs the review process that will assess this decision, and he holds a position on its outcome. That is a governance strain, not an accusation, and it is handled in the RACI (Section 11).

**Driver Intensity**: HIGH

**Enablers** (What would help):

- Capability comparison against the eight-category taxonomy rather than a feature checklist [CT-C1]
- Weighted criteria that reflect teaching use, not meeting use
- Analytics and LMS integration treated as in-scope requirements, not nice-to-haves

**Blockers** (What would hinder):

- Evaluation criteria set primarily by Digital & IT
- "Good enough" judgements made without academic input
- His RIFF chair role being used to argue he cannot hold a position

**Related Stakeholders**:

- Aligned: Key (SD-9), Castle (SD-12), Anand (SD-13), Clavinet (SD-5)
- Opposed: Rhodes (SD-1)

---

### SD-7: Marcus Fairlight (Manager, AV & Learning Spaces) — Solve the estate, not just the software

**Stakeholder**: Marcus Fairlight, Manager, AV & Learning Spaces

**Driver Category**: OPERATIONAL / RISK

**Driver Statement**: Get the lecture-theatre capture estate onto a supportable, patchable footing — and make sure whoever chooses the software understands that the hardware behind it is the actual constraint.

**Context & Background**: Fairlight owns the capture appliances in teaching spaces. The Essential Eight self-assessment identifies his estate twice: operating system patching on lecture-theatre capture appliances is behind, and legacy shared administrative accounts persist in the AV and capture estate [PC-C4]. Neither is a software licensing problem, and neither goes away by changing vendor. His fear is a decision made on licence economics that lands as a room-by-room replacement programme in his team's summer window, with no additional resourcing.

**Driver Intensity**: HIGH

**Enablers** (What would help):

- Appliance inventory completed and costed before the platform decision
- Any option's room-level impact assessed explicitly
- Refresh funding separated from platform licensing

**Blockers** (What would hinder):

- Platform selected without room compatibility assessment
- Transition scheduled into a teaching period
- Shared admin account remediation deferred again

**Related Stakeholders**:

- Aligned: Ohm (SD-10) on the security debt, Ostinato (SD-3) on making capex visible early
- Depends on: Sequence (timetabling data), Kalimba (support model)

---

### SD-8: Sam Okafor (Integration Architect) — End the manual provisioning workaround

**Stakeholder**: Sam Okafor, Integration Architect, Digital & IT

**Driver Category**: OPERATIONAL

**Driver Statement**: Replace LTI-plus-manual-CSV provisioning with automated, event-driven identity flow — and get an architecture he can sustain after the consultant leaves.

**Context & Background**: Echo360 user provisioning currently runs on LTI with manual CSV, and the manual workaround exists specifically for casual academic staff [SL-C4]. This breaches REQ-025 (no manual CSV loads) and sits uncomfortably against REQ-031 (SSO with MFA, no local accounts) [RR-C4]. Okafor owns integration delivery after the engagement ends, so the decision he cares about is not which vendor but which integration pattern — and whether the selected platform supports event-driven provisioning against the canonical model defined in project 001, or forces another batch job.

**Driver Intensity**: HIGH

**Enablers** (What would help):

- Provisioning API and SCIM-style capability treated as mandatory evaluation criteria
- Canonical entity model from project 001 applied to the capture platform
- Timetable feed available for capture scheduling (REQ-009)

**Blockers** (What would hinder):

- A platform whose only provisioning path is bulk import
- Casual staff lifecycle left as a manual exception again
- Integration requirements weighted low against feature comparison

**Related Stakeholders**:

- Aligned: Rhodes (SD-1), Ohm (SD-10), Sequence (timetabling dependency)
- Serves: every option equally — this driver is platform-neutral

---

### SD-9: Prof. Desmond Key (Dean, Music & Performing Arts) — Performance capture is not lecture capture

**Stakeholder**: Prof. Desmond Key, Dean, School of Music & Performing Arts

**Driver Category**: STRATEGIC / OPERATIONAL

**Driver Statement**: Preserve multi-camera, high-fidelity audio capture for performance and ensemble teaching, which is a nationally-recognised strength of the school and cannot be delivered by a meeting-recording tool.

**Context & Background**: REQ-010 — performance and ensemble sessions capturable with multi-camera and high-fidelity audio — is a Could-priority requirement from the academic survey [RR-C5]. Key's problem is that MoSCoW priority reflects institutional breadth, not disciplinary criticality: a requirement affecting one school will always score below one affecting all schools, no matter how existential it is to that school. He has watched discipline tooling (MuseScore, Ableton Live) sit in "investigation required" status for a year [SL-C5] and reads this project as the moment discipline needs get consolidated away.

Principle 4 — Discipline Specialisation at the Edge — exists precisely for this case, and Key does not yet trust that it will be applied.

**Driver Intensity**: CRITICAL (for him; MEDIUM institutionally)

**Enablers** (What would help):

- Explicit application of Principle 4 to bound a discipline exception
- Performance capture scoped and costed as its own line, not as an objection to the core
- Named venues and a defined capability standard

**Blockers** (What would hinder):

- Core decision treated as covering all capture, everywhere
- REQ-010's Could priority used to dismiss the requirement
- Exception approved in principle but unfunded

**Related Stakeholders**:

- Aligned: Moog (SD-6), Anand (SD-13) — same structural argument, different discipline
- Tension: Ostinato (SD-3), Rhodes (SD-1)

---

### SD-10: Tobias Ohm (Cybersecurity Lead) — Close the capture estate's security debt

**Stakeholder**: Tobias Ohm, Cybersecurity Lead

**Driver Category**: COMPLIANCE / RISK

**Driver Statement**: Use the platform change as the forcing function to remove shared administrative accounts and bring capture appliances into the patching regime, moving toward the ML2 target.

**Context & Background**: Digital & IT has set an ML2 target across the SaaS-heavy L&T estate by end 2027 [PC-C5]. Two of the eight mitigation strategies are held back specifically by this project's estate: restrict administrative privileges (legacy shared admin accounts in the AV/capture estate) and patch operating systems (lecture-theatre capture appliances behind) [PC-C4]. Separately, MFA sits at ML2 but with an exception — two tools still permit local accounts, breaching REQ-031 [PC-C6]. Ohm needs to know whether either of those tools is in this project's scope; if so, this procurement closes the exception.

**Driver Intensity**: HIGH

**Enablers** (What would help):

- SSO/MFA enforcement as a mandatory, non-scoreable evaluation gate
- Appliance patching regime agreed with AV as part of transition
- Contract terms covering vulnerability disclosure and breach notification

**Blockers** (What would hinder):

- Security treated as a weighted criterion that can be traded away
- Appliance remediation deferred to a later programme
- A platform requiring local service accounts for room devices

**Related Stakeholders**:

- Aligned: Fairlight (SD-7), Okafor (SD-8), Rhodes (SD-1), Frame (SD-11)

---

### SD-11: Eleanor Frame (Privacy & Records Officer) — Recordings are personal information

**Stakeholder**: Eleanor Frame, Privacy & Records Officer

**Driver Category**: COMPLIANCE

**Driver Statement**: Establish a defensible privacy position for video and audio recordings that capture students — hosting location, retention, disposal, access and consent — before a platform is contracted, not after.

**Context & Background**: The personal information inventory classifies video and audio recordings capturing students as personal information with a biometric-adjacent character, held in Echo360, Zoom and MS Teams, under assumed hosting of AU and US [PC-C2]. That class is flagged as a partial APP 8 trigger — cross-border disclosure requiring assessment of accountability, contract clauses and the practicability of AU-region alternatives [PC-C7]. Frame also carries records management: there is currently no defined retention or minimisation rule for the analytics derived from this estate [PC-C8], and by extension the recordings themselves accumulate without a disposal trigger.

Her leverage is highest before contract signature and close to zero afterwards. She knows it.

**Driver Intensity**: HIGH

**Enablers** (What would help):

- Data residency stated as an evaluation requirement, with APP 8 assessment for any offshore option (REQ-030)
- Retention schedule agreed for recordings before migration — migration is the natural disposal point
- Consent and notification position agreed with Education Committee

**Blockers** (What would hinder):

- Platform selected before the PIA is complete
- Migration executed as a bulk lift, carrying forward everything indefinitely
- Consent treated as a policy afterthought

**Related Stakeholders**:

- Aligned: Ohm (SD-10), Field (SD-14), Tanaka (SD-2) on contract terms
- Serves: students, who have no direct voice in the process

---

### SD-12: Dr. Wynton Castle (Senior Lecturer) — Do not make my teaching harder

**Stakeholder**: Dr. Wynton Castle, Senior Lecturer and Blackboard power user

**Driver Category**: PERSONAL / OPERATIONAL

**Driver Statement**: Whatever is chosen must start recording without him thinking about it, publish where students already look, and not require him to rebuild unit materials or relearn a workflow mid-semester.

**Context & Background**: Castle is the frontline academic voice and participates in principles validation workshops [S-C9]. He represents a constituency that is largely indifferent to the platform argument and highly sensitive to its consequences: links embedded in unit sites, existing recordings referenced in current teaching, and the muscle memory of a working process. REQ-009's four-hour publication window matters to him not as an SLA but as the difference between students having last week's lecture before the tutorial or not [RR-C6].

He also holds a quieter concern shared across academic staff: recordings of his teaching are a record of his performance, and he wants to know who can see them and for how long.

**Driver Intensity**: MEDIUM

**Enablers** (What would help):

- Single entry point maintained — recordings appear in the unit site (Principle 1, REQ-007)
- Existing recording links preserved or redirected through migration
- Training and support timed outside teaching weeks

**Blockers** (What would hinder):

- Cutover mid-semester
- Broken links to prior recordings
- A workflow requiring manual steps to start a recording

**Related Stakeholders**:

- Aligned: Kalimba (SD-15), Moog (SD-6), Anand (SD-13)
- Represents: casual academic staff, who currently suffer the manual provisioning workaround

---

### SD-13: Prof. Priya Anand (Dean, Health Sciences) — Large cohorts depend on this working

**Stakeholder**: Prof. Priya Anand, Dean, Faculty of Health Sciences

**Driver Category**: OPERATIONAL / CUSTOMER

**Driver Statement**: Maintain reliable recording access for large cohorts whose students combine study with clinical placement and shift work, and preserve simulation-context capture.

**Context & Background**: Health Sciences is one of the university's two largest faculties, and its students are among the most dependent on recorded teaching — placement rosters and clinical shifts make live attendance genuinely impossible for parts of the cohort. Her faculty also uses simulation tooling (iSimulate, Kuracloud) in lab settings [SL-C6], where capture serves debrief and assessment rather than lecture review. Anand's driver is availability and continuity, not platform preference; she becomes an opponent only if transition risk lands on her cohorts.

**Driver Intensity**: MEDIUM

**Enablers** (What would help):

- 99.9% availability commitment through teaching periods (REQ-032)
- Simulation-context capture assessed in the requirement set
- Transition sequenced away from her assessment periods

**Blockers** (What would hinder):

- Any recording loss during migration
- Publication delays during high-load weeks
- Simulation capture treated as out of scope without a decision

**Related Stakeholders**:

- Aligned: Castle (SD-12), Field (SD-14), Key (SD-9) on the discipline-needs argument

---

### SD-14: Jazmin Field (President, Student Guild) — Access, captions, and being asked

**Stakeholder**: Jazmin Field, President, Student Guild

**Driver Category**: CUSTOMER / COMPLIANCE

**Driver Statement**: Every student gets the same access to recorded teaching, captioned to a usable standard — and students are told, in advance and in plain language, when and how they are being recorded.

**Context & Background**: Field advocates student experience consistency and accessibility [S-C10]. Two requirements carry her position: REQ-029 (WCAG 2.2 AA conformance for all student-facing tools) and REQ-030 (Privacy Act compliance) [RR-C7]. Captioning is the sharpest edge — auto-captioning quality varies enormously by platform, accent and discipline vocabulary, and a platform that captions clinical or musical terminology poorly delivers a materially worse service to the students who most need captions. Her second concern is consent: students appearing in recordings, particularly in seminars and performance contexts, are currently not systematically informed.

**Driver Intensity**: MEDIUM

**Enablers** (What would help):

- Caption accuracy tested against real discipline vocabulary in evaluation, not vendor claims
- Consistent publication practice across schools (Principle 3)
- Student-facing notification standard agreed with the Guild

**Blockers** (What would hinder):

- Captioning scored on availability rather than accuracy
- School-by-school variation in whether recordings are published
- Consent position deferred past go-live

**Related Stakeholders**:

- Aligned: Frame (SD-11), Anand (SD-13), Clavinet (SD-5)

---

### SD-15: Nina Kalimba (Manager, Digital Learning Support) — The support load lands on my team

**Stakeholder**: Nina Kalimba, Manager, Digital Learning Support

**Driver Category**: OPERATIONAL / PERSONAL

**Driver Statement**: Enter the 2027 academic year with a supported, documented capture workflow and a trained team — not with a new platform, no runbooks, and a semester-one ticket spike.

**Context & Background**: Kalimba's team absorbs every failure mode of the current arrangement: recordings that did not start, publication delays, casual staff without accounts because the CSV had not been run. She is the person for whom the manual provisioning workaround [SL-C4] is a weekly reality rather than an architectural observation. Her driver is not which platform but *how much notice she gets* and whether documentation exists before users arrive.

**Driver Intensity**: MEDIUM

**Enablers** (What would help):

- Transition plan with training window before semester start
- Runbooks and known-issues documentation produced as a deliverable
- Pilot cohort to surface failure modes before full cutover

**Blockers** (What would hinder):

- Cutover close to semester start
- Documentation treated as a post-go-live task
- No pilot phase

**Related Stakeholders**:

- Aligned: Castle (SD-12), Fairlight (SD-7), Bell (delivery)

---

## Driver-to-Goal Mapping

### Goal G-1: Platform recommendation endorsed through governance by 9 October 2026

**Derived From Drivers**: SD-1, SD-2, SD-4, SD-5, SD-6

**Goal Owner**: Prof. Otis Hammond (Executive Sponsor), delivered by Rhonda Bell

**Goal Statement**: Produce a single lecture capture platform recommendation, supported by evidence against agreed weighted criteria, endorsed at RIFF review by 11 September 2026, approved by Education Committee by 25 September 2026, and cleared by Operations Committee by 9 October 2026.

**Why This Matters**: The parent engagement's roadmap and the September business case both depend on this decision being closed [CB-C2]. An unresolved decision blocks the WP8 future state. Equally, a decision imposed without academic endorsement will be reopened, which satisfies nobody's driver.

**Success Metrics**:

- **Primary Metric**: Governance endorsement achieved at each of three gates on schedule
- **Secondary Metrics**:
  - Evaluation criteria signed off by Rhodes, Moog and Tanaka before vendor engagement
  - Zero criteria or weighting changes after issue
  - Formal dissent recorded and addressed, not suppressed

**Baseline**: No decision. Two publicly stated opposing executive positions [S-C2].

**Target**: Endorsed recommendation with documented options analysis and recorded treatment of dissent.

**Measurement Method**: RIFF review minutes; Education Committee and Operations Committee resolutions; signed criteria document held by Procurement.

**Dependencies**:

- Contract and licensing baselines available by 14 August 2026
- Capability evidence gathered against the eight-category taxonomy [CT-C1]
- Architecture Decision Record raised in project 001 for the capture decision

**Risks to Achievement**:

- Criteria negotiation itself becomes the proxy battleground (R-1)
- Education Committee returns the paper for insufficient academic evidence (R-3)
- Baseline data unavailable, forcing evaluation on assumptions (R-6)

---

### Goal G-2: Evaluation conducted on published, weighted, unchanged criteria

**Derived From Drivers**: SD-2, SD-4, SD-6

**Goal Owner**: Grace Tanaka

**Goal Statement**: Issue an evaluation framework with weightings totalling 100% and mandatory pass/fail gates, agreed by all three signatories before any vendor engagement, and apply it without amendment through to recommendation.

**Why This Matters**: This is the single mechanism that converts an executive disagreement into a decidable question. It also protects the outcome from challenge — by a vendor, by a Dean, or by an auditor.

**Success Metrics**:

- **Primary Metric**: 100% of scored criteria traceable to a numbered requirement in the register [RR-C8]
- **Secondary Metrics**:
  - Mandatory gates defined for SSO/MFA (REQ-031), accessibility (REQ-029), data export (REQ-034)
  - All vendor contact logged through a single point
  - Scoring rationale recorded per criterion per option

**Baseline**: No criteria exist. Vendor relationships held informally by two executives.

**Target**: Signed framework in place before first vendor engagement; complete contact log; scored matrix with written rationale.

**Measurement Method**: Signed evaluation framework document; vendor contact log maintained by Procurement; completed scoring matrix.

**Dependencies**:

- Requirements subset for capture agreed from the register (REQ-004, 008, 009, 010, 025, 029, 030, 031, 032, 033, 034, 035)
- Weighting workshop held with Rhodes, Moog, Clavinet, Ohm and Frame represented

**Risks to Achievement**:

- Weighting workshop deadlocks (R-1)
- Informal vendor contact continues in parallel (R-2)

---

### Goal G-3: Automatic capture coverage and publication reliability meet REQ-009

**Derived From Drivers**: SD-6, SD-7, SD-12, SD-13

**Goal Owner**: Dr. Benny Moog, with Marcus Fairlight for the room estate

**Goal Statement**: Achieve automatic capture of 100% of timetabled lectures in capture-equipped teaching spaces, published to the relevant unit site within 4 hours, by the start of Semester 2 2027.

**Why This Matters**: REQ-009 is a Must-priority survey requirement [RR-C9]. It is also the requirement that most directly determines whether students on placement or shift work can keep up (SD-13) and whether academics trust the system (SD-12).

**Success Metrics**:

- **Primary Metric**: Percentage of timetabled lectures in equipped rooms captured and published within 4 hours
- **Secondary Metrics**:
  - Failed-capture incidents per teaching week
  - Median publication latency
  - Rooms meeting the capture capability standard

**Baseline**: ⚠️ Not yet sourced — Echo360 reporting extract due 2026-08-21. Current state is known qualitatively: capture is not universal, and scheduling depends on a timetable feed that is not fully automated.

**Target**: 100% coverage in equipped rooms; median publication latency under 1 hour; 4-hour compliance at or above 99%.

**Measurement Method**: Platform reporting reconciled against the timetable extract from Allocate+; monthly report to the steering committee.

**Dependencies**:

- Timetable data feed available to the capture platform (Ivy Sequence)
- Room capability assessment complete (SD-7)
- Provisioning automation in place so recordings publish to correctly enrolled cohorts (G-4)

**Risks to Achievement**:

- Room estate cannot support the selected platform without replacement (R-4)
- Timetable feed remains manual, so scheduling gaps persist

---

### Goal G-4: Zero manual provisioning; all access via SSO with MFA

**Derived From Drivers**: SD-1, SD-8, SD-10, SD-15

**Goal Owner**: Sam Okafor

**Goal Statement**: Eliminate manual CSV provisioning entirely and enforce university SSO with MFA for all capture platform access, with account and role changes propagating within 15 minutes, by cutover.

**Why This Matters**: REQ-025 prohibits manual CSV loads and REQ-031 prohibits local accounts [RR-C4]. The current LTI-plus-CSV arrangement breaches both, and the workaround exists specifically for casual academic staff [SL-C4] — the group least able to absorb access failures. This goal is identical under every platform option, which makes it the project's safest early investment.

**Success Metrics**:

- **Primary Metric**: Zero manual CSV provisioning events post-cutover
- **Secondary Metrics**:
  - 100% of accounts authenticated via SSO with MFA; zero local accounts
  - Provisioning latency from enrolment or appointment change under 15 minutes (aligns to REQ-023)
  - Casual staff access available on day one of appointment

**Baseline**: LTI with manual CSV; manual workaround for casual academic staff [SL-C4].

**Target**: Fully automated, event-driven provisioning against the canonical entity model.

**Measurement Method**: Provisioning audit log; identity platform report; service desk tickets categorised as access-related.

**Dependencies**:

- Canonical data model for student, course, enrolment from project 001 (REQ-027)
- Selected platform exposes a provisioning API
- Authoritative source for institutional role assignment (REQ-024)

**Risks to Achievement**:

- Selected platform supports only bulk import (mitigated by making this a mandatory gate in G-2)
- Casual staff appointment data not available as an event source

---

### Goal G-5: Captioning meets WCAG 2.2 AA on all published recordings

**Derived From Drivers**: SD-14, SD-13, SD-5

**Goal Owner**: Dr. Benny Moog, with Jazmin Field consulted

**Goal Statement**: Deliver captions on 100% of published recordings within 24 hours of publication, at a measured accuracy sufficient for WCAG 2.2 AA conformance, including discipline-specific vocabulary, from cutover.

**Why This Matters**: REQ-029 makes WCAG 2.2 AA a Must [RR-C7]. Auto-captioning quality is the difference between compliance on paper and access in practice — and it varies most where it matters most, in clinical and musical terminology (SD-14, SD-13).

**Success Metrics**:

- **Primary Metric**: Percentage of published recordings captioned within 24 hours
- **Secondary Metrics**:
  - Measured caption accuracy on a discipline-vocabulary test set
  - Correction request volume and turnaround
  - Accessibility conformance statement issued for the platform

**Baseline**: ⚠️ Not yet sourced — current captioning coverage and accuracy unknown; no test set exists.

**Target**: 100% captioned within 24 hours; accuracy validated against a test set drawn from Health Sciences and Music teaching before contract signature.

**Measurement Method**: Platform captioning report; independent accuracy sample assessed each semester; Guild feedback channel.

**Dependencies**:

- Discipline-vocabulary test set built with Health Sciences and Music (an evaluation deliverable)
- Correction workflow defined and resourced (Nina Kalimba)

**Risks to Achievement**:

- Captioning scored on vendor claims rather than tested output
- Correction workload lands on academics without support

---

### Goal G-6: Retained recordings archive migrated with exit rights proven

**Derived From Drivers**: SD-11, SD-3, SD-12, SD-1

**Goal Owner**: Eleanor Frame (retention position), Rhonda Bell (migration execution)

**Goal Statement**: Apply an approved retention schedule to the recordings archive, migrate 100% of in-retention recordings with their metadata and captions to the selected platform, preserve or redirect existing unit-site links, and demonstrate open-format export from the target platform before contract signature.

**Why This Matters**: This is the binding constraint the executive argument is currently ignoring. Principle 9 (Data Portability and Exit) and REQ-034 (export in open formats on termination) [RR-C10] apply to the platform being *left* as much as the one being joined. Migration is also the only natural point at which a retention schedule can be applied — after cutover, everything migrated becomes permanent by default (SD-11).

**Success Metrics**:

- **Primary Metric**: Percentage of in-retention recordings successfully migrated with metadata and captions intact
- **Secondary Metrics**:
  - Retention schedule approved before migration begins
  - Volume disposed of under schedule rather than migrated
  - Existing unit-site links preserved or redirected
  - Export of video, captions and metadata in open formats demonstrated from the target platform

**Baseline**: ⚠️ Not yet sourced — archive volume, storage footprint and applied retention rules due 2026-08-28. No retention schedule currently applied to recordings; analytics derived from this estate have no defined retention or minimisation rules [PC-C8].

**Target**: 100% of in-retention content migrated intact; zero unplanned loss; documented export capability tested, not asserted.

**Measurement Method**: Migration reconciliation report (source count versus target count); link-check sweep across unit sites; export test recorded in the evaluation.

**Dependencies**:

- Retention schedule approved by Education Committee on Frame's advice
- Incumbent contract terms permit bulk export (Grace Tanaka to confirm)
- Migration window outside teaching weeks (G-8)

**Risks to Achievement**:

- Incumbent export terms are restrictive or costed (R-5)
- Retention decision deferred, forcing a lift-everything migration
- Archive volume materially larger than assumed, extending the window

---

### Goal G-7: Whole-of-life cost held flat or reduced

**Derived From Drivers**: SD-1, SD-3, SD-7

**Goal Owner**: Vernon Ostinato, modelled by Rhonda Bell with Grace Tanaka

**Goal Statement**: Deliver a five-year whole-of-life cost for the consolidated capture capability — licensing, appliance refresh, migration and support — at or below the current five-year run-rate, with appliance refresh separated into "required regardless" and "caused by this decision".

**Why This Matters**: REQ-035 requires ecosystem licence spend to reduce or hold flat while closing Must-priority gaps [RR-C3]. A licence-only comparison would satisfy the letter of that requirement while producing a worse financial outcome, because this capability is the one with a physical estate behind it (SD-7).

**Success Metrics**:

- **Primary Metric**: Five-year whole-of-life cost versus current run-rate baseline
- **Secondary Metrics**:
  - Appliance refresh cost attributed correctly between "required regardless" and "decision-caused"
  - Renewal price protection secured in contract terms
  - Discipline exception costed as a named line item

**Baseline**: ⚠️ Not yet sourced — Echo360 and Zoom contract values, Microsoft entitlement position, and appliance inventory all due August 2026.

**Target**: Whole-of-life cost at or below baseline; no unfunded capex surprise at business case stage.

**Measurement Method**: Cost model reviewed by Finance at options stage and preferred-option stage; contract values confirmed by Procurement.

**Dependencies**:

- All three baseline datasets delivered on schedule
- Appliance condition assessment complete (SD-7)
- Music exception scoped sufficiently to cost (G-9)

**Risks to Achievement**:

- Appliance refresh proves necessary under every option, eliminating the saving (this is an outcome, not a failure — but it must surface early)
- Microsoft entitlement position more complex than assumed

---

### Goal G-8: Transition completed without teaching disruption

**Derived From Drivers**: SD-7, SD-12, SD-13, SD-15

**Goal Owner**: Rhonda Bell, with Marcus Fairlight and Nina Kalimba

**Goal Statement**: Complete pilot in Semester 1 2027 and full cutover in the inter-semester break, maintaining 99.9% availability through teaching periods, with zero recordings lost and support documentation published before users arrive.

**Why This Matters**: REQ-032 sets 99.9% availability for core teaching platforms during teaching periods [RR-C2]. Every operational stakeholder's worst case is the same event — a cutover that fails in week three of semester (SD-12, SD-13, SD-15).

**Success Metrics**:

- **Primary Metric**: Availability during teaching periods
- **Secondary Metrics**:
  - Zero recordings lost in transition
  - Runbooks and known-issues documentation published before cutover
  - Support ticket volume in the first four weeks post-cutover against pilot-derived forecast
  - Staff trained before their first teaching week on the new platform

**Baseline**: ⚠️ Not yet sourced — current capture-related ticket volume due 2026-08-21.

**Target**: 99.9% or better in teaching periods; zero loss; documentation complete before cutover; ticket volume within forecast.

**Measurement Method**: Platform availability reporting; service desk volumes; migration reconciliation (shared with G-6).

**Dependencies**:

- Decision closed by October 2026, leaving a viable procurement and build window
- Room works scheduled into non-teaching weeks (AV capacity)
- Pilot cohort recruited (Wynton Castle and volunteers)

**Risks to Achievement**:

- Decision slips, compressing transition into a teaching period (R-6)
- AV capacity insufficient for room works in the available window (R-4)

---

### Goal G-9: Discipline capability preserved through a bounded exception

**Derived From Drivers**: SD-9, SD-6, SD-3

**Goal Owner**: Prof. Desmond Key, assessed by Dr. Benny Moog

**Goal Statement**: Define, cost and approve a bounded performance-capture capability for named Music & Performing Arts venues under Principle 4, decided in the same governance cycle as the core platform, meeting REQ-010's multi-camera and high-fidelity audio need.

**Why This Matters**: Principle 4 — Discipline Specialisation at the Edge — is the architectural answer to REQ-010 [RR-C5]. Making the exception explicit and bounded protects the core decision from becoming a proxy fight about one school (SD-9) while preventing an unfunded promise (SD-3).

**Success Metrics**:

- **Primary Metric**: Exception scope, venues, capability standard and cost approved alongside the core recommendation
- **Secondary Metrics**:
  - Named venues and capability standard documented
  - Integration with the core platform defined (recordings discoverable through the unit site — Principle 1)
  - Support model agreed, including who maintains specialist equipment

**Baseline**: REQ-010 carries Could priority [RR-C5]; discipline tooling has sat in "investigation required" status [SL-C5]; no capability standard exists.

**Target**: Approved, bounded and funded exception — or a documented decision not to proceed, with the consequence for REQ-010 stated plainly.

**Measurement Method**: Education Committee resolution; cost line in the business case; capability standard document.

**Dependencies**:

- Core platform decision (the exception is defined relative to it)
- Venue assessment with AV (SD-7)

**Risks to Achievement**:

- Exception approved in principle but not funded (the outcome Key most expects)
- Core decision deferred, leaving the exception undefinable

---

### Goal G-10: Capture estate security debt closed

**Derived From Drivers**: SD-10, SD-7, SD-1

**Goal Owner**: Tobias Ohm, delivered with Marcus Fairlight

**Goal Statement**: Remove all shared administrative accounts from the AV and capture estate and bring capture appliances into the managed patching regime, reaching ML2 for both "restrict administrative privileges" and "patch operating systems" across this estate by end 2027.

**Why This Matters**: Both mitigation strategies are held back specifically by this estate [PC-C4], against a Digital & IT target of ML2 by end 2027 [PC-C5], and REQ-033 requires demonstrable Essential Eight alignment [RR-C11]. A platform transition touches every capture-equipped room — doing this work separately means touching them twice.

**Success Metrics**:

- **Primary Metric**: Shared administrative accounts remaining in the AV/capture estate (target: zero)
- **Secondary Metrics**:
  - Percentage of capture appliances within the managed patching regime
  - Local-account exception status against REQ-031 for any in-scope tool
  - Maturity level assessed for both mitigation strategies across this estate

**Baseline**: Restrict administrative privileges ML1 (legacy shared admin accounts in AV/capture estate); patch operating systems ML1 (lecture-theatre capture appliances behind) [PC-C4].

**Target**: ML2 on both strategies for this estate by end 2027; zero shared admin accounts at cutover.

**Measurement Method**: Essential Eight self-assessment refresh; AV asset register with patch status; identity platform account audit.

**Dependencies**:

- Appliance inventory (SD-7)
- Room works scheduled with transition (G-8)
- Funding for any appliances that cannot be brought into support

**Risks to Achievement**:

- Appliances too old to patch, converting remediation into replacement capex (R-4)
- Remediation deferred again if the platform decision slips

---

## Goal-to-Outcome Mapping

### Outcome O-1: One primary capture platform with deliberate boundaries

**Supported Goals**: G-1, G-2, G-9

**Outcome Statement**: The Learning Capture category is served by one primary platform plus one named, bounded discipline exception — replacing the current three-way overlap — with the boundary documented and enforceable through RIFF.

**Measurement Details**:

- **KPI**: Platforms in the Learning Capture category with overlapping mainstream capability
- **Current Value**: 3 (Echo360, MS Teams, Zoom) [SL-C1]
- **Target Value**: 1 primary + 1 bounded discipline exception
- **Measurement Frequency**: At each RIFF review; annually thereafter
- **Data Source**: System categorisation map, maintained by Learning Technologies
- **Report Owner**: Dr. Benny Moog

**Business Value**:

- **Financial Impact**: Removes duplicated licensing in the capture category; feeds the REQ-035 position
- **Strategic Impact**: Demonstrates Principle 2 (Deliberate Capability Boundaries) working in practice — the first real test of the principles set in `000-global`
- **Operational Impact**: One integration, one support model, one patching surface
- **Customer Impact**: Students encounter one way of accessing recorded teaching rather than three

**Timeline**:

- **Phase 1 (Aug–Oct 2026)**: Criteria agreed, evaluation complete, recommendation endorsed
- **Phase 2 (Nov 2026–Feb 2027)**: Contract executed; build and configuration
- **Phase 3 (Mar–Jul 2027)**: Pilot in Semester 1; decommission planning
- **Sustainment (2028+)**: Boundary enforced at each RIFF review; no re-entry of overlapping tooling without justification

**Stakeholder Benefits**:

- **Rhodes**: Fewer platforms to integrate, secure and fund
- **Moog**: A boundary that protects the retained capability as much as it removes the duplicate
- **Key**: A named, legitimate place for discipline capability rather than an ongoing argument
- **Ostinato**: A defensible line in the business case

**Leading Indicators** (early signals of success):

- Evaluation criteria signed by all three parties without escalation
- Deans pre-briefed and not raising objections at committee

**Lagging Indicators** (final proof of success):

- Decommissioned platform contract closed
- No new overlapping capture tooling approved through RIFF in the following 12 months

---

### Outcome O-2: Capture that works without anyone touching it

**Supported Goals**: G-3, G-4, G-8

**Outcome Statement**: Timetabled teaching is captured, provisioned and published automatically — no CSV loads, no manual scheduling, no access tickets on day one of semester.

**Measurement Details**:

- **KPI**: Composite automation index — capture coverage, 4-hour publication compliance, manual provisioning events, access-related tickets
- **Current Value**: ⚠️ Baselines due August 2026; manual CSV provisioning confirmed present [SL-C4]
- **Target Value**: 100% coverage in equipped rooms; ≥ 99% within 4 hours; zero manual provisioning events; access tickets reduced against pilot-derived forecast
- **Measurement Frequency**: Weekly during teaching periods; monthly to steering
- **Data Source**: Platform reporting, provisioning audit log, service desk
- **Report Owner**: Sam Okafor (provisioning), Dr. Benny Moog (capture)

**Business Value**:

- **Financial Impact**: Support effort released; casual staff onboarding no longer manual
- **Strategic Impact**: Proves Principle 12 (Automated Identity Lifecycle) beyond the LMS
- **Operational Impact**: Removes a named single point of failure and a weekly manual task
- **Customer Impact**: Students get recordings reliably; casual staff get access on day one

**Timeline**:

- **Phase 1 (Aug–Oct 2026)**: Provisioning capability made a mandatory evaluation gate
- **Phase 2 (Nov 2026–Feb 2027)**: Integration built against the canonical model
- **Phase 3 (Mar–Jul 2027)**: Pilot validates in live teaching
- **Sustainment (S2 2027+)**: Steady-state monitoring; automation index reported each semester

**Stakeholder Benefits**:

- **Okafor**: An architecture he can sustain
- **Kalimba**: The ticket category that dominates her queue largely disappears
- **Castle**: Recording starts without him thinking about it
- **Ohm**: No local accounts, no shared credentials

**Leading Indicators**:

- Provisioning API validated in evaluation, not assumed
- Timetable feed confirmed available to the platform

**Lagging Indicators**:

- Zero manual provisioning events across a full semester
- Access-related tickets in week one below the pilot forecast

---

### Outcome O-3: A cost position that survives the business case

**Supported Goals**: G-7, G-9, G-10

**Outcome Statement**: The capture capability is delivered at or below its current five-year run-rate, with every cost — licence, appliance, migration, support and the discipline exception — visible and attributed before approval.

**Measurement Details**:

- **KPI**: Five-year whole-of-life cost versus baseline run-rate
- **Current Value**: ⚠️ Not yet sourced — contract and appliance baselines due August 2026
- **Target Value**: At or below baseline, with capex separately identified
- **Measurement Frequency**: At options stage, preferred-option stage, and annually post-implementation
- **Data Source**: Contract register, AV asset register, project cost model
- **Report Owner**: Vernon Ostinato

**Business Value**:

- **Financial Impact**: Direct contribution to the REQ-035 licence position
- **Strategic Impact**: Establishes whole-of-life costing as the norm for L&T platform decisions
- **Operational Impact**: Appliance refresh planned rather than reactive
- **Customer Impact**: Indirect — funds released remain available to close Must-priority capability gaps

**Timeline**:

- **Phase 1 (Aug 2026)**: Baselines sourced
- **Phase 2 (Sep–Oct 2026)**: Options costed whole-of-life; preferred option confirmed
- **Phase 3 (Sep 2026)**: Feeds the business case
- **Sustainment (2027+)**: Annual actual-versus-model review

**Stakeholder Benefits**:

- **Ostinato**: No capex surprise; a saving he can attest to
- **Rhodes**: Her consolidation argument tested on complete numbers rather than asserted
- **Fairlight**: Appliance refresh acknowledged and funded rather than absorbed
- **Key**: The exception costed rather than promised

**Leading Indicators**:

- All six baseline datasets delivered by their due dates
- Appliance refresh split between "required regardless" and "decision-caused"

**Lagging Indicators**:

- Year-one actual spend within tolerance of the model
- No unplanned capital request in the first 24 months

---

### Outcome O-4: A defensible privacy and security position for recordings

**Supported Goals**: G-6, G-10, G-4

**Outcome Statement**: Recordings capturing students are held under a stated residency position with APP 8 assessed where applicable, subject to an approved retention and disposal schedule, accessible only through SSO with MFA, on an estate within the managed patching regime.

**Measurement Details**:

- **KPI**: Compliance position across four elements — residency/APP 8, retention schedule applied, authentication, appliance patching
- **Current Value**: Video/audio recordings classified as personal information with biometric-adjacent character, assumed AU/US hosting, flagged as a partial APP 8 trigger [PC-C2] [PC-C7]; no defined retention rules [PC-C8]; two mitigation strategies at ML1 for this estate [PC-C4]
- **Target Value**: All four elements closed — assessed, approved, enforced, patched
- **Measurement Frequency**: PIA at selection; annual privacy review; Essential Eight self-assessment refresh
- **Data Source**: PIA, retention schedule, identity platform, AV asset register
- **Report Owner**: Eleanor Frame (privacy), Tobias Ohm (security)

**Business Value**:

- **Financial Impact**: Avoided remediation and reduced breach exposure; storage released by disposal
- **Strategic Impact**: Evidence for the Essential Eight ML2 pathway and the university's APP posture
- **Operational Impact**: Defined disposal rather than indefinite accumulation
- **Customer Impact**: Students informed about recording, with their recordings held under a stated retention rule

**Timeline**:

- **Phase 1 (Aug–Sep 2026)**: Residency and export requirements written into evaluation; PIA initiated
- **Phase 2 (Oct 2026–Feb 2027)**: PIA completed on the preferred option; retention schedule approved; contract clauses settled
- **Phase 3 (Mar–Jul 2027)**: Schedule applied at migration; appliance remediation with room works
- **Sustainment (2027+)**: Annual review; disposal runs on schedule

**Stakeholder Benefits**:

- **Frame**: Her position secured at the only point where she has leverage — before signature
- **Ohm**: Two mitigation strategies unblocked
- **Field**: A consent and notification position students can actually read
- **Rhodes**: An estate she can attest to

**Leading Indicators**:

- Residency and export clauses present in the evaluation before vendor engagement
- Retention schedule drafted before migration planning starts

**Lagging Indicators**:

- PIA completed with no unmitigated high findings
- ML2 achieved on both mitigation strategies for this estate

---

### Outcome O-5: Equitable access to recorded teaching

**Supported Goals**: G-3, G-5, G-8

**Outcome Statement**: Every student, in every school, can find and use recordings of their teaching — captioned to a usable standard, published reliably, and reached through the same route regardless of who teaches them.

**Measurement Details**:

- **KPI**: Composite access index — publication compliance, caption coverage and accuracy, variance in publication practice between schools
- **Current Value**: ⚠️ Not yet sourced; publication practice known to vary and captioning coverage unmeasured
- **Target Value**: ≥ 99% published within 4 hours; 100% captioned within 24 hours at validated accuracy; no material variance between schools
- **Measurement Frequency**: Each teaching period
- **Data Source**: Platform reporting; independent caption accuracy sample; Guild feedback
- **Report Owner**: Dr. Benny Moog, with Jazmin Field consulted

**Business Value**:

- **Financial Impact**: Reduced ad-hoc captioning and accessibility remediation
- **Strategic Impact**: Delivers Principle 3 (Consistent Experience Across Schools) and Principle 14 (Accessibility by Default) in the capability where inconsistency is most visible
- **Operational Impact**: One publication practice to support and document
- **Customer Impact**: Direct — placement and shift-working students, students with disability, and students studying in a second language

**Timeline**:

- **Phase 1 (Sep–Oct 2026)**: Caption accuracy tested on a discipline-vocabulary set during evaluation
- **Phase 2 (Nov 2026–Feb 2027)**: Publication standard agreed with Education Committee
- **Phase 3 (Mar–Dec 2027)**: Measured through pilot and first full semester
- **Sustainment (2028+)**: Reported to Education Committee each year

**Stakeholder Benefits**:

- **Field**: A measurable standard rather than an assurance
- **Anand**: Her cohorts' dependence on recordings met reliably
- **Clavinet**: Evidence her committee made an educational decision
- **Castle**: Clear expectations rather than school-by-school improvisation

**Leading Indicators**:

- Discipline-vocabulary test set built and used in evaluation
- Publication standard drafted before cutover

**Lagging Indicators**:

- Caption accuracy sustained across a full year
- No accessibility complaint upheld against recorded teaching

---

### Outcome O-6: A decision that holds

**Supported Goals**: G-1, G-2, G-9

**Outcome Statement**: The platform question stays closed — endorsed through RIFF and Education Committee with dissent recorded and addressed, and not reopened at the next renewal.

**Measurement Details**:

- **KPI**: Decision stability — reopening attempts, and whether the RIFF duplication rule is applied consistently to subsequent requests
- **Current Value**: Contested; no decision; positions held publicly by two senior stakeholders [S-C2]
- **Target Value**: Endorsed decision with recorded dissent; zero substantive reopenings within 24 months
- **Measurement Frequency**: At each RIFF review
- **Data Source**: RIFF register; ADR in project 001; committee minutes
- **Report Owner**: Dr. Benny Moog (RIFF register), Rhonda Bell (ADR)

**Business Value**:

- **Financial Impact**: Avoided cost of repeated evaluation cycles
- **Strategic Impact**: Establishes that contested architecture decisions can be resolved through governance rather than seniority
- **Operational Impact**: Teams can plan against a settled platform
- **Customer Impact**: Stability — students and staff are not moved between platforms repeatedly

**Timeline**:

- **Phase 1 (Sep–Oct 2026)**: Decision taken through all three gates
- **Phase 2 (Nov 2026)**: ADR published in project 001's decisions register
- **Phase 3 (2027)**: Boundary applied to new requests through RIFF
- **Sustainment (2028+)**: Reviewed at contract renewal, not relitigated between

**Stakeholder Benefits**:

- **Hammond**: The decision does not return to him
- **Clavinet**: Her committee's authority demonstrated
- **Moog and Rhodes**: Both can point to a process they participated in shaping
- **Tanaka**: A record that would survive audit

**Leading Indicators**:

- Both principals sign the evaluation criteria
- Dissent recorded in RIFF minutes rather than aired afterwards

**Lagging Indicators**:

- No reopening attempt within 24 months
- Subsequent duplicate-capability requests refused consistently under the same rule

---

## Complete Traceability Matrix

### Stakeholder → Driver → Goal → Outcome

| Stakeholder | Driver ID | Driver Summary | Goal ID | Goal Summary | Outcome ID | Outcome Summary |
|-------------|-----------|----------------|---------|--------------|------------|-----------------|
| Cassandra Rhodes (CIO) | SD-1 | Consolidate onto licensed capability | G-1 | Decision endorsed by Oct 2026 | O-1 | One platform, bounded |
| Cassandra Rhodes (CIO) | SD-1 | Consolidate onto licensed capability | G-7 | Whole-of-life cost flat or down | O-3 | Defensible cost position |
| Cassandra Rhodes (CIO) | SD-1 | Fewer platforms to secure | G-4 | Zero manual provisioning, SSO/MFA | O-2 | Capture that runs itself |
| Grace Tanaka (Procurement) | SD-2 | Defensible process | G-2 | Published unchanged criteria | O-6 | A decision that holds |
| Grace Tanaka (Procurement) | SD-2 | Defensible process | G-1 | Decision endorsed by Oct 2026 | O-1 | One platform, bounded |
| Vernon Ostinato (CFO) | SD-3 | No surprise capital | G-7 | Whole-of-life cost flat or down | O-3 | Defensible cost position |
| Vernon Ostinato (CFO) | SD-3 | Real saving delivered | G-9 | Exception costed, not promised | O-3 | Defensible cost position |
| Prof. Otis Hammond (DVC) | SD-4 | Decision that does not return | G-1 | Decision endorsed by Oct 2026 | O-6 | A decision that holds |
| Prof. Otis Hammond (DVC) | SD-4 | Legitimacy on both sides | G-2 | Published unchanged criteria | O-6 | A decision that holds |
| A/Prof. Pearl Clavinet (Dean L&T) | SD-5 | Pedagogy seen to lead | G-2 | Teaching criteria weighted visibly | O-5 | Equitable access |
| A/Prof. Pearl Clavinet (Dean L&T) | SD-5 | Educational decision, not cost exercise | G-5 | Captioning to WCAG 2.2 AA | O-5 | Equitable access |
| Dr. Benny Moog (Learning Tech) | SD-6 | Do not trade capability for tidiness | G-2 | Criteria reflect teaching use | O-1 | One platform, bounded |
| Dr. Benny Moog (Learning Tech) | SD-6 | Protect capture capability | G-3 | Coverage and 4-hour publication | O-2 | Capture that runs itself |
| Marcus Fairlight (AV) | SD-7 | Supportable estate | G-10 | Security debt closed | O-4 | Defensible privacy/security |
| Marcus Fairlight (AV) | SD-7 | Estate cost made visible | G-7 | Whole-of-life cost flat or down | O-3 | Defensible cost position |
| Marcus Fairlight (AV) | SD-7 | Room works in the right window | G-8 | Transition without disruption | O-2 | Capture that runs itself |
| Sam Okafor (Integration) | SD-8 | End manual provisioning | G-4 | Zero manual provisioning, SSO/MFA | O-2 | Capture that runs itself |
| Sam Okafor (Integration) | SD-8 | Sustainable architecture | G-3 | Coverage and 4-hour publication | O-2 | Capture that runs itself |
| Prof. Desmond Key (Music) | SD-9 | Performance capture preserved | G-9 | Bounded discipline exception | O-1 | One platform, bounded |
| Tobias Ohm (Security) | SD-10 | Close security debt | G-10 | Security debt closed | O-4 | Defensible privacy/security |
| Tobias Ohm (Security) | SD-10 | No local accounts | G-4 | Zero manual provisioning, SSO/MFA | O-4 | Defensible privacy/security |
| Eleanor Frame (Privacy) | SD-11 | Defensible privacy position | G-6 | Archive migrated, exit proven | O-4 | Defensible privacy/security |
| Eleanor Frame (Privacy) | SD-11 | Retention applied | G-6 | Retention schedule at migration | O-4 | Defensible privacy/security |
| Dr. Wynton Castle (Academic) | SD-12 | Do not make teaching harder | G-8 | Transition without disruption | O-2 | Capture that runs itself |
| Dr. Wynton Castle (Academic) | SD-12 | Recordings where students look | G-3 | Coverage and 4-hour publication | O-5 | Equitable access |
| Prof. Priya Anand (Health Sci) | SD-13 | Large cohorts depend on this | G-3 | Coverage and 4-hour publication | O-5 | Equitable access |
| Prof. Priya Anand (Health Sci) | SD-13 | No disruption to my cohorts | G-8 | Transition without disruption | O-2 | Capture that runs itself |
| Jazmin Field (Student Guild) | SD-14 | Captions and equal access | G-5 | Captioning to WCAG 2.2 AA | O-5 | Equitable access |
| Jazmin Field (Student Guild) | SD-14 | Students told they are recorded | G-6 | Retention and consent position | O-4 | Defensible privacy/security |
| Nina Kalimba (Support) | SD-15 | Trained team, documented workflow | G-8 | Transition without disruption | O-2 | Capture that runs itself |
| Ivy Sequence (Timetabling) | — | Scheduling data consumed cleanly | G-3 | Coverage and 4-hour publication | O-2 | Capture that runs itself |
| Students (external) | SD-14 (proxy) | Access to recorded teaching | G-5 | Captioning to WCAG 2.2 AA | O-5 | Equitable access |

### Conflict Analysis

**Competing Drivers**:

- **Conflict 1 — Platform philosophy**: Rhodes (SD-1) wants consolidation onto already-licensed Microsoft capability; Moog (SD-6) and Key (SD-9) defend purpose-built capture and discipline tooling. Incompatible because each is arguing from a different definition of the product class — general-purpose recording versus lecture capture — and because both can cite institutional principle (19 versus 4) in support.
  - **Resolution Strategy**: Decide the *criteria* before the *product*. Run a weighting workshop in which Rhodes, Moog and Clavinet must agree what matters and how much, signed before any vendor engagement (G-2). Separate the core decision from the discipline exception (G-9) so Music's genuine requirement is not the vehicle for the general argument. Where the two principles collide, Principle 2 (Deliberate Capability Boundaries) is the tie-breaker: the question is not which product is better but where the boundary belongs.

- **Conflict 2 — The hidden capex**: Ostinato (SD-3) needs a licence saving; Fairlight (SD-7) knows the appliance estate needs investment regardless. A licence-only comparison makes Fairlight's constraint invisible until it is too late to fund.
  - **Resolution Strategy**: Mandate whole-of-life costing in the options analysis (G-7), with appliance refresh explicitly split into "required regardless of this decision" and "caused by this decision". Ostinato sees the true saving; Fairlight's estate stops being a surprise. Surface this at the options stage, not the preferred-option stage.

- **Conflict 3 — Speed versus contestability**: Rhodes's route (vary the existing agreement) is faster and cheaper to execute; Tanaka (SD-2) needs a value-for-money record and a process that survives challenge, particularly given publicly stated positions.
  - **Resolution Strategy**: Resolved in favour of contestability — the requirement goes to **competitive tender** rather than varying the existing agreement, with the written value-for-money rationale required by the RIFF duplication rule recorded in the decision file [SGP-C2]. That rationale is substantially the same evidence Moog would demand anyway. The probity control (single vendor contact through Tanaka) applies throughout. Rhodes loses the faster route; she retains the ability to have the already-licensed option evaluated on equal terms, which is the substance of her position rather than its mechanism.

- **Conflict 4 — Keep everything versus keep what we should**: Academics (SD-12) and Deans expect recordings to remain available indefinitely; Frame (SD-11) needs a retention schedule with actual disposal.
  - **Resolution Strategy**: Use migration as the forcing point (G-6) — it is the only moment when disposal is operationally natural. Take the retention schedule to Education Committee on Frame's advice *before* migration planning, with an archive-on-request path for genuinely reusable teaching material so the academic concern has a real answer rather than a refusal.

- **Conflict 5 — Recording and the classroom**: Field (SD-14) wants recordings published consistently across all schools; some academics resist universal capture over attendance effects and discomfort at being recorded (SD-12, quietly).
  - **Resolution Strategy**: This is a policy question, not a platform question, and it must not be settled by default through a technical configuration. Take a capture policy to Education Committee covering publication expectations, any unit-level exceptions and their approval route, and student notification. Principle 3 (Consistent Experience Across Schools) sets the default; exceptions are approved, documented and visible rather than exercised silently.

- **Conflict 6 — Governance role and held position**: Moog chairs the RIFF review and holds a position on the outcome.
  - **Resolution Strategy**: Not a disqualification — his expertise is the reason he chairs it. For this decision only, Hammond chairs the RIFF session, Moog presents the capability evidence as a participant, and his position is recorded as a stated interest in the minutes. Documented in the RACI (Section 11).

**Synergies**:

- **Synergy 1 — Provisioning automation**: Rhodes (SD-1), Okafor (SD-8), Ohm (SD-10) and Kalimba (SD-15) all want the same thing for four different reasons — fewer integrations, a sustainable architecture, no shared credentials, fewer tickets. G-4 is platform-neutral and can start immediately, before the contested decision is made.
- **Synergy 2 — Contract terms**: Frame's residency and export requirements (SD-11), Ohm's security terms (SD-10) and Tanaka's exit provisions (SD-2) are one clause set drafted once, serving privacy, security and commercial exit simultaneously — and each is stronger for being demanded by three parties rather than one.
- **Synergy 3 — Reliable, captioned publication**: Field (SD-14), Anand (SD-13), Castle (SD-12) and Clavinet (SD-5) converge on G-3 and G-5. Accessibility, cohort equity, academic workload and educational quality are the same requirement seen from four angles.
- **Synergy 4 — Nobody wants to pay twice**: Ostinato (SD-3), Rhodes (SD-1) and Moog (SD-6) all endorse Principle 19 — realise licensed capability before new spend. They disagree entirely on which licensed capability is going unrealised. Naming the shared principle is the most productive available opening for the weighting workshop.

---

## Communication & Engagement Plan

### Stakeholder-Specific Messaging

#### Cassandra Rhodes (CIO)

**Primary Message**: The consolidation case will be tested properly and on complete numbers — including the estate costs that a licence comparison would hide.

**Key Talking Points**:

- Provisioning automation, SSO/MFA enforcement and appliance remediation are being progressed now, independent of platform choice — your security and integration outcomes are not waiting on the decision
- Whole-of-life costing will show the true consolidation saving rather than an optimistic one
- The RIFF duplication rule is being applied in both directions, which strengthens rather than weakens your position if the evidence supports it

**Communication Frequency**: Weekly

**Preferred Channel**: Working session with Bell and Okafor; steering fortnightly

**Success Story**: One capture platform, automated provisioning, no local accounts, and an estate she can attest to in the Essential Eight self-assessment.

---

#### Dr. Benny Moog (Director, Learning Technologies)

**Primary Message**: Capability evidence you own will be weighted in the criteria before any product is compared — and the discipline exception is being handled as architecture, not as a concession.

**Key Talking Points**:

- Capability comparison runs against the eight-category taxonomy, not a vendor feature checklist
- You co-sign the evaluation criteria; they are not set by Digital & IT alone
- Chairing arrangements for the RIFF session on this decision are adjusted so your stated position is not a governance problem
- LMS integration and analytics are in the mandatory requirement set, not the nice-to-have list

**Communication Frequency**: Weekly

**Preferred Channel**: Working session; capability evidence workshops

**Success Story**: The retained platform demonstrably meets teaching requirements, and the boundary is documented so it holds.

---

#### Grace Tanaka (Procurement & Vendor Manager)

**Primary Message**: You own the process gate; the project will not ask you to compromise it for timeline.

**Key Talking Points**:

- Criteria signed before vendor engagement; no post-issue changes
- All vendor contact through you, including from Rhodes and Moog
- Competitive tender route settled, with the written value-for-money justification on record
- Contract clause set covers residency, export, breach notification and renewal pricing

**Communication Frequency**: Weekly

**Preferred Channel**: Procurement working session

**Success Story**: A decision file that would survive audit, and terms that make the next renewal easier.

---

#### Prof. Otis Hammond (DVC Education) and A/Prof. Pearl Clavinet (Dean L&T)

**Primary Message**: The recommendation will arrive with its opposition addressed and its academic evidence visible — not as an argument for you to settle.

**Key Talking Points**:

- Both principals sign the criteria before evaluation, so the process itself is not contested afterwards
- Academic reference group input is documented in the recommendation
- Teaching-quality and accessibility criteria carry visible weight
- Pre-briefing before every committee paper; no first sight at committee

**Communication Frequency**: Fortnightly (Hammond, steering); before each committee cycle (Clavinet)

**Preferred Channel**: Steering committee; pre-briefing meetings

**Success Story**: Education Committee endorses on the first pass, and the decision is not reopened.

---

#### Vernon Ostinato (CFO)

**Primary Message**: Every cost is on the table at options stage, including the appliance refresh — no capital surprises at business case.

**Key Talking Points**:

- Five-year whole-of-life model covering licence, appliances, migration, support and the discipline exception
- Appliance refresh split into "required regardless" and "decision-caused"
- Renewal price protection sought in contract terms
- Feeds directly into the September business case structure

**Communication Frequency**: At options stage and preferred-option stage; monthly written update

**Preferred Channel**: Cost model review meeting; written summary

**Success Story**: A saving he can attest to, with the capital consequence known in advance.

---

#### Prof. Desmond Key (Music) and Prof. Priya Anand (Health Sciences)

**Primary Message**: Discipline capability is being scoped, costed and decided in the same cycle as the core platform — under Principle 4, not as an afterthought.

**Key Talking Points**:

- Performance capture is treated as a named exception with defined venues and a capability standard, not as an objection to the core
- REQ-010's Could priority reflects institutional breadth, not disciplinary importance — the exception route exists for exactly this case
- Simulation-context capture will be assessed explicitly rather than assumed in or out
- Transition sequenced around assessment periods

**Communication Frequency**: Monthly, with a dedicated session at options stage

**Preferred Channel**: Faculty meeting; site visits to performance venues and simulation labs

**Success Story**: Performance and simulation capture continue, funded and supported, with recordings still reaching students through the unit site.

---

#### Marcus Fairlight (AV), Sam Okafor (Integration), Tobias Ohm (Security), Eleanor Frame (Privacy)

**Primary Message**: Your requirements are mandatory gates in the evaluation, not weighted criteria that can be traded away.

**Key Talking Points**:

- SSO/MFA (REQ-031), accessibility (REQ-029) and data export (REQ-034) are pass/fail
- Room compatibility assessed before, not after, the decision
- PIA runs on the preferred option before contract signature, while there is still leverage
- Appliance remediation is funded and scheduled with the room works, not deferred to a later programme

**Communication Frequency**: Weekly (Fairlight, Okafor), fortnightly (Ohm, Frame)

**Preferred Channel**: Technical working group

**Success Story**: Two Essential Eight strategies move to ML2, provisioning is automated, and the privacy position is settled before signature.

---

#### Dr. Wynton Castle (academics), Nina Kalimba (support), Jazmin Field (students)

**Primary Message**: Nothing changes mid-semester, the recordings you rely on come with you, and training and documentation arrive before the platform does.

**Key Talking Points**:

- Pilot in Semester 1 2027, full cutover in the break — no mid-semester switch
- Existing recording links preserved or redirected; in-retention recordings migrated
- Captions tested against real clinical and musical vocabulary before selection, not after
- Recordings continue to appear in the unit site — one place to look (Principle 1)
- Students will be told clearly when and how they are recorded

**Communication Frequency**: Monthly, moving to weekly during transition

**Preferred Channel**: Academic reference group; Guild meetings; unit coordinator briefings

**Success Story**: Semester 2 2027 starts with recordings appearing where they always did, captioned, with nobody needing to ask how.

---

## Change Impact Assessment

### Impact on Stakeholders

| Stakeholder | Current State | Future State | Change Magnitude | Resistance Risk | Mitigation Strategy |
|-------------|---------------|--------------|------------------|-----------------|---------------------|
| Dr. Wynton Castle (and academics) | Familiar capture workflow; recordings published to unit sites | Possibly a new capture workflow; same publication point | MEDIUM | MEDIUM | Pilot participation; training before their first teaching week; links preserved |
| Casual academic staff | Access depends on a manual CSV run | Automated provisioning on appointment | HIGH (positive) | LOW | Communicate the improvement explicitly — this group has been carrying the failure |
| Nina Kalimba's support team | Reactive support for known failure modes | New platform, new failure modes, then fewer of them | HIGH | MEDIUM | Pilot-derived runbooks; documentation as a deliverable; training window |
| Marcus Fairlight's AV team | Ageing appliances, shared admin accounts, unpatched | Managed, patched estate with individual credentials | HIGH | LOW | Funded and scheduled; resource the room works properly rather than absorbing them |
| Prof. Desmond Key / Music staff | Discipline capability informally sustained | Named, bounded, funded exception — or a documented gap | HIGH | HIGH | Decide in the same cycle as the core; scope and cost it; do not approve in principle only |
| Dr. Benny Moog | Owns platform relationship and roadmap | May be operating a platform he argued against | MEDIUM | HIGH | Co-sign criteria; own the capability evidence; record dissent formally |
| Cassandra Rhodes | Advocating consolidation | May be funding a specialist platform she argued against | MEDIUM | MEDIUM | Same mechanism — a process she shaped; security and integration outcomes delivered either way |
| Students | Variable access and captioning by school | Consistent publication and captioning | MEDIUM (positive) | LOW | Guild engagement; clear notification about recording |
| Eleanor Frame | No retention rule applied to recordings | Approved schedule with actual disposal | MEDIUM | LOW (from her); MEDIUM (from academics) | Archive-on-request path for genuinely reusable material |
| Ivy Sequence (Timetabling) | Timetable data used downstream via batch | Timetable feed drives capture scheduling | LOW | LOW | Consult early on feed design; no additional manual step |

### Change Readiness

**Champions** (Enthusiastic supporters):

- **Sam Okafor** — the provisioning outcome is what he has wanted since the CSV workaround was introduced; platform-agnostic, so he is a champion under every scenario
- **Tobias Ohm** — this project unblocks two of his Essential Eight strategies
- **Nina Kalimba** — her team currently absorbs the failure modes; she supports almost any change that removes them, provided it is documented
- **Jazmin Field** — captioning and consistency are her platform; she has no stake in the vendor question
- **Grace Tanaka** — a properly run process is a professional win regardless of outcome

**Fence-sitters** (Neutral, need convincing):

- **Prof. Otis Hammond** — supports resolution, not a particular answer; convinced by a recommendation that arrives with dissent already addressed
- **A/Prof. Pearl Clavinet** — will support whichever option the academic evidence supports; needs to see teaching quality weighted and reference group input documented
- **Prof. Priya Anand** — indifferent to platform, highly sensitive to transition risk; convinced by the pilot and cutover timing
- **Dr. Wynton Castle** — convinced by continuity: same publication point, preserved links, training before teaching
- **Vernon Ostinato** — supportive if the saving survives whole-of-life costing; a sceptic the moment appliance capex appears late

**Resisters** (Opposed or skeptical):

- **Prof. Desmond Key** — resists any outcome that leaves performance capture unfunded. His scepticism is specifically that the exception will be endorsed in principle and then quietly dropped from the business case. **Strategy**: put the exception in the same governance paper as the core recommendation, with a cost line, so approval or refusal is explicit and on the record.
- **Dr. Benny Moog** — sceptical that a consolidation-driven evaluation can fairly assess teaching capability. **Strategy**: he co-signs the criteria and owns the capability evidence; adjusted RIFF chairing removes the governance strain; formal dissent is recorded rather than absorbed.
- **Cassandra Rhodes** (if the outcome goes against her) — the mirror-image risk, and equally real. **Strategy**: identical mechanism. A process she helped design is the only thing that makes an adverse outcome acceptable to her.
- **A minority of academic staff** — opposed to universal capture on attendance and performance-observation grounds; unlikely to raise it in the platform conversation, likely to raise it at the policy one. **Strategy**: separate the capture policy from the platform decision and take it to Education Committee on its own merits.

---

## Risk Register (Stakeholder-Related)

### Risk R-1: Criteria negotiation becomes the proxy battleground

**Related Stakeholders**: Rhodes, Moog, Clavinet, Tanaka, Hammond

**Risk Description**: The weighting workshop deadlocks because each party recognises that whoever sets the weights sets the outcome. Criteria are renegotiated repeatedly, or agreed and then disputed after evaluation.

**Impact on Goals**: G-1, G-2, and through them O-1 and O-6

**Probability**: HIGH

**Impact**: HIGH

**Mitigation Strategy**: Facilitate the workshop independently (Bell, not Rhodes or Moog). Anchor weights to requirement priority in the register — Must-priority requirements carry more weight than Should, which is a rule neither party set and both already accepted [RR-C8]. Set mandatory pass/fail gates first, so security, accessibility and export are removed from the trading space entirely. Cap the workshop at two sessions with escalation to Hammond on the second.

**Contingency Plan**: Hammond sets the weights on written submissions from both parties, with the rationale minuted. Slower and more damaging to goodwill, but decisive.

---

### Risk R-2: Informal vendor contact compromises the process

**Related Stakeholders**: Rhodes, Moog, Tanaka, incumbent and Microsoft account teams

**Risk Description**: Both principals hold established vendor relationships. Continued informal contact after criteria drafting begins — even innocently — exposes the process to challenge and gives one supplier an advantage.

**Impact on Goals**: G-2, and through it O-6

**Probability**: MEDIUM

**Impact**: HIGH

**Mitigation Strategy**: Single point of contact through Tanaka from the date criteria drafting starts, communicated in writing to both principals and to all three suppliers. Contact log maintained. Clear guidance on what may still be discussed (existing contractual matters) and what may not (anything touching this evaluation).

**Contingency Plan**: Disclose any breach in the RIFF paper, assess materiality with Procurement, and if material, extend the same information to all suppliers to restore parity.

---

### Risk R-3: Education Committee returns the paper

**Related Stakeholders**: Clavinet, Hammond, Bell, Moog

**Risk Description**: The recommendation reads as a cost and consolidation exercise; the committee sends it back for stronger academic evidence, costing a full committee cycle and pushing the decision past the business case window.

**Impact on Goals**: G-1, G-8 (compressed transition), and through them O-6

**Probability**: MEDIUM

**Impact**: HIGH

**Mitigation Strategy**: Pre-brief Clavinet before the paper is finalised. Document academic reference group input, including Castle's. Lead the paper with teaching outcomes and evidence, with cost as supporting analysis rather than the argument.

**Contingency Plan**: Seek an out-of-cycle committee meeting; failing that, re-plan transition to a Semester 2 2027 pilot with full cutover in 2028, and state the delay's cost plainly.

---

### Risk R-4: Room estate cannot support the selected platform

**Related Stakeholders**: Fairlight, Ostinato, Rhodes, Bell

**Risk Description**: The appliance assessment (due August 2026) finds a material proportion of capture-equipped rooms incompatible with the preferred platform or beyond patching support, converting a licence decision into a capital replacement programme.

**Impact on Goals**: G-3, G-7, G-8, G-10; and O-2, O-3

**Probability**: MEDIUM

**Impact**: HIGH

**Mitigation Strategy**: Complete the appliance inventory before, not after, the platform decision — it is scheduled for 2026-08-21 specifically to precede evaluation. Include room compatibility as a scored criterion. Split refresh cost into "required regardless" and "decision-caused" so the finding informs the decision rather than ambushing it.

**Contingency Plan**: Phase the room programme over two years, prioritising the largest teaching spaces, and adjust the coverage target for G-3 explicitly rather than silently missing it.

---

### Risk R-5: Archive export from the incumbent proves restrictive or costly

**Related Stakeholders**: Frame, Tanaka, Moog, Ostinato

**Risk Description**: Existing contract terms limit bulk export, or export is technically possible but priced, or metadata and captions cannot be exported with the media — stranding the retained archive and undermining Principle 9.

**Impact on Goals**: G-6, G-7; and O-4

**Probability**: MEDIUM

**Impact**: HIGH

**Mitigation Strategy**: Tanaka reviews incumbent contract export terms as part of the August baseline, before criteria are finalised. Test export practically during evaluation rather than accepting a contractual assurance. Apply the retention schedule first, so the volume needing export is the smallest defensible set.

**Contingency Plan**: Retain read-only access to the incumbent archive for a defined transition period, with a hard end date and a documented plan for content still required at that point. Budget for it explicitly rather than discovering it.

---

### Risk R-6: Decision slips past October, compressing transition

**Related Stakeholders**: Hammond, Bell, Fairlight, Kalimba, Anand

**Risk Description**: Governance cycles, criteria deadlock or missing baselines push the decision into late 2026, leaving insufficient time to procure, build, migrate and train before Semester 1 2027 — creating pressure to cut over during a teaching period.

**Impact on Goals**: G-1, G-8; and O-2, O-5

**Probability**: MEDIUM

**Impact**: HIGH

**Mitigation Strategy**: Baseline data due dates tracked as hard milestones with named owners (Section 1). Committee dates confirmed and papers scheduled backwards from them now. Progress the platform-neutral work (G-4, G-5 test set, G-6 retention schedule, G-10 remediation) in parallel so slippage costs less.

**Contingency Plan**: Move to pilot in Semester 2 2027 with full cutover at the start of 2028. **Do not cut over mid-semester under any circumstance** — REQ-032 and every operational stakeholder's core driver both prohibit it.

---

### Risk R-7: The discipline exception is approved in principle but unfunded

**Related Stakeholders**: Key, Ostinato, Clavinet, Hammond

**Risk Description**: The exception is endorsed to close the argument, then drops out of the business case when costs are trimmed — losing REQ-010 capability and confirming Key's expectation that discipline needs get consolidated away.

**Impact on Goals**: G-9; and O-1

**Probability**: MEDIUM

**Impact**: MEDIUM

**Mitigation Strategy**: Present the exception with a costed line item in the same governance paper as the core recommendation, so approval means approving the cost. Define the capability standard and named venues concretely enough that a later reduction is visible rather than silent.

**Contingency Plan**: If funding is refused, record the decision and its consequence for REQ-010 explicitly in the ADR and the risk register, so the capability gap is a governed choice rather than an accident.

---

## Governance & Decision Rights

### Decision Authority Matrix (RACI)

| Decision Type | Responsible | Accountable | Consulted | Informed |
|---------------|-------------|-------------|-----------|----------|
| Evaluation criteria and weightings | Rhonda Bell (facilitator) | Grace Tanaka | Rhodes, Moog, Clavinet, Ohm, Frame, Fairlight | Steering Committee |
| Mandatory pass/fail gates (SSO/MFA, accessibility, export) | Tobias Ohm, Eleanor Frame | Grace Tanaka | Okafor, Field | All stakeholders |
| Procurement route — **decided: competitive tender** | Grace Tanaka | Prof. Otis Hammond | Rhodes, Ostinato, Moog | Education Committee |
| Capability evidence and scoring | Dr. Benny Moog | Prof. Otis Hammond | Academic reference group, Deans | Steering Committee |
| Room and appliance assessment | Marcus Fairlight | Cassandra Rhodes | Ohm, Bell | Ostinato |
| Platform recommendation | Rhonda Bell | Prof. Otis Hammond | Rhodes, Moog, Tanaka, Clavinet | All stakeholders |
| RIFF review of the recommendation | **Prof. Otis Hammond (chair, this decision only)** | Education Committee | Moog (presenting, interest declared), Rhodes, Tanaka | All stakeholders |
| Academic approval | A/Prof. Pearl Clavinet | Education Committee | Deans, academic reference group | All stakeholders |
| Discipline exception (scope, standard, cost) | Prof. Desmond Key | Education Committee | Moog, Fairlight, Ostinato | Operations Committee |
| Capture policy (publication, unit-level exceptions, notification) | Dr. Benny Moog | Education Committee | Field, Frame, Castle, Deans | All staff and students |
| Recordings retention schedule | Eleanor Frame | Education Committee | Moog, Deans, Records | All staff |
| Business case and funding | Vernon Ostinato | Operations Committee / University Executive | Hammond, Rhodes, Tanaka | All stakeholders |
| Contract terms and signature | Grace Tanaka | Cassandra Rhodes | Frame, Ohm, Legal | Ostinato |
| Migration cutover go/no-go | Rhonda Bell | Cassandra Rhodes | Fairlight, Kalimba, Moog, Deans | All stakeholders |

> **Governance note**: Moog chairs RIFF reviews as a standing role [S-C8] and holds a position on this decision. For this decision only, Hammond chairs the RIFF session and Moog participates as capability evidence owner with his interest declared in the minutes. This protects both the decision and Moog — his expertise remains available without his impartiality being the argument.

### Escalation Path

1. **Level 1**: Rhonda Bell, Project Manager — day-to-day delivery, scheduling, information flow
2. **Level 2**: Steering Committee (Hammond chair; Rhodes, Clavinet) — criteria disputes, scope, timeline, resourcing
3. **Level 3**: RIFF Review — architectural fit, capability duplication, integration impact, total cost [SGP-C1]
4. **Level 4**: Education Committee (Clavinet chair) — academic approval of the solution request
5. **Level 5**: Operations Committee and/or University Executive (Groove) — financial and strategic approval where thresholds are exceeded [SGP-C4]

---

## Validation & Sign-off

### Stakeholder Review

| Stakeholder | Review Date | Comments | Status |
|-------------|-------------|----------|--------|
| Prof. Otis Hammond (Executive Sponsor) | Scheduled 2026-08-07 | Pending | CHANGES_REQUESTED — not yet reviewed |
| Cassandra Rhodes (CIO) | Scheduled 2026-08-07 | Pending | CHANGES_REQUESTED — not yet reviewed |
| Grace Tanaka (Procurement) | Scheduled 2026-08-05 | Pending — process controls in Sections 2 and 11 to be confirmed | CHANGES_REQUESTED — not yet reviewed |
| Dr. Benny Moog (Learning Technologies) | Scheduled 2026-08-05 | Pending — RIFF chairing arrangement to be agreed | CHANGES_REQUESTED — not yet reviewed |
| Prof. Desmond Key (Music) | Scheduled 2026-08-12 | Pending — discipline exception framing to be confirmed | CHANGES_REQUESTED — not yet reviewed |
| Eleanor Frame (Privacy) | Scheduled 2026-08-12 | Pending | CHANGES_REQUESTED — not yet reviewed |

> All stakeholder reviews are outstanding at v1.0. This document is DRAFT and its influence and resistance assessments are the architect's working judgement from the engagement inputs, not statements the named individuals have endorsed.

### Document Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Project Sponsor | Prof. Otis Hammond, DVC (Education) | | |
| Business Owner | Dr. Benny Moog, Director Learning Technologies | | |
| Enterprise Architect | (Engagement Solution Architect) | | |

---

## Appendices

### Appendix A: Stakeholder Interview Summaries

> Interviews scheduled for the first fortnight of the project. Summaries below record the positions carried forward from the parent engagement's stakeholder register and the week-one prioritisation session [S-C1]; formal interviews will supersede them.

#### Position of record — Cassandra Rhodes (CIO), carried from parent engagement

**Key Points**:

- Favours Microsoft-platform consolidation across collaboration, learning delivery and lecture capture [S-C2]
- A Teams investigation for 2027 was already planned to establish a seamless platform experience [SL-C2]
- Holds the Essential Eight targets and the integration uplift funding [S-C3]

**Quotes**:

- "We are paying twice for a capability that arrives in the licence we already signed." *(position summary, to be confirmed at interview)*

**Follow-up Actions**:

- Confirm the actual Microsoft entitlement position by 2026-08-14 — the argument depends on it being real rather than assumed

---

#### Position of record — Dr. Benny Moog (Director, Learning Technologies), carried from parent engagement

**Key Points**:

- Defends best-of-breed pedagogy tooling against platform consolidation [S-C2]
- Deepest tool knowledge in the institution; runs the RIFF reviews [S-C8]
- Concern is product class, not brand — lecture capture and meeting recording are different categories

**Quotes**:

- "A meeting recorder that can also record a lecture is not a lecture capture platform." *(position summary, to be confirmed at interview)*

**Follow-up Actions**:

- Capability evidence against the eight-category taxonomy by 2026-08-21
- Agree RIFF chairing arrangement with Hammond before the criteria workshop

---

#### Position of record — Prof. Desmond Key (Dean, Music & Performing Arts)

**Key Points**:

- Performance and ensemble capture requires multi-camera and high-fidelity audio (REQ-010) [RR-C5]
- Discipline tooling has been in "investigation required" status without resolution [SL-C5]
- Expects the exception to be endorsed and then defunded

**Quotes**:

- "Every time this comes up we are told the exception is safe, and every time the budget arrives it is not in it." *(position summary, to be confirmed at interview)*

**Follow-up Actions**:

- Venue assessment with Fairlight by 2026-08-28
- Capability standard for performance capture drafted before options analysis

---

### Appendix B: Survey Results

The 2026 academic survey (412 responses across all schools) is the source of the requirements register [RR-C12]. The requirements in this project's scope are:

| ID | Requirement | Category | Priority |
|----|-------------|----------|----------|
| REQ-004 | Record, edit and caption instructional video with a single supported toolchain | Learning Resources | Must |
| REQ-008 | Live online classes with breakout rooms, polling and recording on one primary platform | Learning Delivery | Must |
| REQ-009 | All timetabled lectures captured automatically and published within 4 hours | Learning Capture | Must |
| REQ-010 | Performance and ensemble sessions capturable with multi-camera and high-fidelity audio | Learning Capture | Could |
| REQ-025 | Automated user provisioning for lecture capture — no manual CSV loads | Integration | Must |
| REQ-029 | WCAG 2.2 AA conformance for all student-facing tools | Non-functional | Must |
| REQ-030 | Privacy Act 1988 compliance, AU residency preferred, APP 8 assessed for offshore disclosure | Non-functional | Must |
| REQ-031 | SSO with MFA; no local accounts | Non-functional | Must |
| REQ-032 | 99.9% availability for core teaching platforms during teaching periods | Non-functional | Must |
| REQ-033 | Demonstrable alignment to ASD Essential Eight maturity targets | Non-functional | Must |
| REQ-034 | Data export in open formats on contract termination | Non-functional | Should |
| REQ-035 | Total ecosystem licence spend reduces or holds flat while closing Must-priority gaps | Non-functional | Should |

Response-level breakdown by school and question is not available in the engagement inputs — only the consolidated register. Requests for capture-specific response data should go to Dr. Felix Marimba, custodian of the requirements register [S-C11].

---

### Appendix C: References

- `projects/000-global/ARC-000-PRIN-v1.0.md` — Enterprise Architecture Principles, particularly Principles 1, 2, 3, 4, 9, 12, 14, 15, 16 and 19
- `projects/001-lt-ecosystem/ARC-001-STKE-v1.0.md` — Stakeholder Drivers & Goals Analysis for the parent engagement
- `projects/001-lt-ecosystem/ARC-001-REQ-v1.0.md` — Requirements for the parent engagement
- `projects/001-lt-ecosystem/ARC-001-RISK-v1.0.md` — Risk Register for the parent engagement
- `projects/002-lecture-capture/external/consultant-brief.md` — Engagement brief, WP1–WP9
- `projects/002-lecture-capture/external/system-landscape.md` — System categorisation map and known integrations
- `projects/002-lecture-capture/external/requirements-register.md` — Consolidated academic survey requirements
- `projects/002-lecture-capture/external/privacy-context.md` — Personal information inventory and Essential Eight self-assessment
- `projects/000-global/policies/solution-governance-process.md` — RIFF Review governance process
- `projects/000-global/external/capability-taxonomy.md` — Eight-category L&T capability taxonomy

---

## External References

> This section provides traceability from generated content back to source documents.

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| S | stakeholders.md | Engagement input | `002-lecture-capture/external/` | Stakeholder register with roles, influence and interest ratings, and engagement notes |
| CB | consultant-brief.md | Engagement brief | `002-lecture-capture/external/` | Consultant Engagement Brief — WP1–WP9, scope, dependencies, 31 August 2026 due date |
| RR | requirements-register.md | Requirements input | `002-lecture-capture/external/` | Consolidated academic survey requirements (REQ-001 to REQ-035) |
| PC | privacy-context.md | Compliance input | `002-lecture-capture/external/` | Personal information inventory, data flows, Essential Eight self-assessment |
| SL | system-landscape.md | Foundation artifact | `002-lecture-capture/external/` | System categorisation map, usage status, known integrations |
| SGP | solution-governance-process.md | Foundation artifact | `000-global/policies/` | RIFF Review governance and approval process |
| CT | capability-taxonomy.md | Foundation artifact | `000-global/external/` | Eight-category L&T capability taxonomy |
| PRIN | ARC-000-PRIN-v1.0.md | ArcKit artifact | `000-global/` | Enterprise Architecture Principles (WP1 output) |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| S-C1 | S | Header | Stakeholder Need | "Input for `/arckit:stakeholders` — the engagement stakeholder register. Power/interest analysis, engagement plan and RACI to be generated as governed artifacts." |
| S-C2 | S | Engagement notes | Risk Factor | "Known tension: Rhodes (CIO) favours Microsoft-platform consolidation (Teams/Stream); Moog and Key defend best-of-breed pedagogy tools (Echo360, discipline software). This lands squarely in the WP6 decisions register." |
| S-C3 | S | Executive & governance | Stakeholder Need | "Cassandra 'Cas' Rhodes / Chief Information Officer / Owns Digital & IT; funds integration uplift; Essential Eight targets" |
| S-C4 | S | Project & delivery | Procurement Constraint | "Grace Tanaka / Procurement & Vendor Manager / Contract status data for WP3; vendor roadmap sessions" |
| S-C5 | S | Executive & governance | Stakeholder Need | "Vernon Ostinato / Chief Financial Officer / Business case scrutiny; licence spend optimisation (REQ-035)" |
| S-C6 | S | Executive & governance | Stakeholder Need | "Prof. Otis Hammond / Deputy Vice-Chancellor (Education) / Executive Sponsor; owns the L&T strategy; chairs steering committee" |
| S-C7 | S | Executive & governance | Stakeholder Need | "A/Prof. Pearl Clavinet / Dean of Learning & Teaching; Chair, Education Committee / Academic approval gate; validates WP1 principles" |
| S-C8 | S | Project & delivery | Stakeholder Need | "Dr. Benny Moog / Director, Learning Technologies / Product owner of the L&T ecosystem; deepest tool knowledge; runs RIFF reviews" |
| S-C9 | S | Academic & student representatives | Stakeholder Need | "Dr. Wynton Castle / Senior Lecturer & Blackboard power user / Voice of frontline academics; principles validation workshops" |
| S-C10 | S | Academic & student representatives | Stakeholder Need | "Jazmin Field / President, Student Guild / Student experience consistency (WP1 principle); accessibility advocacy" |
| S-C11 | S | Project & delivery | Stakeholder Need | "Dr. Felix Marimba / Academic Lead, Digital Learning / Owned the academic survey; custodian of the requirements register" |
| CB-C1 | CB | §2, WP6 | Design Decision | "Examples: Echo360 vs Microsoft Stream; Teams scope and provisioning model; integration pattern standards" |
| CB-C2 | CB | §2, WP9 | Business Requirement | "Synthesises all findings into prioritised recommendations and a sequenced delivery roadmap, structured to feed directly into the September business case." |
| RR-C1 | RR | Functional requirements | Functional Requirement | "REQ-010 — Performance and ensemble sessions shall be capturable with multi-camera and high-fidelity audio options" |
| RR-C2 | RR | Non-functional requirements | Non-Functional Requirement | "REQ-032 — Core teaching platforms (LMS, capture, video conferencing) shall meet 99.9% availability during teaching periods" |
| RR-C3 | RR | Non-functional requirements | Non-Functional Requirement | "REQ-035 — Total ecosystem licence spend shall reduce or hold flat while closing Must-priority capability gaps" |
| RR-C4 | RR | Integration / Non-functional | Integration Requirement | "REQ-025 — User provisioning for lecture capture, portfolio and assessment platforms shall be automated — no manual CSV loads"; "REQ-031 — Authentication to all L&T platforms shall use university single sign-on with MFA; no local accounts" |
| RR-C5 | RR | Functional requirements | Functional Requirement | "REQ-010 ... Learning Capture / Could / SURVEY" |
| RR-C6 | RR | Functional requirements | Functional Requirement | "REQ-009 — All timetabled lectures shall be captured automatically and published to the relevant unit site within 4 hours" |
| RR-C7 | RR | Non-functional requirements | Compliance Constraint | "REQ-029 — All student-facing tools shall conform to WCAG 2.2 AA accessibility"; "REQ-030 — All platforms holding personal information shall comply with the Privacy Act 1988 (APPs)" |
| RR-C8 | RR | Header | Procurement Constraint | "MoSCoW priorities were assigned by the project team with the Education Committee." |
| RR-C9 | RR | Functional requirements | Functional Requirement | "REQ-009 ... Learning Capture / Must / SURVEY" |
| RR-C10 | RR | Non-functional requirements | Procurement Constraint | "REQ-034 — Vendor contracts shall permit export of all university data in open formats on termination" |
| RR-C11 | RR | Non-functional requirements | Security Requirement | "REQ-033 — The ecosystem shall demonstrate alignment to the ASD Essential Eight maturity targets set by Digital & IT" |
| RR-C12 | RR | Header | Business Requirement | "Consolidated requirements from the 2026 academic survey (412 responses across all schools)." |
| PC-C1 | PC | §3 | Security Requirement | "Patch operating systems / ML1 / ML2 / Lecture-theatre capture appliances behind" |
| PC-C2 | PC | §1, class 4 | Data Requirement | "Video/audio recordings capturing students / PI (biometric-adjacent) / Echo360, Zoom, MS Teams / AU / US" |
| PC-C3 | PC | Header | Compliance Constraint | "Feeds the `arckit-au` overlay commands: Privacy Impact Assessment (Privacy Act 1988, 13 APPs, APP 8 cross-border disclosure ...), Essential Eight maturity posture (ML0–ML3)" |
| PC-C4 | PC | §3 | Security Requirement | "Restrict administrative privileges / ML1 / ML2 / Legacy shared admin accounts in AV/capture estate" |
| PC-C5 | PC | §3 | Security Requirement | "Target set by Digital & IT: ML2 across the SaaS-heavy L&T estate by end 2027." |
| PC-C6 | PC | §3 | Security Requirement | "Multi-factor authentication / ML2 / ML2 / SSO+MFA enforced; exception: two tools still allow local accounts (breaches REQ-031)" |
| PC-C7 | PC | §1, APP 8 note | Compliance Constraint | "APP 8 triggers: classes 3, 4 (partial), 6 and 7 involve offshore disclosure under the assumed hosting — the PIA must assess cross-border disclosure accountability, contract clauses and the practicability of AU-region alternatives." |
| PC-C8 | PC | §2 | Data Requirement | "Analytics export / Derived engagement data / Ad-hoc extracts / No defined retention or minimisation rules" |
| SL-C1 | SL | Categorisation map | Design Decision | "Learning Capture / Echo360 ✅ · MS Teams ✅¹ · Zoom ✅ / —" |
| SL-C2 | SL | Notes, item 1 | Design Decision | "MS Teams — investigation planned for 2027 to establish a seamless platform experience across collaboration, learning delivery and lecture capture (overlaps with Zoom and Echo360 — key rationalisation candidate)." |
| SL-C3 | SL | Categorisation map | Functional Requirement | "Evaluation & Analytics / Blackboard ✅ · Qualtrics ✅ · Evasys ✅ · Echo360 ✅" |
| SL-C4 | SL | Known integrations, #2 | Integration Requirement | "Echo360 user provisioning / LTI + manual CSV / Manual workaround for casual academic staff" |
| SL-C5 | SL | Notes, item 5 | Risk Factor | "MuseScore / Ableton Live — School of Music & Performing Arts discipline tools; investigation required to determine the extent and nature of current use and licensing across the school." |
| SL-C6 | SL | Categorisation map | Functional Requirement | "Learning Resources ... Discipline-specific: MuseScore ✅ · Ableton Live 🔑 · iSimulate ✅ · Kuracloud ✅" |
| SGP-C1 | SGP | Header | Compliance Constraint | "The central gate is the RIFF Review — Review of Innovation, Fit & Function — which assesses solution requests for architectural fit, capability duplication, integration impact and total cost before any procurement or build proceeds." |
| SGP-C2 | SGP | Rules | Procurement Constraint | "Solutions duplicating capability already licensed (per the system landscape map) must justify why the incumbent tool is unsuitable." |
| SGP-C3 | SGP | Rules | Procurement Constraint | "A request may be paused or closed without progressing further, with the agreement of key consulting stakeholders, if it is deemed not to be required." |
| SGP-C4 | SGP | Roles | Compliance Constraint | "Education Committee — Academic approval of solution requests"; "Operations Committee / University Executive — Financial and strategic approval where thresholds are exceeded" |
| CT-C1 | CT | Taxonomy table | Design Decision | "Eight capability categories define the learning & teaching technology ecosystem. Every current and proposed tool is categorised against this taxonomy to enable cross-system comparison, duplication analysis and rationalisation decisions." |
| PRIN-C1 | PRIN | Executive Summary | Design Decision | "This document establishes the principles governing all technology architecture decisions at The University of Funk ... every project initialised after this document inherits these principles." |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| README.md | `002-lecture-capture/external/` | ArcKit scaffold guidance for the external documents directory; contains no project content |

---

**Generated by**: ArcKit `/arckit:stakeholders` command
**Generated on**: 2026-07-27
**ArcKit Version**: 6.7.2
**Project**: Lecture Capture Platform Consolidation (Project 002)
**Model**: Claude Opus 5 (1M context)

<!-- arckit-provenance:start -->

## Build Provenance

_Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix._

| Field | Value |
|-------|-------|
| Requested Effort | `high` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-07-28T04:26:55.186Z |

<!-- arckit-provenance:end -->
