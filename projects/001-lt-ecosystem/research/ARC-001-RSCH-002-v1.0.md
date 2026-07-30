# Technology and Vendor Market Research: Build versus Buy and Total Cost of Ownership

> **Template Origin**: Official | **ArcKit Version**: 6.7.5 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-RSCH-002-v1.0 |
| **Document Type** | Technology and Service Research (Market / Build-vs-Buy / TCO) |
| **Project** | Learning & Teaching Baseline Strategy (Project 001) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-29 |
| **Last Modified** | 2026-07-29 |
| **Review Cycle** | Quarterly — or on any vendor corporate event affecting a named product |
| **Next Review Date** | 2026-10-29 |
| **Owner** | Sam Okafor, Integration Architect — jointly with Grace Tanaka, Procurement & Vendor Manager |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Steering Committee, Digital & IT, Procurement, Learning Technologies, Finance, Education Committee, RIFF |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-29 | ArcKit AI | Initial creation from `/arckit:research`. Second research instance for project 001 — technology and vendor market research, deliberately scoped away from `ARC-001-RSCH-v1.0` | PENDING | PENDING |

---

## Reading This Document

### This is the second research artefact for project 001. Read the scope boundary first.

`ARC-001-RSCH-v1.0` already exists and holds the **target-organisation** research: strategy, decision rights, stakeholder structure, the existing-systems baseline, and a first pass of external vendor facts across the whole estate. **This document does not restate it and does not supersede it.**

This document is the **market and sourcing** artefact. It answers four questions that `ARC-001-RSCH-v1.0` either left open or explicitly deferred:

| # | Question this document answers | Where v1.0 left it |
|---|-------------------------------|--------------------|
| 1 | Which integration broker or iPaaS product, and does the Principle 19 test on the Microsoft agreement actually succeed? | Deferred — "PeopleSoft Integration Broker (not researched this pass)"; no broker market covered at all |
| 2 | What does the market say about the four declared rationalisation candidates? | Partially — §4.4 raised the Teams / Echo360 / Zoom question; the video toolchain, authoring and survey pairs were noted but not sourced against alternatives |
| 3 | What are Miro, OnExam and badging software actually going to cost, and are they procurable as named? | Miro only, at MEDIUM confidence; OnExam recorded as "Not identified"; badging not researched |
| 4 | Which capability gaps have no incumbent, per ADR-007 Gate 1? | Not addressed |

Where a fact already sits in `ARC-001-RSCH-v1.0`, this document **cites it rather than repeating it**. Where this document contradicts or sharpens it, that is stated explicitly in §11.

### It also does not duplicate project 004

`projects/004-integration-platform/` already holds vendor profiles for **Confluent**, **CloudAMQP** and **Microsoft Azure Integration Services**, plus tech notes on event-broker comparison and the schema-registry landscape. Those are cited as `[P4-*]` and **extended**, not restated. §3 records precisely what is new here: the entitlement question that project 004's profiles assume away, three authoritative Microsoft Learn facts none of them carries, and a reconciliation of project 004's TCO against the figure the project 001 business case is currently carrying.

### The `TBD-WP3` marker, and why there are no invented UoF figures

`ARC-001-FINOPS-v1.0` records that no licence baseline exists until **2026-08-21** and marks every unknown as `TBD-WP3`. **This document adopts that convention without exception.** No figure describing the University of Funk's current spend, seat count or contract terms appears anywhere below. Every dollar figure in this document is either:

- a **published vendor list price** from a real, cited, dated public source; or
- an **arithmetic model** whose inputs are named and whose unknowns are marked `TBD-WP3`.

> A reviewer should treat any UoF-specific dollar figure appearing in a later version without a WP3 reference as a defect, exactly as `ARC-001-FINOPS-v1.0` §"The `TBD-WP3` marker" requires.

**Currency**: Australian dollars. Vendor list prices published in US dollars are quoted **in the currency they were published in**, with an indicative AUD equivalent at **USD 1.00 ≈ AUD 1.54** — an assumption stated for arithmetic transparency, not a treasury rate, and not a substitute for a quote. GST-exclusive.

### Regulatory framing

Australian private-sector higher education. **Privacy Act 1988 (APPs)** including APP 8 for offshore disclosure, **ASD Essential Eight**, **WCAG 2.2 AA**. UK Government frameworks — GDS Service Standard, Technology Code of Practice, G-Cloud, Digital Outcomes and Specialists, UK GDPR — are **not applicable and were not searched**. Australian university procurement runs on institutional policy and sector consortia; §7 covers the sector route, which is the genuine Australian equivalent and which no one has yet used.

### Interview responses recorded

This artefact was generated non-interactively. No user was available to answer the command's scoping questions, so documented defaults were applied and are recorded here for audit:

| Question | Option taken | Basis |
|----------|-------------|-------|
| Research scope | **Full system** | Documented default. Narrowed in practice by the steer in §1.1 to the four areas where research changes a decision |
| Risk appetite | **Medium** | Documented default. Consistent with `ARC-001-ADR-007-v1.0` §7.3 |
| Knowledge compounding (vendor profiles / tech notes) | **Deferred, not skipped** | The generating task restricted file writes to this artefact alone. §12 lists what would be spawned, so the next run can create them without re-researching |

---

## 1. Executive Summary

### 1.1 Research Scope

Research was **deliberately concentrated**, not spread evenly across 24 platforms. Surveying the whole estate again would have reproduced `ARC-001-RSCH-v1.0` at lower confidence. Four areas were selected on a single test: *does a market fact here change a decision that is currently open?*

| # | Area | Decision it changes | Status before this document |
|---|------|--------------------|-----------------------------|
| **A** | **Integration broker / iPaaS** | `ARC-001-ADR-001-v1.0` chose mediation and left the product open pending its Condition 1 Principle 19 test; `ARC-001-ADR-006-v1.0` chose Azure conditionally on the same test | Test **not run**. Both ADRs are Proposed, and ADR-006 Condition 1 "can invalidate the decision, not merely delay it" |
| **B** | **Declared rationalisation candidates** | Which platform is primary in Learning Capture, Evaluation & Analytics, the video toolchain, and Course Design authoring | 0 of 8 categories have a designated primary (`ARC-001-FINOPS-v1.0` §2.1) |
| **C** | **Three net-new spend candidates** — Miro, OnExam, badging | Whether each is approved, deferred, or closed at RIFF | All three queued at Gate 1 (`ARC-001-ADR-007-v1.0` §5.2) |
| **D** | **Capability gaps with no incumbent** | Which gaps legitimately reach Gate 4 (Buy) | Only badging named, and that naming turns out to be wrong — see §5.3 |

**Excluded with reason**: LinkedIn Learning, Leganto, PebblePad, Turnitin, Remark, iSimulate, MuseScore, Ableton Live and Kuracloud. None is a contested primary, none carries queued new spend, and `ARC-001-RSCH-v1.0` §3 already records their corporate, standards and residency position. Re-researching them would consume budget without moving a decision.

**Method**: 24 web searches and fetches plus 3 Microsoft Learn documentation queries, conducted **2026-07-29**. 35 citations, each with a URL, a confidence rating and a fetch date. Full method and evidence rules in Appendix A.

### 1.2 The Three Findings That Change a Decision

**Finding 1 — The Principle 19 test on the Microsoft agreement will fail on entitlement, and it will fail for a reason no artefact has yet stated.**

`ARC-001-ADR-001-v1.0` Condition 1 asks Digital & IT to confirm "whether existing licensed platforms — including the Microsoft agreement — already provide adequate integration or event-brokering capability." `ARC-001-ADR-006-v1.0` calls this Azure's "principal advantage" over AWS and warns that without it "this decision returns to RIFF."

The market evidence says the answer is **no, on entitlement — and yes, on commercial route**, and the distinction is the whole finding:

- A **Microsoft Enterprise Agreement with an Azure Consumption Commitment (MACC) is a commitment to spend, not an entitlement to consume.** It buys discount eligibility, reserved-instance and savings-plan eligibility and marketplace credit qualification — it does not make Azure Service Bus, Event Hubs or Logic Apps free [MR-C9].
- The **Microsoft 365 A3 / A5 education entitlement does include real Power Automate use rights** — standard connectors, 6,000 Power Platform requests per user per day — but it **explicitly excludes premium connectors, and Azure connectors are premium** [MR-C8]. The one path that would have been genuinely free is the one path that cannot reach the Azure services ADR-006 selected.

So Condition 1 as currently worded is close to unanswerable in the affirmative. **The recommendation is not to abandon it but to re-scope it**, from *"is brokering already paid for?"* to *"is there unspent MACC commitment this workload can consume?"* On the second question a "yes" is worth as much: consuming already-committed spend has zero marginal budget impact against BR-002 while still being a real cost to the university. That is a materially different, and answerable, question for Grace Tanaka to put to the Microsoft LSP.

**Finding 2 — The business case is very likely carrying a broker cost line an order of magnitude too high.**

`ARC-001-SOBC-v1.0` §D1.2, quoted into `ARC-001-FINOPS-v1.0` §2.4, values broker licence or hosting at **$80k – $150k per year**. Project 004's independently-derived evidence for the same workload class — 7 integrations, fewer than 10,000 events per day, managed Azure Service Bus plus Event Hubs — puts three-year TCO at **A$63k – 105k**, i.e. roughly **A$21k – 35k per year** [P4-TN1]. That is a **3× to 7× overstatement**, and §3.5 reconciles it line by line.

This is not a rounding argument. R-013 and R-014 are live funding risks; `ARC-001-FINOPS-v1.0` lever L-7 is scoped as "up to $150k/year avoided". If the true recurring figure is nearer A$25k, the cost objection anticipated in ADR-001's recorded dissent largely dissolves, and the Principle 19 test stops being load-bearing for affordability. **Correcting this number is cheaper and faster than winning the argument the current number creates.**

**Finding 3 — The badging option set is stale, and Gate 1 is live after all.**

`ARC-001-ADR-007-v1.0` §5.2 records badging as the honest counter-example that proves the sourcing hierarchy is not a refusal mechanism: "**No incumbent — a genuine gap.** Passes Gate 1 honestly, and reaches Gate 4." The market evidence does not support that, and all three named options have moved:

- **"Milestone" is Anthology Milestone** — a badging and micro-credentialing product in the **incumbent LMS vendor's own family**, integrating to Blackboard Learn Ultra's Achievements tool over **LTI 1.3**, with criteria in Blackboard automatically issuing Milestone badges [MR-C23, MR-C24]. Badging is therefore a **Gate 1 / Gate 2** question about the Blackboard relationship, not a clean Gate 4 open-market case. **But**: Milestone's Open Badges 3.0 support, released 30 July 2025, was **"currently only available in the US. International markets are soon to follow"** [MR-C25]. Availability in Australia must be confirmed in writing before Milestone is treated as a live option.
- **"Badgr" no longer exists under that name.** Concentric Sky was acquired by Instructure in 2022, Badgr Pro became Canvas Credentials, and Canvas Credentials was rebranded **Parchment Digital Badges on 31 October 2025** [MR-C26]. It is reached primarily through a Canvas LMS subscription — a poor structural fit for a Blackboard institution — and the **legacy free issuer plan stopped working on 31 December 2025** [MR-C26].
- **Credly is Pearson-owned** (acquired 31 January 2022, US$200m total value including Pearson's prior ~20% stake) [MR-C27].
- And there is a route nobody asked about: **My eQuals**, the AU/NZ sector credential platform used by **100% of Australian and New Zealand public universities**, has an Open Badges-based digital badging solution with 15 AU/NZ institutions already issuing through it [MR-C29]. That is `ARC-001-ADR-007-v1.0` **Gate 3 — the gate the ADR itself says "no one has used."**

### 1.3 Key Findings

| # | Finding | Confidence | Consequence |
|---|---------|-----------|-------------|
| K-1 | EA/MACC is a spend commitment, not an entitlement; M365 A3/A5 Power Automate excludes Azure premium connectors | MEDIUM-HIGH | ADR-001 C1 / ADR-006 C1 re-scoped (§3.2) |
| K-2 | Broker recurring cost in the SOBC is 3×–7× project 004's evidence | HIGH on the arithmetic, MEDIUM on scope equivalence | SOBC §D1.2 and FINOPS §2.4 re-based (§3.5) |
| K-3 | Azure Service Bus zone redundancy is automatic **in all tiers, at no extra cost** | HIGH — Microsoft Learn | Cheapens NFR-A-001 compliance; ADR-006 Condition 2 (§3.3) |
| K-4 | Service Bus Geo-Replication is **Premium-only** and charges MUs in **both** regions | HIGH — Microsoft Learn | `australiasoutheast` warm recovery would roughly double MU cost (§3.3) |
| K-5 | Azure Schema Registry is an Event Hubs feature available in **Standard, Premium, Dedicated** — not Basic; enforcement is documented by Microsoft as **client-side** | HIGH — Microsoft Learn | Confirms `[P4-VP3]` weakness with an authoritative source; sets the DR-001 tier floor (§3.3) |
| K-6 | Logic Apps Standard includes unlimited free **built-in** operations; managed connectors are metered per call; the Free integration-account tier has **no SLA** | HIGH — Microsoft Learn | A cheaper mediation topology exists than the one costed (§3.4) |
| K-7 | "Milestone" is Anthology Milestone, a Blackboard-family product; OB 3.0 release was **US-only** at 30 July 2025 | HIGH on identity, HIGH on the US-only statement | Badging moves from Gate 4 to Gate 1/2 (§5.3) |
| K-8 | Badgr → Canvas Credentials → **Parchment Digital Badges** (31 Oct 2025); free issuer plan dead 31 Dec 2025 | HIGH | A named option in the landscape is not procurable as named (§5.3) |
| K-9 | **My eQuals** — 100% of AU/NZ public universities, Open Badges-based badging, 15 institutions issuing | MEDIUM | First concrete Gate 3 candidate in the programme (§7) |
| K-10 | Articulate's academic **50% grandfather rate is lost permanently if the subscription lapses** | MEDIUM — aggregators | Retire/retain asymmetry: retiring Articulate is irreversible in price terms (§4.4) |
| K-11 | TechSmith discontinued perpetual licences in Fall 2024; maintenance customers can add Camtasia 2024 seats only **until October 2026** | HIGH — vendor support page | A hard, dated cliff inside the roadmap horizon (§4.3) |
| K-12 | **Microsoft Clipchamp** is free in the M365 ecosystem with unlimited watermark-free 1080p export | MEDIUM-HIGH | Gate 1 candidate against Camtasia for basic editing (§4.3) |
| K-13 | Miro AU residency is **Enterprise-only**; Sydney primary, Melbourne backup; education discounts 30–50% | MEDIUM-HIGH | Sharpens `ARC-001-RSCH-v1.0` §3.8; sets Miro's floor cost (§5.1) |
| K-14 | Qualtrics **removed its Academic Plan**; higher-ed customers pushed to 3-year commitments at materially higher cost | MEDIUM — one source is a competitor | Changes the Qualtrics-vs-Evasys calculus (§4.2) |
| K-15 | **Explorance Blue** holds 50% of Australia's Go8; a UK university replaced EvaSys with Blue after procurement | MEDIUM-HIGH | A third option neither incumbent is currently tested against (§4.2) |
| K-16 | **"OnExam" is not identifiable from any public source** after four search strategies | HIGH as a negative finding | Gate 1 for OnExam cannot be assessed as written (§5.2) |
| K-17 | Australian exam-**operations** market is real and separate: DataBee Exams Manager (UniSA, Charles Sturt), Janison (UTAS since ~2009) | MEDIUM | If OnExam is exam operations, ExamSoft is the **wrong** Gate 1 incumbent (§5.2) |
| K-18 | An institution retired Echo360 in 2026 citing "fiscal priorities and **redundancy in software**" | MEDIUM | Direct sector precedent for the declared Teams/Zoom/Echo360 candidate (§4.1) |
| K-19 | **CAUDIT** operates a Microsoft LSP Panel 2026, an IT Procurement Community of Practice, and CAUDIT Cloud; AWS is a 2026 Engagement Partner | MEDIUM | Gate 3 has a named, live, unasked route (§7) |
| K-20 | RabbitMQ 4.3 (23 Apr 2026) has AMQP 1.0 always-on and improved quorum queues — and still **no native schema registry** | MEDIUM-HIGH | Confirms `[P4-VP1]`'s disqualifying gap holds two releases later (§3.3) |

### 1.4 Build vs Buy Summary

| Capability | Decision | Basis |
|-----------|----------|-------|
| **Integration broker runtime** | **BUY — managed, on the incumbent provider** | Commodity at Wardley ~0.80 (ADR-006). Self-hosting is building a commodity; project 004 costs self-hosted Kafka at A$169k/3yr against A$63k–105k managed, before operator time [P4-TN1]. §3.6 |
| **Schema registry** | **BUY — bundled** | Event Hubs Standard+ includes it [MR-C5]. Buying it separately (Confluent) or self-hosting it (Apicurio) adds a component to a team with a documented single-person dependency. §3.3 |
| **Canonical model, event contracts, role authority, rollover automation, capability register** | **BUILD** | Unchanged from `ARC-001-RSCH-v1.0` §5.1. These are institutional governance artefacts; no vendor supplies them. Not re-argued here |
| **Digital badging** | **DEFER, then GATE 1 on Blackboard** | Reclassified from Gate 4. Milestone is a Blackboard-family product; AU availability unconfirmed. FR-019 is Could-priority. §5.3 |
| **Collaborative whiteboard (Miro)** | **GATE 1 — do not buy yet** | Microsoft Whiteboard is already inside M365; Padlet has a free-form Sandbox canvas [MR-C35]. Miro's AU-resident floor is the Enterprise tier with a 30-seat minimum. §5.1 |
| **Exam platform (OnExam)** | **CANNOT ASSESS — resolve identity first** | The product is not publicly identifiable [MR-C16]. §5.2 |
| **Course-evaluation platform** | **BUY — one, competitively** | Qualtrics/Evasys/Blue is a genuine three-way market question, not a two-way retain-or-retire. §4.2 |
| **Video capture and editing toolchain** | **BUY — but re-scope before renewing** | Camtasia's model changed under the university; Clipchamp and Echo360 already hold much of the ground. §4.3 |
| **Authoring (Articulate 360)** | **RETAIN or RETIRE — decide once, deliberately** | The academic grandfather rate makes retirement irreversible. §4.4 |

### 1.5 Top Recommended Vendors / Products

| Rank | Product | Category | Why | Confidence |
|------|---------|----------|-----|-----------|
| 1 | **Azure Service Bus (Premium) + Event Hubs (Standard) with Azure Schema Registry**, `australiaeast` | Integration broker | Only option that is in-region, zone-redundant at no extra cost, schema-registry-bearing, and on the declared provider. Extends `[P4-VP3]` | HIGH |
| 2 | **Confluent Cloud**, AWS `ap-southeast-2` / Azure Australia East | Integration broker — contingency | Server-side schema rejection is the strongest enforcement model available. Hold as the named contingency if client-side enforcement proves insufficient. Extends `[P4-VP2]` | MEDIUM — CKU rates undisclosed |
| 3 | **Explorance Blue** | Evaluation & Analytics | Purpose-built for course evaluation; 50% of Australia's Go8; the option the current Qualtrics-vs-Evasys framing omits | MEDIUM-HIGH |
| 4 | **Anthology Milestone** | Badging | Gate 1/2 candidate inside the incumbent LMS relationship — conditional on written confirmation of AU availability | MEDIUM |
| 5 | **My eQuals** | Badging — sector route | The Gate 3 answer. Already used by every AU/NZ public university | MEDIUM |

### 1.6 Requirements Coverage

Coverage means *a sourcing position now exists*, not *the requirement is satisfied*.

| Requirement | Category | Sourcing position after this research | Section |
|-------------|----------|--------------------------------------|---------|
| REQ-023, 024, 025, 027, 028 | Integration | Managed Azure broker; schema registry tier floor set; entitlement question re-scoped | §3 |
| REQ-004 | Video toolchain | Camtasia cliff dated; Clipchamp as Gate 1 candidate; Echo360 overlap quantified | §4.3 |
| REQ-008, 009, 010 | Delivery / Capture | Teams/Zoom/Echo360 comparison sourced; sector precedent identified; REQ-010 remains the binding constraint | §4.1 |
| REQ-011, 013, 014 | Collaboration / Active Learning | Miro floor cost and residency tier established; Gate 1 incumbents named | §5.1 |
| REQ-017 | Secure exams | **Blocked** — vendor identity unresolved | §5.2 |
| REQ-019 | Micro-credentials / badges | Reclassified Gate 4 → Gate 1/2; three options re-identified; sector route found | §5.3 |
| REQ-021 | Teaching evaluation | Three-way market established | §4.2 |
| REQ-002 | Interactive content authoring | Articulate licensing mechanics and the grandfather trap established | §4.4 |
| REQ-030 | APP 8 / residency | AU residency confirmed for Azure, Miro (Enterprise only); Evasys remains offshore | §8.2 |
| REQ-032 | 99.9% availability | Azure zone redundancy free in all tiers; geo-replication cost quantified | §3.3 |
| REQ-035 | Flat or reduced spend | Two of three net-new commitments now have a credible deferral case; broker line re-based downward | §8 |

**Not covered**: REQ-003, 005, 006, 007, 015, 016, 018, 020, 022, 026, 029, 031, 033, 034 — deliberately, per §1.1.

### 1.7 What This Research Could Not Establish

1. **Any UoF-specific price, seat count or contract term.** By design — `TBD-WP3`.
2. **Azure list prices as rendered figures.** The AU pricing page selects region and currency dynamically; the fetched page returned tier structure and the caveat *"Prices are estimates only... Actual pricing may vary depending on the type of agreement entered with Microsoft"* but no rendered rates [MR-C1]. The Azure pricing calculator, signed in against the university's own agreement, is the only authoritative source — and that is precisely the artefact Condition 1 requires anyway.
3. **Confluent CKU / eCKU rates.** Not publicly disclosed; sales engagement required [MR-C10]. Unchanged from `[P4-VP2]`.
4. **Echo360, Evasys, Explorance Blue, ExamSoft, Turnitin and Anthology Milestone list prices.** All quote-based. Echo360 "does not offer a free plan" and prices custom [MR-C15]; Evasys and Blue both quote per institution [MR-C30, MR-C31].
5. **The identity of "OnExam".** Four search strategies, no match [MR-C16].
6. **Whether Anthology Milestone is available in Australia.** The OB 3.0 release note says US-only with international to follow [MR-C25]; no AU availability statement was located.
7. **What the university's Microsoft agreement actually covers.** Only Microsoft and the LSP can answer this. It is Condition 1, and it remains open.

---

## 2. Method and Evidence Rules

Four rules, applied without exception. Appendix A records them in full.

1. **Every external claim carries a citation ID, a URL and a confidence rating.** Vendor documentation and vendor support pages rate HIGH. Microsoft Learn rates HIGH. Pricing aggregators and secondary commentary rate MEDIUM or lower and are labelled as such at the point of use.
2. **Competitor-published commentary is flagged.** Two sources in §4.2 are published by direct competitors of the product they describe. That does not make them false; it makes them interested, and the reader is told.
3. **Nothing about the University of Funk is inferred from external sources.** Organisational facts come only from the supplied artefacts.
4. **Negative findings are recorded as findings.** "Not located" and "not identifiable" are results, not gaps in effort — §5.2 is the clearest instance.

### Confidence distribution

| Rating | Count | Typical source |
|--------|-------|----------------|
| HIGH | 11 | Microsoft Learn, vendor support and vendor policy pages, corporate press releases |
| MEDIUM-HIGH | 6 | Vendor marketing with specific verifiable claims; vendor help centres |
| MEDIUM | 15 | Pricing aggregators, institutional pages, sector bodies where the page did not render |
| LOW-MEDIUM | 3 | Competitor-published commentary, single-source pricing claims |

---

## 3. Category A — Integration Broker / iPaaS

### 3.1 What is actually being decided, and what is not

`ARC-001-ADR-001-v1.0` **already chose** Option B, a central integration broker holding the canonical schema. This section does **not** re-open that. Three things are open:

| Open item | Owner | Blocking what |
|-----------|-------|---------------|
| ADR-001 Condition 1 — the Principle 19 test | Cassandra Rhodes | Procurement of anything |
| ADR-006 Condition 1 — what the Microsoft agreement covers | Cassandra Rhodes with Grace Tanaka | The provider decision itself: "*This condition can invalidate the decision, not merely delay it*" |
| Product and tier selection within the chosen provider | Sam Okafor | The DR-001 schema-registry contract, and the recurring cost line |

### 3.2 The entitlement question, answered properly

This is the most consequential paragraph in the document, so it is worth being precise about what was found and what was not.

**What an Enterprise Agreement with a MACC does.** A Microsoft Azure Consumption Commitment is *"a contractual commitment by a customer to spend a fixed dollar amount on Azure consumption over a defined term — typically the three-year length of an Enterprise Agreement"*. What the customer receives in exchange is **commercial treatment**: reserved-instance and savings-plan eligibility, discount eligibility on consumption SKUs, and qualification for marketplace credit programmes [MR-C9]. It is a floor on spend, not a ceiling on cost, and it confers no free capacity.

**What the M365 education entitlement does.** Microsoft 365 A3 and A5 do carry genuine Power Automate use rights — automated, scheduled and instant flows over **standard** connectors (SharePoint, Outlook, Teams, OneDrive, Excel, Forms and others), with an allowance of **6,000 Power Platform requests per user per day**. What it does not carry is **premium connectors**, and *Azure* connectors are classified premium; those require per-user Power Automate Premium licensing [MR-C8].

**Why that combination is decisive.** The only genuinely free integration capability in the estate is Power Automate over standard connectors. That capability cannot reach the Azure messaging services ADR-006 selected without a Premium licence, and even with one, Power Automate is a workflow engine, not a broker holding a canonical schema at runtime — which is the specific thing ADR-001 chose Option B to obtain.

**Therefore**: Condition 1, asked as *"does the Microsoft agreement already provide adequate integration or event-brokering capability?"*, has a defensible answer of **no**. ADR-006 §6.4 anticipated this exact outcome — *"If it does not cover them, this decision returns to RIFF"* — and it is worth saying plainly that a literal reading would send a sound decision back to committee on a technicality.

**Recommended re-scope.** Replace the single question with three, all answerable by Grace Tanaka and the LSP inside two weeks:

| # | Re-scoped Condition 1 question | A "yes" is worth |
|---|-------------------------------|------------------|
| 1a | Is there **unspent MACC commitment** in the current term that this workload can consume? | Zero marginal budget impact against BR-002 — commercially equivalent to entitlement for FinOps purposes, while remaining honestly recorded as real cost |
| 1b | Does any **existing licensed platform** hold a usable brokering surface — Power Automate Premium already licensed anywhere, PeopleSoft Integration Broker, Blackboard REST? | A cheaper starting topology. Note project 004's settled position: PeopleSoft Integration Broker is suitable as a **source adapter**, not as the broker [P4-TN1] |
| 1c | What **rate treatment** does the agreement give the specific meters — Service Bus messaging units, Event Hubs throughput units, Log Analytics ingestion? | Converts §3.5's model from list-price arithmetic into a real number |

> **The honest framing for RIFF.** Principle 19 says *"where a required capability already exists within a licensed platform, the university MUST evaluate configuring and adopting it before acquiring a new platform."* That evaluation has now been done at the market level and the answer is that the capability does not already exist in a usable form. Principle 19 is **satisfied by having tested it and recorded the result** — not only by finding a yes. ADR-007 §8.1 makes the same point when it counts "Gate 1 successes" as one outcome among several.

### 3.3 Market comparison — extending project 004, not repeating it

Project 004's tech note `[P4-TN1]` already carries a six-way comparative matrix across messaging model, protocol, schema registry, dead-letter, replay, operational complexity, AU region and three-year TCO. **That matrix is not reproduced here.** What follows is only what is new, corrected or newly authoritative as of 2026-07-29.

| # | New or corrected fact | Source and rating | Why it matters to project 001 |
|---|----------------------|-------------------|------------------------------|
| N-1 | *"Service Bus supports zone-redundant deployments in all service tiers... zone redundancy is automatically enabled at no extra cost"* and *"Zone redundancy in Service Bus doesn't add extra cost"* | Microsoft Learn — **HIGH** [MR-C3] | `[P4-VP3]` credits Premium with a 99.99% SLA but does not record that the **availability-zone mechanism NFR-A-001 depends on is free at every tier**. ADR-006 leaned on Australia East's zones; this makes that lean cheaper than assumed, and it weakens any argument for Premium purely on resilience grounds |
| N-2 | Geo-Replication is **Premium-only**, and *"each replica runs on the same number of MUs as configured on the primary, and you're charged for the total MUs across all replicas"*, plus per-GB replication data transfer | Microsoft Learn — **HIGH** [MR-C3, MR-C4] | Directly prices ADR-006 Condition 2. A warm `australiasoutheast` posture would roughly **double** the MU line before data transfer. ADR-005's code-and-configuration recovery posture is not merely tolerable — it is the substantially cheaper option, and that should be recorded as a reason, not just an accommodation |
| N-3 | Failover is **manual**: *"Microsoft doesn't automatically initiate failover or promotion, even if your primary region is down"* | Microsoft Learn — **HIGH** [MR-C3] | The recovery-time objective ADR-006 Condition 2 requires must include human detection and decision time. An RTO stated as if failover were automatic would be wrong |
| N-4 | Azure Schema Registry is *"a feature of Event Hubs"* and *"available in the **Standard**, **Premium**, and **Dedicated** tiers"* — **not Basic** | Microsoft Learn — **HIGH** [MR-C5] | Sets a hard floor for DR-001: Event Hubs **Standard is the minimum tier**. A Basic namespace cannot carry the canonical model at runtime. Neither `[P4-VP3]` nor `[P4-TN2]` states the tier constraint |
| N-5 | Microsoft's own term for the enforcement model is **"client-side schema enforcement"** — *"validated against schemas defined in the schema registry on the client side rather than the broker/server side"*, with a dedicated documentation page | Microsoft Learn — **HIGH** [MR-C6] | `[P4-VP3]` lists this as a weakness and `[P4-TN2]` calls it "adequate when all producers are controlled by the integration team". It is now confirmed **from the vendor**, which is what an architecture board needs before accepting the residual risk. It also names the mitigation: the SDK path must be mandatory, and a bypassed SDK admits non-conformant events |
| N-6 | Logic Apps Standard *"includes an **unlimited number** of free built-in operations"*; managed connectors are metered per call at Consumption connector rates; the Free integration-account tier is *"only for exploratory scenarios, not production"* and *"has no service-level agreement"* | Microsoft Learn — **HIGH** [MR-C7] | Opens a genuinely cheaper topology (§3.4) that no artefact has costed. Also a trap: an integration account on the Free tier would carry no SLA into a 99.9% teaching-period target |
| N-7 | RabbitMQ 4.3 released **23 April 2026**; AMQP 1.0 is a core always-enabled protocol with peak throughput more than doubled over 3.13.x; quorum-queue leadership transfer improved; **still no native schema registry** | Vendor blog / release notes — **MEDIUM-HIGH** [MR-C12] | `[P4-VP1]` disqualified CloudAMQP on the schema-registry gap at RabbitMQ 4.1. Two releases and five months later the gap holds. That conclusion can be treated as stable rather than provisional |
| N-8 | CloudAMQP: **Sydney `ap-southeast-2` is available**; dedicated plans allow node count selection and a dedicated VPC | Vendor FAQ / changelog — **MEDIUM** [MR-C11] | `[P4-VP1]` recorded AU availability as *"PROBABLE... specific confirmation required"*. That confirmation is now on record. It does not change the recommendation — the schema gap is decisive — but the profile should stop carrying an open question that is closed |
| N-9 | Confluent: **eCKU** autoscales and charges only consumed capacity with a usage minimum; **Freight** clusters target high-throughput latency-tolerant workloads; regional multipliers apply to ingress/egress; **CKU rates remain undisclosed** | Vendor docs + aggregators — **MEDIUM** [MR-C10] | Freight and eCKU did not exist in `[P4-VP2]`'s pricing model. Neither helps here: Freight optimises for exactly the profile this estate does not have. It reinforces `[P4-VP2]`'s "over-engineered for fewer than 10,000 events/day" finding rather than softening it |

### 3.4 Options analysis

Five options. Wardley positions are quoted from ADR-001 and ADR-006 rather than re-derived.

#### Option A1 — Build: self-hosted broker on university-managed compute

Self-hosted Kafka or RabbitMQ on Azure VMs, with Apicurio Registry as a sidecar for schema.

**Good**: maximum control; no per-message vendor meter; Apicurio is CNCF and broker-agnostic, supporting Avro, JSON Schema, Protobuf, OpenAPI, AsyncAPI and more, with a Confluent-compatible API [P4-TN2]; strongest theoretical exit position.

**Bad**: this is **building a commodity**. `ARC-001-ADR-007-v1.0` §3.3 is explicit that build is reserved for governance artefacts and for capability the market does not supply. Cluster management, capacity planning, security hardening and patching land on a team whose depth is evidenced by R-007's single-person dependency on a course-cloning script. `[P4-TN1]` rates self-hosted Kafka operational complexity **HIGH** and states it is "not recommended for small teams." Managed services carry the patching obligation that ADR-006 relies on for the Essential Eight ML2 pathway (R-020); self-hosting hands it back.

**Cost**: `[P4-TN1]` puts self-hosted Kafka at **A$169k / 3 years** — higher than every managed option except Confluent, before counting operator time.

**Verdict: rejected.** Not on cost alone, but because it fails ADR-007's sourcing hierarchy at Gate 5 and reverses ADR-006's Essential Eight logic.

#### Option A2 — Buy: Azure Service Bus + Event Hubs with Azure Schema Registry *(recommended)*

Service Bus for queue/topic mediation with built-in per-subscription dead-lettering; Event Hubs **Standard or above** for the schema registry and replay; Azure Monitor for the ADR-003 observability plane. All in `australiaeast`.

**Good**: on the declared provider, so no second identity model, network path, cost model or on-call rotation — ADR-006 §6.3's operating-surface argument applies directly. Zone-redundant at no extra cost in every tier [MR-C3]. AMQP 1.0 on the data plane satisfies ADR-006 Condition 3's open-protocol requirement. Schema registry is bundled, not a separate component. Australian residency for every university-held copy, satisfying Principle 8 and NFR-C-002.

**Bad**: **client-side** enforcement, now confirmed from Microsoft [MR-C6] — the SDK must be mandatory and a bypassed SDK admits non-conformant events. The management plane is Azure-specific and not portable. It deepens the concentration ADR-006 §6.5 already records as dissent. And Condition 1 does not make it free (§3.2).

**Tier recommendation, stated precisely because it is where the money is**:

| Component | Recommended tier | Why |
|-----------|-----------------|-----|
| Service Bus | **Standard to start; Premium only when a stated trigger fires** | Standard gives topics, subscriptions, sessions, transactions and duplicate detection on shared capacity billed per operation [MR-C2], and zone redundancy is free at Standard [MR-C3]. Premium buys dedicated MUs, 100 MB messages, VNet/Private Link, JMS 2.0 and Geo-Replication [MR-C2] — none of which fewer than 10,000 events/day requires on day one. **Premium triggers**: Private Link becomes a security requirement; message size exceeds Standard's limit; or Geo-Replication is adopted after the ADR-006 Condition 2 RTO decision |
| Event Hubs | **Standard — this is a floor, not a preference** | Schema Registry is unavailable on Basic [MR-C5]. DR-001 conformance at runtime is therefore impossible below Standard |
| Integration account (only if Logic Apps is used) | **Not Free** | The Free tier has no SLA [MR-C7] and cannot sit under NFR-A-001 |

> **Starting at Standard rather than Premium is the single largest controllable decision in this line item.** `[P4-VP3]` quotes Service Bus Premium at roughly **US$677/month per messaging unit** — about **A$1,042/month, A$12.5k/year** per MU at the stated conversion, and a Premium namespace holds 1, 2 or 4 MUs [MR-C2]. Two MUs is therefore an **A$25k/year** commitment before a single message flows. Standard is a base charge plus per-operation metering [MR-C1, P4-VP3]. At this event volume the gap between the two is most of the difference between §3.5's low and high bands.

#### Option A3 — Buy: Confluent Cloud *(named contingency)*

**Good**: server-side producer rejection is the strongest enforcement model available and the direct answer to N-5's residual risk; full replay from any offset; exactly-once semantics; AU regions confirmed on AWS `ap-southeast-2` and Azure Australia East [P4-VP2].

**Bad**: a new vendor relationship, so it enters ADR-007 at Gate 4 rather than Gate 1. `[P4-VP2]` estimates 40–100% more than Azure under the existing agreement. Kafka partition/consumer-group/offset concepts carry a steeper curve. CKU rates undisclosed [MR-C10]. Freight and eCKU (N-9) optimise for a throughput profile this estate does not have.

**Verdict: hold as the named contingency**, exactly as project 004 concluded — with one addition: the **trigger** should be written down now. Recommended trigger: a schema-conformance defect reaching production through a bypassed SDK path, twice in one teaching period.

#### Option A4 — Buy: CloudAMQP managed RabbitMQ

AU Sydney availability now confirmed (N-8), and `[P4-VP1]` puts a 3-node cluster at **US$297–897/month** with three-year TCO around **A$78k**. But **no native schema registry**, still true at RabbitMQ 4.3 (N-7), so DR-001 conformance would require an Apicurio sidecar and validation in application code — which `[P4-TN2]` calls the weakest model, *"enforcement by convention."*

**Verdict: rejected.** Enforcement by convention is precisely what ADR-001 rejected Option A to escape. Adopting the cheapest broker and then reinstating convention-based conformance would spend money to arrive back at the status quo.

#### Option A5 — Buy less: Logic Apps Standard as the mediation layer *(not previously costed — flagged for assessment)*

Not in project 004's option set, and it deserves to be. Logic Apps Standard *"includes an unlimited number of free built-in operations"*, metering only managed-connector calls and storage [MR-C7]. Nine integrations expressed as built-in HTTP and Request operations against platform REST APIs would consume very little metered capacity.

**Good**: potentially the cheapest option on the declared provider; low-code surface a small team can hold; native Azure Monitor integration for ADR-003.

**Bad — and probably decisive**: it is an **orchestration** engine, not a broker. It does not hold a canonical schema at runtime, and Microsoft's own guidance distinguishes orchestration-first Logic Apps from the messaging primitives [MR-C7]. Adopting it alone would deliver ADR-001 Option A's architecture — point-to-point, conformance by convention — under a managed-service label. It also reintroduces the n×(n−1) coupling ADR-001 rejected.

**Verdict: not a substitute for A2, but assess it as a complement.** Logic Apps for orchestration and adapters; Service Bus and Event Hubs for the contract-bearing spine. Sam Okafor should cost this pairing against A2-alone during the Condition 1 window, because if the metered portion is genuinely small it lowers the integration build effort without weakening runtime conformance.

### 3.5 Reconciling the broker cost line — the arithmetic in full

Two numbers currently describe the same thing and differ by up to 7×.

| Source | Figure | Basis |
|--------|--------|-------|
| `ARC-001-SOBC-v1.0` §D1.2, quoted in `ARC-001-FINOPS-v1.0` §2.4 | **$80k – $150k per year**, possibly nil | "Estimable from scope rather than requiring a baseline"; not independently derived |
| Project 004 `[P4-TN1]` | **A$63k – 105k over three years** ≈ **A$21k – 35k per year** | Managed Azure Service Bus + Event Hubs, 7 integrations, fewer than 10,000 events/day, AU region |

**Why the low figure is more credible**, stated so it can be checked rather than believed:

1. **The workload is small.** Fewer than 10,000 events per day is roughly 0.12 events per second. Both Service Bus Standard's per-operation metering and Event Hubs Standard's throughput units are priced for volumes orders of magnitude larger.
2. **The expensive component is optional.** Premium messaging units at roughly A$12.5k/year each [P4-VP3, MR-C2] are the only line that reaches SOBC scale, and §3.4 shows they are not required on day one.
3. **The resilience mechanism is free.** Zone redundancy — the mechanism NFR-A-001's 99.9% depends on — costs nothing at any tier [MR-C3]. A cost model that assumed resilience had to be purchased would overstate.
4. **The schema registry is bundled.** No separate registry licence [MR-C5].
5. **Project 004's figure spans five options consistently** — A$63k–105k Azure, A$78k CloudAMQP, A$86k NATS, A$148k–360k Confluent, A$169k self-hosted Kafka [P4-TN1]. Only Confluent's upper bound approaches the SOBC's annual figure, and Confluent is not the recommendation.

**Where the SOBC figure could still be right.** Three ways, all worth checking before the number is changed:

- It may include **Azure Monitor / Log Analytics ingestion** for the ADR-003 observability plane. That is a genuine and potentially significant line, and `ARC-001-ADR-006-v1.0` §5 Option A names log retention as "the dominant and most controllable variable." **Retention policy (DR-006) is the lever.**
- It may include **integration platform professional services** — which belong in the one-off capital line under `ARC-001-FINOPS-v1.0` §5.1's mandatory separation, not in recurring licence spend.
- It may be a deliberately conservative ROM at the SOBC's stated ±50%. But ±50% on A$25k is A$12k–38k, not A$80k–150k. The gap is not explained by the stated tolerance.

**Recommended action.** Sam Okafor re-derives the recurring line as a **three-part figure** — messaging and eventing, observability ingestion, and reconciliation compute — each with its own tier assumption, and puts it to the Steering Committee **before** the September business case. Presenting a corrected lower number is easier before submission than after.

> **This finding cuts in the university's favour, which is a reason for more scrutiny, not less.** A model that produces a convenient answer should be checked harder than one that does not. The three-part re-derivation above is the check.

### 3.6 Recommendation for Category A

**BUY, managed, on Azure `australiaeast`: Service Bus starting at Standard plus Event Hubs at Standard for the Azure Schema Registry.** Confluent Cloud is the named contingency with a written trigger. Assess Logic Apps Standard as a complementary orchestration and adapter layer, not as a replacement for the contract-bearing spine.

**Conditions carried forward:**

1. Condition 1 is **re-scoped per §3.2** and answered against questions 1a–1c. It is satisfied by a recorded result, not only by a positive one.
2. Event Hubs is provisioned at **Standard or above**. Basic is architecturally non-viable for DR-001 [MR-C5].
3. Service Bus starts at **Standard**. Premium requires one of the three stated triggers, recorded at RIFF.
4. The **SDK serialisation path is mandatory** for every producer, and a bypass is a defect, not a workaround. This is the mitigation for client-side enforcement [MR-C6].
5. The ADR-006 Condition 2 **RTO includes human detection and decision time**, because promotion is manual [MR-C3].
6. The recurring cost line is **re-derived as three components** and the SOBC figure corrected or defended (§3.5).

---

## 4. Category B — The Declared Rationalisation Candidates

### 4.1 Learning Capture, Learning Delivery and Collaboration — Teams, Zoom, Echo360

`external/system-landscape.md` note 1 names this explicitly as the "key rationalisation candidate", with investigation planned for 2027. `ARC-001-FINOPS-v1.0` §2.2 rates the overlap **High** in three categories. REQ-008 asks for live online classes on **one** primary platform.

`ARC-001-RSCH-v1.0` §4.4 already frames the question. Three market facts sharpen it:

| # | Market fact | Source | Effect on the decision |
|---|------------|--------|-----------------------|
| B1-1 | **The overlap is partly designed.** EchoVideo integrates deeply with Teams and has confirmed integrations with **both** Teams and Zoom [MR-C15] | Vendor — MEDIUM | Weakens the "three platforms doing one job" framing. Echo360 may be the capture and management layer *over* Teams and Zoom rather than a competitor to them. That is a boundary decision under Principle 2, not a retirement |
| B1-2 | **Zoom's Australian position is institutional, not incidental.** AARNet is a leading Zoom APAC reseller for education, delivering licensing and support to *"the majority of Australia's universities"*, has been Zoom's first Australian Platinum Partner, and cloud-recording region is selectable to Australia [MR-C14] | Sector body — MEDIUM-HIGH | Zoom is the **strongest-evidenced APP 8 position** of the three, reached through a sector arrangement. Retiring Zoom would surrender both the residency position and a Gate 3 relationship |
| B1-3 | **There is a 2026 sector precedent for retiring Echo360 on exactly this ground.** One institution's Echo360 contract *"will expire on June 30, 2026, due to fiscal priorities and **redundancy in software**"*, with instructors told to plan alternatives [MR-C16] | Institutional page — MEDIUM | The decision UoF is contemplating has been taken elsewhere, for the stated reason, and the transition was managed at a contract boundary — the exact mechanism `ARC-001-FINOPS-v1.0` §7.2 constraint 1 requires |

**The market comparison, on capability rather than price** (no institutional pricing is published for any of the three):

| Capability | MS Teams | Zoom | Echo360 (EchoVideo) |
|-----------|----------|------|--------------------|
| Scheduled automatic capture of timetabled lectures (REQ-009) | Not a room-capture product | Not a room-capture product | **Purpose-built** |
| Live class with breakouts, polling, recording (REQ-008) | Yes | Yes, plus polling already in the estate | Not the primary use |
| Multi-camera / high-fidelity audio (REQ-010) | No | No | Appliance-dependent — **the binding constraint** |
| Video management, search, analytics, gradebook sync | Stream, limited | Limited | **AskEcho AI study tools from transcripts, analytics, gradebook sync, 99.95% uptime claim** [MR-C15] |
| ASR captions for WCAG 2.2 AA (REQ-029) | Yes | Yes | Yes — and `ARC-001-RSCH-v1.0` §3.4 records Echo360's **WCAG 2.2 AA across all five products, announced 29 April 2026** — the only such declaration located in the estate |
| Australian residency evidence | M365 AU regions | **Strongest** — region-selectable recordings [MR-C14] | Not established |
| Licence position | Probably bundled | AARNet arrangement | Standalone institutional |

**Assessment.** The three-way overlap is real in Collaboration and Learning Delivery and much weaker in Learning Capture, where Echo360 is the only product actually designed for the job. Two constraints already in the register decide it:

- **REQ-010** (multi-camera, high-fidelity audio) is Could-priority but, as `ARC-001-FINOPS-v1.0` §7.2 constraint 3 notes, it *"materially affects which capture platform can be primary."* Neither Teams nor Zoom addresses it.
- The **capture appliance estate** is out of REQ scope but its cost dependency must still be declared. A capture platform change that strands theatre hardware converts a licence saving into a capital cost.

**Recommendation**: **retain Echo360 as primary for Learning Capture; designate one primary for live synchronous delivery between Teams and Zoom; declare the other a bounded exception rather than retiring it.** Do not treat this as a three-way elimination. The most defensible saving is not the removal of a platform but the removal of *undeclared* duplication in Collaboration, where Teams, Zoom, Blackboard, Padlet and Turnitin PeerMark all currently sit without a boundary. Echo360's WCAG 2.2 AA declaration and its Teams/Zoom integrations both argue for keeping it and narrowing its scope.

**For the 2027 investigation**: obtain (i) the Echo360 contract boundary and notice period, (ii) the capture-appliance refresh position, (iii) whether the AARNet Zoom arrangement is transferable or would be lost, and (iv) whether Teams' AU tenant configuration matches Zoom's evidenced recording residency.

### 4.2 Evaluation & Analytics — Qualtrics vs Evasys, and the third option nobody has priced

`ARC-001-FINOPS-v1.0` §7.2 calls this "the cleanest pair in the estate." FR-021/REQ-021 requires **one** platform. `ARC-001-RSCH-v1.0` §3.8 establishes that Qualtrics is IRAP-assessed with AU hosting available, and that Evasys *"hosts all data exclusively on German servers"* — an unambiguous offshore position requiring APP 8 assessment.

The market says this is a **three-way** decision, not a two-way one.

| Product | Position | Evidence | Rating |
|---------|----------|----------|--------|
| **Qualtrics** | General-purpose experience platform, AU hosting, IRAP-assessed. **But**: Qualtrics *removed its Academic Plan*, "widely used by universities for its relatively lower cost", leaving institutions facing "substantially higher cost structures or migrating to new tools"; customers are being moved to **three-year commitments**; base CoreXM around **US$25k–50k/yr** for small-to-mid deployments (≈ A$38k–77k) with modules billed separately | [MR-C32] | **LOW-MEDIUM** — one source is published by a direct competitor (QuestionPro). Flagged deliberately: the claim is plausible and specific, and it is also interested |
| **Evasys** | Purpose-built evaluation, ISO 27001, 900+ organisations, **German hosting only**. Quote-based pricing, no public figures | [MR-C31], `ARC-001-RSCH-v1.0` §3.8 | MEDIUM |
| **Explorance Blue** | **Not currently considered.** Purpose-built for course evaluation at scale. **50% of Australia's Go8** are clients — Monash, UNSW, Melbourne, Adelaide — across Blue Evaluations, Blue Survey, Blue 360, Data Integrity Gateway, Blue Text Analytics and Bluepulse. Automates late withdrawals, cross-listed and team-taught units, and multi-departmental governance. **A UK university ran a procurement exercise and selected Blue to replace EvaSys** | [MR-C30, MR-C31] | MEDIUM-HIGH on market position; residency **not established** and must be tested |

**Assessment.** The pair-framing quietly assumes the answer is one of the two incumbents. Two facts make that assumption expensive:

1. **Qualtrics' higher-education commercial terms have moved against the university** [MR-C32]. If the Academic Plan is gone and renewal means a three-year commitment at materially higher cost, then "retain Qualtrics, retire Evasys" may not deliver the saving the pair-framing implies — and it locks the envelope for three years.
2. **The Evasys → Blue migration is a documented, procured path** [MR-C31], and Blue is already the mainstream choice at half of Australia's most research-intensive universities [MR-C30]. Retaining Evasys on a German-hosted footprint while an AU-mainstream alternative exists is a harder APP 8 position to defend at renewal than it was before this was known.

**Recommendation**: **run this as a three-way competitive assessment at the next contract boundary, not a retain-or-retire choice.** Concretely — establish both contract boundaries first (retirement is only executable there); obtain a written Blue residency and APP 8 statement, since Blue's position is genuinely unestablished; and price the Qualtrics renewal explicitly against a Blue proposal. Note that this is one of very few places in the estate where **retiring the offshore platform and consolidating onto an AU-resident one improves the privacy position and the duplication position at the same time** — the rare case where FinOps and Principle 8 pull together.

Under `ARC-001-ADR-007-v1.0` this enters at **Gate 2** (Extend — does Qualtrics' evaluation module do what Evasys does?) and, if Gate 2 fails, at **Gate 3** before Gate 4, since course evaluation is a problem every Australian university has.

### 4.3 Learning Resources — the video toolchain, and a dated cliff

REQ-004 requires record, edit and caption *"with a single supported toolchain."* Four platforms currently occupy the space: **Camtasia**, **Adobe Creative Suite**, **Echo360** and **Articulate 360**.

**The finding that forces a decision date.** TechSmith *"moved from perpetual licenses to annual subscriptions in Fall 2024"*; the last opportunity to buy perpetual licences at upgrade pricing was **1 October 2024**; and customers with active maintenance *"can continue to add more seats for Snagit 2024 and Camtasia 2024 until **October 2026**"* [MR-C17]. **HIGH confidence — vendor support page.**

That is a hard, dated cliff **inside the roadmap horizon and roughly two months after the WP3 baseline is due**. Three consequences:

1. If the university holds perpetual Camtasia 2024 with maintenance, its ability to add seats ends in **October 2026**. Growth after that requires subscription.
2. If it holds subscription already, the cliff has passed and the exposure is annual escalation instead.
3. **Either way the licence model has changed under the university without a decision being taken** — which is `ARC-001-FINOPS-v1.0` lever L-5 exactly, and it is now dated rather than open-ended.

**Published price evidence** (all MEDIUM, aggregators and the vendor education store):

| Item | Published price | AUD indicative |
|------|----------------|----------------|
| Camtasia education | ~US$169 vs US$249–299 standard [MR-C18] | ~A$260 vs A$383–460 |
| Camtasia 2026 plan range | US$39 (Starter, watermarked) to US$599/yr (Pro); Business US$198/user/yr [MR-C18] | A$60 – A$922; Business ~A$305/user/yr |
| Volume 20–50 seats | US$140–160/user/yr [MR-C18] | ~A$216–246/user/yr |

**The Gate 1 candidate nobody has named**: **Microsoft Clipchamp** is browser-based, sits in the M365 ecosystem, and offers *"free access with unlimited watermark-free exports up to 1080p, plus editing tools such as trim, crop and speed control"* [MR-C19]. TechSmith's own comparison positions Clipchamp for *"casual users and quick content creation"* and Camtasia Pro for *"corporate trainers, instructional designers and educators who need end-to-end content creation"* [MR-C19].

That is a credible **segmentation**, not a replacement. Most academic screen-capture is casual; a minority is genuinely instructional-design work.

**Recommendation**: **segment rather than standardise.** Designate a three-tier toolchain — Clipchamp (bundled, no incremental cost) for casual recording and trimming; Camtasia for a **named, justified, counted** cohort of instructional designers and learning technologists; Echo360 for lecture capture and video management. **Remove Articulate 360 and Adobe CS from the video toolchain designation entirely** — Articulate is an authoring tool (§4.4) and Adobe CS is specialist creative work; neither belongs in the answer to REQ-004. Concrete actions before **October 2026**: establish which Camtasia licence model the university actually holds, count the genuine Camtasia cohort, and test Clipchamp against the residual use cases. This is the clearest available L-4 entitlement-rightsizing target in the estate, and it has a deadline attached.

### 4.4 Course Design authoring — Articulate 360, and a trap in the licensing model

`external/system-landscape.md` note 3 requires investigation into the enterprise licensing model; `ARC-001-FINOPS-v1.0` §7.6 item 1 records it as the largest of the six open licensing questions, spanning three capability categories.

`ARC-001-RSCH-v1.0` §3.7 established list pricing at roughly US$1,449–1,749/user/year. Three mechanics were not previously recorded — all MEDIUM confidence, all from pricing aggregators, and all needing vendor confirmation:

| # | Mechanic | Consequence |
|---|----------|-------------|
| C4-1 | An **Educational Organization discount** exists: **US$1,199 → US$899 annually** (≈ A$1,845 → A$1,384) [MR-C20] | The real academic entry price is materially below the headline. A model built on list price would overstate |
| C4-2 | **Pre-July-2024 academic customers hold a 50% grandfather rate, maintained only while the subscription stays active — "lost permanently if the subscription lapses"** [MR-C20] | **The decisive mechanic.** If UoF is a pre-July-2024 academic customer, retirement is **irreversible in price terms**. Re-acquiring later means paying roughly double |
| C4-3 | Volume discounts begin around **10–25 seats**, deepen at 50+ and 100+; multi-year commitments unlock a further 10–20% [MR-C20] | Seat count is the dominant variable, and consolidating scattered school-level purchases into one agreement is itself a lever (L-6) |

**Why C4-2 changes the shape of the decision.** `ARC-001-FINOPS-v1.0` §7.2 lists Course Design authoring — Blackboard, Articulate 360, H5P — as a duplication candidate, and FR-002's rationale names it. Ordinarily a duplication candidate can be retired and, if the decision proves wrong, reversed at moderate cost. **If the grandfather rate is real and the university holds it, that reversibility does not exist here.** Retiring Articulate would be a one-way door.

That does not argue for retention. It argues for the decision to be taken **once, deliberately, with the academic cohort consulted**, rather than as a by-product of a cost exercise — and for a possible middle path: **shrink the seat count to the genuine authoring cohort while keeping the agreement alive**, preserving the grandfather rate at a fraction of the cost. That is L-4 rightsizing rather than L-1 retirement, and it is available only while the subscription remains active.

**Recommendation**: **retain the agreement; rightsize the seats.** Before any decision, Grace Tanaka must establish in writing (a) whether the university holds the pre-July-2024 academic rate, (b) the current seat count and how many are active, and (c) whether school-level Articulate purchases exist outside the central register — `ARC-001-FINOPS-v1.0` §2.3 flags school-funded spend as the row most likely to break the baseline. **Do not retire Articulate before (a) is answered.**

---

## 5. Category C — The Three Net-New Spend Candidates

All three carry prospective new recurring spend against a flat-envelope target and all three are queued at `ARC-001-ADR-007-v1.0` Gate 1.

### 5.1 Miro — Active Learning and Collaboration

**Gate 1 incumbents to test**: Microsoft Whiteboard (inside M365), Padlet, Blackboard collaboration.

| Fact | Evidence | Rating |
|------|----------|--------|
| Tiers: Free; **Starter US$8/user/mo**; **Business US$20/user/mo** (annual billing); **Enterprise custom with a 30-member minimum**. Monthly billing ~20% higher | [MR-C21] | MEDIUM |
| Business includes SSO; **Enterprise adds SCIM and data residency** | [MR-C21] | MEDIUM |
| Education and nonprofit discounts typically **30–50%** on Business and Enterprise | [MR-C21] | MEDIUM |
| **Australian residency: two AU data centres, primary Sydney, backup Melbourne; "Australia data residency is available only for Enterprise Plan"**; in-scope production data, backups and metadata stored in AU with in-region compute | [MR-C22] | MEDIUM-HIGH — vendor |

**The cost floor, and why it is a floor and not an estimate.** NFR-C-002 and REQ-030 make Australian residency a Must, and NFR-SEC-001 requires institutional SSO with MFA and no local accounts. Residency is **Enterprise-only** [MR-C22], and Enterprise carries a **30-member minimum** [MR-C21]. So the minimum compliant Miro configuration is Enterprise × 30 seats — Miro does not publish Enterprise pricing, but Business at US$20/user/month annual is A$369/user/year at the stated conversion, which puts a 30-seat Business-tier floor at roughly **A$11.1k/year before any education discount**, and Enterprise sits above Business. Applying the reported 30–50% education discount to that floor gives an indicative **A$5.5k–7.8k/year** as an order of magnitude only. **This is a shape, not a quote** — Enterprise is custom-priced and the education discount is unconfirmed.

**Gate 1 assessment.** `ARC-001-RSCH-v1.0` §3.8 already flagged that Padlet's SSO and grade passback are tier-gated, and that a Padlet tier without SSO would breach Principle 16 — which must be settled regardless of Miro. What is new is that **Microsoft Whiteboard is already in the M365 estate** and is characterised as a lightweight canvas native to Teams, while Miro is the richer workspace for workshops, structured facilitation and diagramming [MR-C35]. Padlet also has a free-form infinite canvas, "Sandbox" [MR-C35]. Notably, an Australian university publishes a staff-facing digital whiteboard and collaboration tool comparison guide [MR-C35] — a sector artefact worth reading before UoF writes its own.

**Recommendation**: **do not buy yet. Gate 1 fails on entitlement grounds — capability plausibly already exists.** Run the two-stage test: Stage 1, does Whiteboard or Padlet Sandbox meet REQ-011 and REQ-013? Stage 2 is the one `ARC-001-ADR-007-v1.0` §8.4 warns gets skipped — can Whiteboard be configured with **unit-enrolment-group provisioning** (REQ-012), which is the requirement most likely to defeat a bundled tool? If Stage 2 fails on group provisioning, that is a legitimate Gate 1 failure and Miro proceeds to Gate 2 — with the finding that **AU residency is not a default and costs extra**, and with academic endorsement recorded, since ADR-007 §8.4 rightly notes a configured incumbent can deliver worse pedagogy.

### 5.2 OnExam — a negative finding, and a probable mis-scoping

**The finding: "OnExam" could not be identified from any public source.** Four search strategies were run — the bare product name with exam-platform terms; the name with university and assessment qualifiers; punctuation variants; and the name alongside the Australian assessment vendors it would most plausibly compete with. **No matching vendor, product page, documentation or customer reference was located** [MR-C16]. `ARC-001-RSCH-v1.0` §3.9 reached the same conclusion independently. Two separate research passes failing to identify a named platform is itself evidence.

**Why this matters more than it appears.** `ARC-001-ADR-007-v1.0` §5.2 assigns OnExam to Gate 1 against "ExamSoft and Blackboard assessment", and notes that the landscape records it as *not in use* while also requiring investigation into its *extent of use* — *"the signature of a tool already in use somewhere unrecorded."* `ARC-001-FINOPS-v1.0` §7.6 item 5 makes the same point. **But a Gate 1 test cannot be run against an unidentified product**, because Gate 1 asks whether an incumbent provides the same capability — and the capability is unknown.

**A likely explanation, offered as a hypothesis to test rather than a finding.** The Australian market contains a distinct and healthy segment for exam **operations** — scheduling, venue and room allocation, alternative arrangements, accessibility provisions — which is a different product class from exam **delivery** and lockdown proctoring:

| Product | Segment | Evidence | Rating |
|---------|---------|----------|--------|
| **DataBee Exams Manager** | Exam **operations** — *"streamlines exams and student accessibility management"* for higher education; **University of South Australia** and **Charles Sturt University** named | [MR-C33] | MEDIUM |
| **Janison Exam Management** | Exam **operations and delivery** services; **University of Tasmania since around 2009** | [MR-C34] | MEDIUM |
| **ExamSoft / Examplify** (incumbent) | Exam **delivery** — secure lockdown assessment, LMS grade sync; owned by Turnitin since 2020 | `ARC-001-RSCH-v1.0` §3.5 | MEDIUM-HIGH |

**If OnExam is an exam-operations product, ExamSoft is the wrong Gate 1 incumbent** and the gate as written would return a false pass. REQ-017 — high-stakes exams in a secure lockdown environment, on campus and remotely — is a *delivery* requirement, and ExamSoft already addresses it. An operations product would be a **genuine new capability**, not a duplication, and would belong in §6 rather than here.

**Recommendation**: **resolve identity before assessing.** Three steps, in order, owned by Dr. Benny Moog: (1) ask the schools which product they mean and obtain a URL, a vendor entity name or an invoice; (2) classify it as exam **delivery** or exam **operations**, because that determines which gate and which incumbent apply; (3) only then run Gate 1 — against ExamSoft if delivery, against nothing if operations. And **do not close the request on the grounds that the product cannot be found.** An unidentifiable product in the landscape is a register defect (`ARC-001-FINOPS-v1.0` §9.1 condition D-1, shadow acquisition) as much as it is a procurement question.

### 5.3 Badging software — the option set has moved under the decision

`external/system-landscape.md` note 2 names **Badgr, Credly and Milestone**. `ARC-001-ADR-007-v1.0` §5.2 records badging as the honest Gate 4 case: *"No incumbent — a genuine gap."* All three named options have changed, and the Gate 4 classification does not survive contact with the market.

| Named option | What it actually is now | Evidence | Rating |
|--------------|------------------------|----------|--------|
| **"Milestone"** | **Anthology Milestone** — a badging and micro-credentialing product in the **incumbent LMS vendor's own family**. *"Seamless integration with Anthology Blackboard LMS and Blackboard Course Catalog"*; badges defined in Milestone connect to the **Achievements tool in Blackboard Ultra** over **LTI 1.3**; criteria in Blackboard automatically issue Milestone badges; no coding required to create badges | [MR-C23, MR-C24] | HIGH on identity and integration |
| | **Open Badges 3.0 support was released 30 July 2025 — and: *"This release is currently only available in the US. International markets are soon to follow."*** | [MR-C25] | HIGH — vendor blog, verbatim |
| | Operational constraints: students must have an email address in their Blackboard profile to receive Open Badges; achievements are **not retroactive**; Student Preview cannot earn them | [MR-C24] | HIGH |
| **"Badgr"** | **Does not exist under that name.** Concentric Sky acquired by Instructure (2022); Badgr Pro → Canvas Credentials; **Canvas Credentials → Parchment Digital Badges on 31 October 2025** (*"a change in branding only"*). Reached primarily via a **Canvas LMS subscription**. **The legacy free issuer plan ended: *"Free issuer accounts will no longer work after December 31, 2025."*** | [MR-C26] | HIGH |
| **"Credly"** | **Credly by Pearson** — acquired 31 January 2022, total value **US$200m** including Pearson's prior ~20% stake; 2,000+ organisations, 50m+ credentials to 25m users | [MR-C27] | HIGH |
| *(Unnamed, and the most interesting)* | **My eQuals** — the AU/NZ sector credential platform. Used by **100% of Australian and New Zealand public universities**, 90+ providers including most TAFEs; conceived 2015 as a combined AU/NZ sector response to the Groningen Declaration; **digital badges solution based on the Open Badges standard**; **15 AU/NZ institutions already issuing digital badges** | [MR-C29] | MEDIUM |

**Standards context**: Open Badges 3.0 aligns to W3C Verifiable Credentials and Decentralized Identifiers, and 1EdTech-certified OB 3.0 issuers include Accredible, Acreditta, Badgr (Canvas Credentials), Certifier, Credly and POK [MR-C28] — LOW-MEDIUM, aggregator. The practical point is that **portability is now a standards property rather than a vendor property**, which lowers the cost of choosing wrong and argues against paying a premium for "ecosystem visibility."

**Assessment — the ADR-007 classification needs correcting.**

`ARC-001-ADR-007-v1.0` §5.2 uses badging as the worked example proving the hierarchy is not a refusal mechanism, precisely because it *fails* Gate 1 honestly. That reasoning is sound but the premise is wrong: **badging does not clearly fail Gate 1**, because Milestone is a product of the incumbent LMS vendor, integrating into a Blackboard tool the university already has. Whether it is *entitled* under the current Blackboard agreement is unknown — and unknowable without asking — but that is a Gate 1 question, not a Gate 4 one.

This does **not** weaken ADR-007. It strengthens it, by demonstrating that Gate 1 catches cases the requester and the architect both believed were open-market. It does mean §5.2's table should be amended.

**Two constraints on the Milestone path:**

1. **AU availability is unconfirmed and the only dated statement says US-only** [MR-C25]. An Australian university cannot adopt an OB 3.0 badging capability on a US-only release. This must be confirmed in writing before Milestone is treated as live — a direct instance of `ARC-001-RSCH-v1.0`'s standing caution about relying on vendor statements not put to the vendor.
2. **Blackboard's corporate position is recent.** `ARC-001-RSCH-v1.0` §3.2 records emergence from Chapter 11 on 2 March 2026 as a debt-free standalone entity with ~US$70m new capital. Deepening dependence on that vendor's adjacent product set five months after emergence is a decision to take with eyes open, not by default.

**Recommendation**: **maintain the deferral, but re-route the gate.**

- **Confirm the FR-019 deferral.** It is Could-priority; against a flat envelope with Must gaps open, `ARC-001-FINOPS-v1.0` §7.4 and ADR-007 §5.2 both say defer unless offset by a retirement. Nothing found here changes that. **Record the deferral with rationale** — do not let it lapse silently.
- **When it is picked up, enter at Gate 1, not Gate 4.** Ask Blackboard what Milestone costs and whether any of it is entitled, and ask for a written AU availability statement for OB 3.0.
- **Then Gate 3 before Gate 4.** My eQuals is a live sector platform every AU/NZ public university already uses, with Open Badges-based badging and 15 institutions issuing [MR-C29]. `ARC-001-ADR-007-v1.0` §5 says of Gate 3: *"Gate 3 is the gate no one has used."* **This is the first concrete opportunity to use it**, and a recorded answer from My eQuals — including a "no" — discharges the gate.
- **Amend `ARC-001-ADR-007-v1.0` §5.2** so the badging row reads Gate 1 with Milestone named as the incumbent-family candidate, and add Gate 3 with My eQuals named. Replace "Badgr" with "Parchment Digital Badges (formerly Canvas Credentials / Badgr) — Canvas-coupled" so a stale product name does not survive into procurement.

---

## 6. Category D — Capability Gaps With No Incumbent

`ARC-001-ADR-007-v1.0` Gate 1 asks whether capability is already inside something the university pays for. Applying that across the Must-priority requirements and the eight categories, and using only evidence in this document and `ARC-001-RSCH-v1.0`:

| Gap | Requirement | Incumbent candidate | Gate 1 verdict | Source |
|-----|------------|--------------------|----------------|--------|
| **Integration mediation with runtime schema enforcement** | REQ-023, 024, 027 | Microsoft agreement / Power Automate / PeopleSoft IB | **FAILS Gate 1** — no entitlement (§3.2); PeopleSoft IB is a source adapter, not a broker [P4-TN1] | **The genuine gap.** Proceeds to Gate 4 on Azure |
| **Automated role authority** | REQ-024 | No platform holds institutional role as authoritative | **FAILS** — but this is a **BUILD** at Gate 5: it is the university's own governance artefact, per `ARC-001-RSCH-v1.0` §5.1 | Build |
| **Canonical data model** | REQ-027 | None — no vendor supplies it | **FAILS** — Gate 5 build, deriving from OneRoster 1.2 entity definitions per `ARC-001-RSCH-v1.0` §5.1 | Build |
| **Capability and boundary register** | BR-001 | None | **FAILS** — Gate 5 build. Institutional asset | Build |
| **Digital badging** | REQ-019 (Could) | **Anthology Milestone**, inside the Blackboard family | **DOES NOT FAIL** — reclassified (§5.3) | Gate 1 → Gate 3 → Gate 4 |
| **Collaborative whiteboard** | REQ-011, 013 | Microsoft Whiteboard, Padlet Sandbox | **PROBABLY DOES NOT FAIL** on Stage 1; Stage 2 turns on REQ-012 group provisioning (§5.1) | Gate 1 |
| **Secure exam delivery** | REQ-017 | ExamSoft / Examplify | **DOES NOT FAIL** — incumbent addresses it. The OnExam question is a different, possibly operations-class need (§5.2) | Gate 1, pending identity |
| **Exam operations / accessibility arrangements** | *No requirement written* | None identified | **Cannot assess — no requirement exists.** If OnExam is operations-class, this is an unwritten requirement, not an unapproved purchase | **Register defect** |
| **Multi-camera / high-fidelity capture** | REQ-010 (Could) | Echo360, appliance-dependent | **PARTIAL** — platform capable, appliance estate out of scope but cost-dependent (§4.1) | Boundary decision |

**Two observations worth carrying to RIFF.**

First, **the only capability gap that legitimately reaches Gate 4 for open-market purchase is the integration broker** — and that is the one ADR-001 already decided. Every other candidate either fails to a build at Gate 5 because it is a governance artefact, or does not fail Gate 1 at all. That is a strong validation of ADR-007's default posture and worth saying: the hierarchy is not producing a queue of blocked purchases, it is producing one purchase and several configurations.

Second, the **exam-operations row is a requirements defect, not a sourcing question.** If the schools are asking for exam operations capability, no requirement in `external/requirements-register.md` expresses it. REQ-017 covers delivery. A tool arriving to meet an unwritten requirement is how undeclared duplication forms (BR-007), and the fix is to write the requirement or close the request — not to assess a product against a gap nobody has stated.

---

## 7. Gate 3 — Sector Aggregation, the Gate No One Has Used

`ARC-001-ADR-007-v1.0` §5 is blunt: *"Gate 3 is the gate no one has used."* `ARC-001-SOBC-v1.0` §C1.3 identifies CAUDIT as an uninvestigated route and notes that every Australian university with a student information system, a timetabling system and an LMS faces a near-identical integration problem. `ARC-001-FINOPS-v1.0` §7.7 lists sector aggregation as **"Not investigated."**

It is investigated now, at least to the point of naming live routes. This is the genuine Australian equivalent of the UK G-Cloud framework this document deliberately did not search, and it is materially different in kind: not a purchasing catalogue with published rates, but sector-negotiated panels and consortium arrangements.

| Route | What it is | Relevance | Evidence | Rating |
|-------|-----------|-----------|----------|--------|
| **CAUDIT — Microsoft LSP Panel 2026** | A sector-negotiated Licensing Solution Provider panel, with a **Microsoft renewal in progress** and joint Microsoft–CAUDIT initiatives described as having *"the opportunity to transform the Higher Education sector in Australia"* | **Directly relevant to ADR-006 Condition 1.** The Azure rate treatment, and any MACC structure, would plausibly be negotiated through this panel rather than bilaterally. §3.2 question 1c should be asked **through** it | [MR-C13] | MEDIUM — page returned 403; facts from search extracts |
| **CAUDIT IT Procurement Community of Practice** | Draws on *"Software Licensing and ICT Procurement representatives from Universities throughout Australasia"* | The forum in which the "has anyone solved the PeopleSoft-to-LMS integration problem?" question gets asked. Costs nothing but Grace Tanaka's time | [MR-C13] | MEDIUM |
| **CAUDIT Cloud** | A platform *"to simplify procurement processes for universities and other research organisations, addressing the complexity and expense that can accompany cloud environment adoption"* | Worth assessing against the ADR-006 landing-zone plan before build | [MR-C13] | MEDIUM |
| **AWS — 2026 CAUDIT Engagement Partner** | AWS engages with CAUDIT throughout 2026 | Does **not** reopen ADR-006 — that decision turned on operating surface and Principle 19, not on rate. But it means a sector-rate AWS comparison is obtainable if ADR-006 does return to RIFF | [MR-C13] | MEDIUM |
| **AARNet — Zoom for education** | AARNet delivers Zoom licensing and support to *"the majority of Australia's universities"*; first Australian Zoom Platinum Partner; cloud-recording region selectable to Australia | An **existing** Gate 3 relationship the university may already be inside. Retiring Zoom would forfeit it (§4.1) | [MR-C14] | MEDIUM-HIGH |
| **My eQuals** | AU/NZ sector credential platform, 100% of public universities, Open Badges-based badging, 15 institutions issuing | The Gate 3 answer for badging (§5.3) | [MR-C29] | MEDIUM |

**Recommendation.** Add a **standing Gate 3 step** to the RIFF process: before any Gate 4 competitive process, Procurement records a written answer from the relevant sector route — **including a "no"**. `ARC-001-ADR-007-v1.0` already requires this; what was missing was the list of routes to ask. There now is one.

Three specific asks, all inside 60 days and all owned by Grace Tanaka:

1. **CAUDIT Microsoft LSP Panel** — what does the sector arrangement give on Azure messaging, eventing and Log Analytics meters? This is §3.2 question 1c, asked in the right place.
2. **CAUDIT IT Procurement CoP** — has any Australasian university solved PeopleSoft ↔ LMS ↔ timetabling ↔ placement integration, and what did they use? `ARC-001-SOBC-v1.0` §C1.3 predicted the answer is yes.
3. **My eQuals** — what does its badging solution cover, and what does it cost a member institution? (§5.3)

> **The cheapest finding in this document is that the sector has probably already solved the integration problem, and nobody has asked.** Item 2 costs an email.

---

## 8. Build vs Buy and Three-Year Total Cost of Ownership

### 8.1 Build vs Buy by decision

| # | Decision | Verdict | Gate | Reversibility |
|---|----------|---------|------|--------------|
| 1 | Integration broker runtime | **BUY — managed, Azure `australiaeast`** | 4 | Medium — AMQP 1.0 and portable schemas per ADR-006 Condition 3 |
| 2 | Schema registry | **BUY — bundled in Event Hubs Standard+** | 4 | Medium — Confluent-compatible patterns keep Apicurio open |
| 3 | Orchestration / adapters | **ASSESS — Logic Apps Standard as complement** | 1 | High |
| 4 | Canonical model, role authority, rollover, capability register | **BUILD** | 5 | N/A — institutional assets |
| 5 | Badging | **DEFER; then Gate 1 → 3 → 4** | 1 | High — OB 3.0 portability lowers switching cost |
| 6 | Whiteboard (Miro) | **GATE 1 — test Whiteboard and Padlet first** | 1 | High |
| 7 | Exam platform (OnExam) | **BLOCKED — resolve identity** | — | — |
| 8 | Course evaluation | **BUY one, three-way competitive** | 2 → 3 → 4 | Low — evaluation history migration is costly |
| 9 | Video toolchain | **BUY, segmented three tiers** | 1 → 2 | Medium |
| 10 | Authoring (Articulate) | **RETAIN agreement, rightsize seats** | 4 renewal | **LOW — grandfather rate lost permanently on lapse** |
| 11 | Capture primary | **RETAIN Echo360, narrow scope** | 2 | Low — appliance estate dependency |

### 8.2 Published price evidence — all of it, dated

Every external price signal located on 2026-07-29. AUD at USD 1.00 ≈ AUD 1.54, an assumption.

| Product | Published price (as published) | AUD indicative | Rating | Cite |
|---------|-------------------------------|----------------|--------|------|
| Azure Service Bus Premium | ~US$677/month per messaging unit; namespace holds 1, 2 or 4 MUs; flat rate, no transaction charge | ~A$1,042/mo; ~A$12.5k/yr per MU | MEDIUM (cost estimator, US reference) | [P4-VP3], [MR-C2] |
| Azure Service Bus Standard | Base hourly charge + tiered per-million-operations | Not rendered | MEDIUM | [MR-C1], [P4-VP3] |
| Azure Service Bus zone redundancy | **Nil** — automatic in all tiers | **Nil** | **HIGH** | [MR-C3] |
| Azure Event Hubs Standard | Per throughput unit + per-million operations; **schema registry included** | Not rendered | MEDIUM-HIGH | [MR-C5], [P4-VP3] |
| Logic Apps Standard built-in operations | **Unlimited, free**; managed connectors metered per call | **Nil** for built-in | **HIGH** | [MR-C7] |
| Confluent Cloud | Basic US$50–300/mo; Standard US$1,000–3,000/mo; Enterprise US$5,000–20,000/mo; Schema Registry Advanced US$1/hr. **CKU rates undisclosed** | ~A$77–462/mo … A$7.7k–30.8k/mo | MEDIUM | [P4-VP2], [MR-C10] |
| CloudAMQP dedicated RabbitMQ | Big Bunny US$297/mo; Happy Hare US$597/mo; Roaring Rabbit US$897/mo; VPC peering US$99/mo | ~A$457 / A$919 / A$1,381 / A$152 per month | HIGH (vendor plans page) | [P4-VP1] |
| Articulate 360 academic | **US$1,199 → US$899/yr** with Educational Organization discount; AI Teams US$1,749/user/yr; AI Personal US$1,449/user/yr; **pre-Jul-2024 academic 50% grandfather, lost permanently on lapse** | A$1,845 → **A$1,384/user/yr**; A$2,693; A$2,231 | MEDIUM | [MR-C20] |
| Camtasia | Education ~US$169 vs US$249–299 standard; 2026 plans US$39–599/yr; Business US$198/user/yr; volume 20–50 seats US$140–160/user/yr | ~A$260 vs A$383–460; A$60–922; A$305; A$216–246 | MEDIUM | [MR-C18] |
| Microsoft Clipchamp | **Free**, unlimited watermark-free export to 1080p | **Nil** | MEDIUM-HIGH | [MR-C19] |
| Miro | Starter US$8/user/mo; Business US$20/user/mo (annual); Enterprise custom, **30-member minimum**; education/nonprofit 30–50% | A$148 / A$369 per user/yr; Enterprise above Business | MEDIUM | [MR-C21] |
| Miro AU residency | **Enterprise plan only** — no separate price published | Included in Enterprise | MEDIUM-HIGH | [MR-C22] |
| Qualtrics CoreXM | ~US$25,000–50,000/yr small-to-mid; modules extra; **Academic Plan removed**; 3-year commitments | ~A$38.5k–77k/yr | **LOW-MEDIUM** — one source is a competitor | [MR-C32] |
| Echo360, Evasys, Explorance Blue, ExamSoft, Turnitin, Anthology Milestone, Parchment Digital Badges, Credly, My eQuals | **No list pricing published.** Echo360 explicitly custom-priced with no free plan; Evasys and Blue quote per institution | — | — | [MR-C15, MR-C30, MR-C31] |

> **The distribution is the finding.** Nine of the eighteen product lines the university most needs to price publish nothing at all. `ARC-001-RSCH-v1.0` §5.3 found the same and drew the same conclusion: **the September business case cannot be built on public price evidence, and the WP3 contract register is on the critical path.** This document confirms that independently, from a different and larger sample, and adds one qualification — **the broker line is the exception.** It is the one component whose cost is derivable from published cloud meters plus a volume assumption, and §8.3 derives it.

### 8.3 The one computable line — broker three-year TCO

Because the workload is specified (7–9 integrations, fewer than 10,000 events/day, AU region) and the meters are public, this line can be modelled rather than marked `TBD-WP3`.

```
BrokerTCO(3yr) = Σ(n=1..3) [ Messaging(n) + Eventing(n) + Observability(n) + Compute(n) ]
               + LandingZone + SchemaDefinition + SkillsUplift
               + Contingency

where, for the recommended Standard-tier configuration:
  Messaging(n)     = ServiceBusStandard_base + (operations × per-million-rate)
  Eventing(n)      = EventHubsStandard_TU × hours          [schema registry included]
  Observability(n) = LogAnalytics_GB_ingested × rate       [the dominant variable — DR-006 retention]
  Compute(n)       = event-triggered managed compute, reconciliation service
  ZoneRedundancy   = 0                                     [MR-C3 — free at all tiers]
```

| Variable | Status | Owner |
|----------|--------|-------|
| Event volume | **Known** — fewer than 10,000/day [P4-TN1] | Sam Okafor |
| Service Bus tier | **Decided** — Standard, with three named Premium triggers (§3.4) | Sam Okafor |
| Event Hubs tier | **Decided** — Standard is a floor [MR-C5] | Sam Okafor |
| Meter rates under the university's agreement | **`TBD-WP3`** — Condition 1 question 1c, asked via the CAUDIT LSP panel (§7) | Grace Tanaka |
| Log Analytics GB ingested | **`TBD-WP3`** — set by DR-006 retention policy, not by the platform | Sam Okafor with Eleanor Frame |
| Landing zone / schema / skills effort | Estimable in days once WP5 defines the target architecture; **no institutional blended day rate is published** | Digital & IT |

**Anchor**: project 004's independently-derived **A$63k – 105k over three years** for this configuration [P4-TN1] ≈ **A$21k – 35k/year**, against the SOBC's **$80k – 150k/year**. §3.5 reconciles.

**Assumptions**: volume is stable across three years; Standard tier suffices (falsified by any Premium trigger firing); log retention is bounded by DR-006; recovery stays code-and-configuration per ADR-005, since a warm posture roughly doubles the MU line [MR-C4]; no second broker; USD 1.00 ≈ AUD 1.54.

### 8.4 Scenario comparison

`ARC-001-RSCH-v1.0` §5.4 already assessed four estate-level scenarios and recommended D (declare boundaries, retire undeclared overlaps, fix the joins). That is not re-litigated. These scenarios are **sourcing** scenarios inside D.

| Scenario | Shape | Assessment |
|----------|-------|-----------|
| **S1 — Approve all three net-new requests** | Three new recurring lines: Miro Enterprise (AU residency floor), OnExam (unpriceable), badging | **Reject.** Fails REQ-035 with no offsetting retirement; two of the three fail or cannot pass Gate 1 |
| **S2 — Refuse all three** | No new spend | **Reject.** Would be the procurement freeze `ARC-001-ADR-007-v1.0` §7.5 anticipates as the main criticism. Badging is genuinely wanted and Milestone may be near-free inside the Blackboard relationship |
| **S3 — Gate 1 all three; buy the broker at Standard tier; segment the video toolchain; run evaluation three-way at the boundary** | One new commitment (broker, re-based downward); zero to one new licence lines; two retirements available at boundaries (one survey platform, most Camtasia seats) | **Recommended.** The only scenario that closes the Must-priority integration gap while leaving REQ-035 achievable, and the only one whose savings land at contract boundaries as §7.2 of FINOPS requires |
| **S4 — S3 plus retire Echo360** | Larger licence saving | **Reject on current evidence.** Fails REQ-009 and REQ-010, strands the capture appliance estate, and forfeits the only WCAG 2.2 AA declaration in the estate. Revisit only if the appliance refresh forces it |

### 8.5 Risk-adjusted contingency

Percentages against whatever base WP3 produces. These are **additional to** and **do not replace** `ARC-001-RSCH-v1.0` §5.5.

| Element | Contingency | Driver |
|---------|------------|--------|
| Broker recurring (Azure Standard tier) | **+25%** | Meter rates unknown; log ingestion is the volatile line; a Premium trigger firing is a step change, not a percentage |
| Broker one-off (landing zone, schema, skills) | **+20%** | Standards exist on both sides; the risk is institutional capacity, per `ARC-001-RSCH-v1.0` §5.5 |
| Miro, if approved | **+40%** | Enterprise custom-priced; the 30-seat minimum may exceed genuine demand; education discount unconfirmed |
| Badging, if approved | **+35%** | No published price for any option; Milestone AU availability unconfirmed |
| OnExam | **Not costable** | Product unidentified. A contingency on an unknown base is a fiction |
| Course evaluation transition | **+30%** | Evaluation history migration and academic-reporting continuity; three-way process cost |
| Camtasia position | **+15%** | Licence-model change already occurred; exposure depends on which model is held |
| Articulate | **+10%, plus a stated one-way-door risk** | Grandfather rate is a **binary** exposure, not a percentage — model it as a scenario |

### 8.6 What cannot be costed, and exactly why

Five closures make Section 8 computable. Four are inside the engagement's control; the fifth is not.

1. **Meter rates under the university's Microsoft agreement** — Condition 1 question 1c, via the CAUDIT LSP panel. Owner: Grace Tanaka. Without it, §8.3 is list-price arithmetic.
2. **DR-006 log retention policy** — sets the dominant observability variable. Owners: Sam Okafor, Eleanor Frame.
3. **The institutional blended day rate** — unchanged from `ARC-001-RSCH-v1.0` §5.6. Without it the build components size in effort, not money.
4. **Which Camtasia and Articulate licence models the university holds** — both have dated cliffs and one has a one-way door. Owner: Grace Tanaka. This is L-5, and it is now urgent rather than open-ended.
5. **The identity of OnExam** — Owner: Dr. Benny Moog. Not costable at any confidence until resolved.

> This document declines to present a headline three-year figure for the estate, for the same reason `ARC-001-RSCH-v1.0` §5.6 declined. It does present a computable model and a defensible anchor for the **one** line that can be derived from public meters — and it argues that the existing SOBC figure for that line should be corrected downward before September rather than defended.

---

## 9. Requirements Traceability

| Requirement | Priority | Position established | Gate | Section |
|-------------|----------|---------------------|------|---------|
| REQ-002 | Should | Articulate mechanics and grandfather trap established; retain-and-rightsize recommended | 4 renewal | §4.4 |
| REQ-004 | Must | Three-tier segmented toolchain; Camtasia October 2026 cliff dated; Clipchamp as Gate 1 candidate | 1 → 2 | §4.3 |
| REQ-008 | Must | One primary for synchronous delivery; other declared as bounded exception | 2 | §4.1 |
| REQ-009 | Must | Echo360 retained as capture primary — only product designed for it | 2 | §4.1 |
| REQ-010 | Could | Remains the binding constraint on the capture decision; appliance dependency declared | 2 | §4.1 |
| REQ-011, 013 | Must / Should | Whiteboard and Padlet Sandbox to be tested before Miro | 1 | §5.1 |
| REQ-012 | Must | Identified as the Stage 2 test most likely to defeat a bundled whiteboard | 1 | §5.1 |
| REQ-017 | Must | ExamSoft addresses it; OnExam is a separate, possibly operations-class question | 1 | §5.2 |
| REQ-019 | Could | Reclassified Gate 4 → Gate 1; deferral confirmed; Gate 3 route found | 1 → 3 | §5.3 |
| REQ-021 | Must | Three-way market established; APP 8 and duplication align | 2 → 3 → 4 | §4.2 |
| REQ-023, 024, 025 | Must | Managed Azure broker; entitlement re-scoped; tier floors set | 4 | §3 |
| REQ-027 | Must | Schema registry requires Event Hubs Standard+; enforcement is client-side with a named mitigation | 4 | §3.3 |
| REQ-028 | Must | Broker recommendation covers the placement grade flow (ADR-001 Condition 3 phasing) | 4 | §3.6 |
| REQ-030 | Must | AU residency confirmed for Azure and Miro-Enterprise; Evasys offshore; Blue unestablished | — | §8.2 |
| REQ-032 | Must | Zone redundancy free in all tiers; manual promotion must be in the RTO | — | §3.3 |
| REQ-035 | Should | Broker line re-based downward; two of three net-new commitments deferrable; two retirements available at boundaries | — | §8.4 |

**Coverage**: 16 of 35 requirements have a sourcing position. The 19 not covered were excluded deliberately (§1.1) and are recorded in Appendix C.

---

## 10. Vendor Shortlist for Further Evaluation

| # | Product | Category | Next action | Owner | By |
|---|---------|----------|------------|-------|-----|
| 1 | Azure Service Bus + Event Hubs | Broker | Condition 1 questions 1a–1c via CAUDIT LSP panel; confirm Standard-tier meter rates | Grace Tanaka | 2026-08-12 |
| 2 | Confluent Cloud | Broker contingency | Record the written trigger; do not engage sales yet | Sam Okafor | 2026-08-21 |
| 3 | Explorance Blue | Evaluation | Written AU residency and APP 8 statement; indicative institutional quote | Grace Tanaka | 2026-09-30 |
| 4 | Anthology Milestone | Badging | Written AU availability statement for OB 3.0; entitlement position under the Blackboard agreement | Grace Tanaka | 2026-09-30 |
| 5 | My eQuals | Badging — sector | Gate 3 enquiry: badging scope and member cost | Grace Tanaka | 2026-09-30 |
| 6 | Microsoft Clipchamp | Video | Gate 1 Stage 2 test against residual Camtasia use cases | Dr. Benny Moog | 2026-09-30 |
| 7 | Microsoft Whiteboard | Whiteboard | Gate 1 Stage 2 test on REQ-012 group provisioning | Dr. Benny Moog | 2026-09-30 |
| 8 | Miro | Whiteboard | Engage **only if** item 7 fails on group provisioning | Dr. Benny Moog | Conditional |
| 9 | *OnExam* | Assessment | **Identify the product.** No vendor engagement possible until then | Dr. Benny Moog | 2026-08-21 |

---

## 11. Where This Document Differs From Existing Artefacts

Recorded explicitly so no reader has to reconcile two artefacts by inference.

| # | Artefact and location | What it says | What this document finds | Recommended action |
|---|----------------------|-------------|-------------------------|--------------------|
| D-1 | `ARC-001-SOBC-v1.0` §D1.2; `ARC-001-FINOPS-v1.0` §2.4 | Broker licence/hosting **$80k–150k per year** | Project 004 evidence and public meters support ~**A$21k–35k/year** at Standard tier | Re-derive as three components; correct before September (§3.5) |
| D-2 | `ARC-001-ADR-001-v1.0` Condition 1; `ARC-001-ADR-006-v1.0` Condition 1 | Asks whether the Microsoft agreement "already provides" brokering capability | MACC is a spend commitment, not an entitlement; M365 A3/A5 Power Automate excludes Azure premium connectors. A literal "no" would return a sound decision to RIFF on a technicality | Re-scope to questions 1a–1c; record that a **tested** result satisfies Principle 19 (§3.2) |
| D-3 | `ARC-001-ADR-007-v1.0` §5.2; `ARC-001-FINOPS-v1.0` §7.4 | Badging: *"No incumbent — a genuine gap"*, reaches Gate 4 | "Milestone" is **Anthology Milestone**, in the incumbent LMS vendor's family, integrating to Blackboard Achievements over LTI 1.3. Badging is a Gate 1/2 question | Amend §5.2's badging row; replace the stale "Badgr" name; add My eQuals at Gate 3 (§5.3) |
| D-4 | `ARC-001-ADR-007-v1.0` §5.2 | OnExam: Gate 1 against "ExamSoft and Blackboard assessment" | Product unidentifiable; may be exam **operations**, a different class, in which case ExamSoft is the wrong incumbent and the gate returns a false pass | Resolve identity before assessing; treat the register entry as a possible defect (§5.2) |
| D-5 | `ARC-001-FINOPS-v1.0` §7.2 | Evaluation & Analytics is *"the cleanest pair in the estate"* | It is a **three-way** market. Qualtrics' academic terms have moved; Blue holds 50% of the Go8 and has a documented EvaSys-replacement path | Reframe as three-way competitive at the contract boundary (§4.2) |
| D-6 | `ARC-001-FINOPS-v1.0` §7.7; `ARC-001-SOBC-v1.0` §C1.3 | Sector aggregation *"Not investigated"* | Six live routes now named, three with specific asks | Add a standing Gate 3 step to RIFF (§7) |
| D-7 | `projects/004-integration-platform/vendors/cloudamqp-profile.md` | AU data centres *"PROBABLE... specific confirmation required"* | Sydney `ap-southeast-2` confirmed available | Close the open question in the profile; the recommendation is unchanged (§3.3 N-8) |
| D-8 | `projects/004-integration-platform/vendors/microsoft-azure-integration-services-profile.md` | Records the 99.99% Premium SLA; no tier constraint on Schema Registry | Zone redundancy is free at **all** tiers; Schema Registry is **unavailable on Basic**; Microsoft's own term is "client-side schema enforcement" | Add N-1, N-4 and N-5 to the profile at next update (§3.3) |

**None of these findings invalidates a decision.** D-2 and D-3 change how two conditions are worded and which gate one request enters. D-1 changes a number in the university's favour. The rest sharpen positions already taken.

---

## 12. Spawned Knowledge — Deferred, Not Skipped

The `/arckit:research` command normally spawns vendor profiles and tech notes. The generating task restricted writes to this artefact alone, so **nothing was spawned**. Recording what would be spawned means the next run creates them without re-researching.

**Vendor profiles to create** (`projects/001-lt-ecosystem/vendors/`):

| Slug | Basis in this document |
|------|----------------------|
| `anthology-milestone-profile.md` | §5.3 — identity, LTI 1.3 Blackboard integration, OB 3.0 US-only constraint, operational limits [MR-C23, MR-C24, MR-C25] |
| `explorance-profile.md` | §4.2 — Go8 market position, product family, EvaSys replacement precedent, residency unknown [MR-C30, MR-C31] |
| `myequals-profile.md` | §5.3, §7 — sector ownership, coverage, Open Badges basis, Gate 3 status [MR-C29] |
| `techsmith-profile.md` | §4.3 — perpetual discontinuation, October 2026 seat cliff, education and volume pricing [MR-C17, MR-C18] |
| `articulate-profile.md` | §4.4 — academic discount, grandfather rate and lapse trap, volume thresholds [MR-C20] |
| `miro-profile.md` | §5.1 — tier structure, Enterprise-only AU residency, Sydney/Melbourne, 30-seat minimum [MR-C21, MR-C22] |

**Profiles to update, not create** (in `projects/004-integration-platform/vendors/`): add N-1, N-4, N-5 to the Azure profile; close the AU-region open question in the CloudAMQP profile; add eCKU/Freight to the Confluent profile.

**Tech notes to create** (`projects/001-lt-ecosystem/tech-notes/`):

| Slug | Content |
|------|---------|
| `microsoft-entitlement-vs-commitment.md` | §3.2 — MACC as commitment not entitlement; M365 A3/A5 Power Automate boundary; the three re-scoped Condition 1 questions. **The highest-reuse note here** — it applies to every future Microsoft-adjacent Principle 19 test |
| `open-badges-3-vendor-landscape-2026.md` | §5.3 — Milestone / Parchment / Credly / My eQuals; OB 3.0 as a portability property; the two rebrands and the free-tier sunset |
| `au-heled-sector-procurement-routes.md` | §7 — CAUDIT panels and CoP, CAUDIT Cloud, AARNet Zoom, My eQuals; the standing Gate 3 step |
| `course-evaluation-market-anz-2026.md` | §4.2 — three-way market, Go8 share, Qualtrics academic-plan withdrawal, residency positions |

**Tech note to update**: `projects/004-integration-platform/tech-notes/event-broker-comparison.md` — add the RabbitMQ 4.3 confirmation (N-7) and the Logic Apps Standard option (A5), neither of which is in the current six-way matrix.

---

## 13. Risks and Mitigations

### 13.1 Vendor and market risks

| ID | Risk | L | I | Mitigation | Owner |
|----|------|---|---|-----------|-------|
| MR-R1 | Condition 1 returns a literal "no" and ADR-006 goes back to RIFF, delaying every integration | HIGH | HIGH | Re-scope to 1a–1c **before** asking; present the tested-result reading of Principle 19 (§3.2) | Cassandra Rhodes |
| MR-R2 | Anthology Milestone is not available in Australia, and badging has no incumbent-family option after all | MEDIUM | LOW | FR-019 is Could and already deferred. Gate 3 via My eQuals is the fallback | Grace Tanaka |
| MR-R3 | Articulate is retired before the grandfather-rate position is known, and re-acquisition costs roughly double | MEDIUM | MEDIUM | **Do not retire before the position is confirmed in writing** (§4.4). Rightsize instead | Grace Tanaka |
| MR-R4 | The Camtasia October 2026 seat cliff passes unnoticed and growth forces an unplanned subscription | MEDIUM | LOW | Dated action in §4.3; add to the renewal calendar due 2026-08-21 | Grace Tanaka |
| MR-R5 | Qualtrics renewal lands at materially higher cost on a three-year commitment before the three-way assessment runs | MEDIUM | HIGH | Establish both contract boundaries first; do not renew inside the `ARC-001-FINOPS-v1.0` §8.2 gate without a boundary decision | Grace Tanaka |
| MR-R6 | Blackboard's post-Chapter-11 product direction changes Milestone or Achievements | MEDIUM | MEDIUM | Do not make badging dependent on a single vendor's adjacent roadmap; OB 3.0 portability limits the damage | Dr. Benny Moog |
| MR-R7 | Explorance Blue turns out to host offshore, and the APP 8 argument for switching collapses | MEDIUM | MEDIUM | Residency is a **precondition** of shortlisting, not a discovery during evaluation (§4.2) | Eleanor Frame |
| MR-R8 | Miro is approved on the Business tier for price, breaching REQ-030 because residency is Enterprise-only | MEDIUM | HIGH | Enterprise is the **only** compliant tier [MR-C22]; record it as a condition of any approval | Dr. Benny Moog |

### 13.2 Technical risks

| ID | Risk | L | I | Mitigation | Owner |
|----|------|---|---|-----------|-------|
| MR-R9 | A producer bypasses the SDK and non-conformant events enter the estate — client-side enforcement's known failure mode | MEDIUM | HIGH | Mandatory SDK path as a condition of ADR-001 delivery; the Confluent trigger fires on a second occurrence in one teaching period (§3.6) | Sam Okafor |
| MR-R10 | Event Hubs is provisioned at Basic on cost grounds and DR-001 cannot be enforced at runtime | LOW | HIGH | Standard is stated as an architectural floor, not a preference [MR-C5] (§3.6) | Sam Okafor |
| MR-R11 | The RTO assumes automatic failover; promotion is manual and human decision time is unbudgeted | MEDIUM | MEDIUM | ADR-006 Condition 2 RTO must include detection and decision time [MR-C3] (§3.3) | Sam Okafor |
| MR-R12 | Log Analytics ingestion becomes the dominant unplanned recurring cost | MEDIUM | MEDIUM | DR-006 retention set **before** build; ingestion metered monthly per `ARC-001-FINOPS-v1.0` §4.1 | Sam Okafor |
| MR-R13 | Premium is provisioned "for headroom" at ~A$12.5k/yr per MU with no trigger having fired | MEDIUM | MEDIUM | Three named Premium triggers recorded at RIFF; Standard is the default (§3.4) | Sam Okafor |

### 13.3 Compliance risks

| ID | Risk | L | I | Mitigation | Owner |
|----|------|---|---|-----------|-------|
| MR-R14 | Evasys is renewed on a German-hosted footprint without an APP 8 assessment, while an AU-resident alternative is on the market | MEDIUM | HIGH | Gate 4 of the `ARC-001-FINOPS-v1.0` §8.2 renewal gate blocks renewal without a residency position | Eleanor Frame |
| MR-R15 | A badging platform issues credentials from a US-only release, placing student credential data offshore | LOW | HIGH | Written AU availability statement is a precondition of shortlisting (§5.3) | Eleanor Frame |
| MR-R16 | An unidentified platform (OnExam) is in unrecorded use holding student assessment data | MEDIUM | HIGH | Treat as `ARC-001-FINOPS-v1.0` §9.1 condition D-1 shadow acquisition; escalate to RIFF (§5.2) | Dr. Benny Moog |

---

## 14. Next Steps

### Immediate — before 2026-08-21 (the WP3 baseline date)

1. **Re-scope ADR-001 / ADR-006 Condition 1** to questions 1a–1c and put them to the Microsoft LSP **via the CAUDIT panel**. Owner: Grace Tanaka with Cassandra Rhodes. §3.2, §7.
2. **Re-derive the broker recurring line as three components** and take the corrected figure to Steering before the business case. Owner: Sam Okafor. §3.5.
3. **Identify OnExam.** Ask the schools for a URL, vendor entity or invoice; classify as delivery or operations. Owner: Dr. Benny Moog. §5.2.
4. **Establish the Articulate grandfather-rate position in writing** — and issue a standing instruction not to retire Articulate until it is known. Owner: Grace Tanaka. §4.4.
5. **Establish which Camtasia licence model is held**, ahead of the October 2026 cliff. Owner: Grace Tanaka. §4.3.
6. **Send the CAUDIT IT Procurement CoP enquiry**: has any Australasian university solved this integration problem? Owner: Grace Tanaka. §7.

### Weeks 3–8

7. **Amend `ARC-001-ADR-007-v1.0` §5.2** — badging to Gate 1 with Milestone named; stale "Badgr" replaced; My eQuals added at Gate 3. Owner: Dr. Benny Moog. §5.3.
8. **Run Gate 1 Stage 2 tests** on Microsoft Whiteboard (REQ-012 group provisioning) and Clipchamp (residual Camtasia use cases), with academic endorsement recorded. Owner: Dr. Benny Moog. §5.1, §4.3.
9. **Obtain written AU residency statements** from Explorance and Anthology (Milestone OB 3.0). Owner: Grace Tanaka. §4.2, §5.3.
10. **Record the Confluent contingency trigger** in the ADR-001 implementation record. Owner: Sam Okafor. §3.6.
11. **Add the standing Gate 3 step** to the RIFF process. Owner: Grace Tanaka. §7.

### Weeks 9–16

12. **Cost Logic Apps Standard as a complement** to Service Bus + Event Hubs. Owner: Sam Okafor. §3.4 Option A5.
13. **Set DR-006 retention** before the observability build. Owners: Sam Okafor, Eleanor Frame. §8.3.
14. **Spawn the six vendor profiles and four tech notes** in §12. Owner: Sam Okafor.
15. **Prepare the three-way course-evaluation assessment** against the established contract boundaries. Owner: Grace Tanaka. §4.2.

### Downstream commands

| Command | What this document feeds it |
|---------|---------------------------|
| `/arckit:wardley` | Broker at ~0.80 commodity; badging and whiteboard reclassified toward product/commodity as OB 3.0 and bundled canvases commoditise |
| `/arckit:sobc` | §3.5's corrected broker line and §8.3's model for the Economic Case; §8.2's dated price evidence |
| `/arckit:evaluate` / `/arckit:score` | §10's shortlist with the conditions each vendor must satisfy before scoring |
| `/arckit:sow` | The six standing contract requirements plus the tier floors in §3.6 |
| `/arckit:finops` | Re-based L-7; a dated L-5 (Camtasia, Articulate); a live L-3 position on all three net-new requests |

---

## Appendices

### Appendix A — Research Methodology and Evidence Rules

**Conducted**: 2026-07-29. **Tools**: 24 web searches and page fetches; 3 Microsoft Learn documentation queries via MCP.

**Evidence rules applied:**

1. **Citation required.** Every external claim carries an `[MR-Cn]` ID resolving to a URL in the Document Register, with a confidence rating.
2. **Confidence is assigned by source class, then adjusted.** Vendor documentation, vendor support pages, vendor policy pages and corporate press releases rate HIGH. Microsoft Learn rates HIGH. Vendor marketing with specific verifiable claims rates MEDIUM-HIGH. Pricing aggregators, institutional pages and sector-body pages that did not render rate MEDIUM. Competitor-published commentary and single-source pricing claims rate LOW-MEDIUM.
3. **Interested sources are named as interested.** [MR-C32] is partly competitor-published and says so at the point of use.
4. **Nothing about the University of Funk is sourced externally.** Organisational facts come only from the supplied artefacts and are cited as `[D*]` or by artefact name.
5. **Negative findings are results.** §5.2 is the primary instance; §1.7 lists the others.
6. **Prices are quoted in the currency published**, with an AUD indicative conversion at a stated assumed rate. No conversion is presented as a quote.
7. **Project 004 is cited, not restated.** `[P4-*]` IDs point at existing artefacts; §3.3 records only what is new.

**Searches that returned nothing usable, recorded so the absence is visible**: Azure AU-region rendered pricing (dynamic page); Confluent CKU/eCKU rates (undisclosed); Echo360, Evasys, Explorance Blue, ExamSoft, Anthology Milestone institutional pricing (all quote-based); "OnExam" under four query strategies; the CAUDIT procurement portal (HTTP 403); the Anthology Milestone datasheet (PDF binary, not parsed — facts taken from the HTML product and help pages instead).

### Appendix B — Glossary

| Term | Definition |
|------|-----------|
| **AARNet** | Australia's Academic and Research Network; operates the Zoom education arrangement for most Australian universities |
| **AMQP 1.0** | Open messaging protocol; the data-plane standard ADR-006 Condition 3 requires for exit |
| **APP 8** | Australian Privacy Principle 8 — cross-border disclosure of personal information |
| **CAUDIT** | Council of Australasian University Directors of Information Technology; operates sector procurement panels and communities of practice |
| **CKU / eCKU** | Confluent Kafka Unit; eCKU is the elastic autoscaling variant |
| **Client-side schema enforcement** | Microsoft's term for validation performed by the SDK serialiser rather than rejected at the broker |
| **EA** | Microsoft Enterprise Agreement |
| **Gate 1–5** | The `ARC-001-ADR-007-v1.0` sourcing hierarchy: Realise, Extend, Aggregate, Buy, Build |
| **LSP** | Licensing Solution Provider; the reseller through which Microsoft agreements are transacted |
| **LTI 1.3** | 1EdTech Learning Tools Interoperability, version 1.3, with Advantage services |
| **MACC** | Microsoft Azure Consumption Commitment — a contractual commitment to spend, not an entitlement to consume |
| **Messaging Unit (MU)** | The dedicated-capacity unit of Azure Service Bus Premium |
| **My eQuals** | AU/NZ higher-education digital credential platform, used by all public universities |
| **Open Badges 3.0** | 1EdTech digital credential standard aligned to W3C Verifiable Credentials |
| **Principle 19** | *Realise Licensed Capability Before New Spend* — `ARC-000-PRIN-v1.1` §19 |
| **Throughput Unit (TU)** | The capacity unit of Azure Event Hubs Standard |
| **`TBD-WP3`** | Tracked marker for a figure that cannot be stated until the WP3 contract baseline lands (2026-08-21) |

### Appendix C — Requirements Deliberately Not Covered

| Requirement | Reason for exclusion |
|-------------|---------------------|
| REQ-003 (reading lists) | Leganto uncontested as primary; no queued spend. `ARC-001-RSCH-v1.0` §3.7 covers the LTI-version question |
| REQ-005, 006 (discipline tooling) | `ARC-001-FINOPS-v1.0` §7.2 constraint 2 excludes MuseScore, Ableton, iSimulate and Kuracloud from rationalisation. Researching them could not change a decision |
| REQ-007 (single entry point) | An LMS question, reserved to WP8 |
| REQ-015 (portfolio) | PebblePad uncontested; AU residency already vendor-stated in `ARC-001-RSCH-v1.0` §3.1 |
| REQ-016 (similarity / AI detection) | Turnitin uncontested; no queued spend |
| REQ-018 (placement outcomes) | Depends on the Sonia/Lumivero vendor question, which `ARC-001-RSCH-v1.0` §4.3 owns |
| REQ-020, 022 (analytics, export) | Depend on the institutional data platform, outside this scope |
| REQ-026 (course rollover) | BUILD, settled in `ARC-001-RSCH-v1.0` §5.1 |
| REQ-029 (WCAG 2.2 AA) | Partially covered via Echo360's declaration; a full estate accessibility sweep is a separate assessment |
| REQ-031 (SSO / MFA) | A condition of adoption applied throughout rather than a research category |
| REQ-033 (Essential Eight) | Referenced where managed services carry the patching obligation; the posture assessment is a separate artefact |
| REQ-034 (export on termination) | A standing contract requirement in `ARC-001-FINOPS-v1.0` §7.7, not a market question |

### Appendix D — Not-Applicable Template Sections

Recorded so their absence is a decision, not an omission.

| Template section | Status | Reason |
|-----------------|--------|--------|
| UK Government Considerations — TCoP compliance | **N/A** | Australian private-sector institution |
| GOV.UK Common Platforms (Notify, Pay, One Login) | **N/A** | Not available to, and not appropriate for, an Australian university |
| Digital Marketplace / G-Cloud procurement strategy | **N/A** | **Deliberately not searched.** §7 covers the genuine Australian equivalent — institutional policy and sector consortia |
| Digital Outcomes and Specialists | **N/A** | UK framework |
| UK GDPR / DPIA | **N/A** | Privacy Act 1988 (APPs) applies; the PIA is a separate artefact |
| Government cloud and UK data residency | **Replaced** | Australian residency under APP 8 and NFR-C-002, per ADR-005 and ADR-006 |

---

## External References

### Document Register

**Supplied project artefacts (inputs)**

| Doc ID | Artefact | Location |
|--------|----------|----------|
| D1 | `ARC-000-PRIN-v1.1.md` | `projects/000-global/` |
| D2 | `ARC-001-REQ-v1.0.md` | `projects/001-lt-ecosystem/` |
| D3 | `ARC-001-FINOPS-v1.0.md` | `projects/001-lt-ecosystem/` |
| D4 | `ARC-001-RSCH-v1.0.md` | `projects/001-lt-ecosystem/research/` |
| D5 | `ARC-001-ADR-001-v1.0.md` | `projects/001-lt-ecosystem/decisions/` |
| D6 | `ARC-001-ADR-006-v1.0.md` | `projects/001-lt-ecosystem/decisions/` |
| D7 | `ARC-001-ADR-007-v1.0.md` | `projects/001-lt-ecosystem/decisions/` |
| D8 | `system-landscape.md` | `projects/001-lt-ecosystem/external/` |
| D9 | `requirements-register.md` | `projects/001-lt-ecosystem/external/` |

**Cross-project knowledge cited and extended**

| Doc ID | Artefact | Location |
|--------|----------|----------|
| P4-VP1 | `cloudamqp-profile.md` | `projects/004-integration-platform/vendors/` |
| P4-VP2 | `confluent-profile.md` | `projects/004-integration-platform/vendors/` |
| P4-VP3 | `microsoft-azure-integration-services-profile.md` | `projects/004-integration-platform/vendors/` |
| P4-TN1 | `event-broker-comparison.md` | `projects/004-integration-platform/tech-notes/` |
| P4-TN2 | `schema-registry-landscape.md` | `projects/004-integration-platform/tech-notes/` |

**External sources — all fetched or searched 2026-07-29**

| Cite | Source | URL | Rating |
|------|--------|-----|--------|
| MR-C1 | Azure Service Bus pricing (AU) | `https://azure.microsoft.com/en-au/pricing/details/service-bus/` | MEDIUM — tiers and caveat rendered; rates not |
| MR-C2 | Azure Service Bus premium messaging tier | `https://learn.microsoft.com/azure/service-bus-messaging/service-bus-premium-messaging` | HIGH |
| MR-C3 | Reliability in Azure Service Bus | `https://learn.microsoft.com/azure/reliability/reliability-service-bus` | HIGH |
| MR-C4 | Azure Service Bus Geo-Replication (pricing) | `https://learn.microsoft.com/azure/service-bus-messaging/service-bus-geo-replication` | HIGH |
| MR-C5 | Azure Schema Registry in Event Hubs | `https://learn.microsoft.com/azure/event-hubs/schema-registry-overview` | HIGH |
| MR-C6 | Client-side schema enforcement | `https://learn.microsoft.com/azure/event-hubs/schema-registry-client-side-enforcement` | HIGH |
| MR-C7 | Usage metering, billing and pricing for Azure Logic Apps | `https://learn.microsoft.com/azure/logic-apps/logic-apps-pricing` | HIGH |
| MR-C8 | Power Automate licensing FAQ; Power Platform Licensing Guide (Jan/Mar 2026) | `https://learn.microsoft.com/power-platform/admin/power-automate-licensing/faqs` | MEDIUM-HIGH |
| MR-C9 | MACC guidance (samexpert, nops.io, microsoftnegotiations, Microsoft Learn MACC tracking) | `https://learn.microsoft.com/azure/cost-management-billing/benefits/macc/track-consumption-commitment` | MEDIUM |
| MR-C10 | Confluent Cloud pricing and cluster types | `https://docs.confluent.io/cloud/current/clusters/cluster-types.html`; `https://docs.confluent.io/cloud/current/billing/billing-dimensions.html`; `https://www.cloudzero.com/blog/confluent-cloud-pricing/` | MEDIUM |
| MR-C11 | CloudAMQP FAQ and changelog | `https://www.cloudamqp.com/docs/faq.html`; `https://www.cloudamqp.com/changelog.html` | MEDIUM |
| MR-C12 | RabbitMQ 4.3 release highlights; 4.2 release notes | `https://www.rabbitmq.com/blog/2026/04/23/rabbitmq-4.3-release` | MEDIUM-HIGH |
| MR-C13 | CAUDIT Strategic Procurement; Microsoft LSP Panel 2026; CAUDIT Microsoft Initiative; CAUDIT Cloud; AWS engagement | `https://www.caudit.edu.au/procurement/`; `https://www.caudit.edu.au/procurement/portal/panel/microsoft-lsp-panel-2026/`; `https://www.caudit.edu.au/strategic-initiatives/microsoft-initiative/` | MEDIUM — portal returned HTTP 403; facts from search extracts |
| MR-C14 | AARNet Zoom for Research & Education; AARNet–Zoom 10 years; Platinum Partner; AU cloud-recording storage | `https://www.aarnet.edu.au/zoom` | MEDIUM-HIGH |
| MR-C15 | Echo360 EchoVideo product pages; Echo360 pricing aggregators | `https://echo360.com/the-echosystem/echo-video/` | MEDIUM |
| MR-C16 | Southern Illinois University CTE — Echo360 contract expiry 30 June 2026 | `https://cte.siu.edu/instructional-tech/echo360.php` | MEDIUM |
| MR-C17 | TechSmith transition to annual subscription pricing | `https://support.techsmith.com/hc/en-us/articles/27009223314701-TechSmith-Transition-to-Annual-Subscription-Pricing-Model-in-2025` | HIGH |
| MR-C18 | Camtasia for Education store; Camtasia pricing aggregators | `https://www.techsmith.com/store/camtasia/education`; `https://costbench.com/software/screen-recording/camtasia/` | MEDIUM |
| MR-C19 | Camtasia Pro vs Microsoft Clipchamp | `https://support.techsmith.com/hc/en-us/articles/38439498733069-Camtasia-Pro-vs-Microsoft-Clipchamp` | MEDIUM-HIGH |
| MR-C20 | Articulate 360 pricing (vendr, checkthat.ai, eLearning Industry, stratbeans) | `https://www.articulate.com/360/pricing/`; `https://www.vendr.com/marketplace/articulate` | MEDIUM |
| MR-C21 | Miro pricing 2026 (vendr, spendhound, G2, tekpon) | `https://www.g2.com/products/miro/pricing` | MEDIUM |
| MR-C22 | Miro Australia data residency (blog and help centre) | `https://miro.com/blog/australia-data-residency/`; `https://help.miro.com/hc/en-us/articles/23084283851026-Data-residency-at-Miro` | MEDIUM-HIGH |
| MR-C23 | Anthology Milestone product pages and datasheet | `https://www.blackboard.com/products/lifecycle-engagement/career-development/blackboard-milestone`; `https://www.anthology.com/material/anthology-milestone-badging-and-micro-credentials-made-easy` | MEDIUM-HIGH |
| MR-C24 | Anthology Milestone and Blackboard (administrator help); Award Open Badges Automatically 3900.102 | `https://help.anthology.com/blackboard/administrator/en/tools-management/anthology-milestone-and-blackboard.html`; `https://help.blackboard.com/node/48941` | HIGH |
| MR-C25 | Anthology community — *A New Era for Digital Credentials: Open Badges 3.0 is here*, 4 Aug 2025 | `https://community.anthology.com/public/blogs/a-new-era-for-digital-credentials-open-badges-30-is-here-2025-08-04` | HIGH |
| MR-C26 | Canvas Credentials → Parchment Digital Badges: Instructure customer FAQ; UMD DIT notice; Georgia Tech DLT notice | `https://pages.instructure.com/rs/515-XYL-514/images/Customer%20FAQ%20-%20Canvas%20Credentials%20to%20Parchment%20Digital%20Badges%20.pdf`; `https://it.umd.edu/news/umd-digital-badging-service-rebranding` | HIGH |
| MR-C27 | Pearson acquires Credly, 31 Jan 2022 | `https://plc.pearson.com/en-GB/news-and-insights/news/pearson-acquires-digital-credentialing-leader-credly` | HIGH |
| MR-C28 | 1EdTech-certified Open Badges 3.0 issuer lists (secondary) | `https://sertifier.com/blog/digital-badge-platforms/` | LOW-MEDIUM |
| MR-C29 | My eQuals — about, education providers, digital badges news; HES My eQuals | `https://www.myequals.edu.au/about-us`; `https://www.myequals.edu.au/news/15-australia-and-new-zealand-institutions-issuing-digital-badges`; `https://www.hes.edu.au/myequals` | MEDIUM — site redirected to `myequals.org` mid-fetch |
| MR-C30 | Explorance — *Explorance Widens Stronghold on Australian Higher Education Market*; Course Evaluation Software | `https://explorance.com/news/explorance-widens-stronghold-australian-higher-education-market/`; `https://explorance.com/solutions/course-evaluation-software/` | MEDIUM-HIGH |
| MR-C31 | University of St Andrews education blog — *Blue by Explorance*, Sept 2025 | `https://education.wp.st-andrews.ac.uk/2025/09/01/blue-by-explorance/` | MEDIUM |
| MR-C32 | Qualtrics higher-ed pricing commentary; Qualtrics pricing guide 2026 | `https://www.questionpro.com/blog/qualtrics-price-increases-2026-higher-ed-budget`; `https://cleverx.com/blog/qualtrics-pricing-guide-2026/` | **LOW-MEDIUM — QuestionPro is a direct competitor** |
| MR-C33 | DataBee Exams Manager | `https://www.databee.com.au/products/examsmanager/` | MEDIUM |
| MR-C34 | Janison exam management services | `https://www.janison.com/exam-management/` | MEDIUM |
| MR-C35 | University of Melbourne — digital whiteboard and collaboration tool comparison guide; Microsoft Whiteboard vs Miro comparisons | `https://lms.unimelb.edu.au/staff/guides/zoom/digital-whiteboard-and-collaboration-tool-comparison-guide` | MEDIUM |

### Unreferenced Documents

| Artefact | Location | Why not used |
|----------|----------|-------------|
| `ARC-001-ADR-002` to `ADR-005`, `ADR-008` to `ADR-010` | `projects/001-lt-ecosystem/decisions/` | Outside this task's permitted input set. ADR-005's topology and ADR-003's observability plane enter only through the passages ADR-006 quotes |
| `ARC-001-SOBC-v1.0`, `ARC-001-RISK-v1.0`, `ARC-001-STKE-v1.0`, `ARC-001-DATA-v1.0`, `ARC-001-PLAN-v1.0`, `ARC-001-STRAT-v1.0`, `ARC-001-TRAC-v1.0` | `projects/001-lt-ecosystem/` | Outside the permitted input set. SOBC and RISK content enters only through the figures and risk IDs `ARC-001-FINOPS-v1.0` quotes verbatim |
| `consultant-brief.md`, `privacy-context.md`, `stakeholders.md` | `projects/001-lt-ecosystem/external/` | Outside the permitted input set |
| `ARC-004-RSCH-v1.0` | `projects/004-integration-platform/research/` | Not in the permitted input set. Project 004's findings enter through its vendor profiles and tech notes, which are cited as `[P4-*]` |

---

**Generated by**: ArcKit `/arckit:research` command
**Generated on**: 2026-07-29
**ArcKit Version**: 6.7.5
**Project**: 001-lt-ecosystem — Learning & Teaching Baseline Strategy (The University of Funk)
**Model**: Claude Opus 5
**Generation Context**: Second research instance for project 001, deliberately scoped away from `ARC-001-RSCH-v1.0` (target-organisation research, 987 lines, unmodified by this run) and from project 004's existing broker vendor profiles and tech notes, which are cited and extended rather than restated. External market research conducted 2026-07-29 via 24 web searches and fetches plus 3 Microsoft Learn MCP documentation queries, against real, named, commercially available products. **No fact about the University of Funk was sourced externally, and no UoF-specific cost figure appears anywhere in this document** — the `TBD-WP3` convention established by `ARC-001-FINOPS-v1.0` is applied without exception, pending the 2026-08-21 contract baseline. Australian regulatory framing throughout: Privacy Act 1988 (APPs) including APP 8, ASD Essential Eight, WCAG 2.2 AA. Currency AUD, with US-published list prices quoted as published and converted at a stated assumed rate. UK Government frameworks — G-Cloud, Digital Marketplace, DOS, TCoP, GDS Service Standard, UK GDPR — were deliberately not applied and not searched; §7 covers the Australian sector-procurement equivalent (CAUDIT, AARNet, My eQuals) instead.

<!-- arckit-provenance:start -->

## Build Provenance

*Stamped automatically by the ArcKit plugin's `provenance-stamp.mjs` PostToolUse hook. Complements (does not replace) the human-authored footer above. Carries only fields the model can't authoritatively self-report: build context from `.arckit/state.json` and effort levels derived from command frontmatter + the silent-downgrade matrix.*

| Field | Value |
|-------|-------|
| Requested Effort | `max` |
| Effective Effort | _unknown — model not parsed from existing footer_ |
| Stamped at | 2026-07-29T23:45:50.519Z |

<!-- arckit-provenance:end -->
