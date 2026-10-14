---
appliesTo:
- type: entity
  id: session
  effect: removes
permits:
- related:
  - verb: signs-in-with
    entity: user
- actors:
  - user
  when:
  - entity: user
    fact: Users access
    is: Admin
references:
- kind: code
  role: implementation
  target: server/router/auth-router.go#logout
- kind: code
  role: implementation
  target: server/router/user-router.go#update
---

# Only the person ends their own sessions; Users administrators end them by resetting a sign-in

A User signs out their own sessions; a User with Users access Admin ends another person's sessions by changing how that person signs in.
