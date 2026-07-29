# Tech Note: Event Broker Comparison for Higher Education Integration (2026)

> **Template Origin**: Official | **ArcKit Version**: 6.7.4 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | TN-EBC |
| **Document Type** | Tech Note |
| **Project** | 004-integration-platform |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-29 |
| **Last Modified** | 2026-07-29 |
| **Owner** | Sam Okafor, Integration Architect |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-29 | ArcKit AI | Initial creation from `/arckit:research` agent | PENDING | PENDING |

---

## Summary

This note compares six event broker options for a higher education integration use case characterised by low event volume ( < 10,000 events/day), 7 integrations across heterogeneous systems (SIS, LMS, capture platform, timetabling, placement management), a 3-4 person operations team, and a requirement for schema registry with runtime validation. The comparison is relevant to any university or institution evaluating event-driven integration architecture.

## Key Findings

### Comparative Matrix

| Feature | Azure Service Bus + Event Hubs | Apache Kafka (Confluent Cloud) | Apache Kafka (Self-Hosted) | RabbitMQ | NATS |
|---------|------|------|------|------|------|
| **Messaging model** | Topics + subscriptions (Service Bus); partitioned streams (Event Hubs) | Partitioned log (topics + consumer groups) | Partitioned log (topics + consumer groups) | Exchanges + queues | Subjects with wildcard routing |
| **Protocol** | AMQP 1.0, HTTP | Kafka binary protocol | Kafka binary protocol | AMQP 0.9.1, MQTT, STOMP | NATS protocol |
| **Native schema registry** | YES (Event Hubs) | YES (Confluent) | NO (requires Apicurio or Confluent) | NO | NO |
| **Schema validation** | Client-side SDK | Server-side producer rejection | Depends on registry | Application-level only | Application-level only |
| **Dead-letter queue** | Built-in (per subscription) | Dead-letter topic (configurable) | Dead-letter topic (configurable) | Dead-letter exchange | Custom implementation |
| **Message replay** | Event Hubs: full replay; Service Bus: limited | Full replay from any offset | Full replay from any offset | Streams (RabbitMQ 4.1+) | JetStream replay |
| **Operational complexity (3-4 people)** | LOW (managed) | MEDIUM (managed) | HIGH (self-hosted) | LOW-MEDIUM | LOW |
| **Australian region** | YES | YES (AWS/Azure Sydney) | YES (Azure VMs) | Probable (CloudAMQP) | Unconfirmed |
| **3-year TCO (AUD, managed)** | A$63K-105K | A$148K-360K | A$169K (self-hosted) | A$78K (CloudAMQP) | A$86K (Synadia) |
| **Best for** | Microsoft-agreement customers; general enterprise messaging | High-throughput event streaming; strong schema enforcement | Maximum control; Kafka expertise available | Simple messaging; cost-sensitive | Ultra-lightweight; cloud-native microservices |

### Operational Complexity Assessment for Small Teams

For a 3-4 person integration team with no existing middleware experience:

1. **Azure Service Bus (managed)**: Lowest operational burden. Team learns Azure Portal, Azure CLI, and AMQP client libraries. No infrastructure to manage. Microsoft Learn provides structured training paths. Recommended for teams new to middleware.

2. **RabbitMQ (CloudAMQP managed)**: Low operational burden for the broker itself. AMQP is well-documented with client libraries in all major languages. However, the lack of native schema registry means additional operational surface if Apicurio is added.

3. **NATS (Synadia Cloud managed)**: Simplest broker operationally, but smallest ecosystem and fewest learning resources. Custom schema validation development required. Not recommended for teams that need schema enforcement.

4. **Confluent Cloud Kafka (managed)**: Medium operational burden. Kafka concepts (partitions, consumer groups, offsets, rebalancing) have a steeper learning curve than Service Bus or RabbitMQ. However, Confluent provides excellent training and documentation.

5. **Self-hosted Kafka**: Not recommended for small teams. Cluster management (ZooKeeper/KRaft, broker configuration, topic management, capacity planning, security hardening, patching) requires dedicated operational capacity the team cannot afford.

### PeopleSoft Integration Broker Assessment

PeopleSoft Integration Broker is commonly considered as a candidate at institutions running PeopleSoft as their SIS. The assessment across multiple evaluations consistently finds:

- **Suitable for**: PeopleSoft-to-PeopleSoft messaging; PeopleSoft outbound REST/SOAP calls
- **Not suitable for**: General-purpose event broker serving non-PeopleSoft systems; modern schema registry requirements (JSON Schema, Avro); OAuth 2.0 service-to-service authentication; modern observability integration
- **Key limitation**: PeopleSoft-centric routing architecture; each message node routes to one connector; external systems cannot natively subscribe to PeopleSoft channels
- **Recommendation**: Use PeopleSoft Integration Broker as a **source adapter** (publishing change events from PeopleSoft to the central broker), not as the broker itself

## Relevance to Projects

- **004-integration-platform**: Direct input to broker selection decision
- **003-lms-ultra-migration**: Integration re-engineering depends on the broker selected in this project
- **Future projects**: Any project involving event-driven integration between university systems

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| *Multiple* | See ARC-004-RSCH-v1.0 | Research | `projects/004-integration-platform/research/` | Full research with citations |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| — | — | — | — | See ARC-004-RSCH-v1.0 for full citations |

---

**Generated by**: ArcKit `/arckit:research` agent
**Generated on**: 2026-07-29
**ArcKit Version**: 6.7.4
**Project**: Integration Platform Selection & Implementation (Project 004)
**Model**: Claude Opus 4.6 (1M context)
