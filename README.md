# mtc-apk-releases

Public APK artifacts and the guarded HTTPS OTA publisher. Source, credentials and operational data remain outside this repository.

## Latest artifact: 0.37.0

- APK: [app-release.apk](releases/v0.37.0/app-release.apk), version code 72.
- SHA-256: `c7b4adc62491a76c32b19a7b37db9580eebf516cb93de1898837a07bd2f763de`; 14,460,993 bytes.
- Adds Shift 1 Cycle Time, Injection/Filling Time, Cushion, material/grade, recipe/version, operation mode and measurement basis. Actual zero remains distinct from unavailable values.
- Production evidence appears in the checked-PDF appendix. The four existing checked-sheet templates remain intact.
- Verified: 107 unit tests, lint, focused UI/PDF/JSON trials including 320 dp, matching v2 signer, direct signed release upgrade from 0.36.0 and eight-second cold launch on MTC_API35. Physical-device testing is outside this scope.

Production 0.37.0/API 2026.37/form 2026.08.5 was activated and read-only verified on 16 October 2026 after Desktop 1.18.0 passed installation verification. Settings settings-20261016-113033 preserves all prior numeric limits and enables only the seven new production fields by operation status. Public APK hash and exact active Settings/form payloads match. The provider transaction added one record per configuration table and three audit records; business counts and foreign-key integrity remain unchanged. No application session or new push notification was created.

## Operations

Provider configuration deployments use `ota.release.config_deploy`, with explicit audit, backup and rollback verification. They create no application login session and send no new push notification. Publisher state recognizes these records and avoids duplicate activation/notification.

The previous [0.36.0 APK](releases/v0.36.0/app-release.apk) remains available for rollback. Do not downgrade the desktop while packages using the newer contract await import.
