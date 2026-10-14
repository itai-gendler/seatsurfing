---
availability:
- place: web::public
references:
- kind: code
  role: implementation
  target: server/router/public-booking-router.go#request
- kind: code
  role: implementation
  target: server/router/public-booking-router.go#confirm
- kind: code
  role: implementation
  target: server/router/public-booking-router.go#validateSpaceAndTimes
- kind: code
  role: implementation
  target: ui/src/pages/book/index.tsx
---

# Request public booking

A visitor without an account requests a Space opened for public booking and confirms the request from an emailed link; the confirmed request becomes a booking that waits for approval. It exists while the Organization's plan includes public booking and the Organization opens its public booking page.
