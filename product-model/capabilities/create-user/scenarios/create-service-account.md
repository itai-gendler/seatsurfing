---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses a read-only or read-write service account, enters a username, names and password and saves
  kind: actor
  actor: user
  entities:
  - entity: service-account
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::user-editor
- text: The Product creates the service account
  kind: product
  actor: user
  entities:
  - entity: service-account
    effect: creates
    facts:
    - Name
    - Username
    - Access mode
    - Password
    - API token
  contexts:
    web:
      place: web::administration::user-editor
---

# Create a service account

## Trigger

An administrator of Users and service accounts sets up access for an integration.

## Outcome

The service account exists, read-only or read-write, and authenticates with its username and password.
