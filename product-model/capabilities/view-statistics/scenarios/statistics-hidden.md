---
kind: validation
routes:
  web: Web
steps:
- text: The User opens the dashboard
  kind: actor
  actor: user
  entities:
  - entity: area
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::dashboard
- text: The Organization hides statistics
  kind: condition
  entities:
  - entity: organization
    effect: reads
    facts:
    - Hide statistics
  contexts:
    web:
      place: web::administration::dashboard
- text: The Product shows no figures
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::administration::dashboard
---

# Statistics hidden by the organization

## Trigger

An administrator opens the dashboard while the Organization hides statistics.

## Outcome

No figures are shown; the dashboard says they were hidden by an administrator.
