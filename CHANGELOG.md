# Changelog

Every OTA artifact or metadata change must be recorded here in the same commit.

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
