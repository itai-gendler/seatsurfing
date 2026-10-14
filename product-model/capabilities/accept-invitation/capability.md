---
availability:
- place: web::public
references:
- kind: code
  role: implementation
  target: server/router/auth-router.go#validateUserInvitation
- kind: code
  role: implementation
  target: server/router/auth-router.go#completeUserInvitation
- kind: code
  role: implementation
  target: ui/src/pages/setpw/[id].tsx
---

# Accept invitation

Choose one's password from the link in the invitation email an administrator sent. The link is valid for three days and only until a password is set.
