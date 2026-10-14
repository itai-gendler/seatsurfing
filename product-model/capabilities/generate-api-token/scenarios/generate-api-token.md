---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Generate API token on a service account
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
- text: The Product creates the token, keeps only a fingerprint of it and shows it once
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

# Generate an API token

## Trigger

An integration needs a token to call the REST API.

## Outcome

The service account has a new API token, shown this once; any earlier token no longer works.
