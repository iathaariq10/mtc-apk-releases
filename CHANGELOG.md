# Changelog

Every OTA artifact or metadata change must be recorded here in the same commit.

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
