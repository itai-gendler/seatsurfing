---
availability:
- place: web::administration
domain: users
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#update
---

# Edit user

Change a person's names, email address and how they sign in: send a new invitation, set a password they must change at their next sign-in, or bind them to an identity provider. A change of sign-in method ends their sessions. On one's own account the email address, kind of account and sign-in method stay.
