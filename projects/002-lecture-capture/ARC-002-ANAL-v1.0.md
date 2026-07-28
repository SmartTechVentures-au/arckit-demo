# Architecture Governance Analysis Report

> **Template Origin**: Official | **ArcKit Version**: 6.7.2 | **Command**: `/arckit:analyze`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-ANAL-v1.0 |
| **Document Type** | Governance Analysis Report |
| **Project** | Lecture Capture Platform Consolidation (Project 002) |
| **Classification** | OFFICIAL-SENSITIVE |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-28 |
| **Last Modified** | 2026-07-28 |
| **Review Date** | 2026-08-27 |
| **Owner** | Rhonda Bell, Project Manager |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Project Team; Steering Committee; Evaluation Panel |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-28 | ArcKit AI | Initial creation from `/arckit:analyze` command | [PENDING] | [PENDING] |

---

## Executive Summary

**Overall Status**: ⚠️ **Issues Found** — no critical defects, five high-priority items, all resolvable before the 28 August criteria gate

**Governance Health Score**: **85 / 100 — Grade B**

| Metric | Count |
|--------|-------|
| Total requirements | 62 |
| Critical issues | **0** |
| High priority | **5** |
| Medium priority | **8** |
| Low priority | **2** |
| **Total findings** | **15** |

**Recommendation**: **PROCEED**, resolving H1–H5 before evaluation criteria are signed on 2026-08-28.

### Why no critical findings

This is a genuine result, not a soft assessment. The severity heuristic reserves CRITICAL for principle violations, missing core artifacts, MUST requirements with zero design coverage, and orphan requirements. None apply:

- **Zero principle violations.** All 19 global principles are referenced across the 002 artifact set, and no requirement or decision conflicts with one.
- **No missing core artifact.** REQ, STKE, RISK are all present; SOBC is absent but genuinely blocked, not overlooked.
- **No MUST requirement with zero design coverage** — because no design phase has been reached. `ARC-002-TRAC-v1.0` records design, implementation and test coverage as **PHASE** (not yet applicable) rather than GAP, with the basis stated. That treatment is correct and is not re-scored here as a defect.
- **No orphan requirements.** The single requirement absent from both EVAL and SOW (BR-002) is internal governance that no supplier can deliver, and it traces to three risks.

### Requirements quality is unusually strong

Machine-checked across all 62 requirements:

| Check | Result |
|-------|--------|
| Vague adjectives ("fast", "scalable", "intuitive", "robust", "seamless") | **0 occurrences** |
| Functional requirements without acceptance criteria | **0 of 18** |
| Unresolved placeholders (TBD, TBC, TODO, `???`) across all 9 artifacts | **0** |
| Duplicate or near-duplicate requirements | **0 detected** |

### The five things that matter

1. **H1** — The risk register contradicts the requirements on whether 001's canonical model exists. It does.
2. **H3** — Evaluation criteria are unsigned with 31 days to the gate that makes them binding.
3. **H4** — 15% of the evaluation score cannot be computed; six baseline datasets outstanding.
4. **H2** — One requirement is specified to suppliers but has no scoring criterion.
5. **H5** — Four risks are reported as exceeding an appetite that has never been ratified.

---

## Findings Summary

| ID | Category | Severity | Location | Summary | Recommendation |
|----|----------|----------|----------|---------|----------------|
| H1 | Cross-artifact consistency | HIGH | RISK R-010; REQ §Appendix D, A-11 | Risk register states 001's canonical model "not available"; REQ states it is defined in ARC-001-DATA and consumed | Re-scope R-010 to role assignment only; re-score likelihood |
| H2 | Req → evaluation coverage | HIGH | EVAL Category F; SOW §3.4 | NFR-A-003 (graceful degradation) specified in SOW, no scoring criterion in EVAL | Fold into F.2 assessment questions at the weighting workshop |
| H3 | Procurement readiness | HIGH | EVAL Document Control | Status "DRAFT — unsigned"; BR-004 makes signature the control treating R-001 | Sign by 2026-08-28; do not issue to suppliers before |
| H4 | Business case / cost | HIGH | EVAL §6.3; RISK R-006 | Category H (15 points) unscoreable; 6 baseline datasets outstanding, 4 At Risk | Escalate the six deliverables; they gate five other assessments |
| H5 | Risk governance | HIGH | RISK §Provisional Appetite | 4 risks reported as exceeding appetite; thresholds explicitly "not yet ratified" | Table thresholds at Operations Committee 2026-10-09 |
| M1 | Business case | MEDIUM | SOBC absent | Tier 2 baseline type missing | Strategic/Commercial/Management cases ready; Economic Case blocked until 2026-08-28 |
| M2 | Requirements quality | MEDIUM | REQ, all | 46 of 62 (74%) rated Must/Critical | Review Tier 1 set before criteria signature; high share limits negotiation room |
| M3 | Traceability precision | MEDIUM | EVAL §3.1 MQ-1; SOW §2.4 | INT-004 and BR-005 covered semantically, not cited by ID | Two single-line edits before 28 August |
| M4 | Stakeholder traceability | MEDIUM | STKE, all | Zero requirement-ID references; backward traceability asymmetric | Add req IDs to goals G-1…G-10 at next revision |
| M5 | Timeline consistency | MEDIUM | REQ §13; EVAL §7 | RIFF review 11 Sep precedes Clavinet pre-brief 14 Sep | Resolve at weighting workshop |
| M6 | Document control | MEDIUM | All 9 artifacts | Every artifact DRAFT; no approvals recorded | Expected at this stage; confirm review dates hold |
| M7 | Cross-reference density | MEDIUM | DIAG-001, WARD-001 | Zero inbound references | Self-corrects when ADR and HLD review cite them |
| M8 | Data model | MEDIUM | No ARC-002-DATA | 7 DR requirements, no local data model | **Not a defect** — REQ §Appendix D explains 002 consumes 001's canonical model and holds only a projection |
| L1 | Decisions register | LOW | `decisions/` empty | ADR-001 (001) names the 002 platform decision as a successor ADR | Raise after Operations Committee, 2026-10-09 |
| L2 | Reporting | LOW | `docs/health.json` | Present but predates the last 5 artifacts | Re-run `/arckit:health JSON=true` then `/arckit:pages` |

---

## Requirements Analysis

### Inventory

| Type | Count | Tier 1 (Must/Critical) | Tier 2 (Should/High) | Tier 3 (Could) |
|------|-------|------------------------|----------------------|----------------|
| Business (BR) | 8 | 6 | 2 | 0 |
| Functional (FR) | 18 | 14 | 3 | 1 |
| Non-functional (NFR) | 22 | 17 | 5 | 0 |
| Integration (INT) | 7 | 6 | 1 | 0 |
| Data (DR) | 7 | 7 | 0 | 0 |
| **Total** | **62** | **46 (74%)** | **15 (24%)** | **1 (2%)** |

### Coverage into evaluation and specification

Verified by exact-token matching in `ARC-002-TRAC-v1.0`:

| Measure | Covered | Total | % |
|---------|---------|-------|---|
| Assessed in evaluation framework | 59 | 62 | **95%** |
| Specified in Statement of Work | 60 | 62 | **97%** |
| In both | 58 | 62 | **94%** |
| Tier 1 in evaluation | 44 | 46 | 96% |
| Tier 1 in SOW | 45 | 46 | 98% |

### Finding M2 — priority inflation

74% of requirements are Tier 1. This is below the "everything is MUST" antipattern threshold but high enough to matter in two places:

- **Evaluation**: mandatory gates plus a large Must set leaves little room to differentiate suppliers on anything discretionary
- **Negotiation**: a supplier facing 46 non-negotiable requirements has limited scope to offer trade-offs, which typically surfaces as price rather than as scope

Worth a deliberate review of the Tier 1 set before criteria are frozen. Not a defect — the register's MoSCoW ratings were assigned by the project team with Education Committee, and 002 inherited them faithfully.

---

## Architecture Principles Compliance

**All 19 principles referenced across the 002 artifact set. Zero violations detected.**

| Principle | Where enforced | Status |
|-----------|---------------|--------|
| 1 Single Learning Entry Point | DIAG-001 (no direct student→platform edge); REQ TC-2 | ✅ |
| 2 Deliberate Capability Boundaries | BR-001; EVAL option set | ✅ |
| 3 Consistent Experience Across Schools | NFR-U-002; RISK R-019 | ✅ |
| 4 Discipline Specialisation at the Edge | BR-005; EVAL Category G | ✅ |
| 5 Single Source of Truth | FR-016; DR-004; WARD (rejected LMS-as-hub reasoning) | ✅ |
| 6 Canonical Data Model | DR-002; consumed from ARC-001-DATA | ✅ |
| 7 Privacy by Design | DR-003; NFR-C-001; RISK R-013 | ✅ |
| 8 Data Residency | MQ-4; DR-006; NFR-C-001 | ✅ |
| 9 Data Portability and Exit | **MQ-3 mandatory gate**; NFR-I-002 (priority elevated) | ✅ |
| 10 Interface-Mediated Integration | NFR-I-001; TC-3 | ✅ |
| 11 Event-Driven by Default | INT-001; NFR-I-001 | ✅ |
| 12 Automated Identity Lifecycle | **MQ-1 mandatory gate**; TC-5; FR-016 | ✅ |
| 13 Reproducible Automation | NFR-M-002 | ✅ |
| 14 Accessibility by Default | **MQ-2 mandatory gate**; NFR-C-002 | ✅ |
| 15 Availability Aligned to Teaching Calendar | NFR-A-001; BR-006 | ✅ |
| 16 Layered Security Posture | NFR-SEC-001…004; BR-008 | ✅ |
| 17 Observable Integrations | NFR-M-001 | ✅ |
| 18 Evidence-Based Capability Investment | BR-004; EVAL evidence hierarchy | ✅ |
| 19 Realise Licensed Capability | EVAL option C (Microsoft); WARD sourcing analysis | ✅ |

**Notable**: NFR-I-002 elevates REQ-034 from **Should** (survey register) to **Must** on the authority of Principle 9, and records the deviation explicitly rather than applying it silently. That is correct handling of a principle-versus-priority conflict.

---

## Cross-Artifact Consistency

### Finding H1 — the register contradicts the requirements (HIGH)

**Location**: `ARC-002-RISK-v1.0` R-010 versus `ARC-002-REQ-v1.0` §Appendix D and assumption A-11.

**R-010 states**:

> "The canonical entity model (REQ-027) and single-source institutional role assignment (REQ-024), both deliverables of project 001's integration architecture, are **not available** when INT-001 is built"

**ARC-002-REQ §Appendix D states**:

> "The canonical model for student, course and enrolment (REQ-027) **is defined in `ARC-001-DATA-v1.0.md` and consumed here** rather than redefined"

**Independently verified**: `ARC-001-DATA-v1.0` §Context 1 "Canonical Core" defines PERSON, UNIT, TEACHING_PERIOD, UNIT_OFFERING, ENROLMENT and INSTITUTIONAL_ROLE_ASSIGNMENT. `ARC-001-ADR-001` records the same finding.

**Impact**: R-010 is rated Likelihood 3 / Impact 4 (inherent 12) on a premise that is half wrong. The canonical model exists; only the *authoritative source for institutional role* (REQ-024) is genuinely undecided — and `ARC-001-ADR-001` now names that as a dependency requiring its own ADR-002. Mitigation effort directed at "waiting for the data model" is directed at the wrong thing.

**Recommendation**: re-scope R-010 to role assignment and integration mediation only; re-score likelihood downward; add a reference to `ARC-001-ADR-001` and its pending ADR-002. **Effort: 15 minutes.**

### Terminology consistency

No drift detected. "Unit", "teaching period", "capture-equipped room", "canonical model" and "institutional role" are used consistently across all nine artifacts and align with `ARC-001-DATA` entity naming.

### Timeline consistency — Finding M5

`ARC-002-REQ` §13 schedules RIFF review for **2026-09-11** and the Clavinet pre-brief for **2026-09-14**. The pre-brief must precede the review it prepares for. Flagged in `ARC-002-EVAL` §7 at the time of writing but not yet resolved in REQ.

---

## Traceability Analysis

**Traceability matrix**: ✅ exists (`ARC-002-TRAC-v1.0`, score 97/100 on a procurement-phase basis)

| Direction | Status |
|-----------|--------|
| Requirement → evaluation criterion | 95% by ID; 100% including semantic coverage |
| Requirement → SOW clause | 97% by ID; 100% including semantic coverage |
| Requirement → risk control | 47% (29 of 62) — expected; functional requirements fail as capability shortfall, not as governance risk |
| Stakeholder goal → requirement | **Asymmetric — see M4** |
| Requirement → design / test | **PHASE** — not applicable pre-decision |

### Finding M4 — backward traceability from stakeholder goals

`ARC-002-STKE-v1.0` contains **zero requirement-ID references**, because it was authored before the requirements existed. Every goal G-1…G-10 is reachable *from* the requirements via each requirement's "Traces To" field, but not *to* them from the stakeholder document.

**Impact**: an impact analysis starting from a stakeholder goal must route through REQ. Manageable now; awkward during a change request under time pressure.

### Findings M3 — citation precision

| Requirement | Covered at | Not cited by ID |
|-------------|-----------|-----------------|
| INT-004 (identity provider SSO) | EVAL gate MQ-1 — tests exactly this | MQ-1 source column cites only NFR-SEC-001, REQ-031 |
| BR-005 (discipline exception) | SOW §2.4 — full treatment | §2.4 does not reference BR-005 |

Both are coverage-complete and citation-incomplete. They matter because criteria freeze on 28 August, after which an uncited requirement is one an evaluator may not realise they are assessing.

---

## Vendor Procurement Analysis

### SOW quality — ✅ Complete

| Check | Result |
|-------|--------|
| Requirements incorporated | 59 of 62 by ID; ARC-002-REQ incorporated by reference |
| Deliverables with acceptance criteria | 22 deliverables, all with criteria |
| Mandatory terms stated | 7, marked non-negotiable |
| Pre-signature gates | 2 (D-16 export demonstration, M-8 PIA sign-off) |
| Evaluation restated in SOW | **No — correctly delegated to EVAL** |

The SOW deliberately does **not** restate weightings (verified: zero occurrences of competing percentages). Section 8.1 states ARC-002-EVAL governs on any inconsistency. This preserves the BR-004 control.

### Evaluation framework — ⚠️ two issues

**Finding H3 — unsigned.** Status is "DRAFT — unsigned". BR-004 requires signature by Rhodes, Moog and Tanaka **before any vendor engagement**, and this is the primary control treating R-001 (highest-likelihood risk in the register). 31 days remain. An unsigned framework at issue would breach a MUST requirement and void the control.

**Finding H4 — 15% of the score cannot be computed.** Category H (Commercial & Cost, 15 points) depends on four blockers, the last landing 2026-08-28. `ARC-002-RSCH` further establishes that no specialist vendor publishes list pricing, so the cost columns require actual quotes. The framework handles this correctly by locking technical scores before opening the cost envelope — but the underlying data risk (R-006) gates five other assessments.

**Finding H2 — one requirement has no scoring criterion.** NFR-A-003 (graceful degradation — room-level failure isolation, audio-only fallback) is specified in SOW §3.4 and carries no EVAL sub-criterion. A platform that fails whole rather than in defined steps would lose zero points. Category F's 13 points are fully allocated, so the recommended fix is to fold degradation into F.2's assessment questions rather than re-deriving weights.

### Evaluation fairness

| Check | Result |
|-------|--------|
| Weights derived, not negotiated | ✅ Computed from requirement priorities, derivation shown and auditable |
| Mandatory gates outside trading space | ✅ 4 gates, pass/fail |
| Evidence tier caps score | ✅ Marketing caps at 2/4; 10 sub-criteria require hands-on |
| Declared interests recorded | ✅ Both principals; adjusted RIFF chairing |
| Do-nothing baseline evaluated | ✅ Option D, explicitly not a strawman |
| Deviation from template weighting | ✅ Recorded openly in §1.3 with reasoning |

---

## Risk Management Analysis

**Register exists**: ✅ `ARC-002-RISK-v1.0` — 22 risks, HM Treasury Orange Book methodology

| Measure | Value |
|---------|-------|
| Total risks | 22 |
| Inherent total / residual total | 266 → 156 (**41% reduction**) |
| Critical (residual) | 0 |
| High (residual) | 0 |
| Medium / Low (residual) | 18 / 4 |
| Risks with named owner from STKE RACI | **22 of 22 (100%)** |
| Risks with requirement linkage | 29 of 62 requirements referenced |
| 4Ts distribution | Tolerate 4 · Treat 17 · Transfer 1 · Terminate 0 |

### Finding H5 — appetite thresholds unratified

The register reports **four risks exceeding appetite** (R-013, R-016, R-017, R-018). It also states plainly that no organisational risk appetite statement exists and that the thresholds are **provisional, derived from principle criticality, and require Operations Committee ratification**.

**Impact**: four breaches against unratified numbers are an architect's opinion, not a governance finding. Escalating them as breaches before the thresholds carry authority invites the Committee to dispute the threshold rather than address the risk.

**Recommendation**: table the thresholds for ratification at the same Operations Committee sitting (2026-10-09) as the breach escalations, in that order. The register already recommends this; the analysis confirms it is the correct sequence.

### Risk governance quality

Three observations that raise confidence:

- **R-016 is honestly rated.** It has the weakest control effectiveness in the register (25%) and the largest appetite breach, and the register states no justification for proceeding — recommending explicit fund-or-accept rather than defending the position.
- **Terminate is zero and stated deliberately**, with the option-level termination (RIFF pause provision) recorded separately rather than being padded into the 4Ts table.
- **Assessment integrity caveat present**: residual scores are labelled forecasts because most controls are specified rather than implemented, with three mandatory re-scoring points defined.

---

## Business Case Analysis — Finding M1

**SOBC exists**: ❌ No

`ARC-002-RISK` §I already maps the register into a future business case, and the Strategic, Commercial and Management cases are supportable from existing artifacts. The **Economic Case is not**: it requires the cost baselines outstanding until 2026-08-28, and `ARC-002-RSCH` produced no TCO for the same reason.

**This is correctly sequenced rather than overlooked.** Producing an Economic Case now would require inventing a baseline — the specific failure mode that the ⚠️ convention across REQ, RISK and RSCH exists to prevent.

**Recommendation**: run `/arckit:sobc` after 2026-08-28. Strategic and Management cases could be drafted earlier if useful for the September cycle.

---

## Data Model Analysis — Finding M8

**ARC-002-DATA exists**: ❌ No — and this is correct.

002 defines 7 data requirements (DR-001…DR-007) and 4 entities inline in `ARC-002-REQ` §9. `ARC-002-REQ` §Appendix D states the canonical model is defined in `ARC-001-DATA-v1.0` and consumed rather than redefined, with 002 holding an identity **projection** (Entity 3) rather than a master record.

| Check | Result |
|-------|--------|
| DR requirements mapped to entities | 7 of 7 |
| PII identified | ✅ Recordings classified as personal information, biometric-adjacent |
| Residency documented | ✅ DR-006 cross-border register; MQ-4 gate |
| Retention defined | ✅ DR-005; closes a gap the privacy context flagged as absent |
| Data owners from RACI | ✅ Eleanor Frame (privacy), Sam Okafor (integration) |

Consuming rather than duplicating the canonical model is the correct application of Principle 6. Flagged only so the absence is not later mistaken for an omission.

---

## Compliance Analysis

### UK Government frameworks — **not applicable**

TCoP, GDS Service Standard, AI Playbook, ATRS, NCSC CAF and MOD Secure by Design have **no standing** for The University of Funk, an Australian university. They are excluded throughout the 002 artifact set, correctly and explicitly.

### Applicable frameworks

| Framework | Status | Evidence |
|-----------|--------|----------|
| **Privacy Act 1988 / APPs** | ⚠️ Assessment pending | NFR-C-001, DR-006, MQ-4 in place. PIA is a hard pre-signature gate (M-8, 2026-12-04). R-013 exceeds provisional appetite |
| **APP 8 cross-border** | ⚠️ Assessment pending | Trigger identified; residency stated as an evaluation requirement |
| **ASD Essential Eight** | ⚠️ Gap acknowledged | Two strategies at ML1 for this estate; BR-008 and R-016 address. ML2 target end 2027 |
| **NDB scheme** | ✅ Contractually addressed | NFR-C-005 requires 24-hour vendor notification, protecting the 30-day assessment clock |
| **WCAG 2.2 AA** | ✅ Gated | MQ-2 mandatory gate, with a dated-remediation-plan route recorded as a deliberate design choice |

**No AI components.** Automatic speech recognition is treated as a commodity processing service, not an algorithmic decision system — a defensible classification.

---

## Metrics Dashboard

| Dimension | Score | Basis |
|-----------|-------|-------|
| **Requirements quality** | **92%** | 0 vague, 0 missing acceptance criteria, 0 placeholders, 0 duplicates; −8 for 74% Tier 1 concentration |
| **Principles compliance** | **100%** | 19 of 19 referenced, 0 violations, 1 deviation recorded openly |
| **Traceability** | **94%** | 94% bidirectional by ID; −6 for 2 citation gaps and asymmetric stakeholder linkage |
| **Stakeholder alignment** | **78%** | Forward traceability complete; no requirement IDs in STKE |
| **Risk management** | **88%** | 22 risks, 100% owned, 41% reduction; −12 for unratified appetite |
| **Procurement readiness** | **72%** | Framework complete and fair; −28 for unsigned criteria and unscoreable cost category |
| **Business case** | **N/A — blocked** | Excluded from score; Economic Case genuinely gated on 2026-08-28 |
| **Design / test coverage** | **N/A — phase** | Excluded from score; no design phase reached |
| **Compliance** | **80%** | Frameworks correctly scoped; PIA and E8 assessments pending |

### Overall Governance Health: **85 / 100 — Grade B**

*Good governance, minor issues.* Two dimensions are excluded rather than scored zero, and the exclusion is stated so the figure is not quoted out of context. Including them would produce roughly 66% and would measure the project's **phase** rather than its **governance discipline**.

---

## Recommendations

### High priority — before 2026-08-28

| # | Action | Finding | Owner | Effort |
|---|--------|---------|-------|--------|
| 1 | Sign evaluation criteria under BR-004 | H3 | Grace Tanaka | Workshop + signature |
| 2 | Escalate the six baseline deliverables; four are At Risk | H4 | Rhonda Bell | Tracking |
| 3 | Resolve NFR-A-003 — fold degradation into EVAL F.2 questions | H2 | Rhonda Bell | 30 min at workshop |
| 4 | Re-scope R-010 to role assignment; reference ARC-001-ADR-001 | H1 | Rhonda Bell | 15 min |
| 5 | Add INT-004 to MQ-1 source column; add BR-005 to SOW §2.4 | M3 | Grace Tanaka | 2 single-line edits |
| 6 | Fix RIFF / pre-brief sequencing in REQ §13 | M5 | Rhonda Bell | 5 min |

### Medium priority — before the October gate

| # | Action | Finding | Owner |
|---|--------|---------|-------|
| 7 | Table appetite thresholds for ratification alongside the four breaches | H5 | Vernon Ostinato |
| 8 | Review the 46-requirement Tier 1 set for genuine necessity | M2 | Dr. Benny Moog |
| 9 | Initiate the Privacy Impact Assessment at preferred-option stage | Compliance | Eleanor Frame |

### Lower priority

| # | Action | Finding |
|---|--------|---------|
| 10 | Add requirement IDs to STKE goals G-1…G-10 at next revision | M4 |
| 11 | Regenerate `docs/health.json`, then re-run `/arckit:pages` | L2 |
| 12 | Raise the 002 platform ADR after Operations Committee | L1 |

---

## Next Steps

**Status: ⚠️ MAY PROCEED** — no critical issues. Address H1–H5 in parallel with evaluation preparation.

### Suggested commands

| Command | When | Why |
|---------|------|-----|
| `arckit-au:au-pia` | October, preferred-option stage | Hard pre-signature gate; R-013 above appetite; leverage expires at signature |
| `arckit-au:au-e8-posture` | Any time | R-016 is the largest appetite breach with the weakest controls |
| `/arckit:sobc` | After 2026-08-28 | Economic Case blocked until baselines land |
| `/arckit:diagram` (deployment) | Any time | The appliance estate is the dominant inertia and appears in no diagram |
| `/arckit:analyze` | After H1–H5 resolved | Expect 90%+; re-scoring procurement readiness after signature is the largest single gain |

---

## Appendix: Analysis Methodology

**Artifacts analysed** (9): ARC-002-REQ, ARC-002-STKE, ARC-002-RISK, ARC-002-EVAL, ARC-002-SOW, ARC-002-TRAC, ARC-002-RSCH, ARC-002-DIAG-001, ARC-002-WARD-001. Plus ARC-000-PRIN, ARC-001-DATA and ARC-001-ADR-001 for cross-project consistency, and 5 vendor profiles and 3 tech notes for completeness.

**Detection passes applied**: A (requirements quality), B (principles alignment), C (requirement→design traceability), D (vendor procurement), E (stakeholder traceability), F (risk management), G (business case), H (data model), K (cross-artifact consistency). Passes I (UK Gov) and J (MOD) assessed as not applicable and excluded with reasons.

**Method**: requirement IDs and priorities extracted programmatically; coverage computed by exact-token matching across artifacts; vague-adjective, placeholder and acceptance-criteria checks run mechanically across all 62 requirements. Quantitative claims are machine-derived, not estimated.

**Not modified**: this analysis is non-destructive. No existing artifact was changed.

---

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| REQ | ARC-002-REQ-v1.0.md | ArcKit artifact | `002-lecture-capture/` | 62 requirements |
| RISK | ARC-002-RISK-v1.0.md | ArcKit artifact | `002-lecture-capture/` | 22 risks, appetite position |
| EVAL | ARC-002-EVAL-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Gates, weights, evidence rules |
| SOW | ARC-002-SOW-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Scope, deliverables, terms |
| TRAC | ARC-002-TRAC-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Coverage figures reused here |
| DATA1 | ARC-001-DATA-v1.0.md | ArcKit artifact | `001-lt-ecosystem/` | Canonical Core — evidence for H1 |
| ADR1 | ARC-001-ADR-001-v1.0.md | ArcKit artifact | `001-lt-ecosystem/decisions/` | Corroborates H1 |
| PRIN | ARC-000-PRIN-v1.0.md | ArcKit artifact | `000-global/` | 19 principles |

### Citations

| Citation ID | Doc ID | Section | Category | Quoted Passage |
|-------------|--------|---------|----------|----------------|
| RISK-C1 | RISK | R-010 | Risk Factor | "The canonical entity model (REQ-027) and single-source institutional role assignment (REQ-024) ... are not available when INT-001 is built" |
| REQ-C1 | REQ | Appendix D | Data Requirement | "The canonical model for student, course and enrolment (REQ-027) is defined in `ARC-001-DATA-v1.0.md` and consumed here rather than redefined" |
| DATA1-C1 | DATA1 | §Context 1 | Data Requirement | "Canonical Core — student, course, enrolment, institutional role" defining PERSON, UNIT, TEACHING_PERIOD, UNIT_OFFERING, ENROLMENT, INSTITUTIONAL_ROLE_ASSIGNMENT |
| EVAL-C1 | EVAL | Document Control | Procurement Constraint | Status: "DRAFT — unsigned" |
| RISK-C2 | RISK | Provisional Appetite | Risk Factor | "The thresholds used throughout this register are provisional ... They require ratification by the Operations Committee before they carry authority." |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| Vendor profiles (5), tech notes (3) | `002-lecture-capture/` | Market intelligence; reviewed for completeness, no governance findings |
| External engagement inputs (5) | `002-lecture-capture/external/` | Traced indirectly through the artifacts that cite them |

---

**Generated by**: ArcKit `/arckit:analyze` command
**Generated on**: 2026-07-28
**ArcKit Version**: 6.7.2
**Project**: Lecture Capture Platform Consolidation (Project 002)
**Model**: Claude Opus 5 (1M context)
**Generation Context**: Non-destructive governance analysis of 9 project-002 artifacts plus 3 cross-project artifacts. No governance-scan hook data was available, so artifacts were loaded and analysed directly with programmatic extraction for all quantitative claims. UK Government and MOD detection passes assessed as not applicable and excluded with stated reasons. Design, implementation and test dimensions excluded from scoring as phase-not-reached rather than scored zero.

**END OF ANALYSIS REPORT**

<!-- arckit-provenance:start -->

## Build Provenance

_Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix._

| Field | Value |
|-------|-------|
| Requested Effort | `high` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-07-28T07:41:22.036Z |

<!-- arckit-provenance:end -->
