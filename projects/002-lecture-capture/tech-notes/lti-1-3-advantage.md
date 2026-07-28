# Tech Note: LTI 1.3 and LTI Advantage for LMS Tool Integration

> **Template Origin**: Official | **ArcKit Version**: 6.7.2 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-TECH-lti-1-3-advantage-v1.0 |
| **Document Type** | Technology Note |
| **Project** | Originated in Lecture Capture Platform Consolidation (Project 002) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-27 |
| **Last Updated** | 2026-07-27 |
| **Review Date** | 2027-07-27 |
| **Owner** | Sam Okafor, Integration Architect |
| **Confidence** | **MEDIUM-HIGH** — standard behaviour and certification model well sourced; individual vendor implementation depth verified only for the products researched |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Digital & IT, Learning Innovation, Procurement |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-27 | ArcKit AI | Initial creation from `/arckit:research` | PENDING | PENDING |

---

## Summary

**Learning Tools Interoperability (LTI)** is the 1EdTech standard for integrating third-party tools with a Learning Management System. LTI 1.3 replaces the older LTI 1.1 with a modern security profile, and **LTI Advantage** adds three services on top of LTI 1.3 Core: Deep Linking, Names and Role Provisioning Service (NRPS), and Assignment and Grade Service (AGS). The critical procurement insight is that **"supports LTI 1.3" is not a single capability** — it is a spectrum running from a bare launch to full Advantage certification, and vendors sit at very different points on it, sometimes differently for different LMS platforms. A second insight matters just as much: **LTI is a launch and context standard, not an identity lifecycle standard.** Treating LTI as the provisioning mechanism is a common architectural error that leaves manual account workarounds in place.

## Key Findings

### The certification ladder — ask which rung, not whether

- 1EdTech's Product Directory is the authoritative listing of products that have passed interoperability testing [LTI-C1].
- **"LTI Advantage Complete"** is awarded only where a platform or tool certifies **LTI 1.3 Core plus all three Advantage services** [LTI-C1]. It is a materially stronger claim than "LTI 1.3 supported".
- The three Advantage services:
  - **Deep Linking** — the tool returns content selections that are placed into the LMS course
  - **Names and Role Provisioning Service (NRPS)** — the tool can query the LMS for the course roster and roles
  - **Assignment and Grade Service (AGS)** — the tool writes grades back to the LMS gradebook
- Observed spread among video platforms researched in 2026: Panopto holds **LTI Advantage Complete** [LTI-C2]; Echo360 is **LTI Advantage certified** with Deep Linking, NRPS and AGS documented [LTI-C3]; Kaltura is listed among certified organisations [LTI-C1]; one vendor (YuJa) could not be found in the searched directory results and claims conformance only in its own marketing copy [LTI-C7].

> **Procurement action**: verify certification in the 1EdTech Product Directory directly. A vendor statement that products "conform to the latest LTI standards" is not the same as a certification record.

### Certification does not guarantee depth on *your* LMS

The most important practical finding: **a vendor can hold a general LTI Advantage certification while its integration with one specific LMS is shallower than with others.**

- Echo360's Blackboard Integration Overview states verbatim: *"NOTE that while migrating to LTI 1.3 may appear to be an option within Blackboard, it has not been fully tested by us. We are only supporting migrating to LTI 1.1."* [LTI-C4]
- Echo360's LTI documentation separately notes that **"LTI 1.3 does not currently support linking to EchoVideo Course sections themselves"**, and that there is **no automatic migration path from LTI 1.1 links to LTI 1.3** [LTI-C3].
- By contrast, Panopto documents LTI 1.3 for Blackboard Ultra, Canvas, D2L and Moodle, supporting both Ultra and Original course views [LTI-C5].

> **Design implication**: object-granularity matters. If the tool needs to bind to a course *section* (as scheduled lecture capture does), and the LTI 1.3 implementation only binds at course level, the standard is technically present and functionally insufficient.

### LTI is not a provisioning standard — this is the common architectural error

- NRPS lets a tool *read* a roster within a course context. It does not create, update or deprovision institutional accounts, and it does not propagate role changes proactively.
- Event-driven identity lifecycle requires a separate mechanism — **SCIM** (System for Cross-domain Identity Management) or a documented equivalent provisioning API. SCIM is the documented provisioning pattern for Microsoft Entra ID [LTI-C8].
- The failure mode is well attested in practice: an institution integrates a tool over LTI, discovers roster context is only available at launch time and only for users who launch, and falls back to a bulk CSV load to pre-populate accounts — reintroducing manual provisioning through the back door.

> **Requirement-writing implication**: specify LTI 1.3 **and** a provisioning mechanism as separate requirements. Conflating them produces a platform that launches correctly and provisions manually.

### The market has been forced onto LTI by LMS vendors

- Blackboard announced it would no longer support Building Block (B2) based integrations from **June 2024**, transitioning to a framework based on LTI and REST APIs [LTI-C5].
- Microsoft retired its classic Teams Classes and Teams Meetings LTI app on **15 September 2025**, replaced by the Microsoft 365 LTI app registered as an LTI 1.3/Advantage tool [LTI-C6a] [LTI-C6b].
- Consequence: any integration still running on LTI 1.1 or a proprietary plugin model is on borrowed time, and migration effort is a real cost line in any platform decision.

### Practical integration preconditions people forget

- **Identity matching.** The Microsoft 365 LTI app requires the LMS user's Email or Institutional Email field to be populated with the Entra UPN or primary email address **for every course using the integration** [LTI-C6a]. Equivalent identity-matching preconditions exist for most tools and are frequently discovered late.
- **Migration is rarely automatic.** Echo360 documents no automatic path from LTI 1.1 links to LTI 1.3 [LTI-C3]; Microsoft documents no automatic migration for several classic app content types [LTI-C6b]. Existing course content links generally have to be recreated.
- **Secrets are shown once.** LTI 1.3 registration typically surfaces a client secret exactly once — Echo360's documentation warns: "The Secret on this page appears only once. If you close this page without copying the secret to a safe and secure location, it cannot be recovered." [LTI-C9]. Trivial, and a recurring cause of failed go-lives.

### Recommended evaluation approach

Do not score LTI support from documentation. Test it, on your own LMS instance:

1. **LTI 1.3 launch** with correct role mapping for every institutional role the design needs (coordinator, tutor, marker, student).
2. **Binding at the right granularity** — course *and* section, if the use case needs section.
3. **Deep Linking** placing content into a real course.
4. **NRPS** returning the full roster, not only users who have launched.
5. **AGS** writing back, if grades are in scope.
6. **Provisioning separately** — an event in the authoritative source producing access within the target SLA, with **no file transfer of any kind**.
7. **Migration path** from whatever is in place today, including what happens to existing content links.

## Relevance to Projects

- **002-lecture-capture** — directly underpins NFR-I-001 (LTI 1.3 as a CRITICAL integration standard), INT-003 (capture platform ↔ Blackboard Ultra), FR-016 (access derived from enrolment), TC-2, TC-5 and risk R-022 (platform supports only bulk-import provisioning). The Echo360 Blackboard caveat [LTI-C4] is a project-specific finding of material consequence.
- **001-lt-ecosystem** — applies to REQ-025 (automated provisioning, no manual CSV), REQ-028 and the WP5 integration architecture. The LTI-is-not-provisioning finding should inform the canonical model and event design.
- **Any future project** integrating a tool with Blackboard Ultra or any LMS. The certification-ladder and provisioning-separation findings are vendor-agnostic and durable.
- **Architecture principles** — reinforces Principle 10 (Interface-Mediated Integration), Principle 11 (Event-Driven and Near-Real-Time by Default) and Principle 12 (Automated Identity Lifecycle). LTI satisfies Principle 10 for launch; it does **not** satisfy Principle 12.

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RSCH | ARC-002-RSCH-v1.0.md | ArcKit artifact | `002-lecture-capture/research/` | Parent research findings document |
| REQ | ARC-002-REQ-v1.0.md | ArcKit artifact | `002-lecture-capture/` | NFR-I-001, INT-003, FR-016, TC-2, TC-5 |
| PRIN | ARC-000-PRIN-v1.0.md | ArcKit artifact | `000-global/` | Principles 10, 11, 12 |

### Citations

| Citation ID | Source | URL | Fetch status | Claim supported |
|-------------|--------|-----|--------------|-----------------|
| LTI-C1 | 1EdTech — LTI Advantage certification and Product Directory | https://www.imsglobal.org/ltiadvantage | Search result | "LTI Advantage Complete" awarded for LTI 1.3 Core plus all three Advantage services; Product Directory is the official listing of products passing interoperability testing; Kaltura among certified organisations |
| LTI-C2 | Panopto — Achieves LTI Advantage Complete Certification from 1EdTech | https://www.panopto.com/company/news/panopto-achieves-lti-advantage-certification-1edtech/ | Search result | Panopto holds LTI Advantage Complete certification |
| LTI-C3 | Echo360 Support — LTI Advantage and LTI 1.3 Support | https://support.echo360.com/hc/en-us/articles/11074490900621-EchoVideo-LTI-Advantage-and-LTI-1-3-Support | Fetched | LTI Advantage certified via 1EdTech; Deep Linking, Names and Role Provisioning Services, Assignments and Grades Services; Moodle, Canvas, Brightspace, Blackboard; "LTI 1.3 does not currently support linking to EchoVideo Course sections themselves"; no automatic LTI 1.1 → 1.3 migration |
| LTI-C4 | Echo360 Support — Blackboard Integration Overview | https://support.echo360.com/hc/en-us/articles/11074515169421-EchoVideo-Blackboard-Integration-Overview | Fetched | Verbatim: "NOTE that while migrating to LTI 1.3 may appear to be an option within Blackboard, it has not been fully tested by us. We are only supporting migrating to LTI 1.1." Also LTI 1.1, LTI 1.3 and REST API modes; REST API automates course linking/scheduling, roster sync, consolidated analytics |
| LTI-C5 | Panopto — Blackboard integration and LTI 1.3 release information | https://www.panopto.com/integrations/blackboard/ | Search result | LTI 1.3 for Blackboard Ultra, Canvas, D2L, Moodle; Ultra and Original course views; inherits Blackboard course roles and permissions; Blackboard ended Building Block (B2) support from June 2024 |
| LTI-C6a | Microsoft Learn — Deploy the Microsoft 365 LTI app in Blackboard by Anthology | https://learn.microsoft.com/en-us/microsoft-365/lti/microsoft-365-lti-blackboard | Fetched | Registered via Blackboard "Register LTI 1.3/Advantage Tool" with published Client ID; requires Blackboard Email/Institutional Email populated with Entra UPN or primary email for every course using the integration |
| LTI-C6b | Microsoft Learn — same page, migration guidance | https://learn.microsoft.com/en-us/microsoft-365/lti/microsoft-365-lti-blackboard | Fetched | "The classic Teams Classes and Teams Meetings app has sunset as of September 15, 2025"; no automatic migration for several classic app content types; new Meetings app shows ±6 months of meetings |
| LTI-C7 | YuJa — Security and Trust | https://www.yuja.com/trust-center/security/ | Fetched | "All our products conform to the latest Learning Tool Interoperability (LTI) and Single Sign On (SSO) standards" — vendor claim without certification reference |
| LTI-C8 | Microsoft Learn — SCIM provisioning for apps from Microsoft Entra ID | https://learn.microsoft.com/en-us/entra/identity/app-provisioning/use-scim-to-provision-users-and-groups | Search result | SCIM as the documented provisioning pattern for Entra ID |
| LTI-C9 | Echo360 Support — Creating an LTI 1.3 Integration with Blackboard | https://support.echo360.com/hc/en-us/articles/13786298949901-EchoVideo-Creating-an-LTI-1-3-Integration-with-Blackboard | Fetched | LTI 1.3 Deep Linking setup; Analytics and Deep Linking content tool placements; "The Secret on this page appears only once ... it cannot be recovered" |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| — | — | — |

---

**Generated by**: ArcKit `/arckit:research` agent
**Generated on**: 2026-07-27
**ArcKit Version**: 6.7.2
**Project**: Lecture Capture Platform Consolidation (Project 002)
**Model**: Claude Opus 5 (1M context)
