# Cycle Motion Enterprise Architecture Principles

> **Template Origin**: Official | **ArcKit Version**: 5.15.1 | **Command**: `/arckit:principles`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-000-PRIN-v1.0 |
| **Document Type** | Enterprise Architecture Principles |
| **Project** | Cycle Motion — Cross-Project Standards (Project 000) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-06-29 |
| **Last Modified** | 2026-06-29 |
| **Review Cycle** | Annual |
| **Next Review Date** | 2027-06-29 |
| **Owner** | Fred, CEO — Cycle Motion (Executive Sponsor) |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Cycle Motion leadership, delivery partners, and implementation vendors |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-06-29 | ArcKit AI | Initial creation from `/arckit:principles` command, tailored for Cycle Motion (Australian multichannel cycling manufacturer/distributor) | PENDING | PENDING |

---

## Executive Summary

This document establishes the principles governing all technology architecture decisions at **Cycle Motion Pty Ltd** — an Australian manufacturer and distributor of performance cycling components, trading across wholesale (B2B) and direct-to-consumer (B2C) channels [CB-C1]. These principles ensure that as Cycle Motion modernises its inventory, warehouse, and multichannel commerce systems, every decision is consistent, secure, scalable, and aligned with the business goal of a reliable single source of inventory truth.

**Scope**: All technology systems, integrations, and initiatives at Cycle Motion
**Authority**: Cycle Motion leadership (CEO as Executive Sponsor)
**Compliance**: Mandatory unless an exception is approved (see Section VI)

**Philosophy**: These principles are **technology-agnostic** — they describe WHAT qualities the architecture must have, not HOW to implement them with specific products. They are deliberately **right-sized for a small business**: pragmatic, biased toward proven commodity products over custom builds, and focused on the few qualities that protect revenue and reputation. Technology selection (WMS, inventory hub, connectors) happens during research and design phases, guided by these principles.

**How to read each principle**: Every principle carries a statement (with MUST/SHOULD/MAY), the rationale, the implications for design, validation gates to test compliance objectively, a good-versus-bad example, and the common violations to watch for.

---

## I. Strategic Principles

### 1. Buy Over Build for Commodity Capability

**Principle Statement**:
Cycle Motion MUST acquire proven, supported products for commodity capabilities (warehouse management, inventory sync, accounting, e-commerce) and reserve custom engineering effort for configuration, integration, and genuine points of differentiation.

**Rationale**:
"Build where you differentiate, buy where you don't." Warehouse picking, stock sync, and payment handling are mature, commoditised categories — table stakes, not competitive advantage [CB-C1]. A custom build means owning all maintenance, bugs, and a permanent treadmill of keeping pace with third-party API changes, plus significant key-person risk — the opposite of a low-risk outcome for a small team [CB-C2].

**Implications**:

- Prefer configurable off-the-shelf products with active vendor support over bespoke code
- Engineering effort is directed to configuration and integration, where the real value and risk sit [CB-C3]
- Vendor support quality is a first-class selection criterion, not an afterthought
- Total cost of ownership (licence + integration + support) is assessed over a multi-year horizon, not just upfront price
- Reference-check vendor support specifically before committing

**Validation Gates**:

- [ ] Capability classified as differentiator vs commodity before any build decision
- [ ] For commodity capability, market products evaluated before custom build considered
- [ ] Vendor support model and reference checks documented
- [ ] Build decisions justified by genuine differentiation, not convenience

**Good vs Bad**:

- ✅ **Good**: Adopting a purpose-built warehouse/inventory product and investing effort in clean integration to the system of record.
- ❌ **Bad**: Hand-coding a bespoke WMS — bins, pick paths, barcode scanning, carrier integration — then owning every bug and API break forever.

**Common Violations**:

- Building custom software for a problem already solved by mature products
- Selecting on licence price alone, ignoring support quality and integration cost
- Treating integration as trivial "glue" rather than the place real risk lives

---

### 2. Scalability and Elasticity

**Principle Statement**:
All systems MUST be designed to scale with channel and order-volume growth without re-architecture, supporting additional storefronts and SKUs as the business grows.

**Rationale**:
Cycle Motion runs one B2B and several B2C storefronts today and intends to add channels and volume [CB-C4]. The architecture must absorb new storefronts and higher order throughput without becoming the ceiling on growth — the role MYOB currently and uncomfortably plays as the inventory brain [CB-C2].

**Implications**:

- Adding a sales channel should be a configuration/connector exercise, not a redesign
- The inventory system of record must handle multichannel volume, not just accounting load
- Avoid hard-coded assumptions about the number of channels, SKUs, or warehouse locations
- Capacity (order throughput, SKU count) is sized against realistic growth, not just today

**Validation Gates**:

- [ ] New storefront can be onboarded without architectural change
- [ ] System of record sized for multichannel order volume, not single-channel
- [ ] No hard limits on channels, SKUs, or locations in the design
- [ ] Growth assumptions documented and tested

**Good vs Bad**:

- ✅ **Good**: A sixth storefront is connected to the inventory hub through a standard connector in days, with no core change.
- ❌ **Bad**: Each new channel requires bespoke re-keying or a custom one-off integration that nobody else can maintain.

**Common Violations**:

- Channels integrated by manual re-keying that does not scale with volume [CB-C5]
- An accounting platform pressed into service as a high-volume inventory engine
- Capacity sized for today's order count with no headroom for growth

---

### 3. Interoperability and Integration

**Principle Statement**:
All systems MUST exchange data through well-defined, supported interfaces (published APIs or vendor connectors). Manual re-keying between systems and direct database coupling across product boundaries are prohibited.

**Rationale**:
Cycle Motion's pain is a fragmented landscape where one channel is properly wired in and the rest are run by hand off paper [CB-C5]. Reliable, automated interfaces between commerce, inventory, accounting, and the warehouse are the backbone of every objective in the project. Standard interfaces also keep the business free to change any one product later without breaking the others.

**Implications**:

- Every channel integrates to the system of record via automated interface, never manual entry [CB-C5]
- Use products' supported APIs/connectors rather than unsupported back-door integrations
- Document the interface contract for each integration (fields, direction, frequency, error handling)
- No direct database access into a third-party product's internals
- Prefer products with mature, documented connectors for the platforms in use

**Validation Gates**:

- [ ] Every active channel connected by automated interface (no manual re-keying)
- [ ] Integration contracts documented (direction, fields, frequency, error handling)
- [ ] Only supported/published interfaces used
- [ ] No system reads another product's database directly

**Good vs Bad**:

- ✅ **Good**: Orders flow automatically from every storefront into the system of record; stock levels flow back out — all through supported connectors.
- ❌ **Bad**: B2C orders re-keyed into accounting by hand each day, with errors and lag baked into the process [CB-C5].

**Common Violations**:

- Manual data entry standing in for a real integration
- Unsupported, brittle back-door integrations into product databases
- Undocumented integrations that only one person understands

---

### 4. Security by Design (NON-NEGOTIABLE)

**Principle Statement**:
All systems MUST be secure by design, applying least-privilege access, encryption in transit and at rest, and protection of customer and payment data. Security is NOT a feature to be added later — it is a foundational requirement.

**Rationale**:
Cycle Motion holds customer personal data and processes payments across its storefronts. A breach is an existential reputational and legal risk for a small business. Security must assume breach, eliminate implicit trust, and protect data everywhere it flows.

**Mandatory Controls**:

- [ ] Multi-factor authentication for all administrative and staff access to commerce, inventory, and accounting systems
- [ ] Least-privilege roles — staff and integrations granted only the access they need
- [ ] Secrets and API credentials held in a secure store, never in code, spreadsheets, or email
- [ ] Encryption in transit for all integrations and customer-facing traffic
- [ ] Encryption at rest for all stores holding customer, order, or payment data
- [ ] Logging of authentication and administrative actions across core systems
- [ ] Regular patching and vulnerability review of internet-facing storefronts

**Exceptions**:

- NONE. Security principles are non-negotiable.
- Specific control implementations may vary with documented compensating controls.

**Validation Gates**:

- [ ] Customer and payment data flows identified and protected end to end
- [ ] MFA enforced on all admin access
- [ ] Credentials managed in a secure store
- [ ] Patching/vulnerability process defined for internet-facing systems

**Good vs Bad**:

- ✅ **Good**: Integration credentials stored in a secrets vault; each connector has its own least-privilege account; admin logins require MFA.
- ❌ **Bad**: A shared admin password reused across storefronts and stored in a spreadsheet, with API keys pasted into integration scripts.

**Common Violations**:

- API keys or passwords stored in code, config, or shared documents
- Shared accounts that defeat least privilege and accountability
- Internet-facing commerce platforms left unpatched

---

### 5. Observability and Operational Excellence

**Principle Statement**:
All systems and integrations MUST surface enough monitoring and alerting to detect failures — especially failed syncs, stuck orders, and stock discrepancies — before they reach customers.

**Rationale**:
A small team cannot watch every integration by hand. Silent failures in stock sync or order flow are exactly what cause oversell and lost orders. The business must be told when an integration breaks, not discover it through an angry customer [CB-C6].

**Implications**:

- Integrations report success/failure and alert a human on failure
- Failed or stuck orders are visible and recoverable, not silently dropped
- Stock discrepancies between channels and the system of record are detectable
- Keep a simple, watchable operational view appropriate to a small team — not an enterprise observability stack

**Validation Gates**:

- [ ] Integration failures raise an alert to a named person
- [ ] Failed/stuck orders are visible and recoverable
- [ ] Stock-level discrepancies are detectable and reconcilable
- [ ] Someone is accountable for responding to alerts

**Good vs Bad**:

- ✅ **Good**: A failed order-sync raises an alert and lands in a retry/exception queue the team reviews daily.
- ❌ **Bad**: A connector silently stops syncing for a week and the first sign is overselling stock the business no longer has.

**Common Violations**:

- Integrations that fail silently with no alert
- No way to see or replay orders that failed to sync
- Alerts with no owner, so nobody acts on them

---

## II. Data Principles

### 6. Single Source of Inventory Truth

**Principle Statement**:
Every core data domain — above all **inventory** — MUST have one agreed authoritative system of record. All other systems hold synchronised copies that are clearly subordinate to it.

**Rationale**:
This is the central architectural decision for Cycle Motion: *where should the single source of inventory truth live?* [CB-C2]. Today inventory truth lives in an accounting platform never designed for multichannel stock, and channels can disagree on availability [CB-C2]. A single, authoritative inventory source is the foundation that eliminates oversell and manual reconciliation, and every downstream choice hangs off it [CB-C2].

**Implications**:

- The system of record for inventory is decided explicitly and documented before product selection [CB-C2]
- All channels read availability from, and write movements to, that single source
- Other systems hold read/synchronised copies, never competing masters
- Avoid bidirectional "both are master" arrangements that create split-brain stock counts
- Manufacturing / bill-of-materials data is preserved and owned by a defined system [CB-C7]

**Validation Gates**:

- [ ] Inventory system of record explicitly agreed and documented
- [ ] Every channel sources availability from that single source
- [ ] No two systems both claim to master stock for the same SKU
- [ ] BOM/manufacturing ownership defined [CB-C7]

**Good vs Bad**:

- ✅ **Good**: One inventory master; all storefronts and the warehouse sync to it; accounting receives movements for the books.
- ❌ **Bad**: Each storefront keeps its own stock count and the warehouse keeps a third on paper, so no two figures agree.

**Common Violations**:

- Multiple systems independently editing stock for the same SKU
- Paper-based warehouse counts that diverge from every digital system [CB-C5]
- Treating a synchronised copy as if it were authoritative

---

### 7. Data Sovereignty and Customer Privacy (Australian)

**Principle Statement**:
Customer and personal data MUST be handled in line with the Australian Privacy Principles (APPs) under the Privacy Act 1988, with data residency, retention, and access controls appropriate to a customer-facing Australian business.

**Rationale**:
Cycle Motion is an Australian company trading directly with consumers and trade customers [CB-C8], collecting personal data (names, addresses, contact and order details). The Australian Privacy Principles set the baseline for how that data is collected, used, stored, disclosed, and secured. Even where a small-business turnover exemption might apply, treating the APPs as the standard is the prudent and trust-building choice for a consumer brand.

**Implications**:

- Personal data collection is limited to what each channel genuinely needs (data minimisation)
- Customer data is retained only as long as needed and disposed of securely
- Access to customer data is on a need-to-know basis with least privilege
- Data residency and cross-border transfer (e.g., overseas-hosted platforms or vendors) are understood and consistent with APP obligations
- A clear, accurate privacy notice is provided to customers

> **Verify**: Confirm whether Cycle Motion falls under the Privacy Act small-business exemption (turnover threshold and whether it trades in personal information). Regardless of exemption status, APP-aligned handling is the recommended baseline. Consider running `/arckit:au-pia` for a full Privacy Impact Assessment.

**Validation Gates**:

- [ ] Personal data inventory and flows documented per channel
- [ ] Data minimisation applied to collection
- [ ] Retention and secure-disposal rules defined
- [ ] Data residency / cross-border position understood for each platform and vendor
- [ ] Customer privacy notice in place

**Good vs Bad**:

- ✅ **Good**: Each storefront collects only the data needed to fulfil an order, access is role-restricted, and retention is defined.
- ❌ **Bad**: Full customer exports copied into spreadsheets and shared widely, kept indefinitely with no access control.

**Common Violations**:

- Customer data over-collected or retained indefinitely "just in case"
- Personal data copied into uncontrolled spreadsheets or test systems
- No awareness of where customer data physically resides across platforms and vendors

---

### 8. Data Quality and Reconciliation

**Principle Statement**:
Master data (SKUs, products, pricing, stock) MUST be kept accurate and consistent across systems, with the ability to detect and reconcile discrepancies between channels and the system of record.

**Rationale**:
Multichannel commerce lives or dies on data quality. Inconsistent SKUs, prices, or stock counts across channels produce oversell, mispricing, and customer-facing errors. The business needs to trust that what a storefront shows matches what the system of record holds.

**Implications**:

- A consistent SKU/product definition is shared across channels
- Pricing and availability flow from defined sources, not edited independently per channel
- Discrepancies between a channel and the system of record are detectable and reconcilable
- Validation is applied at the point of data entry, not patched downstream

**Validation Gates**:

- [ ] Consistent SKU/product master shared across channels
- [ ] Pricing and availability sourced from defined systems
- [ ] Reconciliation process exists for channel vs system-of-record discrepancies
- [ ] Validation enforced at data entry

**Good vs Bad**:

- ✅ **Good**: One product master propagates to every channel; a daily reconciliation flags any drift in stock or price.
- ❌ **Bad**: The same product carries different SKUs and prices on three storefronts, edited by hand, with no way to tell which is right.

**Common Violations**:

- Product/SKU definitions maintained independently per channel
- No reconciliation, so drift is discovered only when a customer complains
- Validation deferred downstream instead of enforced at entry

---

## III. Integration Principles

### 9. Loose Coupling

**Principle Statement**:
Systems MUST be loosely coupled through supported interfaces so that any one product (commerce platform, WMS, inventory hub, accounting) can be changed or replaced without forcing changes in the others.

**Rationale**:
Cycle Motion's landscape will keep evolving — adding a WMS, possibly a hub, more storefronts. Loose coupling through clean interfaces means the business is never locked into one product because everything is hard-wired to it, and a future change to one system does not cascade into all the others [CB-C3].

**Implications**:

- Integrate through documented interfaces, not shared databases or product internals
- Each product owns its own data and exposes it through its interface
- Keep integration logic in a clear, replaceable layer rather than buried inside each product
- Favour standard connectors that can be swapped if a product changes

**Validation Gates**:

- [ ] Systems integrate via interfaces, not shared databases
- [ ] Each product can be replaced without redesigning the others
- [ ] Integration logic lives in a defined, documented layer
- [ ] No hidden coupling through product internals

**Good vs Bad**:

- ✅ **Good**: Swapping one storefront platform means re-pointing one connector, not rebuilding the whole estate.
- ❌ **Bad**: Inventory, orders, and accounting so entangled that no single product can be changed without breaking the rest.

**Common Violations**:

- Integration via shared database tables instead of interfaces
- Business logic duplicated and entangled across products
- Lock-in created by hard-wiring everything to one platform's internals

---

### 10. Reliable, Idempotent Synchronisation

**Principle Statement**:
Cross-system synchronisation (stock, orders) MUST be near-real-time where it prevents oversell, and MUST be idempotent and recoverable so that retries and simultaneous sales never create duplicate orders or oversold stock.

**Rationale**:
The two failure modes that break exactly these integrations are **duplicate orders** and **oversell on simultaneous sales** [CB-C6]. Stock that is never synced in real time across channels is the direct cause of oversell exposure [CB-C5]. Synchronisation must therefore be timely, safe to retry, and able to recover from failure without double-processing.

**Implications**:

- Stock availability syncs across channels quickly enough to prevent overselling [CB-C5]
- Order and stock updates are idempotent — processing the same message twice has no ill effect [CB-C6]
- Failed syncs are queued and retried, not lost or silently duplicated
- Concurrency on the same SKU across channels is handled safely
- These failure modes are explicitly tested before any cutover [CB-C6]

**Validation Gates**:

- [ ] Stock sync latency is low enough to prevent oversell
- [ ] Order/stock operations are idempotent (safe to retry)
- [ ] Failed messages are queued, retried, and recoverable
- [ ] Duplicate-order and simultaneous-sale scenarios explicitly tested [CB-C6]

**Good vs Bad**:

- ✅ **Good**: A retried order carries an idempotency key, so a network hiccup never creates a second order or double-decrements stock.
- ❌ **Bad**: A timeout triggers a blind retry that places the order twice and oversells the last unit to two customers.

**Common Violations**:

- Non-idempotent retries that duplicate orders or stock movements
- Stock sync too slow to prevent oversell across channels
- No test coverage for simultaneous sales of the last unit

---

## IV. Quality Attributes

### 11. Performance and Efficiency

**Principle Statement**:
Customer-facing storefronts and core integrations MUST meet defined responsiveness targets under realistic load, sized to actual order volumes per channel.

**Rationale**:
Slow storefronts lose sales and slow syncs widen the oversell window. Targets should be grounded in Cycle Motion's real numbers — SKU count and monthly order volume per channel — so the architecture is sized against reality, not guesswork [CB-C9].

**Implications**:

- Define responsiveness targets for storefronts and sync latency targets for integrations
- Quantify the operation (SKU count, monthly orders per channel) so sizing is realistic [CB-C9]
- Validate performance against realistic data volumes before cutover
- Monitor responsiveness in production, not just at launch

**Validation Gates**:

- [ ] Storefront responsiveness and sync-latency targets defined
- [ ] Operation quantified (SKUs, orders/month per channel) [CB-C9]
- [ ] Performance validated against realistic volumes
- [ ] Responsiveness monitored in production

**Good vs Bad**:

- ✅ **Good**: Targets agreed up front (e.g., storefront pages respond in < 2 seconds, stock sync within minutes), tested against real SKU volumes.
- ❌ **Bad**: No targets; the first sign of a problem is a slow storefront during a sale and stock that syncs hours later.

**Common Violations**:

- No measurable performance or sync-latency targets
- Sizing based on guesswork rather than real channel volumes
- Testing against trivial data that hides real-world slowness

---

### 12. Availability and Reliability

**Principle Statement**:
Customer-facing storefronts and the inventory system of record MUST meet defined availability targets, with tested backup and recovery so that an outage never means lost orders or lost stock data.

**Rationale**:
Storefront downtime is lost revenue; loss of inventory data is operational chaos. A small business cannot afford an untested recovery plan. Availability and recoverability must be defined and proven, proportionate to the cost of downtime.

**Implications**:

- Define availability expectations for storefronts and the system of record
- Define how much downtime and data loss is tolerable (recovery time and recovery point)
- Back up core data (inventory, orders, customers, accounting) and test the restore
- Rely on vendor-provided resilience where products are hosted, and verify it

**Validation Gates**:

- [ ] Availability expectations defined for storefronts and system of record
- [ ] Tolerable downtime and data loss documented
- [ ] Backups exist for core data and restore is tested
- [ ] Vendor resilience/SLA understood for hosted products

**Good vs Bad**:

- ✅ **Good**: Core data backed up daily with a periodically tested restore; storefront and system-of-record SLAs understood and monitored.
- ❌ **Bad**: Backups assumed to exist but never restored — discovered to be unusable only after data is lost.

**Common Violations**:

- Backups never test-restored
- Recovery expectations undefined until an outage forces the question
- Blind reliance on a vendor's resilience without verifying the SLA

---

### 13. Maintainability and Evolvability

**Principle Statement**:
The systems landscape and its integrations MUST be documented and configured for change, so a small team or a new partner can understand and safely evolve it without depending on one person's memory.

**Rationale**:
A manual, undocumented warehouse process and bespoke integrations create key-person and scaling risk [CB-C2]. Documentation and clean configuration reduce that risk and let Cycle Motion bring in partners or staff without the architecture being a black box.

**Implications**:

- The systems landscape, integrations, and key configurations are documented and kept current
- Significant decisions (e.g., the inventory system-of-record choice) are recorded with rationale
- Favour configuration over custom code so changes are visible and reversible
- Reduce reliance on undocumented, in-someone's-head processes

**Validation Gates**:

- [ ] Systems and integration landscape documented and current
- [ ] Key decisions recorded with rationale (Architecture Decision Records)
- [ ] Configuration favoured over bespoke code where practical
- [ ] No critical process dependent solely on one person's knowledge

**Good vs Bad**:

- ✅ **Good**: A current systems diagram, documented integrations, and recorded decisions let a new partner get productive quickly.
- ❌ **Bad**: Warehouse and integration knowledge lives only in one person's head, so their absence stops the business [CB-C2].

**Common Violations**:

- Undocumented integrations and warehouse processes (key-person risk)
- Significant decisions left unrecorded
- Bespoke code where configuration would have been visible and maintainable

---

## V. Commerce and Customer Principles

### 14. Payment Security and PCI-DSS Alignment

**Principle Statement**:
All handling of payment card data MUST align with PCI-DSS, minimising the cardholder data Cycle Motion ever touches by using compliant payment providers and keeping card data out of internal systems.

**Rationale**:
As a B2B and B2C retailer, Cycle Motion processes card payments. Cardholder data is the highest-risk data the business handles, and PCI-DSS is the mandatory standard. The cheapest and safest path for a small business is to minimise scope — let compliant providers handle card data so it never lands in Cycle Motion's own systems.

**Implications**:

- Use PCI-DSS-compliant payment providers; do not store raw card numbers internally
- Keep payment capture within the provider's compliant boundary (e.g., hosted/tokenised flows)
- Card data is never written to logs, spreadsheets, emails, or order exports
- Understand and maintain the applicable PCI-DSS self-assessment obligations

**Validation Gates**:

- [ ] Payment handling uses PCI-DSS-compliant providers
- [ ] No raw card data stored in internal systems, logs, or exports
- [ ] PCI-DSS scope minimised and self-assessment obligations understood
- [ ] Payment flows reviewed as part of security validation

**Good vs Bad**:

- ✅ **Good**: Checkout tokenises payment through a compliant provider; Cycle Motion systems only ever see a token, never a card number.
- ❌ **Bad**: Card details captured into the order record or emailed to staff to key in manually.

**Common Violations**:

- Storing or emailing raw card data
- Expanding PCI scope by routing card data through internal systems
- Treating PCI-DSS as a one-off rather than an ongoing obligation

---

### 15. Order Integrity and Customer Trust

**Principle Statement**:
The architecture MUST protect order integrity end to end — accurate availability, no overselling, no duplicate or dropped orders — because every such failure is a direct hit to customer trust.

**Rationale**:
Oversell, duplicated orders, and stockouts are not just operational annoyances — they are broken promises to customers and trade partners. Eliminating them is the primary business outcome of this whole programme [CB-C5]. Order integrity is therefore a principle in its own right, served by single-source-of-truth (P6) and reliable synchronisation (P10).

**Implications**:

- Availability shown to customers reflects true, current stock
- An order accepted is an order that can be fulfilled (no overselling the last unit)
- Every order from every channel reaches the system of record exactly once
- Order-integrity failure modes are tested with real data before cutover [CB-C6]
- Rollout is phased, starting with the channels bleeding most, to reduce risk [CB-C6]

**Validation Gates**:

- [ ] Customer-visible availability reflects true stock
- [ ] Oversell prevented across all channels
- [ ] Every order reaches the system of record exactly once
- [ ] Integrity failure modes tested on a pilot channel before full cutover [CB-C6]

**Good vs Bad**:

- ✅ **Good**: A pilot on one channel proves no oversell and no duplicate orders under simultaneous sales before any wider rollout [CB-C6].
- ❌ **Bad**: A big-bang cutover across all channels at once, discovering the oversell and duplicate-order bugs live, in front of customers.

**Common Violations**:

- Showing stale availability that lets customers buy unavailable stock
- Big-bang cutovers with no piloted proof of order integrity [CB-C6]
- Accepting orders the business cannot actually fulfil

---

## VI. Development and Delivery Practices

### 16. Configuration and Integration Over Custom Code

**Principle Statement**:
Delivery effort MUST favour configuring and integrating supported products over writing and owning custom code, with configurations version-controlled and reproducible.

**Rationale**:
For a small business, every line of bespoke code is a permanent maintenance liability. The real value and the real risk sit in configuration and integration, not in re-building commodity capability [CB-C3]. Keeping configuration controlled and reproducible avoids undocumented drift.

**Implications**:

- Solve problems by configuration first; build custom only where it differentiates (see P1)
- Integration and key configurations are version-controlled and documented
- Environments and integrations are reproducible, not hand-assembled and forgotten
- Custom code, where unavoidable, is minimal, tested, and documented

**Validation Gates**:

- [ ] Configuration preferred over custom code, with build decisions justified
- [ ] Integration/config under version control and documented
- [ ] Setup is reproducible, not manually assembled
- [ ] Any custom code is minimal, tested, and documented

**Good vs Bad**:

- ✅ **Good**: Connector and product configuration captured in version control, so the integration can be rebuilt and reviewed.
- ❌ **Bad**: A pile of one-off scripts and hand-tweaked settings nobody can reproduce or explain.

**Common Violations**:

- Custom code for problems configuration could solve
- Configuration changes made by hand with no record
- Integrations that cannot be reproduced from a documented source

---

### 17. Test the Failure Modes Before Cutover

**Principle Statement**:
Significant changes MUST be validated — including the specific failure modes that break these integrations — on a pilot with real data before any full cutover.

**Rationale**:
The brief is explicit: pilot on one channel with real data and test the failure modes that break these integrations, namely duplicate orders and oversell on simultaneous sales, before committing [CB-C6]. Testing the happy path is not enough; the failure paths are where customers get hurt.

**Implications**:

- Pilot changes on one channel with real data before wider rollout [CB-C6]
- Explicitly test duplicate-order and simultaneous-sale (oversell) scenarios [CB-C6]
- Validate data accuracy (stock, pricing, orders) end to end before cutover
- Phase the rollout to limit blast radius, starting with the highest-pain channel [CB-C6]

**Validation Gates**:

- [ ] Pilot on one channel with real data completed before cutover [CB-C6]
- [ ] Duplicate-order and oversell scenarios explicitly tested [CB-C6]
- [ ] End-to-end data accuracy validated
- [ ] Rollout phased, not big-bang [CB-C6]

**Good vs Bad**:

- ✅ **Good**: One channel piloted, failure modes deliberately provoked and proven handled, then rolled out channel by channel.
- ❌ **Bad**: All channels switched at once with only happy-path testing, hoping the edge cases never occur.

**Common Violations**:

- Cutting over with only happy-path testing
- Skipping the pilot and going straight to full rollout [CB-C6]
- Never testing the simultaneous-sale and duplicate-order cases

---

### 18. Change Management and Safe Migration

**Principle Statement**:
Changes to core systems MUST be reversible, with backups taken before migration and a defined rollback path, so a failed change never costs the business its data or its ability to trade.

**Rationale**:
Migrating the inventory system of record or reworking a working integration carries real migration risk [CB-C10]. For a business that depends on these systems to trade daily, every significant change needs a safety net.

**Implications**:

- Take and verify a backup before any data migration or major change
- Define a rollback path before starting a change
- Make changes during low-impact windows where possible
- Preserve the working B2B–system-of-record integration unless deliberately reworked with a fallback [CB-C10]

**Validation Gates**:

- [ ] Verified backup taken before migration/major change
- [ ] Rollback path defined and feasible before starting
- [ ] Change windows chosen to minimise trading impact
- [ ] Existing working integrations preserved or safely reworked [CB-C10]

**Good vs Bad**:

- ✅ **Good**: A migration runs with a verified backup and a tested rollback, executed in a quiet window, so a problem is recoverable.
- ❌ **Bad**: A live cutover with no backup and no way back, taking the business offline when it fails.

**Common Violations**:

- Major changes with no backup or rollback path
- Reworking a working integration with no fallback [CB-C10]
- High-risk changes run during peak trading

---

## VII. Exception Process

### Requesting Architecture Exceptions

Principles are mandatory unless a documented exception is approved by Cycle Motion leadership.

**Valid Exception Reasons**:

- Technical or vendor constraints that prevent compliance
- Regulatory or contractual requirements
- Transitional state during migration
- Time-boxed pilot or proof-of-concept

**Exception Request Requirements**:

- [ ] Justification with business/technical rationale
- [ ] Alternative approach and compensating controls
- [ ] Risk assessment and mitigation plan
- [ ] Expiration date (exceptions are time-bound)
- [ ] Remediation plan to achieve compliance

**Approval Process**:

1. Raise the exception with Cycle Motion leadership (CEO as sponsor)
2. Assess risk and compensating controls
3. CEO approval for exceptions to critical principles (Security, Single Source of Truth, Order Integrity)
4. Record the exception alongside the relevant project documentation
5. Review open exceptions periodically

> **Note**: Principle 4 (Security by Design) is non-negotiable. Exceptions may only vary *how* a control is implemented (with documented compensating controls), never *whether* security is applied.

---

## VIII. Governance and Compliance

### Architecture Review Gates

Significant initiatives should pass lightweight reviews at key points, proportionate to a small business:

**Before product selection**:

- [ ] Inventory system-of-record decision made and documented (P6)
- [ ] Buy-vs-build assessed for each capability (P1)
- [ ] Operation quantified (SKUs, order volumes) to brief vendors against reality

**Before cutover**:

- [ ] Integrations automated, documented, and idempotent (P3, P10)
- [ ] Security and payment data flows validated (P4, P14)
- [ ] Failure modes piloted on real data — oversell, duplicate orders (P15, P17)
- [ ] Backup and rollback in place (P18)

**After go-live**:

- [ ] Monitoring and alerting on integrations live (P5)
- [ ] Reconciliation confirming single source of truth holds (P6, P8)
- [ ] Documentation current (P13)

### Enforcement

- Reviews are expected for significant changes to core systems
- Critical-principle violations (Security, Single Source of Truth, Order Integrity, Payment Security) must be remediated before go-live
- Approved exceptions are time-bound and reviewed periodically

---

## IX. Appendix

### Principle Summary Checklist

| # | Principle | Category | Criticality | Validation |
|---|-----------|----------|-------------|------------|
| 1 | Buy Over Build for Commodity Capability | Strategic | HIGH | Build/buy justified, vendor support checked |
| 2 | Scalability and Elasticity | Strategic | HIGH | Add channel without redesign |
| 3 | Interoperability and Integration | Strategic | CRITICAL | All channels automated, no re-keying |
| 4 | Security by Design | Strategic | CRITICAL | MFA, secrets vault, encryption |
| 5 | Observability and Operational Excellence | Strategic | HIGH | Integration alerts, recoverable orders |
| 6 | Single Source of Inventory Truth | Data | CRITICAL | One agreed system of record |
| 7 | Data Sovereignty and Customer Privacy | Data | HIGH | APP-aligned handling, residency known |
| 8 | Data Quality and Reconciliation | Data | HIGH | Shared SKU master, reconciliation |
| 9 | Loose Coupling | Integration | HIGH | Products replaceable independently |
| 10 | Reliable, Idempotent Synchronisation | Integration | CRITICAL | Idempotent, no oversell/duplicates |
| 11 | Performance and Efficiency | Quality | MEDIUM | Targets vs real volumes |
| 12 | Availability and Reliability | Quality | HIGH | Tested backup/restore |
| 13 | Maintainability and Evolvability | Quality | MEDIUM | Documented, low key-person risk |
| 14 | Payment Security and PCI-DSS Alignment | Commerce | CRITICAL | No raw card data internally |
| 15 | Order Integrity and Customer Trust | Commerce | CRITICAL | No oversell, exactly-once orders |
| 16 | Configuration and Integration Over Custom Code | Delivery | HIGH | Config preferred, version-controlled |
| 17 | Test the Failure Modes Before Cutover | Delivery | CRITICAL | Pilot proves failure modes handled |
| 18 | Change Management and Safe Migration | Delivery | HIGH | Backup + rollback before change |

---

## External References

> This section provides traceability from generated content back to source documents.
> Follow citation instructions in the project's citation reference guide.

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| CB | company-brief.md | Company Brief & Project Overview | 000-global/external/ | Verified company profile and inventory/warehouse management project brief for Cycle Motion Pty Ltd |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| CB-C1 | CB | A2 / B5 | Design Decision | "Cycle Motion is an Australian manufacturer and distributor trading across both wholesale (B2B) and direct-to-consumer (B2C) channels." / "build where you differentiate, buy where you don't. Warehouse picking is table stakes, not a competitive differentiator." |
| CB-C2 | CB | B2 / B4 / B5 | Design Decision | "a fragmented systems architecture with no automated single source of inventory truth." / "Where should the single source of inventory truth live going forward?" / "a custom build means owning all maintenance, bugs and support indefinitely... significant key-person risk." |
| CB-C3 | CB | B5 | Design Decision | "Engineering effort should go to configuration and integration, where the real value and risk sit." |
| CB-C4 | CB | B3 | Non-Functional Requirement | "An architecture that scales with channel and volume growth." |
| CB-C5 | CB | B1 / B2 | Integration Requirement | "one channel is properly wired in, five are run by hand off paper" / "oversell exposure because stock is never synced in real time across channels." |
| CB-C6 | CB | B7 | Design Decision | "Pilot on one channel with real data before any full cutover. Explicitly test the failure modes that break these integrations: duplicate orders and oversell on simultaneous sales." / "Phase the rollout — start with the pain bleeding most." |
| CB-C7 | CB | B3 | Functional Requirement | "Manufacturing / BOM requirements preserved and supported." |
| CB-C8 | CB | A1 | Compliance Constraint | "Entity: Cycle Motion Pty Ltd ... Australian Private Company ... Location: WA 6090 (northern Perth)." |
| CB-C9 | CB | B7 | Non-Functional Requirement | "Quantify the operation — SKU count, monthly order volume per channel, MYOB edition, must-have workflows (BOM, multi-location) — so vendors quote against reality." |
| CB-C10 | CB | B4 / B7 | Risk Factor | "larger change with real migration risk; the existing MYOB–Magento integration is reworked." |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| .gitkeep | 000-global/external/ | Placeholder file, no content |

---

**Generated by**: ArcKit `/arckit:principles` command
**Generated on**: 2026-06-29
**ArcKit Version**: 5.15.1
**Project**: Cycle Motion — Cross-Project Standards (Project 000)
**Model**: Claude Opus 4.8 (1M context)
</content>

<!-- arckit-provenance:start -->

## Build Provenance

_Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix._

| Field | Value |
|-------|-------|
| Requested Effort | `high` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-06-29T23:01:47.056Z |

<!-- arckit-provenance:end -->
