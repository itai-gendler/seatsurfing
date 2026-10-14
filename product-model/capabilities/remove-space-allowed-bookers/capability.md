---
availability:
- place: web::administration
domain: areas
references:
- kind: code
  role: implementation
  target: server/router/space-router.go#removeAllowedBookers
- kind: code
  role: implementation
  target: server/router/space-router.go#applyAllowBookers
---

# Remove space allowed bookers

Take Groups off a Space's allowed bookers; with none left, everyone may book the Space.
