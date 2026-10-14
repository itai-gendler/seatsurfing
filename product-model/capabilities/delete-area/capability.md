---
availability:
- place: web::administration
domain: areas
references:
- kind: code
  role: implementation
  target: server/router/location-router.go#delete
- kind: code
  role: implementation
  target: server/repository/location-repository.go#Delete
---

# Delete area

Remove an Area together with its Spaces and every booking and Recurring booking in them.
