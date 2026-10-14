---
availability:
- place: web::administration
domain: areas
references:
- kind: code
  role: implementation
  target: server/router/location-router.go#create
- kind: code
  role: implementation
  target: ui/src/pages/admin/locations/[id].tsx
---

# Create area

Add an Area with its name, description, time zone, capacity, bookable weekdays and floor plan.
