# TVG Commercial SaaS — Migration Gate

V17 adds the platform control plane without breaking the proven TVG workflow.

Before public multi-company launch, migrate every business record to include:
`organizationId`.

Recommended final model:
- organizations/{organizationId}
- users/{uid}.organizationId
- attendance/{id}.organizationId
- leaves/{id}.organizationId
- applications/{id}.organizationId
- locations/{id}.organizationId
- payroll/{id}.organizationId
- assets/{id}.organizationId
- reports generated from organization-scoped queries

Then replace the compatibility catch-all rule with organization-scoped rules.
Firebase Security Rules should enforce tenant isolation; UI filtering alone is not a security boundary.

Platform owner:
users/{uid}.role = "platform_admin"

Platform collections:
organizations
subscriptions
platformSettings
platformAudit

The current V17 rules deliberately preserve the existing application while this migration is staged.
Do not advertise the platform as fully isolated multi-tenant SaaS until the migration and cross-tenant security tests pass.
