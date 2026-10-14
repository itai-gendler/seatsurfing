---
actors:
- user
access: restricted
entryPoints:
- web: /ui/admin/dashboard/
references:
- kind: code
  role: implementation
  target: ui/src/components/SideBar.tsx
- kind: code
  role: implementation
  target: ui/src/components/withPermission.tsx
- kind: code
  role: implementation
  target: server/service/permissions.go#HasAnyPermission
---

# Administration

The administration area, open to Users whose Roles grant at least one administrative access, where they manage Areas and Spaces, other people's bookings, approvals, Users, Groups, Roles, identity providers and the Organization's settings, and read statistics and logs, as far as their access reaches.
