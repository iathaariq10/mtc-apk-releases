# mtc-apk-releases

Public APK release artifacts for the MTC Maintenance internal OTA channel. This repository contains distributable APK files and release metadata only; application source code, credentials, temporary test files, and private operational data must not be committed here.

## Latest Release

- Version: `0.9.2`
- Version code: `33`
- APK: [`releases/v0.9.2/app-release.apk`](releases/v0.9.2/app-release.apk)
- Direct URL: `https://raw.githubusercontent.com/iathaariq10/mtc-apk-releases/main/releases/v0.9.2/app-release.apk`
- SHA-256: `85e2f39d81e26732cf1f93c07fa222e48b3f21ed3761185a2096ec9d1acbfced`
- Live manifest: `https://mtc-maintenance-api.iathaariq10.workers.dev/v1/update/manifest`

Release `0.9.2` keeps one five-form package per machine and closes the final correction
and Settings edge cases: centrally disabled option fields accept the explicit `-`
sentinel, only the original submission owner can resubmit, and EXE import rejects
conflicting machine identity or stale package metadata.

## Publishing Rules

1. Never replace an APK under an existing version path. Publish a new version directory instead.
2. Update this README and `CHANGELOG.md` in the same commit as every APK or manifest-related change, including patch/minor/major changes.
3. Verify the release signature and compare the local APK SHA-256 with the public URL and live OTA manifest before announcing availability.
4. Keep version name, version code, download URL, hash, and release notes synchronized.
5. Do not commit signing keys, API tokens, service-account files, user data, test evidence, or backup artifacts.
