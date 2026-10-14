---
kind: person
acts: external
relations:
- entity: booking
  verb: requests
  cardinality: one-to-one
references:
- kind: code
  role: implementation
  target: server/router/public-booking-router.go
- kind: code
  role: implementation
  target: server/repository/public-booking-repository.go
---

# Visitor

A person without an account who requests a Space on an Organization's public booking page. Visitors exist while the Organization's plan includes public booking and the Organization opens its public booking page.

## Information kept

- **Name** — the name the visitor gave
- **Email address** — where the visitor confirms the request and receives decisions
- **Language** — the language of the visitor's emails
- **Details link** — the private link to the booking's details page, sent once the booking is approved
