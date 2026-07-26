# Changelog

Every OTA artifact or metadata change must be recorded here in the same commit.

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
