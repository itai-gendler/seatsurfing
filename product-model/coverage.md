---
scope: Booking, approval, area and space, group, user, role, sign-in and account security, identity provider, preference, buddy, kiosk, report and organization-settings behavior of the Go server, its REST API and the Next.js web app.
method: Static inspection of source, specs, OpenAPI description and translations at the pinned commit; nothing was run.
covered:
- description: Booking, recurring booking and public booking request handling and the shared booking rules.
  paths:
  - server/router/booking-router.go
  - server/router/recurring-booking-router.go
  - server/router/public-booking-router.go
  - server/service/booking-service.go
  - server/service/space-service.go
  - server/service/location-service.go
- description: Area, space, attribute, group and organization settings handlers.
  paths:
  - server/router/location-router.go
  - server/router/space-router.go
  - server/router/space-attribute-router.go
  - server/router/group-router.go
  - server/router/settings-router.go
  - server/router/floor-plan-renderer.go
- description: Sign-in, passwords, invitations, sessions, authenticator apps, passkeys and identity providers.
  paths:
  - server/router/auth-router.go
  - server/router/passkey-router.go
  - server/router/auth-provider-router.go
  - server/router/routes.go
- description: Users, service accounts, API tokens, roles and their assignment.
  paths:
  - server/router/user-router.go
  - server/router/role-router.go
  - server/api/permissions.go
  - server/service/permissions.go
  - server/router/permissions.go
- description: Buddies, personal preferences and CalDAV connection.
  paths:
  - server/router/buddy-router.go
  - server/service/buddy-service.go
  - server/router/user-preferences-router.go
- description: Kiosk display, statistics, presence report and audit log handlers.
  paths:
  - server/router/kiosk-router.go
  - server/router/stats-router.go
  - server/router/auth-attempt-router.go
- description: Persistence behind the modelled behavior.
  paths:
  - server/repository/
- description: Scheduled booking reminders and booking retention in the server's timer.
  paths:
  - server/app/app.go
- description: Email templates.
  paths:
  - server/res/
- description: REST API description and service-account authentication spec.
  paths:
  - specs/openapi.yaml
  - specs/service-account-bearer-auth.md
- description: Booking Site, public, sign-in and administration pages and their components.
  paths:
  - ui/src/pages/search.tsx
  - ui/src/pages/bookings.tsx
  - ui/src/pages/buddies.tsx
  - ui/src/pages/preferences.tsx
  - ui/src/pages/book/
  - ui/src/pages/login/
  - ui/src/pages/resetpw/
  - ui/src/pages/setpw/
  - ui/src/pages/kiosk/
  - ui/src/pages/admin/approvals/
  - ui/src/pages/admin/bookings/
  - ui/src/pages/admin/locations/
  - ui/src/pages/admin/attributes/
  - ui/src/pages/admin/groups/
  - ui/src/pages/admin/users/
  - ui/src/pages/admin/roles/
  - ui/src/pages/admin/settings/index.tsx
  - ui/src/pages/admin/settings/auth-providers/
  - ui/src/pages/admin/dashboard.tsx
  - ui/src/pages/admin/report/
  - ui/src/pages/admin/audit/
  - ui/src/components/
  - ui/src/pages/_app.tsx
exclusions:
- description: Automated tests, test helpers and performance tooling.
  paths:
  - e2e/
  - server/router/test/
  - server/service/test/
  - server/repository/test/
  - server/app/test/
  - server/testutil/
  - server/perftest/
  - ui/src/components/__tests__/
- description: Build, packaging, CI, deployment examples and the container health check.
  paths:
  - .github/
  - example/
  - healthcheck/
  - Dockerfile
  - docker-compose.yaml
  - build.sh
  - dev.sh
  - release-please-config.json
  - server/router/healthcheck-router.go
- description: Update check and anonymous installation statistics reported to the maintainers.
  paths:
  - server/router/check-update-router.go
- description: Styling, static assets and translation tooling.
  paths:
  - ui/src/styles/
  - ui/public/
  - ui/add-missing-translations.sh
unmapped:
- description: 'Organization profile, domains, domain verification and organization deletion: tenant hosting administration, with custom domains a plan feature and verification and deletion switched on by the operator of the hosted service.'
  paths:
  - server/router/organization-router.go
  - ui/src/pages/admin/settings/org.tsx
  - ui/src/pages/admin/settings/delete/
  - ui/src/pages/admin/confirm/
- description: 'Plugin contract, plugin host API and plugin pages: extensions are separate binaries that own their behavior.'
  paths:
  - server/api/hostapi.go
  - server/api/hostapi_booking.go
  - server/api/hostapi_buddy.go
  - server/api/hostapi_grpc_client.go
  - server/api/hostapi_grpc_server.go
  - server/api/plugin-registry.go
  - server/api/plugin_grpc_client.go
  - server/api/plugin_grpc_convert.go
  - server/api/proto/
  - server/api/pluginpb/
  - server/api/hostapipb/
  - server/api/commonpb/
  - server/app/hostapi-booking.go
  - server/app/hostapi-buddy.go
  - ui/src/pages/admin/plugin/
- description: 'Administration search box and sample data loading: a navigation shortcut over modelled lists and demo data.'
  paths:
  - server/router/search-router.go
  - server/service/search.go
  - ui/src/pages/admin/search/
limitations:
- description: Plan features of organizations in multi-organization installations are set outside this repository.
  paths:
  - server/app/app.go
---

# Coverage
