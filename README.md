# mtc-apk-releases

Public APK release artifacts for the MTC Maintenance internal OTA channel. This repository contains distributable APK files and release metadata only; application source code, credentials, temporary test files, and private operational data must not be committed here.

## Latest Release

- Version: `0.10.5`
- Version code: `39`
- APK: [`releases/v0.10.5/app-release.apk`](releases/v0.10.5/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.10.5/app-release.apk`
- SHA-256: `4d56b01ce855ceb37c7df72b293ccd9c925bfaf557232698866bcd70e2948965`
- Live manifest: `https://mtc-maintenance-api.iathaariq10.workers.dev/v1/update/manifest`

Release `0.10.5` moves notifications to a bell in the top-right application header
with an active-event badge and removes notification history from `Lainnya`. Worker
events are persisted per user and sent as Android-priority `HIGH`, data-only FCM so
the APK service can display them in the notification bar while the app is in the
background. Opening an event consumes and deletes it.

The release also adds server-side daily schedule reminders and push coverage for
review/import, pairing, account/settings, OTA, security, and operational state
changes. The live checksheet contract remains `checksheet-package-2026.08.2`.

## Publishing Rules

1. Never replace an APK under an existing version path. Publish a new version directory instead.
2. Update this README and `CHANGELOG.md` in the same commit as every APK or manifest-related change, including patch/minor/major changes.
3. Verify the release signature and compare the local APK SHA-256 with the public URL and live OTA manifest before announcing availability.
4. Keep version name, version code, download URL, hash, and release notes synchronized.
5. Do not commit signing keys, API tokens, service-account files, user data, test evidence, or backup artifacts.
