# mtc-apk-releases

Public APK artifacts, release metadata, and the browser OTA publisher. Application source code, credentials, and operational data belong outside this repository.

## Latest artifact: 0.35.0 — OTA activation pending

- Version code: `70`
- APK: [app-release.apk](releases/v0.35.0/app-release.apk)
- SHA-256: `b120019ae57f2c5f0b56d7840728be7cc6cdd5eb11f501cdec92f45f3c6a38fd`
- Size: 14,444,609 bytes
- Matching API: `2026.35`
- OTA policy prepared: minimum `0.19.3`, `force_update=true`
- Production D1 manifest remains `0.34.0` until the audited Superadmin publication is accepted.

Shift 1 export follows the full two-day schedule block: day one can export without a checksheet, while day two requires an accepted checksheet for every scheduled machine somewhere in that block. Shift 3 members can submit or revise their own prior-night checksheet within the server window. Every shift still requires DT, WO, and tool/sparepart declarations.

Downtime now records machine type, installed-mold snapshot, and repair target (machine or mold), with condition, symptom, components, times, action, cause, technician, and parts evidence flowing into reports. Historical records are not backfilled from current master data.

Android release signature v2 matches the public signer. Unit tests (105), lint, upgrade install, and cold launch passed; MTC_API35 ran 41 tests with three expected FCM environment skips and zero failures. Two staging live acceptances passed with exact cleanup. Physical-device testing is outside this release scope.

## OTA publication

The publisher page is prepared for APK `0.35.0`; it must be used only after the artifact URL and SHA-256 are verified. Manifest activation and notification remain pending until the Superadmin flow returns an accepted audit receipt.

The checked publisher is served at [the HTTPS release publication page](https://iathaariq10.github.io/mtc-apk-releases/), with source in [docs/index.html](docs/index.html). GitHub Pages build and HTTPS delivery were verified on 7 October 2026; the file matches the local form verified with 18 simulations and a browser render. The production browser operation was verified through its receipt and server records.

The operator signs in with a genuine Superadmin account. Requests go directly from the browser to the maintenance Worker over HTTPS. The form checks health, every release field, and publication history before sending once. It retains no password or bearer token, uses a local marker to prevent a repeat submission when an outcome is uncertain, and attempts logout. An accepted publication does not prove FCM delivery to a phone.

Only the static publisher is hosted. Databases, recovery backups, private evidence, and credentials are excluded from the page.

## Rollback artifact

[Previous public APK 0.34.0](releases/v0.34.0/app-release.apk) remains available for controlled rollback. Its SHA-256 is `67e71f9e6f895c77acd48072b33d2d4e6dca74a053015259fd72c7210cd8f6d1`. Preserve shift decisions and revision history when rolling back; older clients may not understand newer downtime fields.
