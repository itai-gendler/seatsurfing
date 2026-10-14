---
availability:
- place: web::booking-site
- place: web::administration
references:
- kind: code
  role: implementation
  target: server/router/auth-router.go#logout
- kind: code
  role: implementation
  target: ui/src/components/NavBar.tsx
- kind: code
  role: implementation
  target: ui/src/pages/preferences.tsx
---

# Sign out

End one's session on this device, another of one's sessions, or all of them. Signing out of a User who came through an identity provider also takes them to the provider's sign-out.
