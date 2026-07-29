# Stakeholder Drivers & Goals Analysis: Integration Platform Selection & Implementation

> **Template Origin**: Official | **ArcKit Version**: 6.7.4 | **Command**: `/arckit:stakeholders`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-004-STKE-v1.0 |
| **Document Type** | Stakeholder Drivers & Goals Analysis |
| **Project** | 004-integration-platform — Integration Platform Selection & Implementation |
| **Classification** | OFFICIAL-SENSITIVE |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-29 |
| **Last Modified** | 2026-07-29 |
| **Review Cycle** | Fortnightly during project |
| **Next Review Date** | 2026-08-12 |
| **Owner** | Sam Okafor, Integration Architect |
| **Reviewed By** | Cassandra Rhodes, Chief Information Officer |
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

This document identifies the stakeholders of the Integration Platform Selection & Implementation project (Project 004), their underlying drivers, how those drivers convert into measurable goals, and the outcomes that will demonstrate satisfaction. Project 004 exists to resolve a single, consequential condition from ADR-001: Condition 1 — the Principle 19 test. It determines whether existing licensed capability can serve as the event broker before any new purchase is made.

### Key Findings

This is a narrower, more technical project than either the L&T Baseline Strategy (Project 001) or the Ultra Migration (Project 003). The stakeholder set is correspondingly smaller — eight internal stakeholders and four external parties — and the central tension is a three-way disagreement about what "existing licensed capability" means and how hard one must try before declaring it insufficient.

The fault line is not philosophical. It is practical:

1. **Build versus buy versus already-bought**: Okafor (Integration Architect) wants a platform he can build on and sustain — and may favour open-source for control. Rhodes (CIO) wants Principle 19 satisfied quickly, and the Microsoft agreement is the path of least resistance. Ostinato (CFO) wants whichever option avoids a new line item. These three positions are not incompatible in principle, but they lead to different evaluation criteria and different definitions of "genuinely suitable."
2. **Speed versus thoroughness**: Hammond (DVC-E) needs the broker selected and operational before P003 Phase 1 can begin INT-001. But the Principle 19 test requires genuine evaluation of existing capability — PeopleSoft Integration Broker, Ultra webhooks, Microsoft Service Bus — not a perfunctory assessment designed to reach a predetermined conclusion.
3. **Capability versus operational burden**: A full-featured broker (Apache Kafka, Azure Service Bus) provides schema registry, replay, and observability out of the box but demands operational expertise Okafor's team does not currently hold. A lightweight broker (RabbitMQ, NATS) is simpler to operate but may lack the schema registry that ADR-001 requires for runtime enforcement of the canonical model.

### Critical Success Factors

- **CSF-1** — The Principle 19 test is genuine: existing licensed capability is evaluated honestly, with documented criteria and a defensible conclusion — not a rubber stamp for a preferred outcome.
- **CSF-2** — The selected broker is operational with a functioning schema registry before P003 Phase 1 requires INT-001 to be built.
- **CSF-3** — The canonical data model (ARC-001-DATA-v1.0) is deployed as a runtime schema, not merely documented alongside the broker.
- **CSF-4** — Okafor's team can operate the selected platform within 90 days of deployment, with or without vendor dependency.

### Stakeholder Alignment Score

**Overall Alignment**: MEDIUM-HIGH

Alignment on the *need* for a broker is settled — ADR-001 resolved that question. The remaining disagreement is about *which* broker, and that disagreement is healthy: it reflects genuinely different weightings of cost, control, capability, and operational sustainability. No stakeholder opposes the project. The risk is not conflict but convergence on expediency — selecting the easiest option rather than the right one.

---

## Stakeholder Identification

### Internal Stakeholders

| Stakeholder | Role/Department | Influence | Interest | Engagement Strategy |
|-------------|----------------|-----------|----------|---------------------|
| Sam Okafor | Integration Architect, Digital & IT | HIGH | HIGH | Manage Closely — primary evaluator, future operator |
| Cassandra "Cas" Rhodes | Chief Information Officer | HIGH | HIGH | Manage Closely — funds it, owns Principle 19 |
| Dr. Benny Moog | Director, Learning Technologies | MEDIUM | HIGH | Manage Closely — consumes integration outputs |
| Prof. Otis Hammond | Deputy Vice-Chancellor (Education) — Executive Sponsor | HIGH | LOW | Keep Satisfied — approves funding, does not engage with broker detail |
| Vernon Ostinato | Chief Financial Officer | HIGH | LOW | Keep Satisfied — the Principle 19 test is literally his requirement |
| Tobias Ohm | Cybersecurity Lead | MEDIUM | HIGH | Keep Informed — broker security posture, E8 alignment |
| Eleanor Frame | Privacy & Records Officer | MEDIUM | HIGH | Keep Informed — PI flows through the broker, hosting region |
| Grace Tanaka | Procurement & Vendor Manager | MEDIUM | MEDIUM | Keep Informed — contract and licensing terms if new purchase |

### External Stakeholders

| Stakeholder | Organization | Relationship | Influence | Interest |
|-------------|--------------|--------------|-----------|----------|
| Microsoft | Existing agreement holder | Supplier — Azure Integration Services, Service Bus | MEDIUM | HIGH |
| Anthology (Blackboard) | LMS vendor | Supplier — Ultra webhook/event capabilities | MEDIUM | MEDIUM |
| Oracle (PeopleSoft) | SIS vendor | Supplier — PeopleSoft Integration Broker | MEDIUM | LOW |
| Open-source community | Apache Kafka, RabbitMQ, NATS, etc. | Community — if open-source is selected | LOW | LOW |

### Governance Framework Applicability

The template's UK Government roles (GovS 005, GovS 007) are **not applicable** — The University of Funk is an Australian university. Governance follows the RIFF Review -> Education Committee -> Operations Committee -> University Executive pathway. The applicable regulatory overlay is the Privacy Act 1988 and the ASD Essential Eight, carried by Eleanor Frame and Tobias Ohm respectively.

### Stakeholder Power-Interest Grid

```text
                              INTEREST
              Low                              High
        +--------------------------+--------------------------+
        |                          |                          |
        |     KEEP SATISFIED       |     MANAGE CLOSELY       |
        |                          |                          |
   High |  * Hammond (DVC-E)       |  * Okafor (Integration)  |
        |  * Ostinato (CFO)        |  * Rhodes (CIO)          |
        |                          |                          |
 P      |                          |                          |
 O      +--------------------------+--------------------------+
 W      |                          |                          |
 E      |        MONITOR           |      KEEP INFORMED       |
 R      |                          |                          |
        |  * Oracle (PeopleSoft)   |  * Moog (Learning Tech)  |
   Low  |  * Open-source community |  * Ohm (Cybersecurity)   |
        |                          |  * Frame (Privacy)       |
        |                          |  * Tanaka (Procurement)  |
        |                          |  * Microsoft             |
        |                          |  * Anthology             |
        +--------------------------+--------------------------+

   Note: Moog sits on the Manage Closely / Keep Informed boundary.
   He has MEDIUM formal power but HIGH interest as the primary
   consumer of integration outputs. Classified Manage Closely
   for engagement purposes; his engagement is consumption-focused,
   not design-focused.
```

| Stakeholder | Power | Interest | Quadrant | Engagement Strategy |
|-------------|-------|----------|----------|---------------------|
| Sam Okafor | HIGH | HIGH | Manage Closely | Weekly working sessions; leads evaluation |
| Cassandra Rhodes | HIGH | HIGH | Manage Closely | Fortnightly steering; Principle 19 sign-off |
| Dr. Benny Moog | MEDIUM | HIGH | Manage Closely | Fortnightly; validates integration outputs work |
| Prof. Otis Hammond | HIGH | LOW | Keep Satisfied | Milestone briefings; funding approval |
| Vernon Ostinato | HIGH | LOW | Keep Satisfied | Cost checkpoint at selection decision |
| Tobias Ohm | MEDIUM | HIGH | Keep Informed | Security architecture review of shortlisted options |
| Eleanor Frame | MEDIUM | HIGH | Keep Informed | Hosting region and PI flow assessment |
| Grace Tanaka | MEDIUM | MEDIUM | Keep Informed | Contract review if new purchase |
| Microsoft | MEDIUM | HIGH | Keep Informed | Capability demonstration; licensing terms |
| Anthology | MEDIUM | MEDIUM | Keep Informed | Ultra webhook capability assessment |
| Oracle | MEDIUM | LOW | Monitor | PeopleSoft Integration Broker capability review |
| Open-source community | LOW | LOW | Monitor | No engagement unless open-source shortlisted |

**Quadrant Interpretation:**

- **Manage Closely** (High Power, High Interest): Key decision-makers requiring active engagement
- **Keep Satisfied** (High Power, Low Interest): Influential stakeholders needing periodic updates
- **Keep Informed** (Low Power, High Interest): Engaged stakeholders needing regular communication
- **Monitor** (Low Power, Low Interest): Minimal engagement required

---

## Stakeholder Drivers Analysis

### SD-1: Sam Okafor (Integration Architect) — A platform I can build on and sustain

**Stakeholder**: Sam Okafor, Integration Architect, Digital & IT

**Driver Category**: OPERATIONAL / PERSONAL

**Driver Statement**: Needs the integration broker to be a platform he can build on for years — not an underpowered message queue that requires manual workarounds, and not an overpowered enterprise platform that creates operational burden his team cannot carry.

**Context & Background**: Okafor co-designed the integration architecture in WP5 and will operate whatever this project selects. He knows his team's capacity intimately: three people including himself, none with enterprise middleware experience. He wants control — the ability to understand, debug, and extend the platform without calling a vendor. This inclines him toward open-source. But he is also honest about the skills gap: standing up and operating Apache Kafka with a schema registry is not a weekend project, and he has seen other teams try and struggle.

**Driver Intensity**: CRITICAL

**Enablers**:

- Selection criteria that weight operational sustainability, not just feature count
- His technical assessment carrying genuine authority in the decision — not overruled by commercial convenience
- Skills uplift plan that is funded and sequenced before go-live, not deferred as an afterthought

**Blockers**:

- A platform selected for commercial reasons (Microsoft agreement) that he cannot operate independently
- An evaluation that treats his operational concerns as resistance rather than expertise
- Open-source selected without acknowledging the skills investment required

**Related Stakeholders**: Rhodes (his CIO; may favour Microsoft), Ostinato (cost constraint), Ohm (security requirements affect platform choice)

---

### SD-2: Cassandra Rhodes (CIO) — Principle 19 satisfied before any new spend

**Stakeholder**: Cassandra "Cas" Rhodes, Chief Information Officer

**Driver Category**: FINANCIAL / GOVERNANCE

**Driver Statement**: Needs the Principle 19 evaluation completed credibly and quickly — demonstrating that existing licensed capability was genuinely tested before any new purchase is considered.

**Context & Background**: Principle 19 is Rhodes's principle. She proposed it, she championed it at the RIFF Review, and ADR-001 Condition 1 cites it as a precondition for broker procurement. The university already pays for a Microsoft enterprise agreement that includes Azure Service Bus and Azure Integration Services. If that capability can serve, the Principle 19 test is trivially satisfied and the CFO is happy. If it cannot, Rhodes needs a documented, defensible explanation of why not — because the alternative is a new line item that her own principle says should not exist without that test.

**Driver Intensity**: CRITICAL

**Enablers**:

- Microsoft agreement terms clarified promptly — what is included, what requires incremental licensing
- Evaluation criteria published before testing begins, so the conclusion is defensible
- A quick, clean outcome: either existing capability works, or it demonstrably does not

**Blockers**:

- Evaluation that treats the Principle 19 test as a formality while pursuing a preferred alternative
- Microsoft licensing terms that are ambiguous or require protracted clarification
- Open-source advocacy from Okafor that bypasses the existing-capability evaluation

**Related Stakeholders**: Okafor (may favour open-source), Ostinato (wants the cheapest), Tanaka (contract terms), Hammond (timeline pressure)

---

### SD-3: Dr. Benny Moog (Director, Learning Technologies) — Integration that is invisible to academics

**Stakeholder**: Dr. Benny Moog, Director, Learning Technologies

**Driver Category**: OPERATIONAL

**Driver Statement**: Wants the integration broker to be infrastructure that simply works — enrolments arrive, grades flow, provisioning happens — without adding another platform to his team's awareness or another dashboard to his morning.

**Context & Background**: Moog does not care which broker is selected. He cares deeply that it works. His team consumes integration outputs — they do not operate infrastructure. Every platform added to the estate is a platform his team must understand when things break, and he is already carrying the Ultra migration. The broker should be as invisible to Learning Technologies as the network switches are: a thing that exists, that works, and that someone else worries about.

**Driver Intensity**: HIGH

**Enablers**:

- A broker that operates without Learning Technologies involvement
- Clear operational boundary: Okafor's team owns the broker; Moog's team owns the platforms that connect to it
- Reliability that means Moog never has to diagnose an integration failure that turns out to be a broker issue

**Blockers**:

- A broker that requires Learning Technologies staff to learn a new console or monitoring tool
- Reliability issues that surface as "the LMS is broken" when it is actually the broker
- Operational ownership left ambiguous between Digital & IT and Learning Technologies

**Related Stakeholders**: Okafor (operational boundary), Rhodes (funding), Castle and academic staff (downstream impact of broker failures)

---

### SD-4: Vernon Ostinato (CFO) — No new spend unless existing capability is genuinely unsuitable

**Stakeholder**: Vernon Ostinato, Chief Financial Officer

**Driver Category**: FINANCIAL

**Driver Statement**: Requires the Principle 19 test to be completed genuinely — not as a box-ticking exercise. If existing licensed capability can serve, it must. If it cannot, the business case for new spend must quantify the offset.

**Context & Background**: Ostinato approved the L&T Baseline Strategy on the basis of flat or reducing spend. A new integration platform is a new line item. The Microsoft agreement is already paid for. PeopleSoft Integration Broker is already licensed. If either can serve, a new purchase is unjustifiable in Ostinato's terms. His engagement is LOW day-to-day but HIGH at the decision gate — he will scrutinise the evaluation outcome sharply, and he will ask whether the test was genuine or whether the conclusion was written first.

**Driver Intensity**: HIGH

**Enablers**:

- Evaluation report that quantifies cost for each option — including the hidden cost of operating open-source
- Microsoft agreement terms confirmed: what is included at no incremental cost versus what requires additional licensing
- Total cost of ownership comparison, not just licence cost

**Blockers**:

- Evaluation that dismisses existing capability on technical grounds the CFO cannot assess
- Open-source presented as "free" without operational cost
- Microsoft capability rejected without a credible written explanation

**Related Stakeholders**: Rhodes (Principle 19 owner), Tanaka (contract terms), Hammond (programme budget)

---

### SD-5: Tobias Ohm (Cybersecurity Lead) — Broker meets E8 and credential security standards

**Stakeholder**: Tobias Ohm, Cybersecurity Lead

**Driver Category**: COMPLIANCE

**Driver Statement**: Needs the integration broker to meet Essential Eight ML2 requirements and to centralise credential management — service-to-service authentication using OAuth 2.0 or scoped service credentials, not shared secrets or embedded passwords.

**Context & Background**: The broker becomes the credential nexus for every integration in the estate. Every system-to-system connection passes through it. If the broker uses shared secrets, the entire integration estate inherits that weakness. If the broker supports OAuth 2.0 with scoped service accounts, every integration benefits. Ohm's requirements are non-negotiable: they are the ML2 target Rhodes has committed to, and they apply to the broker as to any platform.

**Driver Intensity**: HIGH

**Enablers**:

- Security posture as a weighted evaluation criterion, not an afterthought
- Broker supporting OAuth 2.0 / service principal authentication natively
- Audit logging of all credential usage and access
- Australian-region hosting or assessed cross-border position

**Blockers**:

- Open-source broker deployed without hardening or security review
- Credential management deferred to "after go-live"
- Broker selected before security architecture review

**Related Stakeholders**: Rhodes (E8 target owner), Okafor (implements security configuration), Frame (overlapping compliance)

---

### SD-6: Eleanor Frame (Privacy & Records Officer) — PI flows through a governed, auditable channel

**Stakeholder**: Eleanor Frame, Privacy & Records Officer

**Driver Category**: COMPLIANCE

**Driver Statement**: Needs the integration broker to provide audit logging, access control, and governed data flows for every integration carrying personal information — and needs the broker hosted in Australia or the cross-border position formally assessed.

**Context & Background**: Every integration in the canonical model carries personal information — student identity, enrolment, role assignment, placement grades. The broker is the single channel through which all of it flows. This is simultaneously the strongest privacy argument for a central broker (one channel to govern, not nine) and the strongest privacy risk (one channel to compromise, not nine). Frame needs hosting region confirmed, access logging verifiable, and retention within the broker bounded and documented.

**Driver Intensity**: HIGH

**Enablers**:

- Hosting region confirmed as part of the evaluation, not discovered after selection
- Audit logging as a mandatory evaluation criterion
- Broker retention policy defined — events retained for replay, not accumulated indefinitely
- APP 8 cross-border assessment completed for any non-Australian option

**Blockers**:

- Cloud-hosted broker in a region that triggers APP 8 without assessment
- Audit logging absent or optional in the selected platform
- Privacy assessment sequenced after broker selection

**Related Stakeholders**: Ohm (overlapping security), Okafor (broker configuration), Tanaka (contract clauses for cloud hosting)

---

### SD-7: Prof. Otis Hammond (DVC-E) — This decision does not delay Project 003

**Stakeholder**: Prof. Otis Hammond, Deputy Vice-Chancellor (Education); Executive Sponsor

**Driver Category**: STRATEGIC

**Driver Statement**: Needs the broker selected and operational quickly enough that the Ultra migration (P003) is not delayed — specifically, that INT-001 (PeopleSoft -> Ultra lifecycle integration) can begin on the selected broker.

**Context & Background**: Hammond approved the L&T strategy and chairs the steering committee. He does not engage with broker selection detail — the difference between Kafka and RabbitMQ is not his concern. His concern is that a protracted selection process delays INT-001, which delays P003 Phase 1, which delays the Ultra migration, which delays the entire programme. He expects this decision to be made quickly and cleanly, and he will be impatient with evaluation processes that feel academic.

**Driver Intensity**: HIGH

**Enablers**:

- Evaluation timeboxed with a clear decision deadline
- Existing-capability testing conducted in parallel rather than sequentially
- Decision criteria agreed before evaluation begins, not negotiated during it

**Blockers**:

- Principle 19 test expanded into a multi-month evaluation programme
- Stakeholder disagreement on evaluation criteria delaying the start
- Selected broker requiring months of setup before INT-001 can begin

**Related Stakeholders**: Rhodes (Principle 19 tension with speed), Okafor (delivery timeline), Moog (P003 dependency)

---

### SD-8: Grace Tanaka (Procurement & Vendor Manager) — Commercial terms that don't create lock-in

**Stakeholder**: Grace Tanaka, Procurement & Vendor Manager

**Driver Category**: FINANCIAL / OPERATIONAL

**Driver Statement**: Needs any new commercial arrangement to use open protocols and provide data portability — Principle 9 applies to the broker as to any platform.

**Context & Background**: If the Principle 19 test concludes that a new purchase is required, Tanaka manages the procurement. If the Microsoft agreement is used, Tanaka needs to confirm the terms cover the intended use. Either way, she needs the commercial arrangement to avoid creating a dependency that constrains future decisions. Open protocols (AMQP, CloudEvents, OpenAPI-described schemas) are the contractual equivalent of data export provisions.

**Driver Intensity**: MEDIUM

**Enablers**:

- Open protocol support as an evaluation criterion
- Microsoft agreement terms confirmed early — no ambiguity about what is included
- Exit provisions and data portability assessed for any commercial option

**Blockers**:

- Proprietary messaging protocol that creates broker lock-in
- Microsoft licensing terms that are unclear or require legal interpretation
- Procurement timeline misaligned with the project decision deadline

**Related Stakeholders**: Ostinato (cost), Rhodes (strategy), Microsoft (counterparty)

---

### SD-9: Sam Okafor (Integration Architect) — Canonical model enforced at runtime

**Stakeholder**: Sam Okafor, Integration Architect, Digital & IT

**Driver Category**: OPERATIONAL / STRATEGIC

**Driver Statement**: Needs the broker to provide a schema registry that validates events against the canonical data model at runtime — rejecting non-conformant messages rather than silently accepting them.

**Context & Background**: This is the defining requirement from ADR-001. The entire point of selecting a central broker over point-to-point was runtime enforcement of the canonical model. A broker that cannot validate events against ARC-001-DATA-v1.0's entity definitions (PERSON, UNIT, ENROLMENT, INSTITUTIONAL_ROLE_ASSIGNMENT) is a message pipe, not a mediation layer. It would deliver Option A's architecture (point-to-point) with Option B's cost — the worst of both.

**Driver Intensity**: CRITICAL

**Enablers**:

- Schema registry as a mandatory evaluation criterion, not a nice-to-have
- Canonical model published in a schema format the registry can consume (Avro, JSON Schema, Protobuf)
- Schema versioning and compatibility enforcement from day one

**Blockers**:

- Broker selected for cost or convenience that lacks schema registry capability
- Schema registry deferred as "Phase 2" and never delivered
- Existing licensed capability (PeopleSoft Integration Broker, Ultra webhooks) evaluated as "sufficient" despite lacking schema enforcement

**Related Stakeholders**: Rhodes (Principle 19 tension — existing capability may lack this), Moog (benefits from runtime enforcement), Ohm (schema validation is also a security control)

---

### SD-10: Cassandra Rhodes (CIO) — Skills the team can acquire, not a perpetual vendor dependency

**Stakeholder**: Cassandra "Cas" Rhodes, Chief Information Officer

**Driver Category**: OPERATIONAL / STRATEGIC

**Driver Statement**: Wants the selected broker to be something her team can learn to operate independently — not a managed service that solves the skills problem by creating a vendor dependency.

**Context & Background**: A managed iPaaS (Azure Integration Services, MuleSoft) solves the operational skills gap immediately but makes the university dependent on vendor capability, pricing, and roadmap. Open-source solves the dependency problem but requires skills the team does not currently have. Rhodes is looking for a position between these poles: a platform with a learning curve her team can climb, community support they can access, and an operating model that does not require a vendor on speed-dial.

**Driver Intensity**: MEDIUM

**Enablers**:

- Skills uplift plan as a deliverable of this project, not a separate initiative
- Community size and documentation quality as evaluation criteria
- Managed service acceptable as a starting position if a self-managed exit path exists

**Blockers**:

- Managed service selected with no plan to internalise operations
- Open-source selected with no budget for training
- Skills gap treated as a reason to defer rather than a thing to close

**Related Stakeholders**: Okafor (the one who needs the skills), Ostinato (training cost), Hammond (timeline pressure may compress training)

---

## Driver-to-Goal Mapping

### Goal G-1: Principle 19 test completed — existing licensed capability evaluated and outcome documented

**Derived From Drivers**: SD-2, SD-4

**Goal Owner**: Cassandra Rhodes (accountable), Sam Okafor (responsible for technical evaluation)

**Goal Statement**: Evaluate the integration and event-brokering capability of the existing Microsoft enterprise agreement, PeopleSoft Integration Broker, and Blackboard Ultra webhook/event features against the ADR-001 requirements — and document, in writing, whether each can serve as the event broker with schema registry before any new purchase is considered.

**Why This Matters**: This is ADR-001 Condition 1. The decision to select a central broker was made conditional on this test. Skipping it, or conducting it perfunctorily, undermines the governance framework that produced ADR-001 — and Principle 19 is Rhodes's principle. If it is not applied to her own project, it loses credibility universally.

**Success Metrics**:

- **Primary Metric**: Written evaluation report signed off by Rhodes and Okafor
- **Secondary Metrics**:
  - Each existing capability tested against the same criteria as any new option
  - Evaluation criteria published before testing begins
  - Conclusion defensible to the CFO

**Baseline**: No evaluation performed; ADR-001 Condition 1 outstanding

**Target**: Evaluation complete with a documented, defensible outcome — "existing capability is sufficient" or "existing capability is insufficient because [specific reasons]"

**Measurement Method**: Evaluation report; Principle 19 compliance sign-off

**Dependencies**:

- Microsoft agreement terms confirmed by Tanaka
- PeopleSoft Integration Broker technical documentation accessible to Okafor
- Ultra webhook capability documented by Anthology

**Risks to Achievement**:

- Microsoft agreement terms ambiguous, requiring protracted legal clarification
- Evaluation criteria set to favour a predetermined outcome
- Testing compressed to the point where it cannot be genuine

---

### Goal G-2: Integration broker selected and operational before P003 Phase 1

**Derived From Drivers**: SD-7, SD-1, SD-9

**Goal Owner**: Sam Okafor (delivery), Prof. Otis Hammond (accountable for programme timeline)

**Goal Statement**: Select, deploy, and validate the integration broker — including schema registry — so that INT-001 (PeopleSoft -> Ultra lifecycle integration) can be built on it before P003 Phase 1 commences.

**Why This Matters**: P003 is blocked until the broker is operational. INT-001 is the foundation integration — every other integration depends on users and courses being correct in Ultra. A delay to broker selection delays the entire programme.

**Success Metrics**:

- **Primary Metric**: INT-001 development commenced on the selected broker
- **Secondary Metrics**:
  - Broker deployed in an Australian region (or cross-border position assessed)
  - Schema registry operational with canonical model entities loaded
  - At least one end-to-end test event processed successfully

**Baseline**: No broker deployed; ADR-001 decision proposed but Condition 1 not yet satisfied

**Target**: Broker operational with schema registry; INT-001 development underway

**Measurement Method**: Deployment verification; INT-001 sprint commencement

**Dependencies**:

- G-1 (Principle 19 test) completed
- Hosting region confirmed for the selected option
- Team capacity available for deployment and initial configuration

**Risks to Achievement**:

- Principle 19 test taking longer than expected, compressing deployment time
- Selected broker requiring significant infrastructure setup before it is usable
- Skills gap delaying operational readiness

---

### Goal G-3: Canonical model schema registry operational with runtime validation

**Derived From Drivers**: SD-9, SD-1

**Goal Owner**: Sam Okafor

**Goal Statement**: Deploy the canonical data model (ARC-001-DATA-v1.0) — PERSON, UNIT, TEACHING_PERIOD, UNIT_OFFERING, ENROLMENT, and INSTITUTIONAL_ROLE_ASSIGNMENT — as runtime schemas in the broker's schema registry, with validation enabled so that non-conformant events are rejected.

**Why This Matters**: Runtime schema enforcement is the defining benefit of Option B over Option A in ADR-001. Without it, the broker is a message pipe with the cost of a mediation layer. The canonical model must be a runtime contract, not a documentation artifact.

**Success Metrics**:

- **Primary Metric**: Non-conformant events rejected by the schema registry in testing
- **Secondary Metrics**:
  - All six canonical entities published as versioned schemas
  - Schema compatibility mode configured (backward-compatible by default)
  - Schema change process documented

**Baseline**: Canonical model defined in ARC-001-DATA-v1.0 but not deployed as runtime schemas

**Target**: All entities deployed; validation active; non-conformant events demonstrably rejected

**Measurement Method**: Schema registry deployment; contract test results

**Dependencies**:

- G-2 (broker operational)
- Canonical model published in a format the registry can consume
- Schema format agreed (Avro, JSON Schema, or Protobuf)

**Risks to Achievement**:

- Selected broker's schema registry not supporting the chosen schema format
- Schema registry treated as optional and deferred
- Canonical model entities requiring revision during deployment, creating a dependency on ARC-001-DATA-v1.0 updates

---

### Goal G-4: Security and privacy posture verified for the selected broker

**Derived From Drivers**: SD-5, SD-6

**Goal Owner**: Tobias Ohm (security), Eleanor Frame (privacy)

**Goal Statement**: Verify that the selected broker meets Essential Eight ML2 requirements, uses OAuth 2.0 / service principal authentication for all service-to-service connections, provides audit logging, and is hosted in Australia or has an assessed APP 8 cross-border position.

**Why This Matters**: The broker is the credential nexus and the PI conduit for every integration. A security weakness in the broker is a security weakness in the estate. A privacy gap in the broker is a privacy gap in every data flow.

**Success Metrics**:

- **Primary Metric**: Security architecture review completed and signed off by Ohm
- **Secondary Metrics**:
  - OAuth 2.0 / service principal authentication configured for all connections
  - Audit logging enabled and verified
  - Hosting region confirmed; APP 8 position documented if non-Australian
  - Broker patching included in the managed regime

**Baseline**: No broker deployed; security and privacy posture not assessed

**Target**: Security and privacy sign-off before INT-001 carries production data

**Measurement Method**: Security architecture review document; privacy assessment record

**Dependencies**:

- G-2 (broker deployed)
- Hosting region confirmed during evaluation (G-1)
- Vendor security documentation available for the selected option

**Risks to Achievement**:

- Security review sequenced after INT-001 development begins, creating rework risk
- Cloud-hosted option in a non-Australian region with no practicable alternative
- Open-source broker deployed without security hardening

---

### Goal G-5: Team capability established to operate the selected platform

**Derived From Drivers**: SD-1, SD-10

**Goal Owner**: Cassandra Rhodes (funding), Sam Okafor (delivery)

**Goal Statement**: Ensure Okafor's integration team can deploy, configure, monitor, troubleshoot, and recover the selected broker within 90 days of selection — with documented runbooks, on-call procedures, and at least two team members capable of independent operation.

**Why This Matters**: A broker that only one person can operate reproduces the single-person dependency pattern that ADR-001 was designed to eliminate. Sustainable operations require at least two people who can independently manage the platform, and documented procedures for the scenarios that will occur.

**Success Metrics**:

- **Primary Metric**: Two team members pass an operational readiness assessment
- **Secondary Metrics**:
  - Runbooks documented for deployment, scaling, backup, restore, and failure recovery
  - On-call procedures established
  - Training completed (vendor training, community resources, or self-directed, as appropriate)

**Baseline**: No team member has operational experience with any candidate broker platform

**Target**: Two team members operationally capable; runbooks complete; on-call established

**Measurement Method**: Operational readiness review; runbook audit

**Dependencies**:

- Training budget approved as part of this project
- Selected platform has adequate documentation and community/vendor support
- Time between broker selection and INT-001 production cutover sufficient for skills uplift

**Risks to Achievement**:

- Training budget cut or deferred
- Timeline pressure compressing skills uplift into production delivery
- Platform selected with a steep learning curve and insufficient community resources

---

## Goal-to-Outcome Mapping

### Outcome O-1: A governed integration layer — the canonical model enforced at runtime, observable, auditable

**Supported Goals**: G-2, G-3, G-4

**Outcome Statement**: The university operates a central integration broker that enforces the canonical data model at runtime, provides a single observability plane for all integration flows, and meets the security and privacy standards required for personal information.

**Measurement Details**:

- **KPI**: Canonical schema violations rejected at runtime; integration health visible through a single pane
- **Current Value**: No broker; no schema enforcement; no centralised observability
- **Target Value**: All events validated against canonical schemas; single monitoring dashboard operational; security and privacy sign-off held
- **Measurement Frequency**: Monthly during delivery; quarterly in sustainment
- **Data Source**: Schema registry metrics; broker monitoring; security review records
- **Report Owner**: Sam Okafor

**Business Value**:

- **Financial Impact**: Marginal cost per additional integration falls — new platforms integrate once to the broker, not n times to each consumer
- **Strategic Impact**: ADR-001's architecture proven in production; the canonical model becomes a runtime contract rather than a documentation artifact
- **Operational Impact**: Single observability plane replaces nine separate views; retry, replay, and dead-letter implemented once
- **Customer Impact**: Indirect but consequential — integration reliability means students gain access when enrolled, see grades when recorded, and lose access when withdrawn

**Timeline**:

- **Phase 1 (Months 1-2)**: Principle 19 test completed; broker selected
- **Phase 2 (Months 2-3)**: Broker deployed; schema registry operational; security review completed
- **Phase 3 (Months 3-6)**: INT-001 built and validated on the broker; remaining integrations follow in P003 phases
- **Sustainment (Year 2+)**: New integrations conform to the schema registry by default; schema changes governed

**Stakeholder Benefits**:

- **Okafor**: A platform he designed and can sustain
- **Rhodes**: Principle 19 satisfied; integration architecture operational
- **Moog**: Integration that works without his team worrying about how
- **Ohm and Frame**: Centralised credential and audit position

**Leading Indicators**:

- Principle 19 evaluation completed on schedule
- Schema registry loaded with canonical entities
- INT-001 development commenced on the broker

**Lagging Indicators**:

- Non-conformant events rejected in production (schema enforcement working)
- Integration incident rate trending down from P001 baseline

---

### Outcome O-2: P003 unblocked — INT-001 can begin on the selected broker

**Supported Goals**: G-1, G-2

**Outcome Statement**: The integration broker is selected and operational in time for P003 Phase 1 to commence INT-001 (PeopleSoft -> Ultra lifecycle integration) without delay to the Ultra migration programme.

**Measurement Details**:

- **KPI**: P003 Phase 1 commencement date versus plan
- **Current Value**: P003 Phase 1 blocked pending broker selection
- **Target Value**: P003 Phase 1 commences on plan
- **Measurement Frequency**: Milestone tracking
- **Data Source**: Programme plan; sprint records
- **Report Owner**: Rhonda Bell

**Business Value**:

- **Financial Impact**: Delay cost avoided — each month of P003 delay extends dual-running costs and defers the operational savings the programme promises
- **Strategic Impact**: The programme maintains credibility; subsequent projects (005+) remain fundable
- **Operational Impact**: Okafor's team can focus on building rather than waiting
- **Customer Impact**: Ultra migration proceeds on schedule; students benefit sooner

**Timeline**:

- **Phase 1 (Months 1-2)**: Evaluation and selection
- **Phase 2 (Months 2-3)**: Deployment and validation
- **Phase 3 (Month 3)**: INT-001 commences on the broker

**Stakeholder Benefits**:

- **Hammond**: Programme timeline protected
- **Rhodes**: Integration investment delivering on schedule
- **Okafor**: Building rather than waiting
- **Moog**: Ultra migration not delayed by infrastructure decisions

**Leading Indicators**:

- Evaluation report delivered on schedule
- Broker deployment completed without blocking issues

**Lagging Indicators**:

- P003 Phase 1 start date achieved

---

### Outcome O-3: Sustainable operations — Okafor's team can run and maintain the broker without perpetual vendor dependency

**Supported Goals**: G-5, G-1

**Outcome Statement**: The integration team operates the selected broker independently, with documented procedures, at least two capable operators, and no reliance on vendor professional services for routine operations.

**Measurement Details**:

- **KPI**: Vendor support tickets for routine operations; team members capable of independent operation
- **Current Value**: No broker; no operational capability
- **Target Value**: Zero vendor tickets for routine operations; two or more capable operators; runbooks complete
- **Measurement Frequency**: Monthly
- **Data Source**: Vendor support log; operational readiness review; runbook register
- **Report Owner**: Sam Okafor

**Business Value**:

- **Financial Impact**: Ongoing vendor professional services cost avoided
- **Strategic Impact**: The team builds institutional capability, not vendor dependency
- **Operational Impact**: Issues resolved internally within the team's SLA, not waiting for vendor response
- **Customer Impact**: Faster incident resolution; integration reliability maintained

**Timeline**:

- **Phase 1 (Months 1-2)**: Skills gap assessment; training plan
- **Phase 2 (Months 2-4)**: Training delivery; supervised operation during INT-001 development
- **Phase 3 (Months 4-6)**: Independent operation; runbooks validated through use
- **Sustainment (Year 2+)**: Skills maintained through practice; new team members onboarded from runbooks

**Stakeholder Benefits**:

- **Okafor**: He and his team own the platform, not a vendor
- **Rhodes**: Institutional capability built, not rented
- **Ostinato**: Ongoing vendor dependency cost avoided
- **Moog**: Integration support does not depend on a vendor's response time

**Leading Indicators**:

- Training completed; operational readiness assessment passed
- Runbooks documented and reviewed

**Lagging Indicators**:

- Vendor support tickets for routine operations (target: zero)
- Team member attrition not causing single-person dependency recurrence

---

## Complete Traceability Matrix

### Stakeholder -> Driver -> Goal -> Outcome

| Stakeholder | Driver ID | Driver Summary | Goal ID | Goal Summary | Outcome ID | Outcome Summary |
|-------------|-----------|----------------|---------|--------------|------------|-----------------|
| Okafor (Integration) | SD-1 | Platform I can build on | G-2 | Broker operational before P003 | O-1 | Governed integration layer |
| Okafor (Integration) | SD-1 | Platform I can build on | G-5 | Team capability established | O-3 | Sustainable operations |
| Rhodes (CIO) | SD-2 | Principle 19 satisfied | G-1 | Principle 19 test completed | O-2 | P003 unblocked |
| Moog (Learning Tech) | SD-3 | Integration invisible to academics | G-2 | Broker operational before P003 | O-1 | Governed integration layer |
| Ostinato (CFO) | SD-4 | No new spend unless necessary | G-1 | Principle 19 test completed | O-2 | P003 unblocked |
| Ohm (Cybersecurity) | SD-5 | E8 and credential security | G-4 | Security posture verified | O-1 | Governed integration layer |
| Frame (Privacy) | SD-6 | PI through governed channel | G-4 | Privacy posture verified | O-1 | Governed integration layer |
| Hammond (DVC-E) | SD-7 | No delay to P003 | G-2 | Broker operational before P003 | O-2 | P003 unblocked |
| Tanaka (Procurement) | SD-8 | No lock-in | G-1 | Principle 19 test completed | O-3 | Sustainable operations |
| Okafor (Integration) | SD-9 | Canonical model enforced at runtime | G-3 | Schema registry operational | O-1 | Governed integration layer |
| Rhodes (CIO) | SD-10 | Skills team can acquire | G-5 | Team capability established | O-3 | Sustainable operations |

### Conflict Analysis

**Competing Drivers**:

- **Conflict 1 — Build versus buy versus already-bought** (SD-1 versus SD-2 versus SD-4). Okafor may favour open-source for control and sustainability; Rhodes may favour Microsoft because the agreement already exists and Principle 19 is her principle; Ostinato wants whichever avoids a new line item. These positions converge if the Microsoft capability is genuinely suitable and Okafor can operate it — and diverge sharply if it is not.
  - **Resolution Strategy**: Publish evaluation criteria before testing begins, weighting operational sustainability (SD-1), schema registry capability (SD-9), security posture (SD-5), and total cost of ownership (SD-4) equally alongside Principle 19 compliance (SD-2). Test existing capability first — that is what the principle requires — but against the same criteria any new option would face. If existing capability passes, the conflict dissolves. If it fails, the documented failure gives Rhodes and Ostinato a defensible justification for new spend.

- **Conflict 2 — Speed versus thoroughness** (SD-7 versus SD-2/SD-4). Hammond needs the broker selected quickly to unblock P003. The Principle 19 test requires genuine evaluation — testing PeopleSoft Integration Broker, Ultra webhooks, and Microsoft capability against the ADR-001 requirements. These are in tension only if the evaluation is unbounded.
  - **Resolution Strategy**: Timebox the evaluation at four weeks. Test all three existing capabilities in parallel, not sequentially. Publish a pass/fail matrix against the published criteria. If none passes, move immediately to new-option evaluation with the same criteria and a two-week selection window. Hammond gets a six-week decision; Rhodes gets a genuine test; Ostinato gets a defensible conclusion.

- **Conflict 3 — Capability versus operational burden** (SD-9 versus SD-1/SD-10). A full-featured broker with schema registry (Confluent Kafka, Azure Service Bus with Schema Registry) satisfies SD-9 but may exceed Okafor's team's operational capability. A lightweight broker (RabbitMQ, NATS) is easier to operate but may lack schema registry entirely, failing the defining requirement.
  - **Resolution Strategy**: Schema registry is non-negotiable — it is the reason ADR-001 selected Option B. The question is whether the registry must be built into the broker or can be a sidecar (e.g., Apicurio Registry alongside RabbitMQ). Evaluate both configurations. If a lightweight broker plus schema registry sidecar meets the criteria and is operationally sustainable, it resolves the tension. If not, the skills uplift plan (G-5) must be funded and sequenced to close the gap.

**Synergies**:

- **Synergy 1**: Okafor (SD-1, SD-9) and Rhodes (SD-2) both want the evaluation to be genuine. Their disagreement is about the likely conclusion, not the process. A well-structured evaluation with published criteria satisfies both — whoever's preferred option wins does so on evidence.
- **Synergy 2**: Ohm (SD-5) and Frame (SD-6) both benefit from centralisation. A single broker with centralised credentials and audit is easier to secure and govern than nine point-to-point integrations with nine credential sets and nine audit positions.
- **Synergy 3**: Ostinato (SD-4) and Tanaka (SD-8) converge on commercial terms. Whether the outcome is "use what we have" or "buy something new," both want the commercial position clean and the lock-in minimised.

---

## Communication & Engagement Plan

### Stakeholder-Specific Messaging

#### Sam Okafor (Integration Architect) — Primary Stakeholder

**Primary Message**: This is your platform selection. You will operate it. Your technical assessment carries authority in the decision.

**Key Talking Points**:

- Evaluation criteria weight operational sustainability, not just features
- Schema registry is non-negotiable — the platform must enforce the canonical model
- Skills uplift is funded as part of this project, not deferred

**Communication Frequency**: Weekly (working sessions)

**Preferred Channel**: Technical working sessions; architecture review

**Success Story**: He selected a platform he can build on, and his team can operate it independently within 90 days.

---

#### Cassandra Rhodes (CIO)

**Primary Message**: Principle 19 is being applied to your own project — genuinely, not performatively. The evaluation will either prove existing capability is sufficient or produce a documented justification for new spend.

**Key Talking Points**:

- Microsoft agreement, PeopleSoft Integration Broker, and Ultra webhooks all tested against the same criteria
- Evaluation criteria published before testing — conclusion follows evidence
- If new spend is needed, the business case quantifies why

**Communication Frequency**: Fortnightly (steering)

**Preferred Channel**: Steering meeting; written evaluation summary

**Success Story**: Principle 19 applied credibly; the selected broker is operational; the programme is on track.

---

#### Dr. Benny Moog (Director, Learning Technologies)

**Primary Message**: The broker will be invisible to your team. Okafor's team operates it. Your team consumes integration outputs — enrolments arrive, grades flow, provisioning works.

**Key Talking Points**:

- Clear operational boundary: Digital & IT owns the broker; Learning Technologies owns the platforms
- Reliability is a weighted evaluation criterion
- You will not need a new dashboard or a new console

**Communication Frequency**: Fortnightly; milestone updates

**Preferred Channel**: Brief written update; no technical detail

**Success Story**: Integration just works. He never thinks about the broker.

---

#### Prof. Otis Hammond (DVC-E) and Vernon Ostinato (CFO)

**Primary Message**: The evaluation is timeboxed. The decision will be made within six weeks. The cost position will be clear and defensible.

**Key Talking Points**:

- Principle 19 test genuine but bounded — four weeks for existing capability, two weeks for alternatives if needed
- P003 timeline protected
- Cost comparison includes total cost of ownership, not just licence fees

**Communication Frequency**: Milestone briefings — evaluation outcome; selection decision

**Preferred Channel**: One-page written summary

**Success Story**: Decision made on time, within budget, defensible to audit.

---

#### Tobias Ohm and Eleanor Frame (Compliance)

**Primary Message**: Security and privacy are evaluation criteria, not post-selection assessments. Hosting region, credential model, and audit logging are tested during evaluation.

**Key Talking Points**:

- OAuth 2.0 / service principal authentication mandatory
- Hosting region confirmed before selection
- Audit logging verified, not assumed from vendor claims

**Communication Frequency**: Security/privacy review during evaluation; sign-off before production

**Preferred Channel**: Written assessment with criteria matrix

**Success Story**: No security or privacy finding after selection — because the criteria caught it during evaluation.

---

## Change Impact Assessment

### Impact on Stakeholders

| Stakeholder | Current State | Future State | Change Magnitude | Resistance Risk | Mitigation Strategy |
|-------------|---------------|--------------|------------------|-----------------|---------------------|
| Sam Okafor | No mediation layer; point-to-point integrations | Operates a central broker with schema registry | HIGH | LOW | Co-designer; he wants this change |
| Dr. Benny Moog | Integration failures surface as platform complaints | Integration mediated invisibly; failures caught by monitoring | LOW | LOW | Invisible to him by design |
| Cassandra Rhodes | Principle 19 untested for this project | Principle 19 applied to her own initiative | LOW | LOW | Aligned with her governance position |
| Tobias Ohm | Credential sprawl across nine integrations | Centralised credential management via the broker | MEDIUM | LOW | Aligned with E8 objectives |
| Eleanor Frame | PI flows through ungoverned channels | Single governed channel with audit logging | MEDIUM | LOW | Aligned with APP compliance |
| Vernon Ostinato | No visibility of integration platform costs | Clear cost position — existing or new, quantified | LOW | LOW | Present as improved financial control |
| Grace Tanaka | No procurement action pending | Possible new procurement; definite agreement review | LOW | LOW | Gives her early engagement rather than a rushed purchase |

### Change Readiness

**Champions** (Enthusiastic supporters):

- **Sam Okafor** — he co-designed the architecture that requires this platform; this is his project
- **Tobias Ohm** — centralised credentials and audit is exactly what he has been advocating
- **Eleanor Frame** — a single governed channel is easier to assess and control than nine ungoverned ones

**Fence-sitters** (Neutral, need convincing):

- **Vernon Ostinato** — will support if the Principle 19 test is genuine and the cost position is defensible
- **Grace Tanaka** — supportive if commercial terms are clean and timeline allows proper procurement
- **Dr. Benny Moog** — supportive as long as the broker is invisible to his team; will become a critic if it adds to his operational surface

**Resisters** (Opposed or skeptical):

- No stakeholder opposes this project. The disagreement is about *which* broker, not *whether* a broker. The closest to resistance is **Ostinato**, who will resist any new spend that he judges avoidable — but this is his role, not opposition to the project. *Strategy*: make the Principle 19 test genuine and the cost comparison transparent. If existing capability is sufficient, he is satisfied. If it is not, show him why.

---

## Risk Register (Stakeholder-Related)

### Risk R-1: Principle 19 test becomes a rubber stamp

**Related Stakeholders**: Rhodes, Ostinato, Okafor

**Risk Description**: The Principle 19 evaluation of existing licensed capability is conducted perfunctorily — either to confirm a preference for Microsoft (Rhodes) or to justify a preference for open-source (Okafor) — rather than as a genuine assessment.

**Impact on Goals**: G-1 directly; G-2 indirectly (a contested conclusion delays selection)

**Probability**: MEDIUM

**Impact**: HIGH

**Mitigation Strategy**: Publish evaluation criteria before testing begins; use the same criteria for existing capability and any new option; require both Okafor and Rhodes to sign off the evaluation report; present the criteria and conclusion to Ostinato, who has no platform preference and will scrutinise the methodology.

**Contingency Plan**: If the evaluation is contested, escalate to steering with the criteria matrix and test results. The decision is the steering committee's, not any individual stakeholder's.

---

### Risk R-2: Broker selection delays P003

**Related Stakeholders**: Hammond, Okafor, Rhodes, Moog

**Risk Description**: The evaluation and selection process takes longer than expected — ambiguous Microsoft licensing terms, protracted Principle 19 testing, or disagreement on the conclusion — and P003 Phase 1 is delayed.

**Impact on Goals**: G-2 directly; O-2 (P003 unblocked)

**Probability**: MEDIUM

**Impact**: HIGH

**Mitigation Strategy**: Timebox the evaluation at four weeks with a hard decision deadline. Test existing capabilities in parallel. If the evaluation is inconclusive, default to the option that is most quickly deployable while meeting schema registry and security requirements — with a documented review point after six months.

**Contingency Plan**: If selection is delayed beyond six weeks, begin INT-001 development against a defined interface contract (the canonical model) with the broker abstracted — allowing the integration to be deployed on whichever broker is eventually selected. This adds complexity but protects the P003 timeline.

---

### Risk R-3: Selected broker lacks schema registry capability

**Related Stakeholders**: Okafor, Rhodes, Moog

**Risk Description**: The broker selected on cost or Principle 19 grounds — particularly PeopleSoft Integration Broker or a lightweight message queue — lacks schema registry capability, and runtime enforcement of the canonical model is lost.

**Impact on Goals**: G-3 directly; O-1 (governed integration layer)

**Probability**: MEDIUM

**Impact**: HIGH

**Mitigation Strategy**: Schema registry is a non-negotiable evaluation criterion. Any option that lacks it — built-in or as a composable sidecar — fails the evaluation regardless of cost or Principle 19 compliance. This is documented in the evaluation criteria before testing begins.

**Contingency Plan**: If no existing capability provides schema registry, this is itself the Principle 19 test outcome: existing capability is genuinely unsuitable for the stated requirement. Document this finding and proceed to evaluate options that include schema registry.

---

### Risk R-4: Skills gap delays operational readiness

**Related Stakeholders**: Okafor, Rhodes, Hammond

**Risk Description**: The selected broker requires operational skills that Okafor's team does not hold, and the skills uplift plan is compressed or unfunded, leading to a broker that is deployed but not operationally sustainable.

**Impact on Goals**: G-5 directly; O-3 (sustainable operations)

**Probability**: MEDIUM

**Impact**: MEDIUM

**Mitigation Strategy**: Training budget and timeline included in the project scope from the outset, not added later. Operational sustainability weighted in the evaluation criteria — a platform with a steeper learning curve must demonstrate proportionally stronger community resources and documentation. Accept managed service as a starting position if necessary, with a documented plan to internalise operations.

**Contingency Plan**: If skills uplift cannot be completed before INT-001 production, operate under vendor or community support with a time-bounded plan to transition to independent operation. Do not allow "temporary" vendor dependency to become permanent.

---

## Governance & Decision Rights

### Decision Authority Matrix (RACI)

| Decision Type | Responsible | Accountable | Consulted | Informed |
|---------------|-------------|-------------|-----------|----------|
| Evaluation criteria definition | Okafor | Rhodes | Ohm, Frame, Tanaka | Hammond, Ostinato, Moog |
| Existing capability testing (Principle 19) | Okafor | Rhodes | Microsoft, Anthology, Oracle | Hammond, Ostinato |
| Broker selection recommendation | Okafor | Rhodes | Ohm, Frame, Tanaka, Moog | Hammond, Ostinato |
| Broker selection approval | Rhodes | Hammond | Ostinato, Ohm | All stakeholders |
| Funding approval (if new purchase) | Rhodes | Ostinato | Hammond, Tanaka | All stakeholders |
| Schema registry configuration | Okafor | Okafor | Moog | Rhodes |
| Security architecture review | Ohm | Rhodes | Okafor, Frame | Hammond |
| Privacy assessment | Frame | Rhodes | Ohm, Okafor | Hammond |
| Contract/licensing terms (if new) | Tanaka | Ostinato | Rhodes | Hammond |
| Operational readiness sign-off | Okafor | Rhodes | Ohm | Hammond, Moog |

### Escalation Path

Aligned to the RIFF governance process:

1. **Level 1 — Project working group**: Okafor with Ohm and Frame. Day-to-day evaluation, testing, and deployment decisions.
2. **Level 2 — RIFF Review**: Principle 19 evaluation outcome; broker selection recommendation; schema registry design.
3. **Level 3 — Steering Committee**: Hammond (chair), Rhodes — fortnightly. Selection decision; funding approval for new purchase; timeline variance.
4. **Level 4 — Operations Committee / University Executive**: Where financial thresholds are exceeded or where the Principle 19 test outcome is contested.

---

## Validation & Sign-off

### Stakeholder Review

| Stakeholder | Review Date | Comments | Status |
|-------------|-------------|----------|--------|
| Sam Okafor | Scheduled 2026-08-05 | Pending — evaluation criteria and SD-1/SD-9 characterisation | PENDING |
| Cassandra Rhodes | Scheduled 2026-08-05 | Pending — Principle 19 process and SD-2/SD-10 characterisation | PENDING |
| Prof. Otis Hammond | Scheduled 2026-08-12 | Pending — programme timeline and CSF validation | PENDING |

> **Note**: SD-1, SD-2, and SD-10 characterise stakeholder positions candidly, including personal dimensions. These should be validated with the Executive Sponsor before the analysis is shared beyond the steering group.

### Document Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Project Sponsor | Prof. Otis Hammond, DVC (Education) | | |
| Integration Architect | Sam Okafor | | |
| Chief Information Officer | Cassandra Rhodes | | |

---

## Appendices

### Appendix A: Stakeholder Interview Summaries

No stakeholder interviews have been conducted as at 2026-07-29. This analysis is derived from the Project 001 stakeholder analysis (ARC-001-STKE-v1.0), ADR-001 and its conditions, the privacy context, and the system landscape.

Drivers marked with a PERSONAL category — SD-1, SD-3 — are inferred from role and documented position rather than stated by the individual. They should be tested in validation conversations before being treated as established.

**Planned validation conversations**:

| Stakeholder | Purpose | Target |
|-------------|---------|--------|
| Sam Okafor | Validate SD-1 and SD-9; confirm evaluation approach | Week 1 |
| Cassandra Rhodes | Validate SD-2 and SD-10; confirm Principle 19 process | Week 1 |
| Tobias Ohm | Confirm security evaluation criteria | Week 1 |
| Eleanor Frame | Confirm privacy and hosting requirements | Week 1 |

### Appendix B: Cross-Project Traceability

This stakeholder analysis inherits from and references:

| Source Artifact | Project | Relevance to Project 004 |
|-----------------|---------|--------------------------|
| ARC-001-STKE-v1.0 | 001-lt-ecosystem | Baseline stakeholder register; drivers for Okafor, Rhodes, Ostinato, Moog, Ohm, Frame |
| ARC-003-STKE-v1.0 | 003-lms-ultra-migration | P003 dependency on broker selection; timeline constraint |
| ARC-000-PRIN-v1.1 | 000-global | Governing principles — especially 5, 6, 9, 10, 11, 17, 19 |
| ARC-001-ADR-001-v1.0 | 001-lt-ecosystem | Integration Mediation Approach — this project executes Condition 1 |
| ARC-001-DATA-v1.0 | 001-lt-ecosystem | Canonical data model — schema registry content for this project |

### Appendix C: References

- ARC-000-PRIN-v1.1 — Enterprise Architecture Principles
- ARC-001-ADR-001-v1.0 — Integration Mediation Approach (ADR-001)
- ARC-001-DATA-v1.0 — Data Model and Privacy-Relevant Flows
- ARC-001-STKE-v1.0 — Stakeholder Drivers & Goals Analysis (Project 001)
- ARC-003-STKE-v1.0 — Stakeholder Drivers & Goals Analysis (Project 003)

---

## External References

> This section provides traceability from generated content back to source documents.

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| ADR1 | ARC-001-ADR-001-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/decisions/` | Integration Mediation Approach — Condition 1 is this project's origin |
| DATA1 | ARC-001-DATA-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/` | Canonical data model — schema registry content |
| PP | ARC-000-PRIN-v1.1.md | ArcKit artifact | `projects/000-global/` | Enterprise Architecture Principles — Principle 19 |
| STK1 | ARC-001-STKE-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/` | Stakeholder Drivers & Goals Analysis (Project 001) |
| STK3 | ARC-003-STKE-v1.0.md | ArcKit artifact | `projects/003-lms-ultra-migration/` | Stakeholder Drivers & Goals Analysis (Project 003) |
| PC | privacy-context.md | Compliance input | `projects/004-integration-platform/external/` | Personal information inventory and data flows |
| SL | system-landscape.md | Foundation artifact | `projects/004-integration-platform/external/` | System categorisation map with integrations |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| P4-C1 | ADR1 | Conditions | Governance | "Principle 19 test must be completed before procurement. Digital & IT to confirm in writing whether existing licensed platforms — including the Microsoft agreement — already provide adequate integration or event-brokering capability." |
| P4-C2 | ADR1 | Decision Outcome | Architecture | "Chosen option: Option B — Central integration broker, with a phased adoption path that begins with the two integrations carrying the highest failure cost." |
| P4-C3 | ADR1 | Option B | Capability | "The broker holds the canonical schema, enforces contracts, and provides retry, replay, dead-letter and observability as shared services." |
| P4-C4 | PP | Principle 19 | Design Constraint | "Where a required capability already exists within a licensed platform, the university MUST evaluate configuring and adopting it before acquiring a new platform." |
| P4-C5 | ADR1 | Justification | Architecture | "Enforcement is the difference between a model that governs and a model that documents." |
| P4-C6 | ADR1 | Negative trade-offs | Risk | "Requires operational capability the AV/integration team does not currently hold — skills and on-call" |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| ARC-001-REQ-v1.0.md | `projects/001-lt-ecosystem/` | Requirements document informs ADR-001 but is not directly cited in this stakeholder analysis |
| ARC-001-RISK-v1.0.md | `projects/001-lt-ecosystem/` | Risk register relevant to integration fragility but not directly cited here |

---

**Generated by**: ArcKit `/arckit:stakeholders` command
**Generated on**: 2026-07-29
**ArcKit Version**: 6.7.4
**Project**: Integration Platform Selection & Implementation (Project 004)
**Model**: Claude Opus 4.6 (1M context)
