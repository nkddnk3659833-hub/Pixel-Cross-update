# PIXEL CROSS — update channel

Public repository reserved for in-app update metadata and published Android builds.

## Planned release layout

- `latest.json` — current release manifest consumed by the Android app.
- `releases/<version>/` — release notes and checksums.
- APK assets — published only after a build is verified.

## Release safety

A release must not be announced here until:
1. GitHub Actions has completed successfully.
2. The APK has been installed and smoke-tested on Android.
3. The APK SHA-256 checksum has been calculated.
4. The manifest versionCode is higher than the installed app version.

The app-side updater and manifest parser are not implemented yet. This repository is intentionally initialized without a fake release manifest or placeholder APK.
