# Stakeholder Drivers & Goals Analysis: Inventory & Warehouse Management Uplift

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:stakeholders`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-STKE-v1.0 |
| **Document Type** | Stakeholder Drivers & Goals Analysis |
| **Project** | Inventory & Warehouse Management Uplift (Project 001) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-06-29 |
| **Last Modified** | 2026-06-29 |
| **Review Cycle** | Quarterly |
| **Next Review Date** | 2026-09-29 |
| **Owner** | Nathan Dyke, CEO — Cycle Motion (Executive Sponsor) |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Cycle Motion leadership (Nathan & Kirralee Dyke), Order & Supply Chain team, solution architecture advisor |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-06-29 | ArcKit AI | Initial creation from `/arckit:stakeholders` command, using `stakeholders.md` and the company brief | PENDING | PENDING |

---

## Executive Summary

### Purpose

This document identifies the key stakeholders in Cycle Motion's inventory and warehouse management uplift, their underlying drivers (motivations, concerns, pressures), how those drivers become measurable goals, and the outcomes that will prove the goals are met. It provides traceability from individual concerns to project success metrics so requirements and design decisions can be prioritised around what stakeholders actually care about.

### Key Findings

Cycle Motion is a small, owner-led business: two executive sponsors (Nathan Dyke, CEO; Kirralee Dyke, COO) and a five-person Order & Supply Chain team carry the entire operation [STK-C1][STK-C2][STK-C3]. Alignment on the *problem* is strong — everyone feels the pain of manual re-keying across five B2C stores and the oversell risk from stock that is never synced in real time [CB-C2][CB-C3]. The genuine tension is over the *solution*: the CEO's pull toward the fastest, lowest-cost, least-disruptive move versus the strategically stronger but riskier "inventory hub" architecture, and the operations team's understandable wariness of automation that touches their roles.

### Critical Success Factors

- The single source of inventory truth decision (Path 1 vs Path 2) is made and documented **before** any product is selected [CB-C1].
- Manual re-keying and oversell are demonstrably eliminated, not merely reduced [CB-C2][CB-C3].
- The five-person operations team is engaged as process experts and reassured about their roles, so they become champions rather than resisters [STK-C3].
- Delivery is de-risked by piloting one channel with real data and explicitly testing the duplicate-order and oversell failure modes before any full cutover [CB-C5].

### Stakeholder Alignment Score

**Overall Alignment**: MEDIUM-HIGH

Stakeholders agree strongly on the problem and the desired end state. The MEDIUM element is solution-level: an unresolved CEO-vs-strategic tension on Path 1 (low disruption) versus Path 2 (single hub, larger change), and latent change-resistance risk in the operations team. Both are resolvable through an explicit, evidence-led, phased approach.

---

## Stakeholder Identification

### Internal Stakeholders

| Stakeholder | Role/Department | Influence | Interest | Engagement Strategy |
|-------------|----------------|-----------|----------|---------------------|
| Nathan Dyke | CEO — Strategic Sponsor [STK-C1] | HIGH | HIGH | Manage Closely — strategic decisions, investment sign-off, source-of-truth and vendor approval |
| Kirralee Dyke | COO — Operational Sponsor [STK-C2] | HIGH | HIGH | Manage Closely — process design, day-to-day decisions, primary contact for current workflows |
| Order & Supply Chain Team (5 staff) | Operations / end users [STK-C3] | MEDIUM | HIGH | Keep Informed & actively involve — discovery interviews, process mapping, pilot testing, training |

### External Stakeholders

| Stakeholder | Organization | Relationship | Influence | Interest |
|-------------|--------------|--------------|-----------|----------|
| Chris McKelt | Solution architecture advisory [STK-C4] | Trusted advisor (school friend of the CEO) | MEDIUM-HIGH (informal) | HIGH |
| Implementation vendor | Datapel / Unleashed / Cin7 (shortlist) [CB-C7] | Supplier / delivery partner | MEDIUM | HIGH |
| Wholesale (B2B) trade customers | Australian bike shops | Beneficiary | LOW | HIGH |
| Retail (B2C) customers | Direct consumers | Beneficiary | LOW | MEDIUM |
| Platform & accounting vendors | MYOB / Shopify / Magento (incumbent) | Supplier (existing) | LOW | LOW |
| Distributed brands / suppliers | iGPSport, CYCPLUS, Farsports, etc. | Supplier | LOW | LOW |

> **Note on UK Government roles**: The template's GovS 005 (Digital) and GovS 007 (Security) role tables are intentionally omitted — Cycle Motion is a private Australian company, not a UK Government body, so those mandatory roles do not apply.

### Stakeholder Power-Interest Grid

```text
                          INTEREST
              Low                         High
        ┌─────────────────────┬─────────────────────────┐
        │                     │                         │
        │   KEEP SATISFIED    │     MANAGE CLOSELY       │
   High │                     │                         │
        │  (none — small,     │  • Nathan Dyke (CEO)     │
        │   flat business)    │  • Kirralee Dyke (COO)   │
 P      │                     │  • Chris McKelt (advisor)│
 O      ├─────────────────────┼─────────────────────────┤
 W      │                     │                         │
 E      │      MONITOR        │      KEEP INFORMED       │
 R      │                     │                         │
   Low  │  • Platform vendors │  • Order & Supply Chain  │
        │  • Distributed      │    team (5 staff)        │
        │    brands/suppliers │  • Implementation vendor │
        │                     │  • B2B & B2C customers   │
        └─────────────────────┴─────────────────────────┘
```

| Stakeholder | Power | Interest | Quadrant | Engagement Strategy |
|-------------|-------|----------|----------|---------------------|
| Nathan Dyke (CEO) | HIGH | HIGH | Manage Closely | Strategic checkpoints, investment & vendor sign-off |
| Kirralee Dyke (COO) | HIGH | HIGH | Manage Closely | Frequent working sessions on process & rollout |
| Chris McKelt (advisor) | MEDIUM-HIGH | HIGH | Manage Closely | Architecture decisions, vendor evaluation, de-risking |
| Order & Supply Chain team | MEDIUM | HIGH | Keep Informed / Involve | Discovery, pilot, training; address job-security concerns |
| Implementation vendor | MEDIUM | HIGH | Keep Informed | Discovery checklist, reference checks, pilot delivery |
| B2B trade customers | LOW | HIGH | Keep Informed | Reliable availability/fulfilment; comms on improvements |
| B2C customers | LOW | MEDIUM | Monitor / Keep Informed | Accurate availability, fewer cancellations |
| Platform/accounting vendors | LOW | LOW | Monitor | API/version compatibility watch |
| Distributed brands/suppliers | LOW | LOW | Monitor | Supply continuity |

**Quadrant Interpretation:**

- **Manage Closely** (High Power, High Interest): Key decision-makers requiring active engagement.
- **Keep Satisfied** (High Power, Low Interest): None — in a flat, owner-led SME the high-power people are also highly interested.
- **Keep Informed** (Low/Medium Power, High Interest): Engaged groups needing regular communication and involvement.
- **Monitor** (Low Power, Low Interest): Minimal engagement; watch for compatibility/supply issues.

---

## Stakeholder Drivers Analysis

### SD-1: Nathan Dyke (CEO) — De-risked growth and a sound investment

**Stakeholder**: Nathan Dyke, CEO [STK-C1]

**Driver Category**: STRATEGIC / FINANCIAL / RISK

**Driver Statement**: Scale the business across channels and volume without a proportional rise in headcount, cost, or operational risk — and make a single significant systems investment that pays off rather than becoming a costly, disruptive mistake.

**Context & Background**: Cycle Motion has grown from a garage operation to a Perth warehouse-and-office footprint, distributing a cluster of performance cycling brands [CB-C1]. The current architecture — one channel automated, five run by hand off paper, with accounting doing inventory's job — is the ceiling on further growth [CB-C2]. As owner, Nathan carries the commercial consequence of both inaction and a botched change.

**Driver Intensity**: HIGH

**Enablers**:

- A clear, evidence-led recommendation that names the lowest-risk path to value [CB-C5]
- Buy-not-build for commodity capability, controlling cost and ongoing liability [CB-C4]
- A staged rollout that shows early wins before any big commitment [CB-C6]

**Blockers**:

- Ambiguity over scope (e.g., the 5-vs-7 storefront count) inflating cost and effort [CB-C8]
- A large, all-at-once migration with real disruption risk [CB-C6]

**Related Stakeholders**: Kirralee (COO), Chris McKelt (advisor)

---

### SD-2: Kirralee Dyke (COO) — End the manual firefighting

**Stakeholder**: Kirralee Dyke, COO [STK-C2]

**Driver Category**: OPERATIONAL / PERSONAL

**Driver Statement**: Eliminate the manual re-keying, oversell, and paper-based warehouse chaos that consume the team's time and create daily risk — and make operations scalable, disciplined, and far less dependent on heroics.

**Context & Background**: As operational sponsor and the best source of truth on current workflows [STK-C2], Kirralee owns the pain directly: every B2C order re-keyed into accounting by hand, stock that can oversell because it is never synced in real time, and a warehouse with no system discipline [CB-C2][CB-C3]. This is labour cost, error rate, and stress that compound as volume grows.

**Driver Intensity**: CRITICAL

**Enablers**:

- Automated order flow from every channel into the system of record [CB-C3]
- Near-real-time stock sync that removes oversell exposure [CB-C2]
- System-guided warehouse operations (bins, directed picking, barcode scanning, cycle counts)

**Blockers**:

- Team change-resistance or fear, slowing adoption [STK-C3]
- A WMS-only fix that leaves the five manual B2C stores untouched [CB-C2]

**Related Stakeholders**: Order & Supply Chain team, Nathan (CEO)

---

### SD-3: Order & Supply Chain Team (5 staff) — Less drudgery, fair treatment, job security

**Stakeholder**: Order & Supply Chain team — five staff [STK-C3]

**Driver Category**: OPERATIONAL / PERSONAL / RISK

**Driver Statement**: Remove the tedious, error-prone manual data entry and unclear processes that make the job harder — while being reassured that automation improves their roles rather than threatening them.

**Context & Background**: This group is closest to the day-to-day processes, exceptions, manual workarounds, and customer/supplier issues [STK-C3]. They live the re-keying and the oversell clean-ups. They are the project's richest source of process knowledge — and the people most exposed to change-fatigue and job-security anxiety when "automation" is announced.

**Driver Intensity**: HIGH

**Enablers**:

- Being involved early as process experts, not just recipients of change [STK-C3]
- Clear messaging that automation removes drudgery and redeploys them to higher-value work
- Training and a phased rollout that does not overwhelm them [CB-C6]

**Blockers**:

- Fear that automation reduces roles, breeding quiet resistance
- Change introduced top-down with no consultation or training

**Related Stakeholders**: Kirralee (COO), implementation vendor

---

### SD-4: Chris McKelt (Solution Architecture Advisor) — A defensible, de-risked architecture

**Stakeholder**: Chris McKelt, advisory — trusted by the CEO [STK-C4]

**Driver Category**: STRATEGIC / RISK

**Driver Statement**: Ensure the right architectural decision — where the single source of inventory truth lives — is made on evidence before any product is chosen, and that delivery is de-risked, protecting both Cycle Motion and the advisor's professional reputation.

**Context & Background**: The advisor framed the whole engagement around one gating question and an evidence-led sequence: decide the source of truth first, quantify the operation, pilot on real data, reference-check vendor support, and phase the rollout [CB-C1][CB-C5]. Their informal influence is high because of the trusted relationship with the CEO [STK-C4], which makes them a key channel for steering decisions soundly.

**Driver Intensity**: HIGH

**Enablers**:

- Leadership commitment to deciding the source of truth before product selection [CB-C1]
- Budget/time for proper discovery and a pilot rather than a rushed procurement [CB-C5]

**Blockers**:

- Pressure to pick a product first and retrofit the architecture
- Skipping the pilot to save time, exposing live failure modes [CB-C5]

**Related Stakeholders**: Nathan (CEO), implementation vendor

---

### SD-5: Implementation Vendor — Win, deliver, and be reference-able

**Stakeholder**: Shortlisted vendor (Datapel / Unleashed / Cin7) [CB-C7]

**Driver Category**: FINANCIAL / STRATEGIC

**Driver Statement**: Win the contract and deliver a successful, reference-able implementation — with the commercial risk that support quality and sync reliability are exactly where these platforms are judged.

**Context & Background**: The shortlist spans an MYOB-native WMS (Path 1) and multichannel hubs (Path 2). Reviews flag sync drops and support quality for at least one option, so reference-checking support specifically is decisive [CB-C7]. The vendor's success depends on accurate scope (SKU counts, order volumes, BOM complexity) being provided up front [CB-C9].

**Driver Intensity**: MEDIUM

**Enablers**:

- A well-quantified, equal-terms discovery brief to quote against reality [CB-C9]
- A scoped pilot that proves the integration before full commitment [CB-C5]

**Blockers**:

- Vague scope and the unresolved storefront count [CB-C8]
- Being selected on price alone, then blamed for thin support

**Related Stakeholders**: Chris McKelt (advisor), Kirralee (COO)

---

### SD-6: Trade & Retail Customers — Accurate availability and reliable fulfilment

**Stakeholder**: B2B trade customers (Australian bike shops) and B2C consumers

**Driver Category**: CUSTOMER

**Driver Statement**: Be able to trust that what is shown as in stock really is in stock, and that orders are fulfilled reliably and not cancelled after the fact.

**Context & Background**: Oversell and stockouts across the unsynced stores are broken promises to customers [CB-C2]. For B2B trade customers especially, reliability of supply underpins Cycle Motion's reputation as their distributor. Customers have low direct power but high influence on revenue and brand trust.

**Driver Intensity**: MEDIUM-HIGH

**Enablers**:

- Real-time accurate availability across every storefront [CB-C2]
- Exactly-once order handling — no duplicate or dropped orders [CB-C5]

**Blockers**:

- Continued oversell causing post-purchase cancellations
- Slow or error-prone manual fulfilment

**Related Stakeholders**: Kirralee (COO), Order & Supply Chain team

---

## Driver-to-Goal Mapping

### Goal G-1: Decide and document the single source of inventory truth before product selection

**Derived From Drivers**: SD-1, SD-4 (supported by SD-2)

**Goal Owner**: Nathan Dyke (CEO), advised by Chris McKelt

**Goal Statement**: Make and document an explicit decision between Path 1 (accounting platform remains inventory master + WMS layer) and Path 2 (inventory/order hub as master) **before** evaluating any product — within the discovery phase.

**Why This Matters**: Every downstream choice — which products qualify, what integrations are needed — hangs off this one decision [CB-C1]. Deciding it first is the difference between a coherent architecture and a product chosen for the wrong reasons.

**Success Metrics**:

- **Primary Metric**: Documented, signed-off source-of-truth decision with rationale
- **Secondary Metrics**: Decision made before any vendor shortlisting begins; appetite-for-change (incremental vs transformational) explicitly recorded

**Baseline**: No agreed system of record; accounting platform doing inventory by default [CB-C2]

**Target**: One agreed, documented inventory system of record

**Measurement Method**: Decision record (ADR) approved by the CEO

**Dependencies**: G-6 (operation quantified) informs the decision

**Risks to Achievement**: Pressure to pick a product first (R-3); decision deferred indefinitely

---

### Goal G-2: Eliminate manual order re-keying across all channels

**Derived From Drivers**: SD-2, SD-3, SD-1

**Goal Owner**: Kirralee Dyke (COO)

**Goal Statement**: Automate order flow from every storefront into the system of record so that 100% of orders are captured automatically and manual re-keying falls to zero by the end of rollout.

**Why This Matters**: Manual re-keying of five B2C stores is ongoing labour cost and a compounding error source [CB-C3]; removing it frees the team and removes a class of mistakes.

**Success Metrics**:

- **Primary Metric**: % of orders captured without manual entry (target 100%)
- **Secondary Metrics**: Manual order-entry hours/week (target ~0); order-entry error rate

**Baseline**: One channel automated; five B2C stores re-keyed by hand [CB-C3]

**Target**: All active channels automated; zero routine re-keying

**Measurement Method**: System order logs vs manual entry records; team time tracking

**Dependencies**: G-1 (source of truth), connectors for each storefront

**Risks to Achievement**: Storefront count under-scoped (R-6); vendor connector gaps

---

### Goal G-3: Eliminate oversell through near-real-time, idempotent stock sync

**Derived From Drivers**: SD-2, SD-6, SD-1

**Goal Owner**: Kirralee Dyke (COO)

**Goal Statement**: Achieve near-real-time stock synchronisation across all channels with idempotent order handling, reducing oversell incidents to zero and preventing duplicate orders.

**Why This Matters**: Oversell exists because stock is never synced in real time across channels [CB-C2]; the failure modes that break these integrations are duplicate orders and oversell on simultaneous sales [CB-C5]. This goal directly protects customer trust.

**Success Metrics**:

- **Primary Metric**: Oversell incidents per month (target 0)
- **Secondary Metrics**: Stock-sync latency across channels; duplicate-order incidents (target 0)

**Baseline**: Oversell exposure across five unsynced B2C stores [CB-C2]

**Target**: 0 oversell, 0 duplicate orders; sync latency within agreed threshold

**Measurement Method**: Channel vs system-of-record reconciliation; cancellation/refund logs

**Dependencies**: G-1, G-2; pilot testing of failure modes (G-5)

**Risks to Achievement**: Poor vendor sync reliability (R-2); skipped pilot (R-4)

---

### Goal G-4: Introduce system-guided warehouse discipline

**Derived From Drivers**: SD-2, SD-3

**Goal Owner**: Kirralee Dyke (COO)

**Goal Statement**: Replace the paper-based warehouse with system-guided operations (bins/locations, directed picking, barcode scanning, cycle counts), achieving stock accuracy of ≥ 98%.

**Why This Matters**: The paper-based warehouse is a real problem and a source of key-person and scaling risk [CB-C2]; system discipline makes fulfilment accurate, repeatable, and less person-dependent.

**Success Metrics**:

- **Primary Metric**: Measured stock accuracy (target ≥ 98%)
- **Secondary Metrics**: Pick error rate; cycle-count variance; fulfilment time per order

**Baseline**: Paper-based, manually updated; no system discipline [CB-C2]

**Target**: ≥ 98% stock accuracy; barcode-guided picking and cycle counts in use

**Measurement Method**: WMS cycle-count reports vs system records

**Dependencies**: G-1; warehouse hardware (scanners, labelling)

**Risks to Achievement**: Team adoption (R-1); key-person knowledge loss during transition (R-5)

---

### Goal G-5: Buy a proven product and de-risk delivery with a real-data pilot

**Derived From Drivers**: SD-1, SD-4, SD-5

**Goal Owner**: Chris McKelt (advisor) with Nathan Dyke (CEO)

**Goal Statement**: Select a proven product through a reference-checked evaluation (no custom build), then pilot it on one channel with real data — explicitly testing duplicate-order and oversell failure modes — before any full cutover.

**Why This Matters**: A custom build is high-risk, not low-risk, for a small team [CB-C4]; the safe path is buy + configure + integrate, proven by a pilot that provokes the exact failure modes that break these integrations [CB-C5].

**Success Metrics**:

- **Primary Metric**: Pilot completed on one channel with real data, failure modes tested and handled [CB-C5]
- **Secondary Metrics**: Vendor support reference checks completed [CB-C7]; build-vs-buy recorded as buy [CB-C4]

**Baseline**: No vendor selected; build-vs-buy open

**Target**: Reference-checked vendor selected; successful pilot before cutover

**Measurement Method**: Pilot test report; vendor reference notes; signed evaluation

**Dependencies**: G-1, G-6

**Risks to Achievement**: Pressure to skip the pilot (R-4); thin vendor support (R-2)

---

### Goal G-6: Quantify the operation to brief vendors against reality

**Derived From Drivers**: SD-1, SD-4, SD-5

**Goal Owner**: Kirralee Dyke (COO)

**Goal Statement**: Capture SKU count, monthly order volume per channel, accounting-platform edition, BOM complexity, warehouse locations/bins, and the confirmed storefront count by the end of discovery, so vendors quote against reality.

**Why This Matters**: Vendors can only quote and fit accurately against real numbers [CB-C9], and the storefront count ambiguity (5 vs 7) must be resolved before scoping connectors and licences [CB-C8].

**Success Metrics**:

- **Primary Metric**: Completed discovery data pack (all fields populated)
- **Secondary Metrics**: Confirmed storefront/connector count [CB-C8]

**Baseline**: Key figures unknown; storefront count unconfirmed [CB-C8]

**Target**: Complete, verified operational profile

**Measurement Method**: Discovery checklist sign-off

**Dependencies**: COO and team availability for discovery

**Risks to Achievement**: Incomplete data delaying procurement

---

### Goal G-7: Preserve manufacturing / BOM capability through the change

**Derived From Drivers**: SD-1, SD-2

**Goal Owner**: Kirralee Dyke (COO)

**Goal Statement**: Ensure the selected architecture and product preserve and support Cycle Motion's manufacturing / bill-of-materials requirements (e.g., custom wheel-build line) with no loss of capability at cutover.

**Why This Matters**: Manufacturing/BOM is an existing, real requirement that must survive the change [CB-C10]; losing it would break a core part of the business.

**Success Metrics**:

- **Primary Metric**: BOM/manufacturing workflows verified working post-cutover
- **Secondary Metrics**: Single vs multi-level assembly complexity documented and supported

**Baseline**: BOM handled in the incumbent accounting platform [CB-C10]

**Target**: BOM capability preserved and owned by a defined system

**Measurement Method**: BOM workflow acceptance test at pilot/cutover

**Dependencies**: G-1, vendor BOM capability (e.g., Enterprise editions)

**Risks to Achievement**: Chosen product weak on BOM depth

---

## Goal-to-Outcome Mapping

### Outcome O-1: A single, trusted source of inventory truth

**Supported Goals**: G-1, G-3, G-4, G-7

**Outcome Statement**: All sales channels and the warehouse agree on availability because one system is the authoritative inventory record, with measured stock accuracy ≥ 98%.

**Measurement Details**:

- **KPI**: Stock accuracy (%) and channel-vs-record reconciliation variance
- **Current Value**: Unknown/low — channels can disagree; paper warehouse [CB-C2]
- **Target Value**: ≥ 98% accuracy; near-zero reconciliation variance
- **Measurement Frequency**: Weekly reconciliation; monthly cycle-count report
- **Data Source**: System of record + WMS cycle counts
- **Report Owner**: COO

**Business Value**:

- **Financial Impact**: Fewer write-offs, refunds, and emergency reorders
- **Strategic Impact**: An architecture that can scale channels and volume [CB-C1]
- **Operational Impact**: Decisions made on trusted data, not guesswork
- **Customer Impact**: Accurate availability builds trust [CB-C2]

**Timeline**:

- **Phase 1 (Discovery)**: Source-of-truth decided and documented (G-1)
- **Phase 2 (Pilot)**: One channel proven against the single record
- **Phase 3 (Rollout)**: All channels reconciled to the single record
- **Sustainment**: Ongoing reconciliation holds variance near zero

**Stakeholder Benefits**:

- **Nathan (CEO)**: A scalable, de-risked foundation for growth
- **Kirralee (COO)**: One trusted number instead of conflicting counts

**Leading Indicators**: Source-of-truth decision signed; pilot reconciliation clean
**Lagging Indicators**: Sustained ≥ 98% stock accuracy across all channels

---

### Outcome O-2: Zero oversell and zero duplicate orders

**Supported Goals**: G-2, G-3, G-5

**Outcome Statement**: Oversell and duplicate-order incidents are eliminated across all channels through near-real-time, idempotent synchronisation.

**Measurement Details**:

- **KPI**: Oversell incidents/month and duplicate-order incidents/month
- **Current Value**: Recurring oversell exposure across five unsynced stores [CB-C2]
- **Target Value**: 0 oversell, 0 duplicate orders
- **Measurement Frequency**: Monthly
- **Data Source**: Cancellation/refund logs; order-sync exception reports
- **Report Owner**: COO

**Business Value**:

- **Financial Impact**: Fewer refunds, cancellations, and goodwill costs
- **Strategic Impact**: Reputation as a reliable distributor and retailer
- **Operational Impact**: Less firefighting and clean-up
- **Customer Impact**: Promises kept; trust retained [CB-C6 customer trust]

**Timeline**:

- **Phase 2 (Pilot)**: Failure modes provoked and proven handled [CB-C5]
- **Phase 3 (Rollout)**: Oversell/duplicates trend to zero channel by channel
- **Sustainment**: Sustained zero across all channels

**Stakeholder Benefits**:

- **Customers**: Accurate availability, no post-purchase cancellations
- **Team**: No more oversell clean-up work

**Leading Indicators**: Pilot passes failure-mode tests
**Lagging Indicators**: Sustained 0 oversell / 0 duplicate orders

---

### Outcome O-3: Operations time reclaimed and made scalable

**Supported Goals**: G-2, G-4, G-6

**Outcome Statement**: Manual order-entry effort is eliminated and warehouse work is system-guided, so order volume can grow without a proportional increase in headcount.

**Measurement Details**:

- **KPI**: Manual order-entry hours/week; orders processed per FTE
- **Current Value**: Five B2C stores re-keyed by hand; paper warehouse [CB-C3]
- **Target Value**: ~0 manual entry hours; materially higher orders/FTE
- **Measurement Frequency**: Monthly
- **Data Source**: Team time tracking; order throughput reports
- **Report Owner**: COO

**Business Value**:

- **Financial Impact**: Labour cost avoided as volume grows
- **Strategic Impact**: Headroom to add channels and volume [CB-C1]
- **Operational Impact**: Staff redeployed from data entry to higher-value work
- **Customer Impact**: Faster, more accurate fulfilment

**Timeline**:

- **Phase 1**: Operation quantified (G-6)
- **Phase 2-3**: Re-keying eliminated channel by channel
- **Sustainment**: Throughput per FTE rises with volume

**Stakeholder Benefits**:

- **Team**: Drudgery removed; clearer, less stressful work [STK-C3]
- **Nathan (CEO)**: Growth without proportional cost

**Leading Indicators**: First automated channel live; re-keying hours falling
**Lagging Indicators**: Orders/FTE up; manual entry at ~0

---

### Outcome O-4: A de-risked, reversible delivery

**Supported Goals**: G-1, G-5, G-7

**Outcome Statement**: The change is delivered on a proven product via an evidence-led, piloted, phased approach with no data loss and capability (including BOM) preserved.

**Measurement Details**:

- **KPI**: Pilot pass; zero data-loss at cutover; on-budget delivery
- **Current Value**: Not started; build-vs-buy open
- **Target Value**: Buy decision; successful pilot; clean phased cutover
- **Measurement Frequency**: Per phase gate
- **Data Source**: Pilot report; migration logs; budget tracking
- **Report Owner**: Advisor / CEO

**Business Value**:

- **Financial Impact**: Avoids the cost of a failed or over-scoped build [CB-C4]
- **Strategic Impact**: Confidence to proceed and to scale afterwards
- **Operational Impact**: Continuity of trading through the change
- **Customer Impact**: No service disruption during cutover

**Timeline**:

- **Phase 1**: Buy decision + source of truth (G-1, G-5)
- **Phase 2**: Pilot on highest-pain channel [CB-C6]
- **Phase 3**: Phased rollout; BOM verified (G-7)
- **Sustainment**: Documented, supportable operation

**Stakeholder Benefits**:

- **Nathan (CEO)**: Investment protected; surprises minimised
- **Advisor**: Defensible, reference-able outcome

**Leading Indicators**: Buy decision recorded; pilot scoped
**Lagging Indicators**: Clean phased cutover, no data loss, BOM intact

---

## Complete Traceability Matrix

### Stakeholder → Driver → Goal → Outcome

| Stakeholder | Driver ID | Driver Summary | Goal ID | Goal Summary | Outcome ID | Outcome Summary |
|-------------|-----------|----------------|---------|--------------|------------|-----------------|
| Nathan (CEO) | SD-1 | De-risked growth & sound investment | G-1 | Decide source of truth first | O-1 | Single trusted inventory truth |
| Nathan (CEO) | SD-1 | De-risked growth & sound investment | G-5 | Buy proven product + pilot | O-4 | De-risked, reversible delivery |
| Kirralee (COO) | SD-2 | End manual firefighting | G-2 | Eliminate re-keying | O-3 | Ops time reclaimed & scalable |
| Kirralee (COO) | SD-2 | End manual firefighting | G-3 | Eliminate oversell (idempotent sync) | O-2 | Zero oversell / duplicates |
| Kirralee (COO) | SD-2 | End manual firefighting | G-4 | Warehouse discipline | O-1 | Single trusted inventory truth |
| Ops team (5) | SD-3 | Less drudgery, job security | G-2 | Eliminate re-keying | O-3 | Ops time reclaimed & scalable |
| Ops team (5) | SD-3 | Less drudgery, job security | G-4 | Warehouse discipline | O-1 | Single trusted inventory truth |
| Chris McKelt | SD-4 | Defensible, de-risked architecture | G-1 | Decide source of truth first | O-1 | Single trusted inventory truth |
| Chris McKelt | SD-4 | Defensible, de-risked architecture | G-5 | Buy + pilot failure modes | O-4 | De-risked, reversible delivery |
| Vendor | SD-5 | Win, deliver, be reference-able | G-6 | Quantify the operation | O-4 | De-risked, reversible delivery |
| Customers | SD-6 | Accurate availability & fulfilment | G-3 | Eliminate oversell | O-2 | Zero oversell / duplicates |
| Kirralee / Nathan | SD-1/SD-2 | Preserve core capability | G-7 | Preserve BOM/manufacturing | O-4 | De-risked, reversible delivery |

### Conflict Analysis

**Competing Drivers**:

- **Conflict 1 — Lowest-disruption vs strategically-complete**: Nathan (SD-1) is pulled toward the fastest, lowest-cost, least-disruptive move (Path 1 — WMS layer), while the strategic case (SD-4) favours Path 2 (an inventory hub) that fixes the warehouse, the five manual stores, and multichannel truth in one architecture but with larger migration risk [CB-C1].
  - **Resolution Strategy**: Make the source-of-truth decision explicit and evidence-led **before** product selection (G-1), with appetite-for-change recorded. Use a staged approach — Path 1 is the right low-risk move if the priority is warehouse discipline while keeping the trusted record; Path 2 is the stronger long-term answer if the goal is to fix all three problems at once, at the cost of a carefully managed implementation [CB-C6]. Decision is the CEO's, informed by the advisor.

- **Conflict 2 — "We need a WMS" vs the deeper problem**: The project was framed internally as a warehouse management system need, but the higher-urgency risks are the five manual B2C stores and the missing single source of truth [CB-C2].
  - **Resolution Strategy**: Phase the rollout to start with the pain bleeding most — likely the manual Shopify stores — rather than solving the warehouse in isolation [CB-C6].

- **Conflict 3 — Efficiency goals vs team job-security fears**: Automation (G-2, G-4) advances SD-2's efficiency driver but can threaten SD-3's sense of job security.
  - **Resolution Strategy**: Engage the five staff as process experts from discovery [STK-C3], message automation as removing drudgery and redeploying them to higher-value work, and provide training and a phased rollout. Make them champions.

- **Conflict 4 — Speed vs de-risking**: Pressure for a fast, cheap procurement (SD-1) can tempt skipping the pilot and reference checks that the advisor and vendor success depend on (SD-4, SD-5).
  - **Resolution Strategy**: Frame the pilot and reference-checking as protecting the investment, not delaying it; a piloted failure-mode test is cheap insurance against live oversell/duplicate-order incidents [CB-C5].

**Synergies**:

- **Synergy 1**: SD-2 (end manual firefighting), SD-6 (customer accuracy), and SD-1 (scalable growth) all converge on the same architecture — a single source of truth plus automated, idempotent sync. One solution satisfies executive, operational, and customer drivers at once.
- **Synergy 2**: SD-3 (remove drudgery) and SD-1 (grow without adding headcount) align: automating re-keying both relieves staff and creates the scaling headroom the CEO wants.
- **Synergy 3**: SD-4 (defensible architecture) and SD-1 (sound investment) align on the buy-not-build, decide-first, pilot-before-cutover sequence.

---

## Communication & Engagement Plan

### Stakeholder-Specific Messaging

#### Nathan Dyke (CEO)

**Primary Message**: This is a de-risked, evidence-led investment that removes the ceiling on your growth — decided in the right order, proven by a pilot, and bought rather than built.

**Key Talking Points**:

- One gating decision (where inventory truth lives) drives everything; we make it first [CB-C1]
- Buy proven products; spend effort on configuration and integration, not a risky custom build [CB-C4]
- Staged rollout with early wins; pilot before any big commitment [CB-C6]

**Communication Frequency**: At each phase gate, plus ad-hoc for decisions
**Preferred Channel**: Short decision briefings + decision records
**Success Story**: "We added a channel without adding people, and we haven't oversold since."

#### Kirralee Dyke (COO)

**Primary Message**: This ends the daily firefighting — no more re-keying, no more oversell clean-up, and a warehouse the system actually guides.

**Key Talking Points**:

- Automated order flow from every channel; zero routine re-keying [CB-C3]
- Near-real-time sync removes oversell exposure [CB-C2]
- Your team's process knowledge shapes the design

**Communication Frequency**: Weekly working sessions through discovery and rollout
**Preferred Channel**: Working sessions, process walkthroughs
**Success Story**: "The team spends its day on customers and suppliers, not data entry."

#### Order & Supply Chain Team (5 staff)

**Primary Message**: This removes the tedious, error-prone work and makes your job clearer — and your knowledge is central to getting it right.

**Key Talking Points**:

- You are the experts on the real process; we start by listening [STK-C3]
- Automation takes the drudgery, not the roles — more time for valuable work
- Training and a phased rollout, not a big-bang drop

**Communication Frequency**: During discovery, pilot, and each rollout phase
**Preferred Channel**: Hands-on sessions, demos, training
**Success Story**: "No more re-keying five stores by hand or cleaning up oversells."

#### Chris McKelt (Advisor)

**Primary Message**: Hold the line on the sequence — decide the source of truth, quantify the operation, pilot on real data, reference-check support, phase the rollout.

**Key Talking Points**:

- Architecture decision before product selection [CB-C1]
- Pilot must provoke the duplicate-order and oversell failure modes [CB-C5]
- Reference-check vendor support specifically [CB-C7]

**Communication Frequency**: Throughout; leads decision and evaluation steps
**Preferred Channel**: Decision records, evaluation artifacts
**Success Story**: "The decision was made on evidence and the pilot caught the edge cases before customers did."

#### Implementation Vendor

**Primary Message**: Here is a clear, quantified, equal-terms brief — quote against reality and prove it in a pilot.

**Key Talking Points**:

- Real numbers provided up front (SKUs, volumes, BOM, locations) [CB-C9]
- Confirmed storefront/connector count [CB-C8]
- Pilot-first, with support quality reference-checked [CB-C7]

**Communication Frequency**: During evaluation and delivery
**Preferred Channel**: Discovery checklist, evaluation, pilot reviews
**Success Story**: "A clean pilot and a reference-able multichannel go-live."

---

## Change Impact Assessment

### Impact on Stakeholders

| Stakeholder | Current State | Future State | Change Magnitude | Resistance Risk | Mitigation Strategy |
|-------------|---------------|--------------|------------------|-----------------|---------------------|
| Nathan (CEO) | Carries growth/risk; systems are the ceiling [CB-C2] | Scalable, de-risked platform | MEDIUM | LOW | Evidence-led decisions; staged value |
| Kirralee (COO) | Manages manual firefighting daily [CB-C2] | System-guided, scalable ops | HIGH | LOW | Co-design; early involvement |
| Ops team (5) | Manual re-keying, oversell clean-up, paper [CB-C3] | Automated flow, guided warehouse | HIGH | MEDIUM | Involve as experts; reassure on roles; train |
| Customers | Risk of oversell/cancellations [CB-C2] | Accurate availability, reliable fulfilment | MEDIUM | LOW | Comms on improvements |
| Vendor | N/A (not yet engaged) | Delivery partner | MEDIUM | LOW | Clear scope; pilot; reference checks |

### Change Readiness

**Champions** (Enthusiastic supporters):

- Kirralee (COO) — owns the pain directly and the operational upside [STK-C2]
- Chris McKelt (advisor) — architected the de-risked approach [STK-C4]

**Fence-sitters** (Neutral, need convincing):

- Nathan (CEO) — supportive of the outcome but weighing Path 1 vs Path 2 cost/risk [CB-C1]
- Order & Supply Chain team — supportive of less drudgery but wary of automation's effect on roles [STK-C3]

**Resisters** (Opposed or skeptical):

- None identified outright. The main risk is passive resistance from the team if change is imposed top-down without consultation — addressed by early involvement and clear role messaging.

---

## Risk Register (Stakeholder-Related)

### Risk R-1: Operations team change-resistance / job-security fear

**Related Stakeholders**: Order & Supply Chain team, COO

**Risk Description**: Automation is perceived as a threat to roles, producing quiet resistance, withheld process knowledge, or slow adoption.

**Impact on Goals**: G-2, G-4

**Probability**: MEDIUM
**Impact**: MEDIUM

**Mitigation Strategy**: Involve the five staff as process experts from discovery [STK-C3]; message automation as removing drudgery and redeploying to higher-value work; provide training and a phased rollout.

**Contingency Plan**: Identify a team champion; adjust pace; pair training with visible quick wins.

---

### Risk R-2: Vendor support quality / sync reliability falls short

**Related Stakeholders**: Implementation vendor, COO, customers

**Risk Description**: A chosen platform exhibits sync drops or thin support — reviews already flag this for at least one shortlisted option [CB-C7].

**Impact on Goals**: G-3, G-5

**Probability**: MEDIUM
**Impact**: HIGH

**Mitigation Strategy**: Reference-check vendor support specifically before committing [CB-C7]; prove reliability in the pilot [CB-C5].

**Contingency Plan**: Retain a second shortlisted vendor as fallback; contractual support SLAs.

---

### Risk R-3: Source-of-truth decision deferred or made after product selection

**Related Stakeholders**: CEO, advisor

**Risk Description**: A product is chosen first and the architecture is retrofitted, undermining the single source of truth [CB-C1].

**Impact on Goals**: G-1, and by extension all goals

**Probability**: MEDIUM
**Impact**: HIGH

**Mitigation Strategy**: Make G-1 a hard gate before any vendor shortlisting; advisor holds the sequence [CB-C1].

**Contingency Plan**: Pause procurement until the decision is recorded.

---

### Risk R-4: Pressure to skip the pilot for speed/cost

**Related Stakeholders**: CEO, advisor, vendor

**Risk Description**: To save time or money, the pilot and failure-mode testing are skipped, exposing oversell and duplicate-order bugs live in front of customers [CB-C5].

**Impact on Goals**: G-3, G-5

**Probability**: MEDIUM
**Impact**: HIGH

**Mitigation Strategy**: Frame the pilot as cheap insurance protecting the investment; make a passed pilot a go/no-go gate.

**Contingency Plan**: Limit any unpiloted cutover to the lowest-volume channel with rollback ready.

---

### Risk R-5: Key-person knowledge loss during warehouse transition

**Related Stakeholders**: COO, Order & Supply Chain team

**Risk Description**: The undocumented, person-dependent warehouse process loses critical knowledge during change [CB-C2].

**Impact on Goals**: G-4, G-7

**Probability**: MEDIUM
**Impact**: MEDIUM

**Mitigation Strategy**: Document the current process during discovery; capture exceptions and workarounds from the team [STK-C3].

**Contingency Plan**: Overlap old and new processes during transition; retain a fallback.

---

### Risk R-6: Storefront count ambiguity under-scopes the work

**Related Stakeholders**: CEO, vendor, advisor

**Risk Description**: The brief states seven storefronts but enumerates six, and public research found seven distributed-brand domains — the live B2C count may differ from five, driving connector count and licensing [CB-C8].

**Impact on Goals**: G-2, G-6

**Probability**: MEDIUM
**Impact**: MEDIUM

**Mitigation Strategy**: Confirm the exact number and which brands have dedicated storefronts before scoping connectors [CB-C8] (part of G-6).

**Contingency Plan**: Build scope contingency into vendor quotes for additional connectors.

---

## Governance & Decision Rights

### Decision Authority Matrix (RACI)

| Decision Type | Responsible | Accountable | Consulted | Informed |
|---------------|-------------|-------------|-----------|----------|
| Source-of-truth (Path 1 vs Path 2) | Chris McKelt (advisor), COO | CEO | Ops team, vendor | Ops team |
| Vendor selection | COO, advisor | CEO | Ops team | Ops team, vendor |
| Budget / investment approval | CEO | CEO | COO | Advisor |
| Operational process & workflow design | COO, Ops team | COO | Advisor, vendor | CEO |
| Pilot scope & go/no-go for cutover | COO | CEO | Advisor, vendor, Ops team | All |
| Warehouse operating model (bins, picking) | COO, Ops team | COO | Vendor | CEO |

### Escalation Path

1. **Level 1**: COO (Kirralee) and advisor (Chris) — day-to-day delivery and design decisions
2. **Level 2**: CEO (Nathan) — scope, budget, source-of-truth, vendor, and go/no-go decisions
3. **Level 3**: CEO with any external investors/board (if applicable) — strategic direction and major conflicts

> In a flat, owner-led SME, the CEO is the final authority; this analysis keeps the heavy decisions (source of truth, vendor, go-live) explicitly at that level while delegating process design to the COO and team.

---

## Validation & Sign-off

### Stakeholder Review

| Stakeholder | Review Date | Comments | Status |
|-------------|-------------|----------|--------|
| Nathan Dyke (CEO) | PENDING | — | PENDING |
| Kirralee Dyke (COO) | PENDING | — | PENDING |
| Chris McKelt (advisor) | PENDING | — | PENDING |

### Document Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Project Sponsor (CEO) | Nathan Dyke | | |
| Operational Sponsor (COO) | Kirralee Dyke | | |
| Solution Architecture Advisor | Chris McKelt | | |

---

## Appendices

### Appendix A: Stakeholder Interview Summaries

> No direct interviews have yet been conducted. Per the engagement priorities in `stakeholders.md`, the next discovery step is to confirm goals with Nathan, map current processes with Kirralee, and capture practical issues from the five operational staff [STK-C5]. Summaries will be added here after those sessions.

**Planned discovery sessions**:

- Nathan Dyke (CEO) — confirm business goals, priorities, and appetite for change [STK-C5]
- Kirralee Dyke (COO) — walk the current wholesale and retail order flow and supply chain steps [STK-C5]
- Order & Supply Chain team — capture manual workarounds, exceptions, and bottlenecks [STK-C5]

### Appendix B: Survey Results

No stakeholder surveys have been conducted at this stage.

### Appendix C: References

- ARC-000-PRIN-v1.0 — Cycle Motion Enterprise Architecture Principles
- `company-brief.md` — Company Brief & Project Overview (Inventory & Warehouse Management uplift)
- `stakeholders.md` — Cyclemotion Stakeholders

---

## External References

> This section provides traceability from generated content back to source documents.
> Follow citation instructions in the project's citation reference guide.

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| STK | stakeholders.md | Stakeholder Map | 000-global/external/ | Cyclemotion stakeholder list — leadership, operations team, engagement priorities |
| CB | company-brief.md | Company Brief & Project Overview | 000-global/external/ | Verified company profile and inventory/warehouse management project brief |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| STK-C1 | STK | Key Stakeholders / Executive Leadership | Stakeholder Need | "Nathan Dyke | CEO ... Business leadership, strategy, commercial direction ... Primary executive stakeholder. Likely decision-maker for business priorities, investment, and strategic change." |
| STK-C2 | STK | Key Stakeholders / Executive Leadership | Stakeholder Need | "Kirralee Dyke | COO ... Operations, supply chain, order fulfilment, process management ... Primary operational stakeholder. Likely best contact for understanding current workflows, pain points, and day-to-day business processes." |
| STK-C3 | STK | Key Stakeholders / Operations Team | Stakeholder Need | "Order and Supply Chain Team | 5 staff ... Key user group. Important for understanding manual work, bottlenecks, exceptions, and opportunities for process improvement or automation." |
| STK-C4 | STK | Key Stakeholders | Stakeholder Need | "Nathan Dyke | CEO | Went to school with Chris McKelt" |
| STK-C5 | STK | Initial Engagement Priorities | Stakeholder Need | "Confirm business goals and priorities with Nathan Dyke. Understand current operating processes with Kirralee Dyke. ... Speak with the five operational staff to capture practical issues and improvement opportunities." |
| CB-C1 | CB | B4 | Design Decision | "Where should the single source of inventory truth live going forward? ... Every downstream choice ... hangs off one question." |
| CB-C2 | CB | B2 | Risk Factor | "a fragmented systems architecture with no automated single source of inventory truth ... oversell exposure because stock is never synced in real time across channels." |
| CB-C3 | CB | B1 / B2 | Integration Requirement | "5× Shopify — B2C | None — orders and inventory keyed into MYOB by hand ... Every B2C order is re-keyed into MYOB by hand — ongoing labour cost, data-entry errors." |
| CB-C4 | CB | B5 | Design Decision | "Recommendation: buy, do not build. A custom WMS build ... is assessed as high-risk ... build where you differentiate, buy where you don't." |
| CB-C5 | CB | B7 | Design Decision | "Pilot on one channel with real data before any full cutover. Explicitly test the failure modes that break these integrations: duplicate orders and oversell on simultaneous sales." |
| CB-C6 | CB | B7 | Design Decision | "Phase the rollout — start with the pain bleeding most (likely the five manual Shopify stores) rather than a big-bang cutover." |
| CB-C7 | CB | B6 | Market Evidence | "Cin7 ... Reviews flag sync drops and support quality — reference-check thoroughly before committing." |
| CB-C8 | CB | B8 | Risk Factor | "the brief states seven storefronts total but enumerates one B2B + five B2C (six) ... Confirm the exact number ... before scoping connectors, as this directly drives integration count and licensing." |
| CB-C9 | CB | B7 | Non-Functional Requirement | "Quantify the operation — SKU count, monthly order volume per channel, MYOB edition, must-have workflows (BOM, multi-location) — so vendors quote against reality." |
| CB-C10 | CB | A2 / B3 | Functional Requirement | "in-house manufacturing with bill-of-materials (BOM) requirements ... Manufacturing / BOM requirements preserved and supported." |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| .gitkeep | 000-global/external/ | Placeholder file, no content |

---

**Generated by**: ArcKit `/arckit:stakeholders` command
**Generated on**: 2026-06-29
**ArcKit Version**: 5.15.1
**Project**: Inventory & Warehouse Management Uplift (Project 001)
**Model**: Claude Opus 4.8 (1M context)
</content>

<!-- arckit-provenance:start -->

## Build Provenance

_Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix._

| Field | Value |
|-------|-------|
| Requested Effort | `high` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-06-29T23:07:21.518Z |

<!-- arckit-provenance:end -->
