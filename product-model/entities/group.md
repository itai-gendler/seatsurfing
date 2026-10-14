---
domain: groups
relations:
- entity: user
  verb: includes
  cardinality: many-to-many
references:
- kind: code
  role: implementation
  target: server/router/group-router.go
- kind: code
  role: implementation
  target: server/repository/group-repository.go
---

# Group

A named set of Users that Areas and Spaces name as their allowed bookers or approvers, and identity providers fill. Groups exist while the Organization's plan includes them.

## Information kept

- **Name** — the Group's name, unique within the Organization
- **Members** — the Users in the Group
