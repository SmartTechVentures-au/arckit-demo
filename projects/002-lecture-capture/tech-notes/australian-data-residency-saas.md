# Tech Note: Australian Data Residency for SaaS Platforms

> **Template Origin**: Official | **ArcKit Version**: 6.7.2 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-TECH-australian-data-residency-saas-v1.0 |
| **Document Type** | Technology Note |
| **Project** | Originated in Lecture Capture Platform Consolidation (Project 002) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-27 |
| **Last Updated** | 2026-07-27 |
| **Review Date** | 2027-07-27 |
| **Owner** | Eleanor Frame, Privacy & Records Officer |
| **Confidence** | **MEDIUM-HIGH** — Microsoft position sourced from official documentation; other vendor positions sourced from vendor or reseller announcements |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Governance, Digital & IT, Procurement, Privacy |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-27 | ArcKit AI | Initial creation from `/arckit:research` | PENDING | PENDING |

---

## Summary

Australian data residency is now widely available across major SaaS platforms, which means it has largely stopped being a *differentiator* and become a *hygiene check*. The useful questions have moved on. They are now: **is the residency commitment contractual or merely configurational; does it cover processing as well as storage; and does it survive the vendor adding AI enrichment features?** Under the Privacy Act 1988, APP 8 accountability for cross-border disclosure remains with the disclosing organisation regardless of where data physically sits — so a residency claim on a marketing page is not a compliance position. This note captures the mechanisms observed in the 2026 market and the specific traps found.

## Key Findings

### Residency is now common — so verify the *mechanism*, not the claim

Three distinct mechanisms were observed, and they carry very different assurance:

| Mechanism | Assurance | Example observed |
|---|---|---|
| **Contractual commitment** | Strongest — the vendor is bound, and the position cannot silently change | Microsoft 365 Product Terms data residency, Multi-Geo and Advanced Data Residency [AU-C1] |
| **Regional infrastructure announcement** | Medium — a real capability, but the contractual binding needs separate confirmation | Panopto AU cloud [AU-C3]; Kaltura Asia-Pacific (Sydney) [AU-C4] |
| **Customer-configurable setting** | Weakest on its own — depends on the setting being made *and kept* | Zoom admin-selected storage region [AU-C5] |

> **A configurational residency position is only as good as the configuration change control around it.** If an administrator can flip the region, so can a future administrator who does not know why it was set.

### Microsoft's model is the most explicitly documented (and a useful benchmark)

- Australia is a Microsoft 365 **Local Region Geography**, with data centre locations in **Sydney and Melbourne** [AU-C1] [AU-C2].
- Exchange Online, SharePoint/OneDrive, Microsoft Teams and Copilot all carry **P-M-A** for Australia — Product Terms data residency, Multi-Geo, and Advanced Data Residency [AU-C1].
- Microsoft documents three "Durable Commitments on Data Location": Product Terms, Multi-Geo subscription, and the Advanced Data Residency add-on [AU-C1].
- Critically, Microsoft also documents the **default position where no durable commitment exists**: "the *Tenant's* in scope customer data is not committed to reside in any particular data center ... and that data storage location is subject to change without notice" [AU-C1].
- Also documented: a *Tenant's* Default Geography is set at creation and **cannot be changed** [AU-C1]. Residency options are therefore constrained by a decision made once, possibly years earlier, possibly by someone who has left.
- Note the scope boundary: not all services are covered. Only Core Services and a defined set of Expanded Services fall under ADR; several Microsoft services are explicitly outside it [AU-C1].

> **Benchmark to apply to other vendors**: ask them the same questions Microsoft answers publicly. *Which specific services are covered? Is the commitment contractual? What happens by default if we do nothing?*

### The processing-location trap

The single most useful finding in this note.

AARNet's guidance on Zoom is explicit that setting the Australian region "ensures that both the storage of recordings **and any post-meeting processing such as transcriptions or AI-generated summaries** all happen in Australia" [AU-C5] — the clear implication being that without the setting, processing may occur elsewhere even where storage is in-country.

This matters more every year, because every platform is adding AI enrichment. Kaltura's Sydney regional infrastructure announcement is framed specifically around making its **agentic AI capabilities** available from in-region infrastructure [AU-C4] — which is an implicit acknowledgement that AI processing had previously been a residency exception.

> **Requirement-writing implication**: a data residency requirement that says "data shall be stored in Australia" does not cover transcription, summarisation, translation, face detection, or any other enrichment. Specify **storage, processing and sub-processors** separately, or the AI features will quietly become the APP 8 exposure.

### Absence of a published statement is itself a finding

Two of six platforms researched in Project 002 had **no published Australian residency position at all**:

- One vendor's government/secure-solutions page carried extensive US federal-sector approvals but **no data residency, hosting region, cloud provider, SOC 2, ISO 27001, FedRAMP or IRAP statement** [AU-C6].
- Another vendor's own trust page referenced "multiple physical data center zones" and "industry-leading cloud infrastructure" but **named no region, no cloud provider, and stated no data residency guarantee** [AU-C7].

Neither absence proves the capability is missing. Both mean the position **must be obtained in writing before any privacy assessment can conclude**.

### Certification landscape in Australia

- **IRAP** (Information Security Registered Assessors Program) is the Australian Cyber Security Centre's framework for assessing systems against Australian Government security standards. It is common in Commonwealth procurement and much less common among education-focused SaaS vendors — none of the specialist video platforms researched published an IRAP assessment.
- **ISO 27001** is widely expected in Australian public-sector procurement. Its absence from a vendor's certification list, where SOC 2 Type II is present [AU-C7], is worth noting but is not disqualifying — SOC 2 Type II is a substantive control attestation.
- **HECVAT** (Higher Education Community Vendor Assessment Toolkit) appears among education vendors [AU-C7] and is a useful shortcut: a completed HECVAT usually answers many residency and security questions in one document. **Ask for the HECVAT early** — it is cheaper than a bespoke questionnaire for both sides.

### Recommended information request

For any SaaS platform holding personal information, obtain in writing before contract:

1. The specific region(s) where each data class is **stored at rest** — including derived assets such as transcripts, captions, thumbnails and analytics.
2. The specific region(s) where each data class is **processed**, including all AI/ML enrichment.
3. Whether the position is **contractual or configurational**, and if contractual, which contract document binds it.
4. What happens **by default** if no election is made.
5. Every **sub-processor** with access, and its jurisdiction.
6. **Notification obligations** if the vendor changes hosting location.
7. Completed **HECVAT** (or equivalent) and any **ISO 27001 / SOC 2 Type II / IRAP** attestations.

Maintain the answers as a standing **cross-border disclosure register per data class**, reassessed at each contract renewal — not reconstructed from scratch at each audit.

## Relevance to Projects

- **002-lecture-capture** — directly underpins NFR-C-001 (Privacy Act 1988 compliance and AU residency), DR-006 (residency and cross-border disclosure register), DR-001, risk R-013 (PIA incomplete at signature; APP 8 unresolved), and the recommendation in the research findings that DR-006 be extended to cover processing jurisdiction as well as storage.
- **001-lt-ecosystem** — applies to REQ-030 across the whole L&T estate, and to the privacy context's finding that APP 8 triggers on several data classes under assumed hosting.
- **000-global** — evidence base for Principle 8 (Data Residency and Cross-Border Accountability), specifically its implications that hosting region is a required attribute captured at procurement and that residency posture is reassessed at renewal.
- **Any future SaaS procurement** holding personal information. The mechanism taxonomy, the processing-location trap and the standing information request are all vendor-agnostic and reusable.

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| RSCH | ARC-002-RSCH-v1.0.md | ArcKit artifact | `002-lecture-capture/research/` | Parent research findings document |
| REQ | ARC-002-REQ-v1.0.md | ArcKit artifact | `002-lecture-capture/` | NFR-C-001, DR-006, DR-001 |
| PRIN | ARC-000-PRIN-v1.0.md | ArcKit artifact | `000-global/` | Principle 8 — Data Residency and Cross-Border Accountability |
| PC | privacy-context.md | Compliance input | `002-lecture-capture/external/` | PI inventory and APP 8 trigger analysis |

### Citations

| Citation ID | Source | URL | Fetch status | Claim supported |
|-------------|--------|-----|--------------|-----------------|
| AU-C1 | Microsoft Learn — Microsoft 365 data residency: Overview and Definitions | https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview | Fetched (doc updated 2026-05-06) | Australia a Local Region Geography; Table 3 shows P-M-A for Exchange, SharePoint/OneDrive, Teams, Copilot; three Durable Commitments (Product Terms, Multi-Geo, ADR); default position "not committed to reside in any particular data center ... subject to change without notice"; Default Geography set at tenant creation and cannot be changed; ADR service scope defined |
| AU-C2 | Microsoft Learn — same page, Table 4 | https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview | Fetched | Australia data centre locations: Melbourne, Sydney |
| AU-C3 | Panopto — Expands Global Video Cloud, Launches New Data Center in Australia | https://www.panopto.com/company/news/panopto-expands-global-video-cloud-launches-new-data-center-in-australia/ | Search result | Sydney data centre for ANZ customers, November 2020; AU Cloud in AWS Asia-Pacific (Sydney) Region; content stored locally; encrypted at rest and in transit |
| AU-C4 | IT Business Net — Kaltura Expands AI-Powered Agentic Experiences to Europe, Asia-Pacific, and Canada | https://itbusinessnet.com/2026/04/kaltura-expands-ai-powered-agentic-experiences-to-europe-asia-pacific-and-canada-with-dedicated-regional-infrastructure-for-enterprise-data-residency-and-performance/ | Search result | Asia-Pacific (Sydney) among three new regions; dedicated regional infrastructure for data residency; AI capabilities (Agentic Avatars, AI Genie, Content Lab, REACH AI) available from regional infrastructure storing data within each geography |
| AU-C5 | AARNet — Zoom introduces Live Transcription, and Cloud Recording storage in Australia for education | https://www.aarnet.edu.au/zoom-introduces-live-transcription-and-cloud-recording-storage-in-australia-for-education | Fetched | Australian cloud recording storage activated for AARNet customers 1 February 2021; admin sets Data & Storage region to Australia; ensures storage **and post-meeting processing such as transcriptions or AI-generated summaries** occur in Australia |
| AU-C6 | Echo360 — Government Secure Solutions | https://echo360.com/government/secure-solutions/ | Fetched | No data residency, hosting region, cloud provider, SOC 2, ISO 27001, FedRAMP or IRAP statement; US federal-sector approvals only |
| AU-C7 | YuJa — Security and Trust | https://www.yuja.com/trust-center/security/ | Fetched | "multiple physical data center zones"; no region or cloud provider named; no data residency guarantee; AES-256 at rest; TLS 1.2 minimum / 1.3 default; SOC 2 Type II, GDPR, HECVAT, TX-RAMP, CSA Cyber Essentials; no ISO 27001 |
| AU-C8 | AARNet — Zoom Video Communications for Research & Education | https://www.aarnet.edu.au/zoom | Search result | AARNet is "a leading Zoom APAC Reseller for education in Australia"; hosts Zoom servers on its network; provides local support and cloud recording integration with CloudStor |

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
