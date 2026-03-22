# Authority Model

Ved encodes operational boundaries as language constructs.

Hierarchy example:

- Tenant
- Environment
- Workspace
- Target
- Context
- Namespace

Rules:

- lower scopes cannot mutate higher scopes
- escalation must be explicit
- cross-boundary interaction must be validated

This prevents uncontrolled privilege propagation.
