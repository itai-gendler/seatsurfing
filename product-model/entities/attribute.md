---
domain: areas
references:
- kind: code
  role: implementation
  target: server/router/space-attribute-router.go
- kind: code
  role: implementation
  target: server/repository/space-attribute-repository.go
---

# Attribute

A property the Organization defines for Spaces, Areas or both, such as a standing desk or a number of seats, that people filter by when they search.

## Information kept

- **Label** — the attribute's name
- **Type** — Number, Yes/No or Text
- **Applies to spaces** — whether Spaces carry a value for it
- **Applies to areas** — whether Areas carry a value for it
