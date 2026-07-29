# Tech Note: Schema Registry Landscape (2026)

> **Template Origin**: Official | **ArcKit Version**: 6.7.4 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | TN-SRL |
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

A schema registry is a centralised repository for storing, versioning, and managing event schemas (Avro, JSON Schema, Protobuf) in event-driven architectures. It enforces data contracts between producers and consumers by validating event payloads against registered schemas at runtime. The landscape in 2026 includes four significant options: Confluent Schema Registry (market leader, server-side validation), Azure Event Hubs Schema Registry (managed Azure service, client-side SDK validation), Apicurio Registry (open-source, CNCF-hosted, broker-agnostic), and Karapace (open-source, Confluent API-compatible).

## Key Findings

- **Confluent Schema Registry** is the market leader with server-side validation (producer-side rejection of non-conformant events), full compatibility modes (backward, forward, full, none, and transitive variants), and support for Avro, JSON Schema, and Protobuf. It is tightly coupled to Kafka. Licensed under Confluent Community License (not fully open-source).

- **Azure Event Hubs Schema Registry** provides schema storage, versioning, and compatibility enforcement within the Azure ecosystem. However, validation is client-side — the SDK serializer/deserializer enforces schemas at the application layer, not at the broker. This is weaker than Confluent's server-side enforcement but adequate when all producers are controlled by the integration team.

- **Apicurio Registry** (CNCF) is the leading open-source schema registry. It supports Avro, JSON Schema, Protobuf, OpenAPI, AsyncAPI, GraphQL, WSDL, and XML Schema. It provides compatibility modes and is compatible with the Confluent Schema Registry API (allowing use of Confluent serializers). It can be paired with any message broker (Kafka, RabbitMQ, NATS, Service Bus) as a sidecar.

- **Schema validation enforcement models vary significantly**:
  - **Server-side (Confluent)**: The broker/registry rejects non-conformant events before they enter the topic. Strongest enforcement. Requires Kafka + Confluent Schema Registry.
  - **Client-side SDK (Azure Event Hubs)**: The SDK serializer validates against the registry at serialization time. Adequate when all producers are internal and use the SDK. A bypassed SDK allows non-conformant events.
  - **Application-level (Apicurio sidecar with RabbitMQ/NATS)**: Validation is implemented in application code using the registry API. Weakest enforcement — relies on developer discipline. This is "enforcement by convention."

- **JSON Schema vs Avro for canonical models**: JSON Schema is better for human readability and REST API integration; Avro is better for compact serialisation and schema evolution. For a higher education canonical model with 6 entities and low event volume, JSON Schema is the pragmatic choice due to readability and debugging ease.

- **Operational overhead**: Self-managing a schema registry (Apicurio or Confluent) alongside a self-hosted broker significantly increases operational surface. Managed options (Azure Event Hubs, Confluent Cloud) eliminate registry operations but introduce vendor dependency.

## Relevance to Projects

- **004-integration-platform**: Schema registry selection is the defining requirement for the integration broker. Azure Event Hubs Schema Registry selected (Principle 19 compliance); Confluent Schema Registry is the contingency if client-side validation proves insufficient.
- **003-lms-ultra-migration**: DR-001 requires canonical data model implementation — the schema registry is where the model becomes a runtime contract.

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| WEB-2 | https://learn.microsoft.com/en-us/azure/event-hubs/schema-registry-concepts | Web URL | learn.microsoft.com | Azure Event Hubs Schema Registry |
| WEB-13 | https://www.apicur.io/registry/docs/apicurio-registry/3.3.x/getting-started/assembly-registry-compatibility-modes.html | Web URL | apicur.io | Apicurio Registry compatibility modes |

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
