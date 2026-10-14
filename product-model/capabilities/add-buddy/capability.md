---
availability:
- place: web::booking-site
references:
- kind: code
  role: implementation
  target: server/router/buddy-router.go#create
- kind: code
  role: implementation
  target: ui/src/pages/buddies.tsx
- kind: code
  role: implementation
  target: ui/src/pages/search.tsx
---

# Add buddy

Mark a colleague of the Organization as one's buddy, from My buddies or from their booking on the floor plan. It exists while the Organization shows bookers' names and has not switched buddies off.
