---
appliesTo:
- type: capability
  id: book-space
- type: capability
  id: edit-booking
- type: capability
  id: request-public-booking
references:
- kind: code
  role: implementation
  target: server/service/booking-service.go#CheckBooking
- kind: code
  role: implementation
  target: server/repository/booking-repository.go#GetConcurrent
---

# An Area never holds more bookings at once than its maximum

While an Area sets a maximum number of bookings, a new or changed booking that would exceed it at any moment of its slot is refused, for everyone.
