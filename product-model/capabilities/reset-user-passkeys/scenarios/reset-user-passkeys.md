---
kind: primary
routes:
  web: Web
steps:
- text: The User resets the person's keys for passwordless sign-in and confirms
  kind: actor
  actor: user
  entities:
  - entity: user
    as: person
    effect: reads
    facts:
    - Has passkeys
  contexts:
    web:
      place: web::administration::user-editor
- text: The Product removes all of the person's passkeys
  kind: product
  actor: user
  entities:
  - entity: user
    as: person
    effect: reads
    facts: []
  - entity: passkey
    effect: removes
  contexts:
    web:
      place: web::administration::user-editor
---

# Reset a person's passkeys

## Trigger

A person lost the devices holding their passkeys.

## Outcome

None of the person's passkeys signs them in any more.
