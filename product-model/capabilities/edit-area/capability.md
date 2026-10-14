---
availability:
- place: web::administration
domain: areas
references:
- kind: code
  role: implementation
  target: server/router/location-router.go#update
- kind: code
  role: implementation
  target: server/router/location-router.go#setMap
- kind: code
  role: implementation
  target: server/router/location-router.go#setFloorPlanDesign
---

# Edit area

Change an Area's name, description, time zone, whether it is enabled, its capacity, bookable weekdays, attribute values and floor plan.
