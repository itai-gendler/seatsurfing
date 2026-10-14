---
domain: roles
relations:
- entity: user
  verb: is-held-by
  cardinality: many-to-many
- entity: service-account
  verb: is-held-by
  cardinality: many-to-many
references:
- kind: code
  role: implementation
  target: server/router/role-router.go
- kind: code
  role: implementation
  target: server/repository/role-repository.go
- kind: spec
  role: intent
  target: specs/custom-roles.md
---

# Role

A named set of access levels, one per functionality, that the Organization defines and assigns to Users and service accounts. The built-in Organization Administrator role grants every functionality in full and never changes.

## Information kept

- **Name** — the Role's name, unique within the Organization
- **Description** — what the Role is for
- **Access levels** — for each functionality, the level the Role grants among those the functionality offers
- **Built-in** — whether this is the Organization Administrator role
