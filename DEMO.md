# ArcKit Demonstration — Spoke & Rim Bicycle Retail Chain

> **FICTIONAL DEMONSTRATION.** This workspace demonstrates the
> [ArcKit.org](https://arckit.org) enterprise architecture governance harness
> across a five-project digital transformation portfolio for a fictional
> Australian bicycle shop chain trading with both wholesale and retail
> customers. All company details, people, and figures are invented.

## The scenario in 30 seconds

**Cycle Motion Group, trading as Spoke & Rim**: 12 retail stores (WA/VIC/NSW),
~250 wholesale trade accounts, 6 web properties, ~160 staff, ~A$48M revenue —
grown by acquisition, running a fragmented systems estate. Full scenario:
`projects/000-global/external/demo-scenario-brief.md`.

## The portfolio

| Project | Domain | Central decision |
|---|---|---|
| **001** Inventory & Warehouse Uplift *(base project)* | Inventory truth | Where does the single source of inventory truth live? |
| **002** CRM & Customer 360 | Customer truth | Single CRM across B2B + B2C, or dual-stack? |
| **003** ERP Modernisation | Financial truth | How is ARC-001-ADR-001 (MYOB retained) *governed into supersession*? |
| **004** Retail POS Consolidation | Store operations | One POS for 3 acquired estates, hub-first, before a contract deadline |
| **005** E-Commerce Consolidation | Digital channels | 6 web properties → ≤ 4, SaaS, hub-sourced availability |

The portfolio spine — hub = inventory truth, CRM = customer truth, ERP =
financial truth, everything hub-first — is governed in
`projects/000-global/ARC-000-PORT-v1.0.md`.

## What this demonstrates about ArcKit

1. **The artefact chain per project** (GDS phases): `/arckit:stakeholders` →
   STKE, `/arckit:requirements` → REQ, `/arckit:research` → RSCH,
   `/arckit:adr` → ADR — every document ID'd (`ARC-{proj}-{TYPE}-v{ver}`),
   version-controlled, with document control blocks and revision history.
2. **Traceability**: drivers (SD-n) → goals (G-n) → outcomes (O-n) →
   requirements (BR/FR/NFR/INT/DAT) → decisions, with cross-project
   references (e.g. Project 004's NFR-I-001 enforcing ARC-000-PORT §2).
3. **Governed decision supersession**: ARC-003-ADR-001 shows how an earlier
   correct decision (ARC-001-ADR-001, retain MYOB) is superseded with dated,
   traceable mechanics rather than drift.
4. **Australian overlay scoping** (`arckit-au`): each REQ contains an
   applicability table — Privacy Act PIA, OAIC NDB, Essential Eight, Spam
   Act, PCI DSS, RBA surcharging, STP Phase 2, Peppol, ACL, WCAG scoped
   **in**; PSPF / ISM / DISP / SOCI-CIRMP consciously scoped **out** — the
   overlays are decided, not ignored.
5. **Cross-project tension management**: joint checkpoints (002↔003 on the
   Microsoft stack; 004↔005 on Shopify POS) recorded as research risks and
   ADR conditions.

## Suggested demo walkthrough (10 minutes)

1. `demo-scenario-brief.md` — the business and its fragmentation (1 min)
2. `ARC-000-PORT-v1.0.md` — the spine diagram, sequencing, PR-5 gate (2 min)
3. Project 002 STKE → REQ → ADR — the drivers-to-decision chain (3 min)
4. Project 003 ADR — governed supersession of ADR-001 (2 min)
5. Project 004 REQ §7 — AU overlay applicability table (1 min)
6. Any project's Document Control block — provenance stamping (1 min)

## Next commands to run live in a demo

- `/arckit:evaluate` on 002 or 004 — generate the vendor scoring framework
  (Project 001 already has one at `ARC-001-EVAL-v1.0.md` as the exemplar)
- `/arckit:risk` — project risk registers rolled up to the portfolio
- `/arckit-au:pia` on 002 — the Privacy Impact Assessment gate
- `/arckit:traceability` — verify the SD → G → BR → ADR chains end-to-end
