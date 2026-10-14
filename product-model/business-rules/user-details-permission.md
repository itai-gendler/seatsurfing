---
appliesTo:
- type: entity
  id: user
  effect: changes
  facts:
  - Email address
  - First name
  - Last name
  - Sign-in method
  - Identity provider
  contexts:
  - place: web::administration::user-editor
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Users access
    is: Admin
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#update
---

# Only Users administrators change a person's account details

Changing a person's names, email address and sign-in method in the user editor takes Users access Admin.
