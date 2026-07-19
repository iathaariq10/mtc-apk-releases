# mtc-apk-releases

Public APK release artifacts for the MTC Maintenance internal OTA channel. This repository contains distributable APK files and release metadata only; application source code, credentials, temporary test files, and private operational data must not be committed here.

## Latest Release

- Version: `0.10.1`
- Version code: `35`
- APK: [`releases/v0.10.1/app-release.apk`](releases/v0.10.1/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.10.1/app-release.apk`
- SHA-256: `cb0eec8f06af5a2c367e9a1515eaae85c4d914f1485379ef379d5d201f82b8c7`
- Live manifest: `https://mtc-maintenance-api.iathaariq10.workers.dev/v1/update/manifest`

Release `0.10.1` keeps the `0.10.0` member/admin workflow and fixes Firebase token
registration by using the current `register()`/`onRegistered` API while retaining
legacy refresh compatibility. Important background notifications remain high-priority
FCM data messages. The binary was installed and background-tested on Samsung
`SM-F956B`.

The live D1 manifest serves `0.10.1` with minimum version `0.8.0`, form contract
`checksheet-package-2026.08.1`, a matching artifact hash, and `force_update=false`.

## Publishing Rules

1. Never replace an APK under an existing version path. Publish a new version directory instead.
2. Update this README and `CHANGELOG.md` in the same commit as every APK or manifest-related change, including patch/minor/major changes.
3. Verify the release signature and compare the local APK SHA-256 with the public URL and live OTA manifest before announcing availability.
4. Keep version name, version code, download URL, hash, and release notes synchronized.
5. Do not commit signing keys, API tokens, service-account files, user data, test evidence, or backup artifacts.
