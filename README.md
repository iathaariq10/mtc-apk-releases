# mtc-apk-releases

Public APK artifacts and release metadata. Source code, credentials, and operational data belong outside this repository.

## Latest release: 0.34.0

- Version code: `69`
- APK: [app-release.apk](releases/v0.34.0/app-release.apk)
- SHA-256: `67e71f9e6f895c77acd48072b33d2d4e6dca74a053015259fd72c7210cd8f6d1`
- Size: 14,428,225 bytes
- Matching API: `2026.34`
- OTA policy: minimum `0.19.3`, `force_update=true`
- Production D1 manifest: `0.34.0`, activated 6 October 2026 at 04:38 WITA after backup/recovery and public health verification. Post-activation public manifest verification is pending.

Each two-hour slot in Shift 2 and Shift 3 offers “Tidak melakukan checksheet” with a short reason. Selecting it removes machine and Cooling Tower inputs. Four explicit slot decisions satisfy the checksheet module; DT, WO, and tool/sparepart requirements still apply before PDF export.

Skipped slots remain visible in review, A4 PDF, Excel, and local SQLite without creating measurements or adding inspection coverage. Members can revise the reason within their existing access window. Submitted decision types are locked, and revision snapshots remain available for audit.

Android unit tests (104), build, lint, and signature v2 passed. MTC_API35 ran 40 scenarios with three expected environment skips and zero failures; all 17 compact-screen/PDF scenarios passed. Staging acceptance verified four real skipped-slot submissions, reason revision, closeout, SQLite/PDF, FCM registration for three roles, and notification delivery while the app was closed. Physical-device testing is outside this release scope.

Activation used the official Cloudflare D1 query API and preserved previous release records. That path did not send an OTA push notification; clients continue to check the manifest.

## Rollback artifact

[Previous APK 0.33.0](releases/v0.33.0/app-release.apk) remains available for controlled rollback. Its SHA-256 is `b78f378c18e2b737542417970331de8e454e785c3fe68182f1680c100242fe51`. Preserve skipped-slot records and revision history when rolling back; earlier clients cannot revise skipped decisions.
