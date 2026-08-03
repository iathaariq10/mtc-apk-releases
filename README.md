# mtc-apk-releases

Public APK release artifacts for the MTC Maintenance internal OTA channel. This repository contains distributable APK files and release metadata only; application source code, credentials, temporary test files, and private operational data must not be committed here.

## Latest Release

- Version: `0.18.0`
- Version code: `50`
- APK: [`releases/v0.18.0/app-release.apk`](releases/v0.18.0/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.18.0/app-release.apk`
- SHA-256: `82d93a31048d34eb28c4fbad4a186c083553cc618611463483cc6bb0299a2463`
- OTA policy: minimum `0.13.1`, `force_update=false`
- Live manifest: `https://mtc-maintenance-api.iathaariq10.workers.dev/v1/update/manifest`

Release `0.18.0` completes the two-hour checksheet workflow with mold configuration,
draft/revision history, late-reason handling, admin review, and a 500 C Thermobox
limit. It also adds sparepart usage to Downtime/Work Order, role-correct FID push
registration, clear notifications, and a dated PDF with one combined operations page.

## Publishing Rules

1. Never replace an APK under an existing version path. Publish a new version directory instead.
2. Update this README and `CHANGELOG.md` in the same commit as every APK or manifest-related change, including patch/minor/major changes.
3. Verify the release signature and compare the local APK SHA-256 with the public URL and live OTA manifest before announcing availability.
4. Keep version name, version code, download URL, hash, and release notes synchronized.
5. Do not commit signing keys, API tokens, service-account files, user data, test evidence, or backup artifacts.
