# Consultant Engagement Brief — Learning & Teaching Baseline Strategy

**The University of Funk** | June 2026 | Draft — *fictional demonstration document*

| | |
|---|---|
| **Engagement type** | Solution Architecture |
| **Due date** | 31 August 2026 |

## 1. Background & context

The University of Funk (UoF) is undertaking a Learning & Teaching Baseline Strategy to
understand and rationalise its digital learning technology ecosystem. An academic survey
has been completed; the consolidated requirements derived from that survey are provided
as an input (`requirements-register.md`). The Solution Architect (SA) is **not** required
to gather or manage requirements — they are applied architecturally.

Foundation artifacts already produced by the internal team are provided as baseline
inputs, not work to be reproduced:

- **Capability taxonomy** — eight categories with descriptions (`capability-taxonomy.md`)
- **System categorisation map** — current tools mapped to the taxonomy with usage status
  (`system-landscape.md`)
- **L&T Technology Solution governance process** — the RIFF review and approval flow
  (`solution-governance-process.md`)

## 2. Scope of work

The engagement runs from immediate commencement through to 31 August 2026. The nine work
packages below are sequenced to reflect dependencies — WP1–WP4 can begin in parallel,
with later packages depending on their outputs.

### WP1 — Architecture Principles

Define the governing principles for the learning technology ecosystem. These underpin
all subsequent design decisions and must be agreed before future-state work proceeds.

- Establish principles covering: LMS role and boundaries, integration approach,
  platform governance, student experience consistency
- Validate with key stakeholders

*Start immediately. Must be agreed before WP7 and WP8 proceed.*

### WP2 — Current Landscape Update

Using the existing system categorisation map as the baseline, validate and update the
current L&T technology landscape.

- Confirm active tools, contract status and usage against the existing map
- Incorporate any changes since the baseline was produced
- Produce an updated landscape diagram

*Runs in parallel with WP3 and WP4.*

### WP3 — System Capability Mapping

Map the detailed functionality of each tool against a standardised capability framework.
Prioritise systems with the project team before beginning. For each system capture:

- Functionality currently configured and in use, covered by current contract
- Standardised capability categories to enable cross-system comparison and duplication
  analysis
- Functionality paid for but not configured or in use
- Functionality available at additional cost (optional — confirm with project team)
- Vendor roadmap features due within 12 months at current contract cost

*Runs in parallel with WP2 and WP4. System prioritisation agreed with the project team
before mapping begins.*

### WP4 — Integration Landscape Assessment

Produce a baseline view of the current integration landscape across all systems.
Essential context for WP5 and the recommendations.

- Document all current integrations: source, target, method and data flows
- Identify fragility, gaps, manual workarounds and duplication
- Understand existing IT plans and roadmap for each tool and integration
- Assess the **PeopleSoft → Blackboard** integration in detail: user and course
  lifecycle logic, institutional role assignment, known failures and gaps

*The SA works with the internal Integration Architect throughout. Findings feed WP5.*

### WP5 — Integration Architecture

Working with the internal Integration team, define the integration architecture
governing how all current and future integrations are designed. The SA documents the
architecture; the internal team contributes technical knowledge and owns delivery.

- Define integration patterns and standards — event-driven, API, batch — and where
  each applies
- Define a canonical data model for key entities: student, course, enrolment
- Document the target integration architecture for the known integrations:
  - PeopleSoft → Blackboard: user lifecycle, course lifecycle, institutional role
    assignment
  - Echo360 user provisioning
  - Course cloning automation
  - Institutional hierarchy updates
  - Allocate+ → Blackboard group creation
  - Sonia ↔ Blackboard grades integration (placements)
  - Sandpit provisioning (2027)
- Identify gaps between current state (WP4) and target architecture

*Delivery of these integrations is out of scope; the architecture governing them is in
scope. Depends on WP4 and WP1.*

### WP6 — Architecture Decisions Register

Work across WP2–WP5 will surface decisions that must be made before the future state can
be finalised.

- Document decisions as they emerge, with options, implications and recommended approach
- Examples: Echo360 vs Microsoft Stream; Teams scope and provisioning model;
  integration pattern standards
- Present to the appropriate governance forum (RIFF review) for resolution

*Running document throughout Phase 1 — finalised before WP7 proceeds.*

### WP7 — Requirements Mapping

Map the academic survey requirements to the system capability data from WP3.
Workshop-based with project team support.

- Map requirements to existing system functionality
- Identify gaps, duplication and underutilisation

*Depends on WP3 being sufficiently progressed and the requirements register.*

### WP8 — High-Level Future State

Define the target state for the learning technology ecosystem, grounded in WP1
principles and informed by WP2–WP7 findings.

- Overall ecosystem view: platform positioning, boundaries and integration approach
- LMS-level view: how Blackboard Ultra sits within the broader ecosystem
- Identify what changes, what is rationalised and what gaps require investment

*Depends on WP1, WP5, WP6 and WP7.*

### WP9 — Recommendations & Roadmap

The final deliverable. Synthesises all findings into prioritised recommendations and a
sequenced delivery roadmap, structured to feed directly into the September business case.

**Recommendations:** tool rationalisation and consolidation; cost optimisation from
unused or duplicated capability; capability gaps requiring investment; integration
uplift priorities (from WP4/WP5); risks — fragility, overlap, underutilisation.

**Roadmap:** sequence all recommended platform changes and integration uplifts across a
delivery horizon; show dependencies, phasing and approximate timing; distinguish quick
wins from strategic investments; align to the business case structure.

*Depends on WP8.*

## 3. Work package sequence

| WP | Work Package | Depends on | Timing |
|----|--------------|-----------|--------|
| WP1 | Architecture Principles | — | Start immediately |
| WP2 | Current Landscape Update | — | Start immediately |
| WP3 | System Capability Mapping | — | Start immediately |
| WP4 | Integration Landscape Assessment | — | Start immediately |
| WP5 | Integration Architecture | WP1, WP4 | Once WP4 complete |
| WP6 | Architecture Decisions Register | WP2–WP5 (running) | Throughout Phase 1 |
| WP7 | Requirements Mapping | WP3, requirements register | Once WP3 progressed |
| WP8 | High-Level Future State | WP1, WP5, WP6, WP7 | Final weeks |
| WP9 | Recommendations & Roadmap | WP8 | Final output — Aug 2026 |

## 4. Assumptions

- Consolidated survey requirements are provided to the SA — the SA does not administer
  the survey or maintain the requirements register
- Foundation artifacts (taxonomy, system map, governance process) are provided at
  commencement
- The Integration team is available to support WP4 and WP5 throughout
- The project team facilitates vendor access for capability and roadmap data
- A system prioritisation session with the project team is held in week one
