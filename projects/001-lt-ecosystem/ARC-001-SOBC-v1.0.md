# Strategic Outline Business Case (SOBC) — Learning & Teaching Ecosystem Rationalisation

> **Template Origin**: Official | **ArcKit Version**: 6.7.4 | **Command**: `/arckit:sobc`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-SOBC-v1.0 |
| **Document Type** | Strategic Outline Business Case (SOBC) |
| **Project** | Learning & Teaching Baseline Strategy (Project 001) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-28 |
| **Last Modified** | 2026-07-28 |
| **Review Cycle** | At each engagement milestone until the September submission |
| **Next Review Date** | 2026-08-27 |
| **Owner** | Prof. Otis Hammond, Deputy Vice-Chancellor (Education) — Senior Responsible Owner |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] — Operations Committee, on recommendation of Steering Committee |
| **Distribution** | University Executive; Steering Committee; Education Committee; Operations Committee; Digital & IT; Finance |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-28 | ArcKit AI | Initial creation from `/arckit:sobc` command — four-option appraisal at strategic-estimate depth | [PENDING] | [PENDING] |

## Document Purpose

This SOBC sets out the strategic case for investing in the rationalisation of the University of Funk's Learning & Teaching technology ecosystem. It is written to feed the **September 2026 business case** that the consultant engagement's WP9 roadmap is contracted to support [CB-C1].

**Two things about its position in the sequence should be understood before reading.**

**First, it is deliberately out of canonical order.** An SOBC normally precedes detailed requirements. Here, requirements (`ARC-001-REQ`), a risk register (`ARC-001-RISK`), a data model (`ARC-001-DATA`), two architecture decisions and a Wardley analysis already exist. That is an advantage — this case rests on completed architectural work rather than on estimates of what that work might find — but it changes the question being asked. The question is not *"should we start?"* It is:

> **Should the University fund the rationalisation programme that the 31 August roadmap will describe — and on what conditions?**

**Second, it deliberately does not contain a costed savings figure.** The licence-spend baseline that BR-002's central financial test depends on is a **WP3 output that does not yet exist** [RQ-C1]. Section B4 explains why manufacturing that figure now would make the business case weaker, not stronger, and Section F2 makes producing it a condition of approval rather than a task to be discovered in September.

---

## Executive Summary

**Purpose**: The University's Learning & Teaching technology ecosystem has grown organically over roughly a decade to **more than twenty tools across eight capability categories** [CT-C1]. The result is capability licensed more than once, integrations that fail silently, functionality paid for but never switched on, and an inconsistent experience for students who study across schools. This case seeks approval to fund a bounded, governed rationalisation of that estate.

**Problem Statement**: Four of the seven known integrations move personal information by manual re-keying or flat-file transfer [SL-C1]. Four of eight personal-information classes are disclosed offshore with no cross-border assessment completed. The estate sits largely at Essential Eight Maturity Level 1 against a Maturity Level 2 target for end 2027 [PC-C1]. **None of these are new problems** — they are long-standing estate conditions that this engagement has surfaced and measured for the first time.

**Proposed Solution**: Designate a primary platform for each of the eight capability categories, permit discipline-specific tooling at the edge under common standards, and replace the manual and batch integration estate with a governed, event-driven layer built on a canonical data model. Retire duplicated capability at contract renewal points rather than mid-term.

**Strategic Fit**: Directly delivers all six outcomes in `ARC-001-STKE` and is the executable form of the nineteen architecture principles endorsed as WP1.

**Investment Required (ROM, ±50%)**: **AUD $2.4M – $4.2M over three years** for the recommended option, of which roughly two thirds is one-off integration and governance investment and one third is recurring platform and support cost. See §D1 for the basis of estimate and §B4 for why this band is wide.

**Expected Benefits**: Qualitative at this stage, traced to **10 stakeholder goals and 6 outcomes**. Two are financially material but **cannot yet be quantified**: recurring licence savings from declared retirements, and avoided support effort from eliminated manual handling. Both depend on the WP3 baseline (§B4).

**Return on Investment**: **NPV, BCR and payback are deliberately not stated.** §B4 and §D4 explain the reasoning and set out what must exist before they can be. This is a proportionality judgement appropriate to SOBC stage, not an omission.

**Recommended Option**: **Option 2 — Bounded Consolidation with Integration Uplift.**

**Key Risks**:

1. **R-001** — the consolidation-versus-best-of-breed decision remains unresolved, and it gates the entire future state (residual 16; the highest-scoring strategic risk in the register)
2. **R-013 / R-014** — integration capital produces no licence saving in the same period, so a flat-spend test applied naively would reject the investment that fixes the compliance exposure
3. **R-007 / delivery capacity** — the University has previously built teaching-critical automation and failed to sustain it; control effectiveness for that is recorded as *"None effective"*

**Go/No-Go Recommendation**: **PROCEED — with four conditions (§F2).**

**Rationale**: The compliance exposures are live, predate the engagement, and are not discretionary. The rationalisation opportunity is real but unquantified. Proceeding on the compliance and integration case while making the savings case conditional on the WP3 baseline is the position the evidence actually supports — and it is more defensible to the Operations Committee than a confident number that cannot be substantiated.

**Next Steps if Approved**:

1. WP3 licence and capability baseline delivered — **21 August 2026** (Condition 1)
2. R-001 decided at RIFF with published criteria — **late August 2026** (Condition 2)
3. Roadmap submitted — **31 August 2026**
4. Business case submitted with costed positions — **September 2026**

---

# PART A: STRATEGIC CASE

## A1. Strategic Context

### A1.1 Problem Statement

**Current situation.** The ecosystem grew tool by tool, each acquisition reasonable at the time, none assessed against the estate as a whole. Eight capability categories are served by more than twenty tools [CT-C1]; three platforms deliver overlapping capture, delivery and collaboration capability with no declared boundary between them [SL-C2]. The RIFF governance process exists and is well designed, but it operates without a maintained capability map, so it assesses requests in isolation [SGP-C1].

**Specific pain points** (from `ARC-001-STKE` stakeholder drivers):

| Stakeholder | Driver | Pain point | Impact | Intensity |
|-------------|--------|-----------|--------|-----------|
| Cassandra Rhodes (CIO) | SD-2 | Fragile integration estate; Essential Eight target unreachable | Nightly batch means access state is wrong for up to 24 hours [PC-C2]; estate largely ML1 against ML2 target | **CRITICAL** |
| Vernon Ostinato (CFO) | SD-3 | Capability licensed more than once; functionality paid for and never configured | Unquantified — and the fact that it is unquantified is itself the finding | **HIGH** |
| Eleanor Frame (Privacy) | SD-11 | Sensitive placement information moves by manual re-keying and email [SL-C3] | Live APP 11 exposure; 3 of 29 risks exceed the proposed compliance appetite | **CRITICAL** |
| Prof. Priya Anand (Dean, Health) | SD-14 | Placement outcomes re-keyed by hand between systems | Error-prone; audit concerns; student fairness impact | **HIGH** |
| Sam Okafor (Integration) | SD-7 | Course cloning runs on undocumented scripts held by one person [SL-C4] | Single-person dependency at the busiest point in the academic calendar | **HIGH** |
| Dr. Wynton Castle (Academic) | SD-15 | Casual and sessional colleagues provisioned by manual CSV | Access arrives late in teaching period or persists after it ends | **HIGH** |
| Jazmin Field (Student Guild) | SD-16 | Inconsistent structure and unverified accessibility across schools | Cumulative cognitive cost, invisible to any single teaching team | **HIGH** |
| Prof. Desmond Key (Dean, Music) | SD-13 | Discipline tooling at risk from undifferentiated consolidation | Loss of performance capture and notation capability | **MEDIUM** |

**Consequences of inaction**, stated without inflation:

- **Compliance exposure persists and is now documented.** Four personal-information classes are disclosed offshore with no APP 8 assessment; sensitive placement data moves by hand. `ARC-001-RISK` rates R-017 and R-018 at residual 16 each, both exceeding the proposed compliance appetite of 9. **These conditions have existed for years. What has changed is that they are now written down** — which alters the University's position materially if a breach occurs.
- **The Essential Eight ML2 target for end 2027 is not reachable** on the current trajectory. Lab fleets and lecture-theatre capture appliances sit outside standard patching regimes [PC-C1].
- **Duplication continues to compound.** Every teaching period without declared boundaries adds configuration, training and support load to platforms that may later be retired.
- **The survey's credibility erodes.** 412 academics responded [RR-C1]. A consultation that visibly changes nothing depresses future response rates — a cost that is real, unbudgeted, and borne by the next engagement.

### A1.2 Strategic Drivers

**Link to stakeholder analysis**: every driver below is drawn from `ARC-001-STKE`, which analysed sixteen named internal stakeholders and four inferred external parties.

| Driver ID | Stakeholder | Type | Description | Strategic imperative |
|-----------|-------------|------|-------------|---------------------|
| SD-1 | Hammond (DVC-E) | STRATEGIC | A defensible L&T strategy that survives scrutiny | Institutional credibility |
| SD-2 | Rhodes (CIO) | OPERATIONAL | Eliminate integration fragility; reach ML2 | Risk reduction |
| SD-3 | Ostinato (CFO) | FINANCIAL | Contain licence spend | Cost discipline |
| SD-4 | Clavinet (Dean L&T) | STRATEGIC | Academic credibility of the architecture | Academic governance |
| SD-8 | Marimba (Academic Lead) | STRATEGIC | The survey must visibly matter | Consultation integrity |
| SD-10 | Ohm (Cybersecurity) | COMPLIANCE | Close security gaps | Regulatory posture |
| SD-11 | Frame (Privacy) | COMPLIANCE | APP compliance and breach readiness | Regulatory posture |
| SD-12 | Tanaka (Procurement) | FINANCIAL | Leverage at renewal | Commercial position |
| SD-16 | Field (Student Guild) | STRATEGIC | Consistency and accessibility | Student outcomes |

**Strategic alignment**:

- **Architecture principles** (`ARC-000-PRIN`) — this programme is the executable form of all nineteen. Principles 2 (Deliberate Capability Boundaries), 18 (Evidence-Based Capability Investment) and 19 (Realise Licensed Capability Before New Spend) are the three the investment most directly delivers.
- **RIFF governance** [SGP-C1] — the programme makes RIFF operable by giving it the evidence base it currently lacks.
- **Privacy Act 1988 and the Australian Privacy Principles** — the manual-flow remediation is simultaneously the fragility fix and the privacy fix. `ARC-001-STKE` records this as Synergy 2 and calls it *"the engagement's strongest cross-cutting argument"*.

### A1.3 Stakeholder Goals Addressed

All ten goals from `ARC-001-STKE`. **Every benefit in Part B traces to one of these.**

| Goal ID | Stakeholder | Goal | Current state | Target state |
|---------|-------------|------|---------------|--------------|
| G-1 | Clavinet, Hammond | Architecture principles agreed and academically endorsed | Drafted, pending endorsement | Endorsed by Education Committee |
| G-2 | Ostinato, Moog | Current landscape and capability baseline validated | Baseline map exists; not validated | Validated, with duplication quantified |
| G-3 | Rhodes, Okafor | Integration architecture and canonical model defined | ADR-001 and ADR-002 proposed | Accepted and being implemented |
| G-4 | Rhodes, Moog, Key | Contested platform decisions resolved through governance | **R-001 open** | Decided at RIFF with published criteria |
| G-5 | Marimba | Survey requirements mapped to capability with gaps quantified | Requirements typed; mapping pending WP3 | 35 of 35 mapped to a capability status |
| G-6 | Hammond, Bell | Rationalisation roadmap delivered to business case format | In progress | Delivered 31 August 2026 |
| G-7 | Ostinato, Tanaka | Licence spend held flat or reduced while closing Must gaps | **Baseline not established** | Costed position with renewal calendar |
| G-8 | Ohm, Rhodes | Security posture pathway to target maturity defined | Largely ML1 vs ML2 target | Documented pathway per strategy |
| G-9 | Frame, Anand | Privacy positions assessed and breach readiness established | 0 of 8 classes assessed | 8 of 8 assessed; NDB playbook tested |
| G-10 | Clavinet, Field | Accessibility conformance baseline established | Not systematically verified | All student-facing platforms assessed |

### A1.4 Scope

**In scope**:

- All eight L&T capability categories and the platforms serving them [CT-C1]
- The nine target-state integrations (INT-001 to INT-009), their architecture and their sequencing
- The canonical data model for student, course, enrolment and institutional role
- Privacy, security, accessibility and availability posture across the L&T estate
- Governance uplift — capability map, boundary register, RIFF evidence base

**Out of scope for this case**:

- **Delivery of the integrations themselves.** The architecture governing them is in scope; building them is the programme this case funds, sequenced in the WP9 roadmap [CB-C2]
- Non-L&T institutional systems except as integration counterparties (student information system, timetabling, HR)
- The lecture capture platform procurement, which is running separately as **Project 002** and consumes this programme's integration decisions
- Teaching-lab desktop fleet and lecture-theatre appliance estate, except where security maturity depends on them

**Assumptions** (full register at Appendix C):

1. **The WP3 capability and licence baseline can be produced by 21 August 2026.** If not, the financial case cannot be completed for September and the submission becomes a compliance-and-integration case only
2. Vendors supply capability, contract and roadmap data within the engagement timeline (risk R-011)
3. Contract renewal dates permit retirement without break costs (risk R-005, R-015)
4. No costing baseline exists today; every figure in Part B and Part D is an order-of-magnitude planning band, not a quotation

**Dependencies**:

- **Internal** — Education Committee endorsement of principles (G-1) gates WP7 and WP8; WP3 baseline gates the financial case
- **Cross-project** — Project 002's platform decision consumes ADR-001 and ADR-002; those decisions must be accepted before 002 can complete its integration design
- **External** — vendor cooperation on capability and contract data; HR capability to emit appointment events (ADR-002 assumption A-3, the largest open technical unknown)

### A1.5 Why Now?

**Urgency factors**:

- **31 August 2026** — the roadmap deadline is fixed and the September business case depends on it [CB-C1]
- **End 2027** — the Essential Eight ML2 target. A pathway not started in 2026 will not complete
- **Contract renewal calendar** — rationalisation is only executable at renewal points. Renewals missed in this cycle wait a full contract term (risk R-005)
- **Live compliance exposure** — R-017 and R-018 are open now, not at some future date, and both predate the engagement

**Opportunity cost of delay**: every teaching period without declared boundaries adds configuration and support load to platforms that may later be retired; every renewal signed without exit terms compounds the switching cost the programme exists to reduce (risk R-015, R-029).

**Window of opportunity**: the architectural work is done and paid for. Principles, requirements, risk register, data model, two decisions and a strategic map all exist. **The marginal cost of acting on that work now is far lower than the cost of reproducing it later**, and the analysis has a shelf life — the estate it describes is changing underneath it.

---

# PART B: ECONOMIC CASE

## B1. Critical Success Factors

Adopted from `ARC-001-STKE` §Critical Success Factors, which derived them from stakeholder analysis.

1. **CSF-1 — Principles endorsed before future-state work proceeds.** *Measure*: Education Committee endorsement recorded. *Threshold*: endorsed by mid-August 2026; WP7 and WP8 are both gated on it.
2. **CSF-2 — The consolidation decision is resolved through RIFF with published criteria, not deferred into the roadmap as ambiguity.** *Measure*: R-001 closed with a recorded decision. *Threshold*: decided before the roadmap is submitted.
3. **CSF-3 — Privacy and security findings shape platform decisions rather than invalidating them late.** *Measure*: PIA complete before platform decisions harden. *Threshold*: no platform decision ratified ahead of its privacy assessment.
4. **CSF-4 — The survey is visibly traceable into the recommendations.** *Measure*: proportion of the 35 source requirements mapped to a capability status. *Threshold*: 100%.
5. **CSF-5 — The 31 August deliverable is in the Executive's expected format.** *Measure*: format confirmed with Finance before drafting. *Threshold*: confirmed by 7 August 2026.

## B2. Options Analysis

> **Basis of estimate.** All costs are **Rough Order of Magnitude at ±50%**, expressed in **Australian dollars at 2026 prices**, derived from the scope in `ARC-001-REQ` and the integration architecture in ADR-001 — **not** from quotations, and **not** from a licence baseline, which does not yet exist. Benefit figures are deliberately absent for the reasons in §B4.

### Option 0: Do Nothing (Baseline)

**Description**: Retain the current arrangement — nightly batch, manual CSV provisioning, manual re-keying of placement grades, undocumented cloning scripts, undeclared platform overlap.

**3-year cost**: no incremental investment. Existing recurring licence and support spend continues at an **unmeasured** level, plus continued Learning Technologist effort absorbing manual workarounds.

**Stakeholder goals met**: **0 of 10.**

**Pros**: no investment, no delivery risk, staff know the current failure modes.

**Cons**:

- ❌ Fails BR-004, BR-005, BR-006 and BR-007 outright
- ❌ Leaves R-006, R-008, R-009, R-017 and R-018 unmitigated — three of these exceed the proposed appetite
- ❌ Essential Eight ML2 target becomes unreachable
- ❌ The architectural investment already made is written off
- ❌ Survey credibility damage crystallises (risk R-003)

**Recommendation**: **Reject.** Retained as a genuine baseline — the RIFF pause provision permits closing a request [SGP-C1] — but the evidence against it is the strongest of any option.

---

### Option 1: Compliance and Integration Remediation Only (Minimal)

**Description**: Fix what is broken and non-compliant. Do not rationalise the platform estate.

**Scope**: integration broker and canonical model per ADR-001; role authority per ADR-002; remediate INT-001 (SIS lifecycle) and INT-005 (placement grades); complete the PIA and APP 8 assessments; document the Essential Eight pathway; document and version-control the cloning automation. **No capability boundaries declared, no platforms retired.**

**3-year cost (ROM ±50%)**: **AUD $1.2M – $2.2M**

| Component | Band | Basis |
|-----------|------|-------|
| Integration broker licence/hosting, AU region | $240k – $450k | 3 years recurring; assumes managed service |
| Broker standing-up, schema registry, availability design | $250k – $400k | ADR-001 Phases 1–2 |
| INT-001 and INT-005 delivery | $300k – $550k | ADR-001 Phases 3–4 |
| Role authority service (ADR-002) | $200k – $400k | Composing service on the broker |
| PIA, APP 8 assessments, E8 pathway documentation | $120k – $250k | Specialist effort |
| Cloning automation remediation | $60k – $120k | R-007 treatment |

**Stakeholder goals met**: **5 of 10** — G-3, G-8, G-9 fully; G-1 and G-5 partially. **Not met**: G-2, G-4, G-6, G-7, G-10.

**Pros**: addresses every risk that exceeds the proposed appetite; lowest cost and delivery risk; no contested decisions required, so it can start immediately.

**Cons**: leaves the duplication that motivated the engagement entirely untouched; **BR-002's financial test is not even attempted**; R-001 stays open, so the future state remains ambiguous; the Executive receives a remediation bill with no offsetting position.

**Risks**: the Executive reasonably asks *"what did the strategy engagement produce?"* and the answer is a compliance programme.

---

### Option 2: Bounded Consolidation with Integration Uplift **(RECOMMENDED)**

**Description**: Everything in Option 1, plus designation of a primary platform per capability category with discipline tooling permitted at the edge under common standards, and retirement of declared duplication at contract renewal points.

This is the architectural outcome already reached independently by three methods: **Conflict C-1 Option 3** in the requirements, **Conflict 1 resolution** in the stakeholder analysis, and **`ARC-001-WARD-001` §2** on evolution grounds. Three routes, one answer.

**Scope**: Option 1 in full, plus — capability map and boundary register established and maintained; boundary decisions taken at RIFF with published criteria; retirement paths agreed and sequenced to the renewal calendar; baseline unit-site template and rollover automation; accessibility conformance baseline across student-facing platforms; RIFF operating on architectural evidence.

**3-year cost (ROM ±50%)**: **AUD $2.4M – $4.2M**

| Component | Band | Basis |
|-----------|------|-------|
| All Option 1 components | $1.2M – $2.2M | As above |
| Remaining integrations (INT-002, 003, 004, 006, 007, 009) | $500k – $900k | Marginal cost per integration falls on the broker |
| Capability map, boundary register, RIFF evidence base | $150k – $280k | Build plus first-year maintenance |
| Template, rollover automation, accessibility remediation | $300k – $550k | Student-experience workstream |
| Migration and retirement execution | $250k – $450k | Content and configuration migration at renewal points |
| Change management, training, academic engagement | $150k – $300k | Across the roadmap horizon |

**Stakeholder goals met**: **10 of 10** — with G-7 conditional on the WP3 baseline being produced.

**Benefits** — traced to stakeholder goals, qualitative at this stage:

| ID | Benefit | Goal | Outcome | Type | Quantifiable now? |
|----|---------|------|---------|------|-------------------|
| B-01 | Every capability category has a declared primary and boundary | G-2, G-4 | O-1 | STRATEGIC | ✅ Yes — 0 of 8 → 8 of 8 |
| B-02 | Manual steps eliminated from production flows carrying personal information | G-3 | O-2 | COMPLIANCE | ✅ Yes — 4 of 7 → 0 |
| B-03 | Recurring licence saving from declared retirements | G-7 | O-3 | FINANCIAL | ❌ **No — requires WP3 baseline** |
| B-04 | Avoided support effort from eliminated manual handling | G-3 | O-2 | FINANCIAL | ❌ **No — no effort baseline exists** |
| B-05 | Every personal-information class carries an assessed privacy position | G-9 | O-4 | COMPLIANCE | ✅ Yes — 0 of 8 → 8 of 8 |
| B-06 | Documented Essential Eight pathway for all eight strategies | G-8 | O-4 | COMPLIANCE | ✅ Yes — pathway exists or does not |
| B-07 | Casual and sessional staff provisioned on the automated path | G-3 | O-2 | OPERATIONAL | ✅ Yes — CSV loads → zero |
| B-08 | Single-person dependency on cloning automation removed | G-3 | O-2 | RISK | ✅ Yes — binary |
| B-09 | Student-facing platforms assessed for WCAG 2.2 AA | G-10 | O-5 | COMPLIANCE | ✅ Yes — coverage percentage |
| B-10 | RIFF assesses every request against maintained architectural evidence | G-1, G-4 | O-6 | STRATEGIC | ✅ Yes — 0% → 100% of requests |
| B-11 | 35 survey requirements visibly traced to recommendations | G-5 | O-5 | STRATEGIC | ✅ Yes — coverage percentage |
| B-12 | Platform substitution becomes tractable through the canonical model | G-3 | O-2 | STRATEGIC | ❌ No — realised at next renewal |

**Ten of twelve benefits are measurable today.** The two that are not are precisely the two financial ones — which is the honest shape of this case and the reason §B4 exists.

**Pros**: meets all ten goals; resolves R-001 rather than deferring it; addresses every appetite-exceeding risk; preserves discipline capability under Principle 4, which is what makes it acceptable to Key and Moog; converts the platform argument from advocacy into evidence.

**Cons**: requires the contested decision to actually be taken; larger change-management load; **retirement benefits are constrained by the renewal calendar**, so savings arrive later than costs (risk R-005, R-015); the delivery capacity concern in §E7 applies most strongly here.

---

### Option 3: Full Single-Platform Consolidation (Comprehensive)

**Description**: Consolidate collaboration, learning delivery and learning capture onto a single vendor platform, retiring the specialists. This is driver SD-2 taken to its conclusion.

**Scope**: Option 2 plus aggressive consolidation across categories, migration of all content and configuration onto the designated platform, and retirement of discipline-specific tooling where a general-purpose equivalent exists.

**3-year cost (ROM ±50%)**: **AUD $4.5M – $8.0M**, driven by migration at scale, parallel running through at least one full teaching period, and significantly higher change-management and academic-engagement effort.

**Stakeholder goals met**: **7 of 10** — strong on G-2, G-3, G-7, G-8; **fails G-1 and G-4** (Education Committee endorsement is unlikely where discipline capability is lost) and **fails G-5** in substance, because requirements REQ-005, REQ-006 and REQ-010 describe capability a general-purpose platform does not provide.

**Pros**: lowest steady-state support and security surface; clearest licence saving; simplest estate to govern.

**Cons**:

- ❌ **Loses performance capture and discipline notation capability** — REQ-010 and REQ-005/006 are unmet, and `ARC-001-WARD-001` §2 shows why: discipline tooling sits in a market too thin for general suppliers to serve
- ❌ **Directly opposed by two Deans** (SD-13, SD-14). `ARC-001-STKE` rates the resulting adoption risk as material
- ❌ Highest delivery risk and longest migration
- ❌ Concentrates the estate on one vendor at the point where Principle 9 (portability) is hardest to enforce

**Recommendation**: **Reject.** Not on cost — on capability loss and governability. Conflict C-1 examined this position as its Option 1 and reached the same conclusion.

---

### B2.5 Options Comparison

| Criterion | Option 0 | Option 1 | **Option 2** | Option 3 |
|-----------|----------|----------|-------------|----------|
| 3-year cost (ROM ±50%) | Nil incremental | $1.2M – $2.2M | **$2.4M – $4.2M** | $4.5M – $8.0M |
| Stakeholder goals met | 0 of 10 | 5 of 10 | **10 of 10** | 7 of 10 |
| Appetite-exceeding risks addressed | 0 of 5 | 5 of 5 | **5 of 5** | 5 of 5 |
| Resolves R-001 | ❌ | ❌ | ✅ | ✅ |
| BR-002 financial test attempted | ❌ | ❌ | ✅ conditional | ✅ |
| Discipline capability preserved | ✅ | ✅ | ✅ | ❌ |
| Education Committee endorsable | ❌ | ⚠️ Partial | ✅ | ❌ Unlikely |
| Delivery risk | None | Low | Medium | High |

## B3. Recommended Option

**Option 2 — Bounded Consolidation with Integration Uplift.**

**Rationale**:

1. **It is the only option meeting all ten stakeholder goals**, and the only one that both resolves R-001 and preserves the discipline capability two Deans are mandated to protect.
2. **Three independent methods reached its architecture.** The requirements conflict analysis, the stakeholder conflict analysis and the Wardley evolution analysis converged on *consolidate the general case, permit specialist tooling at the edge*. Convergence from different methods is the strongest evidence available in a decision of this kind.
3. **It addresses every risk exceeding the proposed appetite** while Option 1 does so more cheaply but leaves the strategy question open, and Option 3 does so at the cost of capability the survey explicitly requires.
4. **Its scope is executable at renewal points** rather than requiring mid-term contract breaks, which is what makes the savings realisable at all (risk R-005).

**Sensitivity at ±50%**: at the top of the band ($4.2M) Option 2 costs less than the *bottom* of Option 3's band ($4.5M). At the bottom ($2.4M) it is only marginally above the top of Option 1's band ($2.2M) while meeting twice as many goals. **The recommendation is not sensitive to where within the band the true cost falls** — which is a useful property of a case built on wide, honest ranges.

**Optimism bias**: UK Green Book supplementary guidance suggests uplifts of 40% or more for IT and software programmes. That figure is **UK-derived and not an institutional standard here**, but the underlying finding — that technology programmes are systematically under-estimated — is not jurisdiction-specific. Applying it as a benchmark gives an adjusted band of **AUD $3.4M – $5.9M**. The Steering Committee should decide whether to adopt this benchmark or substitute an institutional figure; **it should not be left implicit.**

## B4. Why This Case Contains No NPV, BCR or Payback Figure

This section exists because its absence would otherwise be read as an oversight.

**The missing input is specific and named.** `ARC-001-REQ` §Budget states: *"Not established at this stage. The engagement's WP3 capability mapping establishes the licence spend baseline"* [RQ-C1]. ADR-001 carries the same position as assumption A-1. `ARC-001-STKE` Outcome O-3 records the current value of its own KPI as *"Baseline to be established in WP3"*.

**The consequence is asymmetric, and the asymmetry matters.** Costs are estimable from scope — integration count, broker model, migration volume — which is why Part B carries ROM bands. **Benefits are not**, because the two financially material ones (B-03 licence saving, B-04 avoided support effort) are both differences against a baseline that has not been measured. A BCR would therefore be a ratio with a real numerator and an invented denominator.

**Three consequences follow, and each is actionable:**

1. **BR-002's central test is currently unfalsifiable.** *"Licence spend held flat or reduced"* cannot be evidenced without knowing current spend. Note that BR-002 is rated SHOULD, not MUST — the requirements author appears to have anticipated exactly this.
2. **The Jevons caution applies to the flat-spend assumption.** Commoditisation lowers unit prices and reliably raises total consumption. Expecting spend to hold flat *because* components are commoditising is backwards; flat spend will come from **declared retirements**, not falling prices. `ARC-001-WARD-001` §9 raises this independently.
3. **Integration capital produces no licence saving in the same period** (risks R-013, R-014). Presenting a single blended NPV would obscure this. `ARC-001-STKE` Conflict 2 already prescribes the fix: **separate recurring licence spend from one-off integration investment in the business case**, and this SOBC does so.

**What must exist before an OBC can carry an NPV:**

| Input | Owner | Needed by |
|-------|-------|-----------|
| Total ecosystem licence spend by platform and renewal date | Grace Tanaka → Vernon Ostinato | 21 August 2026 |
| Licensed-but-unconfigured capability, quantified | Dr. Benny Moog | 21 August 2026 |
| Support effort baseline for manual handling | Sam Okafor | September 2026 |
| University discount rate for internal appraisal | Vernon Ostinato | Before OBC |
| Institutional optimism-bias position | Steering Committee | Before OBC |

> **Note on discount rate.** HM Treasury's 3.5% Social Time Preference Rate is a **UK public-sector** rate. It is not automatically applicable to an Australian university, and Australian public-sector practice commonly applies materially higher real discount rates with sensitivity testing. **The rate must be set by University Finance before any NPV is calculated** — adopting the UK figure by default would be an unexamined assumption embedded at the foundation of the economic case.

---

# PART C: COMMERCIAL CASE

## C1. Procurement Strategy

### C1.1 Applicable Framework

> **UK procurement instruments do not apply.** The Digital Marketplace, G-Cloud, DOS, Crown Commercial Service frameworks, the mandatory 10% social value weighting and HM Treasury spending controls are **UK public-sector mechanisms with no standing for an Australian university**. This case substitutes the University's own **RIFF Review** process [SGP-C1], its Operations Committee and Executive approval thresholds, and Australian market conditions. Recording this explicitly prevents a reviewer reading the omission as a gap.

### C1.2 Market Assessment

| Component | Market position | Sourcing implication |
|-----------|----------------|---------------------|
| Integration broker / iPaaS | **Mature, multi-vendor, Product stage (~0.64)**, and moving toward commodity as hyperscalers bundle event brokering | Buy — but see the timing caution below |
| Learning platforms (8 categories) | **All Product or Commodity.** `ARC-001-WARD-001` §2 found mean differentiation pressure of 0.259 across the eight categories | Buy; no platform choice buys lasting advantage |
| Discipline specialist tooling | Product stage in a **thin market** — low ubiquity, high domain certainty | Buy; consolidation pressure does not apply |
| Role authority, canonical model, capability register | **Custom / Genesis** — no market supplies these | Build |
| Cloud hosting, SSO with MFA | Commodity | Consume as utility |

**Timing caution on the broker.** At evolution ~0.64 and moving to ~0.76 within 24 months, integration brokering is being absorbed into platform bundles. **Buying a differentiated broker product at that point in the evolution curve is the worst available timing** — which is precisely why ADR-001 Condition 1 requires the Principle 19 test on existing licensed capability before purchase. That condition is a strategic action, not a procedural hurdle.

### C1.3 Sourcing Route

**Recommended route**: competitive process under the University's own procurement policy, with RIFF assessment before any commitment [SGP-C1].

| Route | Pros | Cons | Recommendation |
|-------|------|------|----------------|
| Realise existing licensed capability | No new spend; strongest Principle 19 position | May not meet requirement; must be tested not assumed | **Test first (mandatory)** |
| Competitive tender | Best value, defensible, preserves buyer power | Time-consuming against a fixed deadline | **Accept where new capability is required** |
| Direct award | Fast | No competition; weak against RIFF duplication rule | Reject unless justified |
| Sector consortium (CAUDIT) | Aggregated leverage | Not investigated in this engagement | **Investigate — see below** |

> **Unexplored opportunity, flagged honestly.** No Australian sector purchasing agreement was investigated during this engagement. `ARC-001-WARD-001` §8 identifies **sector co-creation on the integration layer** as an available and unused play: every Australian university with a student information system, a timetabling system and an LMS faces an identical problem. This is not a recommendation to delay — it is a recommendation to ask CAUDIT the question before committing to a build.

### C1.4 Contract Approach

**Standing requirements at every renewal**, derived from risks R-015, R-028 and R-029 and from Principle 9. `ARC-001-RISK` §I is explicit that these *"should be standing requirements at every renewal, not project-specific asks"*:

1. **Verified export** in open, documented formats — demonstrated by test, not asserted in contract language (R-028 records export coverage as unverified for four platforms today)
2. **Termination assistance** obligations
3. **Australian data residency**, or a written statement of storage *and processing* locations sufficient to support an APP 8 assessment
4. **Institutional SSO with MFA** as a condition of adoption — no local accounts (R-019 records two current breaches)
5. **Published, versioned integration interfaces** conforming to the canonical model

**Sequencing to the renewal calendar** is the commercial mechanism that makes rationalisation executable. Building that calendar is a Condition 3 deliverable (§F2).

---

# PART D: FINANCIAL CASE

## D1. Budget Requirement

**Total investment sought (ROM ±50%)**: **AUD $2.4M – $4.2M over three years**, or **AUD $3.4M – $5.9M** with the optimism-bias benchmark applied (§B3).

Presented in the two categories that `ARC-001-STKE` Conflict 2 requires be kept separate:

### D1.1 One-off investment (integration, governance and migration)

| Item | Year 1 | Year 2 | Year 3 | Total band |
|------|--------|--------|--------|-----------|
| Broker standing-up, schema registry, availability design | $250k – $400k | — | — | $250k – $400k |
| Integration delivery (INT-001 to INT-009) | $350k – $600k | $450k – $850k | — | $800k – $1.45M |
| Role authority service (ADR-002) | $200k – $400k | — | — | $200k – $400k |
| Capability map, boundary register, RIFF evidence base | $100k – $180k | $50k – $100k | — | $150k – $280k |
| Template, rollover automation, accessibility remediation | $150k – $280k | $150k – $270k | — | $300k – $550k |
| Migration and retirement execution | — | $150k – $270k | $100k – $180k | $250k – $450k |
| PIA, APP 8, Essential Eight pathway | $120k – $250k | — | — | $120k – $250k |
| Change management, training, academic engagement | $70k – $140k | $50k – $100k | $30k – $60k | $150k – $300k |
| **Total one-off** | **$1.24M – $2.25M** | **$850k – $1.59M** | **$130k – $240k** | **$2.22M – $4.08M** |

### D1.2 Recurring cost change

| Item | Direction | Band | Note |
|------|-----------|------|------|
| Integration broker licence or hosting | **Increase** | $80k – $150k/year | New recurring cost; possibly nil if Principle 19 test succeeds |
| Broker and role authority operation | **Increase** | Absorbed within existing team, plus skills uplift | Assumes no new FTE — **to be validated** |
| Retired platform licences | **Decrease** | **Not quantifiable** | Requires WP3 baseline (§B4) |
| Manual handling effort | **Decrease** | **Not quantifiable** | No effort baseline exists |

> **This table is the honest core of the financial case.** Two lines increase and can be estimated. Two lines decrease and cannot. That asymmetry is not a drafting weakness — it is the actual state of the University's knowledge about its own estate, and correcting it is Condition 1.

## D2. Funding Source

- **One-off investment**: capital allocation, to be confirmed by the CFO. `ARC-001-RISK` R-014 identifies unfunded integration uplift as a live risk with residual score 8
- **Recurring cost change**: L&T operating budget, offset by retirements as they land
- **Approval path**: Steering Committee → Education Committee (academic endorsement) → Operations Committee → University Executive where financial or strategic thresholds are exceeded [SGP-C1]

> **Threshold gap, flagged.** The specific financial thresholds triggering Operations Committee versus University Executive approval are **not documented in any artifact available to this engagement**. The governance process names the escalation path but not the values [SGP-C1]. **The CFO should confirm the applicable threshold before the September submission** so the case is routed correctly first time.

## D3. Affordability

**Cannot be assessed at this stage, and the reason is precise.** Affordability is a ratio of programme cost to available budget. The programme cost band is stated in §D1; **the total L&T technology budget it must sit within has not been established** — the same WP3 gap.

What can be said:

- The **one-off investment is front-loaded** — 55% to 60% of the total falls in Year 1, which is the least convenient profile for a fixed capital allocation and should be modelled explicitly in the September submission
- The **recurring increase is small and bounded** ($80k–$150k/year for the broker), and may be nil if the Principle 19 test succeeds
- **Retirement savings arrive later than costs**, constrained by the renewal calendar (R-005) — so a naive year-one affordability test would reject a programme that is affordable across the horizon

**Assessment**: **To be confirmed** — deliberately, not evasively. Condition 1 makes producing the inputs a precondition of approval.

## D4. Financial Appraisal

**Deferred to OBC.** See §B4 for the full reasoning, the list of missing inputs with owners and dates, and the note on discount-rate selection.

**Value-for-money assessment, qualitative** (the appraisal depth appropriate to SOBC stage):

- **Economy** — competitive process with a mandatory Principle 19 test before any purchase; standing exit and export terms at every renewal
- **Efficiency** — marginal integration cost falls from linear to constant once the broker exists; composition logic implemented once rather than nine times (ADR-001, ADR-002)
- **Effectiveness** — 10 of 10 stakeholder goals met; 10 of 12 benefits measurable from day one

**Overall VfM rating**: **Medium-High**, with the qualification that the financial dimension of value for money **cannot be rated at all** until the baseline exists. A reviewer should treat any higher rating in a subsequent draft as evidence the baseline has landed, not as improved advocacy.

---

# PART E: MANAGEMENT CASE

## E1. Governance

### E1.1 Roles and Responsibilities

Derived from `ARC-001-STKE`.

| Decision / Activity | Responsible | Accountable | Consulted | Informed |
|--------------------|-------------|-------------|-----------|----------|
| Overall programme success | Rhonda Bell (PM) | **Prof. Otis Hammond (SRO)** | Steering Committee | All stakeholders |
| Funding approval | Vernon Ostinato (CFO) | Operations Committee | Steering Committee | University Executive |
| Academic endorsement of principles | Dr. Felix Marimba | A/Prof. Pearl Clavinet | Deans, Castle, Field | Academic community |
| Platform boundary decisions (R-001) | Dr. Benny Moog (RIFF) | A/Prof. Pearl Clavinet | Rhodes, Key, Anand, Moog | All stakeholders |
| Integration architecture | Sam Okafor | Cassandra Rhodes | Student Admin, HR, Ohm | Delivery team |
| Privacy and security posture | Eleanor Frame, Tobias Ohm | Cassandra Rhodes | Deans, Frame | OAIC-facing readiness |
| Contract strategy and renewals | Grace Tanaka | Vernon Ostinato | Moog, Rhodes | Vendors |
| Benefits realisation | Report owners per outcome | Prof. Otis Hammond (SRO) | Steering Committee | Executive |

**Senior Responsible Owner**: **Prof. Otis Hammond, Deputy Vice-Chancellor (Education)** — Executive Sponsor, chairs Steering, owns L&T strategy (driver SD-1).

**Steering Committee**: Hammond (chair), Rhodes (CIO), Clavinet (Dean L&T), Ostinato (CFO), with Bell as secretary. **Meets fortnightly** through the engagement.

> ⚠️ **Governance gap carried forward from ADR-002.** `ARC-001-DATA` records **Student Administration and Human Resources as joint business owners** of institutional role data, and E-001 Person's system of record as *"Student Information System / HR"*. **Neither function appears in the sixteen-name stakeholder register.** Both are required for the integration workstream and neither is currently represented in governance. Correcting the register is the first action in §F3.

### E1.2 Approval Gates

| Gate | Criteria | Approving body | Timing |
|------|----------|----------------|--------|
| **Gate 0: SOBC endorsed** | Strategic case accepted; conditions agreed | Steering Committee | August 2026 |
| **Gate 1: Baseline delivered** | WP3 licence and capability baseline complete | Steering Committee | 21 August 2026 |
| **Gate 2: R-001 decided** | Platform boundaries decided at RIFF with published criteria | RIFF → Education Committee | Late August 2026 |
| **Gate 3: Roadmap accepted** | WP9 roadmap delivered in business case format | Prof. Otis Hammond (SRO) | 31 August 2026 |
| **Gate 4: Business case approved** | Costed positions; funding allocated | Operations Committee / Executive | September 2026 |
| **Gate 5: ADR conditions satisfied** | ADR-001 and ADR-002 conditions met before build | Steering Committee | Q4 2026 |
| **Gate 6: Benefits review** | 12 months after first integration cutover | Steering Committee | Late 2027 |

## E2. Delivery Approach

**Phased, sequenced by risk rather than by convenience** — the sequencing `ARC-001-RISK` Finding 1 and ADR-001 Condition 3 both prescribe.

1. **Phase 0 — Conditions (Aug–Sept 2026)**: baseline delivered, R-001 decided, register corrected, Principle 19 test complete
2. **Phase 1 — Foundations (Q4 2026)**: broker confirmed or procured; canonical schema registered; role rules published and academically approved
3. **Phase 2 — Highest-leverage remediation (Q1–Q2 2027)**: INT-005 placement grades and INT-003 casual provisioning first. These close an operational, a compliance and a reputational risk simultaneously
4. **Phase 3 — Core lifecycle (Q2–Q3 2027)**: INT-001 SIS lifecycle, INT-002 role assignment
5. **Phase 4 — Rationalisation at renewal (2027–2028)**: retirements executed at contract renewal points
6. **Phase 5 — Sustainment (2028+)**: boundaries reviewed at each renewal via RIFF

> **No cutover in a teaching period.** Every phase boundary respects the academic calendar; assessment periods carry change freezes (NFR-A-001).

## E3. Key Milestones

| Milestone | Date | Depends on | Owner |
|-----------|------|-----------|-------|
| Business case format confirmed with Finance | 7 Aug 2026 | — | Rhonda Bell |
| Architecture principles endorsed | Mid-Aug 2026 | Validation workshops | A/Prof. Pearl Clavinet |
| **WP3 licence and capability baseline** | **21 Aug 2026** | Vendor data | Grace Tanaka, Dr. Benny Moog |
| Requirements mapped to capability status | Late Aug 2026 | Baseline | Dr. Felix Marimba |
| **R-001 decided at RIFF** | **Late Aug 2026** | Baseline; published criteria | Dr. Benny Moog |
| Privacy Impact Assessment complete | Late Aug 2026 | Vendor hosting data | Eleanor Frame |
| **Roadmap delivered** | **31 Aug 2026** | All of the above | Rhonda Bell |
| **Business case submitted** | **September 2026** | Roadmap accepted | Prof. Otis Hammond |
| First integration cutover (INT-005) | Q1 2027 | Funding; ADR conditions | Sam Okafor |
| Essential Eight ML2 target | End 2027 | Pathway execution | Tobias Ohm |

**Critical path**: WP3 baseline → R-001 decision → roadmap → business case. **Every item on it runs through the 21 August baseline.** A slip there propagates directly to the September submission with no float.

## E4. Resource Requirements

| Role | Source | Commitment | Note |
|------|--------|-----------|------|
| SRO | Internal (Hammond) | 0.1 FTE | Existing |
| Programme Manager | Internal (Bell) | 1.0 FTE | Existing through engagement; **extension beyond 31 Aug not yet secured** |
| Integration Architect | Internal (Okafor) | 1.0 FTE | Existing; **the single most concentrated dependency in the programme** |
| Integration engineers | To be sourced | 2–3 FTE | Skills gap — see below |
| Privacy and security specialists | Internal (Frame, Ohm) | 0.3 FTE each | Existing |
| Change and academic engagement | To be sourced | 0.5–1.0 FTE | Not currently resourced |
| Learning Technologists | Internal | Absorbed | Currently absorbing the manual workarounds this programme removes |

**Skills gap**: ADR-001 records that broker operation *"requires operational capability the AV/integration team does not currently hold — skills and on-call"*. Managed service reduces but does not remove this. **Skills uplift must be planned before first cutover, not after.**

## E5. Change Management

**Anticipated resistance**, from `ARC-001-STKE` conflict analysis:

| Source | Reason | Mitigation |
|--------|--------|-----------|
| Academic community | Rationalisation read as cost-cutting rather than improvement (R-002) | Principles expressed in student and teaching outcome terms; validation with Castle, Field and discipline representatives **before** committee |
| Deans of Music and Health | Fear of losing discipline capability (SD-13, SD-14) | Principle 4 protects discipline tooling **architecturally** — a stronger position than case-by-case advocacy, with the corresponding obligation that specialist tools meet common standards |
| Teaching staff | Template conformance reads as mandated rework (R-025) | **Deliver rollover automation before requesting conformance.** Make the compliant path the easiest path, not an audit |
| Finance | Integration capital yields no licence saving in-period (R-014) | Separate the two cost categories explicitly; sequence quick wins first |

**Change champions**: Dr. Wynton Castle (frontline academic voice) and Jazmin Field (Student Guild) are both LOW influence and HIGH interest — the classic champion profile. `ARC-001-STKE` Synergy 3 notes they appear opposed on templates but **align on outcome** if the intervention is framed as effort reduction rather than conformance.

## E6. Benefits Realisation

**Measurement framework** — taken directly from the outcome KPIs in `ARC-001-STKE`, so benefits are measured against definitions the stakeholders already own.

| Outcome | KPI | Current | Target | Report owner | Frequency |
|---------|-----|---------|--------|--------------|-----------|
| O-1 Bounded ecosystem | Capability categories with declared primary and boundary | 0 of 8 | 8 of 8 | Dr. Benny Moog | At milestones, then annually |
| O-2 Reliable integration | Production flows requiring a manual step | 4 of 7 | 0 | Sam Okafor | Monthly, then quarterly |
| O-3 Spend contained | Annual licence spend vs baseline | **Baseline pending WP3** | Flat or reduced | Grace Tanaka → Vernon Ostinato | Annually at budget |
| O-4 Privacy and security posture | Data classes assessed; strategies at ML2 | 0 of 8 assessed | 8 of 8; ML2 pathway documented | Eleanor Frame, Tobias Ohm | Quarterly |
| O-5 Consistent student experience | Template conformance; WCAG 2.2 AA verification | No template in force | Majority conformance; all platforms assessed | Dr. Benny Moog → Clavinet | Per teaching period |
| O-6 Governance prevents recurrence | Requests assessed against capability map before procurement | 0% (no evidence base) | 100% | Dr. Benny Moog | Per RIFF, reported quarterly |

**Accountability**: the SRO owns benefits realisation overall; each outcome has a named report owner drawn from the stakeholder analysis. **Benefits RAG status is a standing item at Steering.**

## E7. Risk Management

### E7.1 Top Strategic Risks

Drawn from `ARC-001-RISK` (29 risks; 5 exceeding the proposed appetite; **11 with no effective control today**).

| ID | Risk | Residual | Appetite | Mitigation | Owner |
|----|------|----------|----------|-----------|-------|
| R-018 | Sensitive placement data handled manually | **16** | ❌ Exceeds (9) | Sequence INT-005 first; escalate to Steering now | Eleanor Frame |
| R-017 | APP 8 offshore disclosures unassessed | **16** | ❌ Exceeds (9) | Complete PIA — **the cheapest score reduction available**, since the score reflects uncertainty not known harm | Eleanor Frame |
| R-008 | Placement grades re-keyed by hand | **16** | ❌ Exceeds (12) | INT-005 remediation | Prof. Priya Anand |
| R-001 | Consolidation decision unresolved | **16** | ❌ Exceeds (12) | **Hard decision deadline set to land immediately after the WP3 baseline** — see below | Prof. Otis Hammond |
| R-006 | Integration estate fragility | **15** | ❌ Exceeds (12) | ADR-001 broker; phased by failure cost | Cassandra Rhodes |
| R-013 | Licence spend cannot be held flat | 9 | ✅ Within | Quantify unconfigured capability before any acquisition | Vernon Ostinato |
| R-014 | Integration uplift unfunded | 8 | ✅ Within | Separate capital from recurring in the business case | Cassandra Rhodes |
| R-026 | Vendor platforms cannot support event-driven integration | 12 | ✅ Within | Assess interface capability per platform during WP3 | Sam Okafor |
| R-007 | Single-person dependency on cloning automation | 12 | ✅ Within | **Control effectiveness recorded as "None effective"** — document and version-control; train a second operator | Sam Okafor |
| R-009 | Casual provisioning by manual CSV | 12 | ✅ Within | ADR-002 role authority; INT-003 | Sam Okafor |

### E7.2 Three Risk Observations the Executive Should Read

**1. Three of the top five are the same defect.** R-008 (operational), R-018 (compliance) and the breach exposure in R-023 (reputational) all trace to one flow: placement outcomes moving between systems by hand. **Remediating INT-005 closes three risks at once.** It is the single highest-leverage action in the register and should be sequenced first regardless of what else the roadmap contains.

**2. R-001 is a decision risk with a sequencing fix.** It cannot be mitigated by more analysis. But `ARC-001-WARD-001` §6 found the reason it is stuck: the **capability map is the least evolved component in the entire landscape**, and it is what the decision depends on. The fix is therefore not "decide harder" but **set the decision deadline to land immediately after the WP3 baseline, and publish both dates together.**

**3. The register's own honesty is a governance asset.** `ARC-001-RISK` records that **no approved risk appetite statement exists** and marks its own thresholds PROVISIONAL. Every "exceeds appetite" judgement above is therefore an architectural recommendation, not a governance finding. **The Steering Committee should endorse the proposed thresholds or substitute institutional ones** — until then, the escalations have no formal trigger.

---

# PART F: RECOMMENDATION AND NEXT STEPS

## F1. Summary of Recommendation

| | |
|---|---|
| **Recommended option** | Option 2 — Bounded Consolidation with Integration Uplift |
| **Investment (ROM ±50%)** | AUD $2.4M – $4.2M over 3 years ($3.4M – $5.9M with optimism-bias benchmark) |
| **Stakeholder goals met** | 10 of 10 (G-7 conditional on the WP3 baseline) |
| **Benefits identified** | 12, of which 10 are measurable today |
| **Appetite-exceeding risks addressed** | 5 of 5 |
| **NPV / BCR / payback** | Deferred to OBC with stated reasons and named inputs (§B4) |
| **Affordability** | To be confirmed — pending the same baseline |
| **Go / No-Go** | **PROCEED, subject to four conditions** |

## F2. Conditions for Approval

1. **The WP3 licence and capability baseline is delivered by 21 August 2026.** Without it the financial case cannot be completed, BR-002's test cannot be evidenced, and the September submission becomes a compliance-and-integration case only. **This is the single most important condition in this document.**
2. **R-001 is decided at RIFF with published criteria, on a deadline set to land immediately after the baseline.** An unresolved platform question presented to the Executive invites it to be settled on cost, without pedagogical input — the outcome `ARC-001-RISK` §I explicitly warns against.
3. **A contract renewal calendar is produced and the roadmap sequenced against it.** Retirement decisions landing mid-term produce cost rather than saving (R-005). The calendar is what makes the savings realisable.
4. **The stakeholder register is corrected to include Student Administration and Human Resources**, and both are represented in governance before the integration workstream commits. Carried forward from ADR-002.

**Recommended (not mandatory) conditions**:

- Steering Committee endorses the proposed risk appetite thresholds, or substitutes institutional ones
- CFO confirms the Operations Committee versus Executive approval threshold
- CAUDIT is asked whether a sector agreement or shared integration effort exists, before committing to build

## F3. Next Steps if Approved

**Immediate (August 2026)**

1. Correct the stakeholder register; engage Student Administration and HR — **week commencing 4 August**
2. Confirm business case format with Finance — **7 August**
3. Run the Principle 19 test on existing licensed capability, **jointly for ADR-001 and ADR-002** — **by 21 August**
4. Deliver the WP3 baseline — **21 August**
5. Decide R-001 at RIFF — **late August**

**Roadmap and submission (August–September 2026)**

6. Deliver the WP9 roadmap in business case format — **31 August**
7. Submit the business case with costed positions — **September**

**Post-approval (Q4 2026 onward)**

8. Satisfy ADR-001 and ADR-002 conditions before build commences
9. Sequence INT-005 first — it closes three risks simultaneously
10. Produce the **OBC** once the baseline exists, carrying NPV, BCR and payback against a real denominator

## F4. If Not Approved

The compliance exposures do not go away. R-017 and R-018 both exceed the proposed appetite, both predate this engagement, and both are now documented — which changes the University's position materially if a breach occurs.

**If the full programme is not funded, the minimum defensible response is Option 1** (compliance and integration remediation only, AUD $1.2M – $2.2M). It addresses every appetite-exceeding risk while leaving the rationalisation question open. It is not a good outcome — it produces a remediation bill with no offsetting position — but it is a legitimate one, and it is materially better than Option 0.

**Option 0 should not be selected by default through inaction.** If it is chosen, it should be chosen explicitly, with the risk acceptances recorded and signed.

---

# APPENDICES

## Appendix A: Stakeholder Analysis Summary

**Source**: `ARC-001-STKE-v1.0.md` — 16 named internal stakeholders, 4 inferred external parties, 16 drivers, 10 goals, 6 outcomes, 5 conflicts, 5 synergies.

**Overall alignment**: **MEDIUM.** Strong agreement on the problem; genuine documented disagreement on the solution. The fault line is Conflict 1 (consolidation versus best-of-breed) and it is the subject of R-001.

**Compliance stakeholders hold effective veto.** Frame (Privacy) and Ohm (Cybersecurity) carry MEDIUM formal influence but can stop a platform decision late. CSF-3 exists to prevent that.

## Appendix B: Architecture Principles Alignment

**Source**: `ARC-000-PRIN-v1.0.md` — 19 principles.

| Principle | How this programme delivers it |
|-----------|-------------------------------|
| 2. Deliberate Capability Boundaries (CRITICAL) | Option 2's central mechanism — a declared primary per category |
| 4. Discipline Specialisation at the Edge | What makes Option 2 endorsable where Option 3 is not |
| 5. Single Source of Truth (CRITICAL) | ADR-002 resolves the outstanding case (institutional role) |
| 6. Canonical Data Model | Delivered as a WP5 output, consumed by every integration |
| 9. Data Portability and Exit | Standing contract requirement at every renewal (§C1.4) |
| 12. Automated Identity Lifecycle (CRITICAL) | The casual-provisioning defect this programme removes |
| 18. Evidence-Based Capability Investment (CRITICAL) | RIFF operating on a maintained capability map — Outcome O-6 |
| 19. Realise Licensed Capability Before New Spend | Condition on every acquisition in this programme |

## Appendix C: Assumptions Register

| # | Assumption | Impact if invalid |
|---|-----------|-------------------|
| A-1 | WP3 baseline deliverable by 21 August 2026 | Financial case incomplete; submission reduces to Option 1 scope |
| A-2 | No costing baseline exists today; all figures are ROM planning bands | Inherited from ADR-001 A-1. The option *ranking* is robust to this (§B3) |
| A-3 | Vendors supply capability and contract data in time (R-011) | WP3 delayed; A-1 fails |
| A-4 | Renewal dates permit retirement without break costs (R-005, R-015) | Savings deferred by up to a full contract term |
| A-5 | Broker operation absorbed within existing team plus skills uplift | New FTE required; recurring cost rises |
| A-6 | HR can associate appointments with unit offerings (ADR-002 A-3) | Role authority design changes; ADR-002 fallback applies |
| A-7 | Programme Manager available beyond 31 August 2026 | Delivery continuity at risk between engagement end and programme start |

## Appendix D: Benefits Not Yet Quantifiable

| ID | Benefit | Missing input | Owner | Needed by |
|----|---------|--------------|-------|-----------|
| B-03 | Recurring licence saving from retirements | Total spend by platform and renewal date | Grace Tanaka | 21 Aug 2026 |
| B-04 | Avoided support effort from eliminated manual handling | Support effort baseline | Sam Okafor | September 2026 |
| B-12 | Platform substitution tractability | Realised at next renewal; not measurable in-programme | Grace Tanaka | 2028 |

## Appendix E: Risk Register Reference

**Full register**: `ARC-001-RISK-v1.0.md` — 29 risks, 32% inherent-to-residual reduction, 5 exceeding proposed appetite, 11 with no effective control. §E7 above carries the strategic subset.

## Appendix F: Glossary

| Term | Definition |
|------|------------|
| SOBC / OBC / FBC | Strategic Outline / Outline / Full Business Case — successive stages with increasing cost accuracy |
| ROM | Rough Order of Magnitude — a planning band, not a quotation. Used at ±50% throughout |
| APP | Australian Privacy Principles, Privacy Act 1988 (Cth) |
| NDB | Notifiable Data Breach scheme, Privacy Act Part IIIC |
| Essential Eight / ML1, ML2 | ASD mitigation strategies and maturity levels |
| RIFF | Review of Innovation, Fit & Function — the University's solution governance gate |
| SRO | Senior Responsible Owner |
| WP1–WP9 | Consultant engagement work packages |
| Jevons paradox | Efficiency gains raise total consumption rather than reducing spend (§B4) |

---

## Document Approval

| Name | Role | Signature | Date |
|------|------|-----------|------|
| Prof. Otis Hammond | Deputy Vice-Chancellor (Education) — SRO | | [PENDING] |
| Vernon Ostinato | Chief Financial Officer | | [PENDING] |
| Cassandra Rhodes | Chief Information Officer | | [PENDING] |
| A/Prof. Pearl Clavinet | Chair, Education Committee | | [PENDING] |
| Operations Committee | Approving body | | [PENDING] |

**Approval decision**: [PENDING] — APPROVED / APPROVED WITH CONDITIONS / REJECTED / DEFERRED

**Next review**: 2026-08-27, or on delivery of the WP3 baseline, whichever is earlier

---

**END OF STRATEGIC OUTLINE BUSINESS CASE**

*Structured on the HM Treasury Green Book five-case model. UK-specific instruments — Digital Marketplace, G-Cloud, DOS, the 10% social value weighting, HMT spending controls and the 3.5% STPR discount rate — have been **replaced** with the applicable Australian and institutional equivalents rather than left nominally answered. Where a UK-derived benchmark is used (optimism bias), it is labelled as such.*

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| STKE | ARC-001-STKE-v1.0.md | ArcKit artifact | `001-lt-ecosystem/` | 16 stakeholders, 16 drivers, 10 goals, 6 outcomes, 5 conflicts — the mandatory source for every benefit |
| REQ | ARC-001-REQ-v1.0.md | ArcKit artifact | `001-lt-ecosystem/` | BR/FR/NFR/INT/DR requirements; Budget section; Conflict C-1 |
| RISK | ARC-001-RISK-v1.0.md | ArcKit artifact | `001-lt-ecosystem/` | 29 risks; appetite analysis; §I business case integration |
| DATA | ARC-001-DATA-v1.0.md | ArcKit artifact | `001-lt-ecosystem/` | Canonical model; joint ownership of role data |
| ADR1 | ARC-001-ADR-001-v1.0.md | ArcKit artifact | `001-lt-ecosystem/decisions/` | Integration mediation; Principle 19 condition |
| ADR2 | ARC-001-ADR-002-v1.0.md | ArcKit artifact | `001-lt-ecosystem/decisions/` | Role authority; HR engagement gap |
| WARD | ARC-001-WARD-001-v1.0.md | ArcKit artifact | `001-lt-ecosystem/wardley-maps/` | Evolution positioning; Jevons caution; capability-map finding |
| PRIN | ARC-000-PRIN-v1.0.md | ArcKit artifact | `000-global/` | 19 architecture principles |
| CB | consultant-brief.md | Engagement brief | `001-lt-ecosystem/external/` | WP1–WP9 scope, 31 August deadline, September business case |
| SL | system-landscape.md | Foundation artifact | `001-lt-ecosystem/external/` | Tool inventory; seven integrations and their failure modes |
| PC | privacy-context.md | Compliance input | `001-lt-ecosystem/external/` | 8 PI classes; APP 8 triggers; Essential Eight self-assessment |
| RR | requirements-register.md | Requirements input | `001-lt-ecosystem/external/` | 35 consolidated survey requirements; 412 respondents |
| SGP | solution-governance-process.md | Foundation artifact | `000-global/policies/` | RIFF Review process, roles, escalation path, duplication rule |
| CT | capability-taxonomy.md | Foundation artifact | `000-global/external/` | Eight capability categories |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| CB-C1 | CB | §2, WP9 | Business Requirement | "The final deliverable. Synthesises all findings into prioritised recommendations and a sequenced delivery roadmap, structured to feed directly into the September business case." |
| CB-C2 | CB | §2, WP5 | Business Requirement | "Delivery of these integrations is out of scope; the architecture governing them is in scope." |
| CT-C1 | CT | Header and table | Business Requirement | "Eight capability categories define the learning & teaching technology ecosystem. Every current and proposed tool is categorised against this taxonomy to enable cross-system comparison, duplication analysis and rationalisation decisions." |
| SL-C1 | SL | Known integrations | Risk Factor | "PeopleSoft → Blackboard ... Nightly batch flat-file / Fragile; role assignment failures; no intra-day sync" |
| SL-C2 | SL | Notes, item 1 | Design Decision | "MS Teams — investigation planned for 2027 to establish a seamless platform experience across collaboration, learning delivery and lecture capture (overlaps with Zoom and Echo360 — key rationalisation candidate)." |
| SL-C3 | SL | Known integrations | Risk Factor | "Sonia ↔ Blackboard grades (placements) / Manual re-keying / Error-prone; audit concerns" |
| SL-C4 | SL | Known integrations | Risk Factor | "Course cloning automation / Semi-manual scripts / Undocumented; single-person dependency" |
| PC-C1 | PC | §3 | Compliance Constraint | Essential Eight self-assessment: target "ML2 across the SaaS-heavy L&T estate by end 2027"; application control ML0, patch applications ML1, patch operating systems ML1 — "Lecture-theatre capture appliances behind" |
| PC-C2 | PC | §2 | Compliance Constraint | "Flat-files at rest on shared storage; stale de-provisioning (access persists up to 24h after withdrawal)" |
| RR-C1 | RR | Header | Stakeholder Need | "Consolidated requirements from the 2026 academic survey (412 responses across all schools)." |
| RQ-C1 | REQ | §Budget, Cost Estimate | Business Requirement | "Not established at this stage. The engagement's WP3 capability mapping establishes the licence spend baseline, and the WP9 roadmap produces the costed rationalisation position that feeds the September business case. Cost figures are therefore an output of this engagement rather than an input to these requirements." |
| SGP-C1 | SGP | Rules and Roles | Procurement Constraint | "Solutions duplicating capability already licensed (per the system landscape map) must justify why the incumbent tool is unsuitable."; escalation path Education Committee → Operations Committee / University Executive |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| stakeholders.md | `001-lt-ecosystem/external/` | Superseded by ARC-001-STKE, which is the artifact of record and the mandatory source for this business case |
| ARC-002 artifacts | `002-lecture-capture/` | Project 002 is a separate procurement consuming this programme's integration decisions. Including its costs here would double-count; it is referenced as a dependency in §A1.4 only |

---

**Generated by**: ArcKit `/arckit:sobc` command
**Generated on**: 2026-07-28
**ArcKit Version**: 6.7.4
**Project**: Learning & Teaching Baseline Strategy (Project 001)
**Model**: Claude Opus 5 (1M context)
**Generation Context**: Four-option appraisal at strategic-estimate depth, per user direction. Every benefit traced to one of the ten stakeholder goals in ARC-001-STKE; benefit measurement adopts the outcome KPIs from that document verbatim so success is measured against definitions stakeholders already own. NPV, BCR and payback deliberately omitted with reasoning and named missing inputs at §B4 — the licence-spend baseline is a WP3 output that does not yet exist, and ARC-001-REQ §Budget states so explicitly. Costs are ROM bands at ±50% in AUD, derived from scope rather than quotation. UK Green Book five-case structure retained; UK-specific procurement instruments, social value weighting, spending thresholds and the 3.5% STPR discount rate replaced with Australian and institutional equivalents.

<!-- arckit-provenance:start -->

## Build Provenance

*Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix.*

| Field | Value |
|-------|-------|
| Requested Effort | `max` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-07-28T10:56:00.788Z |

<!-- arckit-provenance:end -->
