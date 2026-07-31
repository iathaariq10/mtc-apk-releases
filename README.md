# mtc-apk-releases

Public APK release artifacts for the MTC Maintenance internal OTA channel. This repository contains distributable APK files and release metadata only; application source code, credentials, temporary test files, and private operational data must not be committed here.

## Latest Release

- Version: `0.15.0`
- Version code: `47`
- APK: [`releases/v0.15.0/app-release.apk`](releases/v0.15.0/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.15.0/app-release.apk`
- SHA-256: `d21612a46cc19fd1ad0f6712e334d20488c797bd0f2ec4cfc78c90a1b58c62b4`
- Live manifest: `https://mtc-maintenance-api.iathaariq10.workers.dev/v1/update/manifest`

Release `0.15.0` adds explicit `-` (N/A) input to all applicable two-hour numeric,
condition, leak, and Cooling Tower fields. Blank values remain incomplete, disabled
fields are normalized to `-`, zero remains a real measurement, and Hopper Dryer keeps
the dedicated `On`/`Off` choice.

## Publishing Rules

1. Never replace an APK under an existing version path. Publish a new version directory instead.
2. Update this README and `CHANGELOG.md` in the same commit as every APK or manifest-related change, including patch/minor/major changes.
3. Verify the release signature and compare the local APK SHA-256 with the public URL and live OTA manifest before announcing availability.
4. Keep version name, version code, download URL, hash, and release notes synchronized.
5. Do not commit signing keys, API tokens, service-account files, user data, test evidence, or backup artifacts.
