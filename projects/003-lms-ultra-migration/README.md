# LMS Ultra Migration

Project ID: 003
Created: 2026-07-29

## Overview

Blackboard Ultra migration and integration modernisation for The University of
Funk, executing the integration architecture defined in `001-lt-ecosystem`
ADR-001 (Integration Mediation Approach).

This project governs the migration from Blackboard Learn Original to Blackboard
Ultra, including the re-engineering of the PeopleSoft → Blackboard integration
(user lifecycle, course lifecycle, institutional role assignment), course cloning
automation, and the broader integration platform uplift.

Inherits architecture principles from `000-global`
(`ARC-000-PRIN-v1.1.md`) and the RIFF review flow in `000-global/policies/`.

Engagement inputs are seeded in `external/` from `demo-inputs/`.

> Part of The University of Funk demonstration scenario — fictional. See `DEMO.md`.

## Cross-project traceability

| Source | Artefact | Relevance |
|--------|----------|-----------|
| `000-global` | `ARC-000-PRIN-v1.1.md` | Governing principles (LMS role & boundaries, integration approach) |
| `001-lt-ecosystem` | `ARC-001-ADR-001` | Integration Mediation Approach — this project executes that decision |
| `001-lt-ecosystem` | `ARC-001-ADR-002` | Authoritative Source for Institutional Role Assignment |
| `001-lt-ecosystem` | `ARC-001-RISK-v1.0.md` | Integration fragility risks inherited by this project |
| `001-lt-ecosystem` | `ARC-001-DATA-v1.0.md` | Data model and PI flows for student/course entities |

## Workflow

Use ArcKit commands to generate project artifacts in the recommended order:

### Discovery Phase
1. `/arckit:stakeholders` - Analyze stakeholder drivers and goals
2. `/arckit:risk` - Create risk register
3. `/arckit:sobc` - Create Strategic Outline Business Case

### Alpha Phase
4. `/arckit:requirements` - Define comprehensive requirements
5. `/arckit:data-model` - Design data model and GDPR compliance
6. `/arckit:wardley` - Create Wardley maps for strategic planning
7. `/arckit:research` - Research technology options (if needed)
8. `/arckit:adr` - Document architecture decisions

### Beta Phase
9. `/arckit:hld-review` - Review High-Level Design
10. `/arckit:dld-review` - Review Detailed Design
11. `/arckit:traceability` - Generate requirements traceability matrix

### Compliance (as needed)
- `/arckit:au-pia` - Privacy Impact Assessment (Privacy Act 1988)
- `/arckit:au-e8-posture` - Essential Eight maturity posture
- `/arckit:au-dss` - DTA Digital Service Standard assessment

## Project Structure

Documents use standardized naming: `ARC-{PROJECT_ID}-{TYPE}-v{VERSION}.md`

```
003-lms-ultra-migration/
├── README.md (this file)
│
├── # Core Documents
├── ARC-003-STKE-v1.0.md     # Stakeholder drivers (/arckit:stakeholders)
├── ARC-003-RISK-v1.0.md     # Risk register (/arckit:risk)
├── ARC-003-SOBC-v1.0.md     # Business case (/arckit:sobc)
├── ARC-003-REQ-v1.0.md      # Requirements (/arckit:requirements)
├── ARC-003-DATA-v1.0.md     # Data model (/arckit:data-model)
├── ARC-003-RSCH-v1.0.md     # Research findings (/arckit:research)
├── ARC-003-TRAC-v1.0.md     # Traceability matrix (/arckit:traceability)
│
├── # Multi-instance Documents (subdirectories)
├── decisions/
│   └── ARC-003-ADR-001-v1.0.md  # Architecture decisions (/arckit:adr)
├── diagrams/
│   └── ARC-003-DIAG-001-v1.0.md # Diagrams (/arckit:diagram)
├── wardley-maps/
│   └── ARC-003-WARD-001-v1.0.md # Wardley maps (/arckit:wardley)
├── reviews/
│   ├── ARC-003-HLD-v1.0.md      # HLD review (/arckit:hld-review)
│   └── ARC-003-DLD-v1.0.md      # DLD review (/arckit:dld-review)
│
└── external/                     # External documents (seeded from demo-inputs/)
```

## Document Type Codes

| Code | Document Type |
|------|---------------|
| REQ | Requirements |
| STKE | Stakeholder Analysis |
| RISK | Risk Register |
| SOBC | Strategic Outline Business Case |
| DATA | Data Model |
| ADR | Architecture Decision Record |
| RSCH | Research Findings |
| HLD | High-Level Design Review |
| DLD | Detailed-Level Design Review |
| TRAC | Traceability Matrix |
| DIAG | Architecture Diagram |
| WARD | Wardley Map |

## Status

Track your progress through the workflow:

**Discovery Phase:**
- [ ] Stakeholder analysis complete
- [ ] Risk register created
- [ ] Business case approved

**Alpha Phase:**
- [ ] Requirements defined
- [ ] Data model designed
- [ ] Architecture decisions documented

**Beta Phase:**
- [ ] HLD reviewed and approved
- [ ] DLD reviewed and approved
- [ ] Traceability matrix validated

**Live Phase:**
- [ ] Implementation complete
- [ ] Production deployment
