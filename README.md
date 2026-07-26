# mtc-apk-releases

Public APK release artifacts for the MTC Maintenance internal OTA channel. This repository contains distributable APK files and release metadata only; application source code, credentials, temporary test files, and private operational data must not be committed here.

## Latest Release

- Version: `0.10.7`
- Version code: `41`
- APK: [`releases/v0.10.7/app-release.apk`](releases/v0.10.7/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.10.7/app-release.apk`
- SHA-256: `c1ebf18d2eae8e885cebe2703b058463069561512e470d26a23e4992021814a5`
- Live manifest: `https://mtc-maintenance-api.iathaariq10.workers.dev/v1/update/manifest`

Release `0.10.7` removes the duplicate Mold input from Limit Switch. Mold is now
owned only by Checksheet Mesin, while the five-form package remains compatible with
legacy `checksheet-package-2026.08.2` submissions during the rollout transition.
The active contract is `checksheet-package-2026.08.3`.

## Publishing Rules

1. Never replace an APK under an existing version path. Publish a new version directory instead.
2. Update this README and `CHANGELOG.md` in the same commit as every APK or manifest-related change, including patch/minor/major changes.
3. Verify the release signature and compare the local APK SHA-256 with the public URL and live OTA manifest before announcing availability.
4. Keep version name, version code, download URL, hash, and release notes synchronized.
5. Do not commit signing keys, API tokens, service-account files, user data, test evidence, or backup artifacts.
