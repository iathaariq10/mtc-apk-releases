# mtc-apk-releases

Public APK release artifacts for the MTC Maintenance internal OTA channel. This repository contains distributable APK files and release metadata only; application source code, credentials, temporary test files, and private operational data must not be committed here.

## Latest Release

- Version: `0.22.0`
- Version code: `57`
- APK: [`releases/v0.22.0/app-release.apk`](releases/v0.22.0/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.22.0/app-release.apk`
- SHA-256: `e81f243cc6382dc557207abab69eac739466f65bdbc9bfe995a5a132d4ece066`
- OTA rollout target: minimum `0.19.3`, `force_update=true`.

Release `0.22.0` simplifies the Warehouse organization to one operational role,
`Admin Gudang Sparepart`. That role can manage master parts, private part photos,
requests, receipts, issues, returns, transfers, adjustments, reports, and Stock Count
from both APK and EXE. The existing Maintenance superadmin/TL remains unchanged for
Maintenance and receives only Warehouse read/report access plus reminders; the legacy
Warehouse Supervisor role is inactive and has no account.

Barcode scanning and barcode master data were removed from the APK workflow. Parts
are now found by code/name and represented by one authenticated JPEG, PNG, or WebP
photo stored privately in R2. Worker API `2026.22` and the guarded photo/role D1
migration are active in production. The production `adminsprt` account was replaced
audit-safely and verified with exactly the Warehouse workspace and 11 capabilities.

The signed artifact passed Android unit `87/87`, responsive emulator `5/5` across 17
screenshots, Stock Count resilience `4/4`, Activity recreation `1/1`, lint, release
build, signature verification, install, and cold launch on the drive-D-backed
`MTC_API35` emulator. Worker `105/105`, Python `202/202`, migration `6/6`, backup
recovery/rollback, and controlled staging inventory/photo acceptance also passed.
No physical device was used.

The public download, local signed artifact, and live manifest match at 14,182,465 bytes
and SHA-256 `e81f243cc6382dc557207abab69eac739466f65bdbc9bfe995a5a132d4ece066`.
The manifest exposes `0.22.0`, minimum `0.19.3`, API `2026.22`, form `2026.08.4`, and
`force_update=true`. Clients `0.19.2`, `0.19.3`, `0.20.0`, and `0.21.0` receive HTTP
426 on business routes, while `0.22.0` reaches the normal authentication boundary.
The downloaded public APK installed and cold-launched in 4,876 ms on `MTC_API35`; its
process remained alive and the crash buffer was clean.

## Previous Release 0.21.0

- Version: `0.21.0`
- Version code: `56`
- APK: [`releases/v0.21.0/app-release.apk`](releases/v0.21.0/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.21.0/app-release.apk`
- SHA-256: `9f83835dbc9e53f5bcb6130cf96c8feb21d3ac15288a74a650bc2da8ce72a172`
- OTA rollout target: minimum `0.19.3`, `force_update=true`.

Release `0.21.0` adds additive access profiles and a dedicated Warehouse workspace
without changing the legacy Maintenance role projection. Warehouse users can manage
requests, scan/search parts, view stock, post capability-gated online transactions,
and complete resilient Stock Count sessions. Inventory balances remain server-owned;
the APK has no offline inventory outbox.

Worker API `2026.21`, the guarded D1 access/inventory schema, access control, and the
Warehouse flag are active in production. The controlled production account uses the
least-privilege `warehouse_admin` role; read-only verification reached one warehouse
and three seeded locations while Maintenance access remained denied. Staging acceptance
covered role isolation, transaction lifecycle, append-only movement guards, freeze,
idempotency, and Stock Count, then removed all trial business rows.

The signed artifact passed Worker `103/103`, Python `200/200`, migration `4/4`,
Android unit `87/87`, responsive emulator `6/6`, Stock Count resilience `4/4`,
Activity recreation `1/1`, real QR decode `1/1`, lint, signature verification,
install, and release cold launch on the drive-D-backed `MTC_API35` emulator. No
physical device was used. The public download, live manifest, and local artifact
match at 13,812,896 bytes and SHA-256
`9f83835dbc9e53f5bcb6130cf96c8feb21d3ac15288a74a650bc2da8ce72a172`.
The manifest exposes `0.21.0`, minimum `0.19.3`, API `2026.21`, and
`force_update=true`; clients `0.19.2`, `0.19.3`, and `0.20.0` receive HTTP 426,
while `0.21.0` reaches the normal authentication boundary. The downloaded APK
installed and cold-launched in 1,978 ms on `MTC_API35`; its process remained alive
and the crash buffer was clean.

## Previous Release 0.20.0

- Version: `0.20.0`
- Version code: `55`
- APK: [`releases/v0.20.0/app-release.apk`](releases/v0.20.0/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.20.0/app-release.apk`
- SHA-256: `8d9ee9eb52550f418967444a5940661352c8ded8cad35befaa29e900e14e8199`
- OTA rollout target: minimum `0.19.3`, `force_update=true`.

Release `0.20.0` treats the Shift 1 checksheet schedule as one inclusive two-day
block. A submission on either day completes the machine target for the block; a
second package for the same machine is rejected and correction continues through
history. Shift 1 and two-hour submissions remain editable by their owner until an
admin finalizes them.

Members can reopen their Downtime report or a submitted Work Order result while it is
still awaiting verification. Every mutable review action carries the displayed
revision, so stale admin decisions are rejected. Worker API `2026.20` and operations
contract `2026.18.0` are deployed; no D1 schema migration was required.

The signed artifact passed Python `193/193`, Worker `96/96`, Android unit `85/85`,
lint vital, signature verification, and release build. Controlled staging acceptance
verified revision/import/PDF, FID registration for `anggota`, `admin`, and
`super_admin`, plus one visible diagnostic notification while the APK was background,
then cleaned every trial marker. The production backup
restored with 43 tables, 54 indexes, 36 triggers, integrity `ok`, and clean foreign
keys. Physical-device and broad UI testing were not run. Its final manifest state
before `0.21.0` activation used minimum `0.19.3`, API `2026.20`, and
`force_update=true`.
The public download and manifest match the local signed artifact byte-for-byte;
`0.19.2` is below minimum, `0.19.3` is blocked by forced update, and `0.20.0`
reaches the normal authentication boundary. The downloaded APK installed and
cold-launched successfully on `MTC_API35` with a clean crash buffer.

## Previous Release 0.19.3

- Version: `0.19.3`
- Version code: `54`
- APK: [`releases/v0.19.3/app-release.apk`](releases/v0.19.3/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.19.3/app-release.apk`
- SHA-256: `3d3ea52a090bddca13dafd9a48d9cb84f028ddf238adae1a1346cdcc8d7f54a1`
- Final OTA policy before `0.20.0`: minimum `0.19.2`, `force_update=true`.

Release `0.19.3` kept the Shift 3 context at 06:00 WITA, enabled same-day catch-up
and correction, expanded Shift 1 PDF operations data across shifts, and added a
standalone dated Downtime/Work Order PDF.

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
