# mtc-apk-releases

Public APK release artifacts for the MTC Maintenance internal OTA channel. This repository contains distributable APK files and release metadata only; application source code, credentials, temporary test files, and private operational data must not be committed here.

## Latest Release

- Version: `0.12.0`
- Version code: `43`
- APK: [`releases/v0.12.0/app-release.apk`](releases/v0.12.0/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.12.0/app-release.apk`
- SHA-256: `5745cc71f870eeabd38191b3299321eaa77646d534a7daed32f756ce83c550b0`
- Live manifest: `https://mtc-maintenance-api.iathaariq10.workers.dev/v1/update/manifest`

Release `0.12.0` adds the two-hour checksheet for Shift 2/3, structured downtime,
and Work Order evidence using private Cloudflare R2. The APK uses one operational
flow per shift/slot, server timestamps for compliance, downtime handover, and
retry-safe Photo Picker uploads. R2 use is protected by fail-closed storage and
operation limits below the Cloudflare free-tier allowances.

## Publishing Rules

1. Never replace an APK under an existing version path. Publish a new version directory instead.
2. Update this README and `CHANGELOG.md` in the same commit as every APK or manifest-related change, including patch/minor/major changes.
3. Verify the release signature and compare the local APK SHA-256 with the public URL and live OTA manifest before announcing availability.
4. Keep version name, version code, download URL, hash, and release notes synchronized.
5. Do not commit signing keys, API tokens, service-account files, user data, test evidence, or backup artifacts.
