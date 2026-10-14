---
actors:
- user
access: authenticated
entryPoints:
- web: /ui/search/
references:
- kind: code
  role: implementation
  target: ui/src/components/NavBar.tsx
---

# Booking Site

The signed-in self-service site where every User of the Organization finds a free Space, books it, keeps track of their own bookings and buddies, and manages their preferences and sign-in security.
