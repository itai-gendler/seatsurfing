---
kind: primary
routes:
  web: Web
steps:
- text: The User renames one of their passkeys
  kind: actor
  actor: user
  entities:
  - entity: passkey
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::booking-site::preferences
- text: The Product keeps the new name
  kind: product
  actor: user
  entities:
  - entity: passkey
    effect: changes
    facts:
    - Name
  contexts:
    web:
      place: web::booking-site::preferences
---

# Rename a passkey

## Trigger

A User wants to tell their passkeys apart.

## Outcome

The passkey carries its new name.
