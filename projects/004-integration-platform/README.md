# Integration Platform

Project ID: 004
Created: 2026-07-29

## Overview

Integration platform selection and implementation for The University of Funk,
executing ADR-001 Condition 1 (Principle 19 test) to select the lightweight
event broker for the canonical data model.

This project resolves the open condition from `001-lt-ecosystem` ADR-001: before
the university procures an integration broker, Principle 19 requires demonstrating
that existing licensed capability — including the Microsoft agreement, PeopleSoft
Integration Broker, and Blackboard Ultra's webhook/event capabilities — cannot
serve the purpose. If they can, Option B is delivered using that capability rather
than a new purchase.

Inherits architecture principles from `000-global`
(`ARC-000-PRIN-v1.1.md`) and the RIFF review flow in `000-global/policies/`.

Engagement inputs are seeded in `external/` from `demo-inputs/`.

> Part of The University of Funk demonstration scenario — fictional. See `DEMO.md`.

## Cross-project traceability

| Source | Artefact | Relevance |
|--------|----------|-----------|
| `000-global` | `ARC-000-PRIN-v1.1.md` | Governing principles — especially P10, P11, P17, P19 |
| `001-lt-ecosystem` | `ARC-001-ADR-001-v1.0.md` | Integration Mediation Approach — Condition 1 (Principle 19 test) drives this project |
| `001-lt-ecosystem` | `ARC-001-DATA-v1.0.md` | Canonical data model — the broker must host this as a schema registry |
| `003-lms-ultra-migration` | `ARC-003-REQ-v1.0.md` | DR-001 (canonical model implementation), INT-001 to INT-007 (integrations the broker must mediate) |
| `003-lms-ultra-migration` | `ARC-003-DATA-v1.0.md` | Integration runtime entities (E-I01 to E-I04) — schema registry, event broker, endpoints |
| `003-lms-ultra-migration` | `ARC-003-RISK-v1.0.md` | R-005 (team overwhelmed), R-012 (premium API gating), R-020 (PeopleSoft event capability) |

## Workflow

Use ArcKit commands to generate project artifacts in the recommended order:

### Discovery Phase
1. `/arckit:stakeholders` - Analyze stakeholder drivers and goals
2. `/arckit:requirements` - Define broker selection requirements
3. `/arckit:risk` - Create risk register

### Alpha Phase
4. `/arckit:research` - Research integration platform options (open-source brokers, iPaaS, existing licensed capability)
5. `/arckit:evaluate` - Create vendor/platform evaluation framework
6. `/arckit:adr` - Document the Principle 19 test outcome and broker selection decision
7. `/arckit:wardley` - Map integration capability evolution

### Beta Phase
8. `/arckit:hld-review` - Review integration platform design
9. `/arckit:traceability` - Generate requirements traceability matrix

### Compliance (as needed)
- `/arckit:au-pia` - Privacy Impact Assessment for the integration layer
- `/arckit:au-e8-posture` - Essential Eight assessment for the broker

## Project Structure

Documents use standardized naming: `ARC-{PROJECT_ID}-{TYPE}-v{VERSION}.md`

```
004-integration-platform/
├── README.md (this file)
│
├── # Core Documents
├── ARC-004-STKE-v1.0.md     # Stakeholder drivers (/arckit:stakeholders)
├── ARC-004-REQ-v1.0.md      # Requirements (/arckit:requirements)
├── ARC-004-RISK-v1.0.md     # Risk register (/arckit:risk)
├── ARC-004-RSCH-v1.0.md     # Research findings (/arckit:research)
├── ARC-004-EVAL-v1.0.md     # Evaluation criteria (/arckit:evaluate)
├── ARC-004-TRAC-v1.0.md     # Traceability matrix (/arckit:traceability)
│
├── # Multi-instance Documents (subdirectories)
├── decisions/
│   └── ARC-004-ADR-001-v1.0.md  # Principle 19 test and broker selection
├── diagrams/
│   └── ARC-004-DIAG-001-v1.0.md # Integration platform architecture
├── research/
│   └── ARC-004-RSCH-v1.0.md     # Technology research
│
└── external/                     # External documents (seeded from demo-inputs/)
```

## Document Type Codes

| Code | Document Type |
|------|---------------|
| REQ | Requirements |
| STKE | Stakeholder Analysis |
| RISK | Risk Register |
| RSCH | Research Findings |
| EVAL | Evaluation Criteria |
| ADR | Architecture Decision Record |
| HLD | High-Level Design Review |
| TRAC | Traceability Matrix |
| DIAG | Architecture Diagram |
| WARD | Wardley Map |

## Status

Track your progress through the workflow:

**Discovery Phase:**
- [ ] Stakeholder analysis complete
- [ ] Requirements defined
- [ ] Risk register created

**Alpha Phase:**
- [ ] Technology research complete (Principle 19 test)
- [ ] Evaluation criteria defined
- [ ] Broker selection decision documented (ADR)

**Beta Phase:**
- [ ] HLD reviewed and approved
- [ ] Traceability matrix validated

**Live Phase:**
- [ ] Broker deployed and operational
- [ ] First integration (INT-001) live on broker
