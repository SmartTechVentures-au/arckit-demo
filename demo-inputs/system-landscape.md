# L&T Technology Ecosystem — System Categorisation & Status

**The University of Funk** | Foundation artifact | DRAFT | *fictional demonstration document*

Current tools mapped to the eight-category capability taxonomy, with usage status.
This is the WP2 baseline: the SA validates and updates it, then produces the current
landscape diagram.

## Status key

| Status | Meaning |
|--------|---------|
| ✅ In use | Supported and currently in use |
| 🔑 Licensing | Supported but requires further licensing |
| 🔍 Investigating | Not currently in use — investigating for 2027 |

## Categorisation map

| Category | Core | Discipline-specific |
|----------|------|---------------------|
| **Course Design** | Blackboard ✅ · Articulate 360 🔑 · H5P ✅ | Kuracloud ✅⁴ |
| **Learning Resources** | Blackboard ✅ · Leganto ✅ · LinkedIn Learning ✅ · Camtasia ✅ · Adobe Creative Suite 🔑 · Articulate 360 🔑 | MuseScore ✅⁵ · Ableton Live 🔑⁵ · iSimulate ✅ · Kuracloud ✅⁴ |
| **Learning Delivery** | Blackboard ✅ · Echo360 ✅ · MS Teams ✅¹ · Zoom ✅ · Leganto ✅ | Kuracloud ✅⁴ |
| **Learning Capture** | Echo360 ✅ · MS Teams ✅¹ · Zoom ✅ | — |
| **Active Learning** | H5P ✅ · PebblePad ✅ · Padlet ✅ · Miro 🔍 · Articulate 360 🔑 · Zoom (polling) ✅ | iSimulate ✅ · Kuracloud ✅⁴ |
| **Collaboration** | Blackboard ✅ · MS Teams ✅¹ · Zoom ✅ · Padlet ✅ · Turnitin (PeerMark) ✅ · Miro 🔍 | — |
| **Assessment & Progress Tracking** | Blackboard ✅ · Turnitin ✅ · ExamSoft ✅ · PebblePad ✅ · H5P ✅ · Remark ✅ · (Badging software) 🔍² · OnExam 🔍⁶ | iSimulate ✅ |
| **Evaluation & Analytics** | Blackboard ✅ · Qualtrics ✅ · Evasys ✅ · Echo360 ✅ | — |

## Notes

1. **MS Teams** — investigation planned for 2027 to establish a seamless platform
   experience across collaboration, learning delivery and lecture capture (overlaps
   with Zoom and Echo360 — key rationalisation candidate).
2. **Badging software** — options investigation required, including Badgr, Credly and
   Milestone.
3. **Articulate 360** — investigation required to understand the licensing model for
   enterprise usage of the platform.
4. **Kuracloud** — investigation required to understand if and to what extent an
   internal support model exists for this solution.
5. **MuseScore / Ableton Live** — School of Music & Performing Arts discipline tools;
   investigation required to determine the extent and nature of current use and
   licensing across the school.
6. **OnExam** — investigation required to determine extent and nature of use at UoF.

## Known integrations (WP4/WP5 focus)

| # | Integration | Method (current) | Known issues |
|---|------------|------------------|--------------|
| 1 | PeopleSoft → Blackboard (user & course lifecycle, institutional roles) | Nightly batch flat-file | Fragile; role assignment failures; no intra-day sync |
| 2 | Echo360 user provisioning | LTI + manual CSV | Manual workaround for casual academic staff |
| 3 | Course cloning automation | Semi-manual scripts | Undocumented; single-person dependency |
| 4 | Institutional hierarchy updates | Manual | Drift between PeopleSoft and Blackboard hierarchies |
| 5 | Allocate+ → Blackboard group creation | Batch export/import | Timetable changes not reflected until next run |
| 6 | Sonia ↔ Blackboard grades (placements) | Manual re-keying | Error-prone; audit concerns |
| 7 | Sandpit provisioning | — (planned 2027) | Not yet designed |
