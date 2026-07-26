# mtc-apk-releases

Public APK release artifacts for the MTC Maintenance internal OTA channel. This repository contains distributable APK files and release metadata only; application source code, credentials, temporary test files, and private operational data must not be committed here.

## Latest Release

- Version: `0.10.3`
- Version code: `37`
- APK: [`releases/v0.10.3/app-release.apk`](releases/v0.10.3/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.10.3/app-release.apk`
- SHA-256: `2908dbf91e5f59e0e14d25f97308d4c72d9dab439759613aa86d6e8b493bfe66`
- Live manifest: `https://mtc-maintenance-api.iathaariq10.workers.dev/v1/update/manifest`

Release `0.10.3` fixes the `Lainnya` navigation hierarchy. Child screens now provide
an explicit return action, Android Back returns to the originating primary tab, unknown
or unauthorized routes fall back safely to Beranda, and menu entries explain their
purpose more clearly for members and administrators.

The live D1 manifest serves `0.10.3` with minimum version `0.8.0`, form contract
`checksheet-package-2026.08.1`, a matching artifact hash, and `force_update=false`.

## Publishing Rules

1. Never replace an APK under an existing version path. Publish a new version directory instead.
2. Update this README and `CHANGELOG.md` in the same commit as every APK or manifest-related change, including patch/minor/major changes.
3. Verify the release signature and compare the local APK SHA-256 with the public URL and live OTA manifest before announcing availability.
4. Keep version name, version code, download URL, hash, and release notes synchronized.
5. Do not commit signing keys, API tokens, service-account files, user data, test evidence, or backup artifacts.
