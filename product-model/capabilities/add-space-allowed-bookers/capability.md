---
availability:
- place: web::administration
domain: areas
references:
- kind: code
  role: implementation
  target: server/router/space-router.go#addAllowedBookers
- kind: code
  role: implementation
  target: server/router/space-router.go#applyAllowBookers
---

# Add space allowed bookers

Name Groups as a Space's allowed bookers, so that only their members book the Space.
