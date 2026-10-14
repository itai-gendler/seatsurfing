---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Remove buddy on one of their buddies and confirms
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
- text: The Product removes the buddy
  kind: product
  actor: user
  entities:
  - entity: buddy
    effect: removes
  contexts:
    web:
      place: web::booking-site::buddies
---

# Remove a buddy

## Trigger

A User no longer wants to follow a colleague.

## Outcome

The colleague is no longer the User's buddy.
