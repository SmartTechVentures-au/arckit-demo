# Requirements Traceability Matrix — L&T Ecosystem

> **Template Origin**: Official | **ArcKit Version**: 6.7.4 | **Command**: `/arckit:traceability`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-TRAC-v1.0 |
| **Document Type** | Requirements Traceability Matrix |
| **Project** | Learning & Teaching Baseline Strategy (Project 001) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-28 |
| **Last Modified** | 2026-07-28 |
| **Review Cycle** | On delivery of the WP3 capability baseline, then at each engagement milestone |
| **Next Review Date** | 2026-08-27 |
| **Owner** | Dr. Felix Marimba, Academic Lead (Digital Learning) — requirements custodian, BR-008 owner |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Project Team; Steering Committee; Digital & IT; Education Committee |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-28 | ArcKit AI | Initial creation from `/arckit:traceability` command — 64 requirements traced against eight governing artifacts | [PENDING] | [PENDING] |

## Document Purpose

This matrix traces all 64 requirements in `ARC-001-REQ-v1.0` forward to the architectural artifacts that govern them, and backward to the stakeholder goals and survey requirements they originate from.

> **Read the scope statement in §1.2 before reading the coverage figures.** This project has **no HLD, no DLD, no vendor proposals, no source code and no tests** — and that is correct, not a defect. The consultant brief states plainly: *"Delivery of these integrations is out of scope; the architecture governing them is in scope"* [CB-C1]. A conventional Requirement → Design → Code → Test matrix would report near-zero coverage on three of its four columns and would be actively misleading. This matrix traces what exists.

---

## 1. Overview

### 1.1 Purpose

Three questions, each with a named owner:

1. **Is every requirement governed by something?** — architectural completeness
2. **Does every requirement originate somewhere legitimate?** — no invented scope
3. **Did the 412-response survey visibly change the outcome?** — BR-008, owned by Dr. Felix Marimba, and a stated credibility risk (R-003)

### 1.2 Traceability Scope

**Traced dimensions** (what this project has):

| Dimension | Direction | Artifacts |
|-----------|-----------|-----------|
| Requirement → governing architecture | Forward | ADR-001, ADR-002, DIAG-001, WARD-001, DATA, RISK, SOBC |
| Requirement → stakeholder goal and outcome | Backward | STKE (via `Traces To` lines in REQ) |
| Requirement → survey source | Backward | requirements-register.md (via `Source Ref` lines) |

**Untraced dimensions, and why**:

| Dimension | Status | Reason |
|-----------|--------|--------|
| Requirement → HLD component | ❌ Absent | No HLD exists. Delivery is out of engagement scope [CB-C1] |
| Requirement → DLD module | ❌ Absent | No DLD exists. Same reason |
| Requirement → source code | ❌ Absent | Nothing is built. The roadmap this engagement produces is what schedules the build |
| Requirement → test case | ❌ Absent | No test artifacts. Acceptance criteria exist in REQ but no test cases have been written |

**This is a strategy engagement, and the matrix is scoped to match.** Reporting "0% test coverage" would be arithmetically true and analytically worthless. §5 explains how the score handles this.

### 1.3 Document References

| Artifact | Role in this matrix |
|----------|--------------------|
| `ARC-001-REQ-v1.0` | Source of all 64 requirement IDs, priorities and source references |
| `ARC-001-STKE-v1.0` | Backward target — 10 goals, 6 outcomes |
| `ARC-001-DATA-v1.0` | Governing artifact — 20 canonical entities |
| `ARC-001-RISK-v1.0` | Governing artifact — 29 risks |
| `ARC-001-ADR-001-v1.0` | Governing artifact — integration mediation |
| `ARC-001-ADR-002-v1.0` | Governing artifact — role authority |
| `ARC-001-DIAG-001-v1.0` | Governing artifact — integration container view |
| `ARC-001-WARD-001-v1.0` | Governing artifact — evolution positioning and sourcing |
| `ARC-001-SOBC-v1.0` | Governing artifact — investment case |
| `requirements-register.md` | Backward target — 35 survey requirements REQ-001 to REQ-035 |

**Method note**: the traceability pre-processor hook did not fire for this invocation, so requirement extraction, artifact scanning and coverage computation were performed by script over the eight artifacts above. Reference detection is by exact requirement-ID match, which is conservative — a requirement discussed by name but not by ID counts as uncovered.

---

## 2. Traceability Matrix

### 2.1 Forward Traceability — Business Requirements (8)

| Req ID | Requirement | Priority | Governed by | Status |
|--------|-------------|----------|-------------|--------|
| BR-001 | Deliberately bounded capability ecosystem | MUST | WARD-001, DATA | ✅ Covered |
| BR-002 | Licence spend held flat or reduced while Must gaps close | SHOULD | ADR-001, ADR-002, WARD-001, DATA, RISK, SOBC | ✅ Covered |
| BR-003 | Baseline strategy and roadmap delivered to business case timing | MUST | ADR-001, ADR-002 | ✅ Covered |
| BR-004 | Integration fragility and manual handling eliminated | MUST | ADR-001, ADR-002, DIAG-001, WARD-001, SOBC | ✅ Covered |
| BR-005 | Demonstrable privacy and security posture | MUST | ADR-002, SOBC | ✅ Covered |
| BR-006 | Consistent and accessible student experience | MUST | WARD-001, SOBC | ✅ Covered |
| BR-007 | Governance operating on architectural evidence | MUST | ADR-001, ADR-002, WARD-001, DATA, SOBC | ✅ Covered |
| BR-008 | Survey requirements traceable to outcomes | MUST | WARD-001 | ✅ Covered — and discharged by this document |

**Business coverage: 8/8 (100%).**

### 2.2 Forward Traceability — Functional Requirements (22)

The **Canonical entity** column is the finding. See §4.1.

| Req ID | Requirement | Priority | Canonical entity | Governed by | Status |
|--------|-------------|----------|-----------------|-------------|--------|
| FR-001 | Course template authoring and reuse | MUST | E-007 UNIT_SITE | DATA | ✅ Covered |
| FR-002 | Interactive content authoring without specialist skills | SHOULD | — | — | ❌ **Orphan** |
| FR-003 | Centrally managed reading lists with copyright compliance | MUST | — | — | ❌ **Orphan** |
| FR-004 | Single supported video toolchain | MUST | — | — | ❌ **Orphan** |
| FR-005 | Music notation and audio-production materials | SHOULD | — | — | ❌ **Orphan** |
| FR-006 | Clinical simulation with device integration | MUST | — | — | ❌ **Orphan** |
| FR-007 | Single entry point for students | MUST | E-007 UNIT_SITE | DATA | ✅ Covered |
| FR-008 | Live online classes on one primary platform | MUST | — | — | ❌ **Orphan** |
| FR-009 | Automatic lecture capture and publication | MUST | E-009 RECORDING | DATA | ✅ Covered |
| FR-010 | Multi-camera and high-fidelity performance capture | COULD | E-009 RECORDING | DATA | ✅ Covered |
| FR-011 | Peer review with anonymised marking | SHOULD | — | — | ❌ **Orphan** |
| FR-012 | In-class polling and formative checks | SHOULD | — | — | ❌ **Orphan** |
| FR-013 | Group collaboration linked to enrolment groups | MUST | — | — | ❌ **Orphan** |
| FR-014 | Automatic group provisioning from timetable allocation | MUST | E-008 GROUP_ALLOCATION | DATA | ✅ Covered |
| FR-015 | Whole-of-program portfolio with export on graduation | MUST | E-013 PORTFOLIO_ARTEFACT | DATA | ✅ Covered |
| FR-016 | Similarity and AI-writing detection | MUST | E-010, E-011 | DATA | ✅ Covered |
| FR-017 | Secure examination on-campus and remote | MUST | E-010 ASSESSMENT_ITEM | DATA | ✅ Covered |
| FR-018 | Single-entry placement assessment | MUST | E-014, E-015, E-016 | DATA | ✅ Covered |
| FR-019 | Micro-credentials and badging | COULD | — | — | ❌ **Orphan** |
| FR-020 | Cohort engagement and at-risk dashboard | SHOULD | E-017 ENGAGEMENT_EVENT | DATA | ✅ Covered |
| FR-021 | Single platform for teaching evaluation | MUST | — | — | ❌ **Orphan** |
| FR-022 | Learning analytics export to the institutional data platform | SHOULD | E-017 ENGAGEMENT_EVENT | DATA | ✅ Covered |

**Functional coverage: 11/22 (50%) — the project's only material gap.**

### 2.3 Forward Traceability — Non-Functional Requirements (17)

| Req ID | Requirement | Priority | Governed by | Status |
|--------|-------------|----------|-------------|--------|
| NFR-P-001 | Change propagation latency | MUST | ADR-001, ADR-002, DIAG-001, WARD-001, DATA, RISK | ✅ Covered |
| NFR-P-002 | Lecture capture publication latency | MUST | DATA | ✅ Covered |
| NFR-A-001 | Availability during teaching periods | MUST | ADR-001, ADR-002, DIAG-001, DATA, RISK, SOBC | ✅ Covered |
| NFR-A-002 | Change control aligned to the academic calendar | MUST | DATA | ✅ Covered |
| NFR-S-001 | Peak load capacity | SHOULD | DATA | ✅ Covered |
| NFR-SEC-001 | Authentication via institutional SSO with MFA | MUST | ADR-002, DIAG-001, WARD-001, DATA, RISK | ✅ Covered |
| NFR-SEC-002 | Essential Eight maturity alignment | MUST | ADR-001, ADR-002, DIAG-001, WARD-001, DATA | ✅ Covered |
| NFR-SEC-003 | Automated identity lifecycle | MUST | ADR-001, ADR-002, DIAG-001, DATA | ✅ Covered |
| NFR-C-001 | Privacy Act 1988 compliance | MUST | ADR-001, WARD-001, DATA | ✅ Covered |
| NFR-C-002 | Cross-border disclosure assessment (APP 8) | MUST | ADR-001, WARD-001, DATA | ✅ Covered |
| NFR-C-003 | Audit logging for academic and access records | MUST | ADR-001, ADR-002, DIAG-001, DATA | ✅ Covered |
| NFR-U-001 | Navigation consistency | MUST | WARD-001, DATA, RISK | ✅ Covered |
| NFR-U-002 | Accessibility conformance | MUST | DATA | ⚠️ Covered — thinly, see §4.3 |
| NFR-M-001 | Integration observability | MUST | ADR-001, ADR-002, DIAG-001, WARD-001, DATA | ✅ Covered |
| NFR-M-002 | Reproducible and documented automation | MUST | ADR-001, ADR-002, DIAG-001, WARD-001 | ✅ Covered |
| NFR-I-001 | Published, versioned interfaces | MUST | ADR-001, DIAG-001 | ✅ Covered |
| NFR-I-002 | Data portability and exit | SHOULD | ADR-001, DATA, RISK | ✅ Covered |

**Non-functional coverage: 17/17 (100%).**

### 2.4 Forward Traceability — Integration Requirements (9)

| Req ID | Requirement | Priority | Governed by | Status |
|--------|-------------|----------|-------------|--------|
| INT-001 | SIS to learning platform | CRITICAL | ADR-001, ADR-002, DIAG-001, WARD-001, DATA, RISK, SOBC | ✅ Covered |
| INT-002 | Institutional role assignment | CRITICAL | ADR-001, ADR-002, DIAG-001, WARD-001, DATA, RISK, SOBC | ✅ Covered |
| INT-003 | Automated platform provisioning | CRITICAL | ADR-002, DIAG-001, WARD-001, DATA, RISK, SOBC | ✅ Covered |
| INT-004 | Course cloning and rollover | HIGH | ADR-001, ADR-002, DIAG-001, WARD-001, DATA | ⚠️ Covered — mechanism undecided, ADR-003 candidate |
| INT-005 | Placement management to LMS gradebook | CRITICAL | ADR-001, DIAG-001, WARD-001, DATA, RISK, SOBC | ✅ Covered |
| INT-006 | Timetable allocation to collaboration groups | HIGH | DIAG-001, WARD-001, DATA | ✅ Covered |
| INT-007 | Institutional hierarchy synchronisation | MEDIUM | DIAG-001, DATA | ✅ Covered |
| INT-008 | Sandpit environment provisioning | LOW | DIAG-001, DATA | ⚠️ Covered — shown as a stated omission; not yet designed |
| INT-009 | Learning analytics to institutional data platform | MEDIUM | ADR-001, DIAG-001, WARD-001, DATA, SOBC | ✅ Covered |

**Integration coverage: 9/9 (100%).** All nine appear in the container diagram; INT-004 and INT-008 carry documented caveats rather than silent gaps.

### 2.5 Forward Traceability — Data Requirements (8)

| Req ID | Requirement | Priority | Governed by | Status |
|--------|-------------|----------|-------------|--------|
| DR-001 | Canonical data model for core academic entities | MUST | ADR-001, ADR-002, DIAG-001, WARD-001, DATA | ✅ Covered |
| DR-002 | Institutional role as a governed entity | MUST | ADR-001, ADR-002, DIAG-001, WARD-001, DATA | ✅ Covered |
| DR-003 | Personal information classification and inventory | MUST | ADR-001, DATA | ✅ Covered |
| DR-004 | Sensitive information handling — placement records | MUST | ADR-001, DIAG-001, WARD-001, DATA | ✅ Covered |
| DR-005 | Data residency register | MUST | ADR-001, DIAG-001, WARD-001, DATA, RISK | ✅ Covered |
| DR-006 | Analytics minimisation and retention | SHOULD | DIAG-001, WARD-001, DATA | ✅ Covered |
| DR-007 | Institutional data export on termination | SHOULD | DATA | ✅ Covered |
| DR-008 | Student portfolio portability | MUST | DATA | ✅ Covered |

**Data coverage: 8/8 (100%).**

### 2.6 Backward Traceability

**Requirement → stakeholder goal → outcome.** All eight business requirements carry explicit `Traces To` lines, and between them they reach **all 10 goals and all 6 outcomes** in `ARC-001-STKE`.

| Req ID | Goal(s) | Outcome |
|--------|---------|---------|
| BR-001 | G-2, G-4 | O-1 Bounded ecosystem |
| BR-002 | G-7 | O-3 Spend contained |
| BR-003 | G-6 | — (engagement delivery) |
| BR-004 | G-3 | O-2 Reliable integration |
| BR-005 | G-8, G-9 | O-4 Demonstrable posture |
| BR-006 | G-1, G-10 | O-5 Consistent experience |
| BR-007 | G-4 | O-6 Governance persists |
| BR-008 | G-5 | — (traceability itself) |

**Goal coverage: 10/10. Outcome coverage: 6/6. No orphan goals, no orphan outcomes.**

**Requirement → survey source.** All 64 requirements carry a `Source Ref`. **52 originate in the survey register; 12 are marked `Derived`** — from architecture principles, the privacy and security context, or the current-state assessment. The `Derived` label is what stops the engagement overstating the survey's actual scope, and it is used honestly.

**All 35 source requirements REQ-001 to REQ-035 are referenced.** BR-008's success criterion — *"100% of the 35 source requirements mapped"* — is met at the requirement level. It is **not** yet met at the recommendation level, which is a WP7 and WP9 deliverable.

---

## 3. Coverage Analysis

### 3.1 Overall

| Metric | Value |
|--------|-------|
| Requirements declared | **64** |
| Governed by at least one artifact | **53 (83%)** |
| Orphan requirements | **11 (17%)** — all Functional |
| Design-only references (scope creep) | **0** |
| Backward trace to stakeholder goals | **100%** of BRs; 10/10 goals; 6/6 outcomes |
| Backward trace to survey source | **100%** — 64/64 carry a Source Ref; 35/35 REQ-xxx referenced |

### 3.2 Coverage by Category

| Category | Covered | Total | % | Assessment |
|----------|---------|-------|---|------------|
| Business | 8 | 8 | **100%** | ✅ |
| **Functional** | **11** | **22** | **50%** | ❌ **The gap** |
| Non-Functional | 17 | 17 | **100%** | ✅ |
| Integration | 9 | 9 | **100%** | ✅ |
| Data | 8 | 8 | **100%** | ✅ |

### 3.3 Coverage by Priority

| Priority | Covered | Total | % | Threshold | Result |
|----------|---------|-------|---|-----------|--------|
| MUST_HAVE | 36 | 42 | 86% | 100% | ❌ **6 short** |
| SHOULD_HAVE | 7 | 11 | 64% | > 80% | ⚠️ **Below** |
| COULD_HAVE | 1 | 2 | 50% | < 50% acceptable | ✅ |
| CRITICAL (INT) | 4 | 4 | 100% | 100% | ✅ |
| HIGH (INT) | 2 | 2 | 100% | — | ✅ |
| MEDIUM (INT) | 2 | 2 | 100% | — | ✅ |
| LOW (INT) | 1 | 1 | 100% | — | ✅ |

**Every requirement rated CRITICAL is covered.** The six uncovered MUST_HAVE requirements are all Functional, and §4.1 explains why that is not the defect it appears to be.

### 3.4 Coverage by Governing Artifact

| Artifact | Requirements referenced | Role |
|----------|------------------------|------|
| `ARC-001-DATA` | **46** | The dominant governing artifact — see §4.1 |
| `ARC-001-WARD-001` | 26 | Strategic positioning and sourcing |
| `ARC-001-ADR-001` | 25 | Integration mediation |
| `ARC-001-DIAG-001` | 24 | Integration container view |
| `ARC-001-ADR-002` | 19 | Role authority |
| `ARC-001-RISK` | 11 | Risk treatment |
| `ARC-001-SOBC` | 11 | Investment case |
| `ARC-001-STKE` | **0** | ⚠️ See below |

> **On STKE referencing zero requirement IDs.** This is not a defect. `ARC-001-STKE` predates `ARC-001-REQ` and works in drivers, goals and outcomes rather than requirement IDs. The link exists and is complete — it simply runs the other way, via the `Traces To` lines in REQ (§2.6). A matrix that only scanned forward would have recorded a false gap here.

---

## 4. Gap Analysis

### 4.1 🔍 The functional gap is an entity-boundary artefact, not an architecture defect

The 11 uncovered requirements are all Functional. The explanation is exact, and it survives checking:

> **Every one of the 11 covered functional requirements is covered through a canonical data entity. Every one of the 11 orphans has no entity.** The correspondence is 1:1 with no exceptions.

| Covered FR | Entity |
|-----------|--------|
| FR-001, FR-007 | E-007 UNIT_SITE |
| FR-009, FR-010 | E-009 RECORDING |
| FR-014 | E-008 GROUP_ALLOCATION |
| FR-015 | E-013 PORTFOLIO_ARTEFACT |
| FR-016, FR-017 | E-010 ASSESSMENT_ITEM, E-011 SUBMISSION |
| FR-018 | E-014, E-015, E-016 PLACEMENT_* |
| FR-020, FR-022 | E-017 ENGAGEMENT_EVENT |

**What the orphans have in common**: reading lists, video authoring, music notation, clinical simulation, live classes, peer review, polling, collaboration spaces, badging, teaching evaluation. Each produces an artefact that **stays inside a vendor platform and never becomes an institutional record**. There is no entity for them because there is correctly no entity for them.

**So coverage here tracks the canonical model's entity boundary, not requirement importance.** These 11 are not architectural gaps. They are **capability-assessment gaps** — the question they raise is *"which platform does this, and is it configured?"*, which is precisely WP3 capability mapping and WP7 requirements mapping.

**They close on the same critical path everything else does.** `ARC-001-SOBC` §F2 Condition 1 identifies the WP3 baseline, due **21 August 2026**, as the single most important condition in the programme. It is also what closes this gap. **One deliverable, two consequences** — which strengthens the case for protecting that date.

**Severity: MEDIUM, not CRITICAL.** Re-rating would be warranted if WP3 slips.

### 4.2 ✅ Zero scope creep

**No requirement ID appears in any governing artifact that is absent from `ARC-001-REQ`.** Every BR, FR, NFR, INT and DR cited across two ADRs, a diagram, a Wardley map, a data model, a risk register and a business case resolves to a declared requirement.

For a project where six substantial artifacts were produced across several sessions by different commands, this is a meaningful discipline result. It means no architectural decision has quietly invented scope.

### 4.3 ⚠️ Thinly-covered requirements — governed by exactly one artifact

Seven requirements are referenced by only one artifact. Single-artifact coverage is coverage, but it is fragile — if that artifact changes, the requirement has no second anchor.

| Req | Priority | Sole governing artifact | Comment |
|-----|----------|------------------------|---------|
| BR-008 | MUST | WARD-001 | Discharged by this document; re-check at next revision |
| NFR-P-002 | MUST | DATA | Lecture capture latency — sits primarily in project 002 |
| NFR-A-002 | MUST | DATA | Change control against the academic calendar — no ADR addresses it |
| NFR-U-002 | MUST | DATA | **Accessibility conformance.** Rated MUST, carries legal weight, and no architectural artifact addresses it beyond a data-model mention |
| NFR-S-001 | SHOULD | DATA | Peak load — reasonable to defer |
| DR-007 | SHOULD | DATA | Export on termination |
| DR-008 | MUST | DATA | Portfolio portability |

**NFR-U-002 is the one worth acting on.** Accessibility is a MUST requirement with legal and ethical weight (Principle 14), it is Goal G-10 and Outcome O-5, the SOBC counts it as benefit B-09 — and no ADR, diagram or map governs it. It is currently held by a data-model reference and a stakeholder goal. **That is thinner than its priority warrants.**

### 4.4 ⚠️ Two integration requirements carry documented caveats

Both are covered, both are honest, neither is silent:

- **INT-004 (course cloning and rollover, HIGH)** — appears in four artifacts, but the *mechanism* is undecided. `ARC-001-ADR-001` lists it as an ADR-003 candidate; `ARC-001-DIAG-001` renders it as an edge label rather than a container. Risk R-007 records the current control effectiveness as **"None effective"**.
- **INT-008 (sandpit provisioning, LOW)** — `ARC-001-REQ` records it as *"planned for 2027, not yet designed"*, and the diagram states its omission explicitly rather than drawing an undesigned flow.

### 4.5 ❌ No test dimension exists — structurally, and correctly

No test artifacts exist for this project. Requirements carry acceptance criteria in Given/When/Then form — **all 64 do** — but no test case has been written against them, because nothing is built.

**This is not a gap to fix now.** It becomes one the moment delivery starts. The acceptance criteria already in `ARC-001-REQ` are the raw material; converting them into a test specification is a delivery-phase activity, and should be a condition on the first integration cutover rather than an engagement deliverable.

---

## 5. Traceability Score

**Score: 89 / 100**

Weighted across the dimensions that apply to a strategy engagement. **The implementation and test dimensions are excluded from the denominator, not scored as zero** — including them would produce a number that measures the project's stage rather than its quality.

| Dimension | Weight | Result | Points |
|-----------|--------|--------|--------|
| Requirement → governing architecture | 40 | 53/64 = 83% | 33.1 |
| MUST-priority coverage | 25 | 36/42 = 86% | 21.4 |
| Backward trace to stakeholder goals and outcomes | 15 | 100% | 15.0 |
| Scope discipline — no design-only references | 10 | 100% | 10.0 |
| Backward trace to survey source (BR-008) | 10 | 100% | 10.0 |
| **Total** | **100** | | **89.5 → 89** |

**Assessment: STRONG.** Backward traceability is complete in both directions, scope discipline is clean, and every CRITICAL requirement is governed. The single deduction of consequence is the functional gap, which §4.1 shows is a scheduling artefact rather than an architecture defect.

**Recommendation: PROCEED.** The architecture is traceable and the requirements are legitimate. Two conditions:

1. **Re-run this matrix after the WP3 baseline lands (21 August)** — the 11 functional orphans should close, and if they do not, the gap is real and the severity re-rates upward.
2. **Give NFR-U-002 (accessibility) an architectural home** before the roadmap is submitted. §4.3 refers.

---

## 6. Action Items

### Before the 31 August roadmap

| ID | Action | Owner | Severity | Due |
|----|--------|-------|----------|-----|
| T-1 | Deliver the WP3 capability baseline; map the 11 orphan FRs to a capability status (met / partial / duplicated / unmet) | Grace Tanaka, Dr. Benny Moog | **MEDIUM** | 2026-08-21 |
| T-2 | Give NFR-U-002 accessibility conformance an architectural artifact — an ADR on conformance verification, or explicit treatment in the WP8 target state | A/Prof. Pearl Clavinet with Dr. Benny Moog | **MEDIUM** | 2026-08-31 |
| T-3 | Re-run this matrix once WP3 lands and re-issue as v1.1 | Dr. Felix Marimba | LOW | 2026-08-25 |

### Before delivery commences

| ID | Action | Owner | Severity | Due |
|----|--------|-------|----------|-----|
| T-4 | Raise ADR-003 for course cloning and rollover; INT-004's mechanism is undecided and R-007 has no effective control | Sam Okafor | **MEDIUM** | Q4 2026 |
| T-5 | Convert the acceptance criteria in `ARC-001-REQ` into a test specification; make it a condition on first integration cutover | Sam Okafor | LOW | Before Phase 2 |
| T-6 | Design INT-008 sandpit provisioning, or formally defer it with a review date | Sam Okafor | LOW | 2027 |

**No blocking items.** Nothing in this matrix should stop the roadmap being submitted on 31 August.

---

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| REQ | ARC-001-REQ-v1.0.md | ArcKit artifact | `001-lt-ecosystem/` | Source of all 64 requirement IDs, priorities, source refs and traces-to lines |
| STKE | ARC-001-STKE-v1.0.md | ArcKit artifact | `001-lt-ecosystem/` | Backward target — 10 goals, 6 outcomes |
| DATA | ARC-001-DATA-v1.0.md | ArcKit artifact | `001-lt-ecosystem/` | 20 canonical entities; the dominant governing artifact |
| RISK | ARC-001-RISK-v1.0.md | ArcKit artifact | `001-lt-ecosystem/` | R-003, R-007 |
| ADR1 | ARC-001-ADR-001-v1.0.md | ArcKit artifact | `001-lt-ecosystem/decisions/` | Integration mediation |
| ADR2 | ARC-001-ADR-002-v1.0.md | ArcKit artifact | `001-lt-ecosystem/decisions/` | Role authority |
| DIAG | ARC-001-DIAG-001-v1.0.md | ArcKit artifact | `001-lt-ecosystem/diagrams/` | Integration container view |
| WARD | ARC-001-WARD-001-v1.0.md | ArcKit artifact | `001-lt-ecosystem/wardley-maps/` | Evolution positioning |
| SOBC | ARC-001-SOBC-v1.0.md | ArcKit artifact | `001-lt-ecosystem/` | Investment case; WP3 critical path |
| CB | consultant-brief.md | Engagement brief | `001-lt-ecosystem/external/` | Scope boundary — delivery out of scope |
| RR | requirements-register.md | Requirements input | `001-lt-ecosystem/external/` | 35 survey requirements REQ-001 to REQ-035 |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| CB-C1 | CB | §2, WP5 | Business Requirement | "Delivery of these integrations is out of scope; the architecture governing them is in scope. Depends on WP4 and WP1." |
| RR-C1 | RR | Header | Stakeholder Need | "Consolidated requirements from the 2026 academic survey (412 responses across all schools)." |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| privacy-context.md, system-landscape.md | `001-lt-ecosystem/external/` | Inform the requirements themselves rather than the traceability between them; cited in REQ, ADRs and the diagram |
| stakeholders.md | `001-lt-ecosystem/external/` | Superseded by ARC-001-STKE, which carries the goals and outcomes traced here |
| capability-taxonomy.md | `000-global/external/` | Capability categorisation is the WP3 instrument that will close §4.1; not itself a traceability target |

---

**Generated by**: ArcKit `/arckit:traceability` command
**Generated on**: 2026-07-28
**ArcKit Version**: 6.7.4
**Project**: Learning & Teaching Baseline Strategy (Project 001)
**Model**: Claude Opus 5 (1M context)
**Generation Context**: The traceability pre-processor hook did not fire for this invocation, so requirement extraction, artifact scanning and coverage computation were performed by script over `ARC-001-REQ` and eight governing artifacts, with reference detection by exact requirement-ID match. Scope deliberately excludes HLD, DLD, implementation and test dimensions, none of which exist for this engagement — the consultant brief places delivery out of scope, so a conventional four-column matrix would misreport project stage as project quality. The §4.1 entity-boundary finding was verified by mapping each covered functional requirement to its canonical entity in `ARC-001-DATA`; the correspondence is 1:1 across all 22 functional requirements with no exceptions.

<!-- arckit-provenance:start -->

## Build Provenance

*Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix.*

| Field | Value |
|-------|-------|
| Requested Effort | `high` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-07-28T11:18:28.774Z |

<!-- arckit-provenance:end -->
