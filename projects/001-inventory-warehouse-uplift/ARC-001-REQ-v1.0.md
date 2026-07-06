# Project Requirements: Inventory & Warehouse Management Uplift

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:requirements`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-REQ-v1.0 |
| **Document Type** | Business and Technical Requirements |
| **Project** | Inventory & Warehouse Management Uplift (Project 001) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-06-30 |
| **Last Modified** | 2026-06-30 |
| **Review Date** | 2026-07-30 |
| **Owner** | Kirralee Dyke (COO, Cycle Motion) — Operational Sponsor |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Cycle Motion leadership (Nathan & Kirralee Dyke), Order & Supply Chain team, solution architecture advisor, shortlisted vendors |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-06-30 | ArcKit AI | Initial creation from `/arckit:requirements` command | [PENDING] | [PENDING] |

## Document Purpose

This document defines the business and technical requirements for Cycle Motion's inventory and warehouse management uplift. It will be used to drive vendor selection (evaluation and scoring of the shortlisted products), the source-of-truth architecture decision, the pilot and phased rollout, and acceptance testing. Requirements trace back to the stakeholder analysis (`ARC-001-STKE-v1.0`), the architecture principles (`ARC-000-PRIN-v1.0`), and the research findings (`ARC-001-RSCH-v1.0`).

---

## Executive Summary

### Business Context

Cycle Motion Pty Ltd is an Australian (Perth, WA) manufacturer and distributor of performance cycling components, trading across one B2B store (Magento/Adobe Commerce) and approximately five B2C storefronts (Shopify), with MYOB AccountRight as the accounting, inventory, and manufacturing system of record [CB-C1]. The business runs in-house manufacturing with bill-of-materials requirements (e.g. a custom wheel-build line) [CB-C2].

The current architecture has one channel properly integrated and the rest run by hand off paper: every B2C order is re-keyed into MYOB manually, stock is never synced in real time across channels (creating oversell exposure), and the warehouse is paper-based with no system discipline [CB-C3]. Inventory truth lives in an accounting platform never designed to be a multichannel inventory engine, which has become the ceiling on growth [CB-C4].

This project establishes a reliable, automated **single source of inventory truth** across all channels, eliminates manual re-keying and oversell, introduces disciplined warehouse operations, and preserves manufacturing/BOM capability — delivered by buying a proven product (not building), decided in the right order, and de-risked by a pilot before any cutover [CB-C5].

### Objectives

- Establish one agreed, authoritative system of record for inventory across all sales channels.
- Eliminate manual order re-keying and eliminate oversell and duplicate orders.
- Introduce system-guided warehouse operations while preserving manufacturing/BOM.
- Buy a proven product and de-risk delivery via a real-data pilot and phased rollout.
- Build an architecture that scales with channel and order-volume growth.

### Expected Outcomes

- Oversell incidents reduced to **0** per month; duplicate orders **0** per month.
- Manual order-entry effort reduced from current re-keying of ~5 B2C stores to **~0 hours/week**.
- Measured stock accuracy **≥ 98%**.
- 100% of orders from every active channel captured automatically (no manual re-keying).
- Channel/order volume able to grow without proportional headcount increase.

### Project Scope

**In Scope**:

- A single authoritative system of record for inventory (selection of Path 1, Path 2, or Path 4 — see Conflict C-1).
- Automated, idempotent integration between the storefronts (Shopify ×5, Magento) and the inventory system of record.
- Integration with MYOB AccountRight for accounting (and inventory, if Path 1 is chosen).
- System-guided warehouse operations: bins/locations, directed/barcode picking, cycle counts.
- Manufacturing / bill-of-materials support.
- Carrier/shipping dispatch integration.
- A pilot on one channel with real data, then a phased rollout.

**Out of Scope**:

- Custom-built WMS or inventory platform — explicitly rejected in favour of buy (BR-006) [CB-C6].
- Replacement of the storefront platforms (Shopify, Magento) themselves.
- A full ERP migration replacing MYOB's accounting function (Path 4 / Odoo Path 3) — noted as a future strategic option, not this project's commitment.
- Marketing, CRM, and finance/payroll process redesign beyond inventory/order/warehouse flows.

---

## Stakeholders

| Stakeholder | Role | Organization | Involvement Level |
|-------------|------|--------------|-------------------|
| Nathan Dyke | CEO — Strategic Sponsor [STK-C1] | Cycle Motion | Decision maker (investment, source-of-truth, vendor, go-live) |
| Kirralee Dyke | COO — Operational Sponsor [STK-C2] | Cycle Motion | Requirements definition, process design, day-to-day decisions |
| Order & Supply Chain Team (5 staff) | Operations / end users [STK-C3] | Cycle Motion | Requirements elicitation, user acceptance, pilot testing |
| Chris McKelt | Solution Architecture Advisor [STK-C4] | Advisory | Technical oversight, vendor evaluation, de-risking |
| Implementation vendor | Delivery partner | Datapel / Ostendo / Unleashed / Cin7 (shortlist) | Solution delivery, integration |
| B2B & B2C customers | Beneficiaries | External | User acceptance (indirect — accurate availability, reliable fulfilment) |

---

## Business Requirements

### BR-001: Single Source of Inventory Truth

**Description**: Establish one agreed, authoritative system of record for inventory, from which all channels read availability and to which all stock movements are written.

**Rationale**: Inventory truth currently lives in an accounting platform never designed for multichannel stock, and channels can disagree on availability [CB-C4]. This is the central architectural problem; every downstream choice depends on it [CB-C7].

**Success Criteria**:

- One inventory system of record is agreed and documented before product selection.
- All active channels source availability from that single source.
- Measured stock accuracy ≥ 98%.

**Priority**: MUST_HAVE

**Stakeholder**: Nathan Dyke (CEO), Kirralee Dyke (COO) — supports goals G-1, G-3; principle P6.

---

### BR-002: Eliminate Manual Order Re-Keying

**Description**: Automate order capture from every storefront into the system of record so that no orders are re-keyed by hand.

**Rationale**: Five B2C stores are re-keyed into MYOB manually — ongoing labour cost and a compounding error source [CB-C3].

**Success Criteria**:

- 100% of orders from every active channel captured automatically.
- Manual order-entry effort reduced to ~0 hours/week.

**Priority**: MUST_HAVE

**Stakeholder**: Kirralee Dyke (COO), Order & Supply Chain team — goals G-2; drivers SD-2, SD-3; principle P3.

---

### BR-003: Eliminate Oversell and Duplicate Orders

**Description**: Prevent overselling and duplicate orders across all channels through timely, idempotent stock and order synchronisation.

**Rationale**: Oversell exists because stock is never synced in real time across channels; the failure modes that break these integrations are duplicate orders and oversell on simultaneous sales [CB-C3][CB-C5].

**Success Criteria**:

- Oversell incidents: 0 per month.
- Duplicate-order incidents: 0 per month.

**Priority**: MUST_HAVE

**Stakeholder**: Kirralee Dyke (COO), customers — goals G-3, G-stakeholder-trust; drivers SD-2, SD-6; principles P10, P15.

---

### BR-004: Disciplined, System-Guided Warehouse Operations

**Description**: Replace the paper-based warehouse with system-guided operations (bins/locations, directed/barcode picking, cycle counts).

**Rationale**: The paper-based warehouse is a source of error and key-person/scaling risk [CB-C4].

**Success Criteria**:

- Bins/locations, barcode-guided picking, and cycle counts in operational use.
- Pick error rate and cycle-count variance tracked and trending down.

**Priority**: MUST_HAVE

**Stakeholder**: Kirralee Dyke (COO), Order & Supply Chain team — goal G-4; drivers SD-2, SD-3.

---

### BR-005: Preserve Manufacturing / Bill-of-Materials Capability

**Description**: The selected solution must preserve and support Cycle Motion's manufacturing / bill-of-materials requirements with no loss of capability at cutover.

**Rationale**: In-house manufacturing with BOM (e.g. custom wheel builds) is an existing core capability that must survive the change [CB-C2].

**Success Criteria**:

- BOM/manufacturing workflows verified working at pilot and post-cutover.
- Single vs multi-level assembly complexity documented and supported.

**Priority**: MUST_HAVE

**Stakeholder**: Kirralee Dyke (COO) — goal G-7; principle P-data quality.

---

### BR-006: Buy, Do Not Build

**Description**: Acquire a proven, supported commercial product for the inventory/WMS capability; do not commission a custom build. Engineering effort is directed to configuration and integration.

**Rationale**: A custom WMS/hub build (~A$450k–900k+) is high-risk, not low-risk, for a small team, creating a permanent maintenance/API-treadmill and key-person liability [CB-C6].

**Success Criteria**:

- Build-vs-buy decision recorded as buy.
- No bespoke WMS/inventory platform developed; custom code limited to integration glue.

**Priority**: MUST_HAVE

**Stakeholder**: Nathan Dyke (CEO), Chris McKelt (advisor) — goal G-5; driver SD-1; principle P1.

---

### BR-007: De-Risked, Piloted, Phased Delivery

**Description**: Validate the solution on a pilot of one channel with real data — explicitly testing the duplicate-order and oversell failure modes — before any full cutover, then roll out in phases starting with the highest-pain channel.

**Rationale**: The brief is explicit: pilot on real data and test the failure modes that break these integrations before committing; phase the rollout rather than a big-bang [CB-C5][CB-C8].

**Success Criteria**:

- Pilot completed on one channel with real data; failure modes provoked and proven handled.
- Rollout phased, not big-bang; each phase reversible.

**Priority**: MUST_HAVE

**Stakeholder**: Chris McKelt (advisor), Nathan Dyke (CEO) — goal G-5; driver SD-4; principle P17.

---

### BR-008: Scalable Architecture for Channel and Volume Growth

**Description**: The solution must absorb additional storefronts, SKUs, and order volume without re-architecture.

**Rationale**: The business intends to grow channels and volume; the architecture must not become the ceiling [CB-C9].

**Success Criteria**:

- A new storefront can be onboarded via configuration/connector, without core redesign.
- Order volume can grow without proportional headcount increase.

**Priority**: SHOULD_HAVE

**Stakeholder**: Nathan Dyke (CEO) — goal G-1 (scalability); driver SD-1; principle P2.

---

### BR-009: Quantify the Operation Before Procurement

**Description**: Capture the operational profile — SKU count, monthly order volume per channel, MYOB edition, BOM complexity, warehouse locations/bins, and the confirmed storefront count — before vendor quoting and selection.

**Rationale**: Vendors can only quote and fit accurately against real numbers; the storefront count (5 vs 7) must be resolved before scoping connectors and licences [CB-C9][CB-C10].

**Success Criteria**:

- Completed discovery data pack with all fields populated.
- Confirmed storefront/connector count.

**Priority**: MUST_HAVE

**Stakeholder**: Kirralee Dyke (COO), vendor — goal G-6; driver SD-5.

---

### BR-010: Control Total Cost of Ownership (SME-Appropriate)

**Description**: Keep total cost of ownership proportionate to a small business, assessed over a multi-year horizon (licence + implementation + support), with vendor support quality weighted as a first-class criterion.

**Rationale**: For an owner-led SME, cost and ongoing support liability are decisive; indicative 3-year TCO ranges from ~A$55k (Path 1) to ~A$135k (transformational paths) per the research, pending quantification.

**Success Criteria**:

- 3-year TCO modelled per shortlisted option against the confirmed operational profile.
- Vendor support reference-checked before commitment.

**Priority**: SHOULD_HAVE

**Stakeholder**: Nathan Dyke (CEO) — driver SD-1 (financial); principle P1.

---

## Functional Requirements

### User Personas

#### Persona 1: Kirralee Dyke — COO / Operations Lead

- **Role**: Operational sponsor; owns workflows, fulfilment, and process management [STK-C2].
- **Goals**: End manual firefighting; one trusted inventory number; scalable, disciplined operations.
- **Pain Points**: Manual re-keying, oversell clean-ups, paper warehouse, key-person dependency.
- **Technical Proficiency**: Medium.

#### Persona 2: Order & Supply Chain Operator (×5 staff)

- **Role**: Process orders, coordinate inventory and supply chain across channels [STK-C3].
- **Goals**: Remove tedious data entry and errors; clear processes; secure roles.
- **Pain Points**: Re-keying five stores by hand; chasing exceptions, oversells, backorders.
- **Technical Proficiency**: Low–Medium.

#### Persona 3: Warehouse Picker/Packer

- **Role**: Pick, pack, and dispatch orders from the warehouse.
- **Goals**: Know where stock is and what to pick; accurate, fast fulfilment.
- **Pain Points**: Paper-based picking, no system guidance, stock not where the record says.
- **Technical Proficiency**: Low.

#### Persona 4: Nathan Dyke — CEO

- **Role**: Strategic sponsor; investment and go/no-go authority [STK-C1].
- **Goals**: De-risked growth, sound investment, no disruption to trading.
- **Pain Points**: Systems are the ceiling on growth; risk of a costly failed change.
- **Technical Proficiency**: Medium.

---

### Use Cases

#### UC-1: B2C order flows automatically from storefront to system of record

**Actor**: Order & Supply Chain Operator (system-driven)

**Preconditions**: Storefront connected to the system of record; stock levels current.

**Main Flow**:

1. Customer places an order on a B2C storefront.
2. The order is transmitted automatically to the system of record.
3. The system of record decrements available stock and reserves the items.
4. Updated availability is synced back to all channels.
5. The order is queued for warehouse fulfilment.

**Postconditions**: Order recorded once; stock reduced; all channels reflect new availability.

**Alternative Flows**:

- **Alt 2a**: Transmission fails → order is queued for retry and an alert is raised (no silent loss).

**Exception Flows**:

- **Ex 1**: Duplicate transmission of the same order → idempotency key prevents a second order being created.

**Business Rules**: An order accepted must be fulfillable (no overselling the last unit).

**Priority**: CRITICAL

#### UC-2: Simultaneous sale of the last unit across two channels

**Actor**: System

**Main Flow**:

1. Two customers on different channels attempt to buy the last unit of a SKU at once.
2. The system of record allocates the unit to exactly one order.
3. The other channel's availability is updated to zero promptly.

**Postconditions**: No oversell; one order fulfilled, the other handled per backorder/out-of-stock rules.

**Priority**: CRITICAL

---

### Functional Requirements Detail

#### FR-001: Centralised real-time inventory across all channels

**Description**: The system must maintain a single, authoritative, real-time view of stock-on-hand by location, serving availability to all channels.

**Relates To**: BR-001, UC-1, UC-2

**Acceptance Criteria**:

- [ ] Given a stock movement, when it is recorded, then all channels reflect updated availability within the defined sync latency.
- [ ] Given any SKU, when queried, then exactly one authoritative stock-on-hand figure exists.

**Priority**: MUST_HAVE · **Complexity**: HIGH · **Dependencies**: INT-001, INT-002, INT-003 · Principle P6.

#### FR-002: Automated order ingestion from every storefront

**Description**: The system must automatically ingest orders from all B2C (Shopify ×5) and B2B (Magento) storefronts without manual entry.

**Relates To**: BR-002, UC-1

**Acceptance Criteria**:

- [ ] Given an order on any connected storefront, when placed, then it appears in the system of record automatically.
- [ ] Edge case: a storefront outage queues and back-fills orders on recovery.

**Priority**: MUST_HAVE · **Complexity**: HIGH · **Dependencies**: INT-002, INT-003.

#### FR-003: Near-real-time stock sync to prevent oversell

**Description**: The system must push stock-level changes to all channels quickly enough to prevent overselling.

**Relates To**: BR-003, UC-2

**Acceptance Criteria**:

- [ ] Given a sale on one channel, when stock changes, then other channels reflect it within the agreed latency (see NFR-P-001).
- [ ] Given the last unit, when sold on one channel, then it cannot be sold on another.

**Priority**: MUST_HAVE · **Complexity**: HIGH · Principle P10.

#### FR-004: Idempotent order and stock processing

**Description**: Order and stock operations must be idempotent — processing the same message twice has no ill effect.

**Relates To**: BR-003

**Acceptance Criteria**:

- [ ] Given a retried order message, when reprocessed, then no duplicate order or double stock movement occurs.

**Priority**: MUST_HAVE · **Complexity**: HIGH · Principle P10.

#### FR-005: Bin / location management

**Description**: The system must support warehouse bins/locations and track stock by location.

**Relates To**: BR-004

**Acceptance Criteria**:

- [ ] Given a SKU, when stored, then its bin/location is recorded and retrievable.

**Priority**: MUST_HAVE · **Complexity**: MEDIUM.

#### FR-006: Barcode-guided / directed picking

**Description**: The system must guide picking via barcode scanning and directed pick paths.

**Relates To**: BR-004

**Acceptance Criteria**:

- [ ] Given an order, when picking, then the system directs the picker and validates picks by scan.

**Priority**: SHOULD_HAVE · **Complexity**: MEDIUM.

#### FR-007: Cycle counts and stock adjustments

**Description**: The system must support cycle counts and controlled stock adjustments with an audit trail.

**Relates To**: BR-004, BR-001

**Acceptance Criteria**:

- [ ] Given a cycle count, when completed, then variances are recorded and the record updated.

**Priority**: MUST_HAVE · **Complexity**: MEDIUM.

#### FR-008: Bill-of-materials and manufacturing work orders

**Description**: The system must support bills of materials and manufacturing/assembly work orders (e.g. custom wheel builds), consuming components and producing finished goods.

**Relates To**: BR-005

**Acceptance Criteria**:

- [ ] Given a BOM, when a build is completed, then components are consumed and the finished SKU stocked.
- [ ] Edge case: multi-level assemblies are supported if confirmed in discovery (BR-009).

**Priority**: MUST_HAVE · **Complexity**: HIGH.

#### FR-009: Purchase orders and supplier replenishment

**Description**: The system must support purchase orders and supplier replenishment against stock levels.

**Relates To**: BR-004

**Acceptance Criteria**:

- [ ] Given low stock, when reorder thresholds are met, then a purchase order can be raised against a supplier.

**Priority**: SHOULD_HAVE · **Complexity**: MEDIUM.

#### FR-010: Returns, backorders, and exceptions handling

**Description**: The system must handle returns, backorders, and order exceptions across channels.

**Relates To**: BR-002, BR-003

**Acceptance Criteria**:

- [ ] Given a return, when processed, then stock and order records are updated consistently.
- [ ] Given an out-of-stock item, when ordered, then backorder rules apply per channel.

**Priority**: SHOULD_HAVE · **Complexity**: MEDIUM.

#### FR-011: Carrier / shipping dispatch

**Description**: The system must integrate carrier/shipping to generate labels and dispatch records.

**Relates To**: BR-004

**Acceptance Criteria**:

- [ ] Given a picked order, when dispatched, then a carrier label and tracking are generated.

**Priority**: SHOULD_HAVE · **Complexity**: MEDIUM · **Dependencies**: INT-004.

#### FR-012: Product / SKU master and multichannel pricing

**Description**: The system must maintain a consistent product/SKU master and channel pricing, propagated to channels from defined sources.

**Relates To**: BR-001

**Acceptance Criteria**:

- [ ] Given a product change, when made in the master, then it propagates to channels per rules.
- [ ] Given any SKU, when compared across channels, then identity and price are consistent.

**Priority**: MUST_HAVE · **Complexity**: MEDIUM · Principle P8.

#### FR-013: Order status visibility

**Description**: Staff (and, where appropriate, customers) must be able to see order status across channels.

**Relates To**: BR-002

**Acceptance Criteria**:

- [ ] Given an order, when queried, then its current status is visible to staff.

**Priority**: SHOULD_HAVE · **Complexity**: LOW.

#### FR-014: Operational reporting

**Description**: The system must provide operational reporting on stock, orders, and fulfilment performance.

**Relates To**: BR-004, BR-008

**Acceptance Criteria**:

- [ ] Given operations data, when reported, then stock accuracy, order throughput, and fulfilment metrics are available.

**Priority**: SHOULD_HAVE · **Complexity**: LOW.

#### FR-015: Failed-sync exception queue, retry, and alerting

**Description**: The system must surface failed or stuck syncs/orders in a recoverable exception queue and alert a named person.

**Relates To**: BR-003, BR-002

**Acceptance Criteria**:

- [ ] Given a failed sync, when it occurs, then it is queued for retry and an alert is raised.
- [ ] Given a stuck order, when detected, then it is visible and replayable (no silent loss).

**Priority**: MUST_HAVE · **Complexity**: MEDIUM · Principle P5.

#### FR-016: Role-based user access

**Description**: The system must support role-based access appropriate to a small team, with least privilege.

**Relates To**: NFR-SEC-002

**Acceptance Criteria**:

- [ ] Given a user, when assigned a role, then they have only the access that role requires.

**Priority**: SHOULD_HAVE · **Complexity**: LOW · Principle P4.

---

## Non-Functional Requirements (NFRs)

### Performance Requirements

#### NFR-P-001: Stock Sync Latency

**Requirement**: Stock-level changes must propagate to all channels quickly enough to prevent overselling — target near-real-time, with a defined maximum latency to be confirmed in discovery (indicatively within a few minutes).

**Measurement Method**: Timed sync tests channel-to-channel; oversell incident tracking.

**Load Conditions**: Confirmed peak orders/hour per channel (pending BR-009).

**Priority**: CRITICAL · Principle P10.

#### NFR-P-002: Order Ingestion Latency

**Requirement**: Orders from any channel must appear in the system of record within the agreed latency (indicatively minutes, not hours).

**Priority**: HIGH.

### Availability and Resilience Requirements

#### NFR-A-001: Availability Target

**Requirement**: The inventory system of record and customer-facing storefronts must meet defined availability targets (indicatively ≥ 99.5% for the system of record, plus storefront-platform SLAs), proportionate to the cost of downtime for an SME.

**Priority**: HIGH · Principle P12.

#### NFR-A-002: Backup, Restore, and No-Data-Loss Migration

**Requirement**: Core data (inventory, orders, customers, BOM) must be backed up with a tested restore; any migration must be preceded by a verified backup and a defined rollback path with no data loss.

**Priority**: CRITICAL · Principle P18.

#### NFR-A-003: Recoverable Synchronisation

**Requirement**: Failed syncs and orders must be recoverable (retry/replay) with no silent loss.

**Resilience Patterns Required**:

- [ ] Retry with backoff on transient failures
- [ ] Dead-letter / exception queue for failed messages
- [ ] Timeouts on integration calls
- [ ] Graceful handling of a storefront or connector outage

**Priority**: CRITICAL · Principles P2, P10.

### Scalability Requirements

#### NFR-S-001: Channel and Volume Scaling

**Requirement**: The system must support onboarding additional storefronts, SKUs, and order volume via configuration/connectors without re-architecture.

**Growth Projections**: To be confirmed in discovery (BR-009); design for confirmed SKU count plus headroom.

**Priority**: HIGH · Principle P2.

### Security Requirements

#### NFR-SEC-001: Authentication & MFA

**Requirement**: Administrative and staff access to commerce, inventory, and accounting systems must use multi-factor authentication.

**Priority**: CRITICAL · Principle P4.

#### NFR-SEC-002: Authorisation (Least Privilege)

**Requirement**: Role-based access control with least privilege for staff and integration accounts.

**Priority**: CRITICAL · Principle P4.

#### NFR-SEC-003: Encryption

**Requirement**: Encryption in transit for all integrations and customer-facing traffic; encryption at rest for all stores holding customer, order, or payment data.

**Priority**: CRITICAL · Principle P4.

#### NFR-SEC-004: Secrets Management

**Requirement**: API credentials and secrets must be held in a secure store — never in code, spreadsheets, or email.

**Priority**: CRITICAL · Principle P4.

#### NFR-SEC-005: PCI-DSS Alignment

**Requirement**: Payment card handling must align with PCI-DSS; no raw cardholder data may be stored in Cycle Motion's internal inventory/order systems, logs, or exports. Card capture remains within compliant payment providers.

**Priority**: CRITICAL · Principle P14.

### Compliance and Regulatory Requirements

#### NFR-C-001: Australian Privacy (APPs)

**Requirement**: Customer personal data must be handled in line with the Australian Privacy Principles (Privacy Act 1988): data minimisation, defined retention, least-privilege access, and a clear privacy notice.

> **Verify**: Confirm Privacy Act small-business-exemption status (turnover threshold / whether the business trades in personal information). APP-aligned handling is the recommended baseline regardless. Consider `/arckit:au-pia`.

**Priority**: HIGH · Principle P7.

#### NFR-C-002: Data Residency / Cross-Border Awareness

**Requirement**: Data residency and cross-border transfer must be understood for each hosted platform and any middleware (e.g. overseas-hosted SaaS or connectors), consistent with APP obligations.

**Priority**: MEDIUM · Principle P7.

#### NFR-C-003: Audit Logging

**Requirement**: Stock adjustments, order changes, and administrative actions must be logged with who/what/when for traceability.

**Priority**: MEDIUM · Principle P5.

### Maintainability and Supportability Requirements

#### NFR-M-001: Configuration Over Custom Code

**Requirement**: The solution must be delivered primarily by configuration and supported integration, with custom code minimised, documented, and version-controlled.

**Priority**: HIGH · Principles P16, P13.

#### NFR-M-002: Observability of Integrations

**Requirement**: Integration health must be observable, with failures alerting a named person and a watchable operational view appropriate to a small team.

**Priority**: HIGH · Principle P5.

#### NFR-M-003: Vendor Support Quality & SLA

**Requirement**: The selected vendor must provide a support model with an agreed SLA, reference-checked before commitment. (Research confirmed sync-drop/support concerns for at least one shortlisted option.)

**Priority**: HIGH · Mitigates research risk VR-2.

### Interoperability Requirements

#### NFR-I-001: Supported Interfaces Only

**Requirement**: Integrations must use products' supported/published APIs or connectors; no direct database access into a third-party product's internals.

**Priority**: CRITICAL · Principles P3, P9.

#### NFR-I-002: Loose Coupling / Replaceability

**Requirement**: The architecture must allow any one product (commerce platform, WMS, hub, accounting) to be changed without forcing redesign of the others.

**Priority**: HIGH · Principle P9.

---

## Integration Requirements

### External System Integrations

#### INT-001: MYOB AccountRight

**Purpose**: Accounting system of record (and inventory master, if Path 1 is chosen).

**Integration Type**: Real-time/near-real-time API (native where available).

**Data Exchanged**: Invoices, stock movements, products, purchase orders — direction depends on chosen path.

**Authentication**: MYOB-supported authentication; credentials in a secure store.

**Error Handling**: Idempotent, queued, retried, alerted.

**Priority**: CRITICAL.

> **Design note**: Research found MYOB-native integration is rare — Datapel and Ostendo are MYOB-AccountRight-native; Unleashed, Cin7, Odoo, and ERPNext require middleware in the sync path. This materially affects integration risk (see Conflict C-5) and is a primary input to the source-of-truth decision (Conflict C-1).

#### INT-002: Shopify (×5 B2C storefronts)

**Purpose**: B2C order capture and stock/price sync.

**Integration Type**: Supported connector/API per storefront; idempotent.

**Data Exchanged**: Orders in; availability and pricing out.

**Priority**: CRITICAL · (Confirm exact store count — BR-009.)

#### INT-003: Magento / Adobe Commerce (B2B)

**Purpose**: B2B order capture and stock/price sync (currently the one automated channel).

**Integration Type**: Supported connector/API; idempotent.

**Data Exchanged**: Orders in; availability, pricing, product data out.

**Priority**: CRITICAL.

#### INT-004: Carrier / Shipping

**Purpose**: Generate shipping labels and dispatch/tracking records (e.g. an aggregator such as Starshipit, with Australian carriers).

**Integration Type**: Supported API.

**Priority**: HIGH.

#### INT-005: Middleware (conditional — non-MYOB-native paths only)

**Purpose**: If Path 2/3 (hub or open-source ERP) is chosen, middleware bridges the inventory master and MYOB accounting.

**Integration Type**: Idempotent, monitored, with reference-checked reliability.

**Priority**: CONDITIONAL — applies only if a non-MYOB-native system of record is selected. Carries elevated risk (Principles P9, P10).

---

## Data Requirements

### Data Entities

#### Entity 1: Product / SKU

**Description**: Master record for each sellable/stocked item.

**Data Classification**: INTERNAL · **Retention**: Life of product + statutory accounting retention.

#### Entity 2: Inventory / Stock-on-Hand (by location)

**Description**: Authoritative stock levels per SKU per location.

**Data Classification**: INTERNAL.

#### Entity 3: Order (B2B and B2C)

**Description**: Customer orders from all channels, with line items and fulfilment status.

**Data Classification**: CONFIDENTIAL (contains customer data) · **Retention**: Per accounting/tax and APP requirements.

#### Entity 4: Customer

**Description**: Customer identity and contact/delivery details (personal data).

**Data Classification**: CONFIDENTIAL (PII — APP scope) · **Retention**: Minimised; defined retention with secure disposal.

#### Entity 5: Bill of Materials / Assembly

**Description**: Component structures for manufactured items (e.g. wheel builds).

**Data Classification**: INTERNAL.

#### Entity 6: Supplier / Purchase Order

**Description**: Suppliers and replenishment orders.

**Data Classification**: INTERNAL.

### Data Quality Requirements

- **Accuracy**: Stock accuracy ≥ 98%; validation enforced at point of entry (Principle P8).
- **Consistency**: SKU/product identity and pricing consistent across channels; reconciliation between channels and the system of record.
- **Timeliness**: Stock freshness sufficient to prevent oversell (NFR-P-001).

### Data Migration Requirements

- **Scope**: Products, stock, open orders, customers, BOM, suppliers from MYOB/current state.
- **Strategy**: Phased; pilot one channel first; preserve the working MYOB–Magento integration unless deliberately reworked with a fallback.
- **Validation**: Reconcile migrated data against source; verify BOM workflows.
- **Rollback**: Verified backup and defined rollback before any cutover (NFR-A-002, Principle P18).

---

## Constraints and Assumptions

### Technical Constraints

**TC-1**: Must integrate with MYOB AccountRight (current accounting/inventory system of record).

**TC-2**: Must integrate with the existing storefronts — Shopify (×5) and Magento/Adobe Commerce.

**TC-3**: Must be a bought commercial product; no bespoke WMS/inventory build (Principle P1, BR-006).

**TC-4**: Must preserve manufacturing / BOM capability (BR-005).

### Business Constraints

**BC-1**: SME budget — indicative 3-year TCO A$55k–135k depending on path; cost and support liability are decisive.

**BC-2**: Small team (~7 core staff) — the solution must be operable without a dedicated IT function.

**BC-3**: Trading continuity — no big-bang cutover; delivery must be phased and reversible (BR-007).

### Assumptions

**A-1**: The operational profile (BR-009) will be quantified before procurement.

**A-2**: The exact storefront count (5 vs 7) will be confirmed before connector scoping [CB-C10].

**A-3**: MYOB AccountRight remains the accounting record unless a Path 2/4 decision changes this.

**Validation Plan**: Assumptions confirmed during discovery (BR-009) and the pilot (BR-007).

---

## Success Criteria and KPIs

### Business Success Metrics

| Metric | Baseline | Target | Timeline | Measurement Method |
|--------|----------|--------|----------|-------------------|
| Oversell incidents | Recurring (unsynced stores) | 0 / month | Post-rollout | Cancellation/refund + reconciliation logs |
| Duplicate orders | Possible on retry/simultaneous | 0 / month | Post-rollout | Order-sync exception reports |
| Manual order-entry effort | ~5 B2C stores re-keyed by hand | ~0 hours/week | Post-rollout | Team time tracking |
| Stock accuracy | Unknown / low (paper warehouse) | ≥ 98% | Post-rollout | Cycle-count reports |
| Orders captured automatically | 1 of ~6 channels | 100% of active channels | Post-rollout | System order logs |

### Technical Success Metrics

| Metric | Target | Measurement Method |
|--------|--------|-------------------|
| Stock sync latency | Within agreed threshold (prevents oversell) | Timed sync tests |
| Failed-sync recovery | 100% recoverable, alerted | Exception-queue monitoring |
| Migration data loss | Zero | Pre/post reconciliation |
| Pilot failure-mode tests | Pass (no oversell, no duplicates) | Pilot test report |

---

## Dependencies and Risks

### Dependencies

| Dependency | Description | Owner | Target Date | Status | Impact if Delayed |
|------------|-------------|-------|-------------|--------|-------------------|
| Operational quantification | SKU count, volumes, MYOB edition, BOM complexity, storefront count (BR-009) | COO | Pre-procurement | At Risk | HIGH |
| Source-of-truth decision | Path 1 vs 2 vs 4 (Conflict C-1) | CEO + advisor | Pre-procurement | Open | HIGH |
| Vendor support references | Reference-check shortlisted vendors (NFR-M-003) | Advisor | Pre-selection | Open | HIGH |

### Risks

| Risk ID | Description | Probability | Impact | Mitigation Strategy | Owner |
|---------|-------------|-------------|--------|---------------------|-------|
| R-1 | Non-MYOB-native master needs middleware in sync path (oversell/duplicate risk) | MEDIUM | HIGH | Prefer MYOB-native (Datapel/Ostendo); if hub, reference-check + pilot middleware | Advisor |
| R-2 | Vendor sync-drop/support shortfall (esp. one shortlisted option) | MEDIUM | HIGH | Reference-check support; prove in pilot; contractual SLA | CEO |
| R-3 | Source-of-truth decided after product selection | MEDIUM | HIGH | Gate: decide before shortlisting (Conflict C-1) | CEO |
| R-4 | Pilot skipped for speed/cost → live failure modes | MEDIUM | HIGH | Pilot is a go/no-go gate (BR-007) | CEO |
| R-5 | Storefront count under-scoped (5 vs 7) | MEDIUM | MEDIUM | Confirm in discovery (BR-009) | COO |
| R-6 | Team change-resistance / job-security fear | MEDIUM | MEDIUM | Involve as experts; reframe roles; train | COO |

---

## Requirement Conflicts & Resolutions

> Sourced from the stakeholder analysis conflict section (`ARC-001-STKE-v1.0`).

### Conflict C-1: Low-disruption (Path 1) vs Strategically-complete (Path 2)

**Conflicting Requirements**:

- **Requirement A**: BR-001 satisfied via Path 1 — keep MYOB as inventory master + MYOB-native WMS (lowest disruption).
- **Requirement B**: BR-001 + BR-002 satisfied via Path 2 — an inventory/order hub as master (fixes warehouse, manual stores, and multichannel truth at once, but larger change).

**Stakeholders Involved**: CEO (SD-1) leans low-disruption/low-cost; advisor (SD-4) notes Path 2 is strategically stronger but riskier.

**Nature of Conflict**: Path 1 is fastest/cheapest/lowest-risk but does not by itself solve the five manual Shopify stores; Path 2 solves more but carries migration risk and (for non-MYOB-native products) middleware in the sync path.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Path 1 (Datapel/Ostendo, MYOB-native)** | ✅ Lowest risk/TCO ✅ MYOB-native ✅ Fast value | ❌ Needs separate Shopify-automation workstream ❌ MYOB remains inventory ceiling | CEO happy; advisor partly satisfied |
| **Path 2 (Unleashed/Cin7 hub)** | ✅ Single hub solves all three problems ✅ Scales | ❌ Migration risk ❌ Middleware for MYOB (no native connector) | Strategically stronger; higher risk |
| **Path 4 (MYOB Acumatica)** | ✅ MYOB-family platform upgrade ✅ Built-in WMS/mfg | ❌ Highest cost ❌ Bigger change | Future scaling answer |

**Resolution Strategy**: PHASE + PRIORITISE — decide the source of truth explicitly **before** product selection (BR-001, principle P6); default to the lowest-risk MYOB-native Path 1 unless the CEO elects a transformational appetite.

**Decision**: Deferred to a formal decision gate (ADR pending) informed by BR-009 quantification and CEO appetite. Recommended default: Path 1 (MYOB-native), with a parallel Shopify-automation workstream.

**Decision Authority**: CEO (per STKE RACI), advised by Chris McKelt.

**Stakeholder Management**: If Path 1 is chosen, the advisor's strategic concern is managed by keeping Path 4 as the documented future scaling option.

### Conflict C-2: "We need a WMS" vs the deeper multichannel problem

**Conflicting Requirements**: BR-004 (warehouse discipline) vs BR-002/BR-003 (eliminate manual stores / oversell).

**Nature of Conflict**: Solving the warehouse in isolation leaves the higher-urgency manual-store and single-truth problems unsolved [CB-C4].

**Resolution Strategy**: PHASE — sequence the rollout to start with the highest-pain channel (the manual Shopify stores) rather than the warehouse alone [CB-C8].

**Decision Authority**: COO, endorsed by CEO.

### Conflict C-3: Efficiency/automation vs team job security

**Conflicting Requirements**: BR-002/BR-004 (automation) vs SD-3 (team role security).

**Resolution Strategy**: INNOVATE + COMPROMISE — involve the five staff as process experts (BR-009 discovery), reframe automation as removing drudgery and redeploying to higher-value work, and train through a phased rollout.

**Decision Authority**: COO.

### Conflict C-4: Speed/cost vs de-risking (pilot)

**Conflicting Requirements**: BR-010 (control cost/speed) vs BR-007 (pilot + failure-mode testing before cutover).

**Resolution Strategy**: PRIORITISE de-risking — the pilot is a mandatory go/no-go gate; it is cheap insurance against live oversell/duplicate-order incidents [CB-C5].

**Decision Authority**: CEO.

### Conflict C-5: MYOB-native + low integration risk vs richest multichannel capability

**Conflicting Requirements**: NFR-I-001/INT-001 (MYOB-native, low sync risk — favours Datapel/Ostendo) vs FR-002 richest multichannel breadth (favours hubs like Cin7/Odoo with broader native connectors but middleware-to-MYOB).

**Trade-off Analysis**: MYOB-native products minimise the idempotent-sync risk but may have lighter Shopify-multi-store/Magento breadth; hubs offer broader connectors but reintroduce middleware between the master and MYOB accounting (R-1).

**Resolution Strategy**: PRIORITISE integration risk (Principles P9, P10) — favour MYOB-native, and make Shopify-multi-store connector depth a gating evaluation criterion for the MYOB-native shortlist (Datapel vs Ostendo).

**Decision Authority**: CEO + advisor, at evaluation/scoring.

---

## Timeline and Milestones

| Milestone | Description | Target Date | Dependencies |
|-----------|-------------|-------------|--------------|
| Requirements Approval | Stakeholder sign-off on requirements | [PENDING] | This document |
| Operational Quantification | Discovery data pack complete (BR-009) | [PENDING] | Requirements |
| Source-of-Truth Decision | Path 1/2/4 ADR accepted (C-1) | [PENDING] | Quantification |
| Vendor Selection | Evaluate + score shortlist | [PENDING] | Decision, references |
| Pilot (one channel) | Real-data pilot, failure modes tested | [PENDING] | Selection |
| Phased Rollout | Channel-by-channel, highest pain first | [PENDING] | Pilot pass |

---

## Budget

### Cost Estimate (indicative, AUD — pending BR-009 quantification)

| Category | Estimated Cost | Notes |
|----------|----------------|-------|
| Software licence | Path-dependent | Path 1 lowest; Path 4 highest |
| Implementation / integration | Path-dependent | AU implementation partner |
| Carrier/shipping tool | Modest | Aggregator subscription |
| Training | Modest | 5-person team |
| **Indicative 3-yr TCO** | **~A$55k–135k** | Path 1 (Datapel) low end; transformational paths high end |

### Ongoing Operational Costs

| Category | Annual Cost | Notes |
|----------|-------------|-------|
| Licence/subscription | Path-dependent | Per-user or per-tier |
| Support | Path-dependent | Reference-checked SLA (NFR-M-003) |

---

## Approval

### Requirements Review

| Reviewer | Role | Status | Date | Comments |
|----------|------|--------|------|----------|
| Nathan Dyke | CEO / Business Sponsor | [ ] Approved | [PENDING] | |
| Kirralee Dyke | COO / Operational Sponsor | [ ] Approved | [PENDING] | |
| Chris McKelt | Solution Architecture Advisor | [ ] Approved | [PENDING] | |

### Sign-Off

| Stakeholder | Signature | Date |
|-------------|-----------|------|
| Nathan Dyke, CEO | _________ | [PENDING] |
| Kirralee Dyke, COO | _________ | [PENDING] |

---

## Appendices

### Appendix A: Glossary

- **System of record / single source of truth**: The one authoritative system for a data domain (here, inventory).
- **Idempotent**: An operation that has the same effect whether applied once or many times (prevents duplicate orders/stock movements).
- **Oversell**: Selling stock that is not actually available because channels are out of sync.
- **BOM**: Bill of materials — the component structure of a manufactured item.
- **WMS**: Warehouse management system — bins, directed picking, barcode scanning, cycle counts.
- **Path 1 / 2 / 4**: Source-of-truth options — MYOB-native WMS (1), inventory hub (2), MYOB Acumatica platform upgrade (4).

### Appendix B: Reference Documents

- `ARC-000-PRIN-v1.0` — Cycle Motion Architecture Principles (P1–P18)
- `ARC-001-STKE-v1.0` — Stakeholder Drivers & Goals Analysis (G-1–G-7, SD-1–6, conflicts C-1–4)
- `ARC-001-RSCH-v1.0` — Research Findings (vendor shortlist, MYOB-native analysis, TCO)
- `company-brief.md`, `stakeholders.md` — source material

---

## External References

> This section provides traceability from generated content back to source documents.
> Follow citation instructions in the project's citation reference guide.

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| CB | company-brief.md | Company Brief & Project Overview | 000-global/external/ | Verified company profile and inventory/warehouse project brief |
| STK | stakeholders.md | Stakeholder Map | 000-global/external/ | Cyclemotion stakeholder list — leadership, operations team |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| CB-C1 | CB | A2 / A3 | Business Requirement | "Cycle Motion is an Australian manufacturer and distributor trading across both wholesale (B2B) and direct-to-consumer (B2C) channels ... the B2B store runs on Magento ... the B2C stores on Shopify ... MYOB sits behind everything as the accounting, inventory and manufacturing system of record." |
| CB-C2 | CB | A2 / B3 | Functional Requirement | "in-house manufacturing with bill-of-materials (BOM) requirements — consistent with its custom wheel-build line ... Manufacturing / BOM requirements preserved and supported." |
| CB-C3 | CB | B1 / B2 | Integration Requirement | "5× Shopify — B2C | None — orders and inventory keyed into MYOB by hand ... oversell exposure because stock is never synced in real time across channels." |
| CB-C4 | CB | B2 | Business Requirement | "a fragmented systems architecture with no automated single source of inventory truth ... a capable accounting platform, but not a multichannel inventory engine — it becomes the ceiling on scaling channels and order volume." |
| CB-C5 | CB | B7 | Design Decision | "Pilot on one channel with real data before any full cutover. Explicitly test the failure modes that break these integrations: duplicate orders and oversell on simultaneous sales." |
| CB-C6 | CB | B5 | Procurement Constraint | "Recommendation: buy, do not build. A custom WMS build ... is assessed as high-risk ... A custom build means owning all maintenance, bugs and support indefinitely." |
| CB-C7 | CB | B4 | Design Decision | "Where should the single source of inventory truth live going forward? ... Every downstream choice ... hangs off one question." |
| CB-C8 | CB | B7 | Design Decision | "Phase the rollout — start with the pain bleeding most (likely the five manual Shopify stores) rather than a big-bang cutover." |
| CB-C9 | CB | B3 / B7 | Non-Functional Requirement | "An architecture that scales with channel and volume growth." / "Quantify the operation — SKU count, monthly order volume per channel, MYOB edition, must-have workflows (BOM, multi-location) — so vendors quote against reality." |
| CB-C10 | CB | B8 | Risk Factor | "the brief states seven storefronts total but enumerates one B2B + five B2C (six) ... Confirm the exact number ... before scoping connectors, as this directly drives integration count and licensing." |
| STK-C1 | STK | Key Stakeholders | Stakeholder Need | "Nathan Dyke | CEO ... Primary executive stakeholder. Likely decision-maker for business priorities, investment, and strategic change." |
| STK-C2 | STK | Key Stakeholders | Stakeholder Need | "Kirralee Dyke | COO ... Operations, supply chain, order fulfilment, process management ... Primary operational stakeholder." |
| STK-C3 | STK | Operations Team | Stakeholder Need | "Order and Supply Chain Team | 5 staff ... Important for understanding manual work, bottlenecks, exceptions, and opportunities for process improvement or automation." |
| STK-C4 | STK | Key Stakeholders | Stakeholder Need | "Nathan Dyke | CEO | Went to school with Chris McKelt" |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| .gitkeep | 000-global/external/ | Placeholder file, no content |

---

**Generated by**: ArcKit `/arckit:requirements` command
**Generated on**: 2026-06-30
**ArcKit Version**: 5.15.1
**Project**: Inventory & Warehouse Management Uplift (Project 001)
**Model**: Claude Opus 4.8 (1M context)
**Generation Context**: Derived from ARC-001-STKE, ARC-000-PRIN, ARC-001-RSCH, and external company-brief.md / stakeholders.md. No formal REQ predecessor.
</content>

<!-- arckit-provenance:start -->

## Build Provenance

_Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix._

| Field | Value |
|-------|-------|
| Requested Effort | `max` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-06-30T01:37:56.291Z |

<!-- arckit-provenance:end -->
