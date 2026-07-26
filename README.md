# mtc-apk-releases

Public APK release artifacts for the MTC Maintenance internal OTA channel. This repository contains distributable APK files and release metadata only; application source code, credentials, temporary test files, and private operational data must not be committed here.

## Latest Release

- Version: `0.10.4`
- Version code: `38`
- APK: [`releases/v0.10.4/app-release.apk`](releases/v0.10.4/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.10.4/app-release.apk`
- SHA-256: `2e1c8d8d75276644f9d77bbbe03729baed70258c5c2df149f8578e5ec9b28fa4`
- Live manifest: `https://mtc-maintenance-api.iathaariq10.workers.dev/v1/update/manifest`

Release `0.10.4` completes the `Lainnya` workflow cleanup: role-aware navigation,
safe confirmations and loading states, device-scoped pairing status, notification
history, stricter account administration, and explicit empty/error states. Mold input
now always provides `-` for machines without an installed mold.

Hopper Dryer now follows Production's On/Off decision. MTC measurement fields are
required only while it is On, remain governed by per-machine Settings, and are sent as
`-` while Off. The live contract is `checksheet-package-2026.08.2`.

## Publishing Rules

1. Never replace an APK under an existing version path. Publish a new version directory instead.
2. Update this README and `CHANGELOG.md` in the same commit as every APK or manifest-related change, including patch/minor/major changes.
3. Verify the release signature and compare the local APK SHA-256 with the public URL and live OTA manifest before announcing availability.
4. Keep version name, version code, download URL, hash, and release notes synchronized.
5. Do not commit signing keys, API tokens, service-account files, user data, test evidence, or backup artifacts.
