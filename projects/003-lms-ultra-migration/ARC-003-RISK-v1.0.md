# Risk Register: LMS Ultra Migration & Integration Modernisation

> **Template Origin**: Official | **ArcKit Version**: 6.7.4 | **Command**: `/arckit:risk`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-003-RISK-v1.0 |
| **Document Type** | Risk Register (HM Treasury Orange Book 2023) |
| **Project** | LMS Ultra Migration & Integration Modernisation (Project 003) |
| **Classification** | OFFICIAL-SENSITIVE |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-29 |
| **Last Modified** | 2026-07-29 |
| **Review Cycle** | Monthly (Critical/High), Quarterly (Medium/Low) |
| **Next Review Date** | 2026-08-29 |
| **Owner** | Rhonda Bell, Project Manager — L&T Baseline Strategy |
| **Reviewed By** | [PENDING] — Sam Okafor, Integration Architect |
| **Approved By** | [PENDING] — Prof. Otis Hammond, Executive Sponsor |
| **Distribution** | Steering Committee, Project Team, Digital & IT, Privacy & Records, Cybersecurity |

> **Classification rationale**: This register enumerates unremediated privacy and security weaknesses in the integration estate, identifies live compliance exposures during data migration, and states how long they will remain open. It names affected platforms, quantifies financial exposure in AUD, and describes data-migration privacy controls that are not yet in place. Classified OFFICIAL-SENSITIVE and restricted to the steering and delivery group.

> **Framework note**: The Orange Book is HM Treasury guidance for UK Government. The University of Funk is an Australian institution and is not bound by it. It is applied here as a **methodology** — 4Ts, inherent/residual scoring, appetite thresholds — because it is a sound and widely recognised risk framework, not because it is a compliance obligation. UK-specific risk categories (parliamentary scrutiny, NAO, PAC, GDS assessment, HMT spending controls) are **not applicable** and have been omitted rather than translated. Monetary values are AUD. The applicable regulatory overlay is the Privacy Act 1988 (Cth), the Notifiable Data Breaches scheme, and the ASD Essential Eight.

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-29 | ArcKit AI | Initial creation from `/arckit:risk` command | [PENDING] | [PENDING] |

---

## Executive Summary

### Risk Profile Overview

| Metric | Value |
|--------|-------|
| **Total risks identified** | 22 |
| **Critical (20–25)** | 0 residual (1 inherent) |
| **High (13–19)** | 2 residual (7 inherent) |
| **Medium (6–12)** | 17 residual (14 inherent) |
| **Low (1–5)** | 3 residual (0 inherent) |
| **Total inherent score** | 286 |
| **Total residual score** | 199 |
| **Overall risk reduction** | 30% |
| **Risks exceeding provisional appetite** | 4 (+ 3 at threshold) |
| **Risks with named owner** | 22 of 22 (100%) |

### Risk Category Distribution

| Category | Count | Avg Inherent | Avg Residual | Reduction |
|----------|-------|--------------|--------------|-----------|
| STRATEGIC | 4 | 14.0 | 9.8 | 30% |
| OPERATIONAL | 6 | 11.5 | 8.5 | 26% |
| FINANCIAL | 3 | 12.0 | 5.7 | 53% |
| COMPLIANCE | 4 | 16.0 | 14.0 | 12% |
| REPUTATIONAL | 2 | 12.0 | 8.0 | 33% |
| TECHNOLOGY | 3 | 12.3 | 6.7 | 46% |

### Overall Risk Assessment

**CONCERNING** — but structurally addressable.

No residual risk reaches Critical. However, **two risks remain High after existing controls** (R-014 and R-015, both compliance), and both have essentially no effective control in place today. The pattern is familiar from the Project 001 risk register: this is not a project with novel risks, it is the **same estate** with the same defects, now under the pressure of a concurrent migration and integration re-engineering. The migration amplifies risks that have been tolerated for years by adding time pressure, dual-running complexity, and a vendor dependency.

The 30% inherent-to-residual reduction is modest and deliberately so. The Project 001 register achieved 32% and was candid about why. Several current "controls" remain manual diligence and vendor promises — neither of which the Orange Book would rate above Weak. Inflating the reduction would require crediting controls that exist on paper but have never been tested.

**The distinctive risk shape of this project**: unlike Project 001 (which assessed an estate), Project 003 is delivering change to that estate while it is in production. This means every inherited risk now has a time dimension — there is a window during which the risk is actively worse than baseline (dual-running, temporary data copies, incomplete migration) before it improves.

### Risks Exceeding Appetite

> **No approved organisational risk appetite statement exists.** The thresholds used here are the same PROVISIONAL thresholds proposed in ARC-001-RISK-v1.0, which remain unendorsed. Every "exceeds appetite" judgement is an architectural recommendation, not a governance finding.

Four risks exceed the provisional thresholds; three more sit at the threshold:

| Risk | Category | Residual | Provisional Threshold | Over By |
|------|----------|----------|----------------------|---------|
| R-014 | COMPLIANCE | 16 | 9 | +7 |
| R-015 | COMPLIANCE | 16 | 9 | +7 |
| R-016 | COMPLIANCE | 12 | 9 | +3 |
| R-017 | COMPLIANCE | 12 | 9 | +3 |
| R-001 | STRATEGIC | 12 | 12 | at threshold |
| R-004 | STRATEGIC | 12 | 12 | at threshold |
| R-005 | OPERATIONAL | 12 | 12 | at threshold |

### Top 5 Risks Requiring Immediate Attention

1. **R-014 (COMPLIANCE, 16)** — Data migration creates temporary PI exposure: bulk export of student data from Learn Original with no privacy controls in place for the migration environment. Owner: Eleanor Frame.
2. **R-015 (COMPLIANCE, 16)** — Manual PI flows replicated "temporarily" and never remediated: the estate's most predictable failure mode. Owner: Eleanor Frame.
3. **R-005 (OPERATIONAL, 12)** — Integration team overwhelmed by dual-running: maintaining seven fragile integrations while building their replacements. At appetite threshold. Owner: Sam Okafor.
4. **R-001 (STRATEGIC, 12)** — Migration disruption undermines programme credibility: a teaching-period incident attributed to this project discredits Projects 004+ and the entire L&T strategy. At appetite threshold. Owner: Prof. Otis Hammond.
5. **R-016 (COMPLIANCE, 12)** — Ultra SSO/MFA configuration incomplete at go-live: local accounts persist on the platform that was supposed to close the security gap. Exceeds compliance appetite. Owner: Tobias Ohm.

### Key Findings and Recommendations

**Finding 1 — Four of the top five risks are inherited estate defects amplified by the migration, not new risks introduced by it.** R-005 (dual-running), R-014 (PI exposure), R-015 (manual flows) and R-002 (ADR-002) all describe conditions documented in ARC-001-RISK-v1.0. The migration does not create them — it creates a window during which they are worse, and a deadline by which they must be resolved. This distinction matters for accountability: the risks belong to the estate, not to the project.

**Finding 2 — R-014 and R-015 are the same defect from two angles.** R-014 is the compliance risk of creating new PI exposure during migration. R-015 is the compliance risk of failing to eliminate existing PI exposure after migration. Together they say: the migration must not make the privacy position worse, and it must make it better. The treatment is one work stream — data migration privacy controls — but the register carries both because they have different triggers, different owners, and different timelines.

**Finding 3 — R-005 is the project's single most consequential operational risk, and the only structural mitigation is money.** Okafor's team cannot maintain seven old integrations and build seven new ones simultaneously. No sequencing trick avoids this — it can only be mitigated by additional capacity (staff or vendor professional services) or by narrowing Phase 1 scope. The capacity plan must be approved and funded before migration commences.

**Finding 4 — Three risks (R-012, R-020, R-021) are verification risks that are cheap to reduce.** They score Medium or High because nobody has checked. Checking — API capability assessment, PeopleSoft event publication testing, rollback testing — costs time and effort but no capital, and may lower the scores substantially. These are the cheapest reductions available.

**Recommendation**: Escalate R-014 and R-015 to the Steering Committee at the next fortnightly meeting. Both are live compliance exposures — R-015 predates this project, and R-014 will materialise the moment data migration begins. Approve the integration team capacity plan (R-005) before any migration phase commences.

---

## A. Risk Matrix Visualization

### Inherent Risk Matrix (Before Controls)

```text
                                          IMPACT
                1-Negligible  2-Minor    3-Moderate   4-Major     5-Catastrophic
              ┌────────────┬────────────┬────────────┬────────────┬────────────┐
 5-Almost     │            │            │  R-005     │            │            │
   Certain    │            │            │            │            │            │
              │     5      │     10     │     15     │     20     │     25     │
              ├────────────┼────────────┼────────────┼────────────┼────────────┤
 4-Likely     │            │            │  R-003     │  R-001     │  R-014     │
              │            │            │  R-007     │  R-002     │            │
 L            │            │            │  R-008     │  R-012     │            │
 I            │            │            │  R-009     │  R-015     │            │
 K            │            │            │  R-010     │  R-016     │            │
 E            │            │            │  R-011     │  R-020     │            │
 L            │            │            │  R-013     │            │            │
 I            │     4      │     8      │     12     │     16     │     20     │
 H            ├────────────┼────────────┼────────────┼────────────┼────────────┤
 O 3-Possible │            │            │  R-019     │  R-004     │  R-018     │
 O            │            │            │  R-022     │  R-017     │            │
 D            │            │            │            │  R-021     │            │
              │     3      │     6      │     9      │     12     │     15     │
              ├────────────┼────────────┼────────────┼────────────┼────────────┤
 2-Unlikely   │            │            │  R-006     │            │            │
              │     2      │     4      │     6      │     8      │     10     │
              ├────────────┼────────────┼────────────┼────────────┼────────────┤
 1-Rare       │     1      │     2      │     3      │     4      │     5      │
              └────────────┴────────────┴────────────┴────────────┴────────────┘
```

Legend: 🟥 Critical (20–25) · 🟧 High (13–19) · 🟨 Medium (6–12) · 🟩 Low (1–5)

### Residual Risk Matrix (After Controls)

```text
                                          IMPACT
                1-Negligible  2-Minor    3-Moderate   4-Major     5-Catastrophic
              ┌────────────┬────────────┬────────────┬────────────┬────────────┐
 5-Almost     │            │            │            │            │            │
   Certain    │     5      │     10     │     15     │     20     │     25     │
              ├────────────┼────────────┼────────────┼────────────┼────────────┤
 4-Likely     │            │            │  R-005     │  R-014     │            │
              │            │            │            │  R-015     │            │
 L            │     4      │     8      │     12     │     16     │     20     │
 I            ├────────────┼────────────┼────────────┼────────────┼────────────┤
 K 3-Possible │            │            │  R-003     │  R-001     │            │
 E            │            │            │  R-007     │  R-004     │            │
 L            │            │            │  R-008     │  R-016     │            │
 I            │            │            │  R-010     │  R-017     │            │
 H            │            │            │  R-011     │            │            │
 O            │     3      │     6      │     9      │     12     │     15     │
 O            ├────────────┼────────────┼────────────┼────────────┼────────────┤
 D            │            │  R-006     │  R-002     │  R-009     │  R-018     │
 2-Unlikely   │            │  R-012     │  R-019     │  R-021     │            │
              │            │  R-013     │  R-020     │            │            │
              │            │            │  R-022     │            │            │
              │     2      │     4      │     6      │     8      │     10     │
              ├────────────┼────────────┼────────────┼────────────┼────────────┤
 1-Rare       │     1      │     2      │     3      │     4      │     5      │
              └────────────┴────────────┴────────────┴────────────┴────────────┘
```

**Notable movement:**

- R-014 moved from Critical (20) to High (16) — migration privacy controls planned but not yet implemented; the reduction reflects awareness, not structural control
- R-015 stayed at High (16) — zero reduction; manual flows remain until the integration is delivered. This is a deliberate assessment: no effective control has been added
- R-005 moved from High (15) to Medium (12) — sequencing reduces simultaneous dual-running load but the capacity constraint remains
- R-001 moved from High (16) to Medium (12) — inter-semester phasing and pilot reduce likelihood; impact remains Major because programme credibility is concentrated in this delivery
- R-002 moved from High (16) to Medium (6) — the PeopleSoft-as-source assumption provides a workable interim and ADR-002 is escalated with a decision deadline
- R-020 moved from High (16) to Medium (6) — the architectural fallback ("faster batch") makes the consequence manageable even if event publication is infeasible

---

## B. Top 10 Risks (Ranked by Residual Score)

| Rank | ID | Title | Category | Inherent | Residual | Owner | Status | Response |
|------|-----|-------|----------|----------|----------|-------|--------|----------|
| 1 | R-014 | Data migration creates temporary PI exposure | COMPLIANCE | 20 | **16** | Eleanor Frame | Open | Treat |
| 2 | R-015 | Manual PI flows replicated "temporarily" | COMPLIANCE | 16 | **16** | Eleanor Frame | Open | Treat |
| 3 | R-005 | Integration team overwhelmed by dual-running | OPERATIONAL | 15 | **12** | Sam Okafor | Open | Treat |
| 4 | R-001 | Migration disruption undermines programme credibility | STRATEGIC | 16 | **12** | Prof. Otis Hammond | Open | Treat |
| 5 | R-016 | Ultra SSO/MFA incomplete at go-live | COMPLIANCE | 16 | **12** | Tobias Ohm | Open | Treat |
| 6 | R-004 | Programme dependency — failure discredits L&T strategy | STRATEGIC | 12 | **12** | Prof. Otis Hammond | Open | Treat |
| 7 | R-017 | Cross-border data position unresolved for Ultra hosting | COMPLIANCE | 12 | **12** | Eleanor Frame | Open | Treat |
| 8 | R-018 | Assessment-period disruption during migration | REPUTATIONAL | 15 | **10** | Prof. Otis Hammond | Open | Treat |
| 9 | R-003 | Ultra positioned as vendor mandate | STRATEGIC | 12 | **9** | Dr. Benny Moog | Open | Treat |
| 10 | R-007 | Academic resistance delays Ultra adoption | OPERATIONAL | 12 | **9** | A/Prof. Pearl Clavinet | Open | Treat |

---

## C. Detailed Risk Register

### Risk R-001: Migration disruption undermines programme credibility

**Category:** STRATEGIC
**Status:** Open
**Risk Owner:** Prof. Otis Hammond, DVC (Education) — Executive Sponsor (STKE RACI: Accountable for migration)
**Action Owner:** Rhonda Bell, Project Manager — migration scheduling
**STKE Cross-Reference:** Maps to STKE Conflict C-1 (migration pace vs academic disruption); relates to STKE Goal G-3 (zero assessment-period disruption)

#### Risk Identification

**Risk Description:**
If the Ultra migration causes a visible disruption to teaching — particularly during an assessment period — the incident will be attributed to the L&T Baseline Strategy programme. Projects 004+ depend on this project demonstrating that governed change works. A migration failure does not just damage Project 003; it discredits the architecture and governance framework that justify the entire programme, and the September business case that funded it.

**Root Cause:**
The migration is the first concrete delivery from the L&T strategy. The programme's credibility is concentrated in this single project because no prior delivery has established a track record.

**Trigger Events:**

- Content migration corrupts unit sites during a teaching period
- Integration failure during cutover leaves students without access
- Rollback is required but has not been tested and fails
- An assessment-period freeze is not enforced and a migration-related change causes an outage

**Consequences if Realized:**

- Academic community concludes that the strategy is "IT-driven" and does not protect teaching
- Education Committee withdraws support for subsequent projects
- The September business case is retrospectively judged as having underestimated risk
- Hammond's sponsorship of the programme is weakened

**Affected Stakeholders:**

- **Prof. Otis Hammond**: programme credibility directly undermined
- **A/Prof. Pearl Clavinet**: Education Committee positioned as having approved a disruptive change
- **Dr. Wynton Castle and academics**: direct teaching impact
- **Jazmin Field**: student experience degraded
- **Cassandra Rhodes**: integration programme credibility lost before it has begun

**Related Objectives:**

- **Goal G-3** (Zero assessment-period disruption): directly at risk
- **Outcome O-2** (Academic community adopted Ultra without disruption): the defining outcome

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | LMS migrations routinely encounter content and integration issues; the dual-running complexity of this project increases the surface area |
| **Impact** | 4 — Major | Programme credibility loss affects funding and governance for all subsequent projects |
| **Inherent Risk Score** | **16** (High) | 4 × 4 = 16 |

**Risk Zone:** 🟧 High (13–19)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Inter-semester phasing plan**: Migration phased around the academic calendar with assessment-period change freezes
   - Owner: Rhonda Bell
   - Effectiveness: **Adequate** — the plan exists and is agreed in principle; it has not been stress-tested against actual calendar constraints
   - Evidence: ARC-003-STKE-v1.0 CSF-1

2. **Pilot programme**: Willing academics test migration before broad rollout
   - Owner: Dr. Benny Moog
   - Effectiveness: **Adequate** — design agreed but not yet commenced
   - Evidence: STKE communication plan

3. **Fortnightly Steering Committee**: Escalation and go/no-go authority
   - Owner: Prof. Otis Hammond
   - Effectiveness: **Adequate** — forum exists; decision criteria for go/no-go not yet defined
   - Evidence: STKE governance framework

**Overall Control Effectiveness:** Adequate — reduces likelihood from 4 to 3 (phasing protects assessment periods), but impact remains unchanged because programme credibility is concentrated in this single delivery.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 — Possible | Inter-semester phasing and pilot reduce the likelihood of a teaching-period incident, but content migration issues remain possible |
| **Impact** | 4 — Major | Programme credibility loss is unchanged by controls — the consequence is political, not operational |
| **Residual Risk Score** | **12** (Medium) | 3 × 4 = 12 |

**Risk Zone:** 🟨 Medium (6–12) — at the threshold
**Risk Reduction:** 25% (16 → 12)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:**
The risk is treatable through sequencing discipline, rollback capability, and change freeze enforcement. These are not complex — they are procedural — but they require explicit decision gates and a genuine willingness to delay migration phases if readiness criteria are not met.

**Alternative Responses Considered:**

- **Tolerate**: Rejected — programme credibility is not recoverable once lost
- **Transfer**: Not applicable — reputation cannot be insured
- **Terminate**: Rejected — not migrating is not viable given Anthology's end-of-support trajectory

#### Risk Appetite Assessment

**Provisional appetite for STRATEGIC risks:** Medium (≤ 12)
**Current residual:** 12 (Medium)
**Assessment:** ⚠️ **At provisional appetite threshold** — acceptable only with the action plan below in place
**Escalation Required:** Report to Steering Committee; formal escalation only if phasing plan is not confirmed by 2026-09-30.

#### Action Plan

**Additional Mitigations Needed:**

1. **Define go/no-go criteria for each migration phase**
   - Description: Explicit readiness criteria — content migration success rate, integration test pass, rollback test complete — before any phase proceeds
   - Owner: Rhonda Bell with Dr. Benny Moog
   - Due Date: 2026-09-30
   - Cost: nil (facilitation time)
   - Expected Impact: reduce likelihood 3 → 2

2. **Test rollback capability before the first phase cutover**
   - Description: Execute a full rollback from Ultra to Learn Original in a test environment with representative content and verify restoration completeness
   - Owner: Sam Okafor with Anthology professional services
   - Due Date: 2026-11-30
   - Cost: within migration scope
   - Expected Impact: reduce impact 4 → 3 (credible fallback)

3. **Enforce assessment-period change freeze as a governance rule**
   - Description: No migration-related changes permitted during examination periods — defined dates, enforced through change management, no exceptions without Steering Committee approval
   - Owner: Prof. Otis Hammond
   - Due Date: 2026-09-30
   - Cost: nil
   - Expected Impact: eliminates the highest-consequence trigger

**Target Residual Risk After Mitigations:** L2 × I3 = **6 (Medium)** ✅ within provisional appetite

**Success Criteria:**

- Zero assessment-period disruption incidents attributable to migration
- Rollback capability tested and documented before first cutover
- Go/no-go decision recorded for every migration phase

**Monitoring Plan:**

- **Frequency:** Fortnightly at Steering Committee during migration phases
- **Key Indicators:** migration phase readiness score; content migration success rate; integration test pass rate
- **Escalation Triggers:** any migration-related incident during a teaching period; go/no-go criteria not met at phase gate

---

### Risk R-002: ADR-002 unresolved blocks role assignment integration

**Category:** STRATEGIC
**Status:** Open
**Risk Owner:** Cassandra Rhodes, Chief Information Officer (STKE RACI: Accountable for integration architecture)
**Action Owner:** Sam Okafor, Integration Architect — with Student Administration and HR
**STKE Cross-Reference:** Maps to STKE Risk R-3; relates to STKE Goal G-1 (PeopleSoft → Ultra event-driven)

#### Risk Identification

**Risk Description:**
ADR-002 (Authoritative Source for Institutional Role Assignment) remains unresolved. Student Administration and HR cannot agree on composition rules for institutional role assignment, and the decision is listed as a prerequisite for this project rather than a deliverable of it. Without a resolved ADR-002, the most critical integration flow — user lifecycle and role assignment from PeopleSoft to Ultra — cannot be designed with certainty.

**Root Cause:**
Institutional role assignment is a cross-functional entity that straddles two business units (Student Administration and HR) with different data models and different authority claims. Project 001 identified this tension but correctly ruled it out of scope for a baseline strategy engagement. Project 003 inherits it as a hard prerequisite.

**Trigger Events:**

- ADR-002 decision deferred repeatedly because neither party concedes
- Project 003 commences design with an assumption that proves incorrect
- Role assignment failures in Ultra traced to an incorrect composition rule

**Consequences if Realized:**

- PeopleSoft → Ultra integration designed to an assumption, then refactored — schedule and cost impact
- Role assignment failures continue in Ultra, undermining the proposition that the migration improves things
- The event-driven architecture is delivered without its most important entity
- G-1 (< 15 minutes propagation) cannot be achieved for role assignment events

**Affected Stakeholders:**

- **Sam Okafor**: cannot design the integration without knowing the authoritative source
- **Student Administration**: role assignment rules affect enrolment access
- **Human Resources**: staff role assignment affects teaching access
- **Tobias Ohm**: incorrect role assignment is an access-control exposure
- **Eleanor Frame**: stale roles are a privacy exposure (APP 11)

**Related Objectives:**

- **Goal G-1** (PeopleSoft → Ultra event-driven): directly blocked for role assignment
- **Outcome O-1** (Sustainable integration estate): role assignment is the most consequential entity

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | Cross-functional data ownership disputes between administrative units characteristically stall without executive intervention |
| **Impact** | 4 — Major | Blocks the single most important integration in the project; incorrect assumption produces rework |
| **Inherent Risk Score** | **16** (High) | 4 × 4 = 16 |

**Risk Zone:** 🟧 High (13–19)

#### Current Controls and Mitigations

**Existing Controls:**

1. **PeopleSoft-as-source assumption documented**: The project can proceed with PeopleSoft as the assumed authoritative source and retrofit if ADR-002 concludes differently
   - Owner: Sam Okafor
   - Effectiveness: **Adequate** — provides a workable path but carries refactoring risk
   - Evidence: STKE Risk R-3 contingency plan

2. **Student Administration and HR included as named stakeholders in Project 003**
   - Owner: Rhonda Bell
   - Effectiveness: **Adequate** — representation secured; decision authority not yet established
   - Evidence: ARC-003-STKE-v1.0 stakeholder gap note

3. **Escalation path through Steering Committee to University Executive**
   - Owner: Prof. Otis Hammond
   - Effectiveness: **Adequate** — path exists but has not been invoked for ADR-002
   - Evidence: STKE governance framework Level 5

**Overall Control Effectiveness:** Adequate — the assumption allows design to proceed, reducing likelihood. Impact remains high because an incorrect assumption produces rework.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 — Unlikely | The PeopleSoft-as-source assumption is reasonable and widely expected to hold; full resolution reduces refactoring risk |
| **Impact** | 3 — Moderate | Rework is bounded to the composition rule, not the entire integration; documented assumption limits surprise |
| **Residual Risk Score** | **6** (Medium) | 2 × 3 = 6 |

**Risk Zone:** 🟨 Medium (6–12)
**Risk Reduction:** 63% (16 → 6)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:**
This is a decision risk. The treatment is forcing a decision — not more analysis. The assumption provides an interim mitigation, but the decision must be finalised before the integration goes to production.

**Alternative Responses Considered:**

- **Tolerate**: Rejected — the assumption is acceptable for design but not for production; production role assignment on an unconfirmed source is an access-control risk
- **Transfer**: Not applicable
- **Terminate**: Rejected — role assignment is not optional

#### Action Plan

1. **Set a hard decision deadline for ADR-002**
   - Description: Steering Committee sets a date by which Student Administration and HR must agree or the decision escalates to University Executive automatically
   - Owner: Prof. Otis Hammond
   - Due Date: 2026-08-15
   - Cost: nil
   - Expected Impact: reduce likelihood 2 → 1

2. **Document the PeopleSoft-as-source assumption with explicit retrofit conditions**
   - Description: Record the assumption, the conditions under which it would need to change, and the estimated cost/schedule impact of a retrofit
   - Owner: Sam Okafor
   - Due Date: 2026-08-31
   - Cost: nil
   - Expected Impact: reduce impact 3 → 2 (retrofit is bounded and estimated)

**Target Residual Risk After Mitigations:** L1 × I2 = **2 (Low)** ✅ within provisional appetite

---

### Risk R-003: Ultra positioned as vendor mandate not pedagogical improvement

**Category:** STRATEGIC
**Status:** Open
**Risk Owner:** Dr. Benny Moog, Director Learning Technologies (STKE RACI: Owns Ultra configuration and pedagogical narrative)
**Action Owner:** Dr. Felix Marimba, Academic Lead — communications
**STKE Cross-Reference:** Maps to STKE Risk R-1 (academic resistance); relates to STKE Goal G-4 (consistent accessible templates)

#### Risk Identification

**Risk Description:**
If the Ultra migration is perceived as "the vendor made us upgrade" rather than "this improves teaching", academic resistance will be high and template adoption grudging. The positioning of Ultra determines whether G-4 achieves 80% template adoption or stalls at 30%.

**Root Cause:**
Anthology's end-of-support trajectory for Learn Original creates a genuine vendor forcing function. If the project's communications lead with this rather than with pedagogical benefits, the framing is set.

**Trigger Events:**

- Migration communications emphasise end-of-support rather than teaching improvement
- Template design imposed without academic input
- Ultra feature gaps relative to Learn Original not acknowledged or mitigated
- Training delivered as documentation only, not workshops

**Consequences if Realized:**

- Academic resistance to migration (R-007) intensifies
- Template adoption fails — consistency outcome from Project 001 is lost
- Education Committee withdraws endorsement
- Moog is positioned as the IT emissary rather than the academic designer

**Affected Stakeholders:**

- **Dr. Benny Moog**: his credibility with academics depends on this framing
- **Dr. Wynton Castle**: will adopt or resist based on whether Ultra feels imposed or better
- **A/Prof. Pearl Clavinet**: Education Committee endorsement depends on pedagogical case
- **Jazmin Field**: student experience during transition

**Related Objectives:**

- **Goal G-4** (Consistent accessible templates): adoption depends on positioning
- **Outcome O-2** (Academic community adopted Ultra without disruption)

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | The vendor forcing function is real and easy to lead with; pedagogical framing requires effort |
| **Impact** | 3 — Moderate | Adoption is slowed and grudging rather than prevented; outcome is degraded, not defeated |
| **Inherent Risk Score** | **12** (Medium) | 4 × 3 = 12 |

**Risk Zone:** 🟨 Medium (6–12)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Moog's role as Ultra designer, not IT emissary**: STKE positions Moog as the owner of Ultra configuration and template architecture
   - Owner: Dr. Benny Moog
   - Effectiveness: **Adequate** — the positioning is deliberate but has not been tested with the academic community
   - Evidence: STKE SD-4

2. **Castle involved in pilot programme**: The most influential academic voice will experience Ultra before being asked to endorse it
   - Owner: Dr. Benny Moog
   - Effectiveness: **Adequate** — pilot is designed but not commenced
   - Evidence: STKE communication plan

3. **Principle 3 (Consistent Experience)**: Templates designed to make the easy path the default, not to mandate compliance
   - Owner: A/Prof. Pearl Clavinet
   - Effectiveness: **Adequate** — the principle exists; the template does not yet
   - Evidence: ARC-000-PRIN-v1.1

**Overall Control Effectiveness:** Adequate — reduces likelihood from 4 to 3.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 — Possible | Deliberate positioning and pilot reduce the default to vendor-mandate framing |
| **Impact** | 3 — Moderate | Unchanged |
| **Residual Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6–12)
**Risk Reduction:** 25% (12 → 9)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:**
The treatment is communications discipline: lead with what Ultra does better, acknowledge what Learn Original did well, and position templates as effort reduction.

#### Action Plan

1. **Position Ultra's pedagogical advantages in all migration communications**
   - Owner: Dr. Benny Moog with Dr. Felix Marimba
   - Due Date: 2026-09-30 (before first faculty migration)
   - Cost: nil
   - Expected Impact: reduce likelihood 3 → 2

2. **Acknowledge Learn Original limitations that Ultra addresses**
   - Description: Publish a concrete comparison — not marketing materials, but honest feature comparison with academic language
   - Owner: Dr. Benny Moog
   - Due Date: 2026-09-30
   - Expected Impact: establishes credibility

3. **Deliver automated course cloning before requesting template conformance**
   - Description: Demonstrate effort reduction before asking for adoption — CSF-5
   - Owner: Dr. Benny Moog with Sam Okafor
   - Due Date: 2027-02-28
   - Expected Impact: reduce impact 3 → 2

**Target Residual Risk After Mitigations:** L2 × I2 = **4 (Low)** ✅ within provisional appetite

---

### Risk R-004: Programme dependency — this project's failure discredits the entire L&T strategy

**Category:** STRATEGIC
**Status:** Open
**Risk Owner:** Prof. Otis Hammond, DVC (Education)
**Action Owner:** Cassandra Rhodes, CIO
**STKE Cross-Reference:** Relates to STKE Outcome O-2; cross-references R-001

#### Risk Identification

**Risk Description:**
Project 003 is the first concrete delivery from the L&T Baseline Strategy. If it fails — over budget, behind schedule, or with visible quality defects — the strategy itself is retrospectively judged as having produced a bad plan. Projects 004+ lose funding credibility. The September business case that approved this programme of work is cited as evidence of poor planning.

**Root Cause:**
Programme credibility is concentrated in a single project because no prior delivery has established a track record. This is a structural consequence of sequencing — the first project always carries disproportionate reputational weight.

**Trigger Events:**

- Migration costs exceed business case provision by more than 20%
- Timeline slips past the contracted window for Anthology professional services
- A visible quality defect (broken content, assessment disruption) reaches the Vice-Chancellor

**Consequences if Realized:**

- Projects 004+ deferred or cancelled
- Architecture governance framework perceived as producing plans that cannot be delivered
- CIO's investment in integration modernisation questioned
- Hammond's sponsorship weakened at University Executive

**Affected Stakeholders:**

- **Prof. Otis Hammond**: programme sponsor
- **Cassandra Rhodes**: integration investment credibility
- **Vernon Ostinato**: business case retrospectively questioned
- **Prof. Stella Groove**: institutional decision-making quality

**Related Objectives:**

- **Outcome O-1** (Sustainable integration estate): dependent on programme continuation
- **Outcome O-2** (Academic community adopted Ultra): defining delivery

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 — Possible | LMS migrations are complex but achievable; the integration scope adds meaningful risk |
| **Impact** | 4 — Major | Programme-level consequence; affects future funding decisions |
| **Inherent Risk Score** | **12** (Medium) | 3 × 4 = 12 |

**Risk Zone:** 🟨 Medium (6–12)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Programme governance through Steering Committee**
   - Owner: Prof. Otis Hammond
   - Effectiveness: **Adequate** — oversight exists
   - Evidence: STKE governance framework

2. **Phased delivery with go/no-go gates**
   - Owner: Rhonda Bell
   - Effectiveness: **Adequate** — phases planned but gates not yet defined

**Overall Control Effectiveness:** Adequate — reduces likelihood marginally.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 — Possible | Governance reduces surprise but does not prevent delivery failure |
| **Impact** | 4 — Major | Programme consequence unchanged |
| **Residual Risk Score** | **12** (Medium) | 3 × 4 = 12 |

**Risk Zone:** 🟨 Medium (6–12)
**Risk Reduction:** 0% — controls are procedural, not structural

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:**
The treatment is to deliver early visible wins before attempting the highest-risk phases. PeopleSoft integration (backend, invisible to academics) delivered first; pilot programme with willing academics second. Failures in early phases are recoverable; failures in later phases are visible.

#### Action Plan

1. **Sequence delivery for early wins**: PeopleSoft integration first (highest value, lowest academic visibility), then pilot, then phased faculty rollout
   - Owner: Rhonda Bell
   - Due Date: 2026-09-30
   - Expected Impact: reduce likelihood 3 → 2

2. **Report integration early wins to Steering Committee**: Demonstrate delivered value before the riskiest phases
   - Owner: Sam Okafor
   - Due Date: 2027-03-31
   - Expected Impact: reduce impact 4 → 3 (partial success already banked)

**Target Residual Risk After Mitigations:** L2 × I3 = **6 (Medium)** ✅ within provisional appetite

---

### Risk R-005: Integration team overwhelmed by dual-running

**Category:** OPERATIONAL
**Status:** Open
**Risk Owner:** Sam Okafor, Integration Architect (STKE RACI: Responsible for integration delivery)
**Action Owner:** Cassandra Rhodes, CIO — capacity funding
**STKE Cross-Reference:** Maps to STKE Risk R-2; maps to STKE Conflict C-2 (integration scope vs team capacity); relates to STKE Goal G-5 (team capacity sustained)

#### Risk Identification

**Risk Description:**
Okafor's integration team must simultaneously maintain seven existing fragile integrations (current estate) and build their event-driven replacements (target architecture). The team is sized for maintenance, not concurrent development. Without additional capacity, one or both work streams will degrade — existing integrations fail during teaching, or new integrations are not ready at cutover.

**Root Cause:**
The team that knows the current integrations intimately enough to maintain them is the same team that must design and build the replacements. This is not a planning failure — it is a structural constraint of replacing a system while it is in production.

**Trigger Events:**

- A current integration fails during migration development, pulling the team off new-build work
- Vendor professional services for the PeopleSoft integration are unavailable or delayed
- All seven integrations expected to migrate in the same phase
- Team attrition during the highest-pressure period

**Consequences if Realized:**

- Existing integration failures during teaching — students without access, role assignment errors
- New integrations not ready at cutover — manual workarounds replicated on Ultra
- Team burnout and attrition — loss of the only people who understand both old and new
- Schedule slip cascading to the migration timeline

**Affected Stakeholders:**

- **Sam Okafor**: carries the delivery and the personal burden
- **Cassandra Rhodes**: integration programme depends on team capacity
- **Rhonda Bell**: migration schedule depends on integration readiness
- **Dr. Wynton Castle and academics**: affected by integration failures during dual-running

**Related Objectives:**

- **Goal G-1** (PeopleSoft → Ultra event-driven): delivery depends on team capacity
- **Goal G-5** (Integration team capacity sustained): directly at risk
- **Outcome O-1** (Sustainable integration estate)

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 5 — Almost Certain | Maintaining and replacing seven integrations concurrently with a maintenance-sized team will produce conflicts as a statistical certainty |
| **Impact** | 3 — Moderate | Degradation of both work streams; schedule slip; team burnout |
| **Inherent Risk Score** | **15** (High) | 5 × 3 = 15 |

**Risk Zone:** 🟧 High (13–19)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Risk-based sequencing**: Phase 1 PeopleSoft, Phase 2 provisioning and placement, Phase 3 remainder (STKE Conflict C-2 resolution)
   - Owner: Sam Okafor
   - Effectiveness: **Adequate** — reduces simultaneous work but does not eliminate dual-running
   - Evidence: STKE conflict resolution strategy

2. **Progressive decommission of old flows**: As new integrations go live, old flows are retired, reducing the maintenance surface
   - Owner: Sam Okafor
   - Effectiveness: **Adequate** — sound in principle; depends on Phase 1 succeeding on time
   - Evidence: STKE SD-3 enablers

**Overall Control Effectiveness:** Adequate — reduces likelihood from 5 to 4 (sequencing limits simultaneous work) but does not address the capacity gap.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | Sequencing helps but the team is still undersized for dual-running, even sequenced |
| **Impact** | 3 — Moderate | Unchanged — consequences are operational degradation and schedule slip |
| **Residual Risk Score** | **12** (Medium) | 4 × 3 = 12 |

**Risk Zone:** 🟨 Medium (6–12) — at provisional appetite threshold
**Risk Reduction:** 20% (15 → 12)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:**
The only structural mitigation is additional capacity — either staff augmentation or vendor professional services for the highest-risk integration (PeopleSoft). Sequencing reduces simultaneous load but does not eliminate the dual-running period. This risk cannot be mitigated by working harder or working smarter; it requires resources.

**Alternative Responses Considered:**

- **Tolerate**: Rejected — team burnout produces attrition, which makes the problem worse
- **Transfer**: Partially — vendor professional services transfer delivery risk for PeopleSoft integration
- **Terminate**: Rejected — the integrations are essential

#### Risk Appetite Assessment

**Provisional appetite for OPERATIONAL risks:** Medium (≤ 12)
**Current residual:** 12 (Medium)
**Assessment:** ⚠️ **At provisional appetite threshold** — acceptable only with funded capacity plan
**Escalation Required:** Yes — capacity plan to Steering Committee before migration commences.

#### Action Plan

1. **Approve and fund the integration team capacity plan**
   - Description: Define additional capacity required for the dual-running period — staff augmentation, contractor, or vendor professional services — and approve funding before Phase 1 begins
   - Owner: Cassandra Rhodes with Sam Okafor
   - Due Date: 2026-09-30
   - Cost: AUD 150,000–300,000 (estimated; dependent on vendor PS rates and duration)
   - Expected Impact: reduce likelihood 4 → 2

2. **Engage Anthology professional services for PeopleSoft → Ultra integration**
   - Description: The highest-risk, highest-value integration; Anthology has the most relevant platform knowledge
   - Owner: Grace Tanaka with Sam Okafor
   - Due Date: 2026-10-31
   - Cost: within migration business case provision (see R-011)
   - Expected Impact: transfers Phase 1 delivery risk

3. **Define dual-running exit criteria per integration**
   - Description: For each integration, specify when the old flow can be decommissioned and the team can stop dual-running
   - Owner: Sam Okafor
   - Due Date: 2026-10-31
   - Cost: nil
   - Expected Impact: reduce impact 3 → 2 (bounded dual-running window)

**Target Residual Risk After Mitigations:** L2 × I2 = **4 (Low)** ✅ within provisional appetite

**Success Criteria:**

- No increase in integration incidents during migration versus baseline
- New integrations delivered to plan without schedule slip attributable to capacity
- Team overtime within sustainable limits; zero attrition attributable to dual-running

**Monitoring Plan:**

- **Frequency:** Monthly during delivery
- **Key Indicators:** integration incident rate vs baseline; delivery milestones; team overtime hours
- **Escalation Triggers:** any integration failure during a teaching period; capacity plan not approved by 2026-09-30

---

### Risk R-006: Content migration breaks discipline-specific content

**Category:** OPERATIONAL
**Status:** Open
**Risk Owner:** Dr. Benny Moog, Director Learning Technologies
**Action Owner:** Prof. Desmond Key (Music) and Prof. Priya Anand (Health Sciences) — faculty sign-off
**STKE Cross-Reference:** Maps to STKE Risk R-4; relates to STKE Goal G-6 (discipline tool integrations verified)

#### Risk Identification

**Risk Description:**
Anthology's migration tooling may not handle discipline-specific content types — embedded interactive notation (MuseScore), simulation links (iSimulate, Kuracloud), clinical scenario configurations, high-fidelity performance capture references (Ableton Live). Broken or degraded content in these disciplines will be perceived as exactly the consolidation-driven loss that Project 001's governance process was supposed to prevent.

**Root Cause:**
Migration tooling is designed for generic content types. Discipline-specific content often relies on custom building blocks, embedded LTI links, or non-standard formatting that may not have a direct Ultra equivalent.

**Trigger Events:**

- Migration tooling silently drops embedded LTI content or converts it incorrectly
- Interactive notation distribution breaks because Ultra's content model differs from Learn Original
- Faculty discovers broken content after cutover, during teaching
- Discipline tool vendors slow to verify Ultra compatibility

**Consequences if Realized:**

- Discipline-specific units are unusable without manual remediation
- Prof. Desmond Key and Prof. Priya Anand lose confidence in the migration
- Principle 4 (Discipline Specialisation at the Edge) is violated in practice
- Manual remediation effort during teaching — workload on academics that the migration was supposed to reduce

**Affected Stakeholders:**

- **Prof. Desmond Key**: discipline tools are his stated priority
- **Prof. Priya Anand**: clinical simulation content
- **Dr. Wynton Castle**: LMS power user; any content loss validates his concern
- **Dr. Benny Moog**: template and configuration responsibility

**Related Objectives:**

- **Goal G-6** (Discipline tool integrations verified): directly at risk
- **Goal G-3** (Zero assessment-period disruption): if broken content is discovered during teaching
- **Outcome O-2** (Academic community adopted Ultra without disruption)

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 — Unlikely | Migration tooling handles most content; discipline-specific content is a minority but the consequences are concentrated |
| **Impact** | 3 — Moderate | Discipline units degraded; manual remediation required; reputational consequence within affected faculties |
| **Inherent Risk Score** | **6** (Medium) | 2 × 3 = 6 |

**Risk Zone:** 🟨 Medium (6–12)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Pilot programme includes discipline faculty unit sites**: Music & Performing Arts and Health Sciences included in pilot testing
   - Owner: Dr. Benny Moog
   - Effectiveness: **Adequate** — designed but not commenced
   - Evidence: STKE communication plan

2. **Faculty sign-off before migration phase**: Key and Anand approve before their faculties migrate
   - Owner: Rhonda Bell
   - Effectiveness: **Adequate** — gate exists in the RACI

**Overall Control Effectiveness:** Adequate — catches issues before they affect teaching, if the pilot is thorough.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 — Unlikely | Pilot testing will catch most issues before broad rollout |
| **Impact** | 2 — Minor | Caught in pilot; remediation before teaching period |
| **Residual Risk Score** | **4** (Low) | 2 × 2 = 4 |

**Risk Zone:** 🟩 Low (1–5)
**Risk Reduction:** 33% (6 → 4)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

#### Action Plan

1. **Test migration on representative discipline unit sites in the Ultra sandpit**
   - Owner: Dr. Benny Moog with Key and Anand
   - Due Date: 2026-11-30 (before first discipline faculty migration)
   - Expected Impact: identifies issues before they affect teaching

2. **Verify LTI 1.3 Advantage for all discipline tools in Ultra**
   - Owner: Sam Okafor
   - Due Date: 2026-11-30
   - Expected Impact: confirms or identifies gaps in LTI compatibility

**Target Residual Risk After Mitigations:** L1 × I2 = **2 (Low)** ✅

---

### Risk R-007: Academic resistance delays Ultra adoption

**Category:** OPERATIONAL
**Status:** Open
**Risk Owner:** A/Prof. Pearl Clavinet, Dean of Learning & Teaching
**Action Owner:** Dr. Felix Marimba, Academic Lead — change management
**STKE Cross-Reference:** Maps to STKE Risk R-1; relates to STKE Conflict C-1 (migration pace vs academic disruption)

#### Risk Identification

**Risk Description:**
Academics resist the Ultra migration because the interface change feels imposed, content migration is imperfect, training is inadequate, or the timing conflicts with teaching preparation. Resistance does not prevent migration — Learn Original's end-of-support makes that unavoidable — but it delays adoption, reduces template conformance, and produces grudging compliance rather than genuine improvement.

**Root Cause:**
Interface change fatigue. Academics have limited capacity for learning new tools, and the effort is concentrated during the busiest periods.

**Trigger Events:**

- Training available only as documentation, not workshops
- Content migration producing visible defects in migrated unit sites
- Template design imposed without academic input
- Migration scheduled during teaching preparation periods

**Consequences if Realized:**

- Template adoption below 80% target — consistency outcome not achieved
- Academics recreate Learn Original structures in Ultra, defeating the purpose
- Support load spikes during the first teaching period on Ultra
- Education Committee questions whether sufficient consultation occurred

**Affected Stakeholders:**

- **Dr. Wynton Castle**: the academic most affected and most influential
- **A/Prof. Pearl Clavinet**: academic governance responsibility
- **Dr. Benny Moog**: template adoption depends on academic willingness
- **Jazmin Field**: student experience degrades if academics do not adopt Ultra properly

**Related Objectives:**

- **Goal G-4** (Consistent accessible templates): adoption depends on willingness
- **Outcome O-2** (Academic community adopted Ultra without disruption)

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | Interface changes in LMS platforms routinely produce resistance; Ultra's different navigation model amplifies this |
| **Impact** | 3 — Moderate | Adoption slowed and template conformance reduced, but migration itself proceeds |
| **Inherent Risk Score** | **12** (Medium) | 4 × 3 = 12 |

**Risk Zone:** 🟨 Medium (6–12)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Pilot programme with willing academics**
   - Owner: Dr. Benny Moog
   - Effectiveness: **Adequate** — produces early adopters and identifies issues
   - Evidence: STKE CSF-5

2. **Castle involved in template design and pilot**
   - Owner: Dr. Benny Moog
   - Effectiveness: **Adequate** — Castle's endorsement carries disproportionate weight with colleagues
   - Evidence: STKE SD-6 mitigation

3. **Ultra positioned as pedagogical improvement (R-003 treatment)**
   - Owner: Dr. Benny Moog with Dr. Felix Marimba
   - Effectiveness: **Adequate** — deliberate but not yet tested

**Overall Control Effectiveness:** Adequate — reduces likelihood from 4 to 3.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 — Possible | Pilot and positioning reduce initial resistance but do not eliminate it for the full academic community |
| **Impact** | 3 — Moderate | Unchanged |
| **Residual Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6–12)
**Risk Reduction:** 25% (12 → 9)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

#### Action Plan

1. **Deliver hands-on training workshops, not just documentation**
   - Owner: Dr. Felix Marimba
   - Due Date: Per faculty, before their migration phase
   - Expected Impact: reduce likelihood 3 → 2

2. **Provide sandpit access at least four weeks before cutover**
   - Owner: Dr. Benny Moog
   - Due Date: Per faculty migration phase
   - Expected Impact: academics discover and resolve issues before teaching

3. **Demonstrate automated course cloning and template effort reduction before requesting conformance**
   - Owner: Dr. Benny Moog with Sam Okafor
   - Due Date: 2027-02-28
   - Expected Impact: CSF-5 — consistency as effort reduction, not mandate

**Target Residual Risk After Mitigations:** L2 × I2 = **4 (Low)** ✅

---

### Risk R-008: Course cloning single-person dependency persists during migration

**Category:** OPERATIONAL
**Status:** Open
**Risk Owner:** Sam Okafor, Integration Architect
**Action Owner:** Sam Okafor — documentation and training
**STKE Cross-Reference:** Inherits from ARC-001-RISK R-007; relates to STKE Goal G-5 (team capacity)

#### Risk Identification

**Risk Description:**
Course rollover runs on undocumented scripts held by a single individual. During the migration period, course cloning is more critical than ever — every unit must be cloned into Ultra's format — and the dependency on one person is amplified by the dual-running workload on the integration team.

**Root Cause:**
Cloning automation was built ad hoc without documentation or version control. The individual who built it is also a key member of the integration team delivering the new architecture.

**Trigger Events:**

- The script owner is unavailable during a critical rollover period
- A script fails during migration and nobody else can diagnose or fix it
- The individual leaves the organisation during the project

**Consequences if Realized:**

- Course rollover fails — unit sites not available for the start of a teaching period
- Migration schedule slips because cloning cannot proceed
- Knowledge loss if the individual departs

**Affected Stakeholders:**

- **Sam Okafor**: the individual and the team lead
- **Dr. Benny Moog**: template rollout depends on cloning working
- **Academics**: unit sites not ready for teaching

**Related Objectives:**

- **Goal G-3** (Zero assessment-period disruption): cloning failure produces disruption
- **Goal G-5** (Team capacity sustained): single-person dependency is a capacity fragility

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | Single-person dependency during the highest-pressure period in the estate's history |
| **Impact** | 3 — Moderate | Unit sites unavailable; migration schedule disrupted |
| **Inherent Risk Score** | **12** (Medium) | 4 × 3 = 12 |

**Risk Zone:** 🟨 Medium (6–12)

#### Current Controls and Mitigations

**Existing Controls:**

1. **None effective** — scripts are undocumented and not version-controlled
   - Effectiveness: **Weak**

**Overall Control Effectiveness:** Weak — no reduction.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 — Possible | The individual is currently available and engaged; the risk is latent |
| **Impact** | 3 — Moderate | Unchanged |
| **Residual Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6–12)
**Risk Reduction:** 25% (12 → 9)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

#### Action Plan

1. **Document and version-control the cloning scripts immediately**
   - Owner: Sam Okafor
   - Due Date: 2026-09-30
   - Cost: nil
   - Expected Impact: reduce impact 3 → 2

2. **Train a second operator on cloning procedures**
   - Owner: Sam Okafor
   - Due Date: 2026-10-31
   - Expected Impact: reduce likelihood 3 → 2

3. **Replace scripts with Ultra's native cloning capability where possible**
   - Owner: Dr. Benny Moog with Sam Okafor
   - Due Date: 2027-06-30
   - Expected Impact: eliminate dependency entirely

**Target Residual Risk After Mitigations:** L2 × I2 = **4 (Low)** ✅

---

### Risk R-009: Vendor (Anthology) professional services unavailable or delayed

**Category:** OPERATIONAL
**Status:** Open
**Risk Owner:** Grace Tanaka, Procurement & Vendor Manager
**Action Owner:** Grace Tanaka — contract negotiation
**STKE Cross-Reference:** Relates to STKE SD-14 (Anthology); STKE Conflict C-4 (Anthology commercial interest vs Principle 19)

#### Risk Identification

**Risk Description:**
The PeopleSoft → Ultra integration re-engineering depends on Anthology professional services for platform-specific API knowledge and migration tooling support. If professional services are unavailable, delayed, or prohibitively expensive, the highest-risk integration is delivered without vendor support.

**Root Cause:**
Anthology's professional services capacity is constrained by the global Ultra migration wave — UoF is not the only institution migrating. Service availability is a function of demand across Anthology's customer base.

**Trigger Events:**

- Anthology professional services fully committed to other institutional migrations
- Professional services scope creeps beyond migration support into premium consulting
- Anthology bundles PS engagement with premium licensing tier (R-012 linkage)
- Contract renewal timing misaligns with project schedule

**Consequences if Realized:**

- PeopleSoft integration delivered without vendor platform knowledge — higher defect rate, longer timeline
- Integration team absorbs work intended for vendor PS — R-005 worsened
- Migration schedule delayed; assessment-period phasing compromised

**Affected Stakeholders:**

- **Sam Okafor**: delivery depends on vendor support for PeopleSoft integration
- **Grace Tanaka**: contract negotiation leverage
- **Rhonda Bell**: migration schedule
- **Vernon Ostinato**: cost impact if PS rates are premium

**Related Objectives:**

- **Goal G-1** (PeopleSoft → Ultra event-driven): Phase 1 dependency
- **Goal G-5** (Team capacity sustained): vendor PS is a capacity supplement

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | Global Ultra migration demand constrains Anthology PS capacity |
| **Impact** | 3 — Moderate | Schedule delay and increased team burden; not project-fatal |
| **Inherent Risk Score** | **12** (Medium) | 4 × 3 = 12 |

**Risk Zone:** 🟨 Medium (6–12)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Migration commitment as negotiating leverage**: UoF's commitment to Ultra gives Tanaka leverage for PS terms
   - Owner: Grace Tanaka
   - Effectiveness: **Adequate** — leverage exists but has not been exercised
   - Evidence: STKE SD-10

2. **Contract renewal timing aligned to project**: Renewal is the commercial moment for negotiation
   - Owner: Grace Tanaka
   - Effectiveness: **Adequate** — timing is known but negotiation not commenced

**Overall Control Effectiveness:** Adequate — reduces likelihood from 4 to 3 if leverage is exercised during contract negotiation.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 — Unlikely | Anthology is commercially motivated to support migration; leverage is available |
| **Impact** | 4 — Major | Without PS support the integration is still deliverable but substantially harder and slower |
| **Residual Risk Score** | **8** (Medium) | 2 × 4 = 8 |

**Risk Zone:** 🟨 Medium (6–12)
**Risk Reduction:** 33% (12 → 8)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

#### Action Plan

1. **Negotiate PS terms as part of contract renewal, not as a separate purchase**
   - Owner: Grace Tanaka
   - Due Date: 2026-10-31 (before migration Phase 1)
   - Expected Impact: secure PS availability at agreed rates

2. **Define PS scope and deliverables before engagement begins**
   - Owner: Sam Okafor with Grace Tanaka
   - Due Date: 2026-10-31
   - Expected Impact: prevents scope creep

3. **Develop contingency plan for PeopleSoft integration without Anthology PS**
   - Owner: Sam Okafor
   - Due Date: 2026-10-31
   - Expected Impact: reduces impact of PS unavailability

**Target Residual Risk After Mitigations:** L2 × I3 = **6 (Medium)** ✅

---

### Risk R-010: Migration timeline too compressed for inter-semester phasing

**Category:** OPERATIONAL
**Status:** Open
**Risk Owner:** Rhonda Bell, Project Manager
**Action Owner:** A/Prof. Pearl Clavinet — academic calendar confirmation
**STKE Cross-Reference:** Relates to STKE Conflict C-1 (migration pace vs academic disruption); STKE Goal G-3

#### Risk Identification

**Risk Description:**
The inter-semester windows available for migration may be insufficient for the number of faculties that must migrate. If the academic calendar does not provide enough non-teaching weeks, either migration phases are compressed (risking quality) or the timeline extends beyond the contracted window for Anthology support and Learn Original maintenance.

**Root Cause:**
The academic calendar is fixed and leaves limited inter-semester gaps. The number of faculties multiplied by the migration preparation, cutover, and validation time per faculty may exceed the available windows.

**Trigger Events:**

- Academic calendar analysis reveals fewer usable weeks than assumed
- A faculty migration slips, consuming the window allocated to the next faculty
- Anthology professional services availability constrains the migration window
- Learn Original end-of-support date creates a hard deadline

**Consequences if Realized:**

- Faculties migrated during teaching periods — violating CSF-1 and G-3
- Migration quality compromised — content not fully verified before teaching begins
- Timeline extension requiring additional Anthology Learn Original maintenance fees

**Affected Stakeholders:**

- **Rhonda Bell**: scheduling accountability
- **A/Prof. Pearl Clavinet**: academic calendar gate
- **Dr. Wynton Castle and academics**: teaching-period migration
- **Vernon Ostinato**: cost of timeline extension

**Related Objectives:**

- **Goal G-3** (Zero assessment-period disruption): directly at risk
- **Outcome O-2** (Academic community adopted Ultra without disruption)

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | Inter-semester windows are structurally short; the constraint is real |
| **Impact** | 3 — Moderate | Teaching-period migration or timeline extension; not project-fatal but damaging |
| **Inherent Risk Score** | **12** (Medium) | 4 × 3 = 12 |

**Risk Zone:** 🟨 Medium (6–12)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Inter-semester phasing plan**: Migration phased around the academic calendar
   - Owner: Rhonda Bell
   - Effectiveness: **Adequate** — plan exists; calendar analysis not yet complete
   - Evidence: STKE CSF-1

**Overall Control Effectiveness:** Adequate — the intent is correct but the feasibility is unconfirmed.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 — Possible | Phasing plan reduces compressed-timeline risk but calendar constraints are structural |
| **Impact** | 3 — Moderate | Unchanged |
| **Residual Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6–12)
**Risk Reduction:** 25% (12 → 9)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

#### Action Plan

1. **Complete academic calendar analysis and confirm available migration windows**
   - Owner: Rhonda Bell with A/Prof. Pearl Clavinet
   - Due Date: 2026-09-15
   - Expected Impact: confirms feasibility or forces re-planning before commitments are made

2. **Negotiate Learn Original extended maintenance with Anthology if needed**
   - Owner: Grace Tanaka
   - Due Date: 2026-10-31
   - Cost: to be determined — may be significant
   - Expected Impact: removes the hard deadline pressure

**Target Residual Risk After Mitigations:** L2 × I3 = **6 (Medium)** ✅

---

### Risk R-011: Migration costs exceed business case provision

**Category:** FINANCIAL
**Status:** Open
**Risk Owner:** Vernon Ostinato, Chief Financial Officer
**Action Owner:** Rhonda Bell — cost tracking
**STKE Cross-Reference:** Relates to STKE SD-9 (Ostinato — costs justified by savings)

#### Risk Identification

**Risk Description:**
The Ultra migration and integration re-engineering costs exceed the provision in the September business case. Cost drivers include: Anthology professional services (R-009), integration team augmentation (R-005), extended Learn Original maintenance (R-010), and premium API licensing (R-012). If costs escalate without corresponding savings materialising, the remainder of the roadmap loses funding credibility.

**Root Cause:**
Migration costs are inherently uncertain until vendor pricing, team augmentation needs, and timeline are confirmed. The business case provision was estimated without these details.

**Trigger Events:**

- Anthology PS rates higher than estimated
- Integration team augmentation more expensive or longer than planned
- Timeline extension requiring additional Learn Original maintenance fees
- Unbudgeted premium licensing costs for Ultra API access

**Consequences if Realized:**

- Business case credibility undermined — R-004 consequence
- Remaining roadmap projects (004+) questioned on cost accuracy
- Institutional willingness to fund technology programmes reduced

**Affected Stakeholders:**

- **Vernon Ostinato**: business case accountability
- **Cassandra Rhodes**: competing capital claims within Digital & IT
- **Prof. Otis Hammond**: programme sponsor
- **Prof. Stella Groove**: institutional investment decision

**Related Objectives:**

- **Outcome O-1** (Sustainable integration estate): dependent on continued programme funding
- **Goal G-5** (Team capacity sustained): capacity costs are the largest uncertain item

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | LMS migrations routinely exceed initial estimates; the integration scope adds further uncertainty |
| **Impact** | 3 — Moderate | Financial overrun is manageable but damages credibility for future investment |
| **Inherent Risk Score** | **12** (Medium) | 4 × 3 = 12 |

**Risk Zone:** 🟨 Medium (6–12)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Business case separates migration capital from recurring licence costs**
   - Owner: Vernon Ostinato
   - Effectiveness: **Adequate** — cost structure is clear
   - Evidence: STKE SD-9

2. **Migration costs to be confirmed during contract negotiation**
   - Owner: Grace Tanaka
   - Effectiveness: **Adequate** — cost confirmation is planned but not yet done

**Overall Control Effectiveness:** Adequate — cost structure is sound; actuals are unknown.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 — Possible | Some cost categories will be confirmed through contract negotiation; others remain uncertain |
| **Impact** | 3 — Moderate | Unchanged |
| **Residual Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6–12)
**Risk Reduction:** 25% (12 → 9)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

#### Action Plan

1. **Confirm all cost categories before migration Phase 1 commences**
   - Owner: Rhonda Bell with Grace Tanaka and Vernon Ostinato
   - Due Date: 2026-10-31
   - Expected Impact: eliminates cost uncertainty for the largest items

2. **Establish a migration contingency provision (15–20% of estimated cost)**
   - Owner: Vernon Ostinato
   - Due Date: 2026-10-31
   - Expected Impact: absorbs overruns without requiring re-approval

3. **Track cost-to-completion monthly and report to Steering Committee**
   - Owner: Rhonda Bell
   - Due Date: Ongoing from Phase 1
   - Expected Impact: early warning of cost escalation

**Target Residual Risk After Mitigations:** L2 × I2 = **4 (Low)** ✅

---

### Risk R-012: Anthology gates API access behind premium licensing

**Category:** FINANCIAL
**Status:** Open
**Risk Owner:** Grace Tanaka, Procurement & Vendor Manager
**Action Owner:** Sam Okafor — API requirements specification
**STKE Cross-Reference:** Maps to STKE Risk R-5; relates to STKE Conflict C-4 (Anthology commercial interest vs Principle 19)

#### Risk Identification

**Risk Description:**
REST API endpoints or webhook capabilities required for the event-driven integration architecture (ADR-001) are only available in Ultra's premium licensing tier. This creates an unbudgeted cost and a tension with Principle 19 (Realise Licensed Capability Before New Spend) — the university would be paying extra to use functionality that should be standard.

**Root Cause:**
SaaS vendors routinely gate advanced integration capabilities behind premium tiers. Anthology's commercial interest in deepening the relationship (STKE SD-14) creates an incentive to bundle API access with premium features.

**Trigger Events:**

- API capability assessment reveals that required endpoints are premium-only
- Anthology bundles migration PS with premium licensing
- Standard-tier rate limits are insufficient for near-real-time event throughput

**Consequences if Realized:**

- Unbudgeted licensing cost — AUD 50,000–150,000/year depending on tier
- Principle 19 conflict — paying for capability that should be realised from existing licence
- G-1 (< 15 minutes propagation) unachievable without premium API access
- Alternative integration approaches (SIS framework, LTI) may be less capable

**Affected Stakeholders:**

- **Sam Okafor**: integration design constrained by licensing
- **Grace Tanaka**: contract negotiation
- **Vernon Ostinato**: unbudgeted cost
- **Cassandra Rhodes**: architectural compromise

**Related Objectives:**

- **Goal G-1** (PeopleSoft → Ultra event-driven): API access is prerequisite
- **Outcome O-1** (Sustainable integration estate)

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | SaaS premium API gating is common practice; no confirmation yet from Anthology |
| **Impact** | 3 — Moderate | Financial impact and potential architectural compromise; not project-fatal |
| **Inherent Risk Score** | **12** (Medium) | 4 × 3 = 12 |

**Risk Zone:** 🟨 Medium (6–12)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Migration commitment as negotiating leverage**: API access negotiated as part of migration commitment
   - Owner: Grace Tanaka
   - Effectiveness: **Adequate** — leverage exists
   - Evidence: STKE SD-10

2. **Principle 19 as procurement position**: Requires demonstrating licensed capability before new spend
   - Owner: Grace Tanaka
   - Effectiveness: **Adequate** — frames the negotiation

**Overall Control Effectiveness:** Adequate — the negotiating position is strong but untested.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 — Unlikely | Anthology is commercially motivated to support migration; API access is a reasonable ask in a renewal negotiation |
| **Impact** | 2 — Minor | Even if premium pricing applies, the cost is bounded and quantifiable |
| **Residual Risk Score** | **4** (Low) | 2 × 2 = 4 |

**Risk Zone:** 🟩 Low (1–5)
**Risk Reduction:** 67% (12 → 4)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

#### Action Plan

1. **Document API access requirements before contract negotiation**
   - Owner: Sam Okafor
   - Due Date: 2026-09-30
   - Expected Impact: negotiation informed by technical specifics

2. **Negotiate API access as part of migration commitment, not as an add-on**
   - Owner: Grace Tanaka
   - Due Date: 2026-10-31
   - Expected Impact: API access included in base licensing

3. **Evaluate alternative integration approaches if premium API is unavoidable**
   - Description: SIS framework, LTI Advantage, batch with reduced latency targets
   - Owner: Sam Okafor
   - Due Date: 2026-11-30
   - Expected Impact: architectural fallback that does not require premium tier

**Target Residual Risk After Mitigations:** L1 × I2 = **2 (Low)** ✅

---

### Risk R-013: Savings dependent on later projects (004+) not yet approved

**Category:** FINANCIAL
**Status:** Open
**Risk Owner:** Vernon Ostinato, Chief Financial Officer
**Action Owner:** Cassandra Rhodes — programme sequencing

#### Risk Identification

**Risk Description:**
The September business case justified Project 003 partly on the basis that integration modernisation enables future savings — reduced licence spend through platform rationalisation (Project 004+), eliminated manual effort, and reduced support load. Those savings materialise only if subsequent projects are approved and delivered. Project 003's cost is real; its savings are contingent.

**Root Cause:**
Programme-level benefits are distributed across projects. The investment is front-loaded; the returns are back-loaded and dependent on decisions not yet made.

**Trigger Events:**

- Projects 004+ deferred or cancelled after Project 003 is delivered
- Business case retrospectively assessed as having overstated benefits
- Licence savings do not materialise because rationalisation decisions are not taken

**Consequences if Realized:**

- Project 003 assessed as a cost without proportional benefit
- Integration modernisation positioned as an IT indulgence rather than an investment
- Future programme funding more difficult to secure

**Affected Stakeholders:**

- **Vernon Ostinato**: business case accountability
- **Cassandra Rhodes**: programme investment credibility
- **Prof. Otis Hammond**: programme sponsor

**Related Objectives:**

- **Outcome O-1** (Sustainable integration estate): investment justification

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | Dependent savings on unapproved projects is a common business case weakness |
| **Impact** | 3 — Moderate | Credibility damage; does not prevent the delivered benefit of Project 003 itself |
| **Inherent Risk Score** | **12** (Medium) | 4 × 3 = 12 |

**Risk Zone:** 🟨 Medium (6–12)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Project 003 has standalone benefits**: Eliminated manual effort, improved deprovisioning, reduced integration incidents — benefits that do not depend on 004+
   - Owner: Cassandra Rhodes
   - Effectiveness: **Adequate** — genuine but modest compared to programme-level savings
   - Evidence: STKE Outcomes O-1, O-3

**Overall Control Effectiveness:** Adequate — Project 003's standalone case is real but not sufficient to justify programme-level costs.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 — Unlikely | Programme governance provides a path for 004+ approval; standalone benefits provide a floor |
| **Impact** | 2 — Minor | Reputational only; Project 003's delivered value is independent |
| **Residual Risk Score** | **4** (Low) | 2 × 2 = 4 |

**Risk Zone:** 🟩 Low (1–5)
**Risk Reduction:** 67% (12 → 4)

#### Risk Response (4Ts Framework)

**Primary Response:** TOLERATE — with reporting

**Rationale:**
The contingent savings are inherent to programme-level investment. Treating it would mean approving all subsequent projects now, which is neither practical nor appropriate. The treatment is transparent reporting: quantify Project 003's standalone benefits separately from programme-level savings.

#### Action Plan

1. **Quantify and report Project 003 standalone benefits separately**
   - Owner: Cassandra Rhodes
   - Due Date: 2027-06-30 (post-migration assessment)
   - Expected Impact: demonstrates value independent of programme continuation

**Target Residual Risk:** L2 × I2 = **4 (Low)** ✅ — no further reduction needed

---

### Risk R-014: Data migration creates temporary PI exposure without controls

**Category:** COMPLIANCE
**Status:** Open
**Risk Owner:** Eleanor Frame, Privacy & Records Officer
**Action Owner:** Sam Okafor — migration environment controls
**STKE Cross-Reference:** Maps to STKE Risk R-6; relates to STKE Goal G-2 (manual PI flows eliminated); STKE SD-7 (Frame — migration must not migrate privacy defects)

#### Risk Identification

**Risk Description:**
Bulk data migration from Learn Original to Ultra creates temporary copies of personal information — student submissions, grades, discussion posts, placement records — in a migration environment. Without explicit privacy controls, this environment may be accessible to migration team members beyond those with a legitimate need, retained beyond the cutover period, and lacking the access restrictions that apply in the production systems.

**Root Cause:**
Data migration is treated as a technical exercise. Privacy controls are applied to production systems but not to the migration pipeline between them.

**Trigger Events:**

- Migration environment created without access restriction
- Bulk export from Learn Original includes sensitive data classes that should be segmented
- Migration data retained after cutover without a defined deletion date
- A migration team member accesses student data without authorisation

**Consequences if Realized:**

- APP 6.1 breach — use or disclosure for a purpose other than the original collection purpose
- APP 11.1 breach — personal information not protected by reasonable security safeguards in the migration environment
- Eligible data breach under the NDB scheme if migration data is accessed by unauthorised parties
- OAIC notification and individual notification to affected students

**Affected Stakeholders:**

- **Students**: personal information exposed in migration environment
- **Eleanor Frame**: privacy accountability; NDB assessment if breach occurs
- **Tobias Ohm**: security controls on migration environment
- **Sam Okafor**: migration process design
- **Prof. Stella Groove**: institutional consequence of a notifiable breach

**Related Objectives:**

- **Goal G-2** (Manual PI flows eliminated): the migration itself must not be a new PI exposure
- **Outcome O-3** (Privacy and security posture measurably improved): the migration must not worsen the posture

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | Data migration without explicit privacy controls is the default; controls must be designed and applied deliberately |
| **Impact** | 5 — Catastrophic | NDB notification for a breach involving student personal information in a migration environment would be reputationally devastating and regulatory |
| **Inherent Risk Score** | **20** (Critical) | 4 × 5 = 20 |

**Risk Zone:** 🟥 Critical (20–25)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Data migration plan reviewed by Frame**: STKE SD-7 specifies Frame reviews the migration plan before execution
   - Owner: Eleanor Frame
   - Effectiveness: **Adequate** — the gate is defined but the plan does not yet exist
   - Evidence: STKE SD-7 enablers

2. **Sensitive data classes identified**: Placement records, clearance metadata, and health notes identified as requiring elevated controls
   - Owner: Eleanor Frame
   - Effectiveness: **Adequate** — classification is done; controls are not yet applied
   - Evidence: ARC-003-STKE SD-7

**Overall Control Effectiveness:** Adequate — the intent and classification are in place, but the actual controls (access restriction, retention, deletion) are not implemented.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | No structural controls are in place; the migration environment does not yet exist but will default to unrestricted access |
| **Impact** | 4 — Major | Frame's review gate reduces impact marginally — at least the data classes and risks are identified before migration begins |
| **Residual Risk Score** | **16** (High) | 4 × 4 = 16 |

**Risk Zone:** 🟧 High (13–19)
**Risk Reduction:** 20% (20 → 16)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:**
The controls are straightforward — access restriction, minimisation, retention rule, deletion confirmation — but they must be designed and applied before migration begins. This is a sequencing discipline problem: the privacy controls must be part of the migration design, not an afterthought.

**Alternative Responses Considered:**

- **Tolerate**: Rejected — temporary PI exposure with a real NDB dimension
- **Transfer**: Not applicable — the APP 11 obligation remains with the university regardless
- **Terminate**: Rejected — migration is required; the data must be migrated

#### Risk Appetite Assessment

**Provisional appetite for COMPLIANCE risks:** Low (≤ 9)
**Current residual:** 16 (High)
**Assessment:** ❌ **Exceeds provisional appetite** by 7 points
**Escalation Required:** Yes — Steering Committee immediately. This risk materialises the moment data migration begins.

#### Action Plan

**Additional Mitigations Needed:**

1. **Design data migration with explicit privacy controls**
   - Description: Access restriction on migration environment (named individuals only); data minimisation (migrate only what is needed); retention limit (delete within 30 days of successful cutover); audit log of access
   - Owner: Sam Okafor with Eleanor Frame
   - Due Date: 2026-10-31 (before any data migration begins)
   - Cost: nil — configuration and process design
   - Expected Impact: reduce likelihood 4 → 2

2. **Segment sensitive data classes for separate migration with elevated controls**
   - Description: Placement records, clearance metadata, and health notes migrated separately with Frame's sign-off per batch
   - Owner: Eleanor Frame with Sam Okafor
   - Due Date: 2026-10-31
   - Cost: nil
   - Expected Impact: reduce impact 4 → 3

3. **Confirm migration data deletion after successful cutover**
   - Description: Defined deletion date; deletion confirmed and evidenced; Frame signs off
   - Owner: Sam Okafor
   - Due Date: Within 30 days of each migration phase cutover
   - Cost: nil
   - Expected Impact: limits the exposure window

**Target Residual Risk After Mitigations:** L2 × I3 = **6 (Medium)** ✅ within Medium threshold; still above Low compliance appetite, requiring formal acceptance

**Success Criteria:**

- Migration environment access restricted to named individuals with a legitimate need
- All migration data deleted within 30 days of successful cutover, with deletion confirmed
- Zero unauthorised accesses to migration data
- Sensitive data classes migrated with elevated controls and Frame's sign-off

**Monitoring Plan:**

- **Frequency:** At each migration phase
- **Key Indicators:** migration environment access list; data retention status; deletion confirmation
- **Escalation Triggers:** any unauthorised access to migration data; migration data retained beyond 30 days post-cutover

---

### Risk R-015: Manual PI flows replicated "temporarily" and never remediated

**Category:** COMPLIANCE
**Status:** Open
**Risk Owner:** Eleanor Frame, Privacy & Records Officer
**Action Owner:** Sam Okafor — integration delivery
**STKE Cross-Reference:** Relates to STKE SD-7 (Frame — migration must not migrate privacy defects); STKE Goal G-2 (manual flows eliminated)

#### Risk Identification

**Risk Description:**
The existing manual flows — CSV provisioning, flat-file transfers, placement grade re-keying — are replicated in the Ultra environment "temporarily" pending the integration re-engineering, and are never remediated. The migration succeeds in moving the platform but fails to eliminate the privacy defects that were a primary justification for the project.

**Root Cause:**
Migration and integration re-engineering are different work streams with different timelines. The migration can proceed without the integration re-engineering, and expediency creates pressure to defer the harder work. "We'll fix it in Phase 2" is the estate's most predictable failure mode.

**Trigger Events:**

- Migration Phase 1 proceeds with manual flows replicated because integration re-engineering is not ready
- "Temporary" workarounds are accepted without a remediation deadline
- Integration team capacity consumed by dual-running, leaving no capacity for new-build (R-005)
- ADR-002 delay (R-002) blocks role assignment automation

**Consequences if Realized:**

- Privacy findings from Project 001 persist indefinitely on the new platform
- The project's compliance justification — eliminating manual PI handling — is defeated
- Manual re-keying of placement grades continues with the same APP 11 exposure
- The project is assessed as having achieved a platform upgrade but not an architecture improvement

**Affected Stakeholders:**

- **Eleanor Frame**: privacy findings unresolved despite the project's stated objective
- **Prof. Priya Anand**: placement grade re-keying continues
- **Sam Okafor**: the architecture he designed is not delivered
- **Cassandra Rhodes**: integration investment produced a platform change, not an architecture change

**Related Objectives:**

- **Goal G-2** (Manual PI flows eliminated): directly defeated
- **Outcome O-3** (Privacy and security posture measurably improved): not achieved
- **Outcome O-1** (Sustainable integration estate): manual flows are the opposite of sustainable

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | "Temporary" workarounds becoming permanent is the single most common failure mode in integration programmes |
| **Impact** | 4 — Major | The project's compliance and architecture justification is defeated; privacy exposure continues indefinitely |
| **Inherent Risk Score** | **16** (High) | 4 × 4 = 16 |

**Risk Zone:** 🟧 High (13–19)

#### Current Controls and Mitigations

**Existing Controls:**

1. **CSF-4 explicitly prohibits migrating manual flows in their current form**
   - Owner: Prof. Otis Hammond
   - Effectiveness: **Weak** — the CSF exists on paper but has no enforcement mechanism; expediency will override it under schedule pressure
   - Evidence: ARC-003-STKE-v1.0 CSF-4

2. **Integration re-engineering phased by risk**: Phase 2 targets the highest-privacy-impact flows
   - Owner: Sam Okafor
   - Effectiveness: **Adequate** — the sequencing is sound but the delivery is not yet funded or staffed
   - Evidence: STKE Conflict C-2 resolution

**Overall Control Effectiveness:** Weak — the aspiration is clear but the enforcement is absent. This is the register's most predictable failure.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | CSF-4 has no enforcement mechanism; schedule pressure during migration will create "just for now" compromises |
| **Impact** | 4 — Major | Unchanged — the consequence is the same whether the manual flow is on Learn Original or Ultra |
| **Residual Risk Score** | **16** (High) | 4 × 4 = 16 |

**Risk Zone:** 🟧 High (13–19)
**Risk Reduction:** 0% — this is the only risk in the register with zero reduction, and that is a deliberate assessment

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:**
The treatment is to make temporary workarounds structurally impossible to persist. Every manual flow that is replicated temporarily must have a hard remediation deadline, a named owner, and a Steering Committee report trigger if the deadline passes.

**Alternative Responses Considered:**

- **Tolerate**: Rejected — this defeats the project's stated purpose
- **Transfer**: Not applicable
- **Terminate**: Considered — refusing to migrate until integrations are ready eliminates the risk but delays the entire programme

#### Risk Appetite Assessment

**Provisional appetite for COMPLIANCE risks:** Low (≤ 9)
**Current residual:** 16 (High)
**Assessment:** ❌ **Exceeds provisional appetite** by 7 points — tied with R-014 for the largest compliance exceedance
**Escalation Required:** Yes — Steering Committee. This risk must be explicitly accepted or treated before migration begins.

#### Action Plan

**Additional Mitigations Needed:**

1. **Attach a hard remediation deadline to every temporary manual flow**
   - Description: Any manual flow replicated on Ultra must have: a named owner, a funded remediation plan, and a date. If the date passes, the flow is reported to Steering Committee automatically.
   - Owner: Eleanor Frame with Sam Okafor
   - Due Date: 2026-10-31 (before migration Phase 1)
   - Cost: nil
   - Expected Impact: reduce likelihood 4 → 3 (structural accountability)

2. **Fund and staff the integration re-engineering independently of the migration**
   - Description: Integration re-engineering capacity is not contingent on migration schedule or budget — it has its own staffing and timeline
   - Owner: Cassandra Rhodes
   - Due Date: 2026-10-31
   - Cost: within integration business case provision
   - Expected Impact: reduce likelihood 3 → 2

3. **Prohibit Learn Original decommission until all manual flows are remediated**
   - Description: Learn Original is not retired until the corresponding automated integration is live on Ultra — this creates a forcing function because Learn Original maintenance costs pressure the timeline
   - Owner: Cassandra Rhodes
   - Due Date: N/A — ongoing condition
   - Expected Impact: creates economic pressure to remediate

**Target Residual Risk After Mitigations:** L2 × I3 = **6 (Medium)** ✅ within Medium threshold; formal acceptance required for compliance category

**Success Criteria:**

- Zero manual PI flows remaining on Ultra 12 months after migration
- Every temporary workaround has a remediation date in the register
- Steering Committee receives monthly reporting on outstanding temporary flows

**Monitoring Plan:**

- **Frequency:** Monthly
- **Key Indicators:** count of manual PI flows on Ultra; days past remediation deadline
- **Escalation Triggers:** any temporary flow passing its remediation deadline; any new manual flow created on Ultra without prior approval

---

### Risk R-016: Ultra SSO/MFA configuration incomplete at go-live — local accounts persist

**Category:** COMPLIANCE
**Status:** Open
**Risk Owner:** Tobias Ohm, Cybersecurity Lead
**Action Owner:** Sam Okafor with Anthology — Ultra SSO configuration
**STKE Cross-Reference:** Relates to STKE SD-8 (Ohm — Ultra closes security gap); Principle P16 (Layered Security Posture)

#### Risk Identification

**Risk Description:**
Ultra is deployed with SSO/MFA enforcement incomplete — administrative accounts, integration service accounts, or test accounts using local credentials rather than institutional SSO. This perpetuates the local-account exception that the migration was supposed to eliminate, and breaches Principle 16 (CRITICAL priority).

**Root Cause:**
Ultra's SSO/MFA configuration requires Anthology cooperation and may have technical limitations for certain account types (admin, service, sandbox). Expediency during migration creates pressure to use local accounts "temporarily".

**Trigger Events:**

- Ultra admin accounts configured with local credentials during initial setup and not migrated to SSO
- Integration service accounts using basic authentication rather than OAuth 2.0
- Test environments using local accounts that persist into production
- Anthology requiring local admin accounts for support purposes

**Consequences if Realized:**

- ASD Essential Eight ML2 target for MFA not achieved through migration
- Principle 16 (CRITICAL) violated — local accounts breach the layered security posture
- Two local-account exceptions become four — the migration increases rather than decreases the security gap
- Cybersecurity assessment identifies the migration as having worsened the security posture

**Affected Stakeholders:**

- **Tobias Ohm**: E8 target accountability
- **Cassandra Rhodes**: E8 programme sponsor
- **Sam Okafor**: integration credentials

**Related Objectives:**

- **Outcome O-3** (Privacy and security posture measurably improved): defining metric

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | Local accounts are the default in initial platform setup; SSO enforcement requires explicit configuration and testing |
| **Impact** | 4 — Major | Principle 16 (CRITICAL) breached; E8 ML2 target missed; migration worsens security posture |
| **Inherent Risk Score** | **16** (High) | 4 × 4 = 16 |

**Risk Zone:** 🟧 High (13–19)

#### Current Controls and Mitigations

**Existing Controls:**

1. **SSO/MFA enforcement defined as a go-live gate**: STKE SD-8 specifies no local accounts from day one
   - Owner: Tobias Ohm
   - Effectiveness: **Adequate** — the requirement is stated; the technical feasibility with Anthology is unconfirmed
   - Evidence: STKE SD-8; Principle P16

2. **OAuth 2.0 specified for integration credentials**: ADR-001 requires service-to-service authentication
   - Owner: Sam Okafor
   - Effectiveness: **Adequate** — architectural requirement exists; implementation not yet designed

**Overall Control Effectiveness:** Adequate — reduces likelihood from 4 to 3.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 — Possible | The requirement is clear but Anthology's technical constraints are unknown |
| **Impact** | 4 — Major | Unchanged — a CRITICAL principle breach |
| **Residual Risk Score** | **12** (Medium) | 3 × 4 = 12 |

**Risk Zone:** 🟨 Medium (6–12)
**Risk Reduction:** 25% (16 → 12)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

#### Risk Appetite Assessment

**Provisional appetite for COMPLIANCE risks:** Low (≤ 9)
**Current residual:** 12 (Medium)
**Assessment:** ❌ **Exceeds provisional appetite** by 3 points
**Escalation Required:** Report to Steering Committee; Ohm to confirm with Anthology.

#### Action Plan

1. **Confirm Ultra SSO/MFA configuration capability with Anthology**
   - Description: Verify that all account types — admin, service, test — can use institutional SSO/MFA. Identify any Anthology requirements for local admin accounts.
   - Owner: Tobias Ohm with Anthology
   - Due Date: 2026-10-31
   - Expected Impact: reduce likelihood 3 → 2 (confirmation eliminates uncertainty)

2. **Design OAuth 2.0 service accounts for all integrations**
   - Owner: Sam Okafor
   - Due Date: 2026-11-30
   - Expected Impact: eliminates basic-auth integration credentials

3. **If local accounts are technically required, apply compensating controls and set a remediation date**
   - Description: Short-lived credentials, monitored access, no shared accounts, reviewed quarterly
   - Owner: Tobias Ohm
   - Due Date: 2026-12-31
   - Expected Impact: reduce impact 4 → 3 (compensating controls)

**Target Residual Risk After Mitigations:** L2 × I3 = **6 (Medium)** ✅ within Medium; formal acceptance for compliance category

---

### Risk R-017: Cross-border data position unresolved for Ultra hosting region

**Category:** COMPLIANCE
**Status:** Open
**Risk Owner:** Eleanor Frame, Privacy & Records Officer
**Action Owner:** Grace Tanaka — vendor confirmation
**STKE Cross-Reference:** Inherits from ARC-001-RISK R-017; relates to STKE SD-7 (Frame)

#### Risk Identification

**Risk Description:**
Ultra's hosting region has not been confirmed with Anthology. If Ultra is hosted outside Australia, the migration moves student personal information — submissions, grades, discussion posts, placement records — to an offshore location without an APP 8 cross-border assessment. The same gap identified in ARC-001-RISK-v1.0 for the broader estate now applies specifically and acutely to the LMS migration.

**Root Cause:**
Hosting region was not captured as a procurement attribute in the original Blackboard contract, and no APP 8 assessment exists for the current arrangement.

**Trigger Events:**

- Anthology confirms Ultra is hosted outside Australia
- Migration proceeds without hosting region confirmation
- A privacy complaint or access request exposes the absence of assessment
- Anthology changes hosting region during or after migration

**Consequences if Realized:**

- APP 8.1 breach — university remains accountable for overseas handling
- OAIC engagement with no documented assessment to produce
- Migration may need to be revisited if cross-border position is unacceptable
- Student trust in the handling of their submissions and grades

**Affected Stakeholders:**

- **Students**: personal information held offshore without assessment
- **Eleanor Frame**: compliance accountability
- **Grace Tanaka**: contractual terms for hosting region
- **Prof. Stella Groove**: institutional consequence

**Related Objectives:**

- **Outcome O-3** (Privacy and security posture measurably improved): cross-border position is a privacy metric

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 — Possible | Anthology may host in Australia; the risk is that nobody has confirmed |
| **Impact** | 4 — Major | Regulatory exposure; potential reopening of migration decision |
| **Inherent Risk Score** | **12** (Medium) | 3 × 4 = 12 |

**Risk Zone:** 🟨 Medium (6–12)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Hosting region modelled as a governed attribute** (from ARC-001-DATA-v1.0)
   - Owner: Sam Okafor
   - Effectiveness: **Adequate** — the data structure exists; it is unpopulated for Ultra
   - Evidence: ARC-001-DATA-v1.0 E-018

**Overall Control Effectiveness:** Weak — the structure exists; the confirmation does not.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 — Possible | No change — nobody has asked Anthology |
| **Impact** | 4 — Major | Unchanged |
| **Residual Risk Score** | **12** (Medium) | 3 × 4 = 12 |

**Risk Zone:** 🟨 Medium (6–12)
**Risk Reduction:** 0% — this is a verification risk; checking costs nothing

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:**
This is the cheapest reduction available in the register. Confirm the hosting region with Anthology. If it is Australia, the risk drops to Low. If it is offshore, the APP 8 assessment must be completed before migration begins.

#### Risk Appetite Assessment

**Provisional appetite for COMPLIANCE risks:** Low (≤ 9)
**Current residual:** 12 (Medium)
**Assessment:** ❌ **Exceeds provisional appetite** by 3 points
**Escalation Required:** Yes — but resolution requires a single email to Anthology.

#### Action Plan

1. **Confirm Ultra hosting region with Anthology in writing**
   - Owner: Grace Tanaka
   - Due Date: 2026-08-31
   - Cost: nil — one email
   - Expected Impact: if Australian, reduce likelihood 3 → 1; if offshore, trigger APP 8 assessment

2. **If offshore: complete APP 8 cross-border assessment before migration**
   - Owner: Eleanor Frame
   - Due Date: 2026-10-31
   - Cost: assessment time
   - Expected Impact: reduce impact 4 → 3 (assessed position replaces unknown position)

3. **Include hosting region and change notification provisions in the contract renewal**
   - Owner: Grace Tanaka
   - Due Date: 2026-10-31
   - Expected Impact: prevents future hosting region changes without notice

**Target Residual Risk After Mitigations:** L1 × I3 = **3 (Low)** ✅ within provisional appetite

---

### Risk R-018: Assessment-period disruption during migration

**Category:** REPUTATIONAL
**Status:** Open
**Risk Owner:** Prof. Otis Hammond, DVC (Education)
**Action Owner:** Rhonda Bell — migration scheduling
**STKE Cross-Reference:** Relates to STKE Goal G-3 (zero assessment-period disruption); STKE CSF-1

#### Risk Identification

**Risk Description:**
A migration-related failure — content corruption, integration outage, authentication failure — occurs during an assessment or examination period. Students cannot submit, access grades, or complete examinations. The incident is publicly visible, reported by media, and damages the university's reputation with prospective students and regulators (TEQSA).

**Root Cause:**
Migration introduces change to a production system used by students during high-stakes assessment. The risk is inherent in any migration that cannot be completed entirely outside assessment windows.

**Trigger Events:**

- Migration phase overlaps with assessment period due to schedule pressure (R-010)
- Integration failure during cutover affects student access during assessment
- Rollback required during assessment period and fails (R-022)
- Content migration corruption not detected before assessment

**Consequences if Realized:**

- Students unable to complete assessment — fairness and equity failure
- Media coverage of assessment disruption
- TEQSA review of assessment integrity during transition
- Prospective student confidence reduced
- Education Committee confidence in technology governance lost

**Affected Stakeholders:**

- **Students**: directly and immediately affected
- **Jazmin Field**: student advocacy
- **A/Prof. Pearl Clavinet**: academic quality accountability
- **Prof. Stella Groove**: institutional reputation
- **Prof. Otis Hammond**: sponsor accountability

**Related Objectives:**

- **Goal G-3** (Zero assessment-period disruption): the defining metric
- **Outcome O-2** (Academic community adopted Ultra without disruption)

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 — Possible | Migration failures are common; the phasing plan is designed to prevent assessment-period overlap, but schedule pressure is real |
| **Impact** | 5 — Catastrophic | Assessment disruption: regulatory, reputational, student fairness — the highest-consequence scenario |
| **Inherent Risk Score** | **15** (High) | 3 × 5 = 15 |

**Risk Zone:** 🟧 High (13–19)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Assessment-period change freeze**: No migration during assessment or examination periods
   - Owner: Rhonda Bell
   - Effectiveness: **Adequate** — planned but not yet enforced as a governance rule
   - Evidence: STKE CSF-1

2. **Pilot programme**: Migration tested before broad rollout
   - Owner: Dr. Benny Moog
   - Effectiveness: **Adequate** — catches issues before they reach assessment

3. **Go/no-go gates per migration phase**
   - Owner: Prof. Otis Hammond
   - Effectiveness: **Adequate** — decision authority exists; criteria not yet defined

**Overall Control Effectiveness:** Adequate — reduces likelihood from 3 to 2. Impact is unchanged because the consequence of assessment disruption is independent of controls.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 — Unlikely | Change freeze and phasing substantially reduce the probability of assessment-period impact |
| **Impact** | 5 — Catastrophic | Unchanged — assessment disruption carries the highest consequence regardless of controls |
| **Residual Risk Score** | **10** (Medium) | 2 × 5 = 10 |

**Risk Zone:** 🟨 Medium (6–12)
**Risk Reduction:** 33% (15 → 10)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

#### Action Plan

1. **Enforce assessment-period change freeze as a governance rule with no exceptions** (shared with R-001)
   - Owner: Prof. Otis Hammond
   - Due Date: 2026-09-30
   - Expected Impact: eliminates the highest-consequence trigger

2. **Test rollback capability before each migration phase** (shared with R-001, R-022)
   - Owner: Sam Okafor
   - Due Date: Before each phase cutover
   - Expected Impact: credible fallback if issues emerge

**Target Residual Risk After Mitigations:** L1 × I4 = **4 (Low)** ✅

---

### Risk R-019: Student experience degrades during transition

**Category:** REPUTATIONAL
**Status:** Open
**Risk Owner:** A/Prof. Pearl Clavinet, Dean of Learning & Teaching
**Action Owner:** Dr. Benny Moog — Ultra configuration
**STKE Cross-Reference:** Relates to STKE SD-13 (Field — students not the experiment); STKE Goal G-4

#### Risk Identification

**Risk Description:**
During the transition period, students experience broken content, inconsistent navigation between migrated and unmigrated units, inaccessible materials, or confusion about which platform to use. The degradation is distributed across many small issues rather than a single incident, producing a pervasive sense that "the system doesn't work".

**Root Cause:**
A phased migration necessarily creates a period where some units are on Learn Original and others on Ultra. Students taking units across faculties may be navigating two systems simultaneously.

**Trigger Events:**

- Content migration producing broken links, missing images, or lost formatting
- Students with units on both platforms confused about which to use
- Accessibility regression in Ultra not caught before rollout (WCAG 2.2 AA)
- Mobile experience degraded during transition

**Consequences if Realized:**

- Student satisfaction survey results decline during transition
- Student Guild raises concerns publicly
- Support load spikes across both platforms
- Negative perception of the migration persists after completion

**Affected Stakeholders:**

- **Students**: direct and immediate
- **Jazmin Field**: advocacy role
- **Dr. Wynton Castle**: feels validated in his concern that content would break
- **A/Prof. Pearl Clavinet**: quality accountability

**Related Objectives:**

- **Goal G-4** (Consistent accessible templates): the mitigation for this risk
- **Outcome O-2** (Academic community adopted Ultra without disruption)

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 — Possible | Phased migration necessarily creates inconsistency; content issues are likely in at least some units |
| **Impact** | 3 — Moderate | Distributed quality degradation; recoverable but damaging to student perception |
| **Inherent Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6–12)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Student communication plan for each migration phase**
   - Owner: Dr. Felix Marimba
   - Effectiveness: **Adequate** — planned
   - Evidence: STKE SD-13 enablers

2. **Content migration success rate target (> 95%)**
   - Owner: Dr. Benny Moog
   - Effectiveness: **Adequate** — target set; verification method defined

3. **Student Guild representative in pilot programme**
   - Owner: Dr. Benny Moog
   - Effectiveness: **Adequate** — agreed

**Overall Control Effectiveness:** Adequate — reduces likelihood from 3 to 2.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 — Unlikely | Communications and content verification reduce but cannot eliminate inconsistency during transition |
| **Impact** | 3 — Moderate | Unchanged |
| **Residual Risk Score** | **6** (Medium) | 2 × 3 = 6 |

**Risk Zone:** 🟨 Medium (6–12)
**Risk Reduction:** 33% (9 → 6)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

#### Action Plan

1. **Verify content migration on representative units before each faculty cutover**
   - Owner: Dr. Benny Moog
   - Due Date: Per faculty phase
   - Expected Impact: catches broken content before students encounter it

2. **Provide single-entry-point navigation during dual-platform period** (Principle 1)
   - Owner: Sam Okafor
   - Due Date: Before first faculty migration
   - Expected Impact: reduces student confusion about which platform to use

**Target Residual Risk After Mitigations:** L1 × I2 = **2 (Low)** ✅

---

### Risk R-020: PeopleSoft event publication capability insufficient for near-real-time

**Category:** TECHNOLOGY
**Status:** Open
**Risk Owner:** Sam Okafor, Integration Architect
**Action Owner:** Sam Okafor — technical assessment
**STKE Cross-Reference:** Relates to STKE Goal G-1 (< 15 minutes propagation); Principle P11 (Event-Driven Near-Real-Time)

#### Risk Identification

**Risk Description:**
PeopleSoft's Integration Broker may not support event publication at the frequency, reliability, or format required for near-real-time propagation (< 15 minutes). The PeopleSoft instance may require custom development to publish enrolment, withdrawal, and role-change events, which adds cost, schedule, and maintenance burden.

**Root Cause:**
PeopleSoft is an on-premises ERP system not designed for event-driven integration. Its Integration Broker exists but its capability for the university's specific configuration has not been assessed.

**Trigger Events:**

- Integration Broker assessment reveals that event publication is not configured or supported
- Custom development required exceeds budget or timeline
- PeopleSoft upgrade path conflicts with custom event publication
- Event throughput insufficient for peak enrolment periods

**Consequences if Realized:**

- G-1 (< 15 minutes propagation) unachievable
- Near-real-time architecture falls back to scheduled polling — "faster batch" rather than event-driven
- Deprovisioning latency improvement limited
- ADR-001's architecture proven impractical for the estate's most important source system

**Affected Stakeholders:**

- **Sam Okafor**: integration architecture feasibility
- **Cassandra Rhodes**: integration investment at risk
- **Student Administration**: PeopleSoft is their system
- **Tobias Ohm**: deprovisioning latency (security)

**Related Objectives:**

- **Goal G-1** (PeopleSoft → Ultra event-driven): foundational dependency
- **Outcome O-1** (Sustainable integration estate)

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 — Likely | PeopleSoft event publication capability is commonly limited; the university's configuration is untested |
| **Impact** | 4 — Major | Near-real-time target missed; architecture compromise for the most critical integration |
| **Inherent Risk Score** | **16** (High) | 4 × 4 = 16 |

**Risk Zone:** 🟧 High (13–19)

#### Current Controls and Mitigations

**Existing Controls:**

1. **ADR-001 acknowledges PeopleSoft as the highest-risk integration point**
   - Owner: Sam Okafor
   - Effectiveness: **Adequate** — the risk is identified; the capability is unassessed
   - Evidence: ARC-001-ADR-001-v1.0

2. **Principle 19 allows scheduled polling as a declared exception**: If event publication is not feasible, a "faster batch" with a declared review date is acceptable under Principle 19
   - Owner: Sam Okafor
   - Effectiveness: **Adequate** — provides an architectural fallback
   - Evidence: ARC-000-PRIN-v1.1 Principle 19

**Overall Control Effectiveness:** Adequate — the fallback exists, but the capability has not been assessed.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 — Unlikely | Assessment may confirm capability; even if limited, the fallback is architecturally acceptable |
| **Impact** | 3 — Moderate | Reduced from Major because the "faster batch" fallback achieves most of the benefit |
| **Residual Risk Score** | **6** (Medium) | 2 × 3 = 6 |

**Risk Zone:** 🟨 Medium (6–12)
**Risk Reduction:** 63% (16 → 6)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:**
This is a verification risk. Assess PeopleSoft Integration Broker capability early — it is cheap to check and expensive to discover late.

#### Action Plan

1. **Assess PeopleSoft Integration Broker event publication capability**
   - Owner: Sam Okafor with Student Administration
   - Due Date: 2026-09-30
   - Cost: nil — technical assessment
   - Expected Impact: confirms capability or triggers fallback design early

2. **If event publication is insufficient: design "faster batch" with defined latency target**
   - Description: Scheduled polling at 5–15 minute intervals as a declared Principle 19 exception with a review date
   - Owner: Sam Okafor
   - Due Date: 2026-10-31
   - Expected Impact: achieves most of the latency improvement without custom PeopleSoft development

**Target Residual Risk After Mitigations:** L1 × I2 = **2 (Low)** ✅

---

### Risk R-021: Ultra LTI 1.3 implementation breaks discipline tool behaviour

**Category:** TECHNOLOGY
**Status:** Open
**Risk Owner:** Dr. Benny Moog, Director Learning Technologies
**Action Owner:** Sam Okafor — LTI integration testing
**STKE Cross-Reference:** Relates to STKE Goal G-6 (discipline tool integrations verified); STKE SD-12 (Key — discipline tools work)

#### Risk Identification

**Risk Description:**
Ultra's LTI 1.3 Advantage implementation differs from Learn Original's LTI implementation in ways that break discipline tool behaviour — MuseScore notation rendering, Ableton Live session embedding, iSimulate device integration, or ExamSoft proctoring flow. Discipline tools that work in Learn Original fail or degrade in Ultra.

**Root Cause:**
LTI specifications allow implementation variation. Ultra's content model and iframe handling differ from Learn Original. Discipline tools often use edge-case LTI features (deep linking, grade passback, custom parameters) that are most susceptible to implementation differences.

**Trigger Events:**

- LTI integration testing reveals failures in discipline tool behaviour
- Discipline tool vendors slow to certify Ultra compatibility
- Edge-case LTI features (deep linking, custom parameters) not supported in Ultra's LTI implementation
- Ultra LTI implementation changes in an Ultra update after initial testing

**Consequences if Realized:**

- Discipline-specific units unusable on Ultra — Music & Performing Arts, Health Sciences most affected
- Migration perceived as the consolidation that Project 001's governance was supposed to prevent
- Prof. Desmond Key withdraws support for migration
- Faculty migration delayed; timeline cascades

**Affected Stakeholders:**

- **Prof. Desmond Key**: discipline tools are his primary concern
- **Prof. Priya Anand**: clinical simulation tools
- **Dr. Benny Moog**: LTI configuration
- **Sam Okafor**: integration testing

**Related Objectives:**

- **Goal G-6** (Discipline tool integrations verified): directly at risk
- **Outcome O-2** (Academic community adopted Ultra without disruption)

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 — Possible | LTI implementation differences are common across LMS platforms; discipline tools use edge cases |
| **Impact** | 4 — Major | Faculty-critical tools broken; migration delayed or compromised for affected disciplines |
| **Inherent Risk Score** | **12** (Medium) | 3 × 4 = 12 |

**Risk Zone:** 🟨 Medium (6–12)

#### Current Controls and Mitigations

**Existing Controls:**

1. **LTI verification included in pilot programme**: Discipline tools tested in Ultra sandpit
   - Owner: Dr. Benny Moog
   - Effectiveness: **Adequate** — planned but not commenced
   - Evidence: STKE SD-12 enablers

2. **Faculty sign-off before migration phase**: Key and Anand approve before their faculties migrate
   - Owner: Rhonda Bell
   - Effectiveness: **Adequate** — gate exists

**Overall Control Effectiveness:** Adequate — catches issues before they affect teaching, if testing is thorough.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 — Unlikely | Testing in pilot will catch most issues; the risk is undiscovered edge cases |
| **Impact** | 4 — Major | Unchanged for affected disciplines — a broken tool is a broken tool |
| **Residual Risk Score** | **8** (Medium) | 2 × 4 = 8 |

**Risk Zone:** 🟨 Medium (6–12)
**Risk Reduction:** 33% (12 → 8)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

#### Action Plan

1. **Test all discipline tool LTI integrations in Ultra sandpit before pilot**
   - Owner: Sam Okafor with discipline tool vendors
   - Due Date: 2026-11-30
   - Expected Impact: identifies failures before they affect teaching

2. **Engage discipline tool vendors on Ultra LTI 1.3 certification**
   - Owner: Dr. Benny Moog
   - Due Date: 2026-10-31
   - Expected Impact: vendor confirmation or identified gaps

3. **Design faculty-specific migration contingency if discipline tools cannot be migrated**
   - Description: Faculty remains on Learn Original until LTI issues are resolved; not ideal but protects teaching
   - Owner: Rhonda Bell
   - Due Date: 2026-12-31
   - Expected Impact: reduces impact 4 → 3 (fallback for affected faculties)

**Target Residual Risk After Mitigations:** L2 × I3 = **6 (Medium)** ✅

---

### Risk R-022: Rollback capability not genuinely tested before cutover

**Category:** TECHNOLOGY
**Status:** Open
**Risk Owner:** Sam Okafor, Integration Architect
**Action Owner:** Sam Okafor with Anthology — rollback testing
**STKE Cross-Reference:** Relates to STKE Goal G-3 (zero assessment-period disruption); STKE SD-6 (Castle — migration scheduled with rollback option)

#### Risk Identification

**Risk Description:**
The migration plan includes a rollback capability — the ability to revert from Ultra to Learn Original if critical issues emerge after cutover — but this capability has not been tested against representative content and integrations. An untested rollback is not a rollback; it is an assumption.

**Root Cause:**
Rollback testing is expensive and disruptive — it requires a full restore from Ultra to Learn Original and verification that content, grades, and integrations are intact. The temptation is to assume the vendor tooling works and skip the test.

**Trigger Events:**

- Cutover proceeds without a prior rollback test
- A critical issue emerges after cutover and rollback is attempted but fails
- Rollback testing reveals that data created in Ultra (new grades, submissions) cannot be reverse-migrated

**Consequences if Realized:**

- A critical migration failure with no fallback — the worst-case scenario
- Data loss (grades, submissions entered in Ultra after cutover)
- Forced forward on a broken platform; manual remediation during teaching
- Programme credibility destroyed (R-001, R-004)

**Affected Stakeholders:**

- **Sam Okafor**: rollback capability owner
- **Rhonda Bell**: migration scheduling
- **Dr. Benny Moog**: platform readiness
- **Students**: data loss risk

**Related Objectives:**

- **Goal G-3** (Zero assessment-period disruption): rollback is the last line of defence
- **Outcome O-2** (Academic community adopted Ultra without disruption)

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 — Possible | Skipping rollback testing is common; the capability is plausible but unverified |
| **Impact** | 3 — Moderate | If rollback is needed and fails, consequences are severe — but rollback is a contingency, not a primary path |
| **Inherent Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6–12)

#### Current Controls and Mitigations

**Existing Controls:**

1. **Rollback included in go/no-go criteria** (R-001 action plan)
   - Owner: Rhonda Bell
   - Effectiveness: **Adequate** — the requirement is stated; testing has not occurred
   - Evidence: R-001 action plan

**Overall Control Effectiveness:** Adequate — the requirement is stated.

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 — Unlikely | Go/no-go criteria include rollback test; the gate should prevent untested cutover |
| **Impact** | 3 — Moderate | Unchanged |
| **Residual Risk Score** | **6** (Medium) | 2 × 3 = 6 |

**Risk Zone:** 🟨 Medium (6–12)
**Risk Reduction:** 33% (9 → 6)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:**
This is a verification risk. Test the rollback. If it works, the risk drops. If it does not, redesign the cutover approach before it matters.

#### Action Plan

1. **Execute a full rollback test on a representative migration in the test environment** (shared with R-001)
   - Owner: Sam Okafor with Anthology
   - Due Date: 2026-11-30
   - Cost: within migration scope
   - Expected Impact: reduce likelihood 2 → 1; confirms or disproves rollback capability

2. **If rollback testing reveals data loss: redesign cutover approach**
   - Description: Consider parallel-running with data synchronisation rather than hard cutover; accept that Ultra-native data cannot be reverse-migrated
   - Owner: Sam Okafor
   - Due Date: 2026-12-31
   - Expected Impact: alternative approach that does not depend on rollback

**Target Residual Risk After Mitigations:** L1 × I2 = **2 (Low)** ✅

---

## D. Risk Category Analysis

### STRATEGIC Risks (4)

**Average inherent:** 14.0 · **Average residual:** 9.8 · **Reduction:** 30%

**Key themes:** Every strategic risk in this register is a **credibility** risk rather than a delivery risk. R-001 and R-004 both describe the same concern from different angles — that a visible failure in this project discredits the entire L&T programme. R-002 is a decision risk inherited from Project 001. R-003 is a positioning risk that determines whether adoption is willing or grudging. None of these is solved by more technology; all are solved by sequencing discipline, communications, and governance.

**Pattern recognition:** R-001 and R-004 are the same defect viewed at different altitudes. R-001 is the project-level consequence (migration disruption); R-004 is the programme-level consequence (strategy discredited). Treating R-001 treats R-004 — they share the same controls and the same action plan.

**Highest:** R-001 (12) — at provisional appetite threshold.

### OPERATIONAL Risks (6)

**Average inherent:** 11.5 · **Average residual:** 8.5 · **Reduction:** 26%

**Key themes:** The weakest reduction of any category (tied with compliance), for the same structural reason as in Project 001 — these are pre-existing estate conditions (single-person dependency, manual workarounds) amplified by the migration. R-005 (dual-running) is the single most consequential operational risk and the only one whose mitigation requires money. R-008 (course cloning dependency) is a fragility that has existed for years and becomes critical during migration. R-009 (vendor PS) and R-010 (timeline compression) are delivery risks that can be traded off against each other — more time reduces vendor dependency; more vendor PS reduces timeline pressure.

**Highest:** R-005 (12) — at provisional appetite threshold.

### FINANCIAL Risks (3)

**Average inherent:** 12.0 · **Average residual:** 5.7 · **Reduction:** 53%

**Key themes:** The strongest reduction of any category (53%), largely because the controls are commercial rather than operational — Anthology contract negotiation resolves R-011 and R-012 directly. R-013 is a structural programme risk tolerated with transparent reporting. The financial risks are the least concerning category in this register.

**Highest:** R-011 (9) — within appetite.

### COMPLIANCE Risks (4)

**Average inherent:** 16.0 · **Average residual:** 14.0 · **Reduction:** 12%

**Key themes:** The highest average inherent score, the weakest reduction by a substantial margin, and the source of both top-ranked residual risks. The pattern is identical to Project 001: compliance risks are uncontrolled, not merely unmitigated. R-014 and R-015 are **the same defect from two angles**: R-014 is the risk that migration *creates* new PI exposure; R-015 is the risk that migration *fails to eliminate* existing PI exposure. Together they say the same thing — the migration must improve the privacy position, not replicate or worsen it. R-016 (local accounts) and R-017 (cross-border) are both verification risks that are cheap to reduce by checking.

**Highest:** R-014 (16), R-015 (16) — the two largest appetite exceedances.

### REPUTATIONAL Risks (2)

**Average inherent:** 12.0 · **Average residual:** 8.0 · **Reduction:** 33%

**Key themes:** Both reputational risks are consequences of risks in other categories. R-018 follows from R-001 (migration disruption) and R-010 (timeline compression). R-019 follows from R-006 (content migration) and R-007 (academic resistance). Treating the upstream risks treats these.

**Highest:** R-018 (10) — within appetite but carries the highest single impact rating (5).

### TECHNOLOGY Risks (3)

**Average inherent:** 12.3 · **Average residual:** 6.7 · **Reduction:** 46%

**Key themes:** All three are **verification risks** — the architecture assumes things nobody has checked. R-020 assumes PeopleSoft can publish events. R-021 assumes Ultra's LTI works for discipline tools. R-022 assumes rollback works. All three are cheap to verify and expensive to discover late. The cheapest risk reduction in the register is testing these assumptions early.

**Highest:** R-021 (8) — within appetite.

---

## E. Risk Ownership Matrix

| Stakeholder | Role | Owned Risks | High Risks | Notes |
|-------------|------|-------------|------------|-------|
| Eleanor Frame | Privacy & Records Officer | R-014, R-015, R-017 | 2 | **Heaviest concentration of High risk in the register.** Both top-ranked risks sit with a MEDIUM-influence stakeholder — the same governance mismatch identified in ARC-001-RISK-v1.0. |
| Sam Okafor | Integration Architect | R-005, R-008, R-020, R-022 | 0 | Four risks; the operational and technology cluster. R-005 (dual-running) is his single most consequential risk. |
| Prof. Otis Hammond | DVC (Education) | R-001, R-004, R-018 | 0 | Programme credibility and reputational risk. The sponsor owns the consequence-level risks. |
| Dr. Benny Moog | Director Learning Technologies | R-003, R-006, R-021 | 0 | Positioning, content, and LTI — the academic-facing risks. |
| Cassandra Rhodes | Chief Information Officer | R-002 | 0 | ADR-002 resolution. Note: Rhodes is the accountable owner for integration architecture but delegates delivery risks to Okafor. |
| A/Prof. Pearl Clavinet | Dean of L&T | R-007, R-019 | 0 | Academic governance and student experience. |
| Tobias Ohm | Cybersecurity Lead | R-016 | 0 | SSO/MFA enforcement — single focused risk. |
| Grace Tanaka | Procurement & Vendor Manager | R-009, R-012 | 0 | Vendor management and contract risks. |
| Rhonda Bell | Project Manager | R-010 | 0 | Migration timeline — scheduling risk. |
| Vernon Ostinato | Chief Financial Officer | R-011, R-013 | 0 | Financial risks. |

**Governance observation:** Eleanor Frame owns the register's top two risks (R-014 and R-015) but holds MEDIUM influence in the stakeholder analysis. This is the same mismatch identified in ARC-001-RISK-v1.0 and it has not been resolved. Ownership should be paired with an escalation right — Frame should present R-014 and R-015 directly to the Steering Committee, not through the CIO reporting line. The risks are too consequential and too technical to be summarised by an intermediary.

---

## F. 4Ts Response Framework Summary

| Response | Count | % | Examples |
|----------|-------|---|----------|
| **Tolerate** | 1 | 5% | R-013 (contingent savings — structural programme risk, not remediable within P003) |
| **Treat** | 21 | 95% | R-001, R-005, R-014, R-015 and all others |
| **Transfer** | 0 | 0% | None — see note below |
| **Terminate** | 0 | 0% | None |

**Note on Transfer:** Vendor professional services for the PeopleSoft integration (R-005 action plan) partially transfers delivery risk to Anthology, but this is a *treatment within a Treat response*, not a standalone Transfer. Cyber insurance was considered for R-014 and R-018 and rejected as a primary response for the same reason as in ARC-001-RISK-v1.0: insurance transfers some financial consequence but not the APP 11 obligation or the NDB notification duty.

**Note on the Treat concentration:** 95% Treat reflects that this is a delivery project, not a steady-state operation. Most risks are remediable through the project's own work streams — integration re-engineering, migration privacy controls, SSO enforcement, LTI testing. A mature register would show more Tolerate as the migration completes and residual scores fall.

---

## G. Risk Appetite Compliance

> ⚠️ **No approved risk appetite statement exists.** The thresholds below are the same PROVISIONAL thresholds proposed in ARC-001-RISK-v1.0. They remain unendorsed. Until endorsed, every "exceeds appetite" judgement is an architectural recommendation, not a governance finding. The recommendation from P001 to endorse these thresholds has not been actioned — this register repeats it with added urgency because Project 003 introduces active delivery risk.

**Proposed thresholds (unchanged from ARC-001-RISK-v1.0):**

| Category | Proposed Threshold | Rationale |
|----------|-------------------|-----------|
| STRATEGIC | Medium (≤ 12) | Strategic ambiguity is tolerable for bounded periods with decision deadlines |
| OPERATIONAL | Medium (≤ 12) | Teaching continuity matters but manual workarounds provide fallback |
| FINANCIAL | Medium (≤ 12) | Migration spend is material but not existential |
| COMPLIANCE | **Low (≤ 9)** | Regulatory obligations are not discretionary; a tighter threshold is warranted |
| REPUTATIONAL | Medium (≤ 12) | Reputation recovers; institutional standing is resilient to operational failure |
| TECHNOLOGY | Medium (≤ 12) | Technical assumptions can be verified cheaply during early project phases |

**Compliance against proposed thresholds:**

| Category | Threshold | Within | Exceeding / At Threshold | Action Required |
|----------|-----------|--------|--------------------------|-----------------|
| STRATEGIC | 12 | 2 | 2 at threshold (R-001, R-004) | Monitor; go/no-go criteria |
| OPERATIONAL | 12 | 5 | 1 at threshold (R-005) | Capacity plan funding |
| FINANCIAL | 12 | 3 | 0 | None |
| COMPLIANCE | 9 | 0 | 4 (R-014, R-015 exceed; R-016, R-017 exceed) | Immediate escalation for R-014 and R-015 |
| REPUTATIONAL | 12 | 2 | 0 | None |
| TECHNOLOGY | 12 | 3 | 0 | None |

**Recommendation:** Endorse these thresholds at the Steering Committee — or substitute institutional ones. Without an agreed appetite, the escalations above have no formal trigger. This is the second register to make this recommendation. If the thresholds are not endorsed before Project 003 begins delivery, the compliance escalations for R-014 and R-015 will have no governance weight at the moment they matter most.

---

## H. Prioritised Action Plan

### Priority 1: URGENT — Exceeds appetite, live or imminent exposure

| # | Action | Risks | Owner | Due | Status |
|---|--------|-------|-------|-----|--------|
| 1 | Design data migration privacy controls (access restriction, minimisation, retention, audit) | R-014 | Sam Okafor / Eleanor Frame | 2026-10-31 | Not started |
| 2 | Attach hard remediation deadlines to every temporary manual flow | R-015 | Eleanor Frame / Sam Okafor | 2026-10-31 | Not started |
| 3 | Fund and approve integration team capacity plan before Phase 1 | R-005 | Cassandra Rhodes / Sam Okafor | 2026-09-30 | Not started |
| 4 | Confirm Ultra hosting region with Anthology in writing | R-017 | Grace Tanaka | 2026-08-31 | Not started |
| 5 | Set hard decision deadline for ADR-002 | R-002 | Prof. Otis Hammond | 2026-08-15 | Not started |
| 6 | Confirm Ultra SSO/MFA configuration capability with Anthology | R-016 | Tobias Ohm | 2026-10-31 | Not started |

### Priority 2: HIGH — At appetite threshold or load-bearing for delivery

| # | Action | Risks | Owner | Due | Status |
|---|--------|-------|-------|-----|--------|
| 7 | Define go/no-go criteria for each migration phase | R-001, R-018 | Rhonda Bell / Dr. Benny Moog | 2026-09-30 | Not started |
| 8 | Enforce assessment-period change freeze as governance rule | R-001, R-018 | Prof. Otis Hammond | 2026-09-30 | Not started |
| 9 | Complete academic calendar analysis for migration windows | R-010 | Rhonda Bell / A/Prof. Pearl Clavinet | 2026-09-15 | Not started |
| 10 | Assess PeopleSoft Integration Broker event publication capability | R-020 | Sam Okafor | 2026-09-30 | Not started |
| 11 | Document API access requirements for Anthology contract negotiation | R-012 | Sam Okafor | 2026-09-30 | Not started |
| 12 | Position Ultra pedagogical advantages in migration communications | R-003, R-007 | Dr. Benny Moog / Dr. Felix Marimba | 2026-09-30 | Not started |
| 13 | Sequence delivery for early wins (PeopleSoft first) | R-004 | Rhonda Bell | 2026-09-30 | Not started |

### Priority 3: MEDIUM — Scheduled treatment before migration Phase 1

| # | Action | Risks | Owner | Due | Status |
|---|--------|-------|-------|-----|--------|
| 14 | Negotiate PS terms and API access in Anthology contract renewal | R-009, R-012 | Grace Tanaka | 2026-10-31 | Not started |
| 15 | Document and version-control course cloning scripts; train second operator | R-008 | Sam Okafor | 2026-10-31 | Not started |
| 16 | Confirm all migration cost categories before Phase 1 | R-011 | Rhonda Bell / Grace Tanaka | 2026-10-31 | Not started |
| 17 | Test rollback capability on representative migration | R-022, R-001 | Sam Okafor / Anthology | 2026-11-30 | Not started |
| 18 | Test discipline tool LTI integrations in Ultra sandpit | R-021, R-006 | Sam Okafor / Dr. Benny Moog | 2026-11-30 | Not started |
| 19 | Engage discipline tool vendors on Ultra LTI 1.3 certification | R-021 | Dr. Benny Moog | 2026-10-31 | Not started |
| 20 | Deliver hands-on training workshops per faculty | R-007 | Dr. Felix Marimba | Per faculty phase | Not started |
| 21 | Design OAuth 2.0 service accounts for all integrations | R-016 | Sam Okafor | 2026-11-30 | Not started |
| 22 | Fund integration re-engineering independently of migration | R-015 | Cassandra Rhodes | 2026-10-31 | Not started |
| 23 | Provide sandpit access 4 weeks before each faculty cutover | R-007 | Dr. Benny Moog | Per faculty phase | Not started |
| 24 | Negotiate Learn Original extended maintenance if needed | R-010 | Grace Tanaka | 2026-10-31 | Not started |
| 25 | Deliver automated course cloning before requesting template conformance | R-003, R-007 | Dr. Benny Moog / Sam Okafor | 2027-02-28 | Not started |

---

## I. Integration with SOBC

> **No Strategic Outline Business Case (SOBC) exists for Project 003.** The September business case approved by the University Executive funded the L&T programme broadly; Project 003 is the first drawdown against that case. This section describes how this risk register supports the programme-level business case and any future project-specific SOBC.

**Strategic case** — R-014, R-015 and R-016 evidence the urgency. The migration is not merely a platform upgrade — it is the remediation window for privacy and security defects that carry live regulatory exposure. Deferring the migration defers the remediation.

**Economic case** — R-011, R-012 and R-013 bound the financial options. Migration costs must be confirmed through vendor negotiation before Phase 1 begins. Savings are partly contingent on later projects (R-013) and should be reported separately.

**Commercial case** — R-009 and R-012 bear on the Anthology contract negotiation. Migration commitment provides leverage for professional services and API access. This leverage is available only during the renewal window and expires once the contract is signed.

**Management case** — This register in full, with Section H as the risk management approach and Section J as the monitoring framework.

**Recommendation influence** — R-002 (ADR-002) must be resolved before the integration design is finalised. R-005 (capacity) must be funded before Phase 1 begins. These are prerequisites, not delivery items.

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
| Days R-002 (ADR-002) remains undecided | R-002 | Beyond 2026-10-31 | Prof. Otis Hammond |
| Manual PI flows on Ultra post-migration | R-015 | Any flow without a remediation deadline | Eleanor Frame |
| Migration environment access beyond named individuals | R-014 | Any occurrence | Sam Okafor |
| Integration incidents during migration vs baseline | R-005 | Any increase above baseline | Sam Okafor |
| Platforms with local accounts after Ultra go-live | R-016 | Above current baseline (2) | Tobias Ohm |
| Assessment-period migration activity | R-018 | Any occurrence | Rhonda Bell |
| Content migration success rate per faculty | R-006 | Below 95% | Dr. Benny Moog |
| Migration cost-to-completion vs business case provision | R-011 | Exceeding provision + contingency | Vernon Ostinato |

### Escalation Criteria

- Any risk increasing by 3 or more points between reviews
- Any new risk scoring 16 or above on first assessment
- Any Priority 1 action slipping beyond its due date
- Any suspected disclosure of personal information during data migration — the NDB 30-day assessment clock starts on **suspicion**, not confirmation
- Any risk exceeding the endorsed appetite for two consecutive review cycles
- Any migration-related incident during a teaching period (regardless of risk score)

### Reporting Requirements

| Audience | Frequency | Content |
|----------|-----------|---------|
| Steering Committee | Fortnightly during migration phases | Appetite exceedances, Priority 1 action status, migration phase readiness |
| Education Committee | Per meeting | Academic risks (R-003, R-007), migration timing, faculty readiness |
| Operations Committee | Quarterly | Financial and operational profile, integration incident trending |
| University Executive | At programme review | Full register summary with appetite position, programme credibility assessment |

### Register Maintenance

**Register owner:** Rhonda Bell, Project Manager, through to project completion. **Post-project ownership must transfer** to a named institutional owner — recommended as Sam Okafor (integration risks) and Eleanor Frame (compliance risks). The ARC-001-RISK-v1.0 register recommended naming a post-engagement owner by 31 August 2026; this register inherits that recommendation and extends it: integration and compliance risks persist after migration and must be actively managed.

---

## K. Orange Book Compliance Checklist

### Part I — Risk Management Principles

| Principle | Status | Evidence |
|-----------|--------|----------|
| **A. Governance and Leadership** | ✅ | Every risk has a named owner drawn from the STKE RACI; escalation path follows RIFF governance |
| **B. Integration** | ✅ | Risks trace to STKE goals (G-1 to G-6) and outcomes (O-1 to O-3); Section I links to the business case; STKE risks R-1 to R-6 cross-referenced |
| **C. Collaboration** | ✅ | Risks sourced from STKE conflicts (C-1 to C-4), stakeholder drivers (SD-1 to SD-14), integration landscape, and privacy context |
| **D. Risk Management Processes** | ✅ | Systematic identification across six categories; inherent/residual assessment; 4Ts response; action plan; monitoring |
| **E. Continual Improvement** | ⚠️ Partial | Review framework defined; inherits baseline from ARC-001-RISK-v1.0 for trend comparison on shared risks |

### Part II — Risk Control Framework

| Pillar | Status | Notes |
|--------|--------|-------|
| **Risk appetite** | ⚠️ **Provisional only** | Same unendorsed thresholds as ARC-001-RISK-v1.0; second register to recommend endorsement |
| **Risk culture** | ⚠️ Partial | Weak control effectiveness across the integration estate; controls improving through project delivery |
| **Risk assessment** | ✅ | Consistent 5×5 scales; cross-referenced to Project 001 scores for inherited risks |
| **Risk response** | ✅ | 4Ts applied with rationale and alternatives considered; pattern recognition across related risks |

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
| Prof. Otis Hammond | SD-1 — migration strengthens teaching | Teaching disruption undermines programme | R-001 | Hammond | Inter-semester phasing; go/no-go gates; change freezes | Zero assessment-period disruption |
| Cassandra Rhodes | SD-2 — deliver integration architecture | ADR-002 blocks role assignment | R-002 | Rhodes | Decision deadline; documented assumption | ADR-002 resolved; role assignment integration live |
| Sam Okafor | SD-3 — build it right this time | Team overwhelmed by dual-running | R-005 | Okafor | Capacity plan funded; vendor PS; sequencing | No integration incidents above baseline; delivery to plan |
| Dr. Benny Moog | SD-4 — Ultra as better platform | Ultra positioned as vendor mandate | R-003 | Moog | Pedagogical positioning; course cloning automation | Template adoption > 80% |
| A/Prof. Pearl Clavinet | SD-5 — academic community carries change | Academic resistance delays adoption | R-007 | Clavinet | Pilot; training workshops; sandpit access | Academic satisfaction > 70% |
| Dr. Wynton Castle | SD-6 — do not break my units | Content migration breaks discipline content | R-006 | Moog | Pilot testing on representative units; faculty sign-off | Content migration success > 95% |
| Eleanor Frame | SD-7 — no migrated privacy defects | Data migration creates PI exposure | R-014 | Frame | Migration privacy controls; segmented sensitive data | Zero unauthorised access; deletion within 30 days |
| Eleanor Frame | SD-7 — no migrated privacy defects | Manual flows replicated temporarily | R-015 | Frame | Hard remediation deadlines; independent integration funding | Zero manual PI flows at 12 months |
| Tobias Ohm | SD-8 — Ultra closes security gap | SSO/MFA incomplete at go-live | R-016 | Ohm | Anthology SSO confirmation; OAuth 2.0 service accounts | Zero local accounts on Ultra |
| Vernon Ostinato | SD-9 — costs justified | Migration costs exceed provision | R-011 | Ostinato | Cost confirmation; contingency provision | Costs within provision + contingency |
| Grace Tanaka | SD-10 — negotiate from strength | Anthology gates API access | R-012 | Tanaka | API requirements documented; migration leverage | API access in base licensing |
| Prof. Priya Anand | SD-11 — fix placement grades | Manual flows replicated on Ultra | R-015 | Frame | Bidirectional grade integration; remediation deadline | Zero manual re-keying of placement grades |
| Prof. Desmond Key | SD-12 — discipline tools work | LTI 1.3 breaks discipline tools | R-021 | Moog | LTI testing in sandpit; vendor certification | 100% discipline tools verified |
| Jazmin Field | SD-13 — students not the experiment | Student experience degrades | R-019 | Clavinet | Communication plan; content verification; Guild in pilot | Student satisfaction maintained |
| Anthology | SD-14 — retain customer on Ultra | PS unavailable or delayed | R-009 | Tanaka | PS negotiated in contract renewal | PS engagement confirmed |

---

## Appendix C: STKE Risk Cross-Reference

Traceability from the six risks identified in ARC-003-STKE-v1.0 to this register:

| STKE Risk | STKE Description | Register Risk(s) | Notes |
|-----------|------------------|-------------------|-------|
| R-1 | Academic resistance to Ultra interface change | **R-007** (primary), R-003 | R-003 covers the positioning root cause; R-007 covers the adoption consequence |
| R-2 | Integration team overwhelmed by dual-running | **R-005** | Direct mapping |
| R-3 | ADR-002 unresolved — role assignment source undefined | **R-002** | Direct mapping |
| R-4 | Content migration breaks discipline-specific content | **R-006** (primary), R-021 | R-006 covers content migration; R-021 covers LTI integration |
| R-5 | Anthology gates critical API access behind premium licensing | **R-012** | Direct mapping |
| R-6 | Data migration exposes personal information without adequate controls | **R-014** (primary), R-015 | R-014 covers the migration exposure; R-015 covers the post-migration persistence |

---

## Document Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Risk Register Owner | Rhonda Bell, Project Manager | | |
| Executive Sponsor | Prof. Otis Hammond, DVC (Education) | | |
| Technical Authority | Cassandra Rhodes, Chief Information Officer | | |
| Integration Architect | Sam Okafor | | |
| Privacy Authority | Eleanor Frame, Privacy & Records Officer | | |
| Cybersecurity Authority | Tobias Ohm, Cybersecurity Lead | | |

---

## Next Steps

1. **Escalate R-014 and R-015 to the Steering Committee** at the next fortnightly meeting — R-015 is a live compliance exposure predating this project; R-014 will materialise the moment data migration begins.
2. **Fund the integration team capacity plan** (Priority 1, action 3). This is the project's single most consequential operational risk and the only structural mitigation is money.
3. **Confirm Ultra hosting region with Anthology** (Priority 1, action 4). Costs nothing — one email — and may resolve R-017 entirely.
4. **Set the ADR-002 decision deadline** (Priority 1, action 5) so the role assignment integration can be designed with certainty.
5. **Endorse the provisional risk appetite thresholds** — this is the second register to recommend it. Without endorsed thresholds, the compliance escalations have no governance weight.
6. **Name a post-project register owner** — integration and compliance risks persist after migration.

---

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RK-D1 | ARC-003-STKE-v1.0.md | ArcKit artifact | `projects/003-lms-ultra-migration/` | Stakeholder drivers, goals, outcomes, conflicts, RACI — source of risk owners and STKE risks R-1 to R-6 |
| RK-D2 | ARC-003-REQ-v1.0.md | ArcKit artifact | `projects/003-lms-ultra-migration/` | Requirements — BR, FR, NFR, INT requirements with acceptance criteria |
| RK-D3 | ARC-001-RISK-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/` | Project 001 risk register — inherited risks and provisional appetite thresholds |
| RK-D4 | ARC-001-ADR-001-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/decisions/` | Integration Mediation Approach — canonical model and event broker |
| RK-D5 | ARC-001-ADR-002-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/decisions/` | Authoritative Source for Institutional Role Assignment — unresolved prerequisite |
| RK-D6 | ARC-001-DATA-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/` | Canonical data model — PERSON, UNIT, ENROLMENT, INSTITUTIONAL_ROLE_ASSIGNMENT |
| RK-D7 | ARC-000-PRIN-v1.1.md | ArcKit artifact | `projects/000-global/` | Architecture principles — P10, P11, P12, P13, P16, P17, P19 |
| RK-D8 | system-landscape.md | Foundation artifact | `projects/003-lms-ultra-migration/external/` | Seven integrations, current state defects, known fragility |
| RK-D9 | privacy-context.md | Compliance input | `projects/003-lms-ultra-migration/external/` | PI inventory, manual flows, data classes, APP 8 triggers, E8 self-assessment |
| RK-D10 | solution-governance-process.md | Global policy | `projects/000-global/policies/` | RIFF Review — escalation path |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| RK-C1 | RK-D1 | CSF-1 | Success Factor | "The Ultra migration and integration re-engineering are sequenced so that no teaching period experiences both a changed LMS interface and a changed integration simultaneously" |
| RK-C2 | RK-D1 | CSF-4 | Success Factor | "Manual flows carrying personal information — placement grades, CSV provisioning, hierarchy updates — are eliminated, not migrated to the new platform in their current form" |
| RK-C3 | RK-D1 | CSF-5 | Success Factor | "Academic staff experience the migration as effort reduction (automated cloning, better provisioning) rather than mandated rework" |
| RK-C4 | RK-D1 | Conflict C-2 | Conflict | "ADR-001 specifies a lightweight event broker mediating all nine integrations through a canonical data model. Okafor's team must deliver this while maintaining the current fragile estate" |
| RK-C5 | RK-D1 | SD-7 | Driver | "needs the manual re-keying and flat-file transfers that are privacy findings in Project 001 to be eliminated by the new architecture, not replicated in it" |
| RK-C6 | RK-D8 | Known integrations | Current state | Seven integrations including "Fragile; role assignment failures; no intra-day sync" and "Manual re-keying; error-prone; audit concerns" |
| RK-C7 | RK-D9 | §1–2 | Privacy | "4/7 integrations involve manual handling"; "Flat files on shared storage with PI"; "24h deprovisioning latency"; "2 tools allow local accounts" |
| RK-C8 | RK-D9 | §4 | Privacy | "4 data classes with offshore disclosure (APP 8)" |
| RK-C9 | RK-D7 | P16 | Principle | Principle 16 (Layered Security Posture) — SSO/MFA, no local accounts — rated CRITICAL |
| RK-C10 | RK-D7 | P19 | Principle | Principle 19 (Realise Licensed Capability Before New Spend) — rated HIGH |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| consultant-brief.md | `projects/003-lms-ultra-migration/external/` | Read for context; project scope documented in STKE and REQ artifacts already cited |
| requirements-register.md | `projects/003-lms-ultra-migration/external/` | Academic survey requirements; referenced structurally via ARC-003-REQ-v1.0 |
| ARC-001-STKE-v1.0.md | `projects/001-lt-ecosystem/` | Project 001 stakeholder analysis; inherited via ARC-003-STKE-v1.0 |

---

**Generated by**: ArcKit `/arckit:risk` command
**Generated on**: 2026-07-29
**ArcKit Version**: 6.7.4
**Project**: LMS Ultra Migration & Integration Modernisation (Project 003)
**Model**: Claude Opus 4.6 (1M context)
