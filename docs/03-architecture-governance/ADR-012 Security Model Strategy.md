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

## Field-Level Security Notes

Salesforce-managed fields such as record names and Master-Detail relationship fields cannot be managed as normal editable fields through Permission Sets.

These fields remain controlled by Salesforce to protect record identity, ownership and relationship integrity.

Business fields use Permission Set controlled field-level security.

## Validation Results

The implemented security model was validated against the CRM Intelligence data model.

Confirmed:

- Relationship Profile uses Private sharing.
- Relationship Context uses Controlled by Parent sharing.
- Relationship History uses Controlled by Parent sharing.
- Child record access is inherited through Master-Detail relationships.
- CRM Intelligence User Permission Set provides required object access.
- Field-level security is applied to configurable business fields.
- Salesforce-managed fields remain controlled by platform rules.

## Outcome

The security model provides controlled access to relationship intelligence data while maintaining a simple and maintainable sharing architecture.

The design avoids unnecessary sharing rules by using Relationship Profile as the security boundary.
