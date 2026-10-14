---
entities:
- entity: booking
  shows:
  - Enter
  - Leave
  - Subject
  - Space
- entity: area
  shows:
  - Name
entryPoints:
- web: /ui/book/details/{externalId}/
references:
- kind: code
  role: implementation
  target: ui/src/pages/book/details/[externalId].tsx
- kind: code
  role: implementation
  target: server/router/public-booking-router.go#details
---

# Public booking details

The page a visitor reaches from the link in the approval email, showing their approved booking until it ends and letting them cancel it.
