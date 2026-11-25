# FreightOps — Project Brief

## Overview

FreightOps is an operational shipment monitoring and exception management platform designed for small to medium-sized logistics companies (15–150 employees), including freight forwarders, importers, exporters and delivery providers.

The platform consolidates fragmented shipment information, detects operational discrepancies and uses automated AI workflows to investigate exceptions and recommend resolutions.

## Problem Statement

Logistics companies coordinate shipments using information distributed across carrier APIs, tracking portals, shipping documents, emails and internal systems.

When shipments deviate from their expected lifecycle, operations teams must manually gather information, investigate causes, coordinate stakeholders and determine appropriate actions.

This creates administrative overhead, delays resolution and increases the risk of financial loss and customer dissatisfaction.

## Mission

Reduce the operational and cognitive burden on logistics teams by automatically detecting problems, investigating their causes and providing actionable, evidence-backed recommendations while preserving human decision-making authority.

## Core Functional Requirements

- **Shipment management:** Create, retrieve and manage shipments throughout their lifecycle.
- **Event ingestion:** Receive, normalise and validate shipment events from multiple external sources.
- **State reconciliation:** Establish reliable shipment state despite missing, duplicate, conflicting or out-of-order events.
- **Exception detection:** Identify delays, missing documentation, inconsistent statuses and overdue milestones.
- **Automated investigation:** Gather relevant evidence, identify potential causes and generate structured findings using AI.
- **Resolution management:** Recommend actions, support operator approval and maintain an auditable resolution history.

## Automated AI Workflow

When an operational exception is detected, the system initiates an investigation workflow that:

1. Establishes the context of the exception.
2. Retrieves relevant shipment events, documents and communications.
3. Evaluates available evidence and identifies information gaps.
4. Iteratively retrieves additional information where necessary.
5. Establishes potential causes and downstream consequences.
6. Produces evidence-backed findings and recommended actions.
7. Presents findings for operator review.
8. Executes authorised actions and verifies outcomes where supported.

Deterministic application logic remains responsible for business rules, data integrity, permissions and authoritative shipment state.

## Non-Functional Requirements

- **Reliability:** Handle external service failures and partial workflow failures.
- **Consistency:** Maintain correct shipment state despite concurrent and repeated events.
- **Auditability:** Preserve event history, investigation evidence and resolution decisions.
- **Security:** Enforce data access boundaries and protect against prompt injection.
- **Observability:** Provide visibility into application behaviour, workflow execution and failures.
- **Testability:** Support independent testing of domain logic, integrations and AI workflows.
- **Cost efficiency:** Bound AI execution time, token consumption and investigation scope.

## Technical Stack

| Component | Technology |
|---|---|
| Backend | Go |
| HTTP API | net/http or Chi |
| Database | PostgreSQL |
| Database access | database/sql with pgx |
| Background processing | Go workers and job queues |
| AI integration | LLM API with structured outputs and tool calling |
| Observability | Structured logging, metrics and tracing |
| Testing | Go testing, httptest and AI evaluation datasets |
| Frontend (later milestone) | React and TypeScript |
| Local infrastructure | Docker Compose |

## Implementation Milestones

### Milestone 1 — Shipment Domain
- Domain models and lifecycle transitions.
- Event validation and state reconciliation.
- Table-driven unit tests.

### Milestone 2 — Application Backend
- HTTP API and PostgreSQL persistence.
- Transactional event ingestion.
- Idempotency and error handling.

### Milestone 3 — Operational Exception Detection
- Simulated carrier integrations.
- Concurrent information retrieval.
- Background processing and exception detection rules.

### Milestone 4 — AI-Assisted Investigation
- Deterministic evidence gathering.
- LLM integration and structured findings.
- Evidence and output validation.

### Milestone 5 — Agentic Investigation
- Dynamic tool calling.
- Bounded investigation loops.
- Context management and persistent workflow state.
- Retry and termination policies.

### Milestone 6 — Production Reliability
- Failure recovery and concurrency testing.
- AI workflow evaluation.
- Security and observability.
- Resource and cost management.

### Milestone 7 — Operator Experience
- Shipment monitoring dashboard.
- Exception investigation reports.
- Resolution recommendations and approvals.

## Engineering Learning Objectives

### Go Application Engineering
- Idiomatic Go implementation patterns.
- Interfaces, composition and dependency injection.
- Error handling and context propagation.
- Concurrency, synchronisation and resource management.
- Transactional persistence and API design.
- Testing, debugging and performance profiling.

### AI Application Engineering
- Workflow orchestration.
- Context engineering.
- Tool calling and agentic loops.
- Durable execution and failure recovery.
- Human-in-the-loop decision-making.
- Agent evaluation and security.

### System Design
- Event-driven architecture.
- State reconciliation.
- Integration reliability.
- Operational exception management.
- Separation of deterministic and probabilistic responsibilities.

## Success Criteria

FreightOps can receive shipment information from multiple simulated sources, maintain reliable shipment state, automatically detect operational exceptions and conduct bounded, evidence-backed investigations that reduce the manual effort required to determine appropriate resolutions.

The system remains operationally useful without its AI components.

## Initial Scope Constraints

- A modular monolith rather than microservices.
- Simulated external carrier systems.
- One carrier per shipment initially.
- Read-only AI investigation before automated actions.
- No requirement to replace existing freight management systems.
- Business assumptions to be validated through future industry research.