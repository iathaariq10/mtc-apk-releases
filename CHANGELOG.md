# Changelog

Every OTA artifact or metadata change must be recorded here in the same commit.

## 0.9.0 - 2026-07-19

### Added

- Published signed APK version `0.9.0` (`versionCode 31`).
- Added one package submission per machine with all five checksheet forms under contract `2026.08.1`.
- Added canonical machine alias handling and corrected heater, cooling-time, and multi-machine checked-PDF placement.

### Verified

- APK SHA-256: `c0ea81206e15e911fe5718339e5184ee4d78a9db482838ae30a140c8d84dd906`.
- Android unit/build checks and physical Samsung `SM-F956B` package/PDF instrumentation passed.

### Pending Verification

- Activate the live OTA manifest only after the public GitHub artifact hash matches this release.

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
