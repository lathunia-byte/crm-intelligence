# ADR-013: Salesforce Automation Strategy

## Status

Accepted

## Context

CRM Intelligence currently provides a governed data foundation consisting of Relationship Profile, Relationship Context and Relationship History objects.

As the solution evolves, manual data maintenance becomes increasingly inefficient and risks inconsistencies between related records. Salesforce provides multiple automation technologies, including Flow and Apex. A strategic decision is required to define the primary automation technology for the solution.

## Decision

The CRM Intelligence solution will adopt Salesforce Flow as the primary automation platform.

Automation will be implemented using Record-Triggered Flows wherever declarative functionality satisfies the business requirement.

Apex will be reserved for scenarios where:

declarative automation cannot satisfy the requirement,
complex processing is required,
external integrations require custom logic,
platform governor considerations make Apex more appropriate.
Principles

The automation strategy follows these principles:

Flow before Apex.
One business process per Flow.
Avoid recursive automation.
Use Fast Field Updates where appropriate.
Create related records using After Save Flows.
Minimise SOQL and DML operations.
Keep automation modular and reusable.
Prefer declarative configuration over custom code.

## Consequences

Benefits:

Lower maintenance effort.
Reduced custom code.
Easier administration.
Faster delivery.
Better alignment with Salesforce Well-Architected guidance.

Trade-offs:

Complex orchestration may require future Apex.
Large automation estates require governance and naming standards.

## Flow Standards

### Naming Convention

- RTF - Relationship Profile - Create History
- RTF - Relationship Profile - Initial History
- RTF - Relationship Profile - Status Change
- RTF - Relationship Profile - Closure

### Entry Criteria

Each flow should have:

- Single responsibility
- Clear entry criteria
- Descriptive labels
- Fault paths configured
- Version history maintained

### Flow Design Standards

- Avoid duplicate automation.
- Do not update triggering records in After Save unless necessary.
- Use Decisions instead of unnecessary Assignments.
- Use fault connectors where appropriate.
- Document all flows.
