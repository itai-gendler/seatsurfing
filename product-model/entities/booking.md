---
references:
- kind: code
  role: implementation
  target: server/router/booking-router.go
- kind: code
  role: implementation
  target: server/service/booking-service.go
- kind: code
  role: implementation
  target: server/repository/booking-repository.go
---

# Booking

One Space reserved for one time slot, for a User of the Organization or for a visitor.

## Information kept

- **Space** — the Space booked
- **Enter** — when the booking starts, read in the Area's time zone
- **Leave** — when the booking ends, read in the Area's time zone
- **Subject** — an optional subject, required where the Space asks for one
- **Booker** — who the booking is for: a User or a visitor
- **Public request** — whether a visitor requested it on the public booking page
- **Reminder sent** — when the reminder email for the booking went out

## States

### Confirmed

The Space is reserved and the booker can use it.

### Pending approval

The booking waits for an approver of the Space; it already holds its time slot.
