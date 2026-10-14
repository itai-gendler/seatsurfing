---
appliesTo:
- type: capability
  id: request-public-booking
  contexts:
  - place: web::public
references:
- kind: code
  role: implementation
  target: server/router/public-booking-router.go#validateSpaceAndTimes
- kind: code
  role: implementation
  target: server/service/booking-service.go#GetPublicBookingDurationLimits
---

# A public booking stays within one day and both sets of duration limits

A visitor's request starts and ends on the same day, keeps to the public minimum and maximum durations and the organization-wide ones, the advance limit and the Area's bookable weekdays. The confirmation link is valid for 30 minutes and only once.
