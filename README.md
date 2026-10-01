# mtc-apk-releases

Public APK artifacts and release metadata. Source code, credentials, and operational data belong outside this repository.

## Latest release: 0.33.0

- Version code: `68`
- APK: [app-release.apk](releases/v0.33.0/app-release.apk)
- SHA-256: `b78f378c18e2b737542417970331de8e454e785c3fe68182f1680c100242fe51`
- Size: 14,428,225 bytes
- Matching API: `2026.33`
- OTA: minimum `0.19.3`, `force_update=true`

Members see their own inspection from the server schedule. The four modules are locked before the shift starts and remain available for revision within the configured window after it ends. Shift 3 keeps its start date across midnight. Overshift and replacement require active Admin authorization; a checksheet-only reopening does not unlock DT, WO, or material declarations.

Android unit tests (103), build, lint, and signature v2 passed. The MTC_API35 emulator passed 38 scenarios with three expected environment skips and zero failures; five compact-screen scenarios also passed. Physical-device testing is outside this release scope.

## Rollback artifact

[Previous APK 0.32.0](releases/v0.32.0/app-release.apk) remains available for controlled rollback. Its SHA-256 is `96e286db4632d2e50642cc11956e2c0419ddb6dc42a060b85fb104fcc8adfcd7`.
