# mtc-apk-releases

Public APK artifacts and a guarded HTTPS OTA publisher. Source code, credentials and operational data stay outside this repository.

## Latest artifact: 0.36.0

- APK: [app-release.apk](releases/v0.36.0/app-release.apk), version code 71.
- SHA-256: `43d4ac9b9b44e942febd3426abdf669110cd6ff7275efc251cfb3e008b1cec97`; 14,444,609 bytes.
- API remains `2026.35`; minimum APK `0.19.3`, mandatory-update policy retained.
- Direct PDF export from the member's inspection, compact maintenance/warehouse navigation, flowing A4 portrait DT/WO PDF, and account/month-bound warehouse exports.
- Verified: 105 Android unit tests, lint, affected compact-screen trials, matching public v2 signer, upgrade from 0.35.0 and 8-second cold launch on MTC_API35. Physical-device testing is outside this release scope.

Production manifest 0.36.0 was activated and verified on 16 October 2026 after the public HTTPS APK hash matched. A guarded Cloudflare OAuth configuration deployment added one release and one provider audit record, preserving business rows and the previous release. Backup recovery verified 75 tables, 94 indexes, 107 triggers and zero foreign-key violations. No app session was created and no new push notification was sent.

## OTA operations

The [HTTPS publisher](https://iathaariq10.github.io/mtc-apk-releases/) accepts only the exact known 0.35.0 or target 0.36.0 manifest. It checks health and complete audit history before a genuine Superadmin session can publish. Unknown metadata, races and uncertain outcomes stop repeated submission. Passwords and bearer tokens are not persisted.

Provider configuration deployments are recorded separately as `ota.release.config_deploy`. The publisher recognizes that record and avoids sending another activation/notification for an already deployed target. A configuration deployment does not claim that an app Superadmin logged in or that a push notification was sent.

## Rollback

The [previous public APK 0.35.0](releases/v0.35.0/app-release.apk) remains available. Preserve server decisions, revision history and the recorded manifest when rolling back.
