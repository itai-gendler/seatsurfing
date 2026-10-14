---
kind: primary
routes:
  web: Web
steps:
- text: The User searches My buddies for a colleague by name or email address and adds them
  kind: actor
  actor: user
  entities:
  - entity: buddy
    effect: reads
    facts:
    - Colleague
  contexts:
    web:
      place: web::booking-site::buddies
- text: The Product keeps the colleague as the User's buddy
  kind: product
  actor: user
  entities:
  - entity: buddy
    effect: creates
    facts:
    - Colleague
  - entity: user
    as: colleague
    effect: reads
    facts:
    - Email address
  contexts:
    web:
      place: web::booking-site::buddies
---

# Add a buddy

## Trigger

A User wants to see where a colleague sits.

## Outcome

The colleague is the User's buddy; the floor plan shows their bookings in the buddy color and search can look for Areas where a buddy is on site.

## Edge cases

- The same buddy is added from a colleague's booking on the floor plan.
- Search needs at least three characters and never offers the User themselves.
