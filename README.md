## CorteXField Mobile Application is an open-source project based on [Flutter](https://flutter.dev/)
Powered by CorteXField IoT Platform

Build your own IoT mobile application **with minimum coding efforts**

## Please be informed the Web platform is not supported, because it's a part of our main platform!

## Resources

- [Getting started](https://thingsboard.io/docs/mobile/getting-started/) - learn how to set up and run your first IoT mobile app
- [Customize your app](https://thingsboard.io/docs/mobile/customization/) - learn how to customize the app
- [Publish your app](https://thingsboard.io/docs/mobile/release/) - learn how to publish app to Google Play or App Store

## Private build configuration

`configs.json` contains environment-specific values and secrets, so it is ignored by Git. Use `configs.example.json` as the template for local builds and pass the real file to Flutter:

```sh
flutter build apk --dart-define-from-file=configs.json
```

For GitHub Actions, add these repository or organization secrets:

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

## Live demo app

To be familiar with common app features, review the upstream live demo application available on Google Play and App Store
- [Get it on Google Play](https://play.google.com/store/apps/details?id=org.thingsboard.demo.app&pcampaignid=pcampaignidMKT-Other-global-all-co-prtnr-py-PartBadge-Mar2515-1)
- [Download on the App Store](https://apps.apple.com/us/app/thingsboard-live/id1594355695?itsct=apps_box_badge&amp;itscg=30200)
