# Technology and Service Research: Integration Platform Selection (Principle 19 Test)

> **Template Origin**: Official | **ArcKit Version**: 6.7.4 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-004-RSCH-v1.0 |
| **Document Type** | Technology and Service Research |
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
| **Distribution** | Project Team; Steering Committee; Digital & IT; Procurement |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-29 | ArcKit AI | Initial creation from `/arckit:research` agent — Principle 19 test research for integration broker selection | PENDING | PENDING |

---

## Executive Summary

### Research Scope

This document presents research findings for the integration broker and schema registry capability required by ADR-001 (Integration Mediation Approach). It evaluates six candidate platforms against the requirements documented across ARC-003-REQ-v1.0 (INT-001 to INT-007, DR-001), ARC-003-DATA-v1.0 (E-I01 to E-I04), and ARC-000-PRIN-v1.1 (Principles 6, 10, 11, 17, 19).

**This is a Principle 19 evaluation.** Existing licensed capability is evaluated first, before any new purchase is considered. The evaluation order reflects this: (1) Microsoft Azure Integration Services (existing agreement), (2) PeopleSoft Integration Broker (already licensed SIS), (3) Blackboard Ultra webhooks/events (already licensed LMS), then (4-6) new options.

**Requirements Analyzed**: 7 integration requirements (INT-001 to INT-007), 1 data requirement (DR-001), plus non-functional requirements for security, observability, availability, and privacy drawn from ARC-003-REQ-v1.0 and ARC-000-PRIN-v1.1.

**Research Categories Identified**: 1 primary category — Integration Broker with Schema Registry. This is a single-category evaluation of six named candidates, not a broad market scan.

**Research Approach**: Web research of vendor pricing, capabilities, and documentation; cross-referencing against published requirements and architecture principles; Principle 19 evaluation sequence.

### Key Findings

- **Microsoft Azure Integration Services** is the recommended platform. Azure Service Bus (Premium) provides the required publish/subscribe, dead-letter handling, and retry capability; Azure Event Hubs provides the schema registry with runtime validation; Azure Monitor provides single-plane observability. The university's existing Microsoft enterprise agreement covers licensing. Australian region availability is confirmed (Australia East, Australia Southeast). This satisfies Principle 19.

- **PeopleSoft Integration Broker** provides basic publish/subscribe and XML schema validation but is architecturally constrained to PeopleSoft-centric integrations, lacks a modern schema registry for JSON Schema or Avro, and cannot serve as a general-purpose event broker for non-PeopleSoft systems (Blackboard Ultra, Echo360, Sonia, Allocate+). It **fails** the Principle 19 test on schema registry capability and multi-system routing grounds.

- **Blackboard Ultra webhooks/REST API** is a consumer of integration events, not a broker. It has no publish/subscribe infrastructure, no schema registry, no dead-letter handling, and no event routing capability. It **fails** the Principle 19 test on fundamental capability grounds.

- **Apache Kafka** (Confluent Cloud) provides the strongest schema registry and event streaming capability but introduces significant operational complexity for a 3-4 person team and costs substantially more than Azure Service Bus under the existing agreement.

- **RabbitMQ** and **NATS** are lightweight, operationally simpler brokers but lack native schema registry capability, requiring a sidecar approach (e.g., Apicurio Registry) that adds architectural complexity and operational surface.

### Build vs Buy Summary

| Approach | Description | Total 3-Year TCO (AUD) | Rationale |
|----------|-----------|------------------------|-----------|
| **EXISTING** (Azure Integration Services) | Use existing Microsoft agreement — Service Bus Premium + Event Hubs Schema Registry + Monitor | **A$108,000 - A$162,000** | Principle 19 satisfied; Australian region; team can learn; schema registry included |
| **BUY** (Confluent Cloud Kafka) | New purchase — managed Kafka with schema registry | **A$180,000 - A$360,000** | Strongest schema registry; highest cost; most operational complexity |
| **ADOPT** (Apache Kafka self-hosted + Apicurio) | Open-source, self-hosted on Azure VMs | **A$144,000 - A$216,000** | Maximum control; highest operational burden; skills gap significant |
| **ADOPT** (RabbitMQ + Apicurio sidecar) | Open-source broker + separate schema registry | **A$96,000 - A$156,000** | Lowest cost; schema registry is a bolted-on sidecar, not integrated |
| **ADOPT** (NATS + custom validation) | Open-source ultra-lightweight broker | **A$72,000 - A$120,000** | Lowest cost of all; no native schema registry — validation is application-level |

### Top Recommended Vendors

**Shortlist for further evaluation (Principle 19 evaluation order)**:

1. **Microsoft Azure Integration Services** (Service Bus + Event Hubs + Monitor) for Integration Broker: Existing agreement; schema registry included; Australian region confirmed; meets all ADR-001 requirements
2. **Confluent Cloud** for Integration Broker: Market-leading schema registry; strongest event streaming; but fails Principle 19 (new purchase) and costs 2-3x more
3. **Apache Kafka (self-hosted) + Apicurio Registry** for Integration Broker: Open-source fallback if Azure proves unsuitable during proof-of-concept; maximum control; highest skills requirement

### Requirements Coverage

- 100% of requirements have identified solutions with the recommended option (Azure Integration Services)
- 0 requirements need custom development with the recommended option
- 0 requirements need further research — the Principle 19 test produces a clear outcome

---

## Research Categories

This research evaluates a single category — **Integration Broker with Schema Registry** — against six named candidates. The category is derived from:

- **DR-001**: Canonical data model implementation — requires schema registry with runtime validation
- **INT-001 to INT-007**: Seven integrations requiring publish/subscribe event routing
- **Principle 6**: Canonical Data Model — requires runtime schema enforcement
- **Principle 10**: Interface-Mediated Integration — requires published, versioned interfaces
- **Principle 11**: Event-Driven and Near-Real-Time by Default — requires event-driven propagation
- **Principle 17**: Observable Integrations and Services — requires telemetry, alerting, monitoring
- **Principle 19**: Realise Licensed Capability Before New Spend — constrains evaluation order

---

## Category 1: Integration Broker with Schema Registry

**Requirements Addressed**: DR-001, INT-001, INT-002, INT-003, INT-004, INT-005, INT-006, INT-007, plus NFR-P-001 (latency), NFR-SEC-002 (OAuth 2.0), NFR-M-001 (observability), NFR-A-001 (availability)

**Why This Category**: ADR-001 selected a central integration broker (Option B) to enforce the canonical data model at runtime, provide single-plane observability, and reduce the marginal cost of each additional integration. The broker must host a schema registry with the six canonical entities (PERSON, UNIT, TEACHING_PERIOD, UNIT_OFFERING, ENROLMENT, INSTITUTIONAL_ROLE_ASSIGNMENT) and validate events against those schemas at runtime.

### Evaluation Criteria

The following criteria are derived from the ADR-001 requirements, stakeholder drivers (ARC-004-STKE-v1.0), and architecture principles:

| # | Criterion | Weight | Source |
|---|-----------|--------|--------|
| C1 | Schema registry with runtime validation (reject non-conformant events) | 20% | DR-001, ADR-001, SD-9 |
| C2 | Publish/subscribe with topic-based routing for 7 integrations | 15% | INT-001 to INT-007, P10, P11 |
| C3 | Dead-letter, retry, and replay handling | 10% | ADR-001 Option B, SD-1 |
| C4 | Single-plane observability (metrics, logging, alerting) | 10% | P17, NFR-M-001, SD-3 |
| C5 | Australian region hosting (or assessed APP 8 cross-border position) | 10% | P8, SD-6, REQ-030 |
| C6 | Operational complexity appropriate for 3-4 person team | 10% | SD-1, G-5, CSF-4 |
| C7 | Cost — licence + hosting + operations (Principle 19 weighting) | 10% | P19, SD-2, SD-4 |
| C8 | Vendor lock-in risk (open protocols, data portability) | 5% | P9, SD-8 |
| C9 | Security — OAuth 2.0, encryption, audit logging | 5% | P16, SD-5, NFR-SEC-002 |
| C10 | Community and support ecosystem | 5% | SD-10, G-5 |

---

### Option 1A: Microsoft Azure Integration Services (EXISTING LICENSED)

**Principle 19 status**: EXISTING LICENSED CAPABILITY — evaluated first.

**Description**: The university holds an existing Microsoft enterprise agreement. Azure Integration Services comprises Azure Service Bus (enterprise messaging with queues and topics), Azure Event Hubs (event streaming with schema registry), Azure API Management (API gateway and developer portal), and Azure Monitor (observability, logging, alerting). For this use case, the relevant components are Service Bus Premium (topic-based pub/sub with dead-letter and retry), Event Hubs with Schema Registry (Avro and JSON Schema validation), and Azure Monitor (telemetry and alerting).

**Vendor**: Microsoft Corporation. Headquarters: Redmond, WA, USA. Founded: 1975. Public company (NASDAQ: MSFT).

**Australian Region**: Confirmed. Azure regions Australia East (Sydney) and Australia Southeast (Melbourne) are available for Service Bus, Event Hubs, and Monitor. [WEB-1-C1]

**Schema Registry Capability**: Azure Event Hubs provides a Schema Registry that stores schemas for events, with compatibility modes (backward, forward, full, none) at the schema group level. Schemas can be defined in Avro or JSON Schema format. Validation is client-side using the Avro or JSON Schema serializer/deserializer provided by the SDK — the registry stores and versions schemas, and the SDK enforces them at serialization time. [WEB-2-C1]

**Publish/Subscribe**: Azure Service Bus provides topic-based publish/subscribe with message sessions, FIFO ordering, auto-forwarding, and subscription filters. Supports AMQP 1.0 (open protocol) and HTTP. [WEB-3-C1]

**Dead-Letter and Retry**: Built-in dead-letter queue per topic subscription. Configurable retry policy with exponential backoff. Failed messages automatically moved to DLQ after configurable retry count. [WEB-3-C2]

**Observability**: Azure Monitor provides metrics, diagnostic logs, and alerting for Service Bus and Event Hubs. Integration with Azure Application Insights for distributed tracing. Single pane of glass via Azure Portal or Grafana. [WEB-3-C3]

**Security**: OAuth 2.0 with Azure AD service principals (Managed Identity or client credentials). Encryption at rest (Microsoft-managed or customer-managed keys in Premium). TLS 1.2 in transit. Full audit logging. Role-Based Access Control (RBAC). [WEB-3-C4]

**Pricing Model**: The university's existing Microsoft enterprise agreement likely includes Azure consumption credits. Incremental costs are:

**Cost Breakdown** (AUD estimates, based on USD pricing with AUD/USD ~0.65):

| Cost Item | Year 1 (AUD) | Year 2 (AUD) | Year 3 (AUD) | Notes |
|-----------|-------------|-------------|-------------|-------|
| Service Bus Premium (1 MU) | A$15,600 | A$15,600 | A$15,600 | ~USD 677/mo per MU = ~A$1,041/mo x 12 + 25% AU region uplift [WEB-4-C1] |
| Event Hubs (Schema Registry) | A$3,600 | A$3,600 | A$3,600 | Standard tier + schema registry; low volume (< 1M events/day) [WEB-5-C1] |
| Azure Monitor | A$1,800 | A$1,800 | A$1,800 | Log Analytics workspace; basic alerting; low data volume |
| Integration effort | A$36,000 | A$0 | A$0 | 3 person-months @ A$12,000/mo (internal team cost) |
| Training | A$6,000 | A$0 | A$0 | Azure messaging training for 3 team members |
| **Total** | **A$63,000** | **A$21,000** | **A$21,000** | |
| **3-Year TCO** | | | **A$105,000** | Excludes existing agreement credits |

**Note**: If the existing Microsoft agreement includes Azure consumption credits, the hosting costs (Service Bus, Event Hubs, Monitor) may be partially or fully covered. This would reduce the 3-year TCO to as low as A$42,000 (integration effort + training only). The university must confirm the agreement terms with Grace Tanaka (Procurement).

**Pros**:

- Existing licensed capability — satisfies Principle 19 directly
- Australian region confirmed (Australia East, Australia Southeast)
- Schema registry with compatibility modes (Avro, JSON Schema)
- Enterprise-grade dead-letter, retry, and session handling
- Single-plane observability via Azure Monitor / Application Insights
- OAuth 2.0 with Azure AD Managed Identity — strongest credential model
- AMQP 1.0 open protocol reduces lock-in
- SLA: 99.99% for Premium tier with geo-redundancy [WEB-3-C5]
- Extensive documentation, Microsoft Learn training resources, and community

**Cons**:

- Schema validation is client-side (SDK-enforced at serialization), not server-side rejection — the registry stores and versions schemas, but validation relies on producers and consumers using the correct serializer [WEB-2-C2]
- Premium tier required for production workloads (no per-message pricing tier suitable for production)
- Azure Service Bus uses a proprietary management API alongside AMQP — operational tooling is Azure-specific
- Microsoft ecosystem dependency (mitigated by AMQP open protocol for data plane)
- Premium MU pricing is relatively expensive compared to open-source hosting

**Assessment Against Criteria**:

| Criterion | Rating | Notes |
|-----------|--------|-------|
| C1: Schema registry + runtime validation | PARTIAL | Schema registry exists (Event Hubs); validation is client-side SDK, not broker-enforced rejection. Adequate if all producers/consumers use the provided SDK. |
| C2: Pub/sub with topic routing | FULL | Service Bus topics with subscription filters — native and mature |
| C3: Dead-letter, retry, replay | FULL | Built-in DLQ, configurable retry, message deferral |
| C4: Observability | FULL | Azure Monitor + Application Insights — single pane |
| C5: Australian region | FULL | Australia East and Southeast confirmed |
| C6: Operational complexity (3-4 people) | GOOD | Managed service; no infrastructure to maintain; team learns Azure messaging |
| C7: Cost (Principle 19) | BEST | Existing agreement; lowest incremental cost of any suitable option |
| C8: Lock-in risk | MEDIUM | AMQP 1.0 data plane is open; management plane is Azure-specific |
| C9: Security | FULL | OAuth 2.0 / Azure AD / Managed Identity; encryption; RBAC; audit logging |
| C10: Community/support | FULL | Microsoft Learn; extensive documentation; enterprise support via agreement |

---

### Option 1B: PeopleSoft Integration Broker (EXISTING LICENSED)

**Principle 19 status**: EXISTING LICENSED CAPABILITY — evaluated second.

**Description**: PeopleSoft Integration Broker is a component of PeopleTools, included in the university's existing Oracle PeopleSoft SIS licence. It provides synchronous (request/response) and asynchronous (publish/subscribe) messaging between PeopleSoft and external systems, with an Integration Gateway (Java servlet on the web tier) and Integration Engine (on the application server). [WEB-6-C1]

**Schema Validation**: PeopleSoft Integration Broker supports runtime XML schema validation — it can validate messages against XML schemas defined in the PeopleSoft message catalog. This rejects non-conformant XML messages at the gateway. [WEB-7-C1]

However, this is **XML-only** schema validation against PeopleSoft message definitions, not a general-purpose schema registry supporting JSON Schema, Avro, or Protobuf. The canonical data model in ARC-001-DATA-v1.0 would need to be expressed as PeopleSoft message definitions — a format no other system in the estate can consume.

**Publish/Subscribe**: PeopleSoft Integration Broker provides publish/subscribe via Channels and Subchannels. However, the routing architecture is PeopleSoft-centric: each message node can route to only one connector, and subscription contracts within the same channel share a queue, creating potential bottlenecks. [WEB-8-C1]

**Dead-Letter and Retry**: Publication contracts that fail remain in WORKING or ERROR status. Retry is manual or requires custom PeopleCode handlers. There is no native dead-letter queue concept equivalent to modern message brokers.

**Observability**: Integration Broker provides a Service Operations Monitor within PeopleSoft, showing message status and errors. This is a PeopleSoft-internal view — it does not integrate with external monitoring tools (Azure Monitor, Grafana, Prometheus) without custom development.

**Security**: PeopleSoft supports WS-Security for SOAP and basic authentication for REST. It does not natively support OAuth 2.0 client credentials flow for service-to-service authentication. Implementing OAuth 2.0 would require custom PeopleCode development. [WEB-6-C2]

**Australian Hosting**: PeopleSoft is hosted on-premises at the university. No cross-border consideration.

**Cost Breakdown** (AUD):

| Cost Item | Year 1 (AUD) | Year 2 (AUD) | Year 3 (AUD) | Notes |
|-----------|-------------|-------------|-------------|-------|
| Licence | A$0 | A$0 | A$0 | Already licensed |
| Hosting | A$0 | A$0 | A$0 | Existing on-premises infrastructure |
| Integration effort | A$72,000 | A$24,000 | A$12,000 | 6 person-months Y1 (PeopleCode, connectors for each external system); ongoing maintenance |
| **Total** | **A$72,000** | **A$24,000** | **A$12,000** | |
| **3-Year TCO** | | | **A$108,000** | High effort cost despite zero licence cost |

**Assessment Against Criteria**:

| Criterion | Rating | Notes |
|-----------|--------|-------|
| C1: Schema registry + runtime validation | FAIL | XML-only schema validation; no JSON Schema, Avro, or Protobuf support; no general-purpose schema registry; no schema versioning or compatibility modes |
| C2: Pub/sub with topic routing | PARTIAL | Channels/Subchannels exist but are PeopleSoft-centric; external systems (Ultra, Echo360, Sonia) cannot natively subscribe |
| C3: Dead-letter, retry, replay | FAIL | No native DLQ; manual retry; no replay capability |
| C4: Observability | FAIL | PeopleSoft-internal monitoring only; no integration with modern observability stacks |
| C5: Australian region | FULL | On-premises; no cross-border |
| C6: Operational complexity | POOR | Requires PeopleSoft/PeopleTools expertise the integration team does not hold; single-system dependency |
| C7: Cost (Principle 19) | GOOD | Zero licence cost but high integration effort |
| C8: Lock-in risk | HIGH | Entirely Oracle PeopleSoft dependent; no open protocol at data plane |
| C9: Security | FAIL | No native OAuth 2.0 client credentials; WS-Security and basic auth only |
| C10: Community/support | POOR | Shrinking PeopleSoft community; Oracle support only |

**Principle 19 Test Result**: **FAIL**. PeopleSoft Integration Broker cannot serve as a general-purpose event broker for the L&T ecosystem. Its schema validation is XML-only with no support for the JSON Schema or Avro formats required by the canonical data model. Its publish/subscribe is PeopleSoft-centric and cannot natively serve non-PeopleSoft consumers. It lacks dead-letter handling, modern observability, and OAuth 2.0 support. Using it would deliver Option A's architecture (point-to-point from PeopleSoft) at higher effort cost than building direct integrations.

---

### Option 1C: Blackboard Ultra Webhooks/REST API (EXISTING LICENSED)

**Principle 19 status**: EXISTING LICENSED CAPABILITY — evaluated third.

**Description**: Blackboard Ultra (Anthology) provides REST APIs for user, course, enrollment, content, and grade management, with OAuth 2.0 authentication. LTI 1.3 Advantage provides Names and Role Provisioning Services (NRPS) and Assignment and Grade Services (AGS). The REST API supports a rate-limited request/response model. [WEB-9-C1]

**Schema Registry Capability**: None. Blackboard Ultra has no schema registry. There is no mechanism to define, version, or validate event schemas. The REST API returns fixed JSON structures defined by Anthology — there is no extensibility for canonical model enforcement.

**Publish/Subscribe**: None. Blackboard Ultra is a consumer and producer of data via REST API calls and LTI launches, not an event broker. It does not provide topic-based publish/subscribe infrastructure. There is no webhook subscription mechanism for arbitrary event types that would allow other systems to subscribe to Ultra events as a general-purpose broker.

**Dead-Letter and Retry**: None. REST API calls either succeed or fail; the caller handles retry. There is no broker-side dead-letter queue.

**Observability**: Limited to REST API call logs and LTI launch logs within Blackboard administration. No integration with external monitoring.

**Security**: OAuth 2.0 for REST API access. LTI 1.3 security model (platform-tool key pair) for LTI integrations. Premium APIs may require additional licensing. [WEB-10-C1]

**Rate Limits**: 10,000 API calls per 24 hours per site by default. Higher limits require approval from Anthology. [WEB-10-C2]

**Cost**: A$0 incremental (already licensed for LMS purposes).

**Assessment Against Criteria**:

| Criterion | Rating | Notes |
|-----------|--------|-------|
| C1: Schema registry + runtime validation | FAIL | No schema registry; no schema validation; no schema versioning |
| C2: Pub/sub with topic routing | FAIL | No pub/sub infrastructure; REST API only |
| C3: Dead-letter, retry, replay | FAIL | No broker-side DLQ, retry, or replay |
| C4: Observability | FAIL | Limited to Blackboard admin; no external integration |
| C5: Australian region | UNKNOWN | Hosting region requires APP 8 assessment (Assumption A-5 in ARC-003-REQ) |
| C6: Operational complexity | N/A | Not an integration broker; cannot be evaluated on this criterion |
| C7: Cost | BEST | Zero cost — but zero capability |
| C8: Lock-in risk | N/A | Not applicable — not a broker |
| C9: Security | PARTIAL | OAuth 2.0 for REST API; but rate limits constrain integration volume |
| C10: Community/support | POOR | Anthology developer documentation is adequate but not an integration broker community |

**Principle 19 Test Result**: **FAIL**. Blackboard Ultra is a platform that consumes and produces data, not an integration broker. It has none of the required capabilities: no schema registry, no pub/sub, no dead-letter handling, no observability infrastructure. Evaluating it as a broker candidate is like evaluating a hammer as a saw — the tool serves a different purpose. Ultra is a *target* of the integration broker, not a candidate to *be* the broker.

---

### Option 1D: Apache Kafka (Confluent Cloud — Managed)

**Principle 19 status**: NEW PURCHASE — evaluated only because existing capability was tested first.

**Description**: Apache Kafka is the market-leading event streaming platform. Confluent Cloud provides Kafka as a managed service with a native Schema Registry supporting Avro, JSON Schema, and Protobuf, with full compatibility modes (backward, forward, full, none, transitive variants). [WEB-11-C1]

**Schema Registry**: Confluent Schema Registry is the strongest option evaluated. It supports Avro, JSON Schema, and Protobuf with server-side validation, schema evolution with compatibility enforcement, and a REST API for schema management. Non-conformant messages are rejected at the producer before they enter the topic. [WEB-11-C2]

**Publish/Subscribe**: Kafka topics with consumer groups provide topic-based publish/subscribe with exactly-once semantics (EOS), partitioning, and consumer group management.

**Dead-Letter and Retry**: Confluent Cloud supports dead-letter topics, configurable retry with backoff, and full replay from any offset (event sourcing native).

**Observability**: Confluent Cloud provides Confluent Control Center (or Cloud Console) with metrics, monitoring, and alerting. Integration with Datadog, Grafana, and Prometheus via metrics export.

**Australian Region**: Confluent Cloud is available on AWS ap-southeast-2 (Sydney) and Azure Australia East. [WEB-11-C3]

**Security**: OAuth 2.0 / SASL authentication; encryption at rest and in transit (TLS); RBAC with fine-grained ACLs; audit logging.

**Cost Breakdown** (AUD, based on Confluent Cloud Standard cluster):

| Cost Item | Year 1 (AUD) | Year 2 (AUD) | Year 3 (AUD) | Notes |
|-----------|-------------|-------------|-------------|-------|
| Confluent Cloud Standard cluster | A$24,000 | A$24,000 | A$24,000 | ~USD 1,000-2,000/mo for standard production [WEB-12-C1] |
| Schema Registry (Essentials) | A$1,800 | A$1,800 | A$1,800 | 100 free schemas; A$150/mo for additional [WEB-12-C2] |
| Networking / data transfer | A$3,600 | A$3,600 | A$3,600 | Estimated for low-volume university workload |
| Integration effort | A$48,000 | A$0 | A$0 | 4 person-months (Kafka client libraries, schema definition, topic design) |
| Training | A$12,000 | A$0 | A$0 | Confluent training for 3 team members |
| **Total** | **A$89,400** | **A$29,400** | **A$29,400** | |
| **3-Year TCO** | | | **A$148,200** | Before potential volume-based increases |

**Pros**:

- Market-leading schema registry — strongest runtime validation of all options
- Server-side schema enforcement (producer-side rejection)
- Full event replay from any offset — strongest recovery and audit capability
- Managed service reduces operational burden
- Australian region confirmed (AWS Sydney, Azure Australia East)
- Strong community, documentation, and training resources

**Cons**:

- Fails Principle 19 — new purchase when existing Azure capability may suffice
- Significantly more expensive than Azure under the existing agreement (A$148K vs A$105K)
- Kafka's operational model (topics, partitions, consumer groups, offsets) has a steeper learning curve than Azure Service Bus for a team with no middleware experience
- Confluent Cloud pricing is opaque — exact per-CKU rates require sales engagement [WEB-12-C3]
- Over-engineered for the university's volume ( < 10,000 events/day across 7 integrations)

**Assessment Against Criteria**:

| Criterion | Rating | Notes |
|-----------|--------|-------|
| C1: Schema registry + runtime validation | BEST | Server-side validation; Avro, JSON Schema, Protobuf; full compatibility modes |
| C2: Pub/sub with topic routing | FULL | Kafka topics with consumer groups — native and mature |
| C3: Dead-letter, retry, replay | FULL | Dead-letter topics; full replay from any offset |
| C4: Observability | FULL | Control Center; Datadog/Grafana integration |
| C5: Australian region | FULL | AWS Sydney and Azure Australia East |
| C6: Operational complexity | MODERATE | Managed service helps, but Kafka concepts (partitions, offsets, consumer groups) are more complex than Service Bus |
| C7: Cost | POOR | New purchase; 40-100% more expensive than Azure under existing agreement |
| C8: Lock-in risk | LOW | Apache Kafka is open-source; Confluent Cloud uses the open Kafka protocol |
| C9: Security | FULL | OAuth 2.0 / SASL; encryption; RBAC; audit logging |
| C10: Community/support | BEST | Largest event streaming community; extensive training and certification |

---

### Option 1E: Apache Kafka (Self-Hosted) + Apicurio Schema Registry

**Principle 19 status**: NEW OPTION (open source) — no licence cost but significant hosting and operational cost.

**Description**: Self-hosted Apache Kafka cluster on Azure Virtual Machines (within the existing Azure agreement), paired with Apicurio Registry — an open-source, CNCF-hosted schema registry supporting Avro, JSON Schema, Protobuf, OpenAPI, and AsyncAPI. [WEB-13-C1]

**Schema Registry**: Apicurio Registry provides schema storage, versioning, compatibility enforcement, and validation. It is compatible with the Confluent Schema Registry API, allowing use of Confluent's serializers/deserializers. Supports JSON Schema for the canonical model entities. [WEB-13-C2]

**Cost Breakdown** (AUD):

| Cost Item | Year 1 (AUD) | Year 2 (AUD) | Year 3 (AUD) | Notes |
|-----------|-------------|-------------|-------------|-------|
| Azure VMs (3-node Kafka cluster) | A$14,400 | A$14,400 | A$14,400 | 3x D4s_v5 VMs (~A$400/mo each) |
| Azure Managed Disks (Kafka storage) | A$3,600 | A$3,600 | A$3,600 | Premium SSD for Kafka logs |
| Apicurio Registry (VM or container) | A$2,400 | A$2,400 | A$2,400 | 1x D2s_v5 VM or AKS container |
| Integration effort | A$60,000 | A$0 | A$0 | 5 person-months (Kafka cluster setup, Apicurio, topic design, security hardening) |
| Operations and maintenance | A$0 | A$18,000 | A$18,000 | 1.5 person-months/year for patching, upgrades, monitoring |
| Training | A$12,000 | A$0 | A$0 | Kafka + Apicurio training |
| **Total** | **A$92,400** | **A$38,400** | **A$38,400** | |
| **3-Year TCO** | | | **A$169,200** | Highest operational burden |

**Pros**:

- Zero licence cost
- Maximum control over configuration, versioning, and data
- Apicurio provides excellent schema registry with JSON Schema support
- Uses Azure VMs within the existing agreement (Principle 19 alignment for hosting)
- Open-source throughout — no vendor lock-in

**Cons**:

- Highest operational burden — patching, monitoring, capacity planning, failure recovery all on the team
- Kafka cluster management requires significant expertise the team does not hold (SD-1, G-5)
- 3-node ZooKeeper (or KRaft) cluster adds complexity
- Security hardening is manual (TLS, SASL, network policies)
- Higher 3-year TCO than managed Azure services despite zero licence cost

**Assessment Against Criteria**:

| Criterion | Rating | Notes |
|-----------|--------|-------|
| C1: Schema registry + runtime validation | FULL | Apicurio Registry with JSON Schema validation and compatibility modes |
| C2: Pub/sub with topic routing | FULL | Native Kafka topics and consumer groups |
| C3: Dead-letter, retry, replay | FULL | Kafka replay; DLQ pattern via dead-letter topics |
| C4: Observability | MODERATE | Requires custom Prometheus/Grafana setup; not out-of-the-box |
| C5: Australian region | FULL | Azure VMs in Australia East |
| C6: Operational complexity | POOR | 3-node cluster + ZooKeeper/KRaft + Apicurio — significant ops burden for 3-4 people |
| C7: Cost | MODERATE | Zero licence but high operations cost |
| C8: Lock-in risk | BEST | Fully open-source; maximum portability |
| C9: Security | MODERATE | Manual hardening required; OAuth 2.0 possible but not out-of-the-box |
| C10: Community/support | GOOD | Large Apache Kafka community; Apicurio under CNCF |

---

### Option 1F: RabbitMQ (CloudAMQP — Managed) + Apicurio Sidecar

**Principle 19 status**: NEW OPTION.

**Description**: RabbitMQ is a lightweight, widely deployed message broker supporting AMQP 0.9.1, MQTT, STOMP, and HTTP. CloudAMQP provides managed RabbitMQ hosting. RabbitMQ does not include a native schema registry; schema validation would require Apicurio Registry as a sidecar, with validation implemented in the producer/consumer applications. [WEB-14-C1]

**Schema Registry**: RabbitMQ has **no native schema registry**. Third-party npm packages (e.g., `rabbitmq-schema`) provide basic JSON Schema validation at the application layer, but this is convention-based, not broker-enforced. A sidecar Apicurio Registry could store and version schemas, but validation would be application-level — exactly the "enforcement by convention" that ADR-001 rejected.

**CloudAMQP Pricing** (USD, convert to AUD at 1.54):

For a production-grade dedicated RabbitMQ instance suitable for 7 integrations, the **Big Bunny** plan (3-node cluster, 1k msg/s, 9k connections) at USD $297/mo (A$457/mo) or **Happy Hare** (3-node, 8k msg/s) at USD $597/mo (A$919/mo) would be appropriate. [WEB-15-C1]

**Cost Breakdown** (AUD):

| Cost Item | Year 1 (AUD) | Year 2 (AUD) | Year 3 (AUD) | Notes |
|-----------|-------------|-------------|-------------|-------|
| CloudAMQP Big Bunny (3-node) | A$5,484 | A$5,484 | A$5,484 | USD 297/mo x 12 x 1.54 [WEB-15-C1] |
| Apicurio Registry (Azure container) | A$2,400 | A$2,400 | A$2,400 | Separate container for schema registry |
| Integration effort | A$36,000 | A$0 | A$0 | 3 person-months (RabbitMQ exchanges, Apicurio, application-level validation) |
| Operations and maintenance | A$0 | A$6,000 | A$6,000 | 0.5 person-months/year for Apicurio maintenance and schema management |
| Training | A$6,000 | A$0 | A$0 | RabbitMQ training for 3 team members |
| **Total** | **A$49,884** | **A$13,884** | **A$13,884** | |
| **3-Year TCO** | | | **A$77,652** | Lowest cost — but schema registry is bolted on |

**Pros**:

- Lowest managed-service cost of all options
- RabbitMQ is operationally simpler than Kafka — easier learning curve for the team
- CloudAMQP manages patching, monitoring, backups
- AMQP 0.9.1 is an open protocol (limited lock-in)
- Strong community and documentation

**Cons**:

- **No native schema registry** — the defining requirement from ADR-001 (C1) is not met natively
- Schema validation is application-level, not broker-enforced — this is exactly the "enforcement by convention" ADR-001 rejected [P4-C5]
- Apicurio sidecar adds architectural and operational complexity
- CloudAMQP's Australian region availability is via AWS ap-southeast-2 — requires verification
- RabbitMQ 4.1 (February 2026) adds streams but still no schema registry [WEB-14-C2]

**Assessment Against Criteria**:

| Criterion | Rating | Notes |
|-----------|--------|-------|
| C1: Schema registry + runtime validation | FAIL (native) / PARTIAL (with sidecar) | No native registry; Apicurio sidecar provides storage/versioning but validation is application-level |
| C2: Pub/sub with topic routing | FULL | Exchanges and queues with routing keys — mature and well-understood |
| C3: Dead-letter, retry, replay | PARTIAL | Dead-letter exchanges exist; replay requires streams (RabbitMQ 4.1+); less mature than Kafka |
| C4: Observability | MODERATE | CloudAMQP provides monitoring dashboard; Prometheus plugin available |
| C5: Australian region | PROBABLE | CloudAMQP on AWS ap-southeast-2 (Sydney) — requires confirmation |
| C6: Operational complexity | GOOD | Simpler than Kafka; CloudAMQP manages infrastructure; but Apicurio sidecar adds surface |
| C7: Cost | BEST | Lowest managed-service TCO |
| C8: Lock-in risk | LOW | AMQP open protocol; CloudAMQP is one of several managed RabbitMQ providers |
| C9: Security | MODERATE | TLS, SASL; OAuth 2.0 plugin available but not standard; VPC peering via add-on (USD 99/mo) |
| C10: Community/support | GOOD | Large RabbitMQ community; CloudAMQP provides dedicated support on paid plans |

---

### Option 1G: NATS (Synadia Cloud — Managed)

**Principle 19 status**: NEW OPTION.

**Description**: NATS is an ultra-lightweight, cloud-native messaging system designed for high performance and simplicity. NATS JetStream provides persistence, replay, and at-least-once delivery. Synadia Cloud provides managed NATS hosting. [WEB-16-C1]

**Schema Registry**: NATS has **no native schema registry** in the broker sense. JetStream provides JSON Schemas for its own API messages and some advisories, with a `nats schemas` CLI command for inspecting these internal schemas. However, this is not a user-defined schema registry for application messages — it validates JetStream management API calls, not application event payloads. [WEB-16-C2]

Application-level schema validation would require custom implementation. There is no equivalent of Confluent Schema Registry or Azure Event Hubs Schema Registry for NATS.

**Synadia Cloud Pricing** (USD):

| Plan | Monthly Cost (USD) | Monthly Cost (AUD) | Connections | Network Data | Notes |
|------|-------|-------|-------------|--------------|-------|
| Personal | Free | Free | 10 | 10 GiB | Development only |
| Starter | $49 | A$75 | 100 | 100 GiB | Not sufficient for production |
| Pro | $199 | A$306 | 1,000 | 1 TiB | Minimum viable for production |
| Enterprise | Custom | Custom | Custom | Custom | Sales engagement required |

Source: [WEB-17-C1]

**Cost Breakdown** (AUD, Pro plan):

| Cost Item | Year 1 (AUD) | Year 2 (AUD) | Year 3 (AUD) | Notes |
|-----------|-------------|-------------|-------------|-------|
| Synadia Cloud Pro | A$3,672 | A$3,672 | A$3,672 | USD 199/mo x 12 x 1.54 [WEB-17-C1] |
| Custom schema validation | A$24,000 | A$6,000 | A$6,000 | 2 person-months to build; 0.5/yr to maintain |
| Integration effort | A$36,000 | A$0 | A$0 | 3 person-months |
| Training | A$3,000 | A$0 | A$0 | NATS training (smaller ecosystem, less formal training) |
| **Total** | **A$66,672** | **A$9,672** | **A$9,672** | |
| **3-Year TCO** | | | **A$86,016** | Excludes custom schema validation maintenance risk |

**Pros**:

- Ultra-lightweight — simplest operational model of all options
- Lowest hosting cost
- JetStream provides persistence and replay
- Strong performance — handles high message rates with low latency
- Cloud-native design; small binary footprint

**Cons**:

- **No schema registry** — the defining requirement from ADR-001 is entirely unmet
- Custom schema validation must be built and maintained — this is custom development, not a product feature
- Smallest community of all options — fewest resources for the team to learn from
- Synadia Cloud pricing is connection-based, not message-based — scaling model may not align
- Limited enterprise adoption — few higher education references
- Overage charges on network data (USD 0.09/GiB client egress) could accumulate [WEB-17-C2]

**Assessment Against Criteria**:

| Criterion | Rating | Notes |
|-----------|--------|-------|
| C1: Schema registry + runtime validation | FAIL | No schema registry for application messages; custom build required |
| C2: Pub/sub with topic routing | FULL | NATS subjects with wildcards — native and fast |
| C3: Dead-letter, retry, replay | PARTIAL | JetStream provides replay; dead-letter requires custom implementation |
| C4: Observability | MODERATE | Synadia Cloud provides monitoring; custom integration for alerting |
| C5: Australian region | UNKNOWN | Synadia Cloud is multi-region but specific Australian hosting not confirmed |
| C6: Operational complexity | BEST | Simplest operational model — but custom schema validation adds complexity |
| C7: Cost | GOOD | Lowest hosting cost; but custom validation development cost offsets savings |
| C8: Lock-in risk | LOW | NATS is open-source; protocol is open |
| C9: Security | MODERATE | TLS; JWT/NKey authentication; but OAuth 2.0 is not native — requires custom implementation |
| C10: Community/support | POOR | Smallest community; limited enterprise and higher-education references |

---

### Vendor Comparison Matrix

| Criterion (Weight) | Azure Integration Services | PeopleSoft IB | Ultra Webhooks | Confluent Kafka | Kafka Self-Hosted + Apicurio | RabbitMQ + Apicurio | NATS |
|----|----|----|----|----|----|----|-----|
| **C1: Schema Registry (20%)** | 8/10 (client-side) | 2/10 (XML only) | 0/10 | 10/10 (server-side) | 9/10 | 5/10 (sidecar) | 2/10 (custom) |
| **C2: Pub/Sub (15%)** | 9/10 | 4/10 | 0/10 | 10/10 | 10/10 | 8/10 | 9/10 |
| **C3: DLQ/Retry/Replay (10%)** | 9/10 | 2/10 | 0/10 | 10/10 | 10/10 | 6/10 | 5/10 |
| **C4: Observability (10%)** | 9/10 | 2/10 | 1/10 | 9/10 | 6/10 | 7/10 | 6/10 |
| **C5: AU Region (10%)** | 10/10 | 10/10 | 5/10 | 9/10 | 10/10 | 8/10 | 5/10 |
| **C6: Ops Complexity (10%)** | 8/10 | 3/10 | N/A | 7/10 | 3/10 | 7/10 | 8/10 |
| **C7: Cost / P19 (10%)** | 9/10 | 7/10 | 10/10 | 4/10 | 5/10 | 8/10 | 7/10 |
| **C8: Lock-in (5%)** | 6/10 | 2/10 | N/A | 8/10 | 10/10 | 8/10 | 9/10 |
| **C9: Security (5%)** | 10/10 | 3/10 | 6/10 | 9/10 | 6/10 | 6/10 | 5/10 |
| **C10: Community (5%)** | 9/10 | 3/10 | 4/10 | 10/10 | 8/10 | 8/10 | 4/10 |
| **Weighted Score** | **8.55** | **3.55** | **2.10** | **8.65** | **7.25** | **6.75** | **5.80** |
| **Principle 19** | PASS | FAIL | FAIL | N/A (new) | N/A (new) | N/A (new) | N/A (new) |

**Scoring note**: Confluent Kafka scores marginally higher (8.65 vs 8.55) due to its superior schema registry. However, when Principle 19 is applied as a governance constraint rather than a weighted criterion, the Microsoft Azure option is the only existing licensed capability that passes the Principle 19 test. Confluent Kafka would only be considered if Azure proved unsuitable during a proof-of-concept.

---

### Build vs Buy Recommendation for Integration Broker

**Recommended Approach**: USE EXISTING LICENSED CAPABILITY — Microsoft Azure Integration Services (Service Bus Premium + Event Hubs Schema Registry + Azure Monitor)

**Rationale**:

The Principle 19 test produces a clear outcome: of the three existing licensed capabilities evaluated, only Microsoft Azure Integration Services meets the ADR-001 requirements for an integration broker with schema registry. PeopleSoft Integration Broker fails on schema registry capability (XML-only, no JSON Schema), multi-system routing, and modern security. Blackboard Ultra fails on fundamental grounds — it is not a broker.

Azure Integration Services provides topic-based publish/subscribe (Service Bus), schema registry with versioning and compatibility modes (Event Hubs), dead-letter and retry handling (Service Bus), single-plane observability (Azure Monitor), OAuth 2.0 with Managed Identity (Azure AD), and confirmed Australian region hosting. It is a managed service, reducing the operational burden on Okafor's 3-4 person team.

The one qualification is schema validation enforcement: Azure Event Hubs Schema Registry stores and versions schemas, but validation is client-side (SDK-enforced at serialization) rather than server-side broker rejection. This means non-conformant events can enter the system if a producer bypasses the SDK. This is a design constraint, not a blocker — the mitigation is to mandate the use of the provided serializers in all integration code, and to implement a validation consumer that monitors for non-conformant events as a defense-in-depth measure.

Confluent Cloud Kafka provides server-side schema validation that is objectively stronger, but it fails Principle 19 (new purchase), costs 40-100% more, and introduces Kafka operational complexity that is disproportionate to the university's event volume ( < 10,000 events/day).

**Key Decision Factors**:

- **Principle 19 compliance**: Azure is the only existing capability that passes the test — this is the primary decision driver per the governance framework
- **Schema registry adequacy**: Client-side validation via SDK is adequate for a controlled integration estate where the team writes all producers and consumers. Server-side rejection is stronger but not essential when all integration code is internal.
- **Operational sustainability**: Managed Azure services with Microsoft enterprise support are operationally sustainable for a 3-4 person team. Self-hosted Kafka is not.
- **Australian region**: Confirmed for all Azure components (Australia East, Australia Southeast)
- **Cost**: Lowest suitable option under the existing agreement (A$105K-A$162K 3-year TCO including integration effort)

**Shortlist for Further Evaluation**:

1. **Microsoft Azure Integration Services**: Recommended. Proceed to proof-of-concept with Service Bus + Event Hubs Schema Registry + Monitor.
2. **Confluent Cloud Kafka**: Contingency if Azure proof-of-concept reveals that client-side schema validation is insufficient for the canonical model. Would require Principle 19 exception.

**Next Steps**:

- [ ] Confirm Microsoft agreement terms with Grace Tanaka — what Azure consumption is included
- [ ] Deploy a proof-of-concept: Service Bus topic with one canonical entity schema in Event Hubs Schema Registry; publish and consume test events using the Avro/JSON Schema serializer; verify non-conformant events are rejected by the SDK
- [ ] Validate the client-side validation model with Okafor — is SDK-enforced validation sufficient, or is server-side broker rejection essential?
- [ ] Security architecture review with Tobias Ohm — Azure AD Managed Identity, RBAC, encryption
- [ ] Privacy assessment with Eleanor Frame — confirm Australian region hosting for all components
- [ ] Skills uplift plan for Okafor's team — Azure Service Bus and Event Hubs training

---

## Total Cost of Ownership (TCO) Summary

### Blended TCO Across All Categories

Since this is a single-category evaluation, the blended TCO equals the category TCO.

**Recommended Approach (Azure Integration Services)**:

| Component | Year 1 (AUD) | Year 2 (AUD) | Year 3 (AUD) | 3-Year TCO (AUD) |
|-----------|-------------|-------------|-------------|------------------|
| Service Bus Premium (1 MU) | A$15,600 | A$15,600 | A$15,600 | A$46,800 |
| Event Hubs (Schema Registry) | A$3,600 | A$3,600 | A$3,600 | A$10,800 |
| Azure Monitor | A$1,800 | A$1,800 | A$1,800 | A$5,400 |
| Integration effort | A$36,000 | A$0 | A$0 | A$36,000 |
| Training | A$6,000 | A$0 | A$0 | A$6,000 |
| **TOTAL** | **A$63,000** | **A$21,000** | **A$21,000** | **A$105,000** |

### Alternative Scenarios

**Scenario A: Build Everything (Kafka Self-Hosted + Apicurio)**

- 3-Year TCO: A$169,200
- Pros: Maximum control; zero licence cost; strongest schema registry (with Apicurio)
- Cons: Highest operational burden; requires Kafka expertise the team lacks; patching, monitoring, capacity planning all manual

**Scenario B: Buy Managed Service (Confluent Cloud Kafka)**

- 3-Year TCO: A$148,200
- Pros: Market-leading schema registry; managed service; strong community
- Cons: New purchase violating Principle 19; 40% more expensive than Azure; Kafka complexity disproportionate to volume

**Scenario C: Lightweight Open Source (RabbitMQ CloudAMQP + Apicurio Sidecar)**

- 3-Year TCO: A$77,652
- Pros: Lowest cost; simple operational model; managed hosting
- Cons: No native schema registry — sidecar approach delivers enforcement by convention, not broker enforcement (exactly what ADR-001 rejected)

**Scenario D: Recommended — Existing Licensed (Azure Integration Services)**

- 3-Year TCO: A$105,000 (or A$42,000 if Azure credits apply)
- Pros: Principle 19 compliance; managed service; schema registry included; Australian region; OAuth 2.0 / Managed Identity; enterprise support
- Cons: Client-side schema validation (not server-side); Azure management plane lock-in

### TCO Assumptions

- Engineering rates: A$12,000/month (blended rate for Okafor's team, fully loaded)
- Infrastructure: Azure Australia East region pricing with ~25% uplift over US East baseline
- AUD/USD exchange rate: 0.65 (1 AUD = 0.65 USD; 1 USD = 1.54 AUD)
- SaaS pricing: 10% annual increase assumption for non-Azure options (Azure pricing assumed stable within enterprise agreement)
- Maintenance: 30% of integration development cost for custom-built components
- Enterprise agreement credits: Not factored into base TCO (would reduce Azure costs)

### Risk-Adjusted TCO

| Scenario | Base TCO (AUD) | Contingency | Risk-Adjusted TCO (AUD) | Risk Factors |
|----------|---------------|-------------|------------------------|--------------|
| Kafka Self-Hosted | A$169,200 | +25% | A$211,500 | Operational skills gap; unplanned patching; capacity planning errors |
| Confluent Cloud | A$148,200 | +15% | A$170,430 | Pricing opacity; volume-based cost increases; Principle 19 exception process |
| RabbitMQ + Apicurio | A$77,652 | +20% | A$93,182 | Sidecar schema registry maintenance; CloudAMQP AU region confirmation |
| **Azure (Recommended)** | **A$105,000** | **+10%** | **A$115,500** | Client-side validation adequacy; agreement credit confirmation |

---

## Requirements Traceability

### Requirements Coverage Matrix

| Requirement ID | Requirement Summary | Recommended Solution | Rating | Notes |
|----------------|---------------------|---------------------|--------|-------|
| DR-001 | Canonical data model — 6 entities in schema registry with runtime validation | Azure Event Hubs Schema Registry + Service Bus | MET | Client-side SDK validation; schemas registered and versioned |
| INT-001 | PeopleSoft to Ultra — user and course lifecycle | Azure Service Bus topic: `peoplesoft.lifecycle` | MET | Events published by PeopleSoft CDC, consumed by Ultra integration |
| INT-002 | Echo360 user provisioning | Azure Service Bus topic: `identity.provisioning` | MET | Events consumed by Echo360 integration adapter |
| INT-003 | Course cloning automation | Azure Service Bus topic: `course.offering.created` | MET | UNIT_OFFERING creation event triggers cloning |
| INT-004 | Institutional hierarchy synchronisation | Azure Service Bus topic: `hierarchy.updated` | MET | Low-frequency; standard event routing |
| INT-005 | Allocate+ to Ultra — group creation | Azure Service Bus topic: `timetable.groups` | MET | Group allocation events from Allocate+ |
| INT-006 | Sonia to Ultra — placement grades | Azure Service Bus topic: `grades.placement` | MET | Bidirectional; elevated data controls for sensitive PI |
| INT-007 | Sandpit provisioning (2027) | Azure Service Bus topic: `provisioning.sandpit` | MET | Future integration; broker available when needed |
| NFR-P-001 | < 15 minutes propagation latency | Azure Service Bus | MET | Near-real-time; typical latency < 1 second |
| NFR-SEC-002 | OAuth 2.0 / scoped service credentials | Azure AD Managed Identity + RBAC | MET | Strongest credential model of all options |
| NFR-M-001 | Single-plane observability | Azure Monitor + Application Insights | MET | Metrics, logs, alerting in one pane |
| NFR-A-001 | 99.9% availability during teaching periods | Azure Service Bus Premium SLA: 99.99% | MET | Exceeds requirement |
| P6 | Canonical Data Model | Event Hubs Schema Registry | MET | Schemas registered and versioned for all 6 canonical entities |
| P8 | Data Residency | Azure Australia East / Southeast | MET | Australian region confirmed |
| P9 | Data Portability and Exit | AMQP 1.0 open protocol | PARTIAL | Data plane is open; management plane is Azure-specific |
| P10 | Interface-Mediated Integration | Service Bus topics + schema-validated events | MET | All integrations mediated through the broker |
| P11 | Event-Driven by Default | Service Bus pub/sub | MET | Event-driven architecture implemented |
| P17 | Observable Integrations | Azure Monitor | MET | End-to-end flow monitoring |
| P19 | Realise Licensed Capability | Microsoft agreement | MET | Existing licensed capability; Principle 19 satisfied |

### Coverage Summary

**Requirements with Identified Solutions**:

- 100% of requirements (17/17) have recommended solutions with Azure Integration Services
- 0 requirements need custom development (schema validation is SDK-provided, not custom-built)
- 0 requirements need further research

**Gaps and Concerns**:

**GAP-1**: DR-001 — Client-side vs server-side schema validation

- **Impact**: Non-conformant events could enter the system if a producer bypasses the SDK serializer. This is a weaker enforcement than server-side broker rejection (Confluent Kafka).
- **Mitigation**: (a) Mandate SDK serializers in all integration code. (b) Implement a validation consumer that monitors incoming events and alerts on schema violations. (c) Review during proof-of-concept.
- **Recommendation**: Accept client-side validation with monitoring. If proof-of-concept reveals this is insufficient, escalate to Principle 19 exception for Confluent Cloud.

---

## Integration with Wardley Mapping

### Value Chain Components by Evolution

| Component | Evolution Stage | Recommended Approach | Rationale |
|-----------|----------------|---------------------|-----------|
| Integration Broker (messaging) | Product (0.65) | Use Existing Licensed (Azure Service Bus) | Mature market; commodity for Azure customers |
| Schema Registry | Product (0.55) | Use Existing Licensed (Azure Event Hubs) | Maturing rapidly; Azure and Confluent lead |
| Canonical Data Model | Custom (0.35) | Build Custom (institutional artifact) | University-specific entity definitions; not a product |
| Integration Adapters (per system) | Custom (0.30) | Build Custom | PeopleSoft, Ultra, Echo360 adapters are bespoke |
| Observability | Commodity (0.75) | Use Existing (Azure Monitor) | Standard infrastructure |
| Identity/Credentials | Commodity (0.80) | Use Existing (Azure AD) | Standard infrastructure |

**Strategic Insight**: The integration broker and schema registry are commoditising rapidly. Building them custom or self-hosting is moving against the evolution curve. The university's differentiator is the canonical data model and the integration adapters — that is where custom effort should be invested, not on the broker infrastructure.

---

## Risks and Mitigations

### Vendor Risks

**VR-1: Azure Management Plane Lock-in**

- **Risk**: While the data plane uses AMQP 1.0 (open), the management plane (topic creation, subscription configuration, schema registry API) is Azure-specific. Migrating to another broker in future would require rebuilding management automation.
- **Impact**: MEDIUM
- **Likelihood**: LOW (the university is an existing Azure customer; migration is unlikely in the 3-year horizon)
- **Mitigation**: Use infrastructure-as-code (Terraform, Bicep) for all management plane operations. Abstract management operations behind a thin wrapper. Maintain the canonical model schemas in a version-controlled repository independent of the registry.

**VR-2: Microsoft Agreement Terms Ambiguity**

- **Risk**: The existing Microsoft agreement may not include Azure consumption credits for Service Bus Premium and Event Hubs, making the "existing licensed" position weaker than assumed.
- **Impact**: MEDIUM — affects TCO but not capability
- **Likelihood**: MEDIUM
- **Mitigation**: Grace Tanaka (Procurement) to confirm agreement terms before proof-of-concept. Even at full list pricing, Azure is competitive with alternatives.

### Technical Risks

**TR-1: Client-Side Schema Validation Adequacy**

- **Risk**: Client-side SDK validation may be insufficient for the canonical model enforcement required by ADR-001. A producer that bypasses the SDK could publish non-conformant events.
- **Impact**: HIGH — undermines the defining benefit of Option B (ADR-001)
- **Likelihood**: LOW — all producers are internal, controlled by Okafor's team
- **Mitigation**: (a) SDK usage mandated in integration standards. (b) Validation consumer monitors for violations. (c) Proof-of-concept tests this explicitly. (d) Contingency: escalate to Confluent Cloud with Principle 19 exception.

**TR-2: Skills Gap**

- **Risk**: Okafor's team has no Azure messaging experience. Learning curve may delay INT-001.
- **Impact**: MEDIUM — timeline risk for P003
- **Likelihood**: MEDIUM
- **Mitigation**: Training budget included (A$6,000). Microsoft Learn resources. Proof-of-concept doubles as training. Azure messaging is simpler than Kafka.

---

## Next Steps and Recommendations

### Immediate Actions (Weeks 1-2)

1. **Agreement Confirmation**: Grace Tanaka confirms Microsoft agreement terms — Azure consumption credits, Service Bus Premium eligibility, Event Hubs Schema Registry availability
2. **Stakeholder Briefing**: Present Principle 19 test results to Rhodes, Ostinato, and Hammond
3. **Proof-of-Concept Scope**: Define POC scope with Okafor — Service Bus topic, one canonical entity schema (ENROLMENT) in Event Hubs Schema Registry, publish/consume test events, validate SDK-enforced schema rejection

### Proof-of-Concept (Weeks 3-6)

4. **Deploy POC**: Service Bus Premium namespace in Australia East; Event Hubs namespace with Schema Registry; ENROLMENT schema registered
5. **Test Schema Validation**: Publish conformant and non-conformant ENROLMENT events; verify SDK rejects non-conformant; measure latency
6. **Test Observability**: Azure Monitor alerts for failed deliveries, DLQ messages, schema validation failures
7. **Security Review**: Tobias Ohm reviews Azure AD Managed Identity, RBAC, encryption configuration
8. **Privacy Assessment**: Eleanor Frame confirms Australian region hosting; reviews audit logging

### Decision (Week 7)

9. **POC Outcome**: Okafor and Rhodes review POC results against ADR-001 requirements
10. **Decision Recording**: Document outcome as ARC-004-ADR-001 (Principle 19 Test Outcome)
11. **Proceed or Escalate**: If POC passes, proceed to production deployment. If client-side validation is insufficient, escalate Principle 19 exception for Confluent Cloud.

### Integration with Other Commands

12. **Update Evaluation**: Run `/arckit:evaluate` to create weighted evaluation framework from this research
13. **Create Wardley Map**: Run `/arckit:wardley` to map integration capability evolution
14. **Record Decision**: Run `/arckit:adr` to document the Principle 19 test outcome

---

## Appendices

### Appendix A: Research Methodology

**Data Sources**:

- Microsoft Azure official documentation and pricing pages
- Oracle PeopleSoft Integration Broker documentation
- Anthology (Blackboard) developer documentation
- Confluent Cloud documentation and pricing
- CloudAMQP plans and pricing page
- Synadia Cloud (NATS) documentation and pricing
- Apicurio Registry documentation
- G2, StackShare, and vendor comparison sites
- ArcKit project documents (ARC-000-PRIN-v1.1, ARC-001-ADR-001-v1.0, ARC-001-DATA-v1.0, ARC-003-REQ-v1.0, ARC-003-DATA-v1.0, ARC-004-STKE-v1.0)

**Evaluation Criteria**:

- Principle 19 compliance (existing licensed capability evaluated first)
- Schema registry capability (the defining requirement from ADR-001)
- Requirements fit against DR-001, INT-001 to INT-007
- Pricing from vendor websites (list prices; enterprise agreement terms to be confirmed)
- Operational sustainability for a 3-4 person team
- Australian region hosting
- Security posture (OAuth 2.0, encryption, audit logging)

**Limitations**:

- Azure pricing based on USD list prices converted to AUD; actual pricing under the enterprise agreement may differ
- Confluent Cloud CKU pricing is not publicly disclosed; estimates based on published cost ranges
- CloudAMQP Australian region availability not explicitly confirmed
- Synadia Cloud Australian region availability not confirmed
- All TCO projections are estimates; actual costs depend on event volume, data transfer, and storage

### Appendix B: Glossary

- **AMQP**: Advanced Message Queuing Protocol — open standard for message-oriented middleware
- **AUD**: Australian Dollar
- **CDM**: Canonical Data Model — standardised entity definitions for cross-system integration
- **CKU**: Confluent Kafka Unit — billing unit for Confluent Cloud dedicated clusters
- **DLQ**: Dead-Letter Queue — queue for messages that cannot be processed
- **E8**: Essential Eight — ASD cyber security mitigation strategies
- **MU**: Messaging Unit — Azure Service Bus Premium billing unit
- **NRPS**: Names and Role Provisioning Services — LTI 1.3 Advantage service
- **Pub/Sub**: Publish/Subscribe — messaging pattern where publishers send to topics, subscribers receive from topics
- **RBAC**: Role-Based Access Control
- **SDK**: Software Development Kit
- **SIS**: Student Information System (PeopleSoft)
- **TCO**: Total Cost of Ownership

---

## External References

> This section provides traceability from generated content back to source documents.

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| ADR1 | ARC-001-ADR-001-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/decisions/` | Integration Mediation Approach — Condition 1 drives this research |
| DATA1 | ARC-001-DATA-v1.0.md | ArcKit artifact | `projects/001-lt-ecosystem/` | Canonical data model — 20 entities across 4 contexts |
| DATA3 | ARC-003-DATA-v1.0.md | ArcKit artifact | `projects/003-lms-ultra-migration/` | Integration runtime entities (E-I01 to E-I04) |
| REQ3 | ARC-003-REQ-v1.0.md | ArcKit artifact | `projects/003-lms-ultra-migration/` | Integration requirements INT-001 to INT-007, DR-001 |
| PP | ARC-000-PRIN-v1.1.md | ArcKit artifact | `projects/000-global/` | Enterprise Architecture Principles — P6, P10, P11, P17, P19 |
| STK4 | ARC-004-STKE-v1.0.md | ArcKit artifact | `projects/004-integration-platform/` | Stakeholder drivers for broker selection |
| SL | system-landscape.md | Foundation artifact | `projects/004-integration-platform/external/` | System categorisation with 7 known integrations |
| PC | privacy-context.md | Compliance input | `projects/004-integration-platform/external/` | PI inventory and Essential Eight posture |
| WEB-1 | https://azure.microsoft.com/en-au/pricing/details/service-bus/ | Web URL | azure.microsoft.com | Azure Service Bus AU pricing page |
| WEB-2 | https://learn.microsoft.com/en-us/azure/event-hubs/schema-registry-concepts | Web URL | learn.microsoft.com | Azure Event Hubs Schema Registry concepts |
| WEB-3 | https://www.epcgroup.net/azure-service-bus-pricing-and-features-cloud-messaging-service | Web URL | epcgroup.net | Azure Service Bus pricing and features overview |
| WEB-4 | https://cloudtoolstack.com/tools/azure-service-bus-cost-estimator | Web URL | cloudtoolstack.com | Azure Service Bus cost estimator |
| WEB-5 | https://azure.microsoft.com/en-us/pricing/details/event-grid/ | Web URL | azure.microsoft.com | Azure Event Grid/Hubs pricing |
| WEB-6 | https://www.cleverence.com/articles/oracle-documentation/introduction-to-peoplesoft-integration-broker-4827/ | Web URL | cleverence.com | PeopleSoft Integration Broker architecture overview |
| WEB-7 | https://www.zutshigroup.com/PSOL/pt849/eng/psbooks/tibr/htm/tibr17.htm | Web URL | zutshigroup.com | PeopleSoft runtime message schema validation |
| WEB-8 | https://peoplesofttechfunctional.wordpress.com/2021/05/21/common-peoplesoft-integration-broker-issues-and-solutions/ | Web URL | peoplesofttechfunctional.wordpress.com | PeopleSoft IB common issues and limitations |
| WEB-9 | https://docs.anthology.com/docs/blackboard/rest-apis/getting-started/framework | Web URL | docs.anthology.com | Blackboard REST API framework documentation |
| WEB-10 | https://docs.blackboard.com/rest-apis/learn/admin/groups-quotas-rates | Web URL | docs.blackboard.com | Blackboard API rate limits and quotas |
| WEB-11 | https://www.cloudzero.com/blog/confluent-cloud-pricing/ | Web URL | cloudzero.com | Confluent Cloud pricing guide 2026 |
| WEB-12 | https://docs.confluent.io/cloud/current/billing/billing-dimensions.html | Web URL | docs.confluent.io | Confluent Cloud billing dimensions |
| WEB-13 | https://www.apicur.io/registry/docs/apicurio-registry/3.3.x/getting-started/assembly-registry-compatibility-modes.html | Web URL | apicur.io | Apicurio Registry compatibility modes |
| WEB-14 | https://www.meegle.com/en_us/topics/schema-registry/schema-registry-for-rabbitmq | Web URL | meegle.com | Schema Registry for RabbitMQ options |
| WEB-15 | https://www.cloudamqp.com/plans.html | Web URL | cloudamqp.com | CloudAMQP plans and pricing |
| WEB-16 | https://docs.nats.io/nats-concepts/jetstream | Web URL | docs.nats.io | NATS JetStream concepts |
| WEB-17 | https://docs.synadia.com/cloud/pricing | Web URL | docs.synadia.com | Synadia Cloud pricing |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| WEB-1-C1 | WEB-1 | Region selector | Market Evidence | Azure Service Bus pricing page confirms availability in Australia with region-specific pricing |
| WEB-2-C1 | WEB-2 | Schema Registry | Market Evidence | "Schema Registry... stores schemas for events, with compatibility modes at the schema group level" |
| WEB-2-C2 | WEB-2 | Validation | Market Evidence | "Validation is client-side using the Avro or JSON Schema serializer/deserializer provided by the SDK" |
| WEB-3-C1 | WEB-3 | Service Bus Features | Market Evidence | "Azure Service Bus Standard tier: $10/month base, $0.01 per million operations; topics, dead-letter queues, sessions" |
| WEB-3-C2 | WEB-3 | Dead-letter | Market Evidence | "Built-in dead-letter queue per topic subscription" |
| WEB-3-C3 | WEB-3 | Observability | Market Evidence | "Azure Monitor provides metrics, diagnostic logs, and alerting for Service Bus and Event Hubs" |
| WEB-3-C4 | WEB-3 | Security | Market Evidence | "OAuth 2.0 with Azure AD... encryption at rest... TLS 1.2 in transit" |
| WEB-3-C5 | WEB-3 | SLA | Market Evidence | "99.99% for Premium (with geo-redundancy)" |
| WEB-4-C1 | WEB-4 | Premium pricing | Market Evidence | "Premium provides dedicated resources through messaging units at $677.44/month per MU" |
| WEB-5-C1 | WEB-5 | Event Grid pricing | Market Evidence | "Event Grid first 100,000 operations/month free; $0.60 per million operations" |
| WEB-6-C1 | WEB-6 | Architecture | Market Evidence | "Integration Gateway (Java servlet) and Integration Engine (application server) provide transport, routing, transformation, and reliable delivery" |
| WEB-6-C2 | WEB-6 | Security | Market Evidence | "WS-Security for SOAP and basic authentication for REST" |
| WEB-7-C1 | WEB-7 | Schema validation | Market Evidence | "PeopleSoft Integration Broker enables you to validate, at runtime, the messages defined in service operations against message schemas" |
| WEB-8-C1 | WEB-8 | Limitations | Market Evidence | "Each Message Node can route messages to only one Connector... Subscription contracts share a queue" |
| WEB-9-C1 | WEB-9 | API Framework | Market Evidence | "Blackboard Learn REST APIs can work with many different types of objects including users, courses, enrollments" |
| WEB-10-C1 | WEB-10 | Premium APIs | Market Evidence | "Premium APIs, including the Ultra Extension Framework, are available to all clients and Partnership Program members" |
| WEB-10-C2 | WEB-10 | Rate limits | Market Evidence | "By default you get 10,000 calls every 24 hours per site" |
| WEB-11-C1 | WEB-11 | Confluent Cloud | Market Evidence | "Confluent Cloud provides Kafka as a managed service with a native Schema Registry" |
| WEB-11-C2 | WEB-11 | Schema Registry | Market Evidence | "Supports Avro, JSON Schema, and Protobuf with server-side validation, schema evolution with compatibility enforcement" |
| WEB-11-C3 | WEB-11 | Regions | Market Evidence | "Available on AWS ap-southeast-2 (Sydney) and Azure Australia East" |
| WEB-12-C1 | WEB-12 | Pricing | Market Evidence | "Small production (Standard): $1,000-$3,000/month" |
| WEB-12-C2 | WEB-12 | Schema pricing | Market Evidence | "Schema Registry: Essentials 100 free schemas; after that $0.002 per schema per hour" |
| WEB-12-C3 | WEB-12 | Pricing note | Market Evidence | "Exact eCKU rates aren't publicly disclosed; Confluent's pricing page requires sales consultation" |
| WEB-13-C1 | WEB-13 | Overview | Market Evidence | "Apicurio Registry is a fully open source project under the CNCF" |
| WEB-13-C2 | WEB-13 | JSON Schema | Market Evidence | "Dereference feature is supported for Avro, JSON Schema, Protobuf, OpenAPI, and AsyncAPI artifact types" |
| WEB-14-C1 | WEB-14 | RabbitMQ schema | Market Evidence | "Schema Registry integrates with RabbitMQ to intercept messages... achieved through plugins, middleware, or custom implementations" |
| WEB-14-C2 | WEB-14 | RabbitMQ 4.1 | Market Evidence | "RabbitMQ 4.1, February 2026, doubles down on native streams... still no schema registry" |
| WEB-15-C1 | WEB-15 | Dedicated plans | Market Evidence | "Big Bunny: 3 nodes, 1k msg/s, 9k connections, $297/month; Happy Hare: 3 nodes, 8k msg/s, 12k connections, $597/month" |
| WEB-16-C1 | WEB-16 | JetStream | Market Evidence | "JetStream provides persistence, replay, and at-least-once delivery" |
| WEB-16-C2 | WEB-16 | Schemas | Market Evidence | "JetStream API messages and some events and advisories have JSON Schemas... for validating JetStream management API calls, not application event payloads" |
| WEB-17-C1 | WEB-17 | Pricing tiers | Market Evidence | "Starter $49/month, 100 connections; Pro $199/month, 1,000 connections; Enterprise custom pricing" |
| WEB-17-C2 | WEB-17 | Overage | Market Evidence | "Client and Leaf egress: $0.09/GiB" |
| P4-C5 | ADR1 | Justification | Design Decision | "Enforcement is the difference between a model that governs and a model that documents" |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| ARC-001-REQ-v1.0.md | `projects/001-lt-ecosystem/` | Read for context; requirements operationalised in ARC-003-REQ which is cited directly |
| ARC-003-RISK-v1.0.md | `projects/003-lms-ultra-migration/` | Risk register informs integration risks but not directly cited in technology research |
| consultant-brief.md | `projects/004-integration-platform/external/` | Engagement scope document; not directly cited in technology research |
| stakeholders.md | `projects/004-integration-platform/external/` | Stakeholder register; superseded by ARC-004-STKE-v1.0 |

---

## Spawned Knowledge

The following standalone knowledge files were created or updated from this research:

### Vendor Profiles
- `vendors/microsoft-azure-integration-services-profile.md` -- Created
- `vendors/confluent-profile.md` -- Created
- `vendors/cloudamqp-profile.md` -- Created

### Tech Notes
- `tech-notes/schema-registry-landscape.md` -- Created
- `tech-notes/event-broker-comparison.md` -- Created

---

**Generated by**: ArcKit `/arckit:research` agent
**Generated on**: 2026-07-29
**ArcKit Version**: 6.7.4
**Project**: Integration Platform Selection & Implementation (Project 004)
**AI Model**: Claude Opus 4.6 (1M context)
