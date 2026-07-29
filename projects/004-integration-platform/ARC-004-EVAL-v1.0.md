# Platform Evaluation Framework: Integration Platform Selection (Principle 19 Test)

> **Template Origin**: Official | **ArcKit Version**: 6.7.4 | **Command**: `/arckit:evaluate`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-004-EVAL-v1.0 |
| **Document Type** | Platform Evaluation Framework |
| **Project** | 004-integration-platform — Integration Platform Selection & Implementation |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-29 |
| **Last Modified** | 2026-07-29 |
| **Review Cycle** | On demand (decision-gating artefact) |
| **Next Review Date** | 2026-08-12 |
| **Owner** | Sam Okafor, Integration Architect |
| **Reviewed By** | PENDING — Cassandra Rhodes, Chief Information Officer |
| **Approved By** | PENDING — Prof. Otis Hammond, Deputy Vice-Chancellor (Education) |
| **Distribution** | Steering Committee; Project Team; Digital & IT; Procurement |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-29 | ArcKit AI | Initial creation from `/arckit:evaluate` command — scored platform evaluation for integration broker selection | PENDING | PENDING |

---

## 1. Document Purpose

This document formalises the scored evaluation of six candidate integration broker platforms for the University of Farnsworth (UoF) Integration Platform Selection project (Project 004). It translates the qualitative capability analysis in ARC-004-RSCH-v1.0 into a weighted, quantitative scoring framework that enables defensible platform selection.

The evaluation follows Principle 19 (Existing Licensed First) — candidates are assessed in order of licensing status: existing licensed platforms first, then new purchases and open-source alternatives. Platforms that fail mandatory qualification gates are scored but marked as non-qualifying.

**Upstream dependencies**: ARC-004-RSCH-v1.0 (Technology Research), ARC-003-REQ-v1.0 (Requirements), ARC-000-PRIN-v1.1 (Architecture Principles), ADR-001 (Integration Mediation Approach).

**Downstream consumers**: ADR-002 (Platform Selection Decision), ARC-004-PLAN (Implementation Plan), Steering Committee approval gate.

---

## 2. Evaluation Overview

### 2.1 Purpose

Select an integration broker platform with schema registry capability that satisfies ADR-001 requirements, complies with Principle 19 evaluation order, and can be operationally sustained by a 3-4 person integration team within the university's existing or justifiable budget envelope.

### 2.2 Evaluation Principles

| Principle | Application |
|-----------|-------------|
| **Principle 19 — Existing Licensed First** | Existing licensed platforms are evaluated before new purchases. A new purchase is only justified if existing capability is demonstrably insufficient. |
| **Principle 8 — Australian Hosting** | Platform must be deployable in Australian data centre regions (REQ-030). |
| **Principle 9 — Avoid Lock-in** | Preference for open protocols (AMQP, CloudEvents) and portable architectures. |
| **Principle 17 — Observability** | Single-plane monitoring is a scored criterion, not optional. |

### 2.3 Evaluation Team

| Role | Name | Responsibility |
|------|------|----------------|
| Lead Evaluator | Sam Okafor, Integration Architect | Technical scoring, evidence gathering |
| Commercial Reviewer | Maria Ostinato, Chief Financial Officer | TCO validation, Principle 19 commercial assessment |
| Governance Reviewer | Cassandra Rhodes, Chief Information Officer | Compliance with architecture principles |
| Executive Sponsor | Prof. Otis Hammond, Deputy Vice-Chancellor (Education) | Final approval |

### 2.4 Conflict of Interest Declaration

No member of the evaluation team holds a financial interest in, or advisory relationship with, any of the platform vendors evaluated. The university's existing Microsoft enterprise agreement is a pre-existing institutional contract, not a conflict of interest. This declaration will be reviewed by the Steering Committee as part of the approval gate.

---

## 3. Mandatory Qualifications (Pass/Fail Gates)

Before scoring, each candidate must pass three mandatory qualification gates. A failure on any gate disqualifies the candidate from recommendation, though scoring is completed for the record.

| Gate | Requirement | Source | Pass Condition |
|------|-------------|--------|----------------|
| **MQ-1** | Schema registry capability | DR-001, ADR-001, SD-9 | Platform must provide or natively integrate a schema registry capable of validating event payloads against JSON Schema, Avro, or equivalent. Application-level-only validation (no registry) does not pass. |
| **MQ-2** | Australian region hosting | P8, REQ-030 | Platform must be deployable in an Australian data centre region, either cloud-hosted or on-premises within Australia. |
| **MQ-3** | Event-driven publish/subscribe | INT-001 to INT-007, P10, P11 | Platform must support publish/subscribe messaging with topic-based or exchange-based routing to multiple consumers. Point-to-point-only or single-system-only routing does not pass. |

### Mandatory Qualification Results

| Candidate | Licensing Status | MQ-1 Schema Registry | MQ-2 AU Hosting | MQ-3 Pub/Sub | Qualified |
|-----------|-----------------|----------------------|-----------------|--------------|-----------|
| Azure Integration Services | EXISTING LICENSED | **PASS** — Event Hubs Schema Registry (Avro, JSON Schema) | **PASS** — Australia East, Australia Southeast | **PASS** — Service Bus Topics, subscriptions, AMQP 1.0 | **YES** |
| PeopleSoft Integration Broker | EXISTING LICENSED | **FAIL** — XML schema only; no JSON Schema/Avro registry; PeopleSoft-centric | **PASS** — on-premises, university-hosted | **FAIL** — PeopleSoft-centric routing; cannot route to non-PeopleSoft systems natively | **NO** |
| Blackboard Ultra Webhooks | EXISTING LICENSED | **FAIL** — no schema registry; not a broker | **PASS** — Ultra hosting region (to be confirmed) | **FAIL** — outbound webhooks only; no topic routing or subscription management | **NO** |
| Confluent Cloud (Kafka) | NEW PURCHASE | **PASS** — Confluent Schema Registry (Avro, JSON Schema, Protobuf); server-side validation | **PASS** — AWS ap-southeast-2 Sydney; Azure Australia East | **PASS** — Kafka topics, consumer groups, exactly-once semantics | **YES** |
| Apache Kafka Self-hosted + Apicurio | OPEN SOURCE | **PASS** — Apicurio Registry (Avro, JSON Schema); requires separate deployment | **PASS** — self-hosted on Azure Australia East VMs | **PASS** — Kafka native topics and consumer groups | **YES** |
| RabbitMQ + Apicurio Sidecar | OPEN SOURCE | **PASS (marginal)** — Apicurio sidecar; not natively integrated; bolted-on architecture | **PASS** — self-hosted on Azure Australia East; or CloudAMQP Sydney | **PASS** — exchanges and queues; different model from topic-based but workable | **YES** |

**Disqualified candidates**: PeopleSoft Integration Broker (fails MQ-1, MQ-3) and Blackboard Ultra Webhooks (fails MQ-1, MQ-3) are disqualified from recommendation. Full scoring is recorded below for audit completeness.

---

## 4. Scoring Methodology

### 4.1 Rating Scale

| Score | Label | Definition |
|-------|-------|------------|
| 5 | Exceeds requirement | Fully meets the criterion and provides additional capability beyond what was specified |
| 4 | Meets requirement | Fully satisfies the criterion as stated |
| 3 | Partially meets | Satisfies the criterion with minor gaps or workarounds required |
| 2 | Significant gaps | Substantial workarounds or supplementary tooling required |
| 1 | Does not meet | Fails the criterion; no viable path to compliance without replacement |
| 0 | Not applicable | Criterion cannot be assessed or is structurally irrelevant to this candidate |

### 4.2 Weighting

Ten evaluation criteria, weighted to total 100%. Weights reflect the relative importance established by the architecture requirements and principles documented in ARC-004-RSCH-v1.0.

### 4.3 Weighted Score Calculation

**Weighted Score = Raw Score x Weight x 20**

This produces a 0-100 scale where a candidate scoring 5/5 on every criterion achieves 100.

**Example**: A score of 4/5 on a criterion weighted at 15% = 4 x 0.15 x 20 = 12.0

---

## 5. Evaluation Criteria Detail

### C1: Schema Registry with Runtime Validation (Weight: 20%)

**Source**: DR-001, ADR-001, SD-9

The platform must provide a schema registry that stores, versions, and enforces event schemas at runtime. Schemas must support JSON Schema and/or Avro. Runtime validation means the broker (or a tightly coupled registry component) rejects non-conforming payloads before delivery to consumers. Client-side-only validation (where the SDK validates but the broker accepts anything) scores lower than server-side enforcement.

### C2: Publish/Subscribe with Topic-based Routing (Weight: 15%)

**Source**: INT-001 to INT-007, P10, P11

The platform must support publish/subscribe messaging where producers publish to named topics (or exchanges) and multiple consumers subscribe independently. Routing must support filtering by topic hierarchy or message attributes. The platform must handle the seven integration flows documented in INT-001 through INT-007 across PeopleSoft, Blackboard Ultra, Echo360, Sonia, and Allocate+.

### C3: Dead-letter, Retry, and Replay Handling (Weight: 10%)

**Source**: ADR-001 Option B

Failed messages must be routed to a dead-letter queue (DLQ) rather than being silently dropped. The platform must support configurable retry policies (exponential backoff, max retries) and ideally support event replay from a retained log for recovery scenarios.

### C4: Single-plane Observability (Weight: 10%)

**Source**: P17, NFR-M-001

All integration flows must be observable from a single monitoring interface — message throughput, error rates, latency, DLQ depth, consumer lag. The platform must integrate with or provide dashboards, alerting, and distributed tracing without requiring multiple disconnected monitoring tools.

### C5: Australian Region Hosting (Weight: 10%)

**Source**: P8, REQ-030

The platform must run in an Australian data centre region. For cloud services, this means an Australian availability zone (e.g., Australia East, ap-southeast-2). For self-hosted platforms, this means deployment on infrastructure physically located in Australia. Data sovereignty requires that event payloads containing student PII do not leave Australian jurisdiction.

### C6: Operational Complexity for 3-4 Person Team (Weight: 10%)

**Source**: SD-1, G-5

The integration team is 3-4 people. The platform must be operationally sustainable by this team size without requiring dedicated platform engineering or 24/7 on-call. Managed services score higher than self-hosted. Platforms requiring specialist expertise (e.g., Kafka broker tuning, ZooKeeper management) score lower unless fully managed.

### C7: Cost — Principle 19 Weighting (Weight: 10%)

**Source**: P19, SD-2, SD-4

Three-year total cost of ownership in AUD, including licensing, infrastructure, and operational labour. Platforms covered by existing agreements score highest. New purchases must demonstrate clear capability justification over existing options to score above 2/5. This criterion explicitly operationalises Principle 19's cost dimension.

### C8: Vendor Lock-in Risk (Weight: 5%)

**Source**: P9, SD-8

Degree to which the platform uses open protocols and standards (AMQP 1.0, CloudEvents, Kafka protocol) versus proprietary APIs and management planes. Portability of message formats, schema definitions, and operational configuration. Fully open-source platforms score highest; proprietary platforms with open wire protocols score mid-range.

### C9: Security — OAuth 2.0, Encryption, Audit (Weight: 5%)

**Source**: P16, NFR-SEC-002

The platform must support OAuth 2.0 or equivalent modern authentication, TLS encryption in transit, encryption at rest, role-based access control (RBAC), and audit logging of administrative and message-level operations. Integration with the university's identity provider (Azure AD) is preferred.

### C10: Community and Support Ecosystem (Weight: 5%)

**Source**: SD-10, G-5

Availability of documentation, community forums, Stack Overflow presence, third-party tooling, training resources, and vendor or community support channels. A 3-4 person team relies heavily on external knowledge; platforms with thin community support increase operational risk.

---

## 6. Platform Assessments

### 6.1 Microsoft Azure Integration Services (EXISTING LICENSED)

**Components**: Azure Service Bus (Premium), Azure Event Hubs with Schema Registry, Azure Monitor, Azure API Management (optional).

**Licensing status**: Existing Microsoft enterprise agreement. Service Bus Premium and Event Hubs are consumption-based services within the existing agreement.

**Mandatory qualification**: **PASSED** (MQ-1, MQ-2, MQ-3 all pass)

| Criterion | Weight | Raw Score | Justification | Weighted Score |
|-----------|--------|-----------|---------------|----------------|
| C1: Schema registry | 20% | 3 | Event Hubs Schema Registry supports Avro and JSON Schema with versioning and compatibility modes. However, validation is client-side via SDK — the broker does not reject non-conforming payloads at the server. This is a meaningful gap versus Confluent's server-side enforcement, but the registry itself is fully capable and tightly integrated. | 12.0 |
| C2: Pub/sub routing | 15% | 5 | Service Bus Premium provides topics, subscriptions, correlation filters, SQL filters, and sessions. AMQP 1.0 wire protocol. Supports all seven INT flows natively. | 15.0 |
| C3: DLQ/retry/replay | 10% | 5 | Built-in DLQ per subscription. Configurable retry with exponential backoff. Message deferral and scheduled delivery. Event Hubs provides event replay via consumer group offsets and retention. | 10.0 |
| C4: Observability | 10% | 5 | Azure Monitor provides unified dashboards, alerts, distributed tracing via Application Insights, and Log Analytics. Single pane of glass across all Azure integration components. | 10.0 |
| C5: AU region | 10% | 5 | Australia East (NSW) and Australia Southeast (VIC) confirmed. All required services available in both regions. | 10.0 |
| C6: Operational complexity | 10% | 4 | Fully managed PaaS — no infrastructure to maintain. Azure Portal, CLI, and IaC (Bicep/Terraform) for provisioning. Deducted one point because Azure integration services span multiple components (Service Bus, Event Hubs, Monitor, API Management) requiring Azure-specific expertise the team must acquire. | 8.0 |
| C7: Cost (P19) | 10% | 5 | A$108,000-A$162,000 over 3 years under existing agreement. Lowest TCO for a full-capability option. No new procurement required. Fully satisfies Principle 19. | 10.0 |
| C8: Lock-in risk | 5% | 3 | AMQP 1.0 wire protocol is open standard. CloudEvents support available. However, Azure-specific management APIs, ARM templates, and monitoring integration create platform dependency. Migration to another broker would require reworking operational tooling, not message formats. | 3.0 |
| C9: Security | 5% | 5 | Azure AD (Entra ID) integration, OAuth 2.0, managed identities, TLS 1.2+, encryption at rest (Microsoft-managed or customer-managed keys), RBAC, and comprehensive audit logging via Azure Activity Log and Diagnostic Settings. | 5.0 |
| C10: Community/support | 5% | 5 | Extensive Microsoft documentation, Learn modules, Stack Overflow community, MVP ecosystem, and direct Microsoft support via enterprise agreement. | 5.0 |

**Total weighted score: 88.0 / 100**

---

### 6.2 PeopleSoft Integration Broker (EXISTING LICENSED)

**Components**: PeopleSoft Integration Broker (PeopleTools), Application Engine error handling, Integration Gateway.

**Licensing status**: Existing Oracle/PeopleSoft licence as part of the SIS deployment.

**Mandatory qualification**: **FAILED** (MQ-1 fail, MQ-3 fail). Scored for audit completeness only.

| Criterion | Weight | Raw Score | Justification | Weighted Score |
|-----------|--------|-----------|---------------|----------------|
| C1: Schema registry | 20% | 1 | PeopleSoft validates against XML schemas (message definitions) but has no support for JSON Schema, Avro, or Protobuf. No versioned schema registry. Schema validation is PeopleSoft-internal and does not extend to non-PeopleSoft consumers. | 4.0 |
| C2: Pub/sub routing | 15% | 2 | Integration Broker supports publish/subscribe within PeopleSoft nodes. Routing to non-PeopleSoft systems requires custom connectors (Integration Gateway Target Connectors) for each endpoint. Cannot natively route events to Blackboard Ultra, Echo360, Sonia, or Allocate+ without bespoke development. | 6.0 |
| C3: DLQ/retry/replay | 10% | 1 | No DLQ concept. Failed messages appear in Service Operations Monitor as errors requiring manual investigation via Application Engine. No configurable retry policies. No event replay capability. | 2.0 |
| C4: Observability | 10% | 1 | PeopleSoft Integration Monitor provides visibility into PeopleSoft-to-PeopleSoft message flows only. No integration with external monitoring tools. No alerting framework. No distributed tracing. | 2.0 |
| C5: AU region | 10% | 5 | On-premises, hosted within university data centre in Australia. Full data sovereignty. | 10.0 |
| C6: Operational complexity | 10% | 2 | Requires PeopleSoft/PeopleTools expertise that the integration team does not hold. PeopleSoft administration is a specialist skill set held by the SIS team, not the integration team. Cross-team dependency for every operational task. | 4.0 |
| C7: Cost (P19) | 10% | 5 | Already licensed under existing Oracle/PeopleSoft agreement. Zero incremental licensing cost. | 10.0 |
| C8: Lock-in risk | 5% | 1 | Completely PeopleSoft-locked. Proprietary message formats, proprietary routing, proprietary administration. No portable components. Any future SIS migration would require complete broker replacement. | 1.0 |
| C9: Security | 5% | 2 | Basic authentication (username/password). No native OAuth 2.0 support. TLS available for transport. No modern RBAC model — security tied to PeopleSoft permission lists. Limited audit logging. | 2.0 |
| C10: Community/support | 5% | 2 | Shrinking PeopleSoft community. Oracle support available but focused on core HCM/Financials, not integration broker. Limited Stack Overflow presence. Few integration-specific resources. | 2.0 |

**Total weighted score: 43.0 / 100**

**Disqualification note**: This score is recorded for completeness. PeopleSoft Integration Broker is **not eligible for recommendation** due to failing MQ-1 (schema registry) and MQ-3 (multi-system pub/sub).

---

### 6.3 Blackboard Ultra Webhooks (EXISTING LICENSED)

**Components**: Blackboard Ultra REST API, webhook event subscriptions, Ultra admin console.

**Licensing status**: Existing Blackboard Ultra licence as part of the LMS deployment.

**Mandatory qualification**: **FAILED** (MQ-1 fail, MQ-3 fail). Scored for audit completeness only.

| Criterion | Weight | Raw Score | Justification | Weighted Score |
|-----------|--------|-----------|---------------|----------------|
| C1: Schema registry | 20% | 0 | Ultra is not a broker and has no schema registry. Webhook payloads are defined by Blackboard; consumers must accept whatever format is sent. No validation, no versioning, no compatibility enforcement. Scored 0 (not applicable) because the capability is structurally absent. | 0.0 |
| C2: Pub/sub routing | 15% | 1 | Outbound webhooks only — Ultra pushes events to a configured URL. No topic hierarchy. No subscription management. No filtering beyond event type. No fan-out to multiple consumers without external infrastructure. | 3.0 |
| C3: DLQ/retry/replay | 10% | 0 | No DLQ. No configurable retry. No event log or replay. If a webhook delivery fails, the event may be lost depending on Ultra's internal retry behaviour (undocumented and not configurable). | 0.0 |
| C4: Observability | 10% | 1 | Ultra admin console shows webhook registration status. No message-level monitoring. No throughput metrics. No alerting. No integration with external monitoring. | 2.0 |
| C5: AU region | 10% | 4 | Depends on Ultra SaaS hosting region. Likely hosted in Australian region under current contract, but to be confirmed with Anthology. Deducted one point for uncertainty. | 8.0 |
| C6: Operational complexity | 10% | 2 | Ultra webhooks are simple to configure but are not a broker — building broker-like infrastructure (routing, retry, DLQ, schema validation) around webhooks would require significant custom development and ongoing maintenance. | 4.0 |
| C7: Cost (P19) | 10% | 5 | Already licensed. No incremental cost for webhook functionality. | 10.0 |
| C8: Lock-in risk | 5% | 1 | Completely Blackboard-locked. Webhook format defined by Anthology. No portable message format. Any LMS migration would require complete integration rewrite. | 1.0 |
| C9: Security | 5% | 3 | Webhook signing (HMAC) for payload verification. OAuth 2.0 for REST API access. TLS in transit. Limited credential management and no RBAC for webhook configuration. | 3.0 |
| C10: Community/support | 5% | 2 | Blackboard developer community is declining post-Anthology acquisition. Developer documentation exists but is inconsistent. Limited community tooling. | 2.0 |

**Total weighted score: 33.0 / 100**

**Disqualification note**: This score is recorded for completeness. Blackboard Ultra Webhooks is **not eligible for recommendation** due to failing MQ-1 (schema registry) and MQ-3 (pub/sub routing). Ultra is an event source to be consumed by the selected broker, not a candidate broker itself.

---

### 6.4 Apache Kafka — Confluent Cloud (NEW PURCHASE)

**Components**: Confluent Cloud (managed Kafka), Confluent Schema Registry, Confluent Control Center, ksqlDB (optional).

**Licensing status**: New purchase required. No existing agreement.

**Mandatory qualification**: **PASSED** (MQ-1, MQ-2, MQ-3 all pass)

| Criterion | Weight | Raw Score | Justification | Weighted Score |
|-----------|--------|-----------|---------------|----------------|
| C1: Schema registry | 20% | 5 | Confluent Schema Registry is the industry benchmark. Server-side validation — the broker rejects non-conforming payloads before delivery. Supports Avro, JSON Schema, and Protobuf. Full compatibility modes (backward, forward, full). This is the strongest schema registry capability of any candidate. | 20.0 |
| C2: Pub/sub routing | 15% | 5 | Kafka topics with partitioned consumer groups. Exactly-once semantics. Topic compaction for state events. Supports all seven INT flows with native Kafka patterns. | 15.0 |
| C3: DLQ/retry/replay | 10% | 4 | DLQ via dedicated error topics (convention-based, not built-in like Service Bus). Retry via consumer group offset management. Replay is a core Kafka strength — full event log retention with offset-based replay. Deducted one point because DLQ setup requires application-level implementation rather than platform configuration. | 8.0 |
| C4: Observability | 10% | 5 | Confluent Control Center provides comprehensive monitoring: throughput, latency, consumer lag, schema compatibility. Prometheus metrics endpoint for Grafana integration. Stream lineage for data flow visibility. | 10.0 |
| C5: AU region | 10% | 4 | Available via AWS ap-southeast-2 (Sydney) and Azure Australia East. Deducted one point because the university's primary cloud is Azure, and Confluent's Azure Australia East offering has fewer features than its AWS Sydney deployment. | 8.0 |
| C6: Operational complexity | 10% | 3 | Confluent Cloud is fully managed, eliminating broker operations. However, Kafka's conceptual model (partitions, consumer groups, offset management, exactly-once configuration) is significantly more complex than Service Bus topics. The 3-4 person team would face a steeper learning curve. | 6.0 |
| C7: Cost (P19) | 10% | 2 | A$180,000-A$360,000 over 3 years. 2-3x more expensive than Azure under existing agreement. New procurement process required. Fails Principle 19 — existing capability (Azure) is demonstrably sufficient, so this cost premium is not justified. | 4.0 |
| C8: Lock-in risk | 5% | 3 | Kafka protocol is open-source. Message formats are portable. However, Confluent-specific features (Schema Registry Enterprise, ksqlDB, stream lineage) create Confluent dependency. Self-hosted Kafka migration is possible but loses managed operational simplicity. | 3.0 |
| C9: Security | 5% | 5 | mTLS, OAuth 2.0, SASL, encryption at rest and in transit, fine-grained RBAC, audit logging, and SSO integration. Enterprise-grade security exceeding requirements. | 5.0 |
| C10: Community/support | 5% | 5 | Largest event streaming community globally. Extensive documentation, Kafka Summit conferences, Confluent Developer portal, strong Stack Overflow presence, and Confluent enterprise support. | 5.0 |

**Total weighted score: 84.0 / 100**

---

### 6.5 Apache Kafka — Self-hosted + Apicurio (OPEN SOURCE)

**Components**: Apache Kafka (self-hosted on Azure VMs), Apicurio Registry, Prometheus + Grafana, Kafka Connect.

**Licensing status**: Open-source. No licence cost. Infrastructure and labour costs apply.

**Mandatory qualification**: **PASSED** (MQ-1, MQ-2, MQ-3 all pass)

| Criterion | Weight | Raw Score | Justification | Weighted Score |
|-----------|--------|-----------|---------------|----------------|
| C1: Schema registry | 20% | 4 | Apicurio Registry supports Avro, JSON Schema, and Protobuf with compatibility enforcement. Requires separate deployment and operational management alongside Kafka. Not as tightly integrated as Confluent Schema Registry. Deducted one point for the operational separation and additional deployment surface. | 16.0 |
| C2: Pub/sub routing | 15% | 5 | Native Kafka topics, partitions, and consumer groups. Identical capability to Confluent Cloud at the protocol level. | 15.0 |
| C3: DLQ/retry/replay | 10% | 4 | Same DLQ-via-error-topics pattern as Confluent. Same replay capability via offset management. Same deduction for application-level DLQ implementation. | 8.0 |
| C4: Observability | 10% | 4 | Prometheus JMX exporter for Kafka metrics, Grafana dashboards, Apicurio metrics. Requires manual setup and maintenance of the monitoring stack. No turnkey solution like Azure Monitor or Confluent Control Center. Deducted one point for setup and maintenance burden. | 8.0 |
| C5: AU region | 10% | 5 | Self-hosted on Azure Australia East VMs. Full control over data residency. | 10.0 |
| C6: Operational complexity | 10% | 1 | This is the critical failure point. Self-hosted Kafka requires managing KRaft (or ZooKeeper), broker configuration, partition rebalancing, rolling upgrades, TLS certificate rotation, Apicurio deployment, Prometheus/Grafana stack, and backup/restore procedures. This is a full-time platform engineering role — untenable for a 3-4 person integration team that also must build and maintain integration flows. | 2.0 |
| C7: Cost (P19) | 10% | 3 | A$144,000-A$216,000 over 3 years. No licence cost, but Azure VM infrastructure (3-node Kafka cluster minimum + Apicurio + monitoring VMs) and significantly higher operational labour offset the savings. Net more expensive than Azure Integration Services. | 6.0 |
| C8: Lock-in risk | 5% | 5 | Fully open-source. Apache Kafka, Apicurio Registry, Prometheus, Grafana — all portable. Maximum architectural freedom. No vendor dependency. | 5.0 |
| C9: Security | 5% | 4 | TLS, SASL/SCRAM, ACLs for authorisation. OAuth 2.0 via Apicurio/Keycloak integration. Encryption at rest via Azure disk encryption. Audit logging via Kafka authorizer. Deducted one point because all security configuration is DIY — no managed identity integration, no turnkey RBAC. | 4.0 |
| C10: Community/support | 5% | 5 | Massive Apache Kafka open-source community. Strong Apicurio community (Red Hat backed). Extensive documentation and community tooling. No vendor support contract — community-only. | 5.0 |

**Total weighted score: 79.0 / 100**

---

### 6.6 RabbitMQ + Apicurio Sidecar (OPEN SOURCE)

**Components**: RabbitMQ (self-hosted or CloudAMQP), Apicurio Registry (sidecar), RabbitMQ Management Plugin, Prometheus Plugin.

**Licensing status**: Open-source. No licence cost. Infrastructure and labour costs apply. CloudAMQP managed option available.

**Mandatory qualification**: **PASSED** (MQ-1 marginal pass, MQ-2, MQ-3 all pass)

| Criterion | Weight | Raw Score | Justification | Weighted Score |
|-----------|--------|-----------|---------------|----------------|
| C1: Schema registry | 20% | 2 | RabbitMQ has no native schema registry. Apicurio is deployed as a sidecar — producers and consumers must call the registry API independently; there is no broker-level enforcement. A non-conforming payload will be accepted and delivered by RabbitMQ regardless of registry state. This is architecturally weaker than both Azure (client-SDK validation) and Confluent (server-side rejection). | 8.0 |
| C2: Pub/sub routing | 15% | 4 | RabbitMQ exchanges (topic, fanout, headers, direct) provide flexible routing. Different conceptual model from Kafka topics but functionally adequate for the seven INT flows. AMQP 1.0 support via plugin. Deducted one point because topic-hierarchy routing requires exchange-binding configuration that is more complex than Kafka topic naming. | 12.0 |
| C3: DLQ/retry/replay | 10% | 4 | Built-in DLQ via dead-letter exchanges — messages exceeding retry limits are automatically routed to a DLX. Configurable TTL and retry. However, no native event replay — RabbitMQ is a transient broker, not an event log. Deducted one point for lack of replay. | 8.0 |
| C4: Observability | 10% | 3 | RabbitMQ Management UI provides queue-level metrics, connection monitoring, and basic dashboards. Prometheus plugin exports metrics for Grafana. Less mature than Kafka/Confluent observability. No distributed tracing integration. No stream lineage. | 6.0 |
| C5: AU region | 10% | 5 | Self-hosted on Azure Australia East, or CloudAMQP's Sydney region. Full data residency control. | 10.0 |
| C6: Operational complexity | 10% | 3 | RabbitMQ is simpler to operate than Kafka — single binary, no ZooKeeper/KRaft, familiar queue semantics. However, adding Apicurio sidecar introduces a second system to deploy, monitor, and maintain. CloudAMQP managed option reduces broker operations but not Apicurio operations. Net: manageable but not simple. | 6.0 |
| C7: Cost (P19) | 10% | 4 | A$96,000-A$156,000 over 3 years. Lowest TCO of any option with schema registry capability. However, new procurement/deployment effort required, and the schema registry integration is the weakest of the qualified candidates. | 8.0 |
| C8: Lock-in risk | 5% | 5 | Fully open-source. RabbitMQ (MPL 2.0), Apicurio (Apache 2.0). AMQP 1.0 is an open standard. Maximum portability. | 5.0 |
| C9: Security | 5% | 3 | TLS, SASL for authentication. OAuth 2.0 via RabbitMQ auth plugin (requires configuration). Adequate but not turnkey. No managed identity integration. Audit logging via RabbitMQ log files — less structured than Azure or Confluent audit trails. | 3.0 |
| C10: Community/support | 5% | 4 | Large RabbitMQ community (VMware/Broadcom backed). Good documentation. Strong Stack Overflow presence. Smaller than Kafka ecosystem. CloudAMQP provides managed support option. | 4.0 |

**Total weighted score: 70.0 / 100**

---

## 7. Comparison Matrix

### 7.1 Raw Scores

| Criterion | Weight | Azure Integration Services | PeopleSoft IB | Ultra Webhooks | Confluent Cloud | Kafka Self-hosted | RabbitMQ + Apicurio |
|-----------|--------|---------------------------|---------------|----------------|-----------------|-------------------|---------------------|
| C1: Schema registry | 20% | 3 | 1 | 0 | **5** | 4 | 2 |
| C2: Pub/sub routing | 15% | **5** | 2 | 1 | **5** | **5** | 4 |
| C3: DLQ/retry/replay | 10% | **5** | 1 | 0 | 4 | 4 | 4 |
| C4: Observability | 10% | **5** | 1 | 1 | **5** | 4 | 3 |
| C5: AU region | 10% | **5** | **5** | 4 | 4 | **5** | **5** |
| C6: Operational complexity | 10% | **4** | 2 | 2 | 3 | 1 | 3 |
| C7: Cost (P19) | 10% | **5** | **5** | **5** | 2 | 3 | 4 |
| C8: Lock-in risk | 5% | 3 | 1 | 1 | 3 | **5** | **5** |
| C9: Security | 5% | **5** | 2 | 3 | **5** | 4 | 3 |
| C10: Community/support | 5% | **5** | 2 | 2 | **5** | **5** | 4 |

### 7.2 Weighted Scores

| Criterion | Weight | Azure Integration Services | PeopleSoft IB | Ultra Webhooks | Confluent Cloud | Kafka Self-hosted | RabbitMQ + Apicurio |
|-----------|--------|---------------------------|---------------|----------------|-----------------|-------------------|---------------------|
| C1: Schema registry | 20% | 12.0 | 4.0 | 0.0 | **20.0** | 16.0 | 8.0 |
| C2: Pub/sub routing | 15% | **15.0** | 6.0 | 3.0 | **15.0** | **15.0** | 12.0 |
| C3: DLQ/retry/replay | 10% | **10.0** | 2.0 | 0.0 | 8.0 | 8.0 | 8.0 |
| C4: Observability | 10% | **10.0** | 2.0 | 2.0 | **10.0** | 8.0 | 6.0 |
| C5: AU region | 10% | **10.0** | **10.0** | 8.0 | 8.0 | **10.0** | **10.0** |
| C6: Operational complexity | 10% | **8.0** | 4.0 | 4.0 | 6.0 | 2.0 | 6.0 |
| C7: Cost (P19) | 10% | **10.0** | **10.0** | **10.0** | 4.0 | 6.0 | 8.0 |
| C8: Lock-in risk | 5% | 3.0 | 1.0 | 1.0 | 3.0 | **5.0** | **5.0** |
| C9: Security | 5% | **5.0** | 2.0 | 3.0 | **5.0** | 4.0 | 3.0 |
| C10: Community/support | 5% | **5.0** | 2.0 | 2.0 | **5.0** | **5.0** | 4.0 |
| **TOTAL** | **100%** | **88.0** | **43.0** | **33.0** | **84.0** | **79.0** | **70.0** |

### 7.3 Ranking

| Rank | Candidate | Weighted Score | Mandatory Quals | Principle 19 Status | Eligible |
|------|-----------|---------------|-----------------|---------------------|----------|
| 1 | **Azure Integration Services** | **88.0** | PASS | EXISTING LICENSED | **YES** |
| 2 | Confluent Cloud (Kafka) | 84.0 | PASS | NEW PURCHASE — not justified | YES (contingency) |
| 3 | Apache Kafka Self-hosted + Apicurio | 79.0 | PASS | OPEN SOURCE — not justified | YES (contingency) |
| 4 | RabbitMQ + Apicurio Sidecar | 70.0 | PASS | OPEN SOURCE — not justified | YES (contingency) |
| 5 | PeopleSoft Integration Broker | 43.0 | **FAIL** | EXISTING LICENSED | **NO** |
| 6 | Blackboard Ultra Webhooks | 33.0 | **FAIL** | EXISTING LICENSED | **NO** |

---

## 8. Principle 19 Compliance Assessment

### 8.1 Principle 19 Statement

> *Where existing licensed capability can meet a requirement, it shall be used in preference to new procurement. New purchases are justified only when existing capability is demonstrably insufficient.*

### 8.2 Assessment

**Step 1: Identify existing licensed platforms with potential broker capability.**

Three existing licensed platforms were identified: Azure Integration Services (Microsoft enterprise agreement), PeopleSoft Integration Broker (Oracle/PeopleSoft licence), and Blackboard Ultra Webhooks (Anthology licence).

**Step 2: Evaluate existing platforms against mandatory qualifications.**

- **Azure Integration Services**: Passes all three mandatory qualification gates. Provides schema registry (Event Hubs), pub/sub routing (Service Bus Premium), and Australian region hosting. This is a capable, production-grade integration platform.
- **PeopleSoft Integration Broker**: Fails MQ-1 (no JSON Schema/Avro registry) and MQ-3 (PeopleSoft-centric routing only). Existing licensed, but demonstrably insufficient for the requirements.
- **Blackboard Ultra Webhooks**: Fails MQ-1 (no schema registry) and MQ-3 (no pub/sub routing). Not a broker — existing licensed for LMS purposes, not for integration brokering.

**Step 3: Determine if existing capability is sufficient.**

Azure Integration Services passes all mandatory qualifications and scores 88.0/100 in the weighted evaluation — the highest score of any candidate. The one gap (client-side rather than server-side schema validation) is a limitation, not a disqualification. The ADR-001 requirement is for schema validation, not specifically for server-side broker rejection.

**Step 4: Principle 19 conclusion.**

Existing licensed capability (Azure Integration Services) is demonstrably sufficient. **New procurement is not justified.** Confluent Cloud scores 84.0/100 — 4 points lower — with a 3-year TCO of A$180,000-A$360,000 versus A$108,000-A$162,000 for Azure. The marginal capability advantage in schema registry (server-side vs client-side validation) does not justify the cost premium or new procurement overhead.

### 8.3 Principle 19 Outcome Table

| Candidate | Licensing Status | Principle 19 Test | Outcome |
|-----------|-----------------|-------------------|---------|
| Azure Integration Services | Existing agreement | Existing capability sufficient | **SATISFIES P19** |
| PeopleSoft Integration Broker | Existing licence | Existing capability insufficient (fails MQ-1, MQ-3) | Insufficient |
| Blackboard Ultra Webhooks | Existing licence | Existing capability insufficient (fails MQ-1, MQ-3) | Insufficient |
| Confluent Cloud | New purchase | Not justified — existing capability (Azure) is sufficient | Not justified |
| Kafka Self-hosted + Apicurio | Open source (new deployment) | Not justified — existing capability (Azure) is sufficient | Not justified |
| RabbitMQ + Apicurio | Open source (new deployment) | Not justified — existing capability (Azure) is sufficient | Not justified |

---

## 9. Three-Year TCO Comparison

All figures in Australian Dollars (AUD). Estimates drawn from ARC-004-RSCH-v1.0 vendor research.

| Cost Component | Azure Integration Services | Confluent Cloud | Kafka Self-hosted | RabbitMQ + Apicurio |
|----------------|---------------------------|-----------------|-------------------|---------------------|
| **Licensing / subscription** | Included in EA (consumption-based) | A$120,000 - A$240,000 | A$0 (open source) | A$0 (open source) |
| **Infrastructure** | A$72,000 - A$108,000 | A$36,000 - A$72,000 | A$72,000 - A$108,000 | A$48,000 - A$72,000 |
| **Operational labour (incremental)** | A$36,000 - A$54,000 | A$24,000 - A$48,000 | A$72,000 - A$108,000 | A$48,000 - A$84,000 |
| **3-Year Total** | **A$108,000 - A$162,000** | **A$180,000 - A$360,000** | **A$144,000 - A$216,000** | **A$96,000 - A$156,000** |
| **Relative to Azure** | Baseline | 1.7x - 2.2x | 1.3x - 1.3x | 0.9x - 1.0x |

**Notes**:
- PeopleSoft IB and Ultra Webhooks are excluded from TCO comparison as they failed mandatory qualifications.
- Azure figures assume consumption within existing enterprise agreement at current pricing.
- RabbitMQ + Apicurio is the lowest TCO option, but its weak schema registry integration (scored 2/5) and lower overall score (70.0) make the cost advantage insufficient to overcome capability gaps.
- Labour estimates assume an integration team learning curve for all platforms, with self-hosted options requiring significantly more operational labour.

---

## 10. Risk Assessment

### 10.1 Azure Integration Services (Recommended)

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Client-side schema validation bypassed by non-compliant producer | Medium | Medium | Enforce SDK usage via integration gateway; add schema validation middleware in API Management; monitor for schema violations in Application Insights |
| Azure-specific expertise gap in integration team | Medium | Low | Microsoft Learn training pathway; Azure sandbox environment for team upskilling; university IT has existing Azure operations team for escalation |
| Consumption cost overrun under EA | Low | Medium | Azure Cost Management alerts; reserved capacity for predictable workloads; monthly cost review |
| Azure region outage affecting integration flows | Low | High | Multi-region failover design (Australia East primary, Australia Southeast secondary); Service Bus geo-disaster recovery |

### 10.2 Confluent Cloud (Contingency)

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| New procurement delays project timeline | High | High | Begin procurement process early if Azure PoC fails; pre-qualify Confluent via university procurement framework |
| Cost escalation beyond budget envelope | Medium | High | Negotiate committed-use discounts; establish cost ceilings in contract; monitor CKU consumption |
| Kafka conceptual complexity slows integration development | Medium | Medium | Confluent Developer training; hire or contract Kafka-experienced developer; start with simple flows |

### 10.3 Apache Kafka Self-hosted (Contingency)

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Operational burden overwhelms 3-4 person team | High | High | This is the primary disqualification risk. Mitigation would require hiring dedicated Kafka operations engineer — effectively a fifth team member |
| Unplanned downtime from misconfigured cluster | High | High | Extensive runbook development; automated deployment via Ansible/Terraform; but fundamentally a team-capacity problem |
| Apicurio registry becomes a single point of failure | Medium | High | Deploy Apicurio in HA mode with PostgreSQL backend; adds further operational complexity |

### 10.4 RabbitMQ + Apicurio (Contingency)

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Schema validation bypass due to sidecar architecture | High | Medium | Sidecar is advisory, not enforcing — producers can skip registry. Requires strict development governance and CI/CD pipeline enforcement |
| Apicurio sidecar drift from RabbitMQ message state | Medium | Medium | Health checks and reconciliation scripts; adds operational overhead |
| CloudAMQP vendor exit from Sydney region | Low | High | Self-hosted fallback on Azure VMs; maintain deployment automation |

---

## 11. Recommendation

### 11.1 Primary Recommendation

**Microsoft Azure Integration Services** is recommended as the integration broker platform.

| Attribute | Value |
|-----------|-------|
| **Weighted score** | 88.0 / 100 (highest) |
| **Mandatory qualifications** | All passed |
| **Principle 19 status** | Existing licensed — satisfies P19 |
| **3-Year TCO** | A$108,000 - A$162,000 (lowest for full-capability option) |
| **Key strengths** | Managed PaaS; integrated observability; Australian region; existing agreement; strong security and community |
| **Key gap** | Client-side schema validation (not server-side broker rejection) — mitigated via API Management validation middleware and SDK enforcement |

### 11.2 Contingency

**Confluent Cloud** is the designated contingency platform, to be pursued only if the Azure proof-of-concept (Phase 1, INT-001) reveals a blocking limitation in schema validation, message throughput, or operational capability that cannot be resolved within the Azure platform.

**Contingency trigger criteria**:
- Azure Event Hubs Schema Registry cannot validate the canonical event model schemas defined in ARC-003-DATA-v1.0
- Service Bus Premium message throughput is insufficient for peak enrolment event volumes (INT-001, INT-003)
- Azure Monitor cannot provide the observability required by NFR-M-001 within a single dashboard
- Any of the above must be documented as a formal finding in the Phase 1 PoC report before contingency activation

### 11.3 Rejected Candidates

| Candidate | Rejection Reason |
|-----------|-----------------|
| PeopleSoft Integration Broker | Failed mandatory qualifications MQ-1, MQ-3. Not a general-purpose broker. |
| Blackboard Ultra Webhooks | Failed mandatory qualifications MQ-1, MQ-3. Not a broker at all. |
| Apache Kafka Self-hosted | Passed qualifications but operational complexity (1/5) is untenable for team size. Score 79.0. |
| RabbitMQ + Apicurio | Passed qualifications but weak schema registry integration (2/5) and lower overall score (70.0). |

---

## 12. Next Steps

| Step | Action | Owner | Target Date |
|------|--------|-------|-------------|
| 1 | Present evaluation to Steering Committee for endorsement | Sam Okafor | 2026-08-05 |
| 2 | Draft ADR-002 (Platform Selection Decision) referencing this evaluation | Sam Okafor | 2026-08-07 |
| 3 | Provision Azure Service Bus Premium and Event Hubs Schema Registry in Australia East (sandbox) | Integration Team | 2026-08-12 |
| 4 | Execute Phase 1 PoC: INT-001 (Student Enrolment) end-to-end through Azure broker | Integration Team | 2026-08-26 |
| 5 | PoC finding report — confirm or trigger contingency | Sam Okafor | 2026-08-28 |
| 6 | Full platform provisioning and INT-001 production deployment | Integration Team | 2026-09-15 |

---

## 13. External References

| Reference | Description |
|-----------|-------------|
| ARC-004-RSCH-v1.0 | Technology and Service Research — Integration Platform Selection |
| ARC-004-STKE-v1.0 | Stakeholder Drivers & Goals Analysis |
| ARC-003-REQ-v1.0 | Requirements (INT-001 to INT-007, DR-001, NFRs) |
| ARC-003-DATA-v1.0 | Data Model (canonical event schemas E-I01 to E-I04) |
| ARC-000-PRIN-v1.1 | Architecture Principles (P8, P9, P10, P11, P16, P17, P19) |
| ADR-001 | Integration Mediation Approach (event-driven, schema registry requirement) |
| [Azure Service Bus Documentation](https://learn.microsoft.com/en-us/azure/service-bus-messaging/) | Microsoft Azure Service Bus Premium |
| [Azure Event Hubs Schema Registry](https://learn.microsoft.com/en-us/azure/event-hubs/schema-registry-overview) | Azure Event Hubs Schema Registry |
| [Confluent Schema Registry](https://docs.confluent.io/platform/current/schema-registry/) | Confluent Schema Registry documentation |
| [Apache Kafka](https://kafka.apache.org/documentation/) | Apache Kafka open-source documentation |
| [Apicurio Registry](https://www.apicur.io/registry/) | Apicurio Schema Registry |
| [RabbitMQ](https://www.rabbitmq.com/documentation.html) | RabbitMQ documentation |

---

**Generated by**: ArcKit `/arckit:evaluate` command
**Generated on**: 2026-07-29
**ArcKit Version**: 6.7.4
**Project**: Integration Platform Selection & Implementation (Project 004)
**Model**: Claude Opus 4.6 (1M context)
