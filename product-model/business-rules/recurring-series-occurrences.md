---
appliesTo:
- type: capability
  id: book-space
  contexts:
  - place: web::booking-site
references:
- kind: code
  role: implementation
  target: server/repository/recurring-booking-repository.go#CreateBookings
- kind: code
  role: implementation
  target: server/router/recurring-booking-router.go#create
---

# A recurring series has at most 365 occurrences, each checked on its own

A series yields at most 365 occurrences before its end date; a longer one is refused. Each occurrence is checked like a single booking, and occurrences that break a rule or overlap another booking are left out while the others are booked.
