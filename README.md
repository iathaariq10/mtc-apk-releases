# mtc-apk-releases

Public APK release artifacts for the MTC Maintenance internal OTA channel. This repository contains distributable APK files and release metadata only; application source code, credentials, temporary test files, and private operational data must not be committed here.

## Latest Release

- Version: `0.9.1`
- Version code: `32`
- APK: [`releases/v0.9.1/app-release.apk`](releases/v0.9.1/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.9.1/app-release.apk`
- SHA-256: `dd523032ffd4eff4fcd9752af94a69934670888bc9ef4457c57db68cee7ceaa9`
- Live manifest: `https://mtc-maintenance-api.iathaariq10.workers.dev/v1/update/manifest`

Release `0.9.1` keeps one five-form package per machine and hardens its data boundary:
the Worker derives operator identity from the authenticated member, validates the live
Settings/form/date/options/ranges, keeps the admin approver separate, and permits EXE
import only from a valid Approved envelope. The APK also blocks future dates and uses
the active bootstrap Settings version.

## Publishing Rules

1. Never replace an APK under an existing version path. Publish a new version directory instead.
2. Update this README and `CHANGELOG.md` in the same commit as every APK or manifest-related change, including patch/minor/major changes.
3. Verify the release signature and compare the local APK SHA-256 with the public URL and live OTA manifest before announcing availability.
4. Keep version name, version code, download URL, hash, and release notes synchronized.
5. Do not commit signing keys, API tokens, service-account files, user data, test evidence, or backup artifacts.
