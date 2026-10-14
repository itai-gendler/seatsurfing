---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor picks a day, a time slot and a Space opened for public booking, on the floor plan or from the list
  kind: actor
  actor: visitor
  entities:
  - entity: area
    effect: reads
    facts:
    - Name
  - entity: space
    effect: reads
    facts:
    - Name
  - entity: booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::public-booking
- text: The Visitor enters their name, email address and a subject if wanted and requests the booking
  kind: actor
  actor: visitor
  entities:
  - entity: booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::public-booking
- text: The Product checks the slot lies within one day, the public and organization-wide duration limits, the advance limit and the Area's bookable weekdays
  kind: product
  actor: visitor
  entities:
  - entity: organization
    effect: reads
    facts:
    - Public booking min duration
    - Public booking max duration
    - Min booking duration
    - Max booking duration
    - Max days in advance
  - entity: area
    effect: reads
    facts:
    - Bookable weekdays
  contexts:
    web:
      place: web::public::public-booking
- text: The Product emails the Visitor a confirmation link valid for 30 minutes
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::public-booking
- text: The Visitor opens the confirmation link
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::public-booking
- text: The Space is still free and the Area still has capacity for the slot
  kind: condition
  entities:
  - entity: space
    effect: reads
    facts:
    - Public booking
  - entity: area
    effect: reads
    facts:
    - Max bookings
  contexts:
    web:
      place: web::public::public-booking
- text: The Product keeps the Visitor's details and creates the booking of the Space, waiting for approval
  kind: product
  actor: visitor
  entities:
  - entity: visitor
    effect: changes
    facts:
    - Name
    - Email address
    - Language
    - Details link
  - entity: space
    effect: reads
    facts: []
  - entity: booking
    effect: creates
    to: Pending approval
    facts:
    - Space
    - Enter
    - Leave
    - Subject
    - Booker
    - Public request
  contexts:
    web:
      place: web::public::public-booking
- text: The Product emails each member of the Space's approver groups whose approval notifications are on
  kind: product
  actor: visitor
  entities:
  - entity: group
    effect: reads
    facts:
    - Members
  - entity: user
    as: approver
    effect: reads
    facts:
    - Approval notifications
    - Email address
    - Email language
  - entity: booking
    effect: reads
    facts:
    - Space
    - Enter
    - Leave
    - Subject
  - entity: space
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::public-booking
---

# Request and confirm a public booking

## Trigger

A visitor wants a Space of the Organization without having an account.

## Outcome

The visitor's booking holds the slot and waits for approval; the approvers who asked for notifications know about it.

## Edge cases

- Public booking applies the Organization's duration and advance limits but not its per-person limits or allowed booker groups.
- A Space that requires a subject refuses a request whose subject has fewer than three characters.
