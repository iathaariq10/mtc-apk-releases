# mtc-apk-releases

Public APK release artifacts for the MTC Maintenance internal OTA channel. This repository contains distributable APK files and release metadata only; application source code, credentials, temporary test files, and private operational data must not be committed here.

## Latest Release

- Version: `0.13.0`
- Version code: `44`
- APK: [`releases/v0.13.0/app-release.apk`](releases/v0.13.0/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.13.0/app-release.apk`
- SHA-256: `d7e00eefb29f291266f30902cf44bc8285dde864cda15609efeef626242b3233`
- Live manifest: `https://mtc-maintenance-api.iathaariq10.workers.dev/v1/update/manifest`

Release `0.13.0` replaces manual daily shift assignment with a two-day rotation and
member self-claim. The APK keeps expected and actual members separate, requires a
replacement reason when they differ, and records `Produksi`, `Idle`, or `Off` for all
six machines in every Shift 2/3 slot. Only production machines open the 40-point
checksheet; the entire slot remains one reviewable submission.

## Publishing Rules

1. Never replace an APK under an existing version path. Publish a new version directory instead.
2. Update this README and `CHANGELOG.md` in the same commit as every APK or manifest-related change, including patch/minor/major changes.
3. Verify the release signature and compare the local APK SHA-256 with the public URL and live OTA manifest before announcing availability.
4. Keep version name, version code, download URL, hash, and release notes synchronized.
5. Do not commit signing keys, API tokens, service-account files, user data, test evidence, or backup artifacts.
