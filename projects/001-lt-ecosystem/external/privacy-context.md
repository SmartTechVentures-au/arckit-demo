# Privacy & Security Context — L&T Ecosystem

**The University of Funk** | Input to arckit-au compliance thread | *fictional demonstration document*

Feeds the `arckit-au` overlay commands: **Privacy Impact Assessment** (Privacy Act 1988,
13 APPs, APP 8 cross-border disclosure, Tranche 1 reforms), **Essential Eight maturity
posture** (ML0–ML3), and the **OAIC Notifiable Data Breach playbook**.

> ⚠️ **Demo assumptions.** UoF is fictional. Hosting regions, contract terms and
> maturity levels below are invented scenario assumptions for demonstration purposes
> and make no claim about any real vendor's actual hosting, security or practices.

## 1. Personal information inventory

| # | Information class | Sensitivity | Systems holding it | Hosting region *(assumed)* |
|---|-------------------|-------------|--------------------|----------------------------|
| 1 | Student identity (name, DOB, student ID, contact) | PI | PeopleSoft, Blackboard, Echo360, PebblePad, ExamSoft, Sonia, Allocate+ | AU |
| 2 | Academic records & grades | PI | PeopleSoft, Blackboard, Sonia, ExamSoft | AU |
| 3 | Submitted written/creative work | PI (student IP) | Turnitin, Blackboard, PebblePad | US/EU |
| 4 | Video/audio recordings capturing students | PI (biometric-adjacent) | Echo360, Zoom, MS Teams | AU / US |
| 5 | Placement records (incl. clearance metadata, health-context notes) | **Sensitive information** | Sonia | AU |
| 6 | Exam responses & remote proctoring artifacts | PI | ExamSoft | US |
| 7 | Survey & teaching evaluation responses | PI (de-identified in reporting) | Qualtrics, Evasys | US / EU |
| 8 | Engagement & learning analytics | PI (derived) | Blackboard, Echo360, institutional data platform | AU |

**APP 8 triggers:** classes 3, 4 (partial), 6 and 7 involve offshore disclosure under
the assumed hosting — the PIA must assess cross-border disclosure accountability,
contract clauses and the practicability of AU-region alternatives.

## 2. Data flows of PIA interest

| Flow | Personal information | Current mechanism | Privacy concern |
|------|----------------------|-------------------|-----------------|
| PeopleSoft → Blackboard | Identity, enrolment, roles | Nightly batch flat-file | Flat-files at rest on shared storage; stale de-provisioning (access persists up to 24h after withdrawal) |
| Sonia ↔ Blackboard grades | Grades + sensitive placement context | Manual re-keying | Human error; screenshots/exports circulating via email |
| Echo360 provisioning | Identity | LTI + manual CSV | CSV extracts of the student cohort handled manually |
| Analytics export | Derived engagement data | Ad-hoc extracts | No defined retention or minimisation rules |

## 3. Essential Eight — current self-assessment *(fictional)*

Target set by Digital & IT: **ML2** across the SaaS-heavy L&T estate by end 2027.

| Mitigation strategy | Current | Target | Notes |
|---------------------|---------|--------|-------|
| Application control | ML0 | ML1 | Not enforced on shared teaching-lab fleets |
| Patch applications | ML1 | ML2 | SaaS-managed for most tools; lab software lags |
| Configure MS Office macro settings | ML2 | ML2 | Enforced via Intune |
| User application hardening | ML1 | ML2 | Browser hardening partial |
| Restrict administrative privileges | ML1 | ML2 | Legacy shared admin accounts in AV/capture estate |
| Patch operating systems | ML1 | ML2 | Lecture-theatre capture appliances behind |
| Multi-factor authentication | ML2 | ML2 | SSO+MFA enforced; **exception:** two tools still allow local accounts (breaches REQ-031) |
| Regular backups | ML1 | ML2 | SaaS export coverage unverified for 4 tools (links to REQ-034) |

## 4. NDB readiness notes (stretch scenario)

Tabletop scenario for the OAIC playbook command: *a mis-keyed Sonia export emails a
placement grade sheet — including sensitive clearance metadata — to an external
supervisor distribution list.* Assess eligible-data-breach criteria, the 30-day
investigation clock, and the notification workflow across UoF, the placement providers
and affected students.
