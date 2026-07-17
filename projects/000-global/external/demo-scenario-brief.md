# Demonstration Scenario Brief — "Spoke & Rim" Bicycle Retail Chain

> **FICTIONAL DEMONSTRATION SCENARIO.** This brief extends the Cycle Motion base
> workspace into a fictional Australian bicycle shop chain for the purpose of
> demonstrating the ArcKit.org governance harness across a multi-project digital
> portfolio. Company details, people, store counts, and financials below are
> invented for the demonstration and do not describe any real organisation.

## Date Created: 06/07/2026

| | |
|---|---|
| **Entity (fictional)** | Cycle Motion Group Pty Ltd, trading as **Spoke & Rim** |
| **Sector** | Bicycle retail (B2C) and wholesale distribution (B2B) |
| **HQ** | Perth, Western Australia |
| **Footprint** | 12 retail stores — 6 Perth metro, 2 regional WA, 2 Melbourne, 2 Sydney |
| **Wholesale** | ~250 independent bike shop trade accounts nationally |
| **Online** | 1× Magento B2B trade portal, 5× Shopify B2C brand storefronts |
| **Staff** | ~160 (retail-heavy), incl. 5-person Order & Supply Chain team |
| **Revenue (FY26, fictional)** | ~A$48M — 60% wholesale, 25% retail stores, 15% online |
| **Loyalty members** | ~38,000 ("Spoke & Rim Riders Club", currently spreadsheet-managed) |

## S1. Scenario narrative

Cycle Motion began as a Perth-based manufacturer and distributor of performance
cycling components (see `company-brief.md`). In this demonstration scenario, the
business has since acquired and rebranded a chain of bicycle retail stores under
the **Spoke & Rim** banner, creating a genuine dual-channel operation:

- **Wholesale (B2B)** — distribution of performance component brands (iGPSport,
  CYCPLUS, Farsports, Lewis, Wheeltop, XCADEY, ezMTB) to ~250 independent
  Australian bike shops via the Magento trade portal.
- **Retail (B2C)** — 12 Spoke & Rim stores selling complete bikes, components,
  apparel, and workshop servicing, plus 5 Shopify brand storefronts online.

Growth by acquisition has left a fragmented systems estate. **Project 001**
(inventory & warehouse uplift) is underway and has already fixed the single
source of inventory truth question. Four further programmes now form the
digital transformation portfolio — each run as a governed ArcKit project:

| Project | Domain | Problem in one line |
|---|---|---|
| **002** | CRM & Customer 360 | No CRM: trade accounts in spreadsheets, 38k loyalty members in another spreadsheet, marketing via a disconnected Mailchimp list |
| **003** | ERP Modernisation | MYOB AccountRight is the ceiling — multi-entity, multi-state, payroll (STP Phase 2), landed costs, and Peppol e-invoicing all strain it |
| **004** | Retail POS Consolidation | 12 stores run 3 different POS systems inherited from acquisitions; no unified stock visibility, loyalty, or reporting |
| **005** | E-Commerce Consolidation | 6 web properties (1 Magento + 5 Shopify) with duplicated catalogues, inconsistent pricing, and no B2B/B2C synergy |

## S2. Current systems landscape (scenario state)

| System | Role | Status |
|---|---|---|
| MYOB AccountRight | Accounting system of record (ADR-001, Project 001) | Retained; strained |
| Inventory/Order hub | Single source of inventory truth (Project 001 outcome) | Implementation underway |
| Magento (Adobe Commerce) | B2B trade portal | Working; ageing self-managed stack |
| Shopify ×5 | B2C brand storefronts | Fragmented catalogues |
| POS — Retail Express | 7 stores (legacy estate) | Contract renewal Jun 2027 |
| POS — Square Retail | 3 stores (from acquisition A) | Month-to-month |
| POS — Standalone cash register + EFTPOS | 2 stores (from acquisition B) | No integration at all |
| Mailchimp + spreadsheets | Marketing, trade accounts, loyalty | High-risk, no consent management |

## S3. Fictional people (demonstration cast)

| Person | Role | Portfolio involvement |
|---|---|---|
| Fred Flintstone | CEO | Executive sponsor, investment authority |
| Wilma Flintstone | COO | Operational sponsor across all projects |
| Betty Rubble | GM Retail (Spoke & Rim) | Sponsor: 004 POS; key stakeholder: 002, 005 |
| Barney Rubble | Head of Wholesale | Key stakeholder: 002 CRM, 005 E-Commerce |
| Jane Jetson | Finance Manager | Sponsor: 003 ERP |
| George Jetson | Digital & E-Commerce Lead | Sponsor: 005; key stakeholder: 002, 004 |
| Order & Supply Chain team (5) | Operations | End users across portfolio |
| 12 store managers | Retail operations | End users: 004, 002 |
| Velma Dinkley | Solution architecture advisor | ArcKit-governed advisory across portfolio |

## S4. Regulatory context (Australian, private-sector retail)

The `arckit-au` overlay is installed in this workspace. For a private retailer
the relevant overlays and obligations demonstrated across the portfolio are:

- **Privacy Act 1988 (Cth) / APPs** — customer and loyalty data (002, 004, 005);
  OAIC Notifiable Data Breaches scheme readiness.
- **Spam Act 2003 (Cth)** — marketing consent management (002, 005).
- **PCI DSS v4.x** — cardholder data across POS and e-commerce (004, 005).
- **RBA surcharging & least-cost routing (eftpos)** — payments (004).
- **Australian Consumer Law** — pricing, receipts, refunds, warranties (004, 005).
- **ATO STP Phase 2, GST/BAS, Peppol e-invoicing** — ERP (003).
- **ASD Essential Eight** — baseline cyber posture across all projects.

Government-only overlays (PSPF, DISP, SOCI/CIRMP, ISM classification) are noted
as **not applicable** in each project's requirements, demonstrating how ArcKit
overlays are consciously scoped in or out rather than silently ignored.
