# ArcKit Demonstration Project — The University of Funk

**Learning & Teaching Technology Ecosystem — Baseline Strategy**

> A worked demonstration of [ArcKit](https://arckit.org) governing a real-shaped solution
> architecture engagement for an Australian university, built on the
> [arckit-template](https://github.com/SmartTechVentures-au/arckit-template) dev container.

---

## ⚠️ Fictional scenario

**The University of Funk (UoF) does not exist.** It is a fictional Australian university
invented for this public demonstration. All people named in this repository are fictional
characters. Any resemblance to real institutions, individuals, or governance bodies is
coincidental. Commercial product names (Blackboard, PeopleSoft, Echo360, Turnitin, etc.)
are used illustratively to make the architecture realistic — no statement is made about
any vendor.

---

## 1. The scenario

The University of Funk — a mid-sized Australian university with a nationally renowned
School of Music & Performing Arts and a large Health Sciences faculty — has commissioned
a **Learning & Teaching Baseline Strategy**. Over roughly a decade, its digital learning
ecosystem has grown organically to 20+ tools with overlapping capability, fragile
point-to-point integrations, and licensed functionality nobody switched on.

A Solution Architect (that's you, live on stage) has been engaged to:

- baseline the current landscape against an eight-category capability taxonomy,
- define architecture principles and an integration architecture,
- map academic survey requirements to system capability,
- and deliver a rationalisation roadmap by **31 August 2026**, feeding a September
  business case.

Requirements have already been gathered via an academic survey — the SA **applies** them
architecturally rather than collecting them. That makes this a perfect ArcKit scenario:
the inputs exist, and the job is to turn them into governed, traceable artifacts.

## 2. Repository layout

```
.
├── DEMO.md                              ← you are here
├── demo-inputs/                         ← engagement inputs (pre-ArcKit)
│   ├── consultant-brief.md              ← the engagement brief (WP1–WP9)
│   ├── capability-taxonomy.md           ← 8-category L&T capability model
│   ├── system-landscape.md              ← current tools mapped to taxonomy + status
│   ├── solution-governance-process.md   ← the RIFF review & approval flow
│   ├── requirements-register.md         ← consolidated academic survey requirements
│   ├── stakeholders.md                  ← engagement stakeholder list (fictional)
│   └── privacy-context.md               ← PI inventory, data flows, E8 self-assessment
└── projects/                            ← created live during the talk
    ├── 000-global/                      ← org-wide: principles, risks, data model
    └── 001-lt-ecosystem/                ← the baseline strategy engagement
```

Everything under `demo-inputs/` plays the role of "artifacts the client hands you on
day one". Everything under `projects/` is generated live by ArcKit during the talk —
the **global space first**, then the engagement project inheriting from it. This is the
same "1 global + N projects" shape shown in the deck's client examples.

## 3. Engagement structure → ArcKit mapping

The brief defines nine work packages. Each maps cleanly to ArcKit commands and GDS
phases:

| WP | Work Package | GDS Phase | ArcKit command(s) |
|----|--------------|-----------|-------------------|
| WP1 | Architecture Principles | Planning | `/arckit:principles` |
| WP2 | Current Landscape Update | Discovery | `/arckit:diagram` (current state) |
| WP3 | System Capability Mapping | Discovery | `/arckit:analyze`, `/arckit:research` |
| WP4 | Integration Landscape Assessment | Discovery | `/arckit:diagram`, `/arckit:risk` |
| WP5 | Integration Architecture | Alpha | `/arckit:hld-review`, `/arckit:adr` |
| WP6 | Architecture Decisions Register | Running | `/arckit:adr` (e.g. Echo360 vs MS Stream) |
| WP7 | Requirements Mapping | Alpha | `/arckit:requirements` + traceability |
| WP8 | High-Level Future State | Beta | `/arckit:diagram`, `/arckit:hld-review` |
| WP9 | Recommendations & Roadmap | Beta → Live | `/arckit:sobc`, roadmap, `/arckit:analyze` |

### The Australian compliance thread (`arckit-au` overlay)

The AU thread runs through the whole demo, fed by `demo-inputs/privacy-context.md`:

| arckit-au command | Demo material | Story beat |
|---|---|---|
| **Privacy Impact Assessment** (Privacy Act 1988, 13 APPs) | PI inventory incl. **sensitive information** in Sonia placement records; APP 8 triggers on the offshore-hosted SaaS (assumed regions) | The nightly flat-file and manual re-keying flows aren't just fragile — they're privacy findings |
| **Essential Eight maturity posture** (ML0–ML3) | Fictional self-assessment: mostly ML1, target ML2; MFA exception breaching REQ-031 | Governance artifacts and security posture trace to the same requirements register |
| **NDB Response Playbook** (stretch) | Tabletop: mis-keyed Sonia grade export with clearance metadata | Eligible-data-breach assessment + 30-day clock, live |

The punchline for the talk: the *same* integration weaknesses surface in WP4 (fragility),
the risk register (delivery risk), the PIA (APP findings) and the roadmap (uplift
priority) — and ArcKit's traceability matrix shows all four links.

## 4. Suggested live demo run sheet

Approximate timing for a 25–30 minute live segment:

1. **Orient** — `/arckit:start` (show the harness, decision tree, connected tools).
2. **Global space** —
   `/arckit:init 000-global This is the organisation-wide governance space for The University of Funk, an Australian university rationalising its Learning & Teaching technology ecosystem. Inputs are in demo-inputs/.`
3. **Principles at the top (WP1)** — `/arckit:principles` in `000-global` — LMS role
   and boundaries, integration approach, platform governance, student experience
   consistency. **Talking point:** principles are set once, org-wide — every project
   initialised after this inherits them. This mirrors the "1 global + 4 procurements"
   pattern in the deck's client example.
4. **Engagement project** —
   `/arckit:init 001-lt-ecosystem The Learning & Teaching Baseline Strategy engagement — WP1–WP9 per demo-inputs/consultant-brief.md.`
   Show the console line confirming principles inherited from `000-global` — that
   *is* the multi-project story, in one line of output.
5. **Stakeholders** — `/arckit:stakeholders` in `001` — point it at
   `demo-inputs/stakeholders.md` and let it produce the power/interest analysis.
6. **Requirements (WP7)** — `/arckit:requirements` against
   `demo-inputs/requirements-register.md`.
7. **Risk** — `/arckit:risk` — integration fragility, licence waste, shadow IT.
   Org-level risks (privacy posture, vendor concentration) can sit in `000-global`;
   engagement risks in `001` — mention, don't demo.
8. **Decision** — `/arckit:adr` — *"Echo360 vs Microsoft Stream for lecture capture"*
   (a genuinely contestable decision; good live drama).
9. **AU thread, part 1 — PIA** — run the `arckit-au` Privacy Impact Assessment against
   `demo-inputs/privacy-context.md`: 13 APPs, sensitive information in the Sonia
   placement flow, APP 8 on the (assumed) offshore SaaS hosting.
10. **AU thread, part 2 — Essential Eight** — run the maturity posture command against
    the fictional ML self-assessment; highlight the MFA local-account exception tracing
    back to REQ-031.
11. **The money shot** — `/arckit:build 001 --plan` then `/arckit:build 001` to show
    the GDS harness dispatching subagent waves and committing atomically.
12. **Close** — the traceability matrix: survey requirement → capability → system →
    decision → risk → **APP finding** → roadmap item. One weakness, four governed
    artifacts, all linked — and the whole chain hangs off principles set once in
    `000-global`.
13. **Stretch (time permitting)** — the NDB playbook tabletop from
    `privacy-context.md` §4.

**Delivery is fully live** — the inputs are the only pre-work. If a run stalls,
ArcKit's documented recovery applies: *"Continue from where you stopped. Do not stop
until complete."*, then `/arckit:health` to spot anything skipped.

## 5. What was fictionalised

| Original concept | Demo version |
|---|---|
| Real client university | **The University of Funk** (fictional) |
| Internal solution review gate | **RIFF Review** (Review of Innovation, Fit & Function) |
| All personnel | Fictional characters (see `demo-inputs/stakeholders.md`) |
| Faith-specific discipline tooling | Music/performing-arts tooling (MuseScore, Ableton Live) |
| Governance bodies | Education Committee / Operations Committee / University Executive |

## 6. Prerequisites

- This repo built from **arckit-template** (dev container with Claude Code + ArcKit
  core + `arckit-au` overlay pre-installed).
- `ANTHROPIC_API_KEY` exported on the host before launching the container.
- ArcKit ≥ v5.x, Claude Code ≥ v2.1.172.

---

*Prepared for the Perth AI community talk, 30 July 2026 — Smart Tech Ventures.*