# mtc-apk-releases

Public APK release artifacts for the MTC Maintenance internal OTA channel. This repository contains distributable APK files and release metadata only; application source code, credentials, temporary test files, and private operational data must not be committed here.

## Latest Release

- Version: `0.19.3`
- Version code: `54`
- APK: [`releases/v0.19.3/app-release.apk`](releases/v0.19.3/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.19.3/app-release.apk`
- SHA-256: `3d3ea52a090bddca13dafd9a48d9cb84f028ddf238adae1a1346cdcc8d7f54a1`
- Intended OTA policy: minimum `0.19.2`, `force_update=true`.

Release `0.19.3` keeps the previous Shift 3 context available at the exact 06:00 WITA
boundary, permits same-calendar-day catch-up with a mandatory late reason, and exposes
same-day correction from two-hour history. At 22:00-23:59, every still-valid Shift 2
or Shift 3 context remains selectable instead of hiding the earlier morning context.

Shift 1 checked PDFs now load Downtime and Work Order data across all three shifts for
the same operational date, owner, and machines. Members can also create a standalone
dated Downtime/Work Order PDF from either operations menu without requiring a Shift 1
checksheet. Worker API `2026.19` and operations contract `2026.17.0` are active; the
slot payload remains `shift-slot-2026.13.0` and no D1 schema migration was required.

The signed artifact passed focused Python/Worker/Kotlin tests, lint vital, one focused
standalone-PDF instrumentation test, signature verification, install, and cold launch
on `MTC_API35`. Focused staging acceptance verified the Shift 3 06:00 catch-up and
cleanup. Physical-device and broad UI testing were not run. The OTA manifest remains
on `0.19.2` until this public artifact is fetched and its hash is verified.

## Previous Release 0.19.2

- Version: `0.19.2`
- Version code: `53`
- APK: [`releases/v0.19.2/app-release.apk`](releases/v0.19.2/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.19.2/app-release.apk`
- SHA-256: `5b78dffbeb6d70f399dcf80fce0cba53d62194abb8590c76c259108957202613`
- Final OTA policy before `0.19.3`: minimum `0.19.1`, `force_update=true`.

Release `0.19.2` preserves unfinished Shift 1 and two-hour checksheet work when a
member changes tabs, opens another application, presses Back, or Android recreates the
Activity. Normal edits are autosaved without blocking; Activity stop and explicit
two-hour saves flush durably. Two-hour drafts remain isolated by owner/run/slot and
correction submission revision, while successful submission cannot recreate a final
draft. Worker `2026.18` and operations contract `2026.16.0` remain unchanged.

The signed artifact passed 80 Android unit tests, focused draft/lifecycle
instrumentation, one responsive screenshot flow at two viewports, lint vital, signature
verification, install, and emulator cold launch. Physical-device and broad UI testing
were not run.
The public download and live OTA manifest match this artifact byte-for-byte. The live
manifest exposes `0.19.2`, minimum `0.19.1`, API `2026.18`, and
`force_update=true`. Clients `0.18.0` and `0.19.0` are below minimum, client `0.19.1`
is blocked by the forced-update policy, and `0.19.2` reaches the normal authentication
boundary. A verified D1 backup preceded activation; the post-release audit found one
active manifest, one active operations contract, clean foreign keys, and no
trial/acceptance-pattern rows.

## Previous Release 0.19.1

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
The final `0.19.1` policy before `0.19.2` activation used minimum `0.19.0` and
`force_update=false`.

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
