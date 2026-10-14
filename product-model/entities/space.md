---
domain: areas
relations:
- entity: booking
  verb: holds
  cardinality: one-to-many
- entity: recurring-booking
  verb: repeats-in
  cardinality: one-to-many
- entity: group
  verb: is-approved-by
  cardinality: many-to-many
- entity: group
  verb: allows-booking-by
  cardinality: many-to-many
references:
- kind: code
  role: implementation
  target: server/router/space-router.go
- kind: code
  role: implementation
  target: server/repository/space-repository.go
- kind: code
  role: implementation
  target: server/service/space-service.go
---

# Space

A desk, seat or room on an Area's floor plan that people book for a time slot.

## Information kept

- **Name** — the Space's name
- **Position on floor plan** — where and how large the Space is drawn on the Area's floor plan
- **Enabled** — whether the Space can be booked by people who do not administer Areas
- **Subject required** — whether a booking needs a subject of at least three characters
- **Public booking** — whether visitors may request this Space on the public booking page
- **Kiosk display** — whether the Space shows its status on a kiosk display
- **Approver groups** — the Groups whose members decide this Space's booking requests; empty means bookings need no approval
- **Allowed booker groups** — the Groups whose members alone may book this Space; empty means everyone may
- **Attribute values** — the Space's value for each attribute that applies to Spaces
