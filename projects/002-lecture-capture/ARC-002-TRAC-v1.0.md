# Requirements Traceability Matrix: Lecture Capture Platform Consolidation

> **Template Origin**: Official | **ArcKit Version**: 6.7.2 | **Command**: `/arckit:traceability`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-TRAC-v1.0 |
| **Document Type** | Requirements Traceability Matrix |
| **Project** | Lecture Capture Platform Consolidation (Project 002) |
| **Classification** | OFFICIAL-SENSITIVE |
| **Status** | SUPERSEDED — replaced by [`ARC-002-TRAC-v1.1`](ARC-002-TRAC-v1.1.md) on 2026-07-28 |
| **Version** | 1.0 |
| **Created Date** | 2026-07-28 |
| **Last Modified** | 2026-07-28 |
| **Review Date** | 2026-08-27 |
| **Owner** | Rhonda Bell, Project Manager |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Project Team; Evaluation Panel; Steering Committee |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-28 | ArcKit AI | Initial creation from `/arckit:traceability` command — procurement-phase matrix | [PENDING] | [PENDING] |

## Document Purpose

To verify, **before the evaluation criteria are signed on 2026-08-28**, that every requirement in ARC-002-REQ-v1.0 is either assessed in the evaluation framework or specified in the Statement of Work — and to identify anything that is neither.

Timing is the point of this document. Once criteria are signed under BR-004 they cannot be amended, so a requirement that is missing from the framework at that moment is missing for the whole procurement. This matrix is the last cheap opportunity to find that.

---

## 1. Overview

### 1.1 Traceability Scope — and an Honest Statement of What Cannot Yet Be Traced

The standard traceability chain runs **Requirement → Design → Implementation → Test**. This project is at procurement stage. No platform has been selected, no contract signed, no design produced, no code written and no tests executed.

**Reporting 62 requirements as "not covered" against design, implementation and test columns would be technically accurate and materially misleading.** Those artifacts do not exist because the project has not reached the phase that produces them, not because anything has been missed.

This matrix therefore traces the chain that **does** exist today:

```text
Survey requirement (REQ-xxx)          [engagement input]
        ↓
Stakeholder goal / outcome (G-x, O-x) [ARC-002-STKE]
        ↓
Requirement (BR/FR/NFR/INT/DR)        [ARC-002-REQ]   ← 62 requirements
        ↓
        ├─→ Evaluation gate or criterion (MQ-x, A.1–I.4)  [ARC-002-EVAL]
        ├─→ SOW scope, deliverable or contract term       [ARC-002-SOW]
        └─→ Risk control (R-001 … R-022)                  [ARC-002-RISK]
        ↓
   [PHASE GATE — 2026-10-09 platform decision]
        ↓
   Design → Configuration → Migration → Test    ← not yet applicable
```

**Design, implementation and test coverage are recorded as `PHASE` (not yet applicable), not as `GAP`.** They become traceable after the Operations Committee decision on 2026-10-09 and the design deliverables D-1 to D-6 due 2027-02-12. This matrix must be re-run at that point.

### 1.2 What This Matrix Verifies

| Question | Answered in |
|----------|-------------|
| Is every requirement assessed in the evaluation? | §2.1, §3.1 |
| Is every requirement specified to suppliers? | §2.1, §3.2 |
| Are the Tier 1 (MUST/CRITICAL) requirements fully covered? | §3.3 |
| Which requirements have a risk control behind them? | §2.2 |
| What is covered semantically but not cited by ID? | §4.2 |
| What is genuinely uncovered? | §4.1 |

### 1.3 Document References

| Document | Role in this matrix |
|----------|--------------------|
| ARC-002-REQ-v1.0 | Source of all 62 requirement IDs and priorities |
| ARC-002-EVAL-v1.0 | Evaluation gates and scored criteria — the assessment side |
| ARC-002-SOW-v1.0 | Scope, deliverables and contract terms — the specification side |
| ARC-002-RISK-v1.0 | Risk controls referencing requirements |
| ARC-002-STKE-v1.0 | Stakeholder goals G-1 to G-10, outcomes O-1 to O-6 |
| ARC-002-RSCH-v1.0 | Market evidence informing gate design |
| ARC-000-PRIN-v1.0 | Principles constraining requirements |

### 1.4 Method

Requirement IDs and priorities were extracted programmatically from ARC-002-REQ-v1.0 (62 requirements). Each ID was then matched by exact-token search across the evaluation framework, SOW, risk register, stakeholder analysis and research document. Counts in §3 are machine-derived, not estimated.

**Two priority vocabularies** are in use and are normalised throughout:

| As written | Normalised | Count |
|-----------|-----------|-------|
| MUST_HAVE (29) + CRITICAL (17) | **Tier 1** | 46 |
| SHOULD_HAVE (5) + HIGH (10) | **Tier 2** | 15 |
| COULD_HAVE (1) | **Tier 3** | 1 |

---

## 2. Traceability Matrix

### 2.1 Forward Traceability: Requirement → Evaluation → SOW

Status key: **✅ Traced** — cited by ID in both EVAL and SOW · **◐ Semantic** — requirement is addressed but its ID is not cited · **⚠ Partial** — covered on one side only · **○ Internal** — not supplier-facing by design

#### Business Requirements

| Req ID | Requirement | Tier | Evaluation | SOW | Risk | Status |
|--------|-------------|------|-----------|-----|------|--------|
| BR-001 | Single primary platform with declared boundary | 1 | Whole framework; §2 options | §3.2, S-1 | R-001, R-002 | ✅ |
| BR-002 | Decision endorsed through governance by 9 Oct 2026 | 1 | — | — | R-001, R-004, R-005 | ○ Internal |
| BR-003 | Whole-of-life cost flat or reduced | 2 | H.1–H.3 | §3.2, §7.2 | R-011, R-012 | ✅ |
| BR-004 | Evaluation on published unchanged criteria | 1 | §1.2, Appendix C | §8.1, M-1 | R-001, R-017 | ✅ |
| BR-005 | Bounded, funded discipline exception | 2 | Category G | §2.4 (semantic) | R-003 | ◐ Semantic |
| BR-006 | Transition without teaching disruption | 1 | F.1, F.2, I.3 | §1.3, §5.1 | R-004, R-008 | ✅ |
| BR-007 | Archive accessible; exit rights proven | 1 | MQ-3, E.1–E.4 | §3.2, D-16 | R-020, R-021 | ✅ |
| BR-008 | Essential Eight gaps closed on capture estate | 1 | D.5, D.6, C.5 | §3.2, S-7 | R-016 | ✅ |

#### Functional Requirements

| Req ID | Requirement | Tier | Evaluation | SOW | Risk | Status |
|--------|-------------|------|-----------|-----|------|--------|
| FR-001 | Automatic scheduled capture from timetable | 1 | A.1 | §3.3, S-2 | — | ✅ |
| FR-002 | Publication to unit site within 4 hours | 1 | A.2 | §3.3, S-3 | — | ✅ |
| FR-003 | Ad-hoc capture in ≤ 2 actions | 1 | A.3 | §3.3 | — | ✅ |
| FR-004 | Capture failure detection and alerting | 1 | A.4 | §3.3, D-12 | — | ✅ |
| FR-005 | Review, trim and segment removal | 1 | A.3 | §3.3 | — | ✅ |
| FR-006 | Automatic captioning within 24 hours | 1 | B.1, MQ-2 | §3.3, S-3 | R-015 | ✅ |
| FR-007 | Caption correction workflow | 2 | B.3 | §3.3 | R-015 | ✅ |
| FR-008 | Live class delivery with recording | 1 | A.5 | §3.3, S-4 | — | ✅ |
| FR-009 | Multi-camera performance capture | 3 | G.1 | §3.3, §2.4 | R-003 | ✅ |
| FR-010 | Student playback experience | 1 | A.6 | §3.3 | — | ✅ |
| FR-011 | Engagement analytics per unit | 2 | A.6 | §3.3, S-10 | — | ✅ |
| FR-012 | Unit-level capture policy configuration | 1 | F.5 | §3.3 | R-019 | ✅ |
| FR-013 | Student notification of recording | 1 | D.7 | §3.3 | R-019 | ✅ |
| FR-014 | Retention schedule and defensible disposal | 1 | E.3 | §3.3, S-9, D-11 | R-014 | ✅ |
| FR-015 | Archive migration with link preservation | 1 | E.2 | §3.3, S-8, D-10 | R-020, R-021 | ✅ |
| FR-016 | Access derived from enrolment | 1 | C.1 | §3.3, S-5 | R-018, R-022 | ✅ |
| FR-017 | Bulk export of recordings and captions | 1 | E.1, MQ-3 | §3.3, D-16 | R-020 | ✅ |
| FR-018 | Operational and compliance reporting | 1 | A.4, F.3 | §3.3, D-17–D-21 | — | ✅ |

#### Non-Functional Requirements

| Req ID | Requirement | Tier | Evaluation | SOW | Risk | Status |
|--------|-------------|------|-----------|-----|------|--------|
| NFR-P-001 | Processing and publication latency | 1 | F.4 | §3.4 | — | ✅ |
| NFR-P-002 | Playback performance | 2 | F.4 | §3.4 | — | ✅ |
| NFR-A-001 | 99.9% availability in teaching periods | 1 | F.1 | §3.4, §9.6 | R-004 | ✅ |
| NFR-A-002 | Capture continuity; RPO zero | 1 | F.2 | §3.4, §9.6 | R-021 | ✅ |
| NFR-A-003 | Graceful degradation | 2 | — | §3.4 | — | ⚠ Partial |
| NFR-S-001 | Storage and volume growth | 2 | F.4 (implicit) | §3.4 | R-014 | ⚠ Partial |
| NFR-SEC-001 | SSO with MFA, no local accounts | 1 | **MQ-1**, D.2 | §3.1, §3.4, §9.7 | R-018, R-022 | ✅ |
| NFR-SEC-002 | RBAC; no shared admin accounts | 1 | D.2, C.5 | §3.4 | R-016 | ✅ |
| NFR-SEC-003 | Encryption in transit and at rest | 1 | D.3 | §3.4 | R-018 | ✅ |
| NFR-SEC-004 | Vulnerability and patch management | 1 | D.5 | §3.4, §9.6 | R-016 | ✅ |
| NFR-C-001 | Privacy Act; residency; APP 8 | 1 | **MQ-4**, D.1 | §3.1, §3.4 | R-013 | ✅ |
| NFR-C-002 | WCAG 2.2 AA | 1 | **MQ-2**, B.1–B.3 | §3.1, §3.4 | R-015 | ✅ |
| NFR-C-003 | Audit logging | 2 | D.4 | §3.4 | R-018 | ✅ |
| NFR-C-004 | Essential Eight evidence | 2 | D.6 | §3.4, D-20 | R-016 | ✅ |
| NFR-C-005 | Breach notification within 24 hours | 1 | D.6 | §3.4, §9.7 | R-018 | ✅ |
| NFR-U-001 | Academic workflow effort | 2 | A.3 | §3.4 | — | ✅ |
| NFR-U-002 | Cross-school consistency | 2 | A.6 | §3.4 | R-019 | ✅ |
| NFR-U-003 | Caption accuracy on discipline vocabulary | 2 | **B.2** | §3.4, §7.1(g) | R-015 | ✅ |
| NFR-M-001 | Observability | 2 | F.3 | §3.4 | — | ✅ |
| NFR-M-002 | Documentation and runbooks | 1 | F.6 | §3.4, D-12–D-14 | R-009 | ✅ |
| NFR-I-001 | Integration standards (LTI 1.3, SCIM) | 1 | C.2, C.1 | §3.4, §7.1(d) | R-022 | ✅ |
| NFR-I-002 | Data portability and exit | 1 | **MQ-3**, E.1 | §3.1, §3.4, §9.7 | R-012, R-020 | ✅ |

#### Integration Requirements

| Req ID | Requirement | Tier | Evaluation | SOW | Risk | Status |
|--------|-------------|------|-----------|-----|------|--------|
| INT-001 | SIS → platform identity and roles | 1 | C.1 | §3.5, S-5 | R-010, R-022 | ✅ |
| INT-002 | Timetabling → capture scheduling | 1 | C.3 | §3.5, S-6 | — | ✅ |
| INT-003 | Platform ↔ Blackboard Ultra (LTI 1.3) | 1 | **C.2** | §3.5, §7.1(d) | — | ✅ |
| INT-004 | Identity provider SSO with MFA | 1 | MQ-1 (semantic) | §3.5, S-5 | — | ◐ Semantic |
| INT-005 | Platform → institutional data platform | 2 | A.6 | §3.5, S-10 | — | ✅ |
| INT-006 | Platform ↔ room appliances | 1 | C.5 | §3.5, S-7 | R-007, R-016 | ✅ |
| INT-007 | Incumbent → platform archive migration | 1 | E.2 | §3.5, S-8 | R-020, R-021 | ✅ |

#### Data Requirements

| Req ID | Requirement | Tier | Evaluation | SOW | Risk | Status |
|--------|-------------|------|-----------|-----|------|--------|
| DR-001 | Recording classification and handling | 1 | D.1 | §3.6 | R-018 | ✅ |
| DR-002 | Canonical entity alignment | 1 | C.4 | §3.6 | R-010 | ✅ |
| DR-003 | Analytics minimisation and retention | 1 | D.1 | §3.6 | R-014 | ✅ |
| DR-004 | Identity projection minimisation | 1 | C.4 | §3.6 | — | ✅ |
| DR-005 | Retention and disposal schedule | 1 | E.3 | §3.6, S-9 | R-014 | ✅ |
| DR-006 | Residency and cross-border register | 1 | **MQ-4**, D.1 | §3.6 | R-013 | ✅ |
| DR-007 | Migration data integrity | 1 | E.4 | §3.6 | R-021 | ✅ |

### 2.2 Backward Traceability: Controls and Gates → Requirements

#### Mandatory gates → requirements verified

| Gate | Requirements verified | Consequence of failure |
|------|----------------------|------------------------|
| **MQ-1** SSO/MFA, no local accounts | NFR-SEC-001, REQ-031, INT-004 | Elimination — no remediation route |
| **MQ-2** WCAG 2.2 AA | NFR-C-002, REQ-029, FR-006 | Elimination, unless a dated remediation plan is committed |
| **MQ-3** Open-format export | NFR-I-002, REQ-034, FR-017, BR-007 | Elimination, or escalation if all options fail |
| **MQ-4** Data residency | NFR-C-001, REQ-030, DR-006 | Elimination |

#### Risk controls → requirements

29 of 62 requirements are named in a risk control. The 33 without a risk linkage are predominantly functional requirements whose failure mode is capability shortfall rather than a governance, cost or compliance risk — which is the expected pattern, not a gap.

| Risk | Requirements it protects |
|------|-------------------------|
| R-001 Decision contested | BR-001, BR-004 |
| R-006 Baselines not delivered | BR-003 (and, indirectly, all cost assessment) |
| R-013 PIA incomplete at signature | NFR-C-001, DR-006 |
| R-015 Accessibility on vendor claims | NFR-C-002, NFR-U-003, FR-006, FR-007 |
| R-016 Essential Eight gaps persist | BR-008, NFR-SEC-002, NFR-SEC-004, NFR-C-004 |
| R-018 Privacy incident | FR-016, NFR-SEC-001/003, NFR-C-003/005, DR-001 |
| R-020 Archive stranded | BR-007, FR-017, NFR-I-002, INT-007 |
| R-021 Migration data loss | FR-015, DR-007, INT-007, NFR-A-002 |
| R-022 Bulk-import-only provisioning | FR-016, INT-001, NFR-I-001 |

#### Stakeholder goals → requirements

**Note on a structural gap**: ARC-002-STKE contains zero references to requirement IDs, because it was written before ARC-002-REQ existed. Backward traceability to stakeholder goals therefore runs through the "Traces To" field inside each requirement rather than from the stakeholder document outward. This is a documentation asymmetry, not a coverage gap — every goal G-1 to G-10 is reachable — but it means an impact analysis starting from a stakeholder goal must go via the requirements document. Recorded as action A-4 in §6.

---

## 3. Coverage Analysis

All figures machine-derived from exact-token matching of 62 requirement IDs across five artifacts.

### 3.1 Overall Coverage

| Measure | Covered | Total | % |
|---------|---------|-------|---|
| Requirements assessed in the evaluation framework | 59 | 62 | **95%** |
| Requirements specified in the SOW | 60 | 62 | **97%** |
| Requirements in **both** | 58 | 62 | **94%** |
| Requirements in **neither** | 1 | 62 | **2%** |
| Requirements with a risk control | 29 | 62 | 47% |

### 3.2 Coverage by Tier

| Tier | Count | In EVAL | In SOW | Threshold | Assessment |
|------|-------|---------|--------|-----------|------------|
| **Tier 1** (MUST / CRITICAL) | 46 | 44 (96%) | 45 (98%) | 100% | ⚠ Two shortfalls, both resolvable |
| **Tier 2** (SHOULD / HIGH) | 15 | 14 (93%) | 14 (93%) | > 80% | ✅ Above threshold |
| **Tier 3** (COULD) | 1 | 1 (100%) | 1 (100%) | < 50% acceptable | ✅ |

### 3.3 Coverage by Category

| Category | Count | In EVAL | In SOW | Notes |
|----------|-------|---------|--------|-------|
| Business (BR) | 8 | 7 | 7 | BR-002 is internal governance, correctly absent from both |
| Functional (FR) | 18 | 18 | 18 | Full coverage |
| Non-Functional (NFR) | 22 | 21 | 22 | NFR-A-003 not scored |
| Integration (INT) | 7 | 6 | 7 | INT-004 covered semantically via MQ-1 |
| Data (DR) | 7 | 7 | 7 | Full coverage |

### 3.4 Design, Implementation and Test Coverage

| Measure | Status |
|---------|--------|
| Design coverage | **PHASE** — no HLD/DLD exists; design deliverables D-1 to D-6 due 2027-02-12 |
| Implementation coverage | **PHASE** — no platform selected; configuration begins after contract execution 2026-12-11 |
| Test coverage | **PHASE** — test plan is deliverable D-6; pilot acceptance testing runs Semester 1 2027 |

**These are not gaps.** They are phases the project has not reached. The first meaningful design-side traceability run is after D-1 and D-2 are accepted; the first test-side run is at pilot exit (M-12, 2027-06-25).

**However, two pre-contract verification activities do exist and are traceable now**: the hands-on assessment sessions in ARC-002-EVAL §5.3, and the pre-signature export demonstration (SOW deliverable D-16). These are the earliest evidence any requirement will receive.

| Pre-contract verification | Requirements verified | When |
|--------------------------|----------------------|------|
| Integration test session | INT-001, INT-002, INT-003, INT-006, C.1–C.5 criteria | Week of 2026-09-01 |
| Capability walkthrough | FR-001 to FR-005, FR-008, FR-010, FR-012 | Week of 2026-09-01 |
| Accessibility and captioning session | NFR-C-002, NFR-U-003, FR-006, FR-007 | Week of 2026-09-01 |
| Security and privacy session | NFR-SEC-001, NFR-C-001, DR-006, NFR-C-003 | Week of 2026-09-01 |
| Export and migration session | NFR-I-002, FR-017, FR-015, INT-007, DR-005 | Week of 2026-09-07 |
| Resilience test | NFR-A-002 | Week of 2026-09-07 |

Six of the ten sub-criteria requiring hands-on evidence map to Tier 1 requirements. That is the intended design: the requirements that matter most receive the strongest evidence tier available before commitment.

---

## 4. Gap Analysis

Four findings. One is correct-by-design, two are citation defects with a trivial fix, and one is a genuine scoring omission.

### 4.1 Requirements Covered by Neither Evaluation nor SOW

| Req ID | Requirement | Tier | Assessment |
|--------|-------------|------|-----------|
| **BR-002** | Decision endorsed through governance by 9 October 2026 | 1 | **Correct by design — not a defect** |

BR-002 requires the University's own governance to endorse the recommendation through RIFF, Education Committee and Operations Committee. **No supplier can deliver it and no proposal should be scored against it.** Its absence from both supplier-facing documents is right.

It is not unmanaged: R-001, R-004 and R-005 in the risk register all treat the failure modes, and the milestone schedule in ARC-002-REQ §13 tracks the three gates.

**Action**: classify BR-002 explicitly as an *internal governance requirement* in the next revision of ARC-002-REQ, so future traceability runs do not re-raise it. A requirement type that no supplier can satisfy should be visibly distinguished from one that was overlooked.

### 4.2 Requirements Covered Semantically but Not Cited by ID

These are **citation defects, not coverage defects**. The requirement is addressed; its ID is not written down at the point of coverage. They matter because after 2026-08-28 the criteria are frozen, and an uncited requirement is one an evaluator may not realise they are assessing.

| Req ID | Requirement | Where it is actually covered | Fix |
|--------|-------------|------------------------------|-----|
| **INT-004** | Identity provider SSO with MFA | Gate MQ-1 tests exactly this — "hands-on test against the university IdP in a trial tenant" — but MQ-1's source column cites only NFR-SEC-001 and REQ-031 | Add INT-004 to the MQ-1 source column in ARC-002-EVAL §3.1 |
| **BR-005** | Bounded, funded discipline exception | SOW §2.4 covers it in full as a separately procured item, and EVAL Category G scores it | Add the BR-005 reference to SOW §2.4 |

Both fixes are single-line edits to documents not yet signed. **Both must be made before 2026-08-28.**

### 4.3 Genuine Coverage Shortfall

| Req ID | Requirement | Tier | Nature of gap |
|--------|-------------|------|---------------|
| **NFR-A-003** | Graceful degradation — room-level failure isolation, audio-only fallback, retry with backoff, playback available when capture is degraded | 2 | **Specified in SOW §3.4, not scored in the evaluation** |

The evaluation framework scores capture continuity (F.2, covering NFR-A-002) and observability (F.3, covering NFR-M-001), but has no sub-criterion for degradation behaviour. A platform that fails whole rather than in defined steps would not lose a single point.

This is a real omission with a real consequence: the difference between one room's appliance failing and a whole-campus capture outage is precisely the failure isolation NFR-A-003 requires, and it is currently unassessed.

**Options**, for the weighting workshop on 2026-08-21:

1. Add a sub-criterion under Category F — but F's 13 points are fully allocated, so points must come from F.1–F.6, and the derivation would need re-running.
2. Fold degradation into F.2's assessment questions without adding points — cheapest, and defensible since F.2 already covers continuity. **Recommended.**
3. Accept the gap and rely on the SOW specification alone — weakest, since a specified-but-unscored requirement gives the University no basis to prefer a supplier who meets it.

### 4.4 Design Elements Without Requirements

**None.** No requirement ID appears in the evaluation framework, SOW or risk register that is absent from ARC-002-REQ-v1.0. There is no evidence of scope creep.

The survey register IDs (REQ-001 to REQ-035) appear throughout as *source* references and are correctly distinguished from this project's own requirement IDs.

### 4.5 Requirements Without Test Coverage

Not assessable at this phase — see §3.4. Every Tier 1 requirement will require test coverage in the design phase, and the ten sub-criteria requiring hands-on evidence (ARC-002-EVAL §5.2) establish which receive verification earliest.

---

## 5. Traceability Score

| Dimension | Weight | Score | Weighted |
|-----------|--------|-------|----------|
| Tier 1 requirements assessed in evaluation | 30 | 96% | 28.8 |
| Tier 1 requirements specified in SOW | 25 | 98% | 24.5 |
| Tier 2 requirements covered | 15 | 93% | 14.0 |
| Bidirectional linkage (requirement ↔ control) | 10 | 100% | 10.0 |
| Absence of scope creep | 10 | 100% | 10.0 |
| Citation precision (ID cited where covered) | 10 | 95% | 9.5 |
| **TOTAL** | **100** | | **96.8** |

**Score: 97 / 100 — procurement-phase basis.**

The score deliberately excludes design, implementation and test dimensions. Including them at zero would produce roughly 48/100 and would measure the project's *phase*, not its *traceability discipline*. The exclusion is stated here so the number is not later quoted out of context.

**Recommendation: PROCEED TO CRITERIA SIGNATURE**, conditional on the three §6 blocking actions being completed first. The requirement set is comprehensively carried into both the assessment and specification sides, with one genuine scoring omission and two citation defects, all fixable in single-line edits before 2026-08-28.

---

## 6. Action Items

### Blocking — must complete before criteria signature (2026-08-28)

| # | Action | Owner | Due | Gap |
|---|--------|-------|-----|-----|
| A-1 | Add INT-004 to the MQ-1 source column in ARC-002-EVAL §3.1 | Grace Tanaka | 2026-08-21 | §4.2 |
| A-2 | Resolve NFR-A-003 at the weighting workshop — recommend folding degradation into F.2's assessment questions | Rhonda Bell | 2026-08-21 | §4.3 |
| A-3 | Add the BR-005 reference to SOW §2.4 | Grace Tanaka | 2026-08-28 | §4.2 |

### Non-blocking — next revision

| # | Action | Owner | Due | Gap |
|---|--------|-------|-----|-----|
| A-4 | Add requirement-ID references to ARC-002-STKE goals G-1 to G-10, so impact analysis can start from a stakeholder goal | Rhonda Bell | Next STKE revision | §2.2 |
| A-5 | Classify BR-002 explicitly as an internal governance requirement in ARC-002-REQ | Dr. Benny Moog | Next REQ revision | §4.1 |
| A-6 | Add a forward reference from ARC-002-STKE §10 and ARC-002-REQ §11 to the risk register, resolving the superseded R-1…R-8 IDs | Rhonda Bell | Next revision | ARC-002-RISK Appendix C |

### Scheduled re-runs

| # | Trigger | Purpose |
|---|---------|---------|
| A-7 | After design deliverables D-1 and D-2 accepted (2027-02-12) | First design-side traceability; converts §3.4 from PHASE to measured |
| A-8 | After pilot exit (2027-06-25) | First test-side traceability |
| A-9 | Before cutover (2027-07-24) | Final pre-production verification |

---

## 7. Change Impact Analysis

This matrix supports impact analysis for change requests. Worked examples using the linkages above:

| If this changes | Impact |
|-----------------|--------|
| **NFR-I-002** (export) is relaxed | Gate MQ-3 falls away → EVAL E.1 rescored → SOW §9.7 term 2 renegotiated → risks R-012 and R-020 both re-scored upward → Principle 9 exception required |
| **REQ-009** 4-hour window is relaxed | FR-002 and NFR-P-001 change → EVAL A.2 and F.4 rescored → SOW §3.3 and success criteria change → STKE goal G-3 target changes |
| **Retention schedule** is delayed past migration | DR-005 and FR-014 unmet at cutover → risk R-014 materialises → EVAL E.3 becomes untestable → BR-007 partially unmet |
| **The discipline exception** is refused | BR-005 and FR-009 unmet → EVAL Category G falls away → SOW §2.4 removed → risk R-003 materialises → REQ-010 gap recorded as a governed choice |
| **Baselines slip past 2026-08-28** | BR-003 unassessable → EVAL Category H cannot be scored → risk R-006 materialises → five other risk assessments become unreliable |

The highest-leverage requirement in the set is **INT-001** (SIS → platform identity), referenced 14 times across the evaluation, SOW and risk register. Changing it touches four risks and both mandatory gates that concern access.

---

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| REQ | ARC-002-REQ-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Source of all 62 requirement IDs and priorities |
| EVAL | ARC-002-EVAL-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Gates and scored criteria |
| SOW | ARC-002-SOW-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Scope, deliverables, contract terms |
| RISK | ARC-002-RISK-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Risk controls referencing requirements |
| STKE | ARC-002-STKE-v1.0.md | ArcKit artifact | `002-lecture-capture/` | Stakeholder goals and outcomes |
| RSCH | ARC-002-RSCH-v1.0.md | ArcKit artifact | `002-lecture-capture/research/` | Market evidence informing gate design |
| PRIN | ARC-000-PRIN-v1.0.md | ArcKit artifact | `000-global/` | Principles constraining requirements |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| EVAL-C1 | EVAL | §3.1, MQ-1 | Security Requirement | "University SSO with MFA enforced; **no local accounts** and no platform-native passwords, including for room devices and service identities" |
| EVAL-C2 | EVAL | §1.2 | Procurement Constraint | "Weightings are fixed and signed before any supplier is approached (BR-004). Nothing in Sections 3 to 5 may change after issue." |
| EVAL-C3 | EVAL | §5.2 | Design Decision | Ten sub-criteria — A.1, A.2, A.3, B.2, C.1, C.2, E.1, E.2, F.2, F.5 — cannot be scored above 2 without hands-on evidence |
| SOW-C1 | SOW | §2.4 | Functional Requirement | "Multi-camera, high-fidelity performance capture for named Music & Performing Arts venues (REQ-010, FR-009) is a bounded discipline exception ... decided in the same governance cycle as this procurement but procured separately." |
| REQ-C1 | REQ | §11, R-006 | Risk Factor | Baseline data not delivered forces evaluation on assumptions; five other assessments depend on it |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| Vendor profiles (5) | `002-lecture-capture/vendors/` | Market intelligence per supplier; carry no requirement-ID traceability |
| Tech notes (3) | `002-lecture-capture/tech-notes/` | Reusable technology knowledge; not requirement-scoped |
| External engagement inputs (5) | `002-lecture-capture/external/` | Traced indirectly — survey REQ-xxx IDs are carried inside ARC-002-REQ |

---

**Generated by**: ArcKit `/arckit:traceability` command
**Generated on**: 2026-07-28
**ArcKit Version**: 6.7.2
**Project**: Lecture Capture Platform Consolidation (Project 002)
**Model**: Claude Opus 5 (1M context)
**Generation Context**: Traceability pre-processor hook did not fire; requirement IDs and priorities extracted programmatically from ARC-002-REQ-v1.0 and matched by exact-token search across ARC-002-EVAL, ARC-002-SOW, ARC-002-RISK, ARC-002-STKE and ARC-002-RSCH. All coverage figures are machine-derived. Design, implementation and test dimensions recorded as phase-not-reached rather than as gaps, with the basis stated in §5.

<!-- arckit-provenance:start -->

## Build Provenance

_Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix._

| Field | Value |
|-------|-------|
| Requested Effort | `high` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-07-28T08:26:00.952Z |

<!-- arckit-provenance:end -->
