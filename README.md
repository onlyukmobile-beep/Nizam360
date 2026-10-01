# TVG Management — V17 Master Platform Control

## What this build is
A scratch-deployment foundation for turning TVG Management into a commercial platform.
The existing TVG workflow is preserved. V17 adds a premium **Master Platform Control** workspace for the platform owner.

## Boss identity
Default display name:
**Muhammad Zain Ul Islam**

The master dashboard addresses the owner as:
**Boss**

Your Firebase Auth account must have a matching `users/{UID}` document with:
```json
{
  "role": "platform_admin",
  "name": "Muhammad Zain Ul Islam"
}
```

After login, the sidebar shows **Master Platform Control**.

## Master Platform capabilities
- Platform owner dashboard
- Organization/client creation
- Trial / Monthly / Annual / One-Time plan records
- Subscription watch
- Organization status
- Employee-limit field
- Pakistan province/city fields
- Owner profile
- Premium theme presets
- Custom accent/background/card/text colors
- Local theme persistence
- Existing TVG modules remain available

## New deployment — scratch Firebase project
1. Create a new Firebase project.
2. Add a Web App.
3. Open `app.js`.
4. Replace the `PASTE_*` Firebase values with the Web App config from Firebase Console.
5. Enable Authentication → Email/Password.
6. Create your Boss account in Firebase Authentication.
7. In Firestore create `users/{BossAuthUID}` with:
   - `role`: `platform_admin`
   - `name`: `Muhammad Zain Ul Islam`
   - `status`: `Active`
8. Deploy Firestore rules and Hosting.
9. Test locally before going live.

Firebase Hosting supports SSL, CDN delivery and custom domains; Firebase also provides local emulation/preview workflows. See the official Firebase documentation linked in the project handover.

## GitHub
Put the complete package in a new repository.
Use `main` as the production branch.
Do not commit service-account private keys.

## Commercial architecture — important
V17 adds the **control plane**, but the existing TVG records are still in compatibility mode.
Before selling the same backend to multiple companies, migrate every business record to an `organizationId` and enforce that boundary in Firestore Rules.

See:
`COMMERCIAL-MIGRATION-GATE.md`

The migration must be completed and cross-company security tests passed before public multi-tenant launch.

## Theme Studio
The Master Platform dashboard includes five built-in premium presets:
- TVG Luxury
- Midnight Gold
- Royal Emerald
- Ocean Premium
- Platinum

Custom colors can also be applied.

## Deployment
For Firebase Hosting:
```bash
firebase login
firebase init hosting
firebase deploy --only hosting
```

Use Firebase Console / CLI to deploy Firestore rules separately.

## Important
This package intentionally has no real Firebase credentials. This prevents accidentally deploying the development TVG Firebase project into the new commercial environment.
