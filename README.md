# mtc-apk-releases

Public APK release artifacts for the MTC Maintenance internal OTA channel. This repository contains distributable APK files and release metadata only; application source code, credentials, temporary test files, and private operational data must not be committed here.

## Latest Release

- Version: `0.19.1`
- Version code: `52`
- APK: [`releases/v0.19.1/app-release.apk`](releases/v0.19.1/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.19.1/app-release.apk`
- SHA-256: `a51b8b72ca027bc16bb0a1a9fee027c5ecaa6b29258b04f6a3aaafa59cfe795b`
- OTA policy: minimum `0.19.0`, `force_update=false`.

Release `0.19.1` replaces remaining manual date inputs with calendar controls across
schedule, history/filter, operations, Work Order, and related administration flows.
The two-hour PDF now uses vertically merged `Area / Checkpoint / Item` descriptors
while keeping each slot value separate. Worker `2026.18` and operations contract
`2026.16.0` remain compatible and unchanged. Signed build, focused calendar/PDF tests,
visual PDF review, responsive screenshot, and emulator cold launch passed.
The public download and live OTA manifest match this artifact byte-for-byte. The live
manifest exposes `0.19.1`, minimum `0.19.0`, API `2026.18`, and
`force_update=false`; the production hygiene audit found no trial data.

## Previous Release 0.19.0

- Version: `0.19.0`
- Version code: `51`
- APK: [`releases/v0.19.0/app-release.apk`](releases/v0.19.0/app-release.apk)
- SHA-256: `2af1dd360b5cd4122eada666637c03011eef3a7675435a6d49499c84a556a238`
- Final policy before `0.19.1`: minimum `0.18.0`, `force_update=true`.

Release `0.19.0` fixed the two-hour PDF share crash, added actual downtime recovery
time, calendar-based shift compliance, and restricted manual `-` to numeric fields.

## Previous Release 0.18.0

- Version: `0.18.0`
- Version code: `50`
- APK: [`releases/v0.18.0/app-release.apk`](releases/v0.18.0/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.18.0/app-release.apk`
- SHA-256: `82d93a31048d34eb28c4fbad4a186c083553cc618611463483cc6bb0299a2463`
- Final live policy before `0.19.0` activation: minimum `0.18.0`,
  `force_update=true`
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
