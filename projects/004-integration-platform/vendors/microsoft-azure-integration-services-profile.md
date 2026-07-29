# Vendor Profile: Microsoft Azure Integration Services

> **Template Origin**: Official | **ArcKit Version**: 6.7.4 | **Command**: `/arckit:research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | VP-MAIS |
| **Document Type** | Vendor Profile |
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

## Overview

Microsoft Corporation is the global technology company behind the Azure cloud platform. Azure Integration Services is a suite of managed services for enterprise messaging, event streaming, API management, and workflow orchestration. For integration broker use cases, the relevant components are Azure Service Bus (enterprise messaging with queues and topics), Azure Event Hubs (event streaming with schema registry), and Azure Monitor (observability). The university holds an existing Microsoft enterprise agreement that covers Azure services.

## Products & Services

- **Azure Service Bus** — Enterprise messaging with queues and topics; AMQP 1.0 protocol; dead-letter queues; message sessions; scheduled delivery; auto-forwarding; subscription filters. Premium tier provides dedicated capacity via messaging units with 99.99% SLA.
- **Azure Event Hubs** — Event streaming platform with Schema Registry supporting Avro and JSON Schema; compatibility modes (backward, forward, full, none); schema versioning. Also supports Apache Kafka protocol via Event Hubs for Kafka.
- **Azure API Management** — API gateway and developer portal; not required for the broker use case but available within the suite.
- **Azure Monitor** — Observability platform with metrics, diagnostic logs, alerting, and Application Insights for distributed tracing. Single pane of glass for all Azure services.
- **Azure Active Directory** — Identity and access management; OAuth 2.0 with Managed Identity and service principals; Role-Based Access Control (RBAC).

## Pricing Model

- **Service Bus Basic**: USD $0.05 per million operations (no topics — queues only)
- **Service Bus Standard**: USD $10/month base + $0.01 per million operations (topics enabled)
- **Service Bus Premium**: USD ~$677/month per messaging unit (dedicated capacity; no per-operation charges)
- **Event Hubs Standard**: Per throughput unit + per million operations + schema registry included
- **Azure Monitor**: Log Analytics per GB ingested; basic alerting included

Enterprise agreement customers may receive Azure consumption credits that offset or eliminate these costs.

**Confidence**: HIGH (5+ data points from multiple sources)

## Australian Presence

- Australian data centres: YES — Australia East (Sydney), Australia Southeast (Melbourne)
- Service Bus Premium available in Australian regions: YES
- Event Hubs with Schema Registry available in Australian regions: YES

## Government Award History

> Not applicable. This is an Australian university, not a UK government entity. Microsoft holds significant Australian public sector presence including contracts with Australian universities and government agencies, but specific contract values are not publicly available in the same way as UK procurement notices.

## Strengths

- Existing enterprise agreement with the university — Principle 19 compliance
- Full suite of integration services (messaging, streaming, API management, observability) under one provider
- Managed service reduces operational burden for small teams
- AMQP 1.0 open protocol for the data plane reduces lock-in
- Schema Registry with compatibility modes and versioning
- OAuth 2.0 with Azure AD Managed Identity — strongest credential model
- 99.99% SLA for Service Bus Premium
- Extensive documentation, Microsoft Learn training resources, and enterprise support
- Australian region confirmed for all required services

## Weaknesses

- Schema validation is client-side (SDK-enforced) rather than server-side broker rejection — weaker than Confluent Kafka
- Management plane is Azure-specific — operational tooling is not portable
- Premium tier pricing is relatively expensive compared to open-source alternatives
- Pricing opacity under enterprise agreements requires procurement confirmation
- Azure-specific operational expertise required (Azure Portal, Azure CLI, ARM/Bicep templates)

## Projects Referenced In

- ARC-004-RSCH-v1.0 — Integration Platform Selection (Principle 19 Test) — **Recommended**

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| WEB-1 | https://azure.microsoft.com/en-au/pricing/details/service-bus/ | Web URL | azure.microsoft.com | Azure Service Bus AU pricing |
| WEB-2 | https://learn.microsoft.com/en-us/azure/event-hubs/schema-registry-concepts | Web URL | learn.microsoft.com | Event Hubs Schema Registry |
| WEB-3 | https://www.epcgroup.net/azure-service-bus-pricing-and-features-cloud-messaging-service | Web URL | epcgroup.net | Service Bus features and pricing |

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
