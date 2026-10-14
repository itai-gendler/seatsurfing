---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Revoke API token on a service account and confirms
  kind: actor
  actor: user
  entities:
  - entity: service-account
    effect: reads
    facts:
    - API token
  contexts:
    web:
      place: web::administration::user-editor
- text: The Product removes the token
  kind: product
  actor: user
  entities:
  - entity: service-account
    effect: changes
    facts:
    - API token
  contexts:
    web:
      place: web::administration::user-editor
---

# Revoke an API token

## Trigger

An integration's token should stop working.

## Outcome

The token no longer authenticates the service account.
