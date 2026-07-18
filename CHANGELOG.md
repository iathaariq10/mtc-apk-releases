# Changelog

Every OTA artifact or metadata change must be recorded here in the same commit.

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

### Pending Verification

- Compare the public GitHub artifact hash with the local checksum, activate the D1 OTA
  manifest, and verify the live manifest before declaring OTA `0.9.1` active.

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
