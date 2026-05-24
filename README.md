# CorteXField Mobile App

CorteXField Mobile App is the Flutter mobile client for the CorteXField agricultural IoT platform at [cortexfield.com](https://cortexfield.com/).

It is built for field teams and operators who need mobile access to farm telemetry, dashboards, alerts, and device workflows. The app supports CorteXField deployments focused on real-time monitoring, secure data access, intelligent control, analytics, sustainability, and custom integration across agriculture use cases such as aquaculture, hydroponics, livestock, and open-field operations.

## Project Origin

This repository is a CorteXField-branded derivative of the open-source [ThingsBoard Mobile Application](https://github.com/thingsboard/flutter_thingsboard_app), built with [Flutter](https://flutter.dev/).

The upstream ThingsBoard copyright and license notice are preserved in [LICENSE](LICENSE). When distributing source or binaries, keep the license notice and disclaimer with the app materials. CorteXField is not affiliated with or endorsed by ThingsBoard, and the ThingsBoard name, trademarks, or contributors must not be used to imply endorsement without written permission.

## Build

Build instructions are maintained in [HOW_TO_BUILD.md](HOW_TO_BUILD.md).

The real `configs.json` file contains deployment-specific values and secrets and must not be committed. Use [configs.example.json](configs.example.json) as a template for local builds.

## Private Configuration

`configs.json` is ignored by Git. For local builds, create it from `configs.example.json` and pass it to Flutter:

```sh
flutter build apk --dart-define-from-file=configs.json
```

For GitHub Actions, store sensitive values as repository or organization secrets:

- `APP_ENDPOINT`
- `THINGSBOARD_ANDROID_APP_SECRET`
- `THINGSBOARD_IOS_APP_SECRET` if iOS OAuth needs one

Optional non-secret repository or organization variables:

- `APP_LINKS_URL_HOST`
- `APP_LINKS_URL_SCHEME`
- `ANDROID_APPLICATION_ID`
- `ANDROID_APPLICATION_NAME`
- `IOS_APPLICATION_ID`
- `IOS_APPLICATION_NAME`
- `THINGSBOARD_OAUTH2_CALLBACK_URL_SCHEME`

The Android CI workflow generates `configs.json` at build time from those secrets and variables.

## Upstream Resources

- [ThingsBoard Mobile App docs](https://thingsboard.io/docs/mobile/getting-started/)
- [ThingsBoard app customization](https://thingsboard.io/docs/mobile/customization/)
- [Publishing guide](https://thingsboard.io/docs/mobile/release/)
- [Upstream repository](https://github.com/thingsboard/flutter_thingsboard_app)
