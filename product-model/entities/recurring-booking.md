---
relations:
- entity: booking
  verb: schedules
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: server/router/recurring-booking-router.go
- kind: code
  role: implementation
  target: server/repository/recurring-booking-repository.go
---

# Recurring booking

A series of bookings of one Space at the same time of day, repeating daily or on chosen weekdays until an end date. It exists while the Organization's plan includes recurring bookings and the Organization allows them.

## Information kept

- **Space** — the Space every occurrence books
- **Enter** — the start of the first occurrence; later occurrences start at the same time of day
- **Leave** — the end of the first occurrence; every occurrence lasts as long
- **Subject** — the subject every occurrence carries
- **Cadence** — Daily or Weekly
- **Cycle** — every how many days, or every how many weeks, the series repeats
- **Weekdays** — the weekdays a weekly series falls on
- **End date** — the series creates no occurrence starting at or after this date
