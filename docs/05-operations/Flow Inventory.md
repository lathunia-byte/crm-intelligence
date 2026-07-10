# Flow Inventory

## Document Control

| Field         | Value                          |
| ------------- | ------------------------------ |
| Document Name | Solution Architecture Overview |
| Version       | 1.0                            |
| Status        | Draft                          |
| Owner         | CRM Intelligence Project       |
| Last Updated  | 2026-06-30                     |

---

# 1. Purpose

The Flow Inventory provides a central register of all Salesforce Flows within the CRM Intelligence solution. It supports operational support, change management, troubleshooting, and impact assessment by documenting the purpose, ownership, and status of each automation.

# 2. Flow Inventory

| Flow                                        | Type             | Object               | Trigger      | Purpose                                                                       | Status | Owner          |
| ------------------------------------------- | ---------------- | -------------------- | ------------ | ----------------------------------------------------------------------------- | ------ | -------------- |
| RTF - Relationship Profile - Status Change  | Record-Triggered | Relationship Profile | After Update | Creates a Relationship History record when the relationship status changes.   | Active | Cheryl Leggett |
| RTF - Relationship Context - Create History | Record-Triggered | Relationship Context | After Create | Creates a Relationship History record when new relationship context is added. | Active | Cheryl Leggett |

---

# 3. Naming Standards

## Prefixes

| Prefixes | Meaning                        |
| -------- | ------------------------------ |
| RTF      | Record-Triggered Flow          |
| STF      | Scheduled Flow _(future)_      |
| SLF      | Screen Flow _(future)_         |
| PLF      | Platform Event Flow _(future)_ |

## Naming Convention

<Type> - <Primary Object> - <Business Purpose>

Example:
RTF - Relationship Profile - Status Change

---

# 4. Design Standards

- One business process per Flow.
- Use Before Save Flows only for field updates.
- Use After Save Flows for creating related records.
- Prefer Formula resources over unnecessary Decision elements where appropriate.
- Use descriptive API names and labels.
- Configure fault paths for production-ready automation.
- Minimise DML and SOQL operations.
- Keep Flows modular and single-purpose.

---

# 5. Dependencies

| Flow                                  | Depends On                                 |
| ------------------------------------- | ------------------------------------------ |
| Relationship Profile - Status Change  | Relationship Profile, Relationship History |
| Relationship Context - Create History | Relationship Context, Relationship History |

---

# 6. Change Log

| Version | Sprint   | Change                            |
| ------- | -------- | --------------------------------- |
| 1.0     | Sprint 2 | Initial flow inventory created.   |
| 1.1     | Sprint 3 | Additional automation documented. |

---

# 7. Future Automation

| Planned Flow                            | Status  |
| --------------------------------------- | ------- |
| Relationship Health Score Monitoring    | Planned |
| Scheduled Relationship Review Reminder  | Planned |
| Agentforce Relationship Summary Refresh | Planned |
| Renewal Notification                    | Planned |
| Escalation Workflow                     | Planned |
