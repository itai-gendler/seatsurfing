---
availability:
- place: web::administration
domain: areas
references:
- kind: code
  role: implementation
  target: server/repository/location-repository.go#ReplaceAllowedBookers
---

# Remove area allowed bookers

Take Groups off an Area's allowed bookers; with none left, everyone may book in the Area.
