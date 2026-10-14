---
availability:
- place: web::administration
domain: areas
references:
- kind: code
  role: implementation
  target: server/repository/location-repository.go#ReplaceAllowedBookers
---

# Add area allowed bookers

Name Groups as an Area's allowed bookers, so that only their members book in the Area.
