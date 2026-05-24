# How To Build

This guide explains how to build the CorteXField mobile app without committing private deployment configuration.

## Prerequisites

- Flutter `3.29.3`, matching [.fvmrc](.fvmrc)
- Dart SDK bundled with Flutter
- Android Studio or Android command-line tools
- Android SDK and an available emulator or device
- Xcode and CocoaPods for iOS builds on macOS

If you use FVM:

```sh
fvm flutter pub get
```

If Flutter is installed directly:

```sh
flutter pub get
```

## Local Config

Copy the example file and fill in your private values:

```sh
cp configs.example.json configs.json
```

On Windows PowerShell:

```powershell
Copy-Item configs.example.json configs.json
```

Required private values:

- `thingsboardApiEndpoint`
- `thingsboardAndroidAppSecret`
- `thingsboardIosAppSecret` if iOS OAuth needs one

Typical CorteXField values:

```json
{
  "thingsboardApiEndpoint": "https://thingsboard.cortexfield.com",
  "appLinksUrlHost": "thingsboard.cortexfield.com",
  "appLinksUrlScheme": "https",
  "androidApplicationId": "io.cortexfield.app",
  "androidApplicationName": "CorteXField",
  "iosApplicationId": "io.cortexfield.app",
  "iosApplicationName": "CorteXField",
  "thingsboardOAuth2CallbackUrlScheme": "io.cortexfield.app.auth"
}
```

Do not commit `configs.json`; it is ignored by Git.

## Android Debug Build

```sh
flutter build apk --debug --dart-define-from-file=configs.json
```

FVM:

```sh
fvm flutter build apk --debug --dart-define-from-file=configs.json
```

## Android Release Build

Configure release signing before publishing. Then run:

```sh
flutter build apk --release --dart-define-from-file=configs.json
```

For an app bundle:

```sh
flutter build appbundle --release --dart-define-from-file=configs.json
```

## iOS Build

Run from macOS with Xcode installed:

```sh
flutter build ios --release --dart-define-from-file=configs.json
```

Before App Store distribution, verify bundle ID, signing team, associated domains, and OAuth callback settings in Xcode.

## GitHub Actions Build

The workflow at [.github/workflows/android-ci.yml](.github/workflows/android-ci.yml) generates `configs.json` during CI.

Add these repository or organization secrets:

- `APP_ENDPOINT`
- `THINGSBOARD_ANDROID_APP_SECRET`
- `THINGSBOARD_IOS_APP_SECRET` if required

Optional repository or organization variables:

- `APP_LINKS_URL_HOST`
- `APP_LINKS_URL_SCHEME`
- `ANDROID_APPLICATION_ID`
- `ANDROID_APPLICATION_NAME`
- `IOS_APPLICATION_ID`
- `IOS_APPLICATION_NAME`
- `THINGSBOARD_OAUTH2_CALLBACK_URL_SCHEME`

Trigger the workflow from GitHub Actions or by pushing to `master`.

## Regenerating Branding Assets

When changing app icons or splash assets, update the source files under `assets/branding/`, then run the relevant generators:

```sh
flutter pub run flutter_launcher_icons
dart run flutter_native_splash:create
```

Commit the regenerated Android and iOS assets together with the source branding files.

## License Notes

This app is derived from the upstream ThingsBoard Mobile Application. Keep [LICENSE](LICENSE) with source distributions and include the upstream copyright/license notice and disclaimer with binary distribution materials.
