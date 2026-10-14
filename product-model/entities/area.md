---
domain: areas
relations:
- entity: space
  verb: contains
  cardinality: one-to-many
- entity: group
  verb: allows-booking-by
  cardinality: many-to-many
references:
- kind: code
  role: implementation
  target: server/router/location-router.go
- kind: code
  role: implementation
  target: server/repository/location-repository.go
- kind: code
  role: implementation
  target: server/service/location-service.go
---

# Area

A place people book in, such as a floor or an office, with its floor plan and the Spaces on it.

## Information kept

- **Name** — the Area's name
- **Description** — free text shown with the Area
- **Time zone** — the time zone booking times in this Area are read in
- **Enabled** — whether the Area can be booked by people who do not administer Areas
- **Max bookings** — how many bookings the Area holds at the same time; 0 means no limit
- **Bookable weekdays** — the weekdays a booking in this Area may fall on; empty means every day
- **Floor plan** — the uploaded or designed map of the Area
- **Allowed booker groups** — the Groups whose members alone may book here; empty means everyone may
- **Attribute values** — the Area's value for each attribute that applies to Areas
