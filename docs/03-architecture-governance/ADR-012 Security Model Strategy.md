# ADR-012: Security Model Strategy

## Status

Accepted

## Context

CRM Intelligence contains relationship data that may contain sensitive customer and commercial information.

The solution requires a security model that supports controlled access while maintaining visibility where appropriate.

## Decision

The solution will use Salesforce standard security controls:

- Organisation-wide defaults
- Profiles
- Permission Sets
- Field-level security
- Role hierarchy where appropriate

Relationship Profile is the controlling object.

Child objects:

- Relationship Context
- Relationship History

inherit record access through Master-Detail relationships.

## Consequences

Benefits:

- Simplified sharing model
- Consistent access control
- Reduced duplicate sharing configuration

Considerations:

- Access changes must be managed through the parent object.

## Implementation Decision

The CRM Intelligence security model is based on Relationship Profile as the controlling business record.

Relationship Profile uses Private sharing to ensure relationship data is only accessible to authorised users.

Supporting objects use Master-Detail relationships:

- Relationship Context
- Relationship History

These child objects inherit access from Relationship Profile using Controlled by Parent sharing.

This avoids separate sharing rules and keeps security aligned with the relationship ownership model.

## Security Principles

- Use least privilege access.
- Extend access through Permission Sets rather than profile modification.
- Protect relationship ownership and parent relationships from unnecessary changes.
- Keep child records aligned with parent security.
