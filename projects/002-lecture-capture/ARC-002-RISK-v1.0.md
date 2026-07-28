# Risk Register

> **Template Origin**: Official | **ArcKit Version**: 6.7.2 | **Command**: `/arckit:risk`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-RISK-v1.0 |
| **Document Type** | Risk Register (HM Treasury Orange Book 2023) |
| **Project** | Lecture Capture Platform Consolidation (Project 002) |
| **Classification** | OFFICIAL-SENSITIVE |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-27 |
| **Last Modified** | 2026-07-27 |
| **Review Cycle** | Monthly (Medium risks); fortnightly during procurement and transition |
| **Next Review Date** | 2026-08-27 |
| **Owner** | Rhonda Bell, Project Manager — Risk Register Owner |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Steering Committee; Project Team; Procurement; Digital & IT leadership; Privacy & Records |

> **Classification rationale**: This register records current Essential Eight maturity gaps on the capture estate, names individual risk owners, and documents pre-procurement positions. Disclosure of the security content would assist an attacker; disclosure of the procurement content would compromise probity. OFFICIAL-SENSITIVE, restricted to the steering and project group.

> **Framework note**: This register applies HM Treasury's Orange Book (2023) methodology — 5×5 inherent and residual assessment, the 4Ts response framework, and risk ownership traceable to accountable individuals. The Orange Book is UK Government guidance; The University of Funk is an Australian institution and is not subject to it. It is used here as a recognised methodology, not as a compliance obligation. Where the framework assumes UK public-sector governance (NAO, PAC, ministerial accountability), the equivalent institutional structures apply: RIFF Review, Education Committee, Operations Committee and University Executive [SGP-C1].

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-27 | ArcKit AI | Initial creation from `/arckit:risk` command; consolidates and supersedes the provisional risk lists in ARC-002-STKE-v1.0 §10 and ARC-002-REQ-v1.0 §11 | PENDING | PENDING |

---

## Executive Summary

### Risk Profile Overview

**Total Risks Identified:** 22 risks across 6 categories

| Risk Level | Inherent | Residual | Change |
|------------|----------|----------|--------|
| **Critical** (20-25) | 0 | 0 | — |
| **High** (13-19) | 5 | 0 | ↓ 100% |
| **Medium** (6-12) | 17 | 18 | ↑ 6% |
| **Low** (1-5) | 0 | 4 | ↑ new |
| **TOTAL SCORE** | 266 | 156 | ↓ 41% |

The apparent increase in Medium-rated risks is a consequence of the five High risks moving down into the Medium band, not of new risk emerging. No risk is rated Critical at either stage.

### Risk Category Distribution

| Category | Count | Avg Inherent | Avg Residual | Control Effectiveness |
|----------|-------|--------------|--------------|----------------------|
| **STRATEGIC** | 5 | 12.2 | 8.0 | 34% reduction |
| **OPERATIONAL** | 5 | 12.2 | 7.2 | 41% reduction |
| **FINANCIAL** | 2 | 10.5 | 7.5 | 29% reduction |
| **COMPLIANCE** | 5 | 12.8 | 7.4 | 42% reduction |
| **REPUTATIONAL** | 2 | 12.0 | 6.0 | 50% reduction |
| **TECHNOLOGY** | 3 | 11.7 | 5.3 | 54% reduction |

### Overall Risk Assessment

**Overall Residual Risk Score:** 156 / 550 (maximum exposure = 22 risks × 25)
**Risk Reduction from Controls:** 41% reduction from inherent (266 → 156)
**Risk Profile Status:** ⚠️ **Concerning** — acceptable in aggregate, but concentrated in the categories where institutional tolerance is lowest

The aggregate profile is not alarming: no Critical risks, no High residual risks, and a 41% reduction from controls that mostly already exist in the requirements. The concern is *where* the residual sits. Four risks exceed the provisional appetite, and all four are COMPLIANCE or REPUTATIONAL — the two categories where a university's tolerance is tightest and where recovery after materialisation is slowest.

### Provisional Risk Appetite — Not Yet Ratified

**No organisational risk appetite statement exists.** `projects/000-global/policies/` contains the RIFF governance process but no appetite thresholds, and none was supplied as an engagement input.

The thresholds used throughout this register are **provisional**, derived from the criticality ratings in the architecture principles — principles rated CRITICAL (7 Privacy by Design, 8 Data Residency, 14 Accessibility, 16 Layered Security) imply low tolerance in the COMPLIANCE category, while the university's deliberate decision to undertake ecosystem change implies higher tolerance in STRATEGIC [PRIN-C1]. They require ratification by the Operations Committee before they carry authority.

| Category | Provisional Appetite | Threshold | Derivation |
|----------|---------------------|-----------|------------|
| STRATEGIC | Medium | ≤ 12 | The university has chosen to undertake rationalisation; strategic risk is being taken deliberately |
| OPERATIONAL | Medium | ≤ 9 | Teaching continuity matters, but change is being made during a live academic year |
| FINANCIAL | Medium | ≤ 9 | Business case scrutiny is active; the project is cost-motivated |
| COMPLIANCE | Low | ≤ 6 | Privacy Act 1988 is statutory; Principles 7, 8 and 14 are rated CRITICAL |
| REPUTATIONAL | Low | ≤ 6 | Student trust and academic confidence are slow to rebuild |
| TECHNOLOGY | Medium | ≤ 12 | Platform change is the purpose of the project |

**Action required**: Operations Committee to ratify or amend these thresholds by 2026-10-09, alongside the platform decision.

### Risks Exceeding Appetite

**Number of risks exceeding provisional appetite:** 4 risks

| Risk ID | Title | Category | Residual | Appetite | Excess | Escalation |
|---------|-------|----------|----------|----------|--------|------------|
| R-016 | Essential Eight gaps persist on the capture estate | COMPLIANCE | 9 | 6 | +3 (50%) | Cybersecurity Lead → CIO |
| R-013 | PIA incomplete at contract signature; APP 8 unresolved | COMPLIANCE | 8 | 6 | +2 (33%) | Privacy Officer → Operations Committee |
| R-017 | Procurement probity breached by informal vendor contact | COMPLIANCE | 8 | 6 | +2 (33%) | Procurement → Executive Sponsor |
| R-018 | Privacy incident involving student recordings | REPUTATIONAL | 8 | 6 | +2 (33%) | Privacy Officer → CIO → University Executive |

### Top 5 Risks Requiring Immediate Attention

1. **R-006** (OPERATIONAL, Medium 9 — inherent 16): Baseline data not delivered, forcing evaluation on assumptions — Owner: Rhonda Bell — Status: Open. *Highest inherent score, nearest due date (2026-08-14), and it gates four other risks.*
2. **R-016** (COMPLIANCE, Medium 9): Essential Eight gaps persist on the capture estate — Owner: Tobias Ohm — Status: Open. *Exceeds appetite by the widest margin; the underlying gap predates this project and has already survived one remediation cycle.*
3. **R-013** (COMPLIANCE, Medium 8 — inherent 16): PIA incomplete at contract signature — Owner: Eleanor Frame — Status: Open. *Time-bound in a way the others are not: leverage disappears at signature on 2026-12-11 and cannot be recovered.*
4. **R-001** (STRATEGIC, Medium 9 — inherent 16): Platform decision contested, deadlocked or reopened — Owner: Prof. Otis Hammond — Status: Open. *Highest-likelihood risk in the register; already partially materialised in that positions were taken before evaluation existed.*
5. **R-018** (REPUTATIONAL, Medium 8 — inherent 15): Privacy incident involving student recordings — Owner: Eleanor Frame — Status: Open. *Lowest likelihood of the top five, highest impact; the only risk assessed at Impact 5 that remains above appetite.*

### Key Findings and Recommendations

**Key Findings:**

- **The register reconciles two conflicting risk lists.** ARC-002-STKE §10 and ARC-002-REQ §11 both used the IDs `R-1` … `R-8` for *different* risk sets with partial overlap. Three risks appeared in both under different numbers, and two appeared in one but not the other. This register is now the single canonical source; Appendix C maps every prior ID to its successor.
- **Residual risk concentrates where appetite is tightest.** All four appetite breaches are COMPLIANCE or REPUTATIONAL. No STRATEGIC, OPERATIONAL, FINANCIAL or TECHNOLOGY risk exceeds its threshold. The project's commercial and delivery risks are well-controlled; its compliance risks are not.
- **Controls are strongest where they were designed in, weakest where they were inherited.** TECHNOLOGY risks reduce by 54% and REPUTATIONAL by 50%, because their controls are mandatory gates written into ARC-002-REQ. COMPLIANCE risk R-016 reduces least in absolute terms because its control is a remediation programme that has already been deferred once.
- **Six risks depend on the same six baseline datasets.** R-006 is not merely a risk in its own right — it is a precondition for accurate assessment of R-007, R-010, R-011, R-020 and, indirectly, R-021. If the August baselines slip, five other assessments in this register become unreliable.
- **Ownership is well distributed but three owners carry a fifth each.** Rhodes (23 points), Hammond (23) and Frame (22) each hold roughly 15% of total residual exposure. This is proportionate to their roles rather than a concentration defect, but Frame's three risks are all in the over-appetite set.
- **No risk warrants termination, and one option-level termination remains available.** The pause provision in the RIFF process permits closing the request entirely if evaluation shows no option delivers value [SGP-C3]. That remains live under R-002 and should not be quietly dropped from the options set.

**Recommendations:**

1. **Escalate the four appetite breaches to the Operations Committee on 2026-10-09**, alongside the platform decision and the appetite ratification — not separately, and not after.
2. **Treat the six August baseline deliverables as gating milestones, not dependencies.** Escalate at first slip rather than at the point of impact. R-006 is the highest-leverage item in this register.
3. **Bring the PIA forward.** NFR-C-001 requires it before contract signature; R-013's controls only work if the assessment starts at preferred-option stage (October) rather than at contract drafting (December).
4. **Fund the Essential Eight remediation as part of this project, not as a successor.** R-016 exceeds appetite specifically because the work has been deferred before; a second deferral should require explicit Operations Committee acceptance rather than happening by omission.
5. **Ratify the provisional appetite.** Four "breaches" against unratified thresholds are an opinion, not a governance position. The thresholds need Operations Committee endorsement to mean anything.

---

## A. Risk Matrix Visualization

### Inherent Risk Matrix (Before Controls)

**5×5 Likelihood × Impact Matrix**

```text
                                        IMPACT
             1-Negligible  2-Minor    3-Moderate   4-Major    5-Catastrophic
           ┌───────────┬───────────┬───────────┬───────────┬───────────┐
5-Almost   │           │           │           │           │           │
Certain    │    5      │    10     │    15     │    20     │    25     │
           ├───────────┼───────────┼───────────┼───────────┼───────────┤
           │           │           │  R-003    │  R-001    │           │
4-Likely   │           │           │  R-011    │  R-006    │           │
           │           │           │  R-014    │  R-013    │           │
L          │           │           │  R-015    │           │           │
I          │           │           │  R-016    │           │           │
K          │    4      │    8      │  ▓▓ 12    │  ▓▓ 16    │    20     │
E          ├───────────┼───────────┼───────────┼───────────┼───────────┤
L          │           │           │  R-005    │  R-002    │  R-018    │
I          │           │           │  R-009    │  R-004    │  R-021    │
H 3-Possible│          │           │  R-012    │  R-007    │           │
O          │           │           │  R-019    │  R-008    │           │
O          │           │           │           │  R-010    │           │
D          │           │           │           │  R-017    │           │
           │           │           │           │  R-020    │           │
           │    3      │    6      │  ░░ 9     │  ▓▓ 12    │  ▓▓ 15    │
           ├───────────┼───────────┼───────────┼───────────┼───────────┤
2-Unlikely │           │           │           │  R-022    │           │
           │    2      │    4      │    6      │  ░░ 8     │    10     │
           ├───────────┼───────────┼───────────┼───────────┼───────────┤
1-Rare     │           │           │           │           │           │
           │    1      │    2      │    3      │    4      │    5      │
           └───────────┴───────────┴───────────┴───────────┴───────────┘

Legend: ██ Critical (20-25)  ▓▓ High (13-19)  ░░ Medium (6-12)  ·· Low (1-5)
```

**Risk Zones (Inherent):**

- **Critical (20-25)**: None
- **High (13-19)**: R-001, R-006, R-013 (16 each); R-018, R-021 (15 each) — senior management attention
- **Medium (6-12)**: R-002, R-003, R-004, R-005, R-007, R-008, R-009, R-010, R-011, R-012, R-014, R-015, R-016, R-017, R-019, R-020, R-022
- **Low (1-5)**: None

Note the clustering at Likelihood 3–4: nothing in this project is rated Almost Certain, and nothing is Rare. That distribution is characteristic of a project whose risks are mostly *decisions not yet made* rather than *events outside the university's control*.

### Residual Risk Matrix (After Controls)

**5×5 Likelihood × Impact Matrix — After Controls Applied**

```text
                                        IMPACT
             1-Negligible  2-Minor    3-Moderate   4-Major    5-Catastrophic
           ┌───────────┬───────────┬───────────┬───────────┬───────────┐
5-Almost   │           │           │           │           │           │
Certain    │    5      │    10     │    15     │    20     │    25     │
           ├───────────┼───────────┼───────────┼───────────┼───────────┤
4-Likely   │           │           │           │           │           │
           │    4      │    8      │    12     │    16     │    20     │
L          ├───────────┼───────────┼───────────┼───────────┼───────────┤
I          │           │           │  R-001    │           │           │
K          │           │           │  R-003    │           │           │
E 3-Possible│          │           │  R-006    │           │           │
L          │           │           │  R-008    │           │           │
I          │           │           │  R-011    │           │           │
H          │           │           │  R-016    │           │           │
O          │    3      │    6      │  ░░ 9     │    12     │    15     │
O          ├───────────┼───────────┼───────────┼───────────┼───────────┤
D          │           │  R-009    │  R-005    │  R-002    │           │
           │           │  R-019    │  R-010    │  R-004    │           │
2-Unlikely │           │           │  R-012    │  R-007    │           │
           │           │           │  R-014    │  R-013    │           │
           │           │           │  R-015    │  R-017    │           │
           │           │           │           │  R-018    │           │
           │           │           │           │  R-020    │           │
           │    2      │  ·· 4     │  ░░ 6     │  ░░ 8     │    10     │
           ├───────────┼───────────┼───────────┼───────────┼───────────┤
1-Rare     │           │           │           │  R-021    │           │
           │           │           │           │  R-022    │           │
           │    1      │    2      │    3      │  ·· 4     │    5      │
           └───────────┴───────────┴───────────┴───────────┴───────────┘

Legend: ██ Critical (20-25)  ▓▓ High (13-19)  ░░ Medium (6-12)  ·· Low (1-5)
```

**Risk Movement Analysis:**

- **Significant improvement** — R-021 (15 → 4, 73%): retaining the incumbent archive read-only until reconciliation is signed off converts data loss from a recovery problem into a redirect reversal. R-022 (8 → 4, 50%): a mandatory pass/fail provisioning gate eliminates the failure mode at selection rather than managing it afterwards.
- **Strong improvement** — R-018 (15 → 8, 47%), R-013 (16 → 8, 50%), R-006 (16 → 9, 44%), R-009 (9 → 4, 56%), R-019 (9 → 4, 56%). In each case the control is a specific requirement already written into ARC-002-REQ rather than an intention.
- **Moderate improvement** — R-001 (16 → 9), R-002/R-004/R-007/R-017/R-020 (12 → 8), R-014/R-015 (12 → 6). Controls are designed but not yet in place; these ratings assume the controls are actually implemented.
- **Limited improvement** — R-003 (12 → 9), R-008 (12 → 9), R-011 (12 → 9), R-016 (12 → 9, 25%). R-016 is the weakest control performance in the register, and it is the risk furthest above appetite. That combination is the single most important signal in this section.

**Assessment integrity note**: Residual scores assume designed controls are implemented as specified. Where a control is a requirement not yet delivered (most of them, at v1.0), the residual score is a *forecast*, not a measurement. The register should be re-scored after contract signature, when controls become verifiable.

---

## B. Top 10 Risks (Ranked by Residual Score)

Ranked by residual score, then by inherent score where residual scores tie.

| Rank | ID | Title | Category | Inherent | Residual | Owner | Status | Response |
|------|----|-------|----------|----------|----------|-------|--------|----------|
| 1 | R-006 | Baseline data not delivered; evaluation on assumptions | OPERATIONAL | 16 | 9 | Rhonda Bell | Open | Treat |
| 2 | R-001 | Platform decision contested, deadlocked or reopened | STRATEGIC | 16 | 9 | Prof. Otis Hammond | Open | Treat |
| 3 | R-016 | Essential Eight gaps persist on the capture estate | COMPLIANCE | 12 | 9 | Tobias Ohm | Open | Treat |
| 4 | R-003 | Discipline exception endorsed but unfunded | STRATEGIC | 12 | 9 | A/Prof. Pearl Clavinet | Open | Treat |
| 5 | R-008 | AV capacity insufficient for room works in the July window | OPERATIONAL | 12 | 9 | Cassandra Rhodes | Open | Treat |
| 6 | R-011 | Whole-of-life saving eliminated by appliance capital cost | FINANCIAL | 12 | 9 | Vernon Ostinato | Open | Treat |
| 7 | R-013 | PIA incomplete at contract signature; APP 8 unresolved | COMPLIANCE | 16 | 8 | Eleanor Frame | Open | Treat |
| 8 | R-018 | Privacy incident involving student recordings | REPUTATIONAL | 15 | 8 | Eleanor Frame | Open | Treat |
| 9 | R-002 | Consolidation degrades teaching capability | STRATEGIC | 12 | 8 | A/Prof. Pearl Clavinet | Open | Treat |
| 10 | R-004 | Decision slips past October, missing the business case window | STRATEGIC | 12 | 8 | Prof. Otis Hammond | Open | Treat |

**Below the top 10, also at residual 8**: R-007 (room estate incompatible), R-017 (probity breach), R-020 (archive stranded by export terms). The cut at rank 10 is arbitrary — thirteen risks share residual scores of 8 or 9, and the ranking between them should not be read as a priority order. The prioritised action plan in Section H orders by urgency and appetite breach instead, which is the more useful ordering.

---

## C. Detailed Risk Register

### Risk R-001: Platform decision contested, deadlocked or reopened

**Category:** STRATEGIC
**Status:** Open
**Risk Owner:** Prof. Otis Hammond, DVC (Education) — Executive Sponsor (STKE RACI: Accountable for platform recommendation)
**Action Owner:** Rhonda Bell, Project Manager

#### Risk Identification

**Risk Description:**
The evaluation criteria workshop deadlocks, or criteria are agreed and then disputed after scoring, because each party recognises that whoever sets the weights sets the outcome. The decision is either not taken, taken and immediately contested, or taken and reopened at the next contract renewal.

**Root Cause:**
Two senior stakeholders adopted public positions before any evaluation existed [S-C1]. Both can cite institutional principle in support — Principle 19 for consolidation, Principles 2 and 4 for specialisation — so neither position is unreasonable and neither can be dismissed on authority.

**Trigger Events:**

- Weighting workshop fails to reach agreement across two scheduled sessions
- A party declines to sign the criteria before vendor engagement
- Criteria amended after proposals are received
- Scoring outcome disputed on the basis that the criteria were wrong

**Consequences if Realized:**

- Decision misses the 9 October Operations Committee gate, and with it the business case cycle (links to R-004)
- Executive sponsor forced to arbitrate publicly between the CIO and a Dean
- Whichever platform is selected is relitigated at renewal, so the rationalisation is never banked
- WP8 future state in project 001 remains blocked

**Affected Stakeholders:**

- **Cassandra Rhodes (CIO)**: Her consolidation case is either untested or overridden
- **Dr. Benny Moog (Learning Technologies)**: Operates a platform he argued against, without a process he can point to
- **Prof. Otis Hammond**: Receives the decision he sponsored the project to avoid making personally
- **A/Prof. Pearl Clavinet**: Her committee is asked to endorse a contested recommendation

**Related Objectives:**

- **STKE G-1** (decision endorsed by 9 October): directly threatened
- **STKE G-2** (evaluation on published unchanged criteria): this risk *is* the failure of G-2
- **STKE O-6** (a decision that holds): the outcome this risk destroys

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 - Likely | Positions were taken before evaluation existed; without agreed criteria there is no mechanism to resolve them |
| **Impact** | 4 - Major | Threatens the October gate, the business case, and the parent engagement's future state deliverable |
| **Inherent Risk Score** | **16** (High) | 4 × 4 = 16 |

**Risk Zone:** 🟧 High (13-19)

#### Current Controls and Mitigations

1. **Signed criteria before vendor engagement (BR-004)**: Weightings totalling 100% agreed by Rhodes, Moog and Tanaka before any supplier is approached
   - Owner: Grace Tanaka
   - Effectiveness: **Strong** — binds both principals to a process they shaped
   - Evidence: Not yet in place; criteria due 2026-08-28
2. **Weights anchored to register MoSCoW priority**: Derived from a prioritisation Education Committee already approved [RR-C1], not negotiated fresh
   - Owner: Rhonda Bell
   - Effectiveness: **Adequate** — removes the most contestable part of the weighting argument
3. **Adjusted RIFF chairing**: Hammond chairs the session; Moog presents evidence with his interest declared
   - Owner: Prof. Otis Hammond
   - Effectiveness: **Adequate** — removes the governance strain without excluding the expertise
4. **Dissent recorded, not suppressed (BR-002)**: Formal disagreement is minuted with a written response
   - Owner: Dr. Benny Moog (RIFF register)
   - Effectiveness: **Adequate**

**Overall Control Effectiveness:** Adequate (reduces 16 → 9)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | Signed criteria make deadlock materially less likely, but do not eliminate disagreement over how criteria are applied |
| **Impact** | 3 - Moderate | With a recorded process, a contested outcome is survivable — it costs a governance cycle, not the decision |
| **Residual Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 44% (16 → 9)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:** The risk is high-likelihood but entirely internal, and the treatment is cheap relative to the exposure — a facilitated workshop and a signature.

**Alternatives Considered:**

- **Tolerate**: Rejected — inherent score exceeds strategic appetite and the consequence is a stalled decision
- **Transfer**: Not applicable — no third party can carry an internal governance risk
- **Terminate**: Rejected — abandoning the decision leaves the three-way overlap in place

#### Risk Appetite Assessment

**Provisional appetite (STRATEGIC):** ≤ 12 · **Residual:** 9 · ✅ **Within appetite**

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Independently facilitated weighting workshop, capped at two sessions | Rhonda Bell | 2026-08-21 | Likelihood 4 → 3 |
| Mandatory pass/fail gates set first, removing security, accessibility and export from the trading space | Grace Tanaka | 2026-08-21 | Reduces scope of dispute |
| Criteria signed by all three parties | Grace Tanaka | 2026-08-28 | Impact 4 → 3 |
| Escalation to Hammond on written submissions if the second session fails | Prof. Otis Hammond | 2026-09-04 | Contingency |

**Target Residual:** L2 × I3 = 6 (Medium) after criteria are signed and evidenced.

**Success Criteria:** Criteria signed by 2026-08-28 with zero post-issue amendments; no reopening attempt within 24 months of the decision.

**Monitoring:** Fortnightly at steering. Escalation triggers — criteria unsigned by 2026-09-04, or any amendment requested after issue.

---

### Risk R-002: Consolidation degrades teaching capability

**Category:** STRATEGIC
**Status:** Open
**Risk Owner:** A/Prof. Pearl Clavinet, Dean L&T and Chair, Education Committee (STKE RACI: Education Committee accountable for academic approval)
**Action Owner:** Dr. Benny Moog, Director Learning Technologies

#### Risk Identification

**Risk Description:**
The selected platform meets the cost and integration criteria but delivers capture, analytics or LMS integration at a materially shallower level than the incumbent, degrading teaching quality in ways that only become visible once academics are using it in a live semester.

**Root Cause:**
General-purpose meeting recording and purpose-built lecture capture are different product classes [STKE-C1]. A comparison structured around cost and platform count will not surface the difference unless capability criteria are weighted to expose it.

**Trigger Events:**

- Capability criteria weighted low relative to cost in the evaluation framework
- Evaluation conducted without hands-on academic assessment of the teaching journey
- Analytics and LMS integration treated as desirable rather than mandatory
- Pilot feedback overridden by contractual commitment already made

**Consequences if Realized:**

- Teaching quality reduction across all schools — the broadest-reach consequence in this register
- Academic confidence in Digital & IT damaged for subsequent rationalisation decisions
- Shadow tooling re-emerges as academics work around the platform, recreating the duplication the project set out to remove
- REQ-004, REQ-009 and REQ-020 met nominally but not usefully

**Affected Stakeholders:**

- **Dr. Wynton Castle and academic staff**: Daily teaching workflow degraded
- **Dr. Benny Moog**: The outcome he predicted, having been unable to prevent it
- **Students**: Indirect but universal — worse recordings, worse discovery
- **A/Prof. Pearl Clavinet**: Her committee endorsed the decision

**Related Objectives:**

- **STKE G-2** (criteria reflect teaching use, not meeting use)
- **STKE O-1** (one platform, deliberately bounded — bounded on capability, not just count)
- **REQ BR-001**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | Real but not probable: the risk requires the evaluation to be constructed badly, which the process controls are designed to prevent |
| **Impact** | 4 - Major | Affects every school and every recorded session for the life of the contract; expensive and slow to reverse |
| **Inherent Risk Score** | **12** (Medium) | 3 × 4 = 12 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Capability comparison against the eight-category taxonomy [CT-C1]**, not a vendor feature checklist
   - Owner: Dr. Benny Moog · Effectiveness: **Strong** · Evidence: Taxonomy is an approved foundation artifact
2. **Mandatory gates for provisioning, accessibility and export** — removes three ways a shallow platform could otherwise score adequately
   - Owner: Grace Tanaka · Effectiveness: **Strong**
3. **Semester 1 2027 pilot before full cutover (BR-006)** — surfaces degradation while the contract is young
   - Owner: Rhonda Bell · Effectiveness: **Adequate** — a pilot after signature limits remedy to negotiation
4. **Academic reference group input documented in the recommendation**
   - Owner: A/Prof. Pearl Clavinet · Effectiveness: **Adequate**

**Overall Control Effectiveness:** Adequate (reduces 12 → 8)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 - Unlikely | Taxonomy-based comparison plus mandatory gates make a shallow platform hard to select |
| **Impact** | 4 - Major | Unchanged — controls reduce the chance of the error, not its consequence if made |
| **Residual Risk Score** | **8** (Medium) | 2 × 4 = 8 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 33% (12 → 8)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:** Impact cannot be reduced, so all treatment targets likelihood — better criteria, hands-on assessment, and a pilot that can still influence configuration.

**Alternatives Considered:**

- **Tolerate**: Rejected — within appetite numerically, but the consequence is borne by students and academics who have no voice in the decision
- **Terminate**: Retained as a live option, not rejected. The RIFF pause provision [SGP-C3] permits closing the request entirely if no option delivers value. "Retain both, bounded" must remain in the options set rather than being treated as failure.

#### Risk Appetite Assessment

**Provisional appetite (STRATEGIC):** ≤ 12 · **Residual:** 8 · ✅ **Within appetite**

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Capability evidence assembled against the eight-category taxonomy | Dr. Benny Moog | 2026-08-21 | Likelihood 3 → 2 |
| Hands-on assessment of UC-1 to UC-6 journeys with academic reference group | A/Prof. Pearl Clavinet | 2026-09-09 | Likelihood 3 → 2 |
| Pilot acceptance criteria defined before contract signature, with remedies | Rhonda Bell | 2026-12-11 | Preserves leverage post-signature |

**Target Residual:** L2 × I4 = 8. No further reduction is honestly available — the impact is structural.

**Success Criteria:** Pilot completes with no Must-priority capability regression against the incumbent baseline.

**Monitoring:** Monthly to Education Committee during pilot. Escalation trigger — any Must-priority requirement assessed as regressed during pilot.

---

### Risk R-003: Discipline exception endorsed but unfunded

**Category:** STRATEGIC
**Status:** Open
**Risk Owner:** A/Prof. Pearl Clavinet, Chair Education Committee (STKE RACI: Education Committee accountable for the discipline exception)
**Action Owner:** Prof. Desmond Key, Dean, School of Music & Performing Arts

#### Risk Identification

**Risk Description:**
The performance-capture exception is endorsed in principle to close the argument, then drops out of the business case when costs are trimmed — leaving REQ-010 unmet and the School of Music without multi-camera, high-fidelity capture.

**Root Cause:**
REQ-010 carries a Could priority because MoSCoW measures institutional breadth, not disciplinary criticality [STKE-C2]. A requirement affecting one school loses every prioritisation exercise it enters, structurally and permanently.

**Trigger Events:**

- Exception approved without a costed line item
- Business case cost reduction round after Operations Committee approval
- Venue assessment deferred past the options stage
- Exception scope left undefined, making later reduction invisible

**Consequences if Realized:**

- Nationally recognised performance teaching capability degraded
- Principle 4 (Discipline Specialisation at the Edge) shown to be unenforceable in practice, weakening it for Health Sciences and every future case
- Music school pursues its own tooling outside the architecture — the exact failure mode Principle 4 exists to prevent

**Affected Stakeholders:**

- **Prof. Desmond Key**: The outcome he explicitly predicted
- **Prof. Priya Anand**: Same structural argument, next in line
- **Dr. Benny Moog**: Loses the discipline-specialisation defence

**Related Objectives:**

- **STKE G-9** (bounded discipline exception), **STKE O-1**, **REQ BR-005**, **REQ FR-009**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 - Likely | The pattern has occurred before — discipline tooling has sat in "investigation required" status without resolution [SL-C1] |
| **Impact** | 3 - Moderate | Severe for one school, contained institutionally; recoverable at a later capability review |
| **Inherent Risk Score** | **12** (Medium) | 4 × 3 = 12 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Concurrent decision requirement (BR-005)**: The exception is scoped, costed and decided in the same governance paper as the core recommendation
   - Owner: A/Prof. Pearl Clavinet · Effectiveness: **Strong** — dropping it later requires an explicit refusal on the record
2. **Named venues and a defined capability standard**: Makes a later reduction visible rather than silent
   - Owner: Prof. Desmond Key · Effectiveness: **Adequate** · Evidence: Not yet produced
3. **Explicit refusal path**: If refused, the REQ-010 consequence is recorded in the ADR and risk register as a governed choice

**Overall Control Effectiveness:** Adequate (reduces 12 → 9)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | Concurrent decision makes silent defunding hard, but does not guarantee funding — and the residual pressure is real |
| **Impact** | 3 - Moderate | Unchanged |
| **Residual Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 25% (12 → 9)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:** The available treatment is procedural — it converts a silent omission into an explicit decision. It cannot compel a funding outcome, and this register should not pretend otherwise.

**Alternatives Considered:**

- **Tolerate**: Rejected — tolerating it means accepting the structural defect in prioritisation
- **Terminate**: Would mean removing REQ-010 from scope entirely; rejected as it converts a funding question into a capability loss without a decision

#### Risk Appetite Assessment

**Provisional appetite (STRATEGIC):** ≤ 12 · **Residual:** 9 · ✅ **Within appetite**

> Note: within appetite institutionally, materially over appetite from the School of Music's perspective. The register records the institutional view while noting that risk appetite is not uniform across an organisation.

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Venue assessment and capability standard drafted | Prof. Desmond Key with Marcus Fairlight | 2026-08-28 | Enables costing |
| Exception costed as a named business case line | Vernon Ostinato | 2026-09-25 | Likelihood 4 → 3 |
| Exception decided in the same paper as the core recommendation | A/Prof. Pearl Clavinet | 2026-10-09 | Prevents silent omission |

**Target Residual:** L2 × I3 = 6 once the exception is funded or formally refused.

**Success Criteria:** Explicit Operations Committee decision — approval with funding, or refusal with the REQ-010 consequence recorded.

**Monitoring:** At each governance gate. Escalation trigger — exception absent from any governance paper that contains the core recommendation.

---

### Risk R-004: Decision slips past October, missing the business case window

**Category:** STRATEGIC
**Status:** Open
**Risk Owner:** Prof. Otis Hammond, DVC (Education)
**Action Owner:** Rhonda Bell, Project Manager

#### Risk Identification

**Risk Description:**
Governance cycles, criteria deadlock or missing baselines push the decision beyond 9 October 2026, leaving insufficient time to procure, build, migrate and train before Semester 2 2027 — and creating pressure to cut over during a teaching period.

**Root Cause:**
The timeline has no slack between the October gate and the single viable July 2027 cutover window. Committee cycles are fixed and cannot be compressed.

**Trigger Events:**

- Baselines not delivered on their August dates (R-006)
- Criteria workshop deadlock (R-001)
- Education Committee returns the paper (R-005)
- Contract negotiation extends beyond December

**Consequences if Realized:**

- September business case proceeds without the capture decision, or is delayed
- Cutover pushed to 2028, extending duplicate licensing by a full year (compounds R-011)
- Pressure to cut over mid-semester, breaching REQ-032 and Principle 15

**Affected Stakeholders:**

- **Vernon Ostinato**: Business case incomplete or delayed
- **Marcus Fairlight, Nina Kalimba**: Compressed transition lands on their teams
- **Prof. Priya Anand**: Her cohorts carry the disruption if cutover is compressed

**Related Objectives:** **STKE G-1**, **STKE G-8**, **REQ BC-1**, **REQ BC-2**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | Four separate upstream risks can each cause it; individually unlikely, collectively a reasonable chance |
| **Impact** | 4 - Major | A year's delay to the rationalisation benefit, or a cutover in the wrong window |
| **Inherent Risk Score** | **12** (Medium) | 3 × 4 = 12 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Committee dates confirmed and papers scheduled backwards from them**
   - Owner: Rhonda Bell · Effectiveness: **Strong**
2. **Platform-neutral work progressed in parallel** — provisioning (G-4), captioning test set, retention schedule and E8 remediation do not wait for the decision
   - Owner: Rhonda Bell · Effectiveness: **Strong** — reduces the cost of slippage rather than its likelihood
3. **Absolute prohibition on mid-semester cutover (BR-006)** — the contingency is a later date, never a worse window
   - Owner: Cassandra Rhodes · Effectiveness: **Strong**
4. **Baseline due dates tracked as hard milestones with named owners**
   - Owner: Rhonda Bell · Effectiveness: **Adequate**

**Overall Control Effectiveness:** Strong (reduces 12 → 8)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 - Unlikely | Scheduling discipline and parallel work address the controllable causes |
| **Impact** | 4 - Major | Unchanged — if the window is missed it is missed by a year; the academic calendar does not negotiate |
| **Residual Risk Score** | **8** (Medium) | 2 × 4 = 8 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 33% (12 → 8)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:** Impact is fixed by the academic calendar; all treatment targets likelihood and the cost of the fallback.

**Alternatives Considered:**

- **Tolerate**: Rejected — the compounding cost of a year's duplicate licensing is material
- **Transfer / Terminate**: Not applicable

#### Risk Appetite Assessment

**Provisional appetite (STRATEGIC):** ≤ 12 · **Residual:** 8 · ✅ **Within appetite**

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Committee dates and paper deadlines confirmed in writing | Rhonda Bell | 2026-08-07 | Likelihood 3 → 2 |
| Platform-neutral workstreams started ahead of the decision | Sam Okafor, Eleanor Frame, Tobias Ohm | 2026-08-28 | Reduces slippage cost |
| Fallback plan documented: pilot S2 2027, cutover start of 2028 | Rhonda Bell | 2026-09-25 | Contingency, not a target |

**Target Residual:** L2 × I4 = 8. Impact cannot be reduced further.

**Success Criteria:** Operations Committee approval obtained on or before 2026-10-09.

**Monitoring:** Fortnightly at steering against the milestone schedule. Escalation trigger — any milestone slipping more than 5 working days.

---

### Risk R-005: Education Committee returns the paper

**Category:** STRATEGIC
**Status:** Open
**Risk Owner:** Prof. Otis Hammond, DVC (Education)
**Action Owner:** Rhonda Bell, Project Manager

#### Risk Identification

**Risk Description:**
The recommendation reaches Education Committee reading as a cost and consolidation exercise, and the committee returns it for stronger academic evidence — costing a full committee cycle and pushing the decision past the business case window.

**Root Cause:**
The project's most quantifiable evidence is financial, and financial evidence writes itself more readily than pedagogical evidence. Without deliberate effort the paper drifts toward the numbers that are easiest to present.

**Trigger Events:**

- Paper led by licence economics with teaching outcomes as supporting material
- Deans see the recommendation for the first time at committee
- No documented academic reference group input
- Clavinet not pre-briefed before the paper is finalised

**Consequences if Realized:**

- One full committee cycle lost, directly triggering R-004
- Academic confidence in the process reduced at the moment it is most needed
- Recommendation reopened rather than merely delayed

**Affected Stakeholders:** **A/Prof. Pearl Clavinet** (her committee's authority), **Deans Key and Anand**, **Prof. Otis Hammond**

**Related Objectives:** **STKE G-1**, **STKE O-6**, **REQ BR-002**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | A reasonable chance absent deliberate framing; the committee has an established record of returning insufficiently evidenced papers |
| **Impact** | 3 - Moderate | One committee cycle — significant against this timeline, but not fatal in itself |
| **Inherent Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Pre-briefing before the paper is finalised** — Clavinet sees it before her committee does
   - Owner: Rhonda Bell · Effectiveness: **Strong**
2. **Teaching outcomes lead the paper; cost is supporting analysis**
   - Owner: Dr. Benny Moog · Effectiveness: **Adequate**
3. **Academic reference group input documented, including Castle's**
   - Owner: A/Prof. Pearl Clavinet · Effectiveness: **Adequate**
4. **Deans pre-briefed at options stage** — no first sight at committee
   - Owner: Rhonda Bell · Effectiveness: **Adequate**

**Overall Control Effectiveness:** Adequate (reduces 9 → 6)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 - Unlikely | Pre-briefing removes the most common cause of a returned paper — surprise |
| **Impact** | 3 - Moderate | Unchanged |
| **Residual Risk Score** | **6** (Medium) | 2 × 3 = 6 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 33% (9 → 6)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT · Low-cost, high-yield treatment: briefings and paper structure.

**Alternatives Considered:** **Tolerate** — reasonable on score alone, rejected because the treatment costs almost nothing and the consequence chains directly into R-004.

#### Risk Appetite Assessment

**Provisional appetite (STRATEGIC):** ≤ 12 · **Residual:** 6 · ✅ **Within appetite**

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Clavinet pre-briefed on draft recommendation | Rhonda Bell | 2026-09-14 | Likelihood 3 → 2 |
| Deans Key and Anand briefed at options stage | Rhonda Bell | 2026-09-14 | Removes committee surprise |
| Academic reference group input documented in the paper | Dr. Benny Moog | 2026-09-18 | Addresses the stated return reason |

**Target Residual:** L2 × I3 = 6 (achieved by the controls above).

**Success Criteria:** Education Committee endorses on first submission, 2026-09-25.

**Monitoring:** Weekly in the four weeks before committee. Escalation trigger — pre-briefing not completed 10 working days before the paper deadline.

---

### Risk R-006: Baseline data not delivered; evaluation proceeds on assumptions

**Category:** OPERATIONAL
**Status:** Open
**Risk Owner:** Rhonda Bell, Project Manager (escalation: Prof. Otis Hammond)
**Action Owner:** Grace Tanaka, Cassandra Rhodes, Marcus Fairlight, Eleanor Frame, Nina Kalimba, Dr. Benny Moog (one per dataset)

#### Risk Identification

**Risk Description:**
Some or all of the six baseline datasets — contract values, Microsoft entitlement position, appliance inventory, capture coverage telemetry, archive volume, support ticket data — are not delivered by their August dates, and the evaluation proceeds against assumed figures.

**Root Cause:**
The data is held across six separate owners in four business units, none of whom report to the project, and none of the datasets is maintained as a standing artefact.

**Trigger Events:**

- Any of the six due dates (2026-08-14, 08-21, 08-28) passing without delivery
- A dataset delivered but incomplete or unreconciled
- Contract register found not to hold current renewal terms
- Appliance register found not to exist in usable form

**Consequences if Realized:**

- Evaluation criteria weighted against assumed rather than actual costs
- Five other risks in this register (R-007, R-010, R-011, R-020, R-021) become unreliably assessed
- Business case built on invented baselines — the specific failure both prior artifacts were written to avoid
- Whole-of-life comparison (BR-003) not credible at Operations Committee

**Affected Stakeholders:**

- **Vernon Ostinato**: Cannot validate a cost model built on assumptions
- **Cassandra Rhodes**: Her consolidation argument depends on the entitlement position being real
- **Grace Tanaka**: Cannot construct defensible criteria without contract terms
- **Marcus Fairlight**: Estate constraint remains invisible until it is a surprise

**Related Objectives:** **STKE Baseline Data Status table**, **STKE G-7**, **REQ D-1, D-2, D-3, D-8**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 - Likely | Six datasets, six owners, none with a project reporting line, all within four weeks — and four are already marked At Risk in ARC-002-REQ |
| **Impact** | 4 - Major | Undermines the evaluation, the cost model, and the reliability of five other risk assessments |
| **Inherent Risk Score** | **16** (High) | 4 × 4 = 16 |

**Risk Zone:** 🟧 High (13-19)

#### Current Controls and Mitigations

1. **Named owner and due date per dataset**, published in ARC-002-STKE §1 and ARC-002-REQ §14
   - Owner: Rhonda Bell · Effectiveness: **Adequate** — names an owner but carries no authority over them
2. **Escalation to steering at first slip, not at the point of impact**
   - Owner: Rhonda Bell · Effectiveness: **Adequate**
3. **⚠️ marking convention**: every figure derived from an unsourced baseline is explicitly flagged in both upstream artifacts, so assumption cannot masquerade as fact
   - Owner: Rhonda Bell · Effectiveness: **Strong** — does not deliver the data, but prevents the worst consequence
4. **Criteria signature gate (BR-004)**: criteria cannot be signed on assumed baselines without that being visible to all three signatories
   - Owner: Grace Tanaka · Effectiveness: **Adequate**

**Overall Control Effectiveness:** Adequate (reduces 16 → 9)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | Named ownership and early escalation improve the odds, but the project has no line authority over any of the six owners |
| **Impact** | 3 - Moderate | The ⚠️ convention and the signature gate mean a partial baseline produces a visibly caveated decision rather than a false one |
| **Residual Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 44% (16 → 9)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:** Highest inherent score in the register and the earliest due date. It also gates five other assessments, giving treatment here the highest leverage of any action in the plan.

**Alternatives Considered:**

- **Tolerate**: Rejected — proceeding on assumptions is precisely the failure mode being guarded against
- **Transfer**: Not applicable

#### Risk Appetite Assessment

**Provisional appetite (OPERATIONAL):** ≤ 9 · **Residual:** 9 · ✅ **At appetite limit** — no headroom; any deterioration breaches.

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Written confirmation from each of the six owners that the dataset exists and can be delivered | Rhonda Bell | 2026-08-07 | Converts assumption into commitment or early warning |
| Contract values, terms, renewal dates delivered | Grace Tanaka | 2026-08-14 | Unblocks R-011, R-020 |
| Microsoft entitlement position delivered | Cassandra Rhodes | 2026-08-14 | Unblocks the consolidation argument |
| Appliance inventory delivered | Marcus Fairlight | 2026-08-21 | Unblocks R-007, R-008, R-016 |
| Capture coverage telemetry and support ticket data delivered | Dr. Benny Moog, Nina Kalimba | 2026-08-21 | Establishes G-3 and G-8 baselines |
| Archive volume and retention position delivered | Eleanor Frame | 2026-08-28 | Unblocks R-014, R-021 |

**Target Residual:** L2 × I3 = 6 once all six datasets are delivered and reconciled.

**Success Criteria:** All six datasets delivered by 2026-08-28; zero ⚠️ markers remaining in the business case cost model.

**Monitoring:** Weekly until 2026-08-28. Escalation trigger — any dataset not confirmed as deliverable by 2026-08-07, or any date missed by more than 3 working days.

---

### Risk R-007: Room estate cannot support the selected platform

**Category:** OPERATIONAL
**Status:** Open
**Risk Owner:** Cassandra Rhodes, CIO (STKE RACI: Accountable for room and appliance assessment)
**Action Owner:** Marcus Fairlight, Manager AV & Learning Spaces

#### Risk Identification

**Risk Description:**
The appliance inventory finds a material proportion of capture-equipped rooms incompatible with the preferred platform, or beyond patching support — converting a licensing decision into a capital replacement programme discovered after the decision is made.

**Root Cause:**
The estate has aged without a refresh programme. Appliance capability was never a constraint on platform choice because the platform never changed.

**Trigger Events:**

- Inventory (due 2026-08-21) shows appliances outside vendor support
- Preferred platform requires appliance capability the estate lacks
- Appliances unable to report health telemetry, invalidating assumption A-3 in ARC-002-REQ
- Room compatibility assessed after selection rather than during evaluation

**Consequences if Realized:**

- Licence saving erased by capital cost (directly triggers R-011)
- Coverage target for REQ-009 unachievable in affected rooms
- Room works expand beyond the July 2027 window (triggers R-008)

**Affected Stakeholders:** **Vernon Ostinato** (unplanned capital), **Marcus Fairlight** (unresourced programme), **Prof. Priya Anand** (large-cohort rooms affected first)

**Related Objectives:** **STKE G-3, G-7**, **REQ TC-4**, **REQ BR-003**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | The estate is known to be behind on OS patching [PC-C1], which is circumstantial evidence of age; the inventory does not yet exist |
| **Impact** | 4 - Major | Converts an opex decision into a capex programme, with consequences for cost, coverage and schedule simultaneously |
| **Inherent Risk Score** | **12** (Medium) | 3 × 4 = 12 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Inventory scheduled before the decision, not after** (2026-08-21)
   - Owner: Marcus Fairlight · Effectiveness: **Strong** — timing is the control
2. **Room compatibility as a scored evaluation criterion**
   - Owner: Grace Tanaka · Effectiveness: **Strong**
3. **Refresh cost split into "required regardless" and "decision-caused"** (ARC-002-REQ Conflict C-2)
   - Owner: Vernon Ostinato · Effectiveness: **Adequate** — makes the finding informative rather than disqualifying
4. **Phased room programme available as fallback**, prioritising largest teaching spaces
   - Owner: Marcus Fairlight · Effectiveness: **Adequate**

**Overall Control Effectiveness:** Adequate (reduces 12 → 8)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 - Unlikely | Compatibility scored during evaluation means an incompatible platform is unlikely to be selected |
| **Impact** | 4 - Major | Unchanged — if the estate needs replacing, it needs replacing under every option |
| **Residual Risk Score** | **8** (Medium) | 2 × 4 = 8 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 33% (12 → 8)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:** Treatment converts a post-decision surprise into a pre-decision input. It does not reduce the underlying estate condition, which is a fact to be discovered rather than a risk to be managed.

**Alternatives Considered:** **Tolerate** — rejected; the consequence chains into three other risks.

#### Risk Appetite Assessment

**Provisional appetite (OPERATIONAL):** ≤ 9 · **Residual:** 8 · ✅ **Within appetite**

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Appliance inventory: models, age, support status, telemetry capability | Marcus Fairlight | 2026-08-21 | Likelihood 3 → 2 |
| Room compatibility criterion added to the evaluation framework | Grace Tanaka | 2026-08-28 | Prevents selection of an incompatible platform |
| Refresh cost split produced for each shortlisted option | Vernon Ostinato | 2026-09-09 | Informs rather than blocks |

**Target Residual:** L2 × I4 = 8. Impact is structural.

**Success Criteria:** Inventory complete before evaluation; every shortlisted option carries a room-level compatibility assessment.

**Monitoring:** Weekly until inventory delivered, then at each options review. Escalation trigger — inventory not delivered by 2026-08-28, or more than 20% of rooms assessed as incompatible with any shortlisted option.

---

### Risk R-008: AV capacity insufficient for room works in the July window

**Category:** OPERATIONAL
**Status:** Open
**Risk Owner:** Cassandra Rhodes, CIO
**Action Owner:** Marcus Fairlight, Manager AV & Learning Spaces

#### Risk Identification

**Risk Description:**
Room reconfiguration, appliance remediation and Essential Eight account work all converge on the single July 2027 inter-semester break, exceeding the AV team's capacity — leaving rooms unready for Semester 2 or forcing works into teaching weeks.

**Root Cause:**
Three separate workstreams (platform transition, appliance patching, shared-account remediation) target the same non-teaching window because it is the only one available, and the AV team is sized for business-as-usual rather than programme delivery.

**Trigger Events:**

- Room count requiring physical intervention exceeds the team's July throughput
- Appliance replacement added to scope after the inventory (R-007)
- Additional resourcing not approved by the time the works are scheduled
- Any slippage in the decision compressing the preparation period (R-004)

**Consequences if Realized:**

- Rooms unready at the start of Semester 2 2027, so coverage target for REQ-009 is missed in those spaces
- Pressure to perform works during teaching weeks, breaching BR-006
- Essential Eight remediation deferred again, worsening R-016

**Affected Stakeholders:** **Marcus Fairlight and the AV team** (absorbing the programme), **Prof. Priya Anand and Prof. Desmond Key** (affected venues), **Nina Kalimba** (support load from unready rooms)

**Related Objectives:** **STKE G-8, G-10**, **REQ BR-006**, **REQ BR-008**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | Depends on scope from the inventory, which does not yet exist; three workstreams in one window is inherently tight |
| **Impact** | 4 - Major | Rooms unready at semester start affects teaching directly and cannot be remedied mid-semester |
| **Inherent Risk Score** | **12** (Medium) | 3 × 4 = 12 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Single combined room programme** — platform works, patching and account remediation performed in one visit per room rather than three
   - Owner: Marcus Fairlight · Effectiveness: **Strong** — the most effective control available, and the reason BR-008 is scoped into this project
2. **Phased programme prioritising the largest teaching spaces**
   - Owner: Marcus Fairlight · Effectiveness: **Adequate**
3. **Room works scheduled into non-teaching weeks with an absolute prohibition on teaching-period works**
   - Owner: Cassandra Rhodes · Effectiveness: **Strong** on compliance, but it converts a capacity problem into a schedule problem rather than solving it
4. **Coverage target adjusted explicitly rather than missed silently** if phasing is required
   - Owner: Dr. Benny Moog · Effectiveness: **Adequate**

**Overall Control Effectiveness:** Adequate (reduces 12 → 9)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | Combining the workstreams helps materially, but the capacity constraint is real and the scope is still unknown |
| **Impact** | 3 - Moderate | Phasing with an explicitly adjusted coverage target converts a teaching failure into a slower rollout |
| **Residual Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 25% (12 → 9)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:** Capacity can be added or scope phased; both are available and neither is expensive relative to the consequence. Treatment is constrained by not yet knowing the scope.

**Alternatives Considered:**

- **Transfer**: Contract AV resource for the July window — a genuine option, and the recommended treatment if the inventory shows high room counts. Recorded here as the primary contingency.
- **Tolerate**: Rejected — the consequence lands on teaching.

#### Risk Appetite Assessment

**Provisional appetite (OPERATIONAL):** ≤ 9 · **Residual:** 9 · ✅ **At appetite limit** — no headroom.

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Room works scope derived from the appliance inventory | Marcus Fairlight | 2026-09-04 | Makes the capacity gap measurable |
| Capacity plan for the July 2027 window, including contract resource option | Marcus Fairlight | 2026-11-27 | Likelihood 3 → 2 |
| Phasing plan with explicitly adjusted coverage targets if required | Dr. Benny Moog | 2027-02-26 | Impact 3 → 2 |
| Combined single-visit schedule covering platform, patching and account works | Marcus Fairlight | 2027-04-30 | Removes duplicate room visits |

**Target Residual:** L2 × I3 = 6 once the capacity plan is approved and resourced.

**Success Criteria:** All prioritised rooms ready before Semester 2 2027 teaching begins; zero works performed in teaching weeks.

**Monitoring:** Monthly from November 2026, weekly during the July window. Escalation trigger — capacity plan unapproved by 2026-12-11, or room readiness tracking behind schedule at any point in July.

---

### Risk R-009: Support and training not ready for cutover

**Category:** OPERATIONAL
**Status:** Open
**Risk Owner:** Dr. Benny Moog, Director Learning Technologies
**Action Owner:** Nina Kalimba, Manager Digital Learning Support

#### Risk Identification

**Risk Description:**
Semester 2 2027 begins with a new platform, no runbooks, and untrained staff, producing a week-one ticket spike that the support team cannot absorb and that shapes academic opinion of the platform permanently.

**Root Cause:**
Documentation and training are conventionally treated as post-go-live activities, and the support team is not represented in the selection decision.

**Trigger Events:**

- Runbooks not published before cutover
- Training scheduled after semester begins
- No pilot phase to derive realistic failure modes
- Casual academic staff appointed close to semester start without platform familiarity

**Consequences if Realized:**

- Week-one ticket volume exceeding team capacity, with teaching disrupted while tickets queue
- Academic first impression formed during the worst week, and not revisited
- Support team morale and retention affected

**Affected Stakeholders:** **Nina Kalimba's team** (absorbs it), **Dr. Wynton Castle and casual academics** (unsupported), **students** (indirect, through unavailable recordings)

**Related Objectives:** **STKE G-8**, **STKE O-2**, **REQ BR-006**, **REQ NFR-M-002**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | The default pattern for platform transitions, and the support team has no representation in the decision |
| **Impact** | 3 - Moderate | Disruptive and reputationally costly for a few weeks; recoverable within a semester |
| **Inherent Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Documentation as a named deliverable before cutover (NFR-M-002)** — runbooks, quick reference, student help content
   - Owner: Nina Kalimba · Effectiveness: **Strong** — a requirement rather than an intention
2. **Semester 1 2027 pilot deriving real failure modes** before they arrive at scale
   - Owner: Rhonda Bell · Effectiveness: **Strong**
3. **Training before each user's first teaching week on the platform (BR-006)**
   - Owner: Nina Kalimba · Effectiveness: **Adequate** — casual staff remain hard to reach
4. **Automated provisioning (R-022 control) removes the dominant current ticket category**
   - Owner: Sam Okafor · Effectiveness: **Strong** — addresses the underlying volume, not just the readiness

**Overall Control Effectiveness:** Strong (reduces 9 → 4)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 - Unlikely | Pilot-derived runbooks plus a training window before semester address the direct causes |
| **Impact** | 2 - Minor | With provisioning automated, the residual ticket load is familiarity questions rather than access failures |
| **Residual Risk Score** | **4** (Low) | 2 × 2 = 4 |

**Risk Zone:** 🟩 Low (1-5) · **Risk Reduction:** 56% (9 → 4)

#### Risk Response (4Ts Framework)

**Primary Response:** TOLERATE

**Rationale:** Residual risk is Low and well within appetite. The controls are already committed as requirements; no further action is proposed beyond delivering them. Some week-one question volume is a normal cost of any platform change and is not worth further investment to eliminate.

**Alternatives Considered:** **Treat** — additional surge support for week one was considered and judged disproportionate given the automated-provisioning control removes the dominant ticket category.

#### Risk Appetite Assessment

**Provisional appetite (OPERATIONAL):** ≤ 9 · **Residual:** 4 · ✅ **Well within appetite**

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Ticket baseline established from current capture-related volumes | Nina Kalimba | 2026-08-21 | Enables week-one forecast |
| Runbooks drafted from pilot failure modes | Nina Kalimba | 2027-06-25 | Delivers the control |
| Training delivered to coordinators and casual staff | Nina Kalimba | 2027-07-24 | Delivers the control |

**Target Residual:** 4 (no further reduction sought).

**Success Criteria:** Week-one ticket volume within the pilot-derived forecast; documentation published before cutover.

**Monitoring:** Monthly, moving to weekly during transition. Escalation trigger — runbooks not drafted by end of pilot, or week-one volume exceeding forecast by more than 50%.

---

### Risk R-010: Project 001 canonical model and role assignment not delivered in time

**Category:** OPERATIONAL
**Status:** Open
**Risk Owner:** Cassandra Rhodes, CIO
**Action Owner:** Sam Okafor, Integration Architect

#### Risk Identification

**Risk Description:**
The canonical entity model (REQ-027) and single-source institutional role assignment (REQ-024), both deliverables of project 001's integration architecture, are not available when INT-001 is built — forcing either a delay or a platform-specific point-to-point integration.

**Root Cause:**
This project consumes an architecture that a separate engagement is still defining, and project 001's WP5 depends in turn on WP4 completing.

**Trigger Events:**

- Project 001 WP5 integration architecture slips
- Canonical model defined but not implemented in an available interface
- Authoritative source for role assignment not agreed between HR and student administration
- INT-001 build starting before the model is stable

**Consequences if Realized:**

- FR-016 (enrolment-derived access) and G-4 (zero manual provisioning) blocked
- Fallback to a point-to-point mapping, breaching Principle 10 and TC-3 and recreating the fragility this project was meant to escape
- Casual staff provisioning workaround persists into the new platform

**Affected Stakeholders:** **Sam Okafor** (inherits whatever is built), **casual academic staff** (continued manual access), **Tobias Ohm** (local-account exception persists)

**Related Objectives:** **STKE G-4**, **STKE O-2**, **REQ INT-001**, **REQ D-7**, **REQ A-11**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | Cross-project dependency with its own upstream dependency; project 001's WP5 is not yet complete |
| **Impact** | 4 - Major | Blocks the single most valuable platform-neutral outcome and forces an architecture breach |
| **Inherent Risk Score** | **12** (Medium) | 3 × 4 = 12 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Shared integration architect across both projects** — Okafor holds both sides of the dependency
   - Owner: Sam Okafor · Effectiveness: **Strong** — the dependency is visible to the person who must satisfy it
2. **Dependency tracked explicitly (REQ D-7)** with the consequence documented
   - Owner: Rhonda Bell · Effectiveness: **Adequate**
3. **Provisioning capability as a mandatory evaluation gate (NFR-I-001)** — the selected platform must support event-driven provisioning regardless of when the model lands
   - Owner: Grace Tanaka · Effectiveness: **Strong** — preserves the option even if timing slips
4. **Long lead time**: INT-001 build is not required until early 2027, giving project 001 six months

**Overall Control Effectiveness:** Strong (reduces 12 → 6)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 - Unlikely | Six months of float and a shared architect make the timing failure unlikely |
| **Impact** | 3 - Moderate | If it slips, provisioning can be built to the model later without re-selecting the platform, provided the gate held |
| **Residual Risk Score** | **6** (Medium) | 2 × 3 = 6 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 50% (12 → 6)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:** The gate control is what makes this manageable — it separates *platform capability* from *model availability*, so a delay in one does not compromise the other.

**Alternatives Considered:** **Tolerate** — reasonable on residual score, rejected because the architecture-breach consequence is the specific failure the parent engagement exists to prevent.

#### Risk Appetite Assessment

**Provisional appetite (OPERATIONAL):** ≤ 9 · **Residual:** 6 · ✅ **Within appetite**

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Confirm project 001 WP5 delivery date for the canonical model | Sam Okafor | 2026-09-04 | Converts assumption A-11 into a tracked commitment |
| Provisioning capability confirmed as a mandatory gate in the criteria | Grace Tanaka | 2026-08-28 | Preserves the option under any timing |
| Interface specification for INT-001 agreed against the model | Sam Okafor | 2026-12-11 | Likelihood 3 → 2 |

**Target Residual:** L2 × I2 = 4 once the model is confirmed available.

**Success Criteria:** INT-001 built against the canonical model with no point-to-point mapping.

**Monitoring:** Monthly with project 001 delivery reporting. Escalation trigger — project 001 WP5 slipping beyond 2026-12-11.

---

### Risk R-011: Whole-of-life saving eliminated by appliance capital cost

**Category:** FINANCIAL
**Status:** Open
**Risk Owner:** Vernon Ostinato, Chief Financial Officer
**Action Owner:** Rhonda Bell, Project Manager (cost model)

#### Risk Identification

**Risk Description:**
The licence saving that justifies consolidation is eliminated — or reversed — once appliance refresh, migration effort and support cost are included, and the finding arrives at business case stage rather than at options stage.

**Root Cause:**
Lecture capture is the only L&T capability with a significant physical estate behind it. A licence-only comparison, which is the natural way to compare platforms, structurally omits the largest variable cost.

**Trigger Events:**

- Options costed on licence price alone
- Appliance inventory (R-007) shows material replacement need
- Migration effort discovered after contract signature
- Discipline exception costed late or not at all

**Consequences if Realized:**

- REQ-035 not met — the rationalisation produces no saving
- Business case credibility damaged at Operations Committee
- Unfunded capital request, or the project proceeding with a worse financial outcome than the status quo

**Affected Stakeholders:** **Vernon Ostinato** (exposed at business case), **Cassandra Rhodes** (consolidation case undermined), **Marcus Fairlight** (blamed for a cost he flagged)

**Related Objectives:** **STKE G-7**, **STKE O-3**, **REQ BR-003**, **REQ Conflict C-2**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 - Likely | Absent a deliberate control, licence-only comparison is the default behaviour, and the estate is known to be ageing |
| **Impact** | 3 - Moderate | The saving is the project's financial justification, but the project has non-financial justifications that survive |
| **Inherent Risk Score** | **12** (Medium) | 4 × 3 = 12 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Whole-of-life cost model mandated at options stage (BR-003)** covering licence, appliances, migration, support and the exception
   - Owner: Vernon Ostinato · Effectiveness: **Strong**
2. **Refresh cost split into "required regardless" and "decision-caused"** — prevents both under- and over-attribution
   - Owner: Vernon Ostinato · Effectiveness: **Strong**
3. **Inventory before decision (R-007 control)** — the input the model needs
   - Owner: Marcus Fairlight · Effectiveness: **Adequate** — not yet delivered
4. **Renewal price protection sought in contract terms**
   - Owner: Grace Tanaka · Effectiveness: **Adequate**

**Overall Control Effectiveness:** Adequate (reduces 12 → 9)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | The model surfaces the cost early, but does not change it — if the estate needs refresh, the saving may genuinely not exist |
| **Impact** | 3 - Moderate | Unchanged. Note this is a discovery risk as much as a cost risk: the honest outcome may be that no saving is available |
| **Residual Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 25% (12 → 9)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:** Treatment makes the cost visible early; it cannot make the cost smaller. The register records this distinction deliberately — a control that improves information is not a control that improves outcome.

**Alternatives Considered:**

- **Tolerate**: Rejected — the consequence is a business case failure at the final gate
- **Terminate**: If the model shows no option delivers value, the RIFF pause provision applies [SGP-C3]; recorded under R-002

#### Risk Appetite Assessment

**Provisional appetite (FINANCIAL):** ≤ 9 · **Residual:** 9 · ✅ **At appetite limit** — no headroom.

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Contract values and entitlement position delivered (R-006 dependency) | Grace Tanaka, Cassandra Rhodes | 2026-08-14 | Enables the model |
| Five-year whole-of-life model produced for every shortlisted option | Rhonda Bell | 2026-09-09 | Likelihood 4 → 3 |
| Finance review of the model at options stage, not preferred-option stage | Vernon Ostinato | 2026-09-18 | Prevents late discovery |
| Renewal price protection drafted into contract terms | Grace Tanaka | 2026-12-11 | Protects the saving after year one |

**Target Residual:** L2 × I3 = 6 once the model is validated by Finance against sourced baselines.

**Success Criteria:** Every option costed whole-of-life before shortlisting; no capital surprise between options stage and business case.

**Monitoring:** At each options and business case review. Escalation trigger — any option presented without a whole-of-life figure, or a variance greater than 20% between options-stage and business-case cost.

---

### Risk R-012: Renewal price step-change and lock-in economics

**Category:** FINANCIAL
**Status:** Open
**Risk Owner:** Vernon Ostinato, Chief Financial Officer
**Action Owner:** Grace Tanaka, Procurement & Vendor Manager

#### Risk Identification

**Risk Description:**
The selected platform is priced attractively for the initial term, then repriced substantially at first renewal once the university has migrated its archive, trained its staff and lost practical ability to leave.

**Root Cause:**
Migration cost and archive gravity create switching costs that grow over the contract term. A supplier's pricing power at renewal is a function of how expensive leaving has become.

**Trigger Events:**

- Contract signed without renewal price protection
- Export capability contractual but never tested (links to R-020)
- Archive migrated in a proprietary format
- Single-supplier position with no credible alternative at renewal

**Consequences if Realized:**

- Five-year whole-of-life position invalidated after year three
- REQ-035 met initially, then breached at renewal
- Second rationalisation exercise required to escape

**Affected Stakeholders:** **Vernon Ostinato**, **Grace Tanaka** (negotiating from a weak position), **Cassandra Rhodes** (funding the increase)

**Related Objectives:** **STKE G-7**, **REQ BR-003**, **REQ NFR-I-002**, **Principle 9**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | A recognised pattern in education platform contracts, though not universal |
| **Impact** | 3 - Moderate | Material to the five-year position but outside the immediate project window |
| **Inherent Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Renewal price protection as a contract term** — capped uplift, indexed
   - Owner: Grace Tanaka · Effectiveness: **Strong** where achievable
2. **Open-format export as a mandatory gate (NFR-I-002), tested not asserted** — preserves credible exit and therefore negotiating position
   - Owner: Grace Tanaka · Effectiveness: **Strong** — this is the control that actually constrains pricing power
3. **Whole-of-life model runs five years, spanning at least one renewal**
   - Owner: Vernon Ostinato · Effectiveness: **Adequate**

**Overall Control Effectiveness:** Adequate (reduces 9 → 6)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 - Unlikely | Price protection plus proven exit capability materially reduce a supplier's ability to reprice |
| **Impact** | 3 - Moderate | Unchanged |
| **Residual Risk Score** | **6** (Medium) | 2 × 3 = 6 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 33% (9 → 6)

#### Risk Response (4Ts Framework)

**Primary Response:** TRANSFER

**Rationale:** This is the one risk in the register genuinely transferable to a third party. Contractual price protection shifts renewal-pricing exposure to the supplier for the protected period — the university exchanges some initial-term price flexibility for future certainty.

**Alternatives Considered:**

- **Treat**: Partially applied — the export gate is a treatment that supports the transfer
- **Tolerate**: Rejected — exposure sits outside the project's monitoring horizon, so an untreated risk would simply be forgotten

#### Risk Appetite Assessment

**Provisional appetite (FINANCIAL):** ≤ 9 · **Residual:** 6 · ✅ **Within appetite**

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Renewal price protection clause drafted and negotiated | Grace Tanaka | 2026-12-11 | Likelihood 3 → 2 |
| Export capability tested during evaluation, not accepted contractually | Dr. Benny Moog | 2026-09-09 | Preserves exit leverage |
| Renewal review scheduled 12 months before contract end | Grace Tanaka | 2026-12-11 | Ensures the risk is revisited |

**Target Residual:** 6 (accepted after transfer).

**Success Criteria:** Price protection secured for the full initial term plus first renewal; export demonstrated in evaluation.

**Monitoring:** Annually after signature; formally 12 months before renewal. Escalation trigger — price protection not achievable in negotiation, which would return the response to TREAT and require reassessment.

---

### Risk R-013: PIA incomplete at contract signature; APP 8 position unresolved

**Category:** COMPLIANCE
**Status:** Open
**Risk Owner:** Eleanor Frame, Privacy & Records Officer
**Action Owner:** Eleanor Frame, with Grace Tanaka (contract terms)

#### Risk Identification

**Risk Description:**
The contract is signed before the Privacy Impact Assessment is complete, with the data residency and APP 8 cross-border disclosure position unresolved — leaving the university contractually committed to an arrangement it has not assessed.

**Root Cause:**
Privacy assessment conventionally follows selection, and the Privacy Officer's leverage exists only before signature. Recordings capturing students are personal information with a biometric-adjacent character, currently under assumed AU and US hosting, and are flagged as a partial APP 8 trigger [PC-C2] [PC-C3].

**Trigger Events:**

- Contract drafting beginning before the PIA is initiated
- Residency requirements absent from the evaluation criteria
- Preferred option confirmed without a hosting-location disclosure
- Timeline compression between the October decision and the December signature

**Consequences if Realized:**

- Statutory non-compliance exposure under the Privacy Act 1988
- Offshore hosting locked in contractually with no APP 8 assessment of accountability, contract clauses or the practicability of AU alternatives
- Remediation only available at renewal, years later
- Privacy Officer's sign-off role reduced to ratification after the fact

**Affected Stakeholders:**

- **Students**: Their recordings hosted under an unassessed arrangement; they have no voice in the decision
- **Eleanor Frame**: Accountable for a position she was not given the opportunity to assess
- **Cassandra Rhodes**: Carries the institutional exposure

**Related Objectives:** **STKE G-6, O-4**, **REQ NFR-C-001**, **REQ DR-006**, **Principles 7 and 8 (both CRITICAL)**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 - Likely | The default sequencing places privacy assessment after selection, and the October-to-December window is tight |
| **Impact** | 4 - Major | Statutory exposure, irreversible for the contract term, affecting every recorded student |
| **Inherent Risk Score** | **16** (High) | 4 × 4 = 16 |

**Risk Zone:** 🟧 High (13-19)

#### Current Controls and Mitigations

1. **PIA before contract signature mandated (NFR-C-001)** — an explicit requirement, not a convention
   - Owner: Eleanor Frame · Effectiveness: **Strong**
2. **Residency and APP 8 assessment written into the evaluation criteria** — assessed at options stage, so the preferred option's hosting is known before negotiation
   - Owner: Grace Tanaka · Effectiveness: **Strong**
3. **Frame consulted on contract terms in the RACI** — a defined role in the signature path
   - Owner: Grace Tanaka · Effectiveness: **Adequate**
4. **Cross-border disclosure register (DR-006)** — makes the position durable rather than reassessed each audit
   - Owner: Eleanor Frame · Effectiveness: **Adequate** · Evidence: Not yet created

**Overall Control Effectiveness:** Strong (reduces 16 → 8)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 - Unlikely | With residency in the criteria and the PIA a named pre-signature gate, late assessment becomes a visible omission rather than a silent default |
| **Impact** | 4 - Major | Unchanged — if it occurs, the exposure is statutory and the remedy is years away |
| **Residual Risk Score** | **8** (Medium) | 2 × 4 = 8 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 50% (16 → 8)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:** The treatment is sequencing, and sequencing is free. The entire risk is a function of when the PIA happens relative to signature.

**Alternatives Considered:**

- **Tolerate**: Rejected — statutory obligation, and the risk exceeds appetite
- **Transfer**: Contract clauses shift some liability but cannot transfer the university's own APP obligations as the entity disclosing the information

#### Risk Appetite Assessment

**Provisional appetite (COMPLIANCE):** ≤ 6 · **Residual:** 8 · ❌ **Exceeds appetite by 2 points (33%)**

**Justification for proceeding**: The residual impact rating cannot be reduced below Major while student recordings are held at all — the exposure is inherent to the activity, not to the platform. Likelihood is already reduced to Unlikely by the pre-signature gate. Proceeding requires Operations Committee acknowledgement that a Major-impact privacy risk is inherent to recorded teaching.

**Escalation Required:** Yes — Operations Committee, 2026-10-09, alongside appetite ratification.

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Residency and APP 8 requirements written into the evaluation criteria | Grace Tanaka | 2026-08-28 | Likelihood 4 → 3 |
| PIA initiated at preferred-option stage, not contract-drafting stage | Eleanor Frame | 2026-10-16 | Likelihood 3 → 2 |
| Cross-border disclosure register created for all data classes | Eleanor Frame | 2026-11-27 | Makes the position durable |
| PIA signed off before contract execution — hard gate | Eleanor Frame | 2026-12-04 | Prevents the risk entirely |

**Target Residual:** L1 × I4 = 4 (Low) once the PIA is complete and signed before signature.

**Success Criteria:** PIA complete with no unmitigated high findings before 2026-12-11; residency position documented per data class.

**Monitoring:** Fortnightly from October. Escalation trigger — contract drafting beginning before the PIA is initiated, or any proposal to sign before PIA sign-off.

---

### Risk R-014: Retention schedule not approved before migration

**Category:** COMPLIANCE
**Status:** Open
**Risk Owner:** Eleanor Frame, Privacy & Records Officer
**Action Owner:** Eleanor Frame, with A/Prof. Pearl Clavinet (Education Committee approval)

#### Risk Identification

**Risk Description:**
Migration proceeds without an approved retention schedule, so the entire archive is carried across and everything migrated becomes permanent by default — losing the only operationally natural point at which disposal can occur.

**Root Cause:**
No retention rule is currently applied to recordings, and the derived analytics have no defined retention or minimisation rules at all [PC-C4]. Approving a schedule requires an Education Committee cycle that has not been scheduled.

**Trigger Events:**

- Migration planning completing without the schedule approved
- Education Committee cycle missed
- Academic resistance to disposal delaying approval past the migration window
- Archive volume baseline (R-006) not delivered, so the schedule cannot be scoped

**Consequences if Realized:**

- Indefinite retention of personal information, contrary to Principle 7 and the APPs
- Larger, slower, more expensive migration (compounds R-011 and R-021)
- Storage growth projections (NFR-S-001) invalidated
- The gap identified in the privacy context persists into the new platform, having survived a platform change

**Affected Stakeholders:** **Eleanor Frame**, **students** (their recordings retained indefinitely), **academic staff** (whose material is disposed of, or not), **Vernon Ostinato** (storage cost)

**Related Objectives:** **STKE G-6, O-4**, **REQ BR-007**, **REQ DR-005**, **REQ FR-014**, **REQ D-5**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 - Likely | The schedule does not exist, requires committee approval, and competes with the platform decision for the same committee's attention |
| **Impact** | 3 - Moderate | Serious compliance and cost consequence, but remediable later at higher cost — unlike R-013, it is not locked in contractually |
| **Inherent Risk Score** | **12** (Medium) | 4 × 3 = 12 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Approval made a blocking dependency on migration planning (REQ D-5)** — planning cannot complete without it
   - Owner: Rhonda Bell · Effectiveness: **Strong**
2. **Archive-on-request path (FR-014)** — converts academic resistance from a blocker into a choice, removing the main cause of delay
   - Owner: Eleanor Frame · Effectiveness: **Strong**
3. **Disposal as the default at end of retention**, with continued retention requiring an active decision
   - Owner: Eleanor Frame · Effectiveness: **Adequate**
4. **Long runway** — approval needed by April 2027 for a July 2027 migration

**Overall Control Effectiveness:** Strong (reduces 12 → 6)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 - Unlikely | Blocking dependency plus a nine-month runway plus a pre-agreed answer to the main objection |
| **Impact** | 3 - Moderate | Unchanged |
| **Residual Risk Score** | **6** (Medium) | 2 × 3 = 6 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 50% (12 → 6)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT · **Alternatives**: Tolerate rejected — the compliance gap is pre-existing and this project is the opportunity to close it; a second failure to close it would be harder to justify than the first.

#### Risk Appetite Assessment

**Provisional appetite (COMPLIANCE):** ≤ 6 · **Residual:** 6 · ✅ **At appetite limit** — no headroom.

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Archive volume and current retention position delivered | Eleanor Frame | 2026-08-28 | Enables scoping |
| Retention schedule drafted, covering recordings, transcripts, captions and analytics identifiers | Eleanor Frame | 2026-11-27 | Likelihood 4 → 3 |
| Education Committee approval obtained | A/Prof. Pearl Clavinet | 2027-04-30 | Likelihood 3 → 2 |
| Schedule configured in the target platform before migration | Rhonda Bell | 2027-07-24 | Delivers disposal at migration |

**Target Residual:** L1 × I3 = 3 (Low) once approved and configured.

**Success Criteria:** Schedule approved before migration planning completes; out-of-retention content disposed of rather than migrated.

**Monitoring:** Monthly from November 2026. Escalation trigger — schedule not drafted by 2026-12-11, or committee approval not scheduled by 2027-02-26.

---

### Risk R-015: Accessibility and captioning assessed on vendor claims

**Category:** COMPLIANCE
**Status:** Open
**Risk Owner:** Dr. Benny Moog, Director Learning Technologies
**Action Owner:** Dr. Benny Moog, with Jazmin Field (Student Guild) consulted

#### Risk Identification

**Risk Description:**
WCAG 2.2 AA conformance and caption accuracy are assessed against vendor conformance statements rather than tested output, and the platform proves to caption clinical and musical vocabulary poorly once in live teaching.

**Root Cause:**
Automatic captioning quality varies most in discipline-specific vocabulary, which is precisely what a general conformance claim does not measure. Building a test set requires effort from two faculties before evaluation.

**Trigger Events:**

- Discipline-vocabulary test set (REQ D-8) not built before evaluation
- Captioning scored on availability rather than measured accuracy
- Accessibility assessed against a vendor VPAT rather than the configured platform
- Correction capacity (REQ D-6) not resourced, so poor captions are never fixed

**Consequences if Realized:**

- REQ-029 met on paper, breached in practice — the students most dependent on captions receive the worst service
- Principle 14 breached: accessibility remediated after deployment rather than assessed during evaluation
- Correction workload transferred to academics without support
- Potential complaint exposure, and reputational consequence via the Student Guild

**Affected Stakeholders:** **Students with disability and students studying in a second language** (direct), **Jazmin Field** (advocacy position), **Prof. Priya Anand and Prof. Desmond Key** (their vocabularies are the hard cases), **Nina Kalimba** (correction workload)

**Related Objectives:** **STKE G-5, O-5**, **REQ NFR-C-002**, **REQ NFR-U-003**, **REQ FR-006**, **REQ D-8**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 - Likely | Testing captions properly requires deliberate effort that is easily displaced by the platform argument; the default is to accept the vendor claim |
| **Impact** | 3 - Moderate | Serious for affected students and remediable, but through ongoing correction cost rather than platform replacement |
| **Inherent Risk Score** | **12** (Medium) | 4 × 3 = 12 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Accessibility as a mandatory pass/fail gate (NFR-C-002)** — not a scored criterion that can be traded away
   - Owner: Grace Tanaka · Effectiveness: **Strong**
2. **Discipline-vocabulary test set built before evaluation (REQ D-8)**, reused each semester
   - Owner: Dr. Benny Moog · Effectiveness: **Strong** · Evidence: Not yet built — this dependency is marked At Risk
3. **Vendor accuracy claims explicitly not accepted as evidence (NFR-U-003)**
   - Owner: Dr. Benny Moog · Effectiveness: **Strong**
4. **Conformance assessed against the platform as configured**, not against a generic statement
   - Owner: Dr. Benny Moog · Effectiveness: **Adequate**

**Overall Control Effectiveness:** Strong (reduces 12 → 6)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 - Unlikely | A mandatory gate plus a fixed test set makes claim-based assessment difficult — provided the test set exists |
| **Impact** | 3 - Moderate | Unchanged |
| **Residual Risk Score** | **6** (Medium) | 2 × 3 = 6 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 50% (12 → 6)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT · **Alternatives**: Tolerate rejected — Principle 14 is rated CRITICAL and the consequence falls on students who cannot work around it.

#### Risk Appetite Assessment

**Provisional appetite (COMPLIANCE):** ≤ 6 · **Residual:** 6 · ✅ **At appetite limit** — conditional on the test set being built. If D-8 fails, residual returns to 9 and breaches appetite.

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Discipline-vocabulary test set built with Health Sciences and Music | Dr. Benny Moog | 2026-09-04 | Likelihood 4 → 2; without this the control fails |
| Accuracy threshold agreed and written into the criteria | Grace Tanaka | 2026-08-28 | Makes the gate measurable |
| Caption correction capacity resourced (REQ D-6) | Nina Kalimba | 2027-02-26 | Sustains accuracy after go-live |
| Semester accuracy sampling process established | Dr. Benny Moog | 2027-07-24 | Detects drift |

**Target Residual:** L2 × I2 = 4 (Low) once correction capacity is resourced and sampling is running.

**Success Criteria:** Caption accuracy measured against the test set before selection; 100% of recordings captioned within 24 hours post-cutover.

**Monitoring:** Weekly until the test set is built, then each semester. Escalation trigger — test set not built by 2026-09-04, which invalidates the primary control.

---

### Risk R-016: Essential Eight gaps persist on the capture estate

**Category:** COMPLIANCE
**Status:** Open
**Risk Owner:** Tobias Ohm, Cybersecurity Lead
**Action Owner:** Marcus Fairlight, Manager AV & Learning Spaces

#### Risk Identification

**Risk Description:**
Shared administrative accounts remain in the AV and capture estate and appliances stay outside the managed patching regime, so the university misses its ML2 target for two mitigation strategies and retains an exploitable estate of network-connected devices in every teaching space.

**Root Cause:**
The gap is pre-existing and structural: "restrict administrative privileges" sits at ML1 because of legacy shared admin accounts in the AV/capture estate, and "patch operating systems" sits at ML1 because lecture-theatre capture appliances are behind [PC-C1]. Remediation requires physical access to every room, which is why it has been deferred before.

**Trigger Events:**

- Remediation descoped to protect the project budget or the July window
- Appliance inventory shows devices that cannot be patched, converting remediation to replacement
- AV capacity exhausted by platform works (R-008), displacing security work
- Decision slippage (R-004) compressing the room programme

**Consequences if Realized:**

- ML2 target for end 2027 missed on two of eight strategies; REQ-033 unmet
- A fleet of unpatched, shared-credential devices on the network in every teaching space — a genuine attack surface, not a paperwork gap
- Third deferral becomes the precedent; the gap becomes permanent
- Compounds R-018 — compromised capture devices are a plausible route to a recordings breach

**Affected Stakeholders:** **Tobias Ohm** (accountable for a target he cannot reach), **Cassandra Rhodes** (owns the E8 commitment), **Marcus Fairlight** (owns the estate), **students and staff** (whose recordings sit on the estate)

**Related Objectives:** **STKE G-10, O-4**, **REQ BR-008**, **REQ NFR-SEC-002**, **REQ NFR-SEC-004**, **Principle 16 (CRITICAL)**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 4 - Likely | The work has already been deferred at least once, competes with platform works for the same window and team, and has no dedicated funding |
| **Impact** | 3 - Moderate | Security exposure across the teaching estate and a missed maturity target; not catastrophic in itself, but it is the enabling condition for a more serious event |
| **Inherent Risk Score** | **12** (Medium) | 4 × 3 = 12 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Remediation scoped into this project (BR-008)** rather than left to a successor programme
   - Owner: Tobias Ohm · Effectiveness: **Adequate** — scoping is not funding
2. **Combined single-visit room programme (R-008 control)** — security work rides along with platform works
   - Owner: Marcus Fairlight · Effectiveness: **Strong** — the most credible route to completion
3. **Per-device identity mandated, shared credentials prohibited (NFR-SEC-002)** for the new estate
   - Owner: Tobias Ohm · Effectiveness: **Strong** for new devices, no effect on legacy
4. **Unpatchable appliances identified and replaced or removed, not retained as exceptions (NFR-SEC-004)**
   - Owner: Marcus Fairlight · Effectiveness: **Adequate** — depends on replacement funding

**Overall Control Effectiveness:** Weak-to-Adequate (reduces 12 → 9) — the weakest control performance in the register

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | Scoping and the combined programme help, but the work remains unfunded, competes for constrained AV capacity, and has a track record of deferral |
| **Impact** | 3 - Moderate | Unchanged |
| **Residual Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 25% (12 → 9)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:** The exposure is real and the university has already committed to an ML2 target. The honest position is that current controls are insufficient — this risk needs funding, not further process.

**Alternatives Considered:**

- **Tolerate**: Rejected by the register, but note that a third deferral *is* tolerance by default. If Operations Committee will not fund the work, it should tolerate the risk explicitly and record the acceptance, rather than allowing omission to make the decision.
- **Transfer**: Not applicable — the estate is university-owned

#### Risk Appetite Assessment

**Provisional appetite (COMPLIANCE):** ≤ 6 · **Residual:** 9 · ❌ **Exceeds appetite by 3 points (50%)** — the largest breach in the register.

**Justification**: No justification for proceeding is offered. This risk should either be funded down to appetite or explicitly accepted by the Operations Committee with the acceptance recorded.

**Escalation Required:** Yes — Cybersecurity Lead to CIO immediately; Operations Committee 2026-10-09.

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Appliance inventory including patch status and account inventory | Marcus Fairlight | 2026-08-21 | Quantifies the gap |
| Remediation cost included in the business case as a named line | Vernon Ostinato | 2026-09-25 | Converts scoping into funding |
| Shared administrative accounts removed as rooms are visited | Marcus Fairlight | 2027-07-24 | Likelihood 3 → 2 |
| Retained appliances brought into the managed patching regime | Marcus Fairlight | 2027-12-11 | Impact 3 → 2 |
| E8 self-assessment refreshed to evidence ML2 for this estate | Tobias Ohm | 2027-12-11 | Confirms closure |

**Target Residual:** L2 × I2 = 4 (Low) once funded and delivered.

**Success Criteria:** Zero shared administrative accounts at cutover; 100% of retained appliances patched; ML2 evidenced on both strategies by end 2027.

**Monitoring:** Monthly to the Cybersecurity Lead; quarterly to Operations Committee. Escalation trigger — remediation absent from the business case, or any proposal to descope it from the room programme.

---

### Risk R-017: Procurement probity breached by informal vendor contact

**Category:** COMPLIANCE
**Status:** Open
**Risk Owner:** Grace Tanaka, Procurement & Vendor Manager
**Action Owner:** Grace Tanaka

#### Risk Identification

**Risk Description:**
One or both principals continue existing informal vendor relationships after criteria drafting begins, giving a supplier advance insight into the evaluation and exposing the outcome to challenge.

**Root Cause:**
Both Rhodes and Moog hold established account relationships that are an asset for information-gathering before criteria exist and a liability afterwards. The transition point is a date, not an event, so it is easy to miss.

**Trigger Events:**

- Vendor contact after 2026-08-14 not routed through Procurement
- A supplier referencing evaluation content not yet published
- Roadmap or pricing discussions held outside the process
- Written instruction to suppliers and principals not issued

**Consequences if Realized:**

- Evaluation outcome challengeable by an unsuccessful supplier
- Perception of a predetermined decision, undermining BR-004 and with it R-001's primary control
- Remediation requires extending the same information to all suppliers, costing time against a tight schedule
- Audit exposure for the university's procurement function

**Affected Stakeholders:** **Grace Tanaka** (professional accountability), **Prof. Otis Hammond** (defensibility of the decision), **all three suppliers** (fair treatment), **Dr. Benny Moog and Cassandra Rhodes** (their own positions weakened by the appearance of advantage)

**Related Objectives:** **STKE G-2, O-6**, **REQ BR-004**, **REQ BC-4**, **REQ Conflict C-5**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | Not malicious but genuinely easy — pre-existing relationships and ongoing contractual business make incidental contact natural |
| **Impact** | 4 - Major | A successful challenge would void the process and restart it outside the available window |
| **Inherent Risk Score** | **12** (Medium) | 3 × 4 = 12 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Single point of contact through Procurement from criteria drafting (BC-4)**
   - Owner: Grace Tanaka · Effectiveness: **Strong** where enforced
2. **Written instruction to both principals and all three suppliers**, stating the date and what may still be discussed
   - Owner: Grace Tanaka · Effectiveness: **Strong** — converts an assumption into a notified rule
3. **Contact log maintained**
   - Owner: Grace Tanaka · Effectiveness: **Adequate**
4. **Disclosure and materiality assessment if a breach occurs**, with information extended to all suppliers to restore parity
   - Owner: Grace Tanaka · Effectiveness: **Adequate** — a recovery control, not a preventive one

**Overall Control Effectiveness:** Adequate (reduces 12 → 8)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 - Unlikely | Written instruction and a log make inadvertent breach much less likely, though not impossible given ongoing contractual business with the incumbent |
| **Impact** | 4 - Major | Unchanged — a material breach still voids the process regardless of intent |
| **Residual Risk Score** | **8** (Medium) | 2 × 4 = 8 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 33% (12 → 8)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT · **Alternatives**: Tolerate rejected — the impact is disproportionate to the trivial cost of the control.

#### Risk Appetite Assessment

**Provisional appetite (COMPLIANCE):** ≤ 6 · **Residual:** 8 · ❌ **Exceeds appetite by 2 points (33%)**

**Justification for proceeding**: Likelihood is already minimised; the residual is driven entirely by an Impact rating that cannot be reduced, since any material breach voids the process by definition. The university continues normal contractual business with the incumbent throughout, so contact cannot be reduced to zero.

**Escalation Required:** Yes — notify the Executive Sponsor of the residual position; no further mitigation available beyond disciplined enforcement.

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Written instruction issued to Rhodes, Moog and all three suppliers | Grace Tanaka | 2026-08-14 | Likelihood 3 → 2 |
| Contact log established and maintained | Grace Tanaka | 2026-08-14 | Enables materiality assessment |
| Guidance issued on permitted contact (existing contractual matters) versus prohibited (anything touching this evaluation) | Grace Tanaka | 2026-08-14 | Prevents inadvertent breach |

**Target Residual:** 8 — no further reduction available. This risk is accepted at its residual level with active enforcement.

**Success Criteria:** Zero unlogged vendor contact between 2026-08-14 and contract award; no supplier challenge raised.

**Monitoring:** Weekly during evaluation. Escalation trigger — any contact reported outside the log, assessed for materiality within 48 hours.

---

### Risk R-018: Privacy incident involving student recordings

**Category:** REPUTATIONAL
**Status:** Open
**Risk Owner:** Eleanor Frame, Privacy & Records Officer
**Action Owner:** Tobias Ohm (technical controls), Eleanor Frame (response)

#### Risk Identification

**Risk Description:**
Recordings capturing students are exposed to people who should not see them — published to the wrong unit, accessible after withdrawal, exported inappropriately, or breached through the capture estate — triggering an eligible-data-breach assessment under the Notifiable Data Breach scheme.

**Root Cause:**
The project holds a large, growing archive of personal information with a biometric-adjacent character [PC-C2], accessed daily by thousands of people whose permissions derive from constantly changing enrolment data, on an estate with known security debt (R-016).

**Trigger Events:**

- Recording published against the wrong unit — assessed in ARC-002-REQ as a privacy incident, not a data quality defect
- Access persisting after student withdrawal because deprovisioning lags
- Bulk export performed without authorisation or with excessive scope
- Compromise of an unpatched capture appliance with shared credentials (R-016)
- Migration error exposing archive content (R-021)

**Consequences if Realized:**

- OAIC notification obligation with a 30-day assessment clock [PC-C5]
- Notification to affected students, with attendant media and Student Guild attention
- Loss of student and academic trust in recorded teaching, potentially reducing capture consent and undermining the project's purpose
- Institutional reputational damage disproportionate to the technical scale of the incident

**Affected Stakeholders:** **Students** (whose recordings are exposed), **Jazmin Field** (advocacy), **Eleanor Frame** (response accountability), **Cassandra Rhodes** (institutional exposure), **Prof. Stella Groove** (VC — external consequence)

**Related Objectives:** **STKE O-4**, **REQ NFR-C-001**, **REQ NFR-C-003**, **REQ NFR-C-005**, **REQ FR-016**, **Principle 7 (CRITICAL)**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | Not probable in any given period, but the exposure surface is large and permanent: thousands of users, daily access, continuous enrolment change |
| **Impact** | 5 - Catastrophic | Statutory notification, media exposure, and loss of trust in recorded teaching institution-wide — the only Impact 5 rating in this register, and it is warranted |
| **Inherent Risk Score** | **15** (High) | 3 × 5 = 15 |

**Risk Zone:** 🟧 High (13-19)

#### Current Controls and Mitigations

1. **Access derived from enrolment with no local access lists (FR-016)**, deprovisioning within 15 minutes
   - Owner: Sam Okafor · Effectiveness: **Strong** — removes the largest class of exposure
2. **SSO with MFA, no local accounts (NFR-SEC-001)** as a mandatory gate
   - Owner: Tobias Ohm · Effectiveness: **Strong**
3. **Encryption in transit and at rest including appliance buffers (NFR-SEC-003)**
   - Owner: Tobias Ohm · Effectiveness: **Strong**
4. **Tamper-evident audit logging of view, export and disposal (NFR-C-003)**
   - Owner: Tobias Ohm · Effectiveness: **Adequate** — detective rather than preventive
5. **Vendor breach notification within 24 hours (NFR-C-005)** — preserves the university's 30-day assessment window
   - Owner: Grace Tanaka · Effectiveness: **Adequate**
6. **Quarantine of recordings that cannot be associated to a unit**, rather than publishing them
   - Owner: Dr. Benny Moog · Effectiveness: **Strong** — addresses the wrong-unit trigger directly

**Overall Control Effectiveness:** Strong (reduces 15 → 8)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 - Unlikely | Enrolment-derived access, quarantine on failed association, MFA and encryption close the identified routes |
| **Impact** | 4 - Major | Reduced from Catastrophic: audit logging and 24-hour vendor notification mean an incident is detected and scoped quickly, which materially changes the outcome of an NDB assessment. Not reducible below Major while recordings exist |
| **Residual Risk Score** | **8** (Medium) | 2 × 4 = 8 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 47% (15 → 8)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:** Preventive controls are strong and mostly already specified. The remaining exposure is irreducible while the university records students at all — which it has decided to do.

**Alternatives Considered:**

- **Transfer**: Contract terms place breach notification obligations and some liability on the supplier, but the university remains the APP entity and cannot transfer its own obligations or its reputation
- **Terminate**: Would mean not recording teaching — disproportionate, and contrary to REQ-009
- **Tolerate**: Rejected — exceeds appetite

#### Risk Appetite Assessment

**Provisional appetite (REPUTATIONAL):** ≤ 6 · **Residual:** 8 · ❌ **Exceeds appetite by 2 points (33%)**

**Justification for proceeding**: The residual is driven by an Impact rating that cannot fall below Major while the university holds recordings of students. Likelihood is already Unlikely. The alternative — not recording teaching — would breach REQ-009 and remove a service students depend on. Proceeding requires Operations Committee acknowledgement that this exposure is inherent to the activity.

**Escalation Required:** Yes — Operations Committee 2026-10-09; incident response path pre-agreed with the CIO and University Executive.

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Deprovisioning latency tested in evaluation, not assumed | Sam Okafor | 2026-09-09 | Validates the primary control |
| Vendor 24-hour breach notification secured in contract | Grace Tanaka | 2026-12-11 | Protects the 30-day assessment window |
| NDB response playbook prepared for the recordings scenario | Eleanor Frame | 2027-02-26 | Impact 4 → 3 through faster, better response |
| Audit logging validated against the access scenarios before cutover | Tobias Ohm | 2027-07-24 | Confirms detective control |
| E8 remediation completed (R-016) | Marcus Fairlight | 2027-12-11 | Closes the estate-compromise route |

**Target Residual:** L2 × I3 = 6 (within appetite) once the response playbook exists and the estate is remediated.

**Success Criteria:** Zero privacy incidents involving recordings; deprovisioning within 15 minutes verified; playbook tested by tabletop before cutover.

**Monitoring:** Monthly to the Privacy Officer; immediate escalation on any incident. Escalation trigger — any wrong-unit publication, any access-after-withdrawal event, or any unauthorised export.

---

### Risk R-019: Capture policy backlash from students or academics

**Category:** REPUTATIONAL
**Status:** Open
**Risk Owner:** A/Prof. Pearl Clavinet, Chair Education Committee
**Action Owner:** Dr. Benny Moog, Director Learning Technologies

#### Risk Identification

**Risk Description:**
The capture policy is settled by platform configuration rather than by decision — either publishing everything by default and provoking academic resistance over attendance and observation, or permitting silent opt-out and provoking student objection over inconsistent access.

**Root Cause:**
A platform default settles this question if the institution does not settle it by policy first. Neither pure position is tenable, and both constituencies have legitimate grounds.

**Trigger Events:**

- Cutover occurring before Education Committee approves the capture policy
- Unit-level exceptions configurable without an approval reference
- Student notification (FR-013) not implemented at go-live
- Publication practice varying visibly between schools

**Consequences if Realized:**

- Public disagreement between academic staff and the Student Guild, with the project as the proxy
- Principle 3 (Consistent Experience Across Schools) breached visibly in the capability where inconsistency is most apparent
- Academic goodwill lost at the point the project most needs it, during transition

**Affected Stakeholders:** **Jazmin Field and students** (access consistency), **academic staff** (discretion and observation concerns), **A/Prof. Pearl Clavinet** (her committee owns the policy)

**Related Objectives:** **STKE O-5**, **REQ FR-012**, **REQ FR-013**, **REQ Conflict C-3**, **REQ D-4**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | Likely if the policy is left to configuration, unlikely if decided deliberately — and the project has recognised it |
| **Impact** | 3 - Moderate | Disruptive and visible, but resolvable through the policy process rather than by platform change |
| **Inherent Risk Score** | **9** (Medium) | 3 × 3 = 9 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Capture policy taken to Education Committee separately from the platform decision (REQ D-4)** — decided on its own merits
   - Owner: A/Prof. Pearl Clavinet · Effectiveness: **Strong**
2. **Publish-by-default with approved, recorded exceptions (FR-012)** — the platform rejects an exception without an approval reference
   - Owner: Dr. Benny Moog · Effectiveness: **Strong** — makes the compromise enforceable rather than aspirational
3. **Student notification standard, centrally maintained (FR-013)**
   - Owner: Dr. Benny Moog · Effectiveness: **Adequate**
4. **Guild consulted in the policy development, not merely informed**
   - Owner: A/Prof. Pearl Clavinet · Effectiveness: **Adequate**

**Overall Control Effectiveness:** Strong (reduces 9 → 4)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 - Unlikely | A committee-approved policy with a legitimate exception route removes the grounds for both constituencies' objections |
| **Impact** | 2 - Minor | With a policy in place, disagreement becomes a governance discussion rather than a public dispute |
| **Residual Risk Score** | **4** (Low) | 2 × 2 = 4 |

**Risk Zone:** 🟩 Low (1-5) · **Risk Reduction:** 56% (9 → 4)

#### Risk Response (4Ts Framework)

**Primary Response:** TOLERATE

**Rationale:** Residual is Low and within appetite. The controls are committed; some ongoing disagreement about capture policy is a permanent feature of university teaching and is not worth further investment to eliminate. Annual exception-rate reporting provides the monitoring needed to detect if the compromise stops working.

**Alternatives Considered:** **Treat** — further consultation was considered and judged unlikely to change positions that are genuinely held.

#### Risk Appetite Assessment

**Provisional appetite (REPUTATIONAL):** ≤ 6 · **Residual:** 4 · ✅ **Within appetite**

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Capture policy drafted with Guild and academic input | Dr. Benny Moog | 2027-02-26 | Delivers the control |
| Education Committee approval obtained before cutover | A/Prof. Pearl Clavinet | 2027-04-30 | Delivers the control |
| Exception-rate reporting to Education Committee established | Dr. Benny Moog | 2027-12-11 | Detects control failure |

**Target Residual:** 4 (no further reduction sought).

**Success Criteria:** Policy approved before cutover; exception rate stable and below the threshold the committee sets.

**Monitoring:** Annually to Education Committee after go-live. Escalation trigger — exception rate rising year on year, indicating the default is not accepted.

---

### Risk R-020: Archive stranded by restrictive incumbent export terms

**Category:** TECHNOLOGY
**Status:** Open
**Risk Owner:** Grace Tanaka, Procurement & Vendor Manager
**Action Owner:** Dr. Benny Moog (technical verification)

#### Risk Identification

**Risk Description:**
The incumbent contract limits bulk export, prices it, or permits media export without captions and metadata — stranding the retained archive and making the platform change materially more expensive or partially impossible.

**Root Cause:**
Principle 9 applies to the platform being *left* as much as the one being joined, but the incumbent contract predates the principle. Assumption A-10 in ARC-002-REQ — that bulk export is permitted without additional fee — is unverified.

**Trigger Events:**

- Contract review (D-1) finds restrictive or fee-bearing export terms
- Export technically available but excluding captions or metadata
- Export throughput insufficient for the July window
- Vendor cooperation required and not contractually guaranteed

**Consequences if Realized:**

- BR-007 and FR-015 materially affected; archive migration becomes partial
- Extended read-only retention of the incumbent platform at additional cost
- Historical recordings lost to teaching, breaking unit-site links
- Precedent that the university cannot in practice leave a platform, weakening every future rationalisation

**Affected Stakeholders:** **Eleanor Frame** (records continuity), **academic staff** (their back-catalogue), **Vernon Ostinato** (unbudgeted export or dual-running cost), **Grace Tanaka** (negotiating position)

**Related Objectives:** **STKE G-6, O-4**, **REQ BR-007**, **REQ FR-015**, **REQ INT-007**, **REQ A-10**, **Principle 9**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | Genuinely unknown until the contract is reviewed; restrictive export terms are common in contracts of this vintage |
| **Impact** | 4 - Major | Directly threatens the migration, the cost model and the credibility of the rationalisation |
| **Inherent Risk Score** | **12** (Medium) | 3 × 4 = 12 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Contract export terms reviewed before criteria are finalised (D-1)**
   - Owner: Grace Tanaka · Effectiveness: **Strong** — timing again is the control
2. **Export tested practically during evaluation, not accepted as a contractual assurance**
   - Owner: Dr. Benny Moog · Effectiveness: **Strong**
3. **Retention schedule applied first (R-014)** — minimises the volume needing export
   - Owner: Eleanor Frame · Effectiveness: **Adequate**
4. **Read-only retention of the incumbent for a defined transition period** with a hard end date, budgeted explicitly
   - Owner: Rhonda Bell · Effectiveness: **Adequate** — a contingency that costs money

**Overall Control Effectiveness:** Adequate (reduces 12 → 8)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 - Unlikely | Early review means the position is known before commitments are made; but knowing does not change the terms |
| **Impact** | 4 - Major | Unchanged — if export is restricted, the constraint is contractual and the university has limited leverage |
| **Residual Risk Score** | **8** (Medium) | 2 × 4 = 8 |

**Risk Zone:** 🟨 Medium (6-12) · **Risk Reduction:** 33% (12 → 8)

#### Risk Response (4Ts Framework)

**Primary Response:** TREAT

**Rationale:** Early discovery converts a migration failure into a costed contingency. The controls improve information and preparedness, not the incumbent's contractual terms.

**Alternatives Considered:**

- **Transfer**: Not available — the constraint sits in an existing contract
- **Tolerate**: Rejected — the consequence extends beyond this project to the university's ability to rationalise anything

#### Risk Appetite Assessment

**Provisional appetite (TECHNOLOGY):** ≤ 12 · **Residual:** 8 · ✅ **Within appetite**

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Incumbent contract export terms reviewed and documented | Grace Tanaka | 2026-08-14 | Likelihood 3 → 2; validates or breaks assumption A-10 |
| Practical export test executed on a sample during evaluation | Dr. Benny Moog | 2026-09-09 | Confirms media, captions and metadata export together |
| Dual-running contingency costed if terms prove restrictive | Vernon Ostinato | 2026-09-25 | Prepares the fallback |
| Export throughput validated against the July window | Rhonda Bell | 2027-04-30 | Confirms feasibility |

**Target Residual:** L1 × I4 = 4 (Low) once export is contractually confirmed and practically demonstrated.

**Success Criteria:** Export terms confirmed permissive; sample export produces media, captions and metadata in open formats.

**Monitoring:** Weekly until the contract review completes. Escalation trigger — review finding restrictive terms, which requires immediate reassessment of BR-007 and the migration approach.

---

### Risk R-021: Migration data loss or reconciliation failure

**Category:** TECHNOLOGY
**Status:** Open
**Risk Owner:** Rhonda Bell, Project Manager (STKE RACI: Responsible for migration cutover; Cassandra Rhodes accountable)
**Action Owner:** Sam Okafor, Integration Architect

#### Risk Identification

**Risk Description:**
Recordings, captions or metadata are lost or corrupted during migration, or reconciliation fails to detect a discrepancy, and the loss is discovered after the incumbent platform has been decommissioned.

**Root Cause:**
A one-time bulk transfer of a large archive between two platforms with different schemas, executed under time pressure in a fixed window, with association data that must be re-resolved against a canonical model.

**Trigger Events:**

- Batch reconciliation not performed, or performed without explaining differences
- Source decommissioned before reconciliation sign-off
- Caption or metadata association lost in schema transformation
- Migration window compressed by upstream slippage (R-004)

**Consequences if Realized:**

- Permanent loss of teaching material with no recovery path
- Broken unit-site links affecting current teaching
- Records-management failure — content disposed of without authority, which is as serious as retaining it too long
- Complete loss of academic confidence in the transition

**Affected Stakeholders:** **Academic staff** (their material), **students** (referenced recordings), **Eleanor Frame** (unauthorised disposal), **Dr. Benny Moog** (platform credibility)

**Related Objectives:** **STKE G-6**, **REQ BR-007**, **REQ FR-015**, **REQ DR-007**, **REQ INT-007**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 3 - Possible | Bulk migration of a large archive under a fixed window has a real error rate; schema transformation of association data is the specific hazard |
| **Impact** | 5 - Catastrophic | Irreversible loss of teaching material with no recovery path once the source is gone |
| **Inherent Risk Score** | **15** (High) | 3 × 5 = 15 |

**Risk Zone:** 🟧 High (13-19)

#### Current Controls and Mitigations

1. **Incumbent retained read-only until reconciliation is signed off (DR-007)** — the single most effective control in the register
   - Owner: Rhonda Bell · Effectiveness: **Strong** — converts data loss into a redirect reversal, because the source still exists
2. **Per-batch reconciliation with every difference explained**, not merely counted
   - Owner: Sam Okafor · Effectiveness: **Strong**
3. **Staged migration, oldest teaching periods first**, so errors surface on least-critical content
   - Owner: Rhonda Bell · Effectiveness: **Strong**
4. **Link-check sweep across unit sites post-migration**
   - Owner: Dr. Benny Moog · Effectiveness: **Adequate**
5. **Provenance retained on migrated recordings**, so origin remains evident after cutover
   - Owner: Sam Okafor · Effectiveness: **Adequate**

**Overall Control Effectiveness:** Strong (reduces 15 → 4) — the largest reduction in the register

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 1 - Rare | With the source retained until reconciliation is signed, permanent loss requires both a migration error *and* a reconciliation failure *and* premature decommissioning — three independent failures |
| **Impact** | 4 - Major | Reduced from Catastrophic because recovery is available while the source exists; still Major because discovery after decommissioning remains irreversible |
| **Residual Risk Score** | **4** (Low) | 1 × 4 = 4 |

**Risk Zone:** 🟩 Low (1-5) · **Risk Reduction:** 73% (15 → 4)

#### Risk Response (4Ts Framework)

**Primary Response:** TOLERATE

**Rationale:** Residual is Low and well within appetite. The controls are strong, specified, and cheap — the decisive one is simply not deleting the source until the target is verified. No further investment is warranted.

**Alternatives Considered:** **Treat** — further verification tooling considered and judged disproportionate given the retention-until-sign-off control already removes the irreversibility.

#### Risk Appetite Assessment

**Provisional appetite (TECHNOLOGY):** ≤ 12 · **Residual:** 4 · ✅ **Well within appetite**

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Reconciliation method and sign-off criteria defined | Sam Okafor | 2027-04-30 | Delivers the control |
| Staged migration plan, oldest periods first | Rhonda Bell | 2027-06-25 | Delivers the control |
| Decommissioning gated on written reconciliation sign-off | Cassandra Rhodes | 2027-12-11 | Preserves the recovery path |

**Target Residual:** 4 (no further reduction sought).

**Success Criteria:** Source count reconciles to target with every difference explained; zero unexplained losses; no decommissioning before sign-off.

**Monitoring:** Per batch during migration. Escalation trigger — any batch with an unexplained discrepancy, or any proposal to decommission before sign-off.

---

### Risk R-022: Selected platform supports only bulk-import provisioning

**Category:** TECHNOLOGY
**Status:** Open
**Risk Owner:** Sam Okafor, Integration Architect
**Action Owner:** Grace Tanaka (evaluation gate)

#### Risk Identification

**Risk Description:**
The selected platform's only provisioning path is bulk file import, so the manual CSV workaround survives the platform change — breaching REQ-025 and Principle 12 and carrying the casual-staff access failure into the new estate.

**Root Cause:**
Provisioning capability is easy to assert and hard to verify from documentation. A platform can present an API that does not in practice support event-driven role assignment at the granularity required.

**Trigger Events:**

- Provisioning capability scored rather than gated
- Capability accepted on vendor documentation without testing
- Role granularity insufficient for the coordinator/tutor/marker model
- Casual staff appointment events not consumable by the platform

**Consequences if Realized:**

- The project's most valuable platform-neutral outcome is lost
- REQ-025 and REQ-031 breached; the local-account exception potentially extended
- Casual academic staff continue to start teaching without access
- Nina Kalimba's dominant ticket category persists, undermining R-009's control

**Affected Stakeholders:** **Sam Okafor** (inherits it), **casual academic staff**, **Nina Kalimba's team**, **Tobias Ohm** (E8 and local accounts)

**Related Objectives:** **STKE G-4, O-2**, **REQ NFR-I-001**, **REQ INT-001**, **REQ FR-016**, **Principle 12**

#### Inherent Risk Assessment (Before Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 2 - Unlikely | Modern platforms in this market generally offer provisioning APIs; the risk is granularity and event support rather than complete absence |
| **Impact** | 4 - Major | Loses the highest-value platform-neutral outcome and perpetuates a known access failure for the contract term |
| **Inherent Risk Score** | **8** (Medium) | 2 × 4 = 8 |

**Risk Zone:** 🟨 Medium (6-12)

#### Current Controls and Mitigations

1. **Provisioning capability as a mandatory pass/fail gate (NFR-I-001)** — not a scored criterion
   - Owner: Grace Tanaka · Effectiveness: **Strong**
2. **Capability tested in evaluation, not accepted from documentation**
   - Owner: Sam Okafor · Effectiveness: **Strong**
3. **Bulk user file loads prohibited in production (Principle 12, TC-5)** — constrains selection, not just configuration
   - Owner: Sam Okafor · Effectiveness: **Strong**
4. **Role granularity requirements specified explicitly (FR-016)** — coordinator, tutor, marker, AV operator, admin

**Overall Control Effectiveness:** Strong (reduces 8 → 4)

#### Residual Risk Assessment (After Controls)

| Assessment | Rating | Justification |
|------------|--------|---------------|
| **Likelihood** | 1 - Rare | A tested mandatory gate makes selection of a non-compliant platform close to impossible |
| **Impact** | 4 - Major | Unchanged — if it happened, the consequence would run for the contract term |
| **Residual Risk Score** | **4** (Low) | 1 × 4 = 4 |

**Risk Zone:** 🟩 Low (1-5) · **Risk Reduction:** 50% (8 → 4)

#### Risk Response (4Ts Framework)

**Primary Response:** TOLERATE

**Rationale:** The mandatory gate resolves this at selection. Residual is Low and within appetite; no further action is proposed beyond enforcing the gate.

**Alternatives Considered:** **Treat** — no additional treatment available beyond the gate, which is already the strongest control possible for a selection-time risk.

#### Risk Appetite Assessment

**Provisional appetite (TECHNOLOGY):** ≤ 12 · **Residual:** 4 · ✅ **Well within appetite**

#### Action Plan

| Action | Owner | Due | Expected Impact |
|--------|-------|-----|-----------------|
| Provisioning capability confirmed as a mandatory gate in the criteria | Grace Tanaka | 2026-08-28 | Delivers the control |
| Provisioning tested against the role model during evaluation | Sam Okafor | 2026-09-09 | Verifies rather than assumes |

**Target Residual:** 4 (no further reduction sought).

**Success Criteria:** Zero manual provisioning events post-cutover; provisioning latency under 15 minutes verified in evaluation.

**Monitoring:** At evaluation, then via the provisioning audit log post-cutover. Escalation trigger — any platform reaching shortlist without demonstrated event-driven provisioning.

---

## D. Risk Category Analysis

### STRATEGIC Risks

**Total:** 5 · **Avg Inherent:** 12.2 · **Avg Residual:** 8.0 · **Control Effectiveness:** 34% reduction

- R-001: Decision contested, deadlocked or reopened — Residual 9 (Medium)
- R-003: Discipline exception endorsed but unfunded — Residual 9 (Medium)
- R-002: Consolidation degrades teaching capability — Residual 8 (Medium)
- R-004: Decision slips past October — Residual 8 (Medium)
- R-005: Education Committee returns the paper — Residual 6 (Medium)

**Key Themes:**

- Every strategic risk is a *decision risk* — none arises from external events. This is unusual and favourable: the university controls all five outcomes.
- Four of the five chain into one another. R-005 triggers R-004; R-001 triggers R-004; R-004 compresses everything downstream. The chain is the real exposure, not any individual link.
- Controls are procedural and cheap, which is why effectiveness is only 34% — procedure reduces likelihood well but rarely touches impact.

**Category Risk Profile:** ✅ Acceptable — all within the provisional ≤ 12 appetite, though R-001 and R-003 sit close to the line.

---

### OPERATIONAL Risks

**Total:** 5 · **Avg Inherent:** 12.2 · **Avg Residual:** 7.2 · **Control Effectiveness:** 41% reduction

- R-006: Baseline data not delivered — Residual 9 (Medium)
- R-008: AV capacity insufficient in the July window — Residual 9 (Medium)
- R-007: Room estate cannot support the platform — Residual 8 (Medium)
- R-010: Project 001 canonical model not delivered in time — Residual 6 (Medium)
- R-009: Support and training not ready — Residual 4 (Low)

**Key Themes:**

- Three of five concern *capacity and information held outside the project* — six data owners, an AV team, and a separate engagement. The project has responsibility without authority in each case.
- The July 2027 window is a shared constraint across R-007, R-008 and R-016; it is the single busiest point in the plan.
- R-006 and R-008 both sit exactly at the appetite limit of 9, with no headroom for deterioration.

**Category Risk Profile:** ⚠️ Concerning — nothing exceeds appetite, but two risks sit at the threshold and both depend on parties outside the project's control.

---

### FINANCIAL Risks

**Total:** 2 · **Avg Inherent:** 10.5 · **Avg Residual:** 7.5 · **Control Effectiveness:** 29% reduction

- R-011: Whole-of-life saving eliminated by appliance capital cost — Residual 9 (Medium)
- R-012: Renewal price step-change and lock-in economics — Residual 6 (Medium)

**Key Themes:**

- The weakest control effectiveness of any category (29%), for an honest reason: the controls improve *information* about cost rather than reducing cost. Making a capital requirement visible does not make it smaller.
- Both risks are currently unquantifiable — no contract values, no entitlement position, no appliance inventory. This category cannot be properly assessed until R-006 is resolved.

**Category Risk Profile:** ⚠️ Concerning — within appetite on current assessment, but the assessment itself rests on unsourced baselines. Re-score after 2026-08-28.

---

### COMPLIANCE Risks

**Total:** 5 · **Avg Inherent:** 12.8 · **Avg Residual:** 7.4 · **Control Effectiveness:** 42% reduction

- R-016: Essential Eight gaps persist — Residual 9 (Medium) ❌ **exceeds appetite**
- R-013: PIA incomplete at signature — Residual 8 (Medium) ❌ **exceeds appetite**
- R-017: Procurement probity breach — Residual 8 (Medium) ❌ **exceeds appetite**
- R-014: Retention schedule not approved — Residual 6 (Medium)
- R-015: Accessibility assessed on vendor claims — Residual 6 (Medium)

**Key Themes:**

- **Highest average inherent score in the register, and the only category with appetite breaches.** Three of five exceed the ≤ 6 threshold.
- Two of the three breaches (R-013, R-017) are driven by irreducible Impact ratings rather than by weak controls — the likelihood is already Unlikely in both. The third (R-016) is genuinely under-controlled.
- Two risks are pre-existing conditions this project inherits rather than creates: R-016's security debt and R-014's absent retention schedule. Both have survived previous opportunities to close them.
- R-014 and R-015 sit exactly at appetite, and R-015's position is conditional on a dependency currently marked At Risk.

**Category Risk Profile:** ❌ **Unacceptable without escalation** — three appetite breaches require Operations Committee decision, either to fund down or to accept explicitly.

---

### REPUTATIONAL Risks

**Total:** 2 · **Avg Inherent:** 12.0 · **Avg Residual:** 6.0 · **Control Effectiveness:** 50% reduction

- R-018: Privacy incident involving student recordings — Residual 8 (Medium) ❌ **exceeds appetite**
- R-019: Capture policy backlash — Residual 4 (Low)

**Key Themes:**

- Strong control effectiveness, but the residual concentrates in a single risk whose impact cannot be reduced below Major while the university records students at all.
- R-018 is the only Impact 5 inherent rating in the register. It is also the risk most dependent on other risks: R-016 (estate compromise) and R-021 (migration error) are both plausible routes to it.

**Category Risk Profile:** ⚠️ Concerning — one breach, driven by inherent exposure rather than control weakness.

---

### TECHNOLOGY Risks

**Total:** 3 · **Avg Inherent:** 11.7 · **Avg Residual:** 5.3 · **Control Effectiveness:** 54% reduction

- R-020: Archive stranded by incumbent export terms — Residual 8 (Medium)
- R-021: Migration data loss or reconciliation failure — Residual 4 (Low)
- R-022: Platform supports only bulk-import provisioning — Residual 4 (Low)

**Key Themes:**

- **Best control effectiveness in the register (54%)**, for a structural reason: these risks have *mandatory gates and verification steps* rather than process commitments. R-021's control — retain the source until reconciliation is signed — is the single most effective control documented here.
- The residual concentrates in R-020, the one technology risk the university cannot control, because it sits in someone else's contract.

**Category Risk Profile:** ✅ Acceptable — well within appetite, strong controls, and the only outstanding item is information-dependent (D-1, due 2026-08-14).

---

## E. Risk Ownership Matrix

| Stakeholder | Role | Owned Risks | High | Medium | Low | Total Residual | Concentration |
|-------------|------|-------------|------|--------|-----|----------------|---------------|
| Cassandra Rhodes | CIO | R-007, R-008, R-010 | 0 | 3 | 0 | 23 | Moderate — all operational, appropriate to role |
| Prof. Otis Hammond | DVC (Education), Sponsor | R-001, R-004, R-005 | 0 | 3 | 0 | 23 | Moderate — all governance/timeline, appropriate |
| Eleanor Frame | Privacy & Records Officer | R-013, R-014, R-018 | 0 | 3 | 0 | 22 | ⚠️ **Two of three exceed appetite** |
| A/Prof. Pearl Clavinet | Dean L&T, Chair EC | R-002, R-003, R-019 | 0 | 2 | 1 | 21 | Moderate — academic and policy |
| Grace Tanaka | Procurement | R-017, R-020 | 0 | 2 | 0 | 16 | Focused — one exceeds appetite |
| Vernon Ostinato | CFO | R-011, R-012 | 0 | 2 | 0 | 15 | Focused — financial, appropriate |
| Rhonda Bell | Project Manager | R-006, R-021 | 0 | 1 | 1 | 13 | Low |
| Dr. Benny Moog | Director Learning Tech | R-009, R-015 | 0 | 1 | 1 | 10 | Low |
| Tobias Ohm | Cybersecurity Lead | R-016 | 0 | 1 | 0 | 9 | ⚠️ **Single risk, largest appetite breach** |
| Sam Okafor | Integration Architect | R-022 | 0 | 0 | 1 | 4 | Low |
| **TOTAL** | | **22 risks** | **0** | **18** | **4** | **156** | |

**Risk Concentration Analysis:**

- **No individual owns more than three risks or more than 15% of total residual exposure.** Distribution is proportionate rather than concentrated — a healthier position than most registers of this size.
- ⚠️ **Eleanor Frame's portfolio is the concern, not by volume but by composition.** Two of her three risks (R-013, R-018) exceed appetite, and both are driven by irreducible impact. She holds the highest-consequence risks with the least ability to reduce them, and her leverage on R-013 expires at contract signature.
- ⚠️ **Tobias Ohm owns a single risk that is the largest appetite breach in the register.** R-016 needs funding rather than management attention; concentrating it on one owner without a budget makes it structurally unlikely to close.
- **Rhodes and Hammond each carry 23 points but in well-defined lanes** — Rhodes operational and estate, Hammond governance and timeline. Neither is over-extended.
- **Sam Okafor owns only R-022 as risk owner** but is action owner on four others. Ownership volume understates his load.

**Escalation Paths:**

- Strategic and timeline risks → Prof. Otis Hammond → Steering Committee → Operations Committee
- Operational and estate risks → Cassandra Rhodes → Steering Committee
- Compliance risks → Eleanor Frame / Tobias Ohm → CIO → Operations Committee
- Procurement probity → Grace Tanaka → Executive Sponsor
- Reputational risks → Eleanor Frame → CIO → University Executive (Prof. Stella Groove)

---

## F. 4Ts Response Framework Summary

| Response | Count | % | Total Residual Score | Key Examples |
|----------|-------|---|---------------------|--------------|
| **TOLERATE** | 4 | 18% | 16 | R-009, R-019, R-021, R-022 — all Low residual, controls committed, no further action proposed |
| **TREAT** | 17 | 77% | 134 | R-001, R-006, R-013, R-016, R-018 and 12 others — active mitigation with named actions and dates |
| **TRANSFER** | 1 | 5% | 6 | R-012 — renewal price protection shifts repricing exposure to the supplier |
| **TERMINATE** | 0 | 0% | 0 | None — see note below |
| **TOTAL** | 22 | 100% | 156 | |

**Response Breakdown by Category:**

| Category | Tolerate | Treat | Transfer | Terminate | Predominant |
|----------|----------|-------|----------|-----------|-------------|
| STRATEGIC | 0 | 5 | 0 | 0 | Treat (100%) |
| OPERATIONAL | 1 | 4 | 0 | 0 | Treat (80%) |
| FINANCIAL | 0 | 1 | 1 | 0 | Mixed |
| COMPLIANCE | 0 | 5 | 0 | 0 | Treat (100%) |
| REPUTATIONAL | 1 | 1 | 0 | 0 | Mixed |
| TECHNOLOGY | 2 | 1 | 0 | 0 | Tolerate (67%) |

**Key Insights:**

- **77% treatment is high, and the reason is favourable rather than alarming.** Most of these risks are decisions not yet made rather than events outside the university's control, and decisions respond well to treatment. A register dominated by external events would show more tolerance and transfer.
- **Only one genuine transfer opportunity exists.** Most of this project's risk is internal — governance, capacity, sequencing — and internal risk cannot be contracted away. Where the register could have claimed transfer (R-018 via vendor liability clauses), it has not, because the university remains the APP entity and cannot transfer its own statutory obligations or its reputation.
- **Tolerance is concentrated in TECHNOLOGY, where controls are strongest.** Two of the four tolerated risks (R-021, R-022) reach Low residual through mandatory gates and verification, which is the pattern worth replicating elsewhere.
- **Zero terminations, stated deliberately.** No risk in this register warrants stopping the activity that creates it. One *option-level* termination remains live and must not be lost: the RIFF pause provision permits closing the request entirely if evaluation shows no option delivers value [SGP-C2]. That is recorded under R-002 and belongs in the options set, not in this table.
- **Two tolerances are conditional.** R-009 and R-019 are tolerated on the assumption their committed controls are delivered. If documentation or the capture policy slip, both return to TREAT.

---

## G. Risk Appetite Compliance

**Provisional thresholds** (derived from principle criticality; not yet ratified — see Executive Summary):

| Category | Appetite | Threshold | Risks Within | Risks Exceeding | Action Required |
|----------|----------|-----------|--------------|-----------------|-----------------|
| STRATEGIC | Medium | ≤ 12 | 5 (100%) | 0 | ✅ Compliant |
| OPERATIONAL | Medium | ≤ 9 | 5 (100%) | 0 | ✅ Compliant — but R-006 and R-008 sit at the limit |
| FINANCIAL | Medium | ≤ 9 | 2 (100%) | 0 | ✅ Compliant — assessment rests on unsourced baselines |
| COMPLIANCE | Low | ≤ 6 | 2 (40%) | 3 (60%) | ❌ Operations Committee decision required |
| REPUTATIONAL | Low | ≤ 6 | 1 (50%) | 1 (50%) | ⚠️ Operations Committee acknowledgement required |
| TECHNOLOGY | Medium | ≤ 12 | 3 (100%) | 0 | ✅ Compliant |

**Overall Appetite Compliance:** 18 of 22 risks (82%) within provisional appetite; 2 of 6 categories contain breaches.

**Risks Exceeding Appetite — Detail:**

| Risk ID | Category | Appetite | Residual | Excess | % Over | Nature of Breach | Escalation |
|---------|----------|----------|----------|--------|--------|------------------|------------|
| R-016 | COMPLIANCE | 6 | 9 | +3 | 50% | **Under-controlled** — remediation scoped but unfunded, deferred before | Operations Committee: fund or explicitly accept |
| R-013 | COMPLIANCE | 6 | 8 | +2 | 33% | **Irreducible impact** — likelihood already Unlikely | Operations Committee: acknowledge |
| R-017 | COMPLIANCE | 6 | 8 | +2 | 33% | **Irreducible impact** — any material breach voids the process | Executive Sponsor: note residual |
| R-018 | REPUTATIONAL | 6 | 8 | +2 | 33% | **Irreducible impact** — inherent to holding recordings of students | Operations Committee: acknowledge |

**The distinction matters more than the count.** Three of the four breaches (R-013, R-017, R-018) exceed appetite because their *impact* cannot be reduced — the likelihood in each is already Unlikely and the controls are strong. These require acknowledgement, not more work.

R-016 is different. Its likelihood is Possible, its controls are the weakest in the register, and its 25% reduction is the poorest control performance documented. It exceeds appetite because the work has not been funded, not because the risk is inherent. It is the only breach where spending money would close the gap.

**Recommendations:**

1. **R-016 — fund it or accept it explicitly.** A third deferral by omission would be the worst available outcome: the exposure persists and nobody has decided to accept it. Operations Committee, 2026-10-09.
2. **R-013, R-017, R-018 — seek formal acknowledgement, not further mitigation.** Each has been treated as far as it can be. Presenting them as open actions would misrepresent them as solvable.
3. **Ratify the appetite thresholds first.** Every judgement in this section is provisional until the Operations Committee sets the thresholds. Four breaches against unratified numbers is an architect's opinion, not a governance finding.
4. **Watch the at-limit risks.** R-006, R-008, R-011, R-014 and R-015 all sit exactly at their thresholds with no headroom. Any deterioration breaches, and R-015's position depends on a dependency currently marked At Risk.

---

## H. Prioritized Action Plan

Priority reflects urgency and appetite breach rather than residual score. Costs are stated as effort and ownership rather than currency amounts — the project has no sourced cost baseline (R-006), and inventing figures here would contradict the ⚠️ convention used throughout ARC-002-STKE and ARC-002-REQ.

### Priority 1: URGENT — due within 4 weeks

| # | Action | Risk(s) | Owner | Due | Cost | Expected Impact | Status |
|---|--------|---------|-------|-----|------|-----------------|--------|
| 1 | Written confirmation from all six baseline owners that data exists and can be delivered | R-006 | Rhonda Bell | 2026-08-07 | Project effort | Converts assumption to commitment; gates 5 other risks | Not Started |
| 2 | Contract values, terms, renewal dates delivered | R-006, R-011, R-020 | Grace Tanaka | 2026-08-14 | Business-as-usual | Unblocks financial assessment; tests assumption A-10 | Not Started |
| 3 | Microsoft entitlement position delivered | R-006, R-011 | Cassandra Rhodes | 2026-08-14 | Business-as-usual | Makes the consolidation argument testable | Not Started |
| 4 | Written probity instruction to both principals and all three suppliers | R-017 | Grace Tanaka | 2026-08-14 | Minimal | Likelihood 3 → 2 on the largest procurement exposure | Not Started |
| 5 | Appliance inventory: models, age, patch status, shared accounts, telemetry | R-006, R-007, R-008, R-016 | Marcus Fairlight | 2026-08-21 | AV team effort | Quantifies the estate constraint across four risks | Not Started |
| 6 | Capture coverage telemetry and support ticket baselines delivered | R-006, R-009 | Dr. Benny Moog, Nina Kalimba | 2026-08-21 | Business-as-usual | Establishes G-3 and G-8 measurement baselines | Not Started |
| 7 | Independently facilitated weighting workshop, two-session cap | R-001, R-005 | Rhonda Bell | 2026-08-21 | Project effort | Likelihood 4 → 3 on the highest-likelihood risk | Not Started |

### Priority 2: HIGH — due before the decision gate

| # | Action | Risk(s) | Owner | Due | Cost | Expected Impact | Status |
|---|--------|---------|-------|-----|------|-----------------|--------|
| 8 | Archive volume and retention position delivered | R-006, R-014, R-021 | Eleanor Frame | 2026-08-28 | Business-as-usual | Enables retention scoping and migration sizing | Not Started |
| 9 | Evaluation criteria signed by Rhodes, Moog and Tanaka | R-001, R-002 | Grace Tanaka | 2026-08-28 | Project effort | The primary control for the register's top strategic risk | Not Started |
| 10 | Mandatory gates confirmed: SSO/MFA, accessibility, export, provisioning | R-013, R-015, R-020, R-022 | Grace Tanaka | 2026-08-28 | Included above | Four risks controlled by a single mechanism | Not Started |
| 11 | Residency and APP 8 requirements written into criteria | R-013 | Grace Tanaka | 2026-08-28 | Included above | Likelihood 4 → 3 before negotiation begins | Not Started |
| 12 | Discipline-vocabulary caption test set built | R-015 | Dr. Benny Moog | 2026-09-04 | Two faculties' effort | Without this the R-015 control fails and it breaches appetite | Not Started |
| 13 | Written value-for-money rationale for the competitive tender route recorded in the decision file | R-017, R-004 | Grace Tanaka | 2026-08-28 | Project effort | Route settled; recording the rationale removes the strongest available challenge to the outcome | Not Started |
| 14 | Practical export test on a sample archive | R-020, R-021 | Dr. Benny Moog | 2026-09-09 | Project effort | Verifies rather than assumes the migration is possible | Not Started |
| 15 | Whole-of-life cost model for every shortlisted option | R-011, R-007 | Rhonda Bell | 2026-09-09 | Project effort | Prevents late capital discovery | Not Started |
| 16 | Clavinet and Deans pre-briefed on the draft recommendation | R-005, R-003 | Rhonda Bell | 2026-09-14 | Minimal | Removes the main cause of a returned paper | Not Started |
| 17 | E8 remediation costed as a named business case line | R-016 | Vernon Ostinato | 2026-09-25 | Project effort | The only action that closes the register's largest breach | Not Started |
| 18 | Discipline exception costed and included in the decision paper | R-003 | Vernon Ostinato | 2026-09-25 | Project effort | Prevents silent defunding | Not Started |

### Priority 3: MEDIUM — post-decision, pre-signature

| # | Action | Risk(s) | Owner | Due | Cost | Expected Impact | Status |
|---|--------|---------|-------|-----|------|-----------------|--------|
| 19 | Appetite thresholds ratified by Operations Committee | All | Vernon Ostinato | 2026-10-09 | Minimal | Makes every appetite judgement in this register authoritative | Not Started |
| 20 | Four appetite breaches escalated with fund-or-accept decisions | R-013, R-016, R-017, R-018 | Rhonda Bell | 2026-10-09 | Minimal | Converts drift into decision | Not Started |
| 21 | PIA initiated at preferred-option stage | R-013 | Eleanor Frame | 2026-10-16 | Privacy effort | Likelihood 3 → 2 while leverage still exists | Not Started |
| 22 | Cross-border disclosure register created | R-013 | Eleanor Frame | 2026-11-27 | Privacy effort | Makes the residency position durable | Not Started |
| 23 | Retention schedule drafted | R-014 | Eleanor Frame | 2026-11-27 | Privacy effort | Likelihood 4 → 3 | Not Started |
| 24 | AV capacity plan for the July 2027 window, including contract resource | R-008, R-016 | Marcus Fairlight | 2026-11-27 | AV effort | Likelihood 3 → 2 on a shared constraint | Not Started |
| 25 | Contract terms: residency, export, 24-hour breach notification, price protection | R-012, R-013, R-018, R-020 | Grace Tanaka | 2026-12-11 | Legal effort | One clause set serving four risks | Not Started |
| 26 | PIA signed off — hard gate before contract execution | R-013 | Eleanor Frame | 2026-12-04 | Privacy effort | Prevents the risk entirely | Not Started |

### Priority 4: SCHEDULED — transition period

| # | Action | Risk(s) | Owner | Due | Expected Impact |
|---|--------|---------|-------|-----|-----------------|
| 27 | Reconciliation method and sign-off criteria defined | R-021 | Sam Okafor | 2027-04-30 | Preserves the recovery path |
| 28 | Retention schedule approved by Education Committee | R-014 | A/Prof. Pearl Clavinet | 2027-04-30 | Likelihood 3 → 2 |
| 29 | Capture policy approved before cutover | R-019 | A/Prof. Pearl Clavinet | 2027-04-30 | Delivers the tolerated position |
| 30 | NDB response playbook for the recordings scenario | R-018 | Eleanor Frame | 2027-02-26 | Impact 4 → 3 |
| 31 | Runbooks, documentation and training delivered | R-009 | Nina Kalimba | 2027-07-24 | Delivers the tolerated position |
| 32 | Shared administrative accounts removed during room visits | R-016, R-018 | Marcus Fairlight | 2027-07-24 | Likelihood 3 → 2 |
| 33 | Retained appliances brought into the managed patching regime | R-016 | Marcus Fairlight | 2027-12-11 | Impact 3 → 2 |
| 34 | E8 self-assessment refreshed to evidence ML2 for this estate | R-016 | Tobias Ohm | 2027-12-11 | Confirms closure |

**Action Plan Summary:**

- **Total actions:** 34 across four priority bands
- **Urgent actions due within 4 weeks:** 7, of which 5 are baseline-data deliverables
- **Actions closing an appetite breach:** 5 (items 4, 12, 17, 20, 21)
- **Highest-leverage single action:** item 5, the appliance inventory — it feeds four separate risks and gates the cost model
- **Expected aggregate reduction:** residual 156 → approximately 108 (31%) if all target residuals are achieved
- **Target completion:** 2027-12-11

---

## I. Integration with SOBC

**How this register feeds the Strategic Outline Business Case:**

### SOBC Strategic Case

- **"Why now?"** rests on R-016 and R-014 — two pre-existing compliance gaps (security debt on the capture estate, no retention schedule for recordings) that this project is the practical opportunity to close. Both have survived earlier opportunities; the strategic argument is that a platform transition touches every room and every recording exactly once.
- R-002 defines the boundary of the strategic ambition: consolidation must not be pursued at the cost of teaching capability.

### SOBC Economic Case

- **Risk-adjusted costing** must incorporate R-011 (appliance capital), R-007 (room compatibility) and R-020 (export cost). Each is currently unquantified pending R-006.
- **Contingency cannot yet be calculated.** With no sourced cost baseline, applying a percentage contingency would compound an invented figure. The Economic Case should be built after 2026-08-28, not before.
- R-012 requires the Economic Case to run five years and span at least one renewal, or the lock-in exposure is invisible.

### SOBC Commercial Case

- R-017 (probity) and R-020 (incumbent export terms) are commercial risks carried by the competitive tender route now settled; R-017's controls apply from the date criteria drafting began.
- R-012's price protection requirement is a commercial term, not a technical one.

### SOBC Financial Case

- R-016's remediation cost must appear as a named line (action 17). If it is absent from the Financial Case, the appetite breach persists by default.
- R-003's discipline exception must likewise appear as a named line (action 18).

### SOBC Management Case (Part E — Risk Management)

- This register in full, with the ownership matrix (Section E) evidencing accountability and the monitoring framework (Section J) evidencing ongoing capability.
- The four appetite breaches and their fund-or-accept decisions are the material content for Part E.

### Influence on the Recommendation

- No risk in this register argues against proceeding. The profile is Concerning rather than Unacceptable, with no Critical risks and no High residual risks.
- **But two findings should shape option selection**: options requiring extensive appliance replacement carry compounding exposure across R-007, R-008, R-011 and R-016; and any option whose export capability cannot be practically demonstrated should be treated as failing NFR-I-002 rather than as carrying a manageable risk.

---

## J. Monitoring and Review Framework

### Review Schedule

| Risk Level | Frequency | Reviewed By | Escalated To | Format |
|------------|-----------|-------------|--------------|--------|
| **Critical (20-25)** | Weekly | Risk Owner + PM | Steering Committee | Dashboard + narrative |
| **High (13-19)** | Fortnightly | Risk Owner | Steering Committee | Dashboard |
| **Medium (6-12)** | Monthly | Risk Owner | Project Manager | Exception report |
| **Low (1-5)** | Quarterly | Action Owner | Risk Owner | Status update |
| **Appetite breaches** | Fortnightly regardless of level | Risk Owner | Operations Committee | Narrative with fund-or-accept status |

The register currently contains no Critical or High residual risks, so the operative cadences are monthly for the 18 Medium risks, quarterly for the 4 Low risks, and fortnightly for the 4 appetite breaches.

**Elevated cadence during August 2026**: weekly review of R-006 and its six dependent deliverables until all baselines land. This is the period in which the register is least reliable and most changeable.

### Key Risk Indicators

**Leading indicators** (predict deterioration):

- Baseline deliverables not confirmed by their owners → R-006 and five dependent assessments
- Criteria unsigned within 10 working days of the target date → R-001, R-002
- Vendor contact appearing outside the log → R-017
- Appliance inventory showing more than 20% of rooms incompatible → R-007, R-008, R-011, R-016
- Caption test set not built by 2026-09-04 → R-015 returns to breach
- Project 001 WP5 slipping → R-010
- E8 remediation absent from a business case draft → R-016 breach persists

**Lagging indicators** (confirm materialisation):

- Governance gate missed → R-004 realised
- Education Committee returns the paper → R-005 realised
- Any recording published against the wrong unit → R-018 realised
- Any batch reconciliation discrepancy unexplained → R-021 realised
- Manual provisioning event post-cutover → R-022 realised
- Room not ready at the start of Semester 2 2027 → R-008 realised

### Escalation Criteria

Automatic escalation to Steering Committee when:

1. Any risk score increases by 3 or more points
2. Any risk reaches High (13+) residual
3. Any new risk is identified at Medium or above
4. Any appetite breach remains without a fund-or-accept decision after 2026-10-09
5. Any Priority 1 action slips by more than 5 working days
6. Any of the six baseline deliverables misses its date
7. Any proposal to cut over during a teaching period, or to decommission the incumbent before reconciliation sign-off — both are prohibited, and a proposal to do either is itself an escalation event

### Reporting Requirements

- **Weekly (August 2026 only)**: R-006 baseline tracker to the Steering Committee
- **Fortnightly**: appetite breaches (R-013, R-016, R-017, R-018) with decision status
- **Monthly**: full register to the Steering Committee, with matrix and action plan status
- **At each governance gate**: register summary in the RIFF, Education Committee and Operations Committee papers
- **Annually post-implementation**: register review with Education Committee, including capture policy exception rates (R-019) and E8 status (R-016)

### Risk Register Maintenance

**Risk Register Owner:** Rhonda Bell, Project Manager

**Update process:** Risk owners submit updates monthly (fortnightly for appetite breaches); the register owner validates and updates; material changes go to the Steering Committee for approval; version increments with each update and the change is logged in Revision History.

**Mandatory re-scoring points:**

1. **After 2026-08-28**, when baselines land — R-007, R-011, R-014, R-016, R-020 and R-021 are all currently assessed against unsourced data
2. **After contract signature**, when designed controls become verifiable rather than forecast
3. **After the Semester 1 2027 pilot**, when operational assumptions are tested against live teaching

**Assessment integrity caveat**: residual scores in v1.0 assume that controls specified in ARC-002-REQ are implemented as written. Most are not yet in place. Until they are, every residual score is a forecast.

---

## K. Orange Book Compliance Checklist

### Part I — Risk Management Principles

- ✅ **A. Governance and Leadership** — every risk has a named owner drawn from the stakeholder RACI; escalation paths run to Steering, Operations Committee and University Executive; appetite is defined, though provisionally.
- ✅ **B. Integration** — every risk traces to stakeholder goals (G-1 to G-10) and requirement IDs; Section I maps the register into the business case; risk review is embedded in the governance gates.
- ✅ **C. Collaboration and Best Information** — risks are sourced from the stakeholder conflict analysis, the requirements dependencies, the privacy context and the Essential Eight self-assessment. **Qualified**: six baseline datasets are outstanding, and the register states explicitly where assessments rest on unsourced data rather than presenting them as evidenced.
- ✅ **D. Risk Management Processes** — systematic identification across all six categories; consistent 5×5 methodology; inherent and residual tracked separately; 4Ts applied with alternatives considered and rejection reasons recorded.
- ✅ **E. Continual Improvement** — review schedule defined by risk level; leading and lagging KRIs specified; three mandatory re-scoring points identified; version control through Revision History.

### Part II — Risk Control Framework

- ✅ **Risk appetite and tolerance defined** — provisionally, pending Operations Committee ratification. Flagged rather than presented as settled.
- ✅ **Risk ownership and governance established** — ownership matrix with concentration analysis in Section E.
- ✅ **Risk assessment methodology documented** — scales in Appendix A, applied consistently and with justification recorded per rating.
- ✅ **Control effectiveness measured** — inherent versus residual per risk, aggregated by category, with the weakest performer (R-016, 25%) explicitly identified rather than averaged away.

**Honest qualification**: this register satisfies the Orange Book's structural requirements. It does not yet satisfy its evidential ones — six datasets are outstanding, appetite is unratified, and most controls are specified rather than implemented. Compliance with the framework is not the same as confidence in the numbers.

---

## Appendix A: Risk Assessment Scales

### Likelihood Scale

| Score | Rating | Probability | Description |
|-------|--------|-------------|-------------|
| 1 | Rare | < 5% | Highly unlikely; requires multiple independent failures |
| 2 | Unlikely | 5-25% | Could happen but probably will not |
| 3 | Possible | 25-50% | Reasonable chance; has happened in comparable contexts |
| 4 | Likely | 50-75% | More likely than not without further action |
| 5 | Almost Certain | > 75% | Expected to occur |

### Impact Scale

Financial bands are expressed in Australian dollars and are **provisional**, calibrated to a mid-sized university platform procurement pending ratification alongside the appetite thresholds. The project has no sourced cost baseline (R-006), so financial impact ratings in this register are relative judgements rather than measured variances.

| Score | Rating | Financial (provisional) | Schedule | Teaching / Stakeholder | Description |
|-------|--------|------------------------|----------|------------------------|-------------|
| 1 | Negligible | < A$25K | < 1 week | No teaching effect | Absorbed in routine management |
| 2 | Minor | A$25K–100K | 1-4 weeks | Isolated inconvenience | Manageable within contingency |
| 3 | Moderate | A$100K–400K | 1-2 months | One school or one teaching period affected | Requires management effort and approval |
| 4 | Major | A$400K–1.5M | 2-6 months | Multiple schools, or a full year's teaching affected | Threatens objectives; difficult recovery |
| 5 | Catastrophic | > A$1.5M | > 6 months | Institution-wide, or statutory/regulatory consequence | Project failure or external notification |

### Risk Score Matrix

| Range | Level | Indicator | Action |
|-------|-------|-----------|--------|
| 20-25 | Critical | 🟥 | Immediate escalation; senior management action |
| 13-19 | High | 🟧 | Management attention; mitigation plan required |
| 6-12 | Medium | 🟨 | Management monitoring; mitigation considered |
| 1-5 | Low | 🟩 | Routine monitoring; accept or low-cost controls |

---

## Appendix B: Stakeholder-Risk Linkage

**Traceability from stakeholder drivers to risks:**

| Stakeholder | Driver (ARC-002-STKE) | Risk ID | Risk Title | Category | Residual |
|-------------|----------------------|---------|------------|----------|----------|
| Cassandra Rhodes (CIO) | SD-1: Consolidate onto licensed capability | R-001 | Decision contested or reopened | STRATEGIC | 9 |
| Cassandra Rhodes | SD-1 | R-011 | Whole-of-life saving eliminated | FINANCIAL | 9 |
| Grace Tanaka (Procurement) | SD-2: A defensible process | R-017 | Procurement probity breached | COMPLIANCE | 8 |
| Grace Tanaka | SD-2 | R-020 | Archive stranded by export terms | TECHNOLOGY | 8 |
| Vernon Ostinato (CFO) | SD-3: No surprise capital | R-011 | Whole-of-life saving eliminated | FINANCIAL | 9 |
| Vernon Ostinato | SD-3 | R-012 | Renewal price step-change | FINANCIAL | 6 |
| Prof. Otis Hammond (DVC) | SD-4: A decision that does not return | R-001 | Decision contested or reopened | STRATEGIC | 9 |
| Prof. Otis Hammond | SD-4 | R-004 | Decision slips past October | STRATEGIC | 8 |
| A/Prof. Pearl Clavinet (Dean L&T) | SD-5: Pedagogy must lead | R-005 | Education Committee returns the paper | STRATEGIC | 6 |
| A/Prof. Pearl Clavinet | SD-5 | R-002 | Consolidation degrades teaching capability | STRATEGIC | 8 |
| Dr. Benny Moog (Learning Tech) | SD-6: Do not trade capability for tidiness | R-002 | Consolidation degrades teaching capability | STRATEGIC | 8 |
| Dr. Benny Moog | SD-6 | R-015 | Accessibility assessed on vendor claims | COMPLIANCE | 6 |
| Marcus Fairlight (AV) | SD-7: Solve the estate, not just the software | R-007 | Room estate cannot support the platform | OPERATIONAL | 8 |
| Marcus Fairlight | SD-7 | R-008 | AV capacity insufficient in July | OPERATIONAL | 9 |
| Marcus Fairlight | SD-7 | R-016 | Essential Eight gaps persist | COMPLIANCE | 9 |
| Sam Okafor (Integration) | SD-8: End manual provisioning | R-022 | Bulk-import-only provisioning | TECHNOLOGY | 4 |
| Sam Okafor | SD-8 | R-010 | Project 001 canonical model delayed | OPERATIONAL | 6 |
| Prof. Desmond Key (Music) | SD-9: Performance capture is not lecture capture | R-003 | Discipline exception unfunded | STRATEGIC | 9 |
| Tobias Ohm (Security) | SD-10: Close the capture estate's security debt | R-016 | Essential Eight gaps persist | COMPLIANCE | 9 |
| Tobias Ohm | SD-10 | R-018 | Privacy incident involving recordings | REPUTATIONAL | 8 |
| Eleanor Frame (Privacy) | SD-11: Recordings are personal information | R-013 | PIA incomplete at signature | COMPLIANCE | 8 |
| Eleanor Frame | SD-11 | R-014 | Retention schedule not approved | COMPLIANCE | 6 |
| Eleanor Frame | SD-11 | R-018 | Privacy incident involving recordings | REPUTATIONAL | 8 |
| Dr. Wynton Castle (Academic) | SD-12: Do not make my teaching harder | R-009 | Support and training not ready | OPERATIONAL | 4 |
| Dr. Wynton Castle | SD-12 | R-019 | Capture policy backlash | REPUTATIONAL | 4 |
| Prof. Priya Anand (Health Sci) | SD-13: Large cohorts depend on this | R-008 | AV capacity insufficient in July | OPERATIONAL | 9 |
| Jazmin Field (Student Guild) | SD-14: Access, captions, and being asked | R-015 | Accessibility on vendor claims | COMPLIANCE | 6 |
| Jazmin Field | SD-14 | R-019 | Capture policy backlash | REPUTATIONAL | 4 |
| Nina Kalimba (Support) | SD-15: The support load lands on my team | R-009 | Support and training not ready | OPERATIONAL | 4 |
| Rhonda Bell (PM) | Delivery | R-006 | Baseline data not delivered | OPERATIONAL | 9 |
| Rhonda Bell | Delivery | R-021 | Migration data loss | TECHNOLOGY | 4 |

**Stakeholder conflicts mapped to risks:**

| Conflict (ARC-002-STKE) | Risk(s) Created | Mitigation |
|-------------------------|-----------------|------------|
| C-1: Consolidation vs purpose-built capture depth | R-001, R-002 | Signed weighted criteria before vendor engagement; mandatory gates |
| C-2: Licence saving vs appliance estate reality | R-007, R-011, R-016 | Whole-of-life costing with refresh cost split |
| C-3: Universal publication vs academic discretion | R-019 | Publish-by-default with approved, recorded exceptions |
| C-4: Retention and disposal vs keeping everything | R-014 | Schedule applied at migration with archive-on-request |
| C-5: Procurement speed vs contestability | R-017, R-004 | Competitive tender route settled, with the written value-for-money justification on record |
| C-6: Discipline capability vs institutional prioritisation | R-003 | Exception costed and decided in the same governance paper |

---

## Appendix C: Prior Risk ID Reconciliation

**This register supersedes two earlier provisional risk lists**, both of which used the identifiers `R-1` … `R-8` for *different* sets of risks. That collision is resolved here.

| Prior ID | Source Artifact | Prior Title | Successor ID | Notes |
|----------|-----------------|-------------|--------------|-------|
| R-1 | ARC-002-STKE §10 | Criteria negotiation becomes the proxy battleground | **R-001** | Merged with REQ R-1 |
| R-2 | ARC-002-STKE §10 | Informal vendor contact compromises the process | **R-017** | Recategorised as COMPLIANCE |
| R-3 | ARC-002-STKE §10 | Education Committee returns the paper | **R-005** | Unchanged in substance |
| R-4 | ARC-002-STKE §10 | Room estate cannot support the selected platform | **R-007** | Merged with REQ R-4 |
| R-5 | ARC-002-STKE §10 | Archive export from the incumbent restrictive or costly | **R-020** | Merged with REQ R-3 |
| R-6 | ARC-002-STKE §10 | Decision slips past October | **R-004** | Merged with REQ R-5 |
| R-7 | ARC-002-STKE §10 | Discipline exception approved but unfunded | **R-003** | Merged with REQ R-6 |
| R-1 | ARC-002-REQ §11 | Evaluation criteria negotiation deadlocks | **R-001** | Duplicate of STKE R-1 |
| R-2 | ARC-002-REQ §11 | Baseline data not delivered | **R-006** | New in REQ; not in STKE |
| R-3 | ARC-002-REQ §11 | Incumbent export terms restrictive | **R-020** | Duplicate of STKE R-5 |
| R-4 | ARC-002-REQ §11 | Appliance estate incompatible | **R-007** | Duplicate of STKE R-4 |
| R-5 | ARC-002-REQ §11 | Decision slips past October | **R-004** | Duplicate of STKE R-6 |
| R-6 | ARC-002-REQ §11 | Discipline exception unfunded | **R-003** | Duplicate of STKE R-7 |
| R-7 | ARC-002-REQ §11 | Bulk-import-only provisioning | **R-022** | New in REQ; not in STKE |
| R-8 | ARC-002-REQ §11 | Caption accuracy on vendor claims | **R-015** | New in REQ; not in STKE |

**Risks identified for the first time in this register** (present in neither prior list): R-002 (consolidation degrades teaching capability), R-008 (AV capacity), R-009 (support readiness), R-010 (project 001 dependency), R-011 (whole-of-life saving eliminated), R-012 (renewal price step-change), R-013 (PIA incomplete at signature), R-014 (retention schedule not approved), R-016 (Essential Eight gaps persist), R-018 (privacy incident), R-019 (capture policy backlash), R-021 (migration data loss). Twelve of 22.

**Action required**: ARC-002-STKE §10 and ARC-002-REQ §11 should carry a forward reference to this register at their next revision, so the superseded IDs are not cited in later artifacts. Tracked as a documentation action for the register owner.

---

## Document Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| **Risk Register Owner** | Rhonda Bell, Project Manager | | |
| **Senior Responsible Owner** | Prof. Otis Hammond, DVC (Education) | | |
| **Technology Risk Owner** | Cassandra Rhodes, CIO | | |
| **Compliance Risk Owner** | Eleanor Frame, Privacy & Records Officer | | |
| **Steering Committee Chair** | Prof. Otis Hammond | | |

---

## Next Steps

1. **Immediate (this week)**:
   - [ ] Confirm the six baseline deliverables with their owners (Priority 1, action 1)
   - [ ] Issue the probity instruction to principals and suppliers (Priority 1, action 4)
   - [ ] Schedule the facilitated weighting workshop (Priority 1, action 7)
   - [ ] Brief Tobias Ohm and Eleanor Frame on their appetite-breaching risks

2. **This month**:
   - [ ] All six baselines delivered by 2026-08-28, then re-score R-007, R-011, R-014, R-016, R-020, R-021
   - [ ] Evaluation criteria signed with mandatory gates confirmed
   - [ ] Caption test set built (the control on which R-015's appetite position depends)

3. **Before the October gate**:
   - [ ] Appetite thresholds tabled for Operations Committee ratification
   - [ ] Four appetite breaches presented with fund-or-accept decisions
   - [ ] E8 remediation and the discipline exception costed as named business case lines
   - [ ] Register incorporated into the SOBC Management Case Part E

---

**END OF RISK REGISTER**

---

*This risk register applies HM Treasury Orange Book (2023) methodology within ArcKit's stakeholder-driven architecture governance framework. The University of Funk is a fictional Australian institution; see DEMO.md.*

*Register owner: Rhonda Bell, Project Manager — L&T Baseline Strategy*

## External References

> This section provides traceability from generated content back to source documents.

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| S | stakeholders.md | Engagement input | `002-lecture-capture/external/` | Stakeholder register with influence, interest and engagement notes |
| PC | privacy-context.md | Compliance input | `002-lecture-capture/external/` | Personal information inventory, data flows, Essential Eight self-assessment |
| SL | system-landscape.md | Foundation artifact | `002-lecture-capture/external/` | System categorisation map and known integrations |
| RR | requirements-register.md | Requirements input | `002-lecture-capture/external/` | Consolidated academic survey requirements |
| SGP | solution-governance-process.md | Foundation artifact | `000-global/policies/` | RIFF Review governance and approval process |
| PRIN | ARC-000-PRIN-v1.0.md | ArcKit artifact | `000-global/` | Enterprise Architecture Principles with criticality ratings |
| STKE | ARC-002-STKE-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Stakeholder analysis — drivers, goals, conflicts, RACI, provisional risks |
| REQ | ARC-002-REQ-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Requirements — controls, dependencies, provisional risks |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| S-C1 | S | Engagement notes | Risk Factor | "Known tension: Rhodes (CIO) favours Microsoft-platform consolidation (Teams/Stream); Moog and Key defend best-of-breed pedagogy tools (Echo360, discipline software)." |
| PC-C1 | PC | §3 | Security Requirement | "Restrict administrative privileges / ML1 / ML2 / Legacy shared admin accounts in AV/capture estate"; "Patch operating systems / ML1 / ML2 / Lecture-theatre capture appliances behind" |
| PC-C2 | PC | §1, class 4 | Data Requirement | "Video/audio recordings capturing students / PI (biometric-adjacent) / Echo360, Zoom, MS Teams / AU / US" |
| PC-C3 | PC | §1, APP 8 note | Compliance Constraint | "APP 8 triggers: classes 3, 4 (partial), 6 and 7 involve offshore disclosure under the assumed hosting — the PIA must assess cross-border disclosure accountability, contract clauses and the practicability of AU-region alternatives." |
| PC-C4 | PC | §2 and §3 | Data Requirement | "Analytics export / Derived engagement data / Ad-hoc extracts / No defined retention or minimisation rules"; "Target set by Digital & IT: ML2 across the SaaS-heavy L&T estate by end 2027." |
| PC-C5 | PC | §4 | Compliance Constraint | "Assess eligible-data-breach criteria, the 30-day investigation clock, and the notification workflow across UoF, the placement providers and affected students." |
| SL-C1 | SL | Notes, item 5 | Risk Factor | "MuseScore / Ableton Live — School of Music & Performing Arts discipline tools; investigation required to determine the extent and nature of current use and licensing across the school." |
| RR-C1 | RR | Header | Procurement Constraint | "MoSCoW priorities were assigned by the project team with the Education Committee." |
| SGP-C1 | SGP | Header and Roles | Compliance Constraint | "The central gate is the RIFF Review — Review of Innovation, Fit & Function — which assesses solution requests for architectural fit, capability duplication, integration impact and total cost before any procurement or build proceeds." |
| SGP-C2 | SGP | Rules | Procurement Constraint | "A request may be paused or closed without progressing further, with the agreement of key consulting stakeholders, if it is deemed not to be required." |
| PRIN-C1 | PRIN | Principle Index | Design Decision | Principles 7 (Privacy by Design), 8 (Data Residency), 14 (Accessibility) and 16 (Layered Security) are each rated CRITICAL criticality. |
| STKE-C1 | STKE | SD-6 | Risk Factor | "a general-purpose meeting-recording tool and a purpose-built lecture capture platform are not the same product class, and he expects the difference to be dismissed in a cost comparison" |
| STKE-C2 | STKE | SD-9 | Risk Factor | "MoSCoW priority reflects institutional breadth, not disciplinary criticality: a requirement affecting one school will always score below one affecting all schools" |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| consultant-brief.md | `002-lecture-capture/external/` | Engagement scope and work packages; informs project context but no passage is cited directly in risk assessment |
| capability-taxonomy.md | `000-global/external/` | Capability categories inform the risk of capability degradation structurally, but no specific passage is cited |
| README.md | `002-lecture-capture/external/` | ArcKit scaffold guidance; contains no project content |

---

**Generated by**: ArcKit `/arckit:risk` command
**Generated on**: 2026-07-27
**ArcKit Version**: 6.7.2
**Project**: Lecture Capture Platform Consolidation (Project 002)
**Model**: Claude Opus 5 (1M context)
**Generation Context**: Derived from ARC-002-STKE-v1.0 (RACI, drivers, conflicts, provisional risks), ARC-002-REQ-v1.0 (controls, dependencies, provisional risks), ARC-000-PRIN-v1.0 (principle criticality for appetite derivation), the privacy context, system landscape and RIFF governance process. No organisational risk appetite statement was available; provisional thresholds derived and flagged for ratification.

<!-- arckit-provenance:start -->

## Build Provenance

_Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix._

| Field | Value |
|-------|-------|
| Requested Effort | `high` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-07-28T04:27:47.856Z |

<!-- arckit-provenance:end -->
