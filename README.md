# mtc-apk-releases

Public APK release artifacts for the MTC Maintenance internal OTA channel. This repository contains distributable APK files and release metadata only; application source code, credentials, temporary test files, and private operational data must not be committed here.

## Latest Release

- Version: `0.10.0`
- Version code: `34`
- APK: [`releases/v0.10.0/app-release.apk`](releases/v0.10.0/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.10.0/app-release.apk`
- SHA-256: `7ac7bec118a7d1e3ba85af4918bc9d186b4a87ef8ed76697178351befc304ea0`
- Live manifest: `https://mtc-maintenance-api.iathaariq10.workers.dev/v1/update/manifest`

Release `0.10.0` polishes the member and admin workflows, keeps each machine as one
five-form submission package, applies operation-status field access consistently on
APK and EXE, and delivers important background notifications through high-priority
FCM data messages. Pairing, batch review, checked-PDF mapping, and PC import were
verified together in a controlled live trial.

## Publishing Rules

1. Never replace an APK under an existing version path. Publish a new version directory instead.
2. Update this README and `CHANGELOG.md` in the same commit as every APK or manifest-related change, including patch/minor/major changes.
3. Verify the release signature and compare the local APK SHA-256 with the public URL and live OTA manifest before announcing availability.
4. Keep version name, version code, download URL, hash, and release notes synchronized.
5. Do not commit signing keys, API tokens, service-account files, user data, test evidence, or backup artifacts.
