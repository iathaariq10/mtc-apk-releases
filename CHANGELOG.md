# Changelog

Every OTA artifact or metadata change must be recorded here in the same commit.

## 0.26.0 - 2026-09-01

### Added

- Add one derived Shift closeout status for Checksheet, Downtime, Work Order, and
  explicit sparepart-use decisions, including a direct action to the first incomplete
  section.
- Add server-side approval guards for Shift 1 and two-hour submissions while keeping
  explicit no-Downtime and zero-Work-Order shifts valid.

### Changed

- Save the member draft before closeout preflight and fail closed on an unavailable
  preflight instead of queuing an incomplete checksheet package.
- Use Worker API `2026.26`; keep D1 schema, Warehouse roles, single-location inventory,
  and minimum APK `0.19.3` unchanged.

### Verified

- APK is 14,264,385 bytes with SHA-256
  `b5af2ed7bed61b2008b69f5a417986c63a9c4459ee9e6fd6c304f871446bf91a`, one signer,
  and APK Signature Scheme v2 verification.
- Android unit `92/92`, focused operations/responsive instrumentation `10/10`, Worker
  `116/116`, lint/release build, install, and cold launch passed on the drive-D-backed
  `MTC_API35` AVD. No physical device was used.
- Staging acceptance reached closeout `3/3`, preserved Warehouse stock, deleted the
  private R2 object, removed all trial rows, and left foreign keys clean. Production
  backup restored with 63 tables, 72 indexes, 72 triggers, integrity `ok`, and clean
  foreign keys before Worker deployment.

## 0.25.0 - 2026-08-23

### Added

- Give the sole `Admin Gudang Sparepart` complete master-part and stock controls in
  both APK and EXE, including create/edit/rename, archive/reactivate, photo,
  receipt, issue, return, adjustment, verification, Stock Count, and reporting.
- Add explicit one-location guards so all new balances, movements, reservations,
  and Stock Count sessions use `Gudang Sparepart`.

### Changed

- Remove receiving, quarantine, rack-transfer, and barcode concepts from the daily
  Warehouse UI while preserving historical location rows as inactive records.
- Keep the Maintenance TL limited to Warehouse viewing, reports, and reminders;
  operational stock authority remains with `warehouse_admin` only.
- Deploy Worker API `2026.25` and target OTA minimum `0.19.3` with
  `force_update=true` for APK `0.25.0` code `60`.

### Fixed

- Restore exact staging cleanup after role-switch and inventory acceptance runs,
  including role assignments and all one-location/delete guards.
- Keep safe transport retries limited to read/login/logout requests so stock writes
  cannot be replayed accidentally after an uncertain network response.

### Verified

- APK is 14,264,385 bytes with SHA-256
  `6dbd0be7da2276641ffd4ca30fb8990a53577afb465a2b832da71ff8699fb517`, one signer,
  and APK Signature Scheme v2 verification.
- Android unit `91/91`, responsive instrumentation `7/7`, Stock Count/recreation
  instrumentation `5/5`, Worker `110/110`, Python `207/207`, release/lint, desktop
  interaction, 22 desktop captures, and signed cold launch passed on the
  drive-D-backed `MTC_API35` AVD. No physical device was used.
- Staging access, inventory, private photo, dated monthly reporting, append-only
  ledger, and full Worker-APK-EXE acceptance passed with exact cleanup and FK zero.
- Production backup SHA-256
  `a0413b2fa9dfeb1d9003b9ac92a7aab706ebbe12d05fa3a8fe01808fa61f46ae` restored,
  migrated to 63 tables/72 indexes/72 triggers, and rolled back to the exact
  baseline. Production Worker version is
  `b3afe484-f19b-4c4c-a51a-143a081f9bfb`; only `location-main` is active and the two
  existing part masters remain unchanged.

## 0.24.0 - 2026-08-23

### Added

- Add a simple Warehouse verification queue for spareparts recorded on final
  Downtime and Work Order data, including idempotent verify/reject and one-time
  return handling for reusable items.
- Add consumable/returnable classification, master-machine/other-machine/general
  application categories, and dated monthly Warehouse reports for Excel and PDF.
- Add direct previous-shift entry points for Downtime and Work Order history.

### Changed

- Simplify the Warehouse APK and EXE navigation around `Beranda`, `Stok`, and
  `Verifikasi`, while keeping stock mutation online and server-authoritative.
- Deploy Worker API `2026.24` and the guarded `20260815_simple_warehouse` D1
  migration. Keep the existing `adminsprt` account and report-only Warehouse access
  for the Maintenance TL.
- Target OTA minimum `0.19.3` with `force_update=true` for APK `0.24.0` code `59`.

### Fixed

- Use the current Asia/Makassar date when Shift 1 opens, preserve server shift dates
  for Shift 2/3, and keep historical pending data revisable until final admin review.
- Make checked-PDF Downtime/Work Order appendices use the same daily all-shift scope
  as standalone exports for Shift 1, Shift 2, and Shift 3.
- Derive automatic inventory and Stock Count movement dates from Asia/Makassar at
  the UTC date boundary.

### Verified

- APK is 14,248,001 bytes with SHA-256
  `927578d8f1781eca186a7451026d1e39ab11e949b872f8368263a6414cb5c6e2`, one signer,
  and APK Signature Scheme v2 verification.
- Android unit `91/91`, Worker `109/109`, Python `206/206`, lint/release build,
  emulator previous-shift UI, install, and cold launch passed. No physical device
  was used.
- Staging and production backups restored with the target 63-table schema, 72
  indexes, 67 triggers, clean foreign keys, and guarded rollback to the exact
  baseline. Staging access and enhanced inventory acceptance passed with 6
  documents, 7 movements, 3 Stock Count sessions, returnable/other-machine
  classification, WITA-dated monthly reporting, private photo coverage, and exact
  cleanup.
- Production Worker version `b2b33e2b-8c3e-4a64-8760-e1e8137ca521`, one active
  manifest, 31 inventory triggers, the existing sole `adminsprt` Warehouse
  assignment, report-only TL capabilities, zero inventory documents/movements, and
  clean foreign keys were verified read-only after deployment.
- The public URL, live manifest, and local APK match at 14,248,001 bytes and SHA-256
  `927578d8f1781eca186a7451026d1e39ab11e949b872f8368263a6414cb5c6e2`.
  The public APK installed and cold-launched on `MTC_API35` in 2,842 ms; its process
  remained alive and the crash buffer was empty.

## 0.22.0 - 2026-08-12

### Added

- Add one authenticated private photo per sparepart, with JPEG/PNG/WebP validation,
  a 3 MiB limit, stable R2 identity, revisioned metadata, and upload/delete controls
  in both APK and EXE.
- Add full master-part and stock-management access for the sole operational
  `Admin Gudang Sparepart` role on both clients.
- Add a daily WITA Warehouse digest for the Admin Gudang and report/reminder-only TL.

### Changed

- Make `warehouse_admin` the only active Warehouse operator role, deactivate the
  legacy `warehouse_supervisor` role, and restrict Maintenance `super_admin` to
  Warehouse view/report access while retaining all existing Maintenance authority.
- Deploy Worker API `2026.22` and the guarded D1 role/photo migration. Replace the
  production `adminsprt` identity audit-safely with a fresh least-privilege account.
- Target OTA minimum `0.19.3` with `force_update=true` for APK `0.22.0` code `57`.

### Removed

- Remove barcode scanning, camera scanner metadata/dependency, and the barcode-first
  APK flow. Spareparts are identified by photo and code/name search.

### Verified

- APK is 14,182,465 bytes with SHA-256
  `e81f243cc6382dc557207abab69eac739466f65bdbc9bfe995a5a132d4ece066`, one signer,
  and APK Signature Scheme v2 verification.
- Worker `105/105`, Python `202/202`, migration `6/6`, Android unit `87/87`, responsive
  emulator `5/5` with 17 screenshots, Stock Count resilience `4/4`, Activity
  recreation `1/1`, lint, signed build, install, and cold launch passed.
- Production/staging backups restored with 62 target tables, 69 indexes, 65 triggers,
  integrity `ok`, clean foreign keys, and rollback to the 61-table baseline. Staging
  access and inventory acceptance passed with 6 documents, 7 movements, 3 Stock
  Count sessions, private R2 photo coverage, append-only guards, and exact cleanup.
- Production has one active Warehouse account, no Supervisor account, clean foreign
  keys, and a verified `adminsprt` login with Warehouse-only access. No physical
  device was used and no mutating production inventory acceptance was run.
- The public URL, live manifest, and local APK match at 14,182,465 bytes and SHA-256
  `e81f243cc6382dc557207abab69eac739466f65bdbc9bfe995a5a132d4ece066`.
  Exactly one manifest is active at `0.22.0`, minimum `0.19.3`, API `2026.22`, form
  `2026.08.4`, and `force_update=true`; clients `0.19.2` through `0.21.0` receive HTTP
  426, while `0.22.0` reaches the normal authentication boundary.
- The downloaded public APK installed and cold-launched on the drive-D-backed
  `MTC_API35` emulator in 4,876 ms. Its process remained alive and the crash buffer
  was clean.

## 0.21.0 - 2026-08-11

### Added

- Add additive access roles, capabilities, workspace selection, and a dedicated
  Warehouse workspace while retaining the legacy Maintenance role projection.
- Add server-owned spare-part master data, aliases/barcodes, per-location balances,
  requests, reservations, immutable documents/movements, and Stock Count sessions.
- Add APK Warehouse home, request, scan/search, stock, online transaction, and
  resilient Stock Count flows with capability-gated actions.

### Changed

- Deploy Worker API `2026.21`, the guarded access/inventory D1 migration, and staged
  access/warehouse feature activation. Keep inventory online-only and fail closed.
- Target OTA minimum `0.19.3` with `force_update=true` for APK `0.21.0` code `56`.

### Verified

- APK is 13,812,896 bytes with SHA-256
  `9f83835dbc9e53f5bcb6130cf96c8feb21d3ac15288a74a650bc2da8ce72a172`, one signer,
  and APK Signature Scheme v2 verification.
- Worker `103/103`, Python `200/200`, migration `4/4`, Android unit `87/87`,
  responsive emulator `6/6`, Stock Count resilience `4/4`, Activity recreation
  `1/1`, real QR decode `1/1`, lint, build, install, and cold launch passed.
- Staging acceptance passed access isolation, inventory lifecycle, append-only
  guards, idempotency, freeze, and Stock Count with exact cleanup. Production was
  migrated after a verified backup/recovery drill and received read-only smoke only.
- Production account isolation, one warehouse, three locations, 25 inventory
  triggers, zero inventory business rows, and clean foreign keys were verified.
  No physical device was used.
- The public URL, live manifest, and local APK match at 13,812,896 bytes and SHA-256
  `9f83835dbc9e53f5bcb6130cf96c8feb21d3ac15288a74a650bc2da8ce72a172`.
  Exactly one manifest is active at `0.21.0`, minimum `0.19.3`, API `2026.21`, and
  `force_update=true`; `0.19.2`, `0.19.3`, and `0.20.0` receive HTTP 426, while
  `0.21.0` reaches the normal authentication boundary.
- The downloaded public APK installed and cold-launched on the drive-D-backed
  `MTC_API35` emulator in 1,978 ms. Its process remained alive, the login screen was
  visible, and the crash buffer was clean.

## 0.20.0 - 2026-08-09

### Changed

- Treat the Shift 1 schedule as one inclusive two-day block. A package submitted on
  either day completes the machine target for that block, while duplicate packages
  are rejected and corrections remain available from history until final review.
- Allow members to revise pending Shift 1/two-hour submissions, Downtime reports, and
  submitted Work Order results; stale admin actions are rejected by revision guard.
- Deploy Worker API `2026.20` and operations contract `2026.18.0` without a D1 schema
  migration. Target OTA policy is minimum `0.19.3` with `force_update=true`.

### Verified

- APK version code `55`, 13,467,495 bytes, SHA-256
  `8d9ee9eb52550f418967444a5940661352c8ded8cad35befaa29e900e14e8199`, one signer,
  and APK Signature Scheme v2 verification passed.
- Python `193/193`, Worker `96/96`, Android unit `85/85`, contract roundtrip, lint
  vital, and signed release build passed. Broad UI and physical-device testing were
  not run.
- Controlled staging acceptance verified package revision/import/PDF, FID registration
  for `anggota`, `admin`, and `super_admin`, and one visible diagnostic notification
  while the APK was background; exact cleanup and foreign-key checks passed.
  Production received no trial data.
- The production backup restored with 43 tables, 54 indexes, 36 triggers, integrity
  `ok`, and clean foreign keys. Worker `c9a45f00-2e2c-4ae8-bf8d-fb26f718eef8` and
  exactly one operations contract `2026.18.0` are active.
- The public URL, live manifest, and local APK match at 13,467,495 bytes and SHA-256
  `8d9ee9eb52550f418967444a5940661352c8ded8cad35befaa29e900e14e8199`.
  The manifest exposes `0.20.0`, minimum `0.19.3`, API `2026.20`, and
  `force_update=true`; `0.19.2` is below minimum, `0.19.3` is blocked by forced
  update, and `0.20.0` reaches the normal authentication boundary.
- The downloaded public APK installed and cold-launched on `MTC_API35` in 1,553 ms;
  its process remained alive and the crash buffer was clean.

## 0.19.3 - 2026-08-07

### Added

- Added standalone daily Downtime/Work Order PDF export for members from both the
  Downtime and Work Order menus, with a calendar and a dated filename.
- Added a same-day correction action for two-hour submissions that are still pending
  review or need correction.

### Changed

- Kept every eligible two-hour context available through the end of the slot's WITA
  calendar day. Catch-up submissions remain late and require a nonblank reason.
- Expanded the Shift 1 checked-PDF operations appendix to Shift 1/2/3 on the same
  operational date, owner, and machines; two-hour PDFs remain exact-shift.
- Activated the forced OTA boundary as minimum `0.19.2`, `force_update=true`, with
  Worker API `2026.19` and operations contract `2026.17.0`.

### Fixed

- Preserved access to the previous Shift 3 and its 06:00 slot when the global shift
  context changes to Shift 1 at exactly 06:00 WITA.
- Prevented an earlier valid Shift 3 context from disappearing at 22:00 while Shift 2
  catch-up is also still available.

### Verified

- APK version code `54`, 13,451,111 bytes, SHA-256
  `3d3ea52a090bddca13dafd9a48d9cb84f028ddf238adae1a1346cdcc8d7f54a1`, one signer,
  and APK Signature Scheme v2 verification passed.
- Focused Python `16/16`, Worker `17/17`, Kotlin unit/compile, lint vital, signed build,
  focused standalone-PDF instrumentation `1/1`, install, and cold launch passed on
  `MTC_API35`; the crash buffer was clean.
- Production/staging backups restored with 43 tables, 54 indexes, 36 triggers,
  integrity `ok`, and clean foreign keys. Staging catch-up acceptance passed and left
  zero temporary users, sessions, devices, runs, submissions, Downtime, and Work Order
  rows. No mutating production acceptance was run.
- The public URL, live manifest, and local APK match at 13,451,111 bytes and SHA-256
  `3d3ea52a090bddca13dafd9a48d9cb84f028ddf238adae1a1346cdcc8d7f54a1`.
  The manifest exposes `0.19.3`, minimum `0.19.2`, API `2026.19`, and
  `force_update=true`; clients `0.19.1` and `0.19.2` receive HTTP 426, while `0.19.3`
  reaches the normal authentication boundary. Exactly one OTA manifest and one
  operations contract remain active; production foreign keys and trial-user checks
  are clean, and operational row counts were unchanged by activation.

## 0.19.2 - 2026-08-04

### Changed

- Added automatic local persistence for Shift 1 and two-hour checksheet edits when
  values change, tabs/screens change, Back is used, or the Activity enters background.
- Added a durable Activity-stop flush and kept the two-hour manual save action as an
  explicit confirmation path. Two-hour drafts remain scoped by owner/run/slot and
  correction submission revision.
- Set the active OTA boundary to minimum `0.19.1` and `force_update=true`, so every
  client below `0.19.2` must install this reliability patch. Worker API, D1 schema, and
  operations contract versions do not change.

### Fixed

- Prevented unfinished checksheet values from disappearing when members temporarily
  leave the form or Android recreates the Activity.
- Prevented a completed two-hour submission from being recreated by a late lifecycle
  callback, and prevented restored editor context from crossing into a different run.

### Verified

- APK version code `53`, 13,434,727 bytes, SHA-256
  `5b78dffbeb6d70f399dcf80fce0cba53d62194abb8590c76c259108957202613`, one signer,
  and APK Signature Scheme v2 verification passed.
- Android unit tests `80/80`, focused draft/lifecycle instrumentation `4/4`, responsive
  screenshot instrumentation `2/2`, lint vital, signed release build, install, and cold
  launch passed on `MTC_API35`. Physical-device and broad UI testing were not run.
- The public URL, live manifest, and local APK match at 13,434,727 bytes and SHA-256
  `5b78dffbeb6d70f399dcf80fce0cba53d62194abb8590c76c259108957202613`.
  The manifest exposes `0.19.2`, minimum `0.19.1`, API `2026.18`, and
  `force_update=true`; versions `0.18.0`, `0.19.0`, and `0.19.1` receive HTTP 426,
  while `0.19.2` reaches the normal authentication boundary.
- A full D1 backup preceded activation and restored with 43 tables, 54 indexes, 36
  triggers, integrity `ok`, and clean foreign keys. Exactly one OTA manifest and one
  operations contract remain active; trial-pattern counts are zero across users,
  sessions, devices, push targets, notifications, checksheets, two-hour slots,
  downtime, and Work Orders.

## 0.19.1 - 2026-08-04

### Changed

- Replaced remaining manual date inputs with calendar controls in schedule, history
  filters, two-hour history, Work Order, and related APK/EXE operational flows.
- Reworked the two-hour PDF descriptor table into `Area / Checkpoint / Item`, with
  consecutive Area and Checkpoint cells vertically merged while every Item and slot
  value remains separate.
- Set the active OTA boundary to minimum `0.19.0` and `force_update=false`; this
  client-only patch does not change Worker API or operations contract versions.

### Verified

- APK version code `52`, 13,434,727 bytes, SHA-256
  `a51b8b72ca027bc16bb0a1a9fee027c5ecaa6b29258b04f6a3aaafa59cfe795b`, one signer,
  and APK Signature Scheme v2 verification passed.
- Focused Python/Kotlin tests, lint vital, release build, four calendar/PDF emulator
  cases, responsive screenshot flow, seven-page APK PDF render, and signed cold launch
  passed on `MTC_API35`. Physical-device and broad UI testing were not run.
- The public URL, live manifest, and local APK match at 13,434,727 bytes and SHA-256
  `a51b8b72ca027bc16bb0a1a9fee027c5ecaa6b29258b04f6a3aaafa59cfe795b`.
  The manifest exposes `0.19.1`, minimum `0.19.0`, API `2026.18`, and
  `force_update=false`; `0.18.0` receives HTTP 426 while `0.19.0` and `0.19.1`
  reach the normal authentication boundary.
- A full D1 backup preceded activation. Exactly one OTA manifest and one operations
  contract remain active, foreign keys are clean, and trial-pattern counts are zero
  across users, sessions, notifications, checksheets, two-hour slots, downtime, and
  Work Orders.

## 0.19.0 - 2026-08-04

### Changed

- Restricted the explicit two-hour `Tidak Berlaku (-)` choice to numeric fields.
  Enabled condition and leak checks now require `OK/NG` or `centang/X`; disabled and
  historical legacy values remain compatible.
- Replaced manual shift-compliance date text with a calendar that automatically loads
  Compliance, Review, or Member Results for the selected date.
- Combined downtime occurrence, actual recovery, corrective action, root cause, and
  sparepart usage in one member form, while retaining open-event and next-shift
  handover paths.

### Fixed

- Fixed the two-hour PDF share crash by aligning the cache path with `FileProvider`,
  granting read access through `ClipData`, and returning share/create errors to the UI.

### Verified

- APK version code `51`, 13,418,343 bytes, SHA-256
  `2af1dd360b5cd4122eada666637c03011eef3a7675435a6d49499c84a556a238`, and APK
  Signature Scheme v2 verification passed.
- Focused workflow UI `3/3`, PDF exporter `1/1`, and actual Android system chooser
  `1/1` passed on `MTC_API35`; broad UI and physical-device testing were not run.
- Staging acceptance passed the two-hour operations/private-R2 round-trip, package
  revision/import/PDF, FID registration for `anggota`, `admin`, and `super_admin`, and
  a visible background notification. Exact trial cleanup and foreign-key checks passed.
- Production D1 backup restored successfully with 43 tables, integrity `ok`, and zero
  foreign-key violations. Worker `2026.18` and operations contract `2026.16.0` /
  `shift-slot-2026.13.0` are active; production retained eight Shift 1 submissions,
  six two-hour submissions, and two downtime events with zero trial rows.
- Public URL and manifest hashes match the local artifact. The live manifest exposes
  `0.19.0`, minimum `0.18.0`, API `2026.18`, and `force_update=true`; `0.18.0` receives
  HTTP 426 while `0.19.0` reaches the normal authentication boundary. The downloaded
  public APK installed and cold-launched on `MTC_API35` with no crash marker.

## 0.18.0 - 2026-08-03

The manifest was subsequently tightened to minimum `0.18.0` with
`force_update=true`; that was the observed live boundary immediately before `0.19.0`
activation.

### Added

- Added mold name plus Slider, Sayap, and Eject configuration to each production
  machine in the Shift 2/3 two-hour checksheet.
- Added editable local drafts, Pending Review revision, member history/PDF export,
  late-reason capture after the on-time window, and admin two-hour review access.
- Added sparepart name, quantity, and unit to Downtime and Work Order records and to
  their single combined PDF summary page.
- Added clear-notification controls and Firebase Installation registration for
  `anggota`, `admin`, and `super_admin` audiences.

### Changed

- Raised the Thermobox input ceiling to `500 C`, retained explicit `-` for
  non-applicable two-hour checkpoints, and kept downtime as one gross duration from
  incident start until machine recovery.
- Removed the redundant Shift 1 section context labels requested by operations.
- Enlarged two-hour PDF table text, included the date in the filename, and corrected
  page numbering to include the combined Downtime/Work Order appendix.
- Updated the compatible Worker API to `2026.17`; OTA remains optional for APK
  `0.13.1+` (`force_update=false`).

### Verified

- APK SHA-256: `82d93a31048d34eb28c4fbad4a186c083553cc618611463483cc6bb0299a2463`.
- Version code `50`, APK Signature Scheme v2 with one existing signer, release build,
  lint vital, focused Kotlin/Python/Worker tests, and emulator cold launch passed.
- APK-generated two-hour PDF was inspected across all seven pages for six machines,
  four slots, mold controls, `-`, gross downtime, Work Order, and sparepart usage.
- Isolated staging acceptance passed operations/private R2, checksheet revision and
  PC import, FID registration for all three roles, visible background notification,
  exact cleanup, and zero foreign-key violations.
- Production D1 backup/recovery was verified before the three ordered migrations;
  Worker `2026.17` deployed with production data counts intact and zero foreign-key
  violations. No trial account or trial submission was created in production.

## 0.16.0 - 2026-08-01

### Changed

- Added explicit `OK` / `NG` / `-` safety input to the Shift 1 checksheet and three
  measurement contexts: hydraulic cycle, lubrication-pump cycle, and heater state.
- Kept non-applicable or non-steady measurements out of machine-condition KPI while
  preserving them as evidence in checked PDF output; door and Mold Close remain the
  independent safety gate, while Fuse `NG` remains directly critical.
- Updated the form contract to `2026.08.4` and the compatible Worker API source to
  `2026.15`. The OTA remains optional for APK `0.13.1+` (`force_update=false`).

### Verified

- APK SHA-256: `6fa7eab73d1f4d8d2ceb2608b7eb65eb1adae0ae023e3a1f042ae625d43fa701`.
- Version code `48`, APK Signature Scheme v2, targeted Python `74/74`, Worker
  compatibility `28/28`, APK focused unit tests, and release lint/build passed.
- Staging then production Worker/form activation passed. Production D1 recovery was
  verified before activation: 41 tables, integrity `ok`, and zero foreign-key
  violations. No trial account, submission, or production data was created.
- Emulator cold-launch verification is pending because this Windows profile has no
  registered Android virtual device; no physical-device test was substituted.

## 0.15.0 - 2026-07-31

### Changed

- Added explicit `-` (N/A) input to applicable numeric, condition, leak, and Cooling
  Tower fields in the Shift 2/3 two-hour checksheet.
- Kept blank values incomplete, kept `0` as a real measurement, automatically
  normalized disabled fields to `-`, and retained `On`/`Off` for Hopper Dryer.
- Updated the operations contract to `2026.13.0`, slot package to
  `shift-slot-2026.11.0`, and Worker API to `2026.14`.

### Verified

- APK SHA-256: `d21612a46cc19fd1ad0f6712e334d20488c797bd0f2ec4cfc78c90a1b58c62b4`.
- Version code `47`, APK Signature Scheme v2 with the existing single signer,
  Python `148/148`, Worker `84/84`, Android unit `66/66`, lint/build, EXE smoke,
  and minimal emulator verification passed.
- Isolated staging acceptance passed shift, downtime, Work Order/private R2, two
  five-form submissions, revision, batch approval, PC import/PDF, background FCM,
  and operational alert recovery with exact cleanup and zero foreign-key violations.

## 0.14.0 - 2026-07-31

### Added

- Added exactly one combined Downtime and Work Order summary page to every checksheet
  PDF export, including scoped empty states and bounded detail rows.
- Added effective-dated shift rotation safety, audited checksheet soft-delete, and
  strict OTA compatibility validation across the Worker and APK.

### Changed

- Simplified downtime to one gross duration from incident start until machine
  recovery; response, active-work, and waiting breakdowns are no longer shown.
- Replaced manual ISO-8601 entry with WITA date/time pickers and slightly enlarged
  text throughout Shift 1, Shift 2/3, and operations-summary PDF pages.
- Hardened checked-PDF packet validation, atomic/non-overwriting export, and
  account-bound WorkManager media uploads.

### Verified

- APK SHA-256: `3765c7f8273c181bf8a81d416ff69057b3ede468b8cc02a4a2f422813bc42021`.
- Version code `46`, APK Signature Scheme v2 with the existing single signer,
  Python `146/146`, Worker `83/83`, Android unit `65/65`, lint/build, package
  round-trip, and focused emulator checks passed.
- Isolated staging acceptance passed two five-form submissions, pending revision,
  batch approval, PC import, combined PDF, private-R2 operations, background FCM,
  and operational alert recovery with exact cleanup and zero foreign-key violations.

## 0.13.1 - 2026-07-29

### Changed

- Added the checksheet date to checked-PDF filenames using
  `Checksheet Mesin - Checked - YYYY-MM-DD.pdf`.
- Kept one combined PDF for multi-machine exports and rejected packets whose
  checksheets do not share one valid date.

### Verified

- APK SHA-256: `772b0fec313c732134c7a21a796062e61c067c35596d0859c98e95249ca87b6b`.
- Version code `45`, APK Signature Scheme v2 with the existing single signer,
  Android unit tests `50/50`, release/debug lint and builds, and focused checked-PDF
  instrumentation `2/2` passed on Android Studio emulator `MTC_API35`.
- Release installation, version inspection, cold launch, live process, and empty
  crash buffer passed on the same emulator before OTA publication.

## 0.13.0 - 2026-07-29

### Changed

- Replaced mandatory daily admin assignment with an automatic two-day member
  rotation and the `Mulai Shift Saya` member claim.
- Added explicit expected/actual member context. Replacement claims require a reason
  while preserving the authenticated member as operator/verifier.
- Added per-slot status selection for all six canonical machines:
  `Produksi`, `Idle`, or `Off`. Only production machines require the 40-point form,
  and one slot remains one atomic submission/review.
- Updated the APK to operations contract `2026.12.0`, slot package
  `shift-slot-2026.10.0`, and Worker API `2026.12`.

### Verified

- APK SHA-256: `d7e00eefb29f291266f30902cf44bc8285dde864cda15609efeef626242b3233`.
- Version code `44`, APK Signature Scheme v2 with the existing single signer,
  Android unit tests, release lint, and clean release build passed.
- Worker `71/71`, Python `131/131`, contract round-trip, production D1
  recovery/migration, controlled shift/downtime/private-R2 acceptance, exact cleanup,
  and foreign-key verification passed before OTA publication.
- OTA public-hash, active manifest, emulator cold launch, and background-push evidence
  must be recorded in the source repository after activation.

## 0.12.0 - 2026-07-28

### Added

- Added a dedicated two-hour checksheet for production machines on Shift 2 and
  Shift 3, including server-timestamp compliance, scheduled Cooling Tower input,
  revision, review, and one submission per slot.
- Added structured downtime reporting with fair wait-time separation and cross-shift
  incident handover.
- Added Work Orders with scored review and private photo/video evidence in Cloudflare
  R2 through Android Photo Picker and retry-safe background uploads.

### Safety

- Added fail-closed R2 guards at 8 GB storage, 800,000 Class A operations, and
  8,000,000 Class B operations over the app ledger window.
- Added admin quota visibility and non-retryable APK handling when the Worker blocks
  an upload with HTTP `507`.

### Verified

- APK SHA-256: `5745cc71f870eeabd38191b3299321eaa77646d534a7daed32f756ce83c550b0`.
- Version code `43`, APK Signature Scheme v2, release lint/build, 48 Android unit
  tests, install, and cold launch passed on Android Studio emulator API 35.
- Worker `70/70`, Python `129/129`, D1 migration/recovery, production feature
  acceptance, private R2 upload/download/delete, exact cleanup, and foreign-key
  verification passed.

## 0.10.7 - 2026-07-26

### Fixed

- Removed the duplicate Mold input from Checksheet Limit Switch. Mold is now entered
  once in Checksheet Mesin and remains available as package-level machine context.
- Aligned the APK with `checksheet-package-2026.08.3`; the Worker accepts and
  normalizes conflict-free `2026.08.2` packages during the migration window.

### Verified

- APK SHA-256: `c1ebf18d2eae8e885cebe2703b058463069561512e470d26a23e4992021814a5`.
- Version code `41`, APK Signature Scheme v2, release lint/build, 42 Android unit
  tests, focused package-contract instrumentation, and five-form roundtrip passed.
- Live D1 form `2026.08.3` contains five forms, one Machine-owned `mold_name`, and
  no Limit Switch `mold_name`.

## 0.10.6 - 2026-07-26

### Fixed

- Deduplicated concurrent Firebase registration callbacks so the same user/token pair
  cannot create parallel Worker upserts.
- Forwarded the generic Worker `entity_id` from background FCM data into the APK
  notification intent.

### Verified

- APK SHA-256: `9df18327f3f3e151fa58ed805520ad22e994a6ef66b1c2651980edcff8b02dd7`.
- Version code `40`, APK Signature Scheme v2, release lint/build/install/cold launch,
  42 Android unit tests, and focused FCM instrumentation passed.
- Controlled acceptance passed background notification-bar delivery plus the complete
  two-machine/five-form revision, batch-review, isolated-import, combined-PDF, and
  operational-alert recovery flow.

## 0.10.5 - 2026-07-26

### Changed

- Moved notification access to a badged bell in the top-right APK header and removed
  notification history and the duplicate `Lainnya` entry.
- Consumed notification events are deleted immediately instead of retained as read
  history.
- Expanded Worker push coverage to review/import, pairing, user/account, Settings,
  OTA, repeated-login, schedule, and operational-state events.
- Daily checksheet schedule reminders now originate from the Worker cron, so delivery
  does not depend on opening the APK.

### Verified

- APK SHA-256: `4d56b01ce855ceb37c7df72b293ccd9c925bfaf557232698866bcd70e2948965`.
- Version code `39`, APK Signature Scheme v2, release lint/build/install/cold launch,
  41 Android unit tests, and 3 focused emulator instrumentation tests passed.
- A controlled Android Studio emulator trial proved data-only FCM delivery to the
  notification bar while the APK was in the background.
- The same live trial passed two one-package submissions (`MA780` and `PLY950`), five
  forms per package, Pending Review revision, one batch decision, two-row isolated PC
  import, one combined checked PDF, and `Critical` to `Healthy` operational alerts.
- Worker regression passed `43/43`; D1 cleanup and foreign-key verification passed.

## 0.10.4 - 2026-07-26

### Changed

- Reworked every `Lainnya` workflow with role-aware navigation, explicit return
  behavior, independent loading states, safe confirmations, useful empty/error
  states, and current-account protection.
- Pairing requests are scoped to the current device; active devices cannot be
  silently reassigned to another member.
- Notifications now expose active/history views and route member review events to
  Riwayat instead of an unauthorized admin screen.
- Mold dropdowns always include `-` when no mold is installed.
- Hopper Dryer status is an explicit Production decision. MTC measurement fields are
  active and required only for `On`; `Off` stores the measurements as `-`, while
  machine-specific central Settings remain authoritative.

### Verified

- APK SHA-256: `2e1c8d8d75276644f9d77bbbe03729baed70258c5c2df149f8578e5ec9b28fa4`.
- Version code `38`, APK Signature Scheme v2, 39 Android unit tests, release lint,
  release build, install, cold launch, and fatal-log check passed.
- One focused `Lainnya` navigation instrumentation test passed on Android Studio
  emulator API 35; no physical device was used.
- Worker tests passed `39/39`; D1 form `2026.08.2` and all 21 Hopper access matrices
  were verified with no foreign-key violations.

## 0.10.3 - 2026-07-26

### Fixed

- Added role-aware route validation for the `Lainnya` menu.
- Added a visible return action on child screens and preserved the primary tab that
  opened `Lainnya`, so Back no longer jumps unexpectedly to Beranda.
- Unknown routes now return to Beranda instead of silently opening the checksheet form.
- Added concise descriptions to operational, administration, account, and device menu
  entries.

### Verified

- APK SHA-256: `2908dbf91e5f59e0e14d25f97308d4c72d9dab439759613aa86d6e8b493bfe66`.
- Version code `37`, APK Signature Scheme v2, release build, lint vital, unit tests,
  install, cold launch, and fatal-log check passed.
- Focused navigation instrumentation passed on Android Studio emulator `MTC_API35`.

## 0.10.2 - 2026-07-26

### Added

- Added member revision while a checksheet is still Pending Review, guarded by a
  submission revision number so an admin cannot review stale data.
- Added persistent notification inbox/history, read state, and navigation from a
  tapped background notification to the relevant APK tab.
- Added Hopper Dryer On/Off input. Off forces the remaining Hopper fields to `-`.

### Fixed

- Mold and limit-switch mode inputs now accept `-` consistently with central Settings.
- Push token registration is retried after login/session restore, while important FCM
  events remain high-priority data messages.

### Verified

- APK SHA-256: `227bdb2abe1d0d94e0d638be2f277d52b535e1d0b6f2ea3227d2386a0a744c7f`.
- Version code `36`, APK Signature Scheme v2, release build, lint vital, unit tests,
  install, cold launch, and fatal-log check passed on Android Studio emulator
  `MTC_API35`.
- Worker `36/36`, Python `94/94`, contract/documentation guards, and
  APK-to-Worker-to-EXE package round-trip passed.

## 0.10.1 - 2026-07-19

### Changed

- Migrated Android FCM registration from deprecated `getToken()` to
  `FirebaseMessaging.register()` and `onRegistered`, while retaining the legacy token
  refresh callback for SDK compatibility.

### Verified

- APK SHA-256: `cb0eec8f06af5a2c367e9a1515eaae85c4d914f1485379ef379d5d201f82b8c7`.
- Version code `35`, signature v2, cold launch, package/input/PDF instrumentation, and
  FCM background delivery passed on Samsung `SM-F956B`.

## 0.10.0 - 2026-07-19

### Added

- Published signed APK version `0.10.0` (`versionCode 34`).
- Added polished member/admin navigation, one five-form package per machine, and
  centrally configurable field access for Production, Idle, and Off conditions.
- Important FCM events now use high-priority data messages so the APK service can
  display notifications while the app is in the background.

### Fixed

- Machine aliases, heater values, cooling time, and multi-machine checked-PDF data
  remain bound to the correct canonical machine.
- Disabled heater-current positions also disable the matching fuse field.
- Compact-screen admin navigation now scrolls to the Administration section before
  screenshot validation, and deprecated Compose dropdown anchors were migrated.

### Verified

- APK SHA-256: `7ac7bec118a7d1e3ba85af4918bc9d186b4a87ef8ed76697178351befc304ea0`.
- APK Signature Scheme v2 with the production signer; Android unit, lint vital,
  debug, instrumentation, and release builds passed.
- Samsung `SM-F956B` physical tests passed for package submission, all five forms,
  six-machine PDF mapping, combined-machine PDF output, responsive UI, and FCM.
- A controlled live trial passed pairing, three machine-operation conditions,
  three five-form packages, batch approval, EXE import, monthly Excel/PDF reports,
  Imported status, and cleanup of temporary D1 rows.
- The public GitHub artifact and active D1 manifest hashes match the local APK.
- The live manifest serves `0.10.0` with `force_update=false`; signed release install
  and cold launch passed on Samsung `SM-F956B` without a fatal exception.

## 0.9.2 - 2026-07-19

### Fixed

- Centrally disabled mold/mode fields now accept the explicit `-` sentinel during
  APK validation instead of blocking submission.
- Resubmit is restricted to the original submission owner so the checksheet operator
  cannot be replaced by a reviewing admin.
- EXE import rejects conflicting `machine_id`/`machine_code`, stale package versions,
  and unknown package-level fields.

### Verified

- APK SHA-256: `85e2f39d81e26732cf1f93c07fa222e48b3f21ed3761185a2096ec9d1acbfced`.
- APK Signature Scheme v2, one signer; Android unit and release builds passed.
- Worker regression test passed `21/21`; package round-trip to SQLite passed.
- Physical-device verification for `0.9.2` is pending because no ADB device was
  connected during this patch build; `0.9.1` remains the latest device-tested base.

## 0.9.1 - 2026-07-19

### Added

- Published signed APK version `0.9.1` (`versionCode 32`).
- Added server-authoritative operator identity, live Settings/form/date/value
  validation, review/import state guards, and APK-to-SQLite round-trip coverage.

### Verified

- APK SHA-256: `dd523032ffd4eff4fcd9752af94a69934670888bc9ef4457c57db68cee7ceaa9`.
- APK Signature Scheme v2, Android unit/release build, package instrumentation `2/2`,
  five-form UI instrumentation `1/1`, installation, and cold launch passed on Samsung
  `SM-F956B`.
- Live Worker package flow proved authenticated member identity, separate cloud
  reviewer, authoritative Settings, Approved sync listing, Imported transition, and
  complete cleanup of temporary D1 rows.
- Local artifact, public GitHub URL, and active D1 manifest hashes match. The live
  manifest serves `0.9.1`, minimum `0.8.0`, form
  `checksheet-package-2026.08.1`, and `force_update=false`.

## 0.9.0 - 2026-07-19

### Added

- Published signed APK version `0.9.0` (`versionCode 31`).
- Added one package submission per machine with all five checksheet forms under contract `2026.08.1`.
- Added canonical machine alias handling and corrected heater, cooling-time, and multi-machine checked-PDF placement.

### Verified

- APK SHA-256: `c0ea81206e15e911fe5718339e5184ee4d78a9db482838ae30a140c8d84dd906`.
- Android unit/build checks and physical Samsung `SM-F956B` package/PDF instrumentation passed.
- The public GitHub artifact, local release, and active D1 manifest hashes match.
- The live manifest serves `0.9.0` with `force_update=false` and form version
  `checksheet-package-2026.08.1`.
- Authenticated package create/read/delete and Worker-to-device FCM delivery passed;
  the temporary test identity and data were removed afterward.

## 0.8.7 - 2026-07-19

### Added

- Published signed APK version `0.8.7` (`versionCode 30`).
- Added centrally controlled form access, batch review, pairing requests, FCM support, and consolidated checked-PDF export.

### Verified

- APK SHA-256: `7b0c1bb2a5a9232a72baa961377eff719a63ce68f7982ce7f83bb1049061cf58`.
- OTA manifest points to the immutable `releases/v0.8.7/app-release.apk` artifact.

### Pending Verification

- Final physical-device regression for version `0.8.7`, including closed-app/background FCM delivery and the two-machine checked-PDF scenario.

## 0.8.1 - 2026-07-18

- Published the earlier internal OTA release with charging KPI diagnostics and checked-PDF context improvements.
