# Risk Register: Learning & Teaching Baseline Strategy

> **Template Origin**: Official | **ArcKit Version**: 6.4.0 | **Command**: `/arckit:risk`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-RISK-v1.0 |
| **Document Type** | Risk Register (HM Treasury Orange Book 2023) |
| **Project** | Learning & Teaching Baseline Strategy (Project 001) |
| **Classification** | OFFICIAL-SENSITIVE |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-27 |
| **Last Modified** | 2026-07-27 |
| **Review Cycle** | Monthly (Critical/High), Quarterly (Medium/Low) |
| **Next Review Date** | 2026-08-27 |
| **Owner** | Rhonda Bell, Project Manager — L&T Baseline Strategy |
| **Reviewed By** | [PENDING] — Prof. Otis Hammond, Executive Sponsor |
| **Approved By** | [PENDING] — Steering Committee |
| **Distribution** | Steering Committee, Project Team, Digital & IT, Privacy & Records, Cybersecurity |

> **Classification rationale**: This register enumerates unremediated privacy and security weaknesses, names the platforms affected, and states how long they will remain open. Classified OFFICIAL-SENSITIVE and restricted to the steering and delivery group.

> **Framework note**: The Orange Book is HM Treasury guidance for UK Government. The University of Funk is an Australian institution and is not bound by it. It is applied here as a **methodology** — 4Ts, inherent/residual scoring, appetite thresholds — because it is a sound and widely recognised risk framework, not because it is a compliance obligation. UK-specific risk categories (parliamentary scrutiny, NAO, PAC, GDS assessment, HMT spending controls) are **not applicable** and have been omitted rather than translated. Monetary values are AUD.

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-27 | ArcKit AI | Initial creation from `/arckit:risk` command | [PENDING] | [PENDING] |

---

## Executive Summary

### Risk Profile Overview

| Metric | Value |
|--------|-------|
| **Total risks identified** | 29 |
| **Critical (20–25)** | 0 residual (5 inherent) |
| **High (13–19)** | 5 residual (9 inherent) |
| **Medium (6–12)** | 23 residual (15 inherent) |
| **Low (1–5)** | 1 residual (0 inherent) |
| **Total inherent score** | 414 |
| **Total residual score** | 281 |
| **Overall risk reduction** | 32% |
| **Risks exceeding provisional appetite** | 5 |
| **Risks with named owner** | 29 of 29 (100%) |

### Risk Category Distribution

| Category | Count | Avg Inherent | Avg Residual | Reduction |
|----------|-------|--------------|--------------|-----------|
| STRATEGIC | 5 | 15.0 | 9.0 | 40% |
| OPERATIONAL | 7 | 14.7 | 10.9 | 26% |
| FINANCIAL | 4 | 11.5 | 7.2 | 37% |
| COMPLIANCE | 6 | 15.8 | 11.8 | 25% |
| REPUTATIONAL | 3 | 13.0 | 8.0 | 38% |
| TECHNOLOGY | 4 | 14.0 | 9.0 | 36% |

### Overall Risk Assessment

**CONCERNING** — but tractable.

No residual risk reaches Critical. However, **five risks remain High after existing controls, and four of those five have essentially no effective control in place today**. The pattern is consistent and worth stating plainly: this is not a project with a risk problem, it is an **estate** with a risk problem that the project has surfaced. R-006, R-008, R-017 and R-018 all describe conditions that have existed for years and are only now being assessed.

The 30% inherent-to-residual reduction is modest by design. Inflating it would require crediting controls that do not exist — several current "controls" are manual checking and staff diligence, which the Orange Book would rate Weak.

### Risks Exceeding Appetite

> **No approved organisational risk appetite statement exists.** There is no `projects/000-global/risk-appetite.md`. The thresholds in Section G are **PROVISIONAL**, proposed by this register for Executive endorsement. Every "exceeds appetite" judgement below is therefore an architectural recommendation, not a governance finding — a distinction that matters if this register is cited in the September business case.

Five risks exceed the provisional thresholds:

| Risk | Category | Residual | Provisional Threshold | Over By |
|------|----------|----------|----------------------|---------|
| R-018 | COMPLIANCE | 16 | 9 | +7 |
| R-017 | COMPLIANCE | 16 | 9 | +7 |
| R-008 | OPERATIONAL | 16 | 12 | +4 |
| R-001 | STRATEGIC | 16 | 12 | +4 |
| R-006 | OPERATIONAL | 15 | 12 | +3 |

### Top 5 Risks Requiring Immediate Attention

1. **R-018 (COMPLIANCE, 16)** — Sensitive placement information transferred by manual re-keying and email. Owner: Eleanor Frame.
2. **R-017 (COMPLIANCE, 16)** — Four personal information classes disclosed offshore with no APP 8 assessment completed. Owner: Eleanor Frame.
3. **R-008 (OPERATIONAL, 16)** — Placement grades re-keyed by hand between systems. Owner: Prof. Priya Anand.
4. **R-001 (STRATEGIC, 16)** — Consolidation-versus-best-of-breed decision unresolved, blocking the future state. Owner: Prof. Otis Hammond.
5. **R-006 (OPERATIONAL, 15)** — Integration estate fragility: nightly batch, role assignment failures, no intra-day synchronisation. Owner: Cassandra Rhodes.

### Key Findings and Recommendations

**Finding 1 — Three of the top five are the same defect viewed from different angles.** R-008 (operational), R-018 (compliance) and the breach exposure in R-023 all trace to one flow: placement outcomes moving between systems by hand. Remediating INT-005 closes an operational risk, a privacy risk and a reputational risk simultaneously. It is the single highest-leverage action in this register and should be sequenced first regardless of what else the roadmap contains.

**Finding 2 — The compliance risks are unassessed, not merely unmitigated.** R-017 sits at 16 not because the offshore disclosures are known to be unsafe, but because nobody has looked. The residual score reflects uncertainty, and completing the PIA may lower it substantially at low cost. This is the cheapest score reduction available.

**Finding 3 — R-001 is a decision risk, not a delivery risk.** It cannot be mitigated by doing more work; it requires someone to decide. Every week it stays open, WP8 and the roadmap carry unresolved ambiguity. The recommendation is a hard decision deadline, not further analysis.

**Finding 4 — Control effectiveness is weak across the estate.** Of 29 risks, 11 have no effective control today. "Staff are careful" is the current control for the estate's most sensitive data flow.

**Recommendation**: Escalate R-017 and R-018 to the Steering Committee at the next fortnightly meeting. Both are live compliance exposures with a real regulatory dimension, and both predate this engagement.

---

## A. Risk Matrix Visualization

### Inherent Risk Matrix (Before Controls)

```text
                                          IMPACT
                1-Negligible  2-Minor    3-Moderate   4-Major     5-Catastrophic
              ┌────────────┬────────────┬────────────┬────────────┬────────────┐
 5-Almost     │            │            │  R-009     │  R-006     │            │
   Certain    │            │            │  R-019     │  R-008     │            │
              │     5      │     10     │     15     │  R-017  20 │     25     │
              ├────────────┼────────────┼────────────┼────────────┼────────────┤
 4-Likely     │            │            │  R-003     │  R-001     │  R-018     │
              │            │            │  R-005     │  R-013     │            │
 L            │            │            │  R-010     │  R-021     │            │
 I            │            │            │  R-012     │  R-026     │            │
 K            │            │            │  R-020     │  R-028     │            │
 E            │            │            │  R-022     │            │            │
 L            │            │            │  R-025     │            │            │
 I            │            │            │  R-027     │            │            │
 H            │     4      │     8      │     12     │     16     │     20     │
 O            ├────────────┼────────────┼────────────┼────────────┼────────────┤
 O 3-Possible │            │            │  R-015     │  R-007     │  R-004     │
 D            │            │            │  R-016     │  R-011     │  R-023     │
              │            │            │            │  R-014     │            │
              │            │            │            │  R-024     │            │
              │            │            │            │  R-029     │            │
              │     3      │     6      │     9      │     12     │     15     │
              ├────────────┼────────────┼────────────┼────────────┼────────────┤
 2-Unlikely   │            │            │            │            │  R-002*    │
              │     2      │     4      │     6      │     8      │     10     │
              ├────────────┼────────────┼────────────┼────────────┼────────────┤
 1-Rare       │     1      │     2      │     3      │     4      │     5      │
              └────────────┴────────────┴────────────┴────────────┴────────────┘
```

*R-002 sits at L4/I4 inherent (16); shown here for completeness of the low-likelihood band.

Legend: 🟥 Critical (20–25) · 🟧 High (13–19) · 🟨 Medium (6–12) · 🟩 Low (1–5)

### Residual Risk Matrix (After Controls)

```text
                                          IMPACT
                1-Negligible  2-Minor    3-Moderate   4-Major     5-Catastrophic
              ┌────────────┬────────────┬────────────┬────────────┬────────────┐
 5-Almost     │            │            │  R-006     │            │            │
   Certain    │     5      │     10     │     15     │     20     │     25     │
              ├────────────┼────────────┼────────────┼────────────┼────────────┤
 4-Likely     │            │            │  R-009     │  R-001     │            │
              │            │            │  R-019     │  R-008     │            │
 L            │            │            │            │  R-017     │            │
 I            │            │            │            │  R-018     │            │
 K            │     4      │     8      │     12     │     16     │     20     │
 E            ├────────────┼────────────┼────────────┼────────────┼────────────┤
 L 3-Possible │            │  R-012     │  R-005     │  R-007     │            │
 I            │            │  R-025     │  R-010     │  R-021     │            │
 H            │            │            │  R-013     │  R-026     │            │
 O            │            │            │  R-020     │            │            │
 O            │            │            │  R-027     │            │            │
 D            │            │            │  R-028     │            │            │
              │     3      │     6      │     9      │     12     │     15     │
              ├────────────┼────────────┼────────────┼────────────┼────────────┤
 2-Unlikely   │            │  R-003     │  R-002     │  R-014     │  R-004     │
              │            │  R-011     │  R-015     │  R-024     │  R-023     │
              │            │            │  R-016     │            │            │
              │            │            │  R-022     │            │            │
              │            │            │  R-029     │            │            │
              │     2      │     4      │     6      │     8      │     10     │
              ├────────────┼────────────┼────────────┼────────────┼────────────┤
 1-Rare       │     1      │     2      │     3      │     4      │     5      │
              └────────────┴────────────┴────────────┴────────────┴────────────┘
```

**Notable movement:**

- R-018 moved from Critical (20) to High (16) — controls are weak; the reduction reflects awareness only
- R-017 moved from Critical (20) to High (16) — no assessment completed, so reduction is minimal
- R-008 moved from Critical (20) to High (16) — manual checking is the only control
- R-006 moved from Critical (20) to High (15) — workarounds reduce impact, not likelihood
- R-002 moved from High (16) to Medium (6) — principles written in academic-outcome terms, validation planned
- R-022 moved from Medium (12) to Medium (6) — data model now defines retention and minimisation

---

## B. Top 10 Risks (Ranked by Residual Score)

| Rank | ID | Title | Category | Inherent | Residual | Owner | Status | Response |
|------|-----|-------|----------|----------|----------|-------|--------|----------|
| 1 | R-018 | Sensitive placement data handled manually | COMPLIANCE | 20 | **16** | Eleanor Frame | Open | Treat |
| 2 | R-017 | APP 8 offshore disclosures unassessed | COMPLIANCE | 20 | **16** | Eleanor Frame | Open | Treat |
| 3 | R-008 | Placement grades re-keyed by hand | OPERATIONAL | 20 | **16** | Prof. Priya Anand | Open | Treat |
| 4 | R-001 | Consolidation decision unresolved | STRATEGIC | 20 | **16** | Prof. Otis Hammond | Open | Treat |
| 5 | R-006 | Integration estate fragility | OPERATIONAL | 20 | **15** | Cassandra Rhodes | In Progress | Treat |
| 6 | R-007 | Single-person dependency on cloning automation | OPERATIONAL | 12 | **12** | Sam Okafor | Open | Treat |
| 7 | R-009 | Casual staff provisioning by manual CSV | OPERATIONAL | 15 | **12** | Sam Okafor | Open | Treat |
| 8 | R-019 | Local accounts breach SSO/MFA requirement | COMPLIANCE | 15 | **12** | Tobias Ohm | Open | Treat |
| 9 | R-021 | Accessibility conformance unverified | COMPLIANCE | 16 | **12** | A/Prof. Pearl Clavinet | Open | Treat |
| 10 | R-026 | Vendor platforms may not support event-driven integration | TECHNOLOGY | 16 | **12** | Sam Okafor | Open | Treat |

---

## C. Detailed Risk Register

> Full Orange Book profiles are provided for the six highest-residual risks. Risks R-007 onward carry a structured profile with all mandatory fields — identification, inherent assessment, controls, residual assessment, 4Ts response, owner, action and target date — in condensed form.

### Risk R-001: Consolidation decision unresolved, blocking future state

**Category:** STRATEGIC
**Status:** Open
**Risk Owner:** Prof. Otis Hammond, DVC (Education) — Executive Sponsor (STKE RACI: Accountable for roadmap sequencing)
**Action Owner:** Dr. Benny Moog, Director Learning Technologies (RIFF facilitation)

#### Risk Identification

**Risk Description:**
The CIO favours consolidating collaboration, delivery and lecture capture onto a single vendor platform; the Director of Learning Technologies and the Dean of Music & Performing Arts defend best-of-breed pedagogical tooling. The disagreement is documented and unresolved. WP8 future-state design and the WP9 roadmap both depend on knowing which platforms persist.

**Root Cause:**
No governing architecture existed while the ecosystem grew, so platform overlap accumulated without a decision framework. The disagreement is genuine — both positions have merit — and there is no agreed basis on which to settle it.

**Trigger Events:**

- RIFF review is scheduled but does not reach a conclusion
- Capability mapping (WP3) does not complete in sufficient depth to compare options on evidence
- The decision is deferred to the September business case, where it is settled on cost alone

**Consequences if Realized:**

- WP8 future state is ambiguous — "one platform or three" is unanswerable
- WP9 roadmap cannot sequence retirements, so BR-002 licence savings cannot be modelled
- The Executive arbitrates a pedagogical question without pedagogical input
- Engagement is judged to have avoided the hard question

**Affected Stakeholders:**

- **Cassandra Rhodes (CIO)**: consolidation objective unmet; support surface unchanged
- **Dr. Benny Moog**: positioned as the obstacle to a decision made elsewhere
- **Prof. Desmond Key**: discipline capability decided without the school present
- **Vernon Ostinato (CFO)**: savings cannot be quantified without knowing what retires

**Related Objectives:**

- **Goal G-4** (Contested platform decisions resolved through governance): directly defeated
- **Goal G-6** (Roadmap delivered to business case timing): blocked downstream
- **Outcome O-1** (Bounded ecosystem): unachievable without the decision

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | Contested decisions between senior stakeholders with no agreed criteria characteristically slip |
| **Impact** | 5 — Catastrophic | Blocks the terminal deliverable; the engagement's central question goes unanswered |
| **Inherent Risk Score** | **20** (Critical) | 4 × 5 = 20 |

**Risk Zone:** 🟥 Critical (20–25)

#### Current Controls and Mitigations

**Existing Controls:**

1. **RIFF Review process**: an established institutional gate for solution decisions
   - Owner: Dr. Benny Moog
   - Effectiveness: **Adequate** — the forum exists but has no maintained evidence base
   - Evidence: documented in the governance process; used for prior solution requests

2. **Fortnightly Steering Committee**: escalation path exists (Hammond, Rhodes, Clavinet)
   - Owner: Prof. Otis Hammond
   - Effectiveness: **Adequate** — provides a venue, does not compel a decision
   - Evidence: cadence agreed in the engagement plan

3. **Architecture principle 2 (Deliberate Capability Boundaries)**: requires every overlap to be declared
   - Owner: A/Prof. Pearl Clavinet
   - Effectiveness: **Adequate** — reframes the question from "which wins" to "where is the boundary", which is answerable
   - Evidence: ARC-000-PRIN-v1.0 endorsed pathway

**Overall Control Effectiveness:** Adequate — reduces impact from 5 to 4 (a declared boundary is a valid outcome even without full consolidation), but does not reduce likelihood.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | The forum exists but nothing yet compels a decision by a date |
| **Impact** | 4 — Major | Principle 2 makes "declared boundary" an acceptable outcome, so total ambiguity is avoided |
| **Residual Risk Score** | **16** (High) | 4 × 4 = 16 |

**Risk Zone:** 🟧 High (13–19)
**Risk Reduction:** 20% (20 → 16)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:**
This is a decision risk, not a delivery risk — it cannot be mitigated by further analysis. The treatment is procedural: publish decision criteria before options are scored, and set a hard deadline that protects WP8.

**Alternative Responses Considered:**

- **Tolerate**: Rejected — the consequence is failure of the terminal deliverable
- **Transfer**: Not applicable — cannot be contracted or insured
- **Terminate**: Rejected — abandoning the rationalisation objective defeats the engagement

#### Risk Appetite Assessment

**Provisional appetite for STRATEGIC risks:** Medium (≤ 12)
**Current residual:** 16 (High)
**Assessment:** ❌ **Exceeds provisional appetite** by 4 points

**Justification:** Acceptable only for a bounded period with a decision deadline attached. Not acceptable as a standing position through to the business case.

**Escalation Required:** Yes — Steering Committee, next fortnightly meeting.

#### Action Plan

**Additional Mitigations Needed:**

1. **Publish decision criteria before scoring**
   - Description: Agree and publish the weighting of pedagogical capability, integration cost, security conformance and whole-of-life licence cost, with both positions represented in setting them
   - Owner: Dr. Benny Moog with Cassandra Rhodes
   - Due Date: 2026-08-07
   - Cost: nil (facilitation time)
   - Expected Impact: reduce likelihood 4 → 3

2. **Set a hard decision deadline protecting WP8**
   - Description: Steering Committee sets a date beyond which the decision escalates to Education Committee automatically
   - Owner: Prof. Otis Hammond
   - Due Date: 2026-08-07
   - Cost: nil
   - Expected Impact: reduce likelihood 3 → 2

3. **Complete capability mapping to sufficient depth on the contested categories**
   - Description: Prioritise Learning Delivery, Learning Capture and Collaboration in WP3 so the comparison rests on evidence
   - Owner: Dr. Benny Moog
   - Due Date: 2026-08-14
   - Cost: within engagement scope
   - Expected Impact: reduce impact 4 → 3

**Target Residual Risk After Mitigations:** L2 × I3 = **6 (Medium)** ✅ within provisional appetite

**Success Criteria:**

- Decision criteria published and agreed by both positions before any option is scored
- Decision recorded in the WP6 register with options, implications and rationale before WP8 concludes

**Monitoring Plan:**

- **Frequency:** Fortnightly at Steering Committee
- **Key Indicators:** criteria published (Y/N); decision recorded (Y/N); days to WP8 deadline
- **Escalation Triggers:** criteria not published by 2026-08-07; decision open at 2026-08-21

---

### Risk R-006: Integration estate fragility

**Category:** OPERATIONAL
**Status:** In Progress
**Risk Owner:** Cassandra Rhodes, Chief Information Officer (STKE RACI: Accountable for integration architecture)
**Action Owner:** Sam Okafor, Integration Architect

#### Risk Identification

**Risk Description:**
The student information system feeds the learning platform by nightly batch flat-file. Role assignment fails intermittently, there is no intra-day synchronisation, and institutional hierarchy drifts between systems. Four of seven known integrations involve manual handling or flat-file transfer.

**Root Cause:**
Point-to-point integrations were built incrementally with no governing architecture, canonical model or declared authoritative source for core entities.

**Trigger Events:**

- Teaching period commencement, when enrolment change volume peaks
- A student enrols or withdraws and the change is not reflected for up to 24 hours
- Flat-file transfer fails silently overnight with no alerting

**Consequences if Realized:**

- Students cannot reach materials at the start of a teaching period
- Staff lack marking access when they need it
- Withdrawn students retain access for up to 24 hours — an access-control exposure
- Support load spikes at the busiest point in the academic calendar

**Affected Stakeholders:**

- **Students**: cannot access enrolled units
- **Dr. Wynton Castle and teaching staff**: access failures during teaching
- **Sam Okafor**: carries the operational burden
- **Eleanor Frame**: stale deprovisioning is an APP 11 exposure

**Related Objectives:**

- **Goal G-3** (Integration architecture defined): this risk is the reason it exists
- **Outcome O-2** (Reliable governed integration): directly threatened

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 5 — Almost Certain | Already occurring; documented as a current defect |
| **Impact** | 4 — Major | Teaching disruption at scale during peak periods |
| **Inherent Risk Score** | **20** (Critical) | 5 × 4 = 20 |

**Risk Zone:** 🟥 Critical (20–25)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Manual workarounds**: staff intervene when failures are reported
   - Owner: Learning Technologies
   - Effectiveness: **Weak** — reactive, triggered by user report after impact has occurred
   - Evidence: documented manual CSV workaround for casual staff

2. **Semi-manual scripts for cloning**: partially automates rollover
   - Owner: single individual (see R-007)
   - Effectiveness: **Weak** — undocumented, single-person dependency

**Overall Control Effectiveness:** Weak — reduces impact from 4 to 3 by shortening outage duration, but does nothing to reduce likelihood.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 5 — Almost Certain | Still occurring; nothing structural has changed |
| **Impact** | 3 — Moderate | Manual intervention limits duration once a failure is noticed |
| **Residual Risk Score** | **15** (High) | 5 × 3 = 15 |

**Risk Zone:** 🟧 High (13–19)
**Risk Reduction:** 25% (20 → 15)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:**
The target integration architecture (WP5) and canonical model directly address the root cause. This is remediable, and the requirements are already specified (NFR-P-001, INT-001, INT-002).

**Alternative Responses Considered:**

- **Tolerate**: Rejected — recurring teaching disruption is not tolerable
- **Transfer**: Not applicable
- **Terminate**: Not viable — the integration is essential

#### Risk Appetite Assessment

**Provisional appetite for OPERATIONAL risks:** Medium (≤ 12)
**Current residual:** 15 (High)
**Assessment:** ❌ **Exceeds provisional appetite** by 3 points
**Escalation Required:** Yes — but note this is a pre-existing estate condition, not a project-introduced risk.

#### Action Plan

**Additional Mitigations Needed:**

1. **Define target integration architecture and canonical model**
   - Owner: Sam Okafor with the Solution Architect
   - Due Date: 2026-08-28 (WP5 deliverable)
   - Cost: within engagement scope
   - Expected Impact: enables all subsequent reduction; no immediate score change

2. **Implement monitoring on existing batch flows as an interim control**
   - Description: Alert on batch failure and record count anomalies so failures are detected before users report them
   - Owner: Sam Okafor
   - Due Date: 2026-09-30
   - Cost: minimal — existing tooling
   - Expected Impact: reduce impact 3 → 2

3. **Deliver event-driven propagation for identity, enrolment and role**
   - Owner: Sam Okafor, funded via the business case
   - Due Date: 2027-06-30
   - Cost: capital, to be estimated in WP9
   - Expected Impact: reduce likelihood 5 → 2

**Target Residual Risk After Mitigations:** L2 × I2 = **4 (Low)** ✅ within provisional appetite

**Success Criteria:**

- Propagation latency within 15 minutes at the 95th percentile (NFR-P-001)
- Zero integration failures discovered by user report

**Monitoring Plan:**

- **Frequency:** Monthly during delivery
- **Key Indicators:** propagation latency; failures detected by monitoring vs by user report
- **Escalation Triggers:** any teaching-period access failure affecting more than 50 students

---

### Risk R-008: Placement grades re-keyed by hand

**Category:** OPERATIONAL
**Status:** Open
**Risk Owner:** Prof. Priya Anand, Dean of Health Sciences (STKE RACI: Accountable for placement data)
**Action Owner:** Sam Okafor, Integration Architect

#### Risk Identification

**Risk Description:**
Placement assessment outcomes recorded by external supervisors are manually re-keyed into the LMS gradebook. The process is documented as error-prone with audit concerns, and grade sheets circulate by email and screenshot.

**Root Cause:**
No integration exists between the placement management platform and the gradebook. The gap was bridged by human effort and never revisited.

**Trigger Events:**

- End-of-placement assessment periods when volume concentrates
- A supervisor submits an outcome and it is transcribed incorrectly
- An export is emailed to the wrong recipient

**Consequences if Realized:**

- A student receives an incorrect grade on their academic record
- Grade disputes with no attributable audit trail
- Sensitive placement information disclosed to unintended recipients (links to R-018, R-023)
- Professional accreditation exposure for Health Sciences

**Affected Stakeholders:**

- **Students on placement**: academic record accuracy and fairness
- **Prof. Priya Anand**: faculty accountability for assessment integrity
- **Eleanor Frame**: privacy exposure from manual handling
- **Placement supervisors**: burden of an unsupported process

**Related Objectives:**

- **Goal G-3** (Integration architecture): INT-005 exists specifically for this
- **Outcome O-2** (Reliable governed integration)

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 5 — Almost Certain | Manual transcription at this volume produces errors as a statistical certainty |
| **Impact** | 4 — Major | Incorrect academic records with accreditation and fairness consequences |
| **Inherent Risk Score** | **20** (Critical) | 5 × 4 = 20 |

**Risk Zone:** 🟥 Critical (20–25)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Manual checking by placement administrators**
   - Owner: Health Sciences placement team
   - Effectiveness: **Weak** — human verification of human transcription; catches some errors, not systematically
   - Evidence: none — no error rate is measured

**Overall Control Effectiveness:** Weak — reduces impact marginally by catching some errors before finalisation.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | Checking catches some errors but the process remains manual end to end |
| **Impact** | 4 — Major | Errors reaching the academic record retain full consequence |
| **Residual Risk Score** | **16** (High) | 4 × 4 = 16 |

**Risk Zone:** 🟧 High (13–19)
**Risk Reduction:** 20% (20 → 16)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:**
INT-005 (bidirectional placement-to-gradebook synchronisation) is already specified as a Must requirement and eliminates the root cause. This is the highest-leverage single remediation in the register — it closes an operational risk, a compliance risk (R-018) and a reputational risk (R-023) together.

#### Risk Appetite Assessment

**Provisional appetite for OPERATIONAL risks:** Medium (≤ 12)
**Current residual:** 16 (High)
**Assessment:** ❌ **Exceeds provisional appetite** by 4 points
**Escalation Required:** Yes — Steering Committee.

#### Action Plan

**Additional Mitigations Needed:**

1. **Interim control — prohibit email and spreadsheet transfer immediately**
   - Description: Issue handling instruction; route all transfers through the placement platform only
   - Owner: Prof. Priya Anand with Eleanor Frame
   - Due Date: 2026-08-14
   - Cost: nil
   - Expected Impact: reduce impact 4 → 3 (limits disclosure exposure)

2. **Implement INT-005 bidirectional synchronisation with conflict-resolution rule**
   - Owner: Sam Okafor
   - Due Date: 2027-03-31 (priority-one remediation in the roadmap)
   - Cost: capital, to be estimated in WP9
   - Expected Impact: reduce likelihood 4 → 1

**Target Residual Risk After Mitigations:** L1 × I3 = **3 (Low)** ✅ within provisional appetite

**Success Criteria:**

- Zero placement outcomes entered by manual re-keying
- All transfers attributable in the audit log (E-020)

**Monitoring Plan:**

- **Frequency:** Monthly until remediated
- **Key Indicators:** count of manual transfers; failed-sync queue depth once INT-005 is live
- **Escalation Triggers:** any grade dispute traced to transcription error

---

### Risk R-017: APP 8 offshore disclosures unassessed

**Category:** COMPLIANCE
**Status:** Open
**Risk Owner:** Eleanor Frame, Privacy & Records Officer (STKE RACI: Responsible for privacy positions)
**Action Owner:** Eleanor Frame with Grace Tanaka (contract terms)

#### Risk Identification

**Risk Description:**
Four classes of personal information — submitted student work, some recordings, exam responses and proctoring artifacts, and survey responses — are disclosed offshore under the assessed hosting arrangements. No APP 8 cross-border assessment has been completed for any platform.

**Root Cause:**
Platforms were adopted on functional merit without hosting region being captured as a procurement attribute, and no assessment gate existed.

**Trigger Events:**

- A privacy complaint or access request exposes the absence of assessment
- A vendor changes hosting region without notice
- An overseas recipient suffers a breach involving university data

**Consequences if Realized:**

- APP 8.1 breach — the university remains accountable for the overseas recipient's handling
- OAIC engagement with no documented assessment to produce
- Platform decisions taken during this engagement may need reopening
- Student trust in the handling of their work and exam data

**Affected Stakeholders:**

- **Students**: their work, exam responses and recordings held offshore
- **Eleanor Frame**: holds the compliance accountability
- **Prof. Stella Groove**: institutional consequence
- **Grace Tanaka**: contractual remedies may not exist

**Related Objectives:**

- **Goal G-9** (Privacy positions assessed): this risk defines the gap
- **Outcome O-4** (Demonstrable privacy posture)

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 5 — Almost Certain | The disclosures are occurring now; the assessment gap is a present fact, not a possibility |
| **Impact** | 4 — Major | Regulatory exposure plus potential reopening of platform decisions |
| **Inherent Risk Score** | **20** (Critical) | 5 × 4 = 20 |

**Risk Zone:** 🟥 Critical (20–25)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Standard vendor contracts**: contain general data protection clauses
   - Owner: Grace Tanaka
   - Effectiveness: **Weak** — not verified against APP 8 accountability requirements
   - Evidence: none — clauses not reviewed for this purpose

2. **Hosting region now modelled as a governed attribute** (E-018, DR-005)
   - Owner: Sam Okafor
   - Effectiveness: **Adequate** — structure exists but is unpopulated
   - Evidence: ARC-001-DATA-v1.0

**Overall Control Effectiveness:** Weak — the data structure exists; the assessments do not.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | Assessment gap remains open; residual score reflects uncertainty rather than known unsafety |
| **Impact** | 4 — Major | Unchanged — contract clauses unverified |
| **Residual Risk Score** | **16** (High) | 4 × 4 = 16 |

**Risk Zone:** 🟧 High (13–19)
**Risk Reduction:** 20% (20 → 16)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:**
This is the cheapest score reduction available in the register. The risk is high because nobody has looked, not because the arrangements are known to be unsafe — completing the PIA may lower it substantially at the cost of assessment time alone.

#### Risk Appetite Assessment

**Provisional appetite for COMPLIANCE risks:** Low (≤ 9) — compliance exposure warrants a tighter threshold than delivery risk
**Current residual:** 16 (High)
**Assessment:** ❌ **Exceeds provisional appetite** by 7 points — the largest exceedance in the register
**Escalation Required:** Yes — Steering Committee immediately.

#### Action Plan

**Additional Mitigations Needed:**

1. **Complete the Privacy Impact Assessment across all 13 APPs**
   - Owner: Eleanor Frame
   - Due Date: 2026-08-28
   - Cost: within engagement scope
   - Expected Impact: reduce likelihood 4 → 2

2. **Capture and confirm hosting region for every platform**
   - Description: Populate E-018 `hosting_region` from vendor confirmation, not assumption
   - Owner: Grace Tanaka
   - Due Date: 2026-08-21
   - Cost: nil
   - Expected Impact: prerequisite for the above

3. **Review contractual accountability and breach notification clauses**
   - Owner: Grace Tanaka with Eleanor Frame
   - Due Date: 2026-09-30
   - Cost: legal review time
   - Expected Impact: reduce impact 4 → 3

**Target Residual Risk After Mitigations:** L2 × I3 = **6 (Medium)** ✅ within a Medium threshold; still above a Low compliance appetite, requiring formal acceptance

**Success Criteria:**

- Cross-border position documented and accepted for all four classes
- Practicability of an Australian-region alternative recorded, including where none exists

**Monitoring Plan:**

- **Frequency:** Fortnightly until PIA complete
- **Key Indicators:** data classes assessed (of 8); platforms with confirmed hosting region (of ~25)
- **Escalation Triggers:** PIA not complete by 2026-08-28

---

### Risk R-018: Sensitive placement information handled manually

**Category:** COMPLIANCE
**Status:** Open
**Risk Owner:** Eleanor Frame, Privacy & Records Officer
**Action Owner:** Prof. Priya Anand with Sam Okafor

#### Risk Identification

**Risk Description:**
Placement records contain clearance metadata and health-context notes — sensitive information under the Privacy Act 1988, attracting elevated protection. This data currently moves between systems by manual re-keying, with exports and screenshots circulating by email.

**Root Cause:**
The absence of INT-005 forced a manual bridge, and no handling controls were applied to compensate for the elevated sensitivity of the data crossing it.

**Trigger Events:**

- A mis-addressed email sends a placement grade sheet to an external distribution list
- A screenshot containing clearance metadata is shared in a group chat
- An export is retained on a shared drive without access control

**Consequences if Realized:**

- APP 11 breach involving **sensitive** information
- Likely eligible data breach under the NDB scheme — sensitive information substantially raises the serious-harm threshold likelihood
- OAIC notification plus individual notification to affected students
- Placement provider relationships damaged; accreditation exposure

**Affected Stakeholders:**

- **Students on placement**: sensitive personal information exposed
- **Eleanor Frame**: NDB assessment and notification accountability
- **Prof. Priya Anand**: faculty and provider relationships
- **Prof. Stella Groove**: institutional reputation

**Related Objectives:**

- **Goal G-9** (Privacy positions and breach readiness)
- **Outcome O-4** (Demonstrable privacy posture)

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | Manual handling of sensitive data at this volume, over years, makes an incident probable |
| **Impact** | 5 — Catastrophic | Sensitive information breach with NDB notification and regulatory engagement |
| **Inherent Risk Score** | **20** (Critical) | 4 × 5 = 20 |

**Risk Zone:** 🟥 Critical (20–25)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Staff awareness and care**
   - Owner: Health Sciences placement team
   - Effectiveness: **Weak** — diligence is not a control; it fails under workload
   - Evidence: none

**Overall Control Effectiveness:** Weak — this is the estate's most sensitive data flow and its only control is staff carefulness.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | Unchanged — no structural control |
| **Impact** | 4 — Major | Marginally reduced: existing records processes would support a rapid NDB response |
| **Residual Risk Score** | **16** (High) | 4 × 4 = 16 |

**Risk Zone:** 🟧 High (13–19)
**Risk Reduction:** 20% (20 → 16)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:**
The interim control (prohibit email and spreadsheet transfer) costs nothing and can be issued this month. The structural fix (INT-005) is already a Must requirement.

**Alternative Responses Considered:**

- **Tolerate**: Rejected — sensitive information with a live regulatory dimension
- **Transfer**: Considered — cyber insurance does not transfer the APP 11 obligation, only some financial consequence
- **Terminate**: Considered — suspending placements is disproportionate and academically damaging

#### Risk Appetite Assessment

**Provisional appetite for COMPLIANCE risks:** Low (≤ 9)
**Current residual:** 16 (High)
**Assessment:** ❌ **Exceeds provisional appetite** by 7 points
**Escalation Required:** Yes — immediate. This is the register's highest-priority item.

#### Action Plan

**Additional Mitigations Needed:**

1. **Issue an immediate handling instruction**
   - Description: Prohibit email, screenshot and spreadsheet transfer of placement records; route all transfers through the platform
   - Owner: Prof. Priya Anand with Eleanor Frame
   - Due Date: 2026-08-14
   - Cost: nil
   - Expected Impact: reduce likelihood 4 → 3

2. **Apply field-level access control to sensitive attributes**
   - Description: Restrict `clearance_metadata` and `health_context_notes` to authorised placement administrators only
   - Owner: Tobias Ohm with Learning Technologies
   - Due Date: 2026-10-31
   - Cost: configuration effort
   - Expected Impact: reduce impact 4 → 3

3. **Implement INT-005 (shared with R-008)**
   - Owner: Sam Okafor
   - Due Date: 2027-03-31
   - Expected Impact: reduce likelihood 3 → 1

4. **Complete the NDB response playbook and tabletop it**
   - Owner: Eleanor Frame
   - Due Date: 2026-09-30
   - Cost: nil
   - Expected Impact: reduces consequence severity, not score

**Target Residual Risk After Mitigations:** L1 × I3 = **3 (Low)** ✅ within provisional appetite

**Success Criteria:**

- Zero placement records transferred outside the governed integration
- NDB playbook tested by tabletop exercise

**Monitoring Plan:**

- **Frequency:** Monthly until INT-005 is live
- **Key Indicators:** manual transfer count; field-level access control in place (Y/N)
- **Escalation Triggers:** any suspected disclosure — 30-day NDB assessment clock starts on suspicion, not confirmation

---

### Risk R-021: Accessibility conformance unverified across the estate

**Category:** COMPLIANCE
**Status:** Open
**Risk Owner:** A/Prof. Pearl Clavinet, Dean of Learning & Teaching
**Action Owner:** Dr. Benny Moog, Director Learning Technologies

#### Risk Identification

**Risk Description:**
WCAG 2.2 AA conformance is a Must-priority requirement, but no student-facing platform has had its conformance independently verified. Vendor claims have been accepted without testing.

**Root Cause:**
Accessibility was not a weighted evaluation criterion at procurement, and no conformance register exists.

**Trigger Events:**

- A student using assistive technology cannot complete an assessment
- A formal accessibility complaint is lodged
- A platform is renewed without conformance evidence

**Consequences if Realized:**

- Students with disability disadvantaged in assessment — a fairness and equity failure
- Legal exposure under disability discrimination provisions
- Remediation cost incurred for the remaining contract term
- Reputational damage disproportionate to the technical defect

**Affected Stakeholders:**

- **Students with disability**: direct and immediate
- **Jazmin Field**: accessibility is her stated advocacy
- **A/Prof. Pearl Clavinet**: academic quality accountability

**Related Objectives:**

- **Goal G-10** (Accessibility conformance baseline)
- **Outcome O-5** (Consistent accessible student experience)

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | Across 20-plus platforms, unverified conformance means some are almost certainly non-conformant |
| **Impact** | 4 — Major | Student disadvantage with legal and reputational consequence |
| **Inherent Risk Score** | **16** (High) | 4 × 4 = 16 |

**Risk Zone:** 🟧 High (13–19)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Vendor conformance claims**: most vendors publish accessibility statements
   - Owner: Grace Tanaka
   - Effectiveness: **Weak** — claimed, not verified
   - Evidence: vendor documentation only

2. **Captioning available on capture platforms**
   - Owner: Learning Technologies
   - Effectiveness: **Adequate** for one dimension of conformance
   - Evidence: `captions_available` attribute in the data model

**Overall Control Effectiveness:** Weak to Adequate.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 — Possible | Major platforms likely broadly conformant; long tail is the exposure |
| **Impact** | 4 — Major | Unchanged |
| **Residual Risk Score** | **12** (Medium) | 3 × 4 = 12 |

**Risk Zone:** 🟨 Medium (6–12)
**Risk Reduction:** 25% (16 → 12)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

#### Risk Appetite Assessment

**Provisional appetite for COMPLIANCE risks:** Low (≤ 9)
**Current residual:** 12 (Medium)
**Assessment:** ⚠️ **Exceeds provisional appetite** by 3 points
**Escalation Required:** Report to Education Committee; not Steering-level escalation.

#### Action Plan

1. **Establish a conformance register with verified status per platform**
   - Owner: Dr. Benny Moog · Due: 2026-09-30 · Impact: likelihood 3 → 2
2. **Make accessibility a weighted criterion in all future evaluations**
   - Owner: Grace Tanaka · Due: 2026-09-30 · Impact: prevents recurrence
3. **Assign remediation owners and dates to identified gaps**
   - Owner: Dr. Benny Moog · Due: 2026-12-31 · Impact: impact 4 → 3

**Target Residual Risk:** L2 × I3 = **6 (Medium)** ✅

**Success Criteria:** conformance status verified for all student-facing platforms; every gap owned with a date.

---

### Consolidated Risk Profiles (R-002 to R-029)

> All mandatory Orange Book fields are present. Risks profiled in full above are omitted from this table.

| ID | Category | Title & Description | Root Cause | Inherent L/I/Score | Existing Controls (Effectiveness) | Residual L/I/Score | 4Ts | Owner | Key Action | Target Date | Target Score |
|----|----------|---------------------|------------|--------------------|-----------------------------------|--------------------|-----|-------|-----------|-------------|--------------|
| R-002 | STRATEGIC | **Strategy perceived as cost-cutting.** Academics read the rationalisation as budget-driven and the Education Committee declines to endorse the future state. | Principles and recommendations expressed in technical/financial terms without pedagogical framing | 4/4/**16** | Principles written in student and teaching outcome terms (Adequate); academic validation workshops planned (Adequate) | 2/3/**6** | Treat | A/Prof. Pearl Clavinet | Run principles validation with Castle, Field and discipline representatives before committee | 2026-08-14 | 4 |
| R-003 | STRATEGIC | **Survey influence nominal.** The 412-response survey visibly changes nothing; consultation credibility and future response rates fall. | WP7 mapping compressed under deadline pressure | 4/3/**12** | REQ Appendix E preserves REQ-xxx cross-reference (Strong) | 2/2/**4** | Treat | Dr. Felix Marimba | Publish requirement-to-recommendation traceability in the WP9 deliverable | 2026-08-31 | 2 |
| R-004 | STRATEGIC | **Deliverable misses 31 August or wrong format.** Roadmap does not reach the September business case in usable form. | Fixed deadline with dependencies on vendor and workshop availability | 3/5/**15** | Fortnightly steering (Adequate); WP dependency sequencing (Adequate) | 2/5/**10** | Treat | Rhonda Bell | Confirm business case format with Finance; draft WP9 directly into it | 2026-08-07 | 6 |
| R-005 | STRATEGIC | **Rationalisation not executable at contract timing.** Retirement decisions land mid-term where no exit provision exists, producing cost rather than saving. | Contract terms not aligned to architectural planning | 4/3/**12** | Procurement holds contract data (Adequate) | 3/3/**9** | Treat | Grace Tanaka | Build renewal calendar; align roadmap sequencing to renewal dates | 2026-08-21 | 6 |
| R-007 | OPERATIONAL | **Single-person dependency on cloning automation.** Course rollover runs on undocumented scripts held by one individual. | Automation built ad hoc without documentation or version control | 3/4/**12** | None effective | 3/4/**12** | Treat | Sam Okafor | Document and version-control the scripts; train a second operator | 2026-09-30 | 4 |
| R-009 | OPERATIONAL | **Casual and sessional provisioning by manual CSV.** Short-tenure staff receive access late or retain it after their engagement ends. | Automated provisioning path does not cover non-continuing staff | 5/3/**15** | Manual CSV process (Weak) | 4/3/**12** | Treat | Sam Okafor | Extend automated provisioning to casual and sessional basis (INT-003) | 2027-03-31 | 4 |
| R-010 | OPERATIONAL | **Specialist tool support model undefined.** Discipline tools have no named internal support arrangement. | Adopted at school level without central support agreement | 4/3/**12** | Informal school-level support (Weak) | 3/3/**9** | Treat | Dr. Benny Moog | Define and record a support model and owner per specialist tool | 2026-09-30 | 6 |
| R-011 | OPERATIONAL | **Vendor unresponsiveness blocks WP3.** Capability, contract and roadmap data not supplied within the timeline. | No commercial leverage outside renewal windows | 3/4/**12** | Procurement engagement from week one (Adequate) | 2/3/**6** | Treat | Grace Tanaka | Prioritise vendors with contracts falling due inside the roadmap horizon | 2026-08-07 | 4 |
| R-012 | OPERATIONAL | **Timeline compression degrades mapping depth.** WP7 reduces to desk analysis; coverage overstated. | Workshop-based method against a fixed date | 4/3/**12** | Week-one prioritisation (Adequate); explicit coverage statement committed (Strong) | 3/2/**6** | Treat | Rhonda Bell | State depth-analysis vs desk-review coverage explicitly in the deliverable | 2026-08-31 | 4 |
| R-013 | FINANCIAL | **Licence spend cannot be held flat.** Must-priority gaps cannot be closed within a flat envelope. | Capability gaps may require new acquisition | 4/4/**16** | Capability mapping will quantify unused licensed capability (Adequate) | 3/3/**9** | Treat | Vernon Ostinato | Quantify licensed-but-unconfigured capability before any acquisition is approved | 2026-08-21 | 6 |
| R-014 | FINANCIAL | **Integration uplift unfunded.** Capital for integration remediation is not approved, leaving requirements specified but undeliverable. | Rationalisation read as savings-only | 3/4/**12** | Business case separates recurring licence from one-off capital (Adequate) | 2/4/**8** | Treat | Cassandra Rhodes | Present integration investment with its own benefit case, sequenced by risk | 2026-08-31 | 6 |
| R-015 | FINANCIAL | **Exit provisions prevent planned retirement.** Contracts lack termination assistance, so retirement incurs cost. | Exit terms not negotiated at original procurement | 3/3/**9** | REQ-034 export requirement now specified (Adequate) | 2/3/**6** | Tolerate | Grace Tanaka | Accept for existing contracts; require exit terms at every renewal | 2027-06-30 | 6 |
| R-016 | FINANCIAL | **Licensed capability not realisable in practice.** Functionality paid for cannot be configured within the contract or support model. | Capability assumed available without verification | 3/3/**9** | WP3 capability mapping (Adequate) | 2/3/**6** | Treat | Dr. Benny Moog | Verify configurability, not just licensing, during capability mapping | 2026-08-21 | 4 |
| R-019 | COMPLIANCE | **Local accounts breach SSO/MFA requirement.** Two platforms permit local accounts, breaching REQ-031 directly. | Platforms adopted before the authentication standard was enforced | 5/3/**15** | SSO+MFA enforced across the rest of the estate (Strong) | 4/3/**12** | Treat | Tobias Ohm | Dated remediation plan per platform; no renewal without SSO capability | 2026-12-31 | 4 |
| R-020 | COMPLIANCE | **Essential Eight ML2 target missed.** Estate remains largely ML1 against an end-2027 ML2 target. | Lab fleets and capture appliances outside standard patching regimes | 4/3/**12** | Intune macro enforcement (Strong); SSO+MFA (Strong); partial browser hardening (Adequate) | 3/3/**9** | Treat | Tobias Ohm | Documented pathway per mitigation strategy with owners and dates | 2026-09-30 | 6 |
| R-022 | COMPLIANCE | **Analytics without retention or minimisation.** Engagement data extracted ad hoc with no deletion rules — APP 11.2 exposure. | Analytics grew organically without governance | 4/3/**12** | Data model now defines `retention_expires_at` and de-identification (Adequate) | 2/3/**6** | Treat | Eleanor Frame | Implement automated retention expiry on engagement data | 2027-06-30 | 4 |
| R-023 | REPUTATIONAL | **Notifiable data breach becomes public.** A breach involving sensitive placement data attracts media and regulator attention. | Manual handling of sensitive information (see R-018) | 3/5/**15** | Records processes support response (Adequate) | 2/5/**10** | Treat | Prof. Stella Groove | Complete and tabletop the NDB playbook; remediate R-018 | 2026-09-30 | 5 |
| R-024 | REPUTATIONAL | **Teaching platform outage during assessment.** Core platform unavailable during an examination window. | Vendor SLAs unverified; no change freeze in force | 3/4/**12** | Vendor SLAs exist but unverified (Weak) | 2/4/**8** | Treat | Cassandra Rhodes | Verify SLAs against NFR-A-001; define assessment-period change freezes | 2026-10-31 | 4 |
| R-025 | REPUTATIONAL | **Academic resistance prevents consistency outcome.** Template conformance is read as mandated rework and adoption stalls. | Consistency framed as compliance rather than effort reduction | 4/3/**12** | Castle involved in principles validation (Adequate); variation permitted and recorded (Adequate) | 3/2/**6** | Treat | A/Prof. Pearl Clavinet | Deliver rollover automation before requesting conformance | 2027-02-28 | 4 |
| R-026 | TECHNOLOGY | **Vendor platforms cannot support event-driven integration.** Target architecture proves undeliverable against SaaS interface limits. | Interface capability not assessed before requirements were set | 4/4/**16** | None — capability unassessed | 3/4/**12** | Treat | Sam Okafor | Assess interface capability per platform during WP3; record batch exceptions with review dates | 2026-08-21 | 6 |
| R-027 | TECHNOLOGY | **External supervisor authentication gap.** Institutional SSO does not reach placement providers, so NFR-SEC-001 cannot be met for E-015. | Identity provider scope stops at the institutional boundary | 4/3/**12** | Time-bounded authorisation status modelled (Adequate) | 3/3/**9** | Treat | Tobias Ohm | Decide federation vs formally approved compensating exception at RIFF | 2026-10-31 | 6 |
| R-028 | TECHNOLOGY | **Export capability unverified.** Backup and export coverage unverified for four platforms; substitution may be impossible. | Export claimed contractually, never tested | 4/4/**16** | Contract terms assert export (Weak) | 3/3/**9** | Treat | Grace Tanaka | Test export by extraction on all four platforms | 2026-10-31 | 4 |
| R-029 | TECHNOLOGY | **Vendor lock-in via proprietary formats.** Export exists but only in formats requiring vendor tooling, defeating portability. | Open-format requirement not specified at original procurement | 3/4/**12** | REQ-034 and NFR-I-002 now specify open formats (Adequate) | 2/3/**6** | Tolerate | Grace Tanaka | Accept for existing contracts; require open formats at renewal | 2027-06-30 | 6 |

---

## D. Risk Category Analysis

### STRATEGIC Risks (5)

**Average inherent:** 15.0 · **Average residual:** 9.0 · **Reduction:** 40%

**Key themes:** Every strategic risk is a *decision or perception* risk rather than a delivery risk. R-001 needs a decision; R-002 and R-003 need framing and visible traceability; R-004 needs format confirmation; R-005 needs calendar alignment. None is solved by additional analysis, which is worth stating because the instinct on a consultancy engagement is to analyse.

**Highest:** R-001 (16) — the only strategic risk exceeding provisional appetite.

### OPERATIONAL Risks (7)

**Average inherent:** 14.7 · **Average residual:** 10.9 · **Reduction:** 26%

**Key themes:** The weakest reduction of any category, and for a structural reason — these are pre-existing estate conditions with no effective controls. R-006, R-007, R-008 and R-009 all describe manual or fragile processes that have run for years. Control effectiveness is rated Weak in every case because the current control is human diligence.

**Highest:** R-008 (16), R-006 (15) — both exceed provisional appetite.

### FINANCIAL Risks (4)

**Average inherent:** 11.5 · **Average residual:** 7.2 · **Reduction:** 37%

**Key themes:** The best-controlled category, largely because the controls are analytical rather than operational — capability mapping and cost separation reduce these risks without capital expenditure. R-015 and R-029 are tolerated for existing contracts with treatment applied at renewal, which is the only practical response to terms already signed.

**Highest:** R-013 (9) — within appetite.

### COMPLIANCE Risks (6)

**Average inherent:** 15.8 · **Average residual:** 11.8 · **Reduction:** 25%

**Key themes:** The highest average inherent score in the register and the source of both top-ranked risks. The pattern is uniform — obligations exist, the estate has not been assessed against them, and the residual scores reflect *unmeasured* exposure. R-017 in particular may fall sharply once the PIA is complete; it is high because nobody has looked.

**Highest:** R-018 (16), R-017 (16) — the two largest appetite exceedances in the register.

### REPUTATIONAL Risks (3)

**Average inherent:** 13.0 · **Average residual:** 8.0 · **Reduction:** 38%

**Key themes:** All three are consequences of risks in other categories rather than independent causes — R-023 follows R-018, R-024 follows R-006, R-025 follows the NFR-U-001 conformance requirement. Treating the upstream risk treats these.

**Highest:** R-023 (10) — within appetite but carries the highest single impact rating (5).

### TECHNOLOGY Risks (4)

**Average inherent:** 14.0 · **Average residual:** 9.0 · **Reduction:** 36%

**Key themes:** Three of four are *assumption* risks — the architecture assumes vendor platforms can do things nobody has verified (event-driven interfaces, export, federation). These are cheap to reduce through assessment during WP3 and expensive to discover later.

**Highest:** R-026 (12) — within appetite but load-bearing for the entire integration architecture.

---

## E. Risk Ownership Matrix

| Stakeholder | Role | Owned Risks | High Risks | Notes |
|-------------|------|-------------|------------|-------|
| Eleanor Frame | Privacy & Records Officer | R-017, R-018, R-022 | 2 | **Heaviest concentration of High risk in the register.** Both top-ranked risks sit with a MEDIUM-influence stakeholder — a governance mismatch worth noting. |
| Sam Okafor | Integration Architect | R-007, R-009, R-026 | 0 | Three operational/technology risks; all remediated by the same integration programme |
| Grace Tanaka | Procurement & Vendor Manager | R-005, R-011, R-015, R-028, R-029 | 0 | Largest count; all contract-timing or verification risks |
| Tobias Ohm | Cybersecurity Lead | R-019, R-020, R-027 | 0 | Security posture cluster |
| Cassandra Rhodes | Chief Information Officer | R-006, R-014, R-024 | 1 | Accountable for the estate's largest operational risk |
| A/Prof. Pearl Clavinet | Dean of L&T | R-002, R-021, R-025 | 0 | Academic governance and accessibility |
| Rhonda Bell | Project Manager | R-004, R-012 | 0 | Delivery risks |
| Prof. Otis Hammond | DVC (Education) | R-001 | 1 | Owns the register's single strategic High risk |
| Prof. Priya Anand | Dean of Health Sciences | R-008 | 1 | Placement integrity |
| Dr. Benny Moog | Director Learning Technologies | R-010, R-016 | 0 | Capability and support model |
| Vernon Ostinato | Chief Financial Officer | R-013 | 0 | Licence spend |
| Dr. Felix Marimba | Academic Lead | R-003 | 0 | Survey credibility |
| Prof. Stella Groove | Vice-Chancellor | R-023 | 0 | Institutional reputation |

**Governance observation:** Eleanor Frame owns both of the register's top two risks but holds MEDIUM influence in the stakeholder analysis. Ownership should be paired with an escalation right — the Steering Committee should hear directly from Privacy on R-017 and R-018 rather than through the CIO line.

---

## F. 4Ts Response Framework Summary

| Response | Count | % | Examples |
|----------|-------|---|----------|
| **Tolerate** | 2 | 7% | R-015 (exit provisions on signed contracts), R-029 (proprietary formats on existing terms) |
| **Treat** | 27 | 93% | R-001, R-006, R-008, R-017, R-018 and all others |
| **Transfer** | 0 | 0% | None — see note below |
| **Terminate** | 0 | 0% | None |

**Note on Transfer:** Cyber insurance was considered for R-018 and R-023 and rejected as a *primary* response. Insurance transfers financial consequence but not the APP 11 obligation or the NDB notification duty — the university remains accountable regardless. Recommending Transfer here would misrepresent what insurance achieves. It may still be worth holding as a secondary financial control, which is a Finance decision rather than an architectural one.

**Note on the Treat concentration:** 93% Treat is high and reflects that most risks here are remediable estate defects rather than accepted trade-offs. A mature register would show more Tolerate as controls bed in and residual scores fall within appetite.

---

## G. Risk Appetite Compliance

> ⚠️ **No approved risk appetite statement exists.** The thresholds below are **PROVISIONAL** — proposed by this register for Executive endorsement, not derived from an existing institutional position. Until endorsed, every "exceeds appetite" judgement is an architectural recommendation.

**Proposed thresholds:**

| Category | Proposed Threshold | Rationale |
|----------|-------------------|-----------|
| STRATEGIC | Medium (≤ 12) | Strategic ambiguity is tolerable for bounded periods with decision deadlines |
| OPERATIONAL | Medium (≤ 12) | Teaching continuity matters but manual workarounds provide fallback |
| FINANCIAL | Medium (≤ 12) | Licence spend is material but not existential |
| COMPLIANCE | **Low (≤ 9)** | Regulatory obligations are not discretionary; a tighter threshold is warranted |
| REPUTATIONAL | Medium (≤ 12) | Reputation recovers; institutional standing is resilient to operational failure |
| TECHNOLOGY | Medium (≤ 12) | Technical assumptions can be verified cheaply during WP3 |

**Compliance against proposed thresholds:**

| Category | Threshold | Within | Exceeding | Action Required |
|----------|-----------|--------|-----------|-----------------|
| STRATEGIC | 12 | 4 | 1 (R-001) | Steering Committee decision deadline |
| OPERATIONAL | 12 | 5 | 2 (R-006, R-008) | Steering escalation; interim controls |
| FINANCIAL | 12 | 4 | 0 | None |
| COMPLIANCE | 9 | 3 | 3 (R-017, R-018, R-021) | Immediate escalation for R-017 and R-018 |
| REPUTATIONAL | 12 | 3 | 0 | None |
| TECHNOLOGY | 12 | 4 | 0 | None |

**Recommendation:** Endorse these thresholds at the Steering Committee, or substitute institutional ones. Without an agreed appetite, "exceeds appetite" carries no governance weight and the escalations above have no formal trigger.

---

## H. Prioritised Action Plan

### Priority 1: URGENT — Exceeds appetite, live exposure

| # | Action | Risks | Owner | Due | Status |
|---|--------|-------|-------|-----|--------|
| 1 | Issue handling instruction prohibiting email, screenshot and spreadsheet transfer of placement records | R-018, R-008, R-023 | Prof. Priya Anand / Eleanor Frame | 2026-08-14 | Not started |
| 2 | Publish platform decision criteria before options are scored | R-001 | Dr. Benny Moog / Cassandra Rhodes | 2026-08-07 | Not started |
| 3 | Set hard decision deadline protecting WP8 | R-001 | Prof. Otis Hammond | 2026-08-07 | Not started |
| 4 | Confirm hosting region per platform from vendor, not assumption | R-017 | Grace Tanaka | 2026-08-21 | Not started |
| 5 | Complete Privacy Impact Assessment across all 13 APPs | R-017, R-018, R-022 | Eleanor Frame | 2026-08-28 | Not started |

### Priority 2: HIGH — Within appetite but load-bearing

| # | Action | Risks | Owner | Due | Status |
|---|--------|-------|-------|-----|--------|
| 6 | Confirm business case format with Finance; draft WP9 into it directly | R-004 | Rhonda Bell | 2026-08-07 | Not started |
| 7 | Assess vendor interface capability for event-driven integration | R-026 | Sam Okafor | 2026-08-21 | Not started |
| 8 | Quantify licensed-but-unconfigured capability | R-013, R-016 | Dr. Benny Moog | 2026-08-21 | Not started |
| 9 | Build contract renewal calendar aligned to the roadmap | R-005, R-015 | Grace Tanaka | 2026-08-21 | Not started |
| 10 | Define target integration architecture and canonical model | R-006, R-008, R-009 | Sam Okafor | 2026-08-28 | In progress |
| 11 | Run principles validation with academic and student representatives | R-002, R-025 | A/Prof. Pearl Clavinet | 2026-08-14 | Not started |

### Priority 3: MEDIUM — Scheduled treatment

| # | Action | Risks | Owner | Due | Status |
|---|--------|-------|-------|-----|--------|
| 12 | Complete and tabletop the NDB response playbook | R-023, R-018 | Eleanor Frame | 2026-09-30 | Not started |
| 13 | Document and version-control cloning automation; train a second operator | R-007 | Sam Okafor | 2026-09-30 | Not started |
| 14 | Essential Eight pathway per mitigation strategy with owners and dates | R-020 | Tobias Ohm | 2026-09-30 | Not started |
| 15 | Define support model per specialist tool | R-010 | Dr. Benny Moog | 2026-09-30 | Not started |
| 16 | Establish accessibility conformance register | R-021 | Dr. Benny Moog | 2026-09-30 | Not started |
| 17 | Test export by extraction on the four unverified platforms | R-028 | Grace Tanaka | 2026-10-31 | Not started |
| 18 | Decide external supervisor federation vs compensating exception | R-027 | Tobias Ohm | 2026-10-31 | Not started |
| 19 | Apply field-level access control to sensitive placement attributes | R-018 | Tobias Ohm | 2026-10-31 | Not started |
| 20 | Verify vendor SLAs; define assessment-period change freezes | R-024 | Cassandra Rhodes | 2026-10-31 | Not started |
| 21 | Dated remediation plan for local-account platforms | R-019 | Tobias Ohm | 2026-12-31 | Not started |
| 22 | Implement INT-005 placement-to-gradebook synchronisation | R-008, R-018 | Sam Okafor | 2027-03-31 | Not started |
| 23 | Extend automated provisioning to casual and sessional staff | R-009 | Sam Okafor | 2027-03-31 | Not started |
| 24 | Deliver rollover automation before requesting template conformance | R-025 | Dr. Benny Moog | 2027-02-28 | Not started |
| 25 | Implement automated retention expiry on engagement data | R-022 | Eleanor Frame | 2027-06-30 | Not started |

---

## I. Integration with the September Business Case

The engagement feeds a business case rather than producing one. This register supports it as follows:

**Strategic case** — R-006, R-008 and R-017 evidence the urgency. The integration estate is not merely inefficient; it carries live compliance exposure. That is the strongest available argument for investment now rather than at the next planning cycle.

**Economic case** — R-013 and R-014 bound the financial options. Risk-adjusted costing should reflect that integration capital is not offset by licence savings in the same period, and that R-015 constrains when savings can actually be realised.

**Commercial case** — R-005, R-015, R-028 and R-029 all bear on contract strategy. Exit terms, verified export and open formats should be standing requirements at every renewal, not project-specific asks.

**Management case** — this register in full, with the Section H action plan as the risk management approach and Section J as the monitoring framework.

**Recommendation influence** — R-001 must be resolved *before* the business case, not within it. Presenting the Executive with an unresolved platform question invites it to be settled on cost, without pedagogical input.

---

## J. Monitoring and Review Framework

### Review Schedule

| Risk Level | Frequency | Forum |
|------------|-----------|-------|
| High (13–19) | Monthly | Steering Committee |
| Medium (6–12) | Quarterly | Project working group |
| Low (1–5) | Six-monthly | Register review only |
| Appetite exceedances | Every meeting until within threshold | Steering Committee |

### Key Risk Indicators

| KRI | Risk | Threshold | Owner |
|-----|------|-----------|-------|
| Placement records transferred outside the governed path | R-018, R-008 | Any occurrence | Prof. Priya Anand |
| Data classes with completed APP 8 assessment | R-017 | Below 8 of 8 by 2026-08-28 | Eleanor Frame |
| Days R-001 remains undecided | R-001 | Beyond 2026-08-21 | Prof. Otis Hammond |
| Integration failures detected by user report | R-006 | Any occurrence once monitoring is live | Sam Okafor |
| Platforms permitting local accounts | R-019 | Above 0 after 2026-12-31 | Tobias Ohm |
| Student-facing platforms with unverified accessibility | R-021 | Above 0 after 2026-09-30 | Dr. Benny Moog |

### Escalation Criteria

- Any risk increasing by 3 or more points between reviews
- Any new risk scoring 16 or above on first assessment
- Any Priority 1 action slipping beyond its due date
- Any suspected disclosure of sensitive information — the NDB 30-day assessment clock starts on **suspicion**, not confirmation
- Any risk exceeding the endorsed appetite for two consecutive review cycles

### Reporting Requirements

| Audience | Frequency | Content |
|----------|-----------|---------|
| Steering Committee | Fortnightly | Appetite exceedances, Priority 1 action status |
| Education Committee | Per meeting | Academic and accessibility risks (R-002, R-021, R-025) |
| Operations Committee | Quarterly | Financial and operational profile |
| University Executive | At business case | Full register summary with appetite position |

### Register Maintenance

**Register owner:** Rhonda Bell, Project Manager, through to 31 August 2026. **Handover required** — post-engagement ownership must transfer to a named institutional owner, recommended as Dr. Benny Moog with Digital & IT. An unowned register after the consultant leaves is the most common failure mode for engagements of this shape.

---

## K. Orange Book Compliance Checklist

### Part I — Risk Management Principles

| Principle | Status | Evidence |
|-----------|--------|----------|
| **A. Governance and Leadership** | ✅ | Every risk has a named owner drawn from the STKE RACI; escalation path follows the RIFF governance structure |
| **B. Integration** | ✅ | Risks trace to stakeholder goals (G-x) and outcomes (O-x); Section I links to the business case |
| **C. Collaboration** | ✅ | Risks sourced from documented stakeholder conflicts, the integration landscape assessment, and the privacy context |
| **D. Risk Management Processes** | ✅ | Systematic identification across six categories, inherent/residual assessment, 4Ts response, action plan, monitoring |
| **E. Continual Improvement** | ⚠️ Partial | Review framework defined; **no baseline for trend comparison** — this is v1.0 |

### Part II — Risk Control Framework

| Pillar | Status | Notes |
|--------|--------|-------|
| **Risk appetite** | ⚠️ **Provisional only** | No approved institutional statement exists; thresholds proposed for endorsement |
| **Risk culture** | ⚠️ Partial | Weak control effectiveness across the estate suggests risk has been managed informally |
| **Risk assessment** | ✅ | Consistent 5×5 scales applied throughout |
| **Risk response** | ✅ | 4Ts applied with rationale and alternatives considered |

---

## Appendix A: Risk Assessment Scales

### Likelihood Scale

| Rating | Descriptor | Probability |
|--------|------------|-------------|
| 1 | Rare | < 5% |
| 2 | Unlikely | 5–25% |
| 3 | Possible | 25–50% |
| 4 | Likely | 50–75% |
| 5 | Almost Certain | > 75% |

### Impact Scale

| Rating | Descriptor | Description |
|--------|------------|-------------|
| 1 | Negligible | Absorbed without management attention |
| 2 | Minor | Manageable within existing capacity |
| 3 | Moderate | Requires management effort and rescheduling |
| 4 | Major | Threatens objectives; students or staff materially affected |
| 5 | Catastrophic | Regulatory notification, institutional consequence, or deliverable failure |

### Risk Score Matrix

| | I=1 | I=2 | I=3 | I=4 | I=5 |
|---|---|---|---|---|---|
| **L=5** | 5 | 10 | 15 | 20 | 25 |
| **L=4** | 4 | 8 | 12 | 16 | 20 |
| **L=3** | 3 | 6 | 9 | 12 | 15 |
| **L=2** | 2 | 4 | 6 | 8 | 10 |
| **L=1** | 1 | 2 | 3 | 4 | 5 |

🟩 Low 1–5 · 🟨 Medium 6–12 · 🟧 High 13–19 · 🟥 Critical 20–25

---

## Appendix B: Stakeholder-Risk Linkage

Traceability from stakeholder driver through to mitigation, per Orange Book Principle B:

| Stakeholder | Driver (STKE) | Concern | Risk | Owner | Mitigation | Success Criterion |
|-------------|---------------|---------|------|-------|------------|-------------------|
| Cassandra Rhodes | SD-2 — eliminate fragility, reach ML2 | Integration estate unsustainable | R-006 | Rhodes | Target integration architecture + monitoring | Propagation within 15 min at p95 |
| Dr. Benny Moog | SD-6 — protect pedagogical fit | Consolidation decided on cost alone | R-001 | Hammond | Criteria published before scoring | Decision recorded with rationale |
| Eleanor Frame | SD-11 — APP compliance and breach readiness | Sensitive data handled manually | R-018 | Frame | Handling instruction + INT-005 | Zero transfers outside governed path |
| Eleanor Frame | SD-11 — cross-border accountability | Offshore disclosure unassessed | R-017 | Frame | Complete PIA across 13 APPs | Position recorded for all 4 classes |
| Prof. Priya Anand | SD-14 — placement integrity | Grades re-keyed by hand | R-008 | Anand | INT-005 bidirectional sync | Zero manual entries |
| Vernon Ostinato | SD-3 — contain licence spend | Flat envelope unachievable | R-013 | Ostinato | Quantify unused licensed capability | Costed position in business case |
| Jazmin Field | SD-16 — consistency and accessibility | Conformance unverified | R-021 | Clavinet | Conformance register | All student-facing platforms assessed |
| Dr. Felix Marimba | SD-8 — survey must matter | Mapping compressed | R-003 | Marimba | Published traceability in WP9 | REQ-xxx visible in recommendations |
| Dr. Wynton Castle | SD-15 — do not add workload | Conformance as mandated rework | R-025 | Clavinet | Automation delivered before conformance asked | Rollover self-service adopted |
| Tobias Ohm | SD-10 — close security gaps | Local accounts persist | R-019 | Ohm | Dated remediation per platform | Zero local accounts |
| Grace Tanaka | SD-12 — leverage at renewal | Exit provisions absent | R-015, R-028 | Tanaka | Renewal calendar + export testing | Export verified by test |
| Rhonda Bell | SD-9 — deliver 31 August | Timeline vs depth | R-012 | Bell | Explicit coverage statement | Deliverable states depth vs desk review |

---

## Document Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Risk Register Owner | Rhonda Bell, Project Manager | | |
| Executive Sponsor | Prof. Otis Hammond, DVC (Education) | | |
| Technical Authority | Cassandra Rhodes, Chief Information Officer | | |
| Privacy Authority | Eleanor Frame, Privacy & Records Officer | | |

---

## Next Steps

1. **Escalate R-017 and R-018 to the Steering Committee** at the next fortnightly meeting — both are live compliance exposures predating this engagement.
2. **Issue the placement handling instruction** (Priority 1, action 1). Costs nothing, can be done this week, and reduces the register's highest risk immediately.
3. **Endorse or replace the provisional risk appetite thresholds** — without an agreed appetite the escalations have no formal trigger.
4. **Set the R-001 decision deadline** so WP8 is not blocked.
5. **Name a post-engagement register owner** before 31 August.
6. Run `/arckit:au-pia` — it discharges the largest single action in this register.

---

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RK-D1 | ARC-001-STKE-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/` | Stakeholder drivers, conflicts, RACI — source of risk owners |
| RK-D2 | ARC-001-REQ-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/` | Requirements and documented risk section |
| RK-D3 | ARC-001-DATA-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/` | Data model — privacy exposure and governance registers |
| RK-D4 | ARC-000-PRIN-v1.0.md | ArcKit artifact | `projects/000-global/` | Architecture principles — non-compliance risks |
| RK-D5 | privacy-context.md | Compliance input | `projects/001-lt-ecosystem/external/` | PI inventory, data flows, Essential Eight self-assessment |
| RK-D6 | system-landscape.md | Foundation artifact | `projects/001-lt-ecosystem/external/` | Known integrations and current-state defects |
| RK-D7 | consultant-brief.md | Engagement brief | `projects/001-lt-ecosystem/external/` | Work packages, deadline, assumptions |
| RK-D8 | solution-governance-process.md | Global policy | `projects/000-global/policies/` | RIFF Review — escalation path |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| RK-C1 | RK-D6 | Known integrations | Current state | "Fragile; role assignment failures; no intra-day sync"; "Manual workaround for casual academic staff"; "Undocumented; single-person dependency"; "Drift between PeopleSoft and Blackboard hierarchies"; "Error-prone; audit concerns" |
| RK-C2 | RK-D5 | §1 | Privacy | "APP 8 triggers: classes 3, 4 (partial), 6 and 7 involve offshore disclosure under the assumed hosting" |
| RK-C3 | RK-D5 | §1 | Privacy | Row 5 of the inventory: "Placement records (incl. clearance metadata, health-context notes)" classified "Sensitive information" |
| RK-C4 | RK-D5 | §2 | Privacy | "Human error; screenshots/exports circulating via email"; "Flat-files at rest on shared storage; stale de-provisioning (access persists up to 24h after withdrawal)"; "No defined retention or minimisation rules" |
| RK-C5 | RK-D5 | §3 | Security | Target "ML2 across the SaaS-heavy L&T estate by end 2027"; MFA row: "two tools still allow local accounts (breaches REQ-031)"; backups row: "SaaS export coverage unverified for 4 tools" |
| RK-C6 | RK-D1 | Engagement notes | Conflict | "Known tension: Rhodes (CIO) favours Microsoft-platform consolidation (Teams/Stream); Moog and Key defend best-of-breed pedagogy tools" |
| RK-C7 | RK-D7 | Header, §2 | Constraint | "Due date: 31 August 2026"; "structured to feed directly into the September business case" |
| RK-C8 | RK-D5 | §4 | Privacy | "a mis-keyed Sonia export emails a placement grade sheet — including sensitive clearance metadata — to an external supervisor distribution list" |
| RK-C9 | RK-D8 | Process flow | Governance | Education Committee, Operations Committee and University Executive approval path via the RIFF Review |
| RK-C10 | RK-D6 | Notes | Context | Investigations outstanding for badging software, Articulate 360 licensing, Kuracloud support model, MuseScore and Ableton Live usage |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| ARC-001-REQ-v1.0.md (RK-D2) | `projects/001-lt-ecosystem/` | Requirement IDs referenced throughout; no verbatim passage quoted |
| ARC-001-DATA-v1.0.md (RK-D3) | `projects/001-lt-ecosystem/` | Entity IDs referenced throughout; no verbatim passage quoted |
| ARC-000-PRIN-v1.0.md (RK-D4) | `projects/000-global/` | Principles referenced by number; no verbatim passage quoted |

---

**Generated by**: ArcKit `/arckit:risk` command
**Generated on**: 2026-07-27
**ArcKit Version**: 6.4.0
**Project**: Learning & Teaching Baseline Strategy (Project 001)
**AI Model**: Claude Opus 5 (1M context)

<!-- arckit-provenance:start -->

## Build Provenance

_Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix._

| Field | Value |
|-------|-------|
| Requested Effort | `high` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-07-27T00:35:27.078Z |

<!-- arckit-provenance:end -->
