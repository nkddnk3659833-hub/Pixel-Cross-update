# PIXEL CROSS update manifest

The Android client will read the public manifest from:

`https://raw.githubusercontent.com/nkddnk3659833-hub/Pixel-Cross-update/main/latest.json`

Do not create `latest.json` until a real APK has been built, smoke-tested, and checksummed.

## Proposed schema

```json
{
  "schemaVersion": 1,
  "appId": "com.pixelcross",
  "versionCode": 4,
  "versionName": "0.2.2",
  "minimumSupportedVersionCode": 1,
  "releaseNotes": "Bug fixes and improvements",
  "apkUrl": "https://github.com/nkddnk3659833-hub/Pixel-Cross-update/releases/download/v0.2.2/pixel-cross-0.2.2.apk",
  "sha256": "64-character-lowercase-hex-checksum",
  "publishedAt": "2026-11-26T00:00:00Z"
}
```

## Client validation rules

1. Require the expected `appId` and supported `schemaVersion`.
2. Offer an update only when `versionCode` is greater than the installed version.
3. Treat `minimumSupportedVersionCode` as a compatibility floor, not as permission to bypass Android installation confirmation.
4. Download only over HTTPS.
5. Verify the APK SHA-256 before opening the Android package installer.
6. Never install silently; Android must show the system installation confirmation.
7. If the manifest is malformed or the checksum fails, keep the installed app unchanged.

## Release procedure

1. Build and test the APK in the private development repository.
2. Create a versioned GitHub Release in this public repository and attach the APK.
3. Calculate SHA-256 from the exact uploaded APK.
4. Update `latest.json` only after the release asset is available.
